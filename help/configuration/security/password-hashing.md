---
title: hashing password
description: Scopri le strategie e l’implementazione di hashing della password.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# hashing password

Attualmente, Commerce utilizza la propria strategia per l’hashing della password, basata su diversi algoritmi nativi di hashing PHP. Commerce supporta più algoritmi come `MD5`, `SHA256`oppure `Argon 2ID13`. Se l&#39;estensione Sodium è installata (installata per impostazione predefinita in PHP 7.3), allora `Argon 2ID13` viene scelto come algoritmo di hash predefinito. In caso contrario, `SHA256` è il valore predefinito. Commerce può utilizzare il PHP nativo `password_hash` con supporto dell’algoritmo Argon 2i.

Per evitare di compromettere le password meno recenti con hash con algoritmi obsoleti, come `MD5`, l’implementazione corrente fornisce un metodo per aggiornare l’hash senza modificare la password originale. In generale, l’hash della password ha il seguente formato:

```text
password_hash:salt:version<n>:version<n>
```

Dove `version<n>`...`version<n>` rappresenta tutte le versioni degli algoritmi hash utilizzate sulla password. Inoltre, il sale viene sempre memorizzato insieme all&#39;hash della password, in modo da poter ripristinare l&#39;intera catena di algoritmi. Esempio:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La prima parte rappresenta l’hash della password. Il secondo, `8qnyO4H1OYIfGCUb` è il sale. Gli ultimi due sono i diversi algoritmi hash: 1 `SHA256` e 2 `Argon 2ID13`. Ciò significa che la password del cliente è stata originariamente impostata con hash con `SHA256` e in seguito, l&#39;algoritmo è stato aggiornato con `Argon 2ID13` e l&#39;hash è stato riavviato con Argon.

## Strategia hash di aggiornamento

Considera l’aspetto del meccanismo di aggiornamento dell’hash. Supponiamo che originariamente una password sia stata impostata con hash con `MD5` e poi l&#39;algoritmo è stato aggiornato più volte con Argon 2ID13. Il diagramma seguente mostra il flusso di aggiornamento dell’hash.

![Flusso di lavoro di aggiornamento hash](../../assets/configuration/hash-upgrade-algorithm.png)

Ogni algoritmo hash utilizza l’hash password precedente per generare un nuovo hash. Commerce non memorizza la password originale non elaborata.

![Strategia di aggiornamento hash](../../assets/configuration/hash-upgrade-strategy.png)

Come descritto in precedenza, l’hash della password potrebbe avere più versioni hash applicate alla password originale.
Ecco come funziona il meccanismo di verifica della password durante l’autenticazione del cliente.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Poiché Commerce memorizza tutte le versioni degli hash delle password utilizzate insieme all’hash della password, possiamo ripristinare l’intera catena di hash durante la verifica della password. Il meccanismo di verifica dell’hash è simile alla strategia di aggiornamento dell’hash: in base alle versioni memorizzate insieme all’hash della password, l’algoritmo genera hash dalla password fornita e restituisce il risultato del confronto tra la password con hash e l’hash memorizzato nel database.

## Implementazione

La `\Magento\Framework\Encryption\Encryptor` la classe è responsabile della generazione e della verifica dell&#39;hash della password. La [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) aggiorna l’hash di una password del cliente all’algoritmo hash più recente.

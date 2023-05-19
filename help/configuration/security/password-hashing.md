---
title: Hashing password
description: Scopri le strategie e l’implementazione di hashing delle password.
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Hashing password

Attualmente, Commerce utilizza una propria strategia per l’hashing delle password, basata su diversi algoritmi di hashing PHP nativi. Commerce supporta più algoritmi come `MD5`, `SHA256`, o `Argon 2ID13`. Se è installata l&#39;estensione Sodio (installata per impostazione predefinita in PHP 7.3), `Argon 2ID13` viene scelto come algoritmo di hashing predefinito. Altrimenti, `SHA256` è il valore predefinito. Commerce può utilizzare il PHP nativo `password_hash` con supporto algoritmo Argon 2i.

Per evitare di compromettere le password meno recenti con hash di algoritmi obsoleti come `MD5`, l’implementazione corrente fornisce un metodo per aggiornare l’hash senza modificare la password originale. In generale, l’hash della password ha il seguente formato:

```text
password_hash:salt:version<n>:version<n>
```

Dove `version<n>`...`version<n>` rappresenta tutte le versioni degli algoritmi hash utilizzate sulla password. Inoltre, il sale viene sempre memorizzato insieme all&#39;hash della password, in modo da poter ripristinare l&#39;intera catena di algoritmi. Ecco un esempio:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La prima parte rappresenta l’hash della password. La seconda, `8qnyO4H1OYIfGCUb` è il sale. Gli ultimi due sono i diversi algoritmi hash: 1 è `SHA256` e 2 è `Argon 2ID13`. Ciò significa che originariamente era presente un hash alla password del cliente `SHA256` e in seguito, l’algoritmo è stato aggiornato con `Argon 2ID13` e l&#39;hash è stato riesumato con Argon.

## Strategia di aggiornamento hash

Considera l’aspetto del meccanismo di aggiornamento hash. Supponiamo che originariamente, una password sia stata sottoposta ad hashing con `MD5` l&#39;algoritmo è stato aggiornato più volte con Argon 2ID13. Il diagramma seguente mostra il flusso di aggiornamento hash.

![Flusso di lavoro di aggiornamento hash](../../assets/configuration/hash-upgrade-algorithm.png)

Ogni algoritmo hash utilizza l’hash della password precedente per generare un nuovo hash. Commerce non memorizza la password originale non elaborata.

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

Poiché Commerce memorizza tutte le versioni di hash della password utilizzate insieme all’hash della password, possiamo ripristinare l’intera catena di hash durante la verifica della password. Il meccanismo di verifica dell’hash è simile alla strategia di aggiornamento dell’hash: in base alle versioni memorizzate insieme all’hash della password, l’algoritmo genera hash dalla password fornita e restituisce il risultato del confronto tra la password con hash e l’hash memorizzato nel database.

## Implementazione

Il `\Magento\Framework\Encryption\Encryptor` La classe è responsabile della generazione e della verifica dell&#39;hash della password. Il [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) Il comando aggiorna l’hash della password di un cliente all’algoritmo hash più recente.

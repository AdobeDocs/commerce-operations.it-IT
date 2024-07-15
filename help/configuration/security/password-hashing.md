---
title: Hashing password
description: Scopri le strategie e l’implementazione di hashing delle password.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Hashing password

Attualmente, Commerce utilizza una propria strategia per l’hashing delle password, basata su diversi algoritmi di hashing PHP nativi. Commerce supporta più algoritmi come `MD5`, `SHA256` o `Argon 2ID13`. Se è installata l&#39;estensione Sodium (installata per impostazione predefinita in PHP 7.3), viene scelto `Argon 2ID13` come algoritmo di hashing predefinito. In caso contrario, `SHA256` è il valore predefinito. Commerce può utilizzare la funzione PHP `password_hash` nativa con il supporto dell&#39;algoritmo Argon 2i.

Per evitare di compromettere le password meno recenti che sono state sottoposte a hashing con algoritmi obsoleti come `MD5`, l&#39;implementazione corrente fornisce un metodo per aggiornare l&#39;hash senza modificare la password originale. In generale, l’hash della password ha il seguente formato:

```text
password_hash:salt:version<n>:version<n>
```

Dove `version<n>`...`version<n>` rappresenta tutte le versioni degli algoritmi hash utilizzate nella password. Inoltre, il sale viene sempre memorizzato insieme all&#39;hash della password, in modo da poter ripristinare l&#39;intera catena di algoritmi. Ecco un esempio:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

La prima parte rappresenta l’hash della password. Il secondo `8qnyO4H1OYIfGCUb` è il sale. Gli ultimi due sono diversi algoritmi hash: 1 è `SHA256` e 2 è `Argon 2ID13`. Ciò significa che alla password del cliente è stato originariamente applicato l&#39;hash con `SHA256` e successivamente l&#39;algoritmo è stato aggiornato con `Argon 2ID13` e l&#39;hash è stato rieseguito con Argon.

## Strategia di aggiornamento hash

Considera l’aspetto del meccanismo di aggiornamento hash. Si supponga che in origine sia stato eseguito l&#39;hashing di una password con `MD5` e che l&#39;algoritmo sia stato aggiornato più volte con Argon 2ID13. Il diagramma seguente mostra il flusso di aggiornamento hash.

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

La classe `\Magento\Framework\Encryption\Encryptor` è responsabile della generazione e della verifica dell&#39;hash della password. Il comando [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) aggiorna un hash della password del cliente all&#39;algoritmo hash più recente.

---
title: "[!DNL Upgrade Compatibility Tool] requisiti"
description: Verifica che il sistema soddisfi i requisiti necessari per eseguire il [!DNL Upgrade Compatibility Tool] in un’interfaccia a riga di comando per il progetto Adobe Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Chiavi di accesso Adobe Commerce

{{commerce-only}}

Devi avere [Chiavi di accesso Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) per scaricare e utilizzare [!DNL Upgrade Compatibility Tool]. Aggiungi le chiavi di accesso Adobe Commerce al tuo `auth.json` che si trova in `~/.composer` per impostazione predefinita.

>[!NOTE]
>
>Controlla il tuo **COMPOSER_HOME** variabile di ambiente per vedere dove `auth.json` il file si trova.

La **chiave pubblica** corrisponde a _username_ considerando che **chiave privata** è _password_:

## Esempio di chiavi di accesso Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Se non si configura correttamente il **Chiavi di accesso Adobe Commerce**, non è possibile scaricare [!DNL Upgrade Compatibility Tool] e `composer create-project` il comando avrà esito negativo.

Esegui `composer install` nel terminale per installare le dipendenze.

## Requisiti di sistema

I requisiti minimi per l&#39;utilizzo del [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia a riga di comando sono:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7.3 |
| Compositore | nessun requisito noto. |
| Node.js | Versioni di Node.js `^12.22.0`, `^14.17.0`oppure `>=16.0.0` (vedi [Installa Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Limiti di memoria | Almeno 2 GB di RAM. |

[!DNL Upgrade Compatibility Tool] richiede [PCNTL](https://www.php.net/manual/en/book.pcntl.php) e altre estensioni PHP per l&#39;esecuzione. Controlla le estensioni PHP richieste utilizzando `composer check-platform-reqs` comando:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce è supportato solo sui sistemi operativi Linux. Puoi eseguire il [!DNL Upgrade Compatibility Tool] in un sistema operativo Linux. Non è necessario eseguire il [!DNL Upgrade Compatibility Tool] dove si trova l’istanza Adobe Commerce.

È necessario per [!DNL Upgrade Compatibility Tool] per avere accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server.

Se esegui la [!DNL Upgrade Compatibility Tool] rispetto a un&#39;istanza Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere un&#39;elevata quantità di RAM (almeno 2 GB).

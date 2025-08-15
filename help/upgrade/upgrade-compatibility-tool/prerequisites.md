---
title: '[!DNL Upgrade Compatibility Tool] requisiti'
description: Verificare che il sistema soddisfi i requisiti necessari per eseguire  [!DNL Upgrade Compatibility Tool]  in un'interfaccia della riga di comando per il progetto Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Chiavi di accesso Adobe Commerce

{{commerce-only}}

È necessario disporre di [chiavi di accesso Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) per scaricare e utilizzare [!DNL Upgrade Compatibility Tool]. Aggiungi le chiavi di accesso Adobe Commerce al file `auth.json`, che per impostazione predefinita si trova in `~/.composer`.

>[!NOTE]
>
>Controllare la variabile di ambiente **COMPOSER_HOME** per vedere dove si trova il file `auth.json`.

La **chiave pubblica** corrisponde al _nome utente_, mentre la **chiave privata** è la _password_:

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
> Se non configuri correttamente le **chiavi di accesso Adobe Commerce**, non puoi scaricare [!DNL Upgrade Compatibility Tool] e il comando `composer create-project` non riuscirà.

Esegui `composer install` nel terminale per installare le dipendenze.

## Requisiti di sistema

I requisiti minimi per utilizzare [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando sono:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7,3 |
| Compositore | nessun requisito noto. |
| Node.js | Versioni di Node.js `^12.22.0`, `^14.17.0` o `>=16.0.0` (vedi [Installa Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limitazioni della memoria | Almeno 2 GB di RAM. |

[!DNL Upgrade Compatibility Tool] richiede [PCNTL](https://www.php.net/manual/en/book.pcntl.php) e altre estensioni PHP per l&#39;esecuzione. Controllare le estensioni PHP richieste utilizzando il comando `composer check-platform-reqs`:

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

Adobe Commerce è supportato solo su sistemi operativi Linux. È possibile eseguire [!DNL Upgrade Compatibility Tool] in un sistema operativo Linux. Non è necessario eseguire [!DNL Upgrade Compatibility Tool] dove si trova l&#39;istanza Adobe Commerce.

[!DNL Upgrade Compatibility Tool] deve avere accesso al codice sorgente dell&#39;istanza di Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all’installazione di Adobe Commerce su un altro server.

Se si esegue [!DNL Upgrade Compatibility Tool] su un&#39;istanza di Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere una quantità elevata di RAM (almeno 2 GB).

Esegui [!DNL Upgrade Compatibility Tool] da [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) per [progetti Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.

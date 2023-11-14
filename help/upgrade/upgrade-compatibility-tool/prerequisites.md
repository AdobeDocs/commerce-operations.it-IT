---
title: '''[!DNL Upgrade Compatibility Tool] requisiti"'
description: Verificare che il sistema soddisfi i requisiti necessari per eseguire [!DNL Upgrade Compatibility Tool] in un’interfaccia della riga di comando per il progetto Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Chiavi di accesso Adobe Commerce

{{commerce-only}}

Devi avere [Chiavi di accesso Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) per scaricare e utilizzare [!DNL Upgrade Compatibility Tool]. Aggiungi le chiavi di accesso Adobe Commerce al tuo `auth.json` file, che si trova in `~/.composer` per impostazione predefinita.

>[!NOTE]
>
>Controlla il tuo **COMPOSER_HOME** variabile di ambiente per vedere dove `auth.json` il file si trova.

Il **chiave pubblica** corrisponde al _nome utente_ considerando che **chiave privata** è il _password_:

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
> Se non configuri correttamente il **Chiavi di accesso Adobe Commerce**, non è possibile scaricare [!DNL Upgrade Compatibility Tool] e `composer create-project` il comando avrà esito negativo.

Esegui `composer install` nel terminale per installare le dipendenze.

## Requisiti di sistema

Requisiti minimi per l&#39;utilizzo del [!DNL Upgrade Compatibility Tool] in un’interfaccia della riga di comando:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7.3 |
| Compositore | nessun requisito noto. |
| Node.js | Versioni di Node.js `^12.22.0`, `^14.17.0`, o `>=16.0.0` (vedere [Installare Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limitazioni della memoria | Almeno 2 GB di RAM. |

[!DNL Upgrade Compatibility Tool] richiede [PCNTL](https://www.php.net/manual/en/book.pcntl.php) e altre estensioni PHP per l’esecuzione. Controlla le estensioni PHP richieste utilizzando `composer check-platform-reqs` comando:

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

Adobe Commerce è supportato solo su sistemi operativi Linux. È possibile eseguire [!DNL Upgrade Compatibility Tool] in un sistema operativo Linux. Non è necessario eseguire [!DNL Upgrade Compatibility Tool] in cui si trova l’istanza di Adobe Commerce.

È necessario per [!DNL Upgrade Compatibility Tool] per accedere al codice sorgente dell’istanza Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all’installazione di Adobe Commerce su un altro server.

Se si esegue [!DNL Upgrade Compatibility Tool] rispetto a un’istanza di Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere una quantità elevata di RAM (almeno 2 GB).

Esegui il [!DNL Upgrade Compatibility Tool] dal [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) per [Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} progetti.

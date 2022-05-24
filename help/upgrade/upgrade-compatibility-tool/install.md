---
title: Scarica la [!DNL Upgrade Compatibility Tool]
description: Segui questi passaggi per scaricare i [!DNL Upgrade Compatibility Tool] per il progetto Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Installa il [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La [!DNL Upgrade Compatibility Tool] è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce.

## Prerequisiti

Per installare [!DNL Upgrade Compatibility Tool], è necessario installare i prerequisiti necessari.

Vedi [prerequisiti](../upgrade-compatibility-tool/prerequisites.md) per ulteriori informazioni.

## Scarica la [!DNL Upgrade Compatibility Tool]

Per scaricare i [!DNL Upgrade Compatibility Tool], esegui il seguente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Chiavi di accesso Adobe Commerce

Devi avere [Chiavi di accesso Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) per scaricare e utilizzare [!DNL Upgrade Compatibility Tool]. Aggiungi le chiavi di accesso Adobe Commerce al tuo `auth.json` che si trova in `~/.composer` per impostazione predefinita.

>[!WARNING]
>
>Controlla il tuo **COMPOSER_HOME** variabile di ambiente per vedere dove `auth.json` il file si trova.

La **chiave pubblica** corrisponde a _username_ considerando che **chiave privata** è _password_:

### Esempio di chiavi di accesso Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Compositore

Scarica la [!DNL Upgrade Compatibility Tool] archivio ed esecuzione `composer install` nel terminale per installare le dipendenze.

>[!WARNING]
>
>Se la **Chiavi di accesso Adobe Commerce** non sono configurati correttamente, non è possibile scaricare il [!DNL Upgrade Compatibility Tool] e quando si esegue `composer create-project` il comando avrà esito negativo.

### Node.js

Per installare Node.js, consulta Node.js [documentazione](https://nodejs.dev/learn/how-to-install-nodejs).

## Estensioni di terze parti

Adobe consiglia di contattare il fornitore dell&#39;estensione per determinare se l&#39;estensione è completamente compatibile con l&#39;ultima versione rilasciata di Adobe Commerce.

Vedi [Esegui lo strumento](../upgrade-compatibility-tool/run.md) per informazioni sull&#39;esecuzione di [!DNL Upgrade Compatibility Tool].

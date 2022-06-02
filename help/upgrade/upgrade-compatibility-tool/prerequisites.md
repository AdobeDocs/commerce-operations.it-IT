---
title: '"[!DNL Upgrade Compatibility Tool] requisiti"'
description: 'Verifica che il sistema soddisfi i requisiti necessari per eseguire il [!DNL Upgrade Compatibility Tool] per il progetto Adobe Commerce. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Requisiti di sistema

{{commerce-only}}

I requisiti minimi per l&#39;utilizzo del [!DNL Upgrade Compatibility Tool] sono:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7,3 |
| Compositore | nessuna condizione nota |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`oppure `>=16.0.0`) |
| Limiti di memoria | Almeno 2 GB di RAM |

Puoi eseguire il [!DNL Upgrade Compatibility Tool] in diversi sistemi operativi (Windows non supportato). Non è necessario eseguire il [!DNL Upgrade Compatibility Tool] dove si trova l’istanza Adobe Commerce.

È necessario per [!DNL Upgrade Compatibility Tool] per avere accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server.

Se esegui la [!DNL Upgrade Compatibility Tool] rispetto a un&#39;istanza Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere un&#39;elevata quantità di RAM (almeno 2 GB).

## Chiavi di accesso Adobe Commerce

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

## Compositore

Scarica la [!DNL Upgrade Compatibility Tool] archivio ed esecuzione `composer install` nel terminale per installare le dipendenze.

>[!NOTE]
>
> Se non si configura correttamente il **Chiavi di accesso Adobe Commerce**, non è possibile scaricare [!DNL Upgrade Compatibility Tool]. Esecuzione del `composer create-project` il comando avrà esito negativo.

## Node.js

Per installare Node.js, consulta Node.js [documentazione](https://nodejs.dev/learn/how-to-install-nodejs).

## Estensioni di terze parti

Adobe consiglia di contattare il fornitore dell&#39;estensione per determinare se l&#39;estensione è completamente compatibile con l&#39;ultima versione di Adobe Commerce.

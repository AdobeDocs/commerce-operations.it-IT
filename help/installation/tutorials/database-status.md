---
title: Controllare lo stato del database
description: Segui questi passaggi per controllare lo stato del database Adobe Commerce o Magenti Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 2%

---


# Controllare lo stato del database

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Utilizzo dei comandi

Controllare lo stato del database.

```bash
bin/magento setup:db:status
```

Questo comando non dispone di argomenti o opzioni.

Segue l&#39;output del campione:

```terminal
All modules are up to date.
```

Il comando restituisce uno dei seguenti codici di uscita:

| Codice di uscita | Descrizione | Azione consigliata |
|--------------|--------------|---------------|
| 0 | Normale | Nessuno |
| 1 | Alcuni moduli utilizzano versioni del codice più recenti o precedenti rispetto al database | Esegui [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database ed eseguire `composer update` dalla directory radice dell’applicazione per aggiornare le dipendenze dei componenti |
| 2 | `magento setup:upgrade` obbligatorio | [`magento setup:upgrade`](database-upgrade.md) per aggiornare [schema di database](https://glossary.magento.com/database-schema) |

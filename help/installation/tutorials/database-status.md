---
title: Controllare lo stato del database
description: Segui questi passaggi per controllare lo stato del database Adobe Commerce o Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
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
| 2 | `magento setup:upgrade` obbligatorio | [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database |

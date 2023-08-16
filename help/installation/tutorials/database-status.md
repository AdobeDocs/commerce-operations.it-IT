---
title: Controllare lo stato del database
description: Segui questi passaggi per controllare lo stato del tuo database Adobe Commerce o Magento Open Source.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 3%

---

# Controllare lo stato del database

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Utilizzo dei comandi

Per controllare lo stato del database.

```bash
bin/magento setup:db:status
```

Il comando non contiene argomenti o opzioni.

Di seguito è riportato un esempio di output:

```terminal
All modules are up to date.
```

Il comando restituisce uno dei seguenti codici di uscita:

| Codice di uscita | Descrizione | Azione suggerita |
|--------------|--------------|---------------|
| 0 | Normale | Nessuno |
| 1 | Alcuni moduli utilizzano versioni di codice più recenti o precedenti rispetto al database | Esegui [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database ed eseguire `composer update` dalla directory radice dell&#39;applicazione per aggiornare le dipendenze dei componenti |
| 2 | `magento setup:upgrade` è obbligatorio | [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database |

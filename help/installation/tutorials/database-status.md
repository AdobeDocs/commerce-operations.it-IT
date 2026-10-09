---
title: Controllare lo stato del database
description: Per verificare lo stato del database Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%
---
# Controllare lo stato del database

Prima di eseguire questo comando, è necessario [creare o aggiornare la configurazione della distribuzione](deployment.md).

## Utilizzo dei comandi

Per controllare lo stato del database.

```shell
bin/magento setup:db:status
```

Il comando non contiene argomenti o opzioni.

Di seguito è riportato un esempio di output:

```text
All modules are up to date.
```

Il comando restituisce uno dei seguenti codici di uscita:

| Codice di uscita | Descrizione | Azione suggerita |
|--------------|--------------|---------------|
| 0 | Normale | Nessuno |
| 1 | Alcuni moduli utilizzano versioni di codice più recenti o precedenti rispetto al database | Eseguire [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database ed eseguire `composer update` dalla directory radice dell&#39;applicazione per aggiornare le dipendenze dei componenti |
| 2 | `magento setup:upgrade` è obbligatorio | [`magento setup:upgrade`](database-upgrade.md) per aggiornare lo schema del database |

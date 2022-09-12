---
title: Creare lo schema del database
description: Segui questi passaggi per creare un database per il tuo Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Creare lo schema del database

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Configurare il database e aggiungere dati

Utilizzo comando:

```bash
bin/magento setup:db-schema:upgrade
```

Per visualizzare lo stato del database, immettere

```bash
bin/magento setup:db:status
```

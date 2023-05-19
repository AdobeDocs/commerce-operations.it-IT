---
title: Creare lo schema del database
description: Per creare un database per il tuo Adobe Commerce o Magento Open Source, segui la procedura riportata di seguito.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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

Per visualizzare lo stato del database, immettere:

```bash
bin/magento setup:db:status
```

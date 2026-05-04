---
title: Creare lo schema del database
description: Per creare un database per il progetto Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Creare lo schema del database

Prima di eseguire questo comando, è necessario [creare o aggiornare la configurazione della distribuzione](deployment.md).

## Configurare il database e aggiungere dati

Utilizzo comando:

```shell
bin/magento setup:db-schema:upgrade
```

Per visualizzare lo stato del database, immettere:

```shell
bin/magento setup:db:status
```

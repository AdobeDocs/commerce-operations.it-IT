---
title: Processi Cron
description: Scopri i gruppi cron e come creare un processo cron personalizzato.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Processi Cron

In questi argomenti viene illustrato come impostare un processo cron personalizzato e, facoltativamente, un gruppo cron personalizzato. Se l’estensione Commerce richiede l’esecuzione periodica di attività pianificate, puoi utilizzare questi argomenti per impostare una cron _processo_ (l&#39;attività pianificata) e facoltativamente un cron _gruppo_, che esegue contemporaneamente attività personalizzate.

Se utilizzi un gruppo cron fornito da Commerce, non devi definire un gruppo cron personalizzato; tuttavia, se desideri che i processi cron vengano eseguiti con una pianificazione diversa o che vengano eseguiti tutti insieme, devi definire un gruppo cron

L’applicazione Commerce fornisce i seguenti gruppi cron:

- `default`, che contiene la maggior parte dei processi cron
- `index`, che aggiorna [indici](../cli/manage-indexers.md)
- `consumers`, che esegue la coda dei messaggi [consumatori](../cli/start-message-queues.md)
- Questi argomenti sono disponibili solo in Adobe Commerce
   - `staging`, che esegue [Relativo allo staging](https://docs.magento.com/user-guide/cms/content-staging.html) attività
   - `catalog_event`, che esegue le attività per target e le regole del carrello acquisti

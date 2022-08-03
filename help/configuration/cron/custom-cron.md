---
title: Processi Cron
description: Scopri i gruppi cron e creare un lavoro cron personalizzato.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# Processi Cron

Questi argomenti illustrano come impostare un lavoro cron personalizzato ed eventualmente un gruppo di cron personalizzato. Se l’estensione Commerce richiede l’esecuzione periodica di attività pianificate, puoi utilizzare questi argomenti per impostare un cron _lavoro_ (l&#39;attività pianificata) ed eventualmente un cron _gruppo_, che esegue attività personalizzate allo stesso tempo.

Se utilizzi un gruppo cron fornito con Commerce, non è necessario definire un gruppo cron personalizzato; tuttavia, se desideri che i tuoi lavori cron vengano eseguiti in una pianificazione diversa o desideri che vengano eseguiti tutti insieme, devi definire un gruppo cron

L’applicazione Commerce fornisce i seguenti gruppi principali:

- `default`, che contiene la maggior parte dei lavori cron
- `index`, che rinfresca [indicizzatori](../cli/manage-indexers.md)
- `consumers`, che esegue la coda dei messaggi [consumatori](../cli/start-message-queues.md)
- Questi argomenti sono disponibili solo in Adobe Commerce
   - `staging`, che esegue [Staging](https://docs.magento.com/user-guide/cms/content-staging.html) attività
   - `catalog_event`, che esegue attività per le regole di destinazione e carrello acquisti

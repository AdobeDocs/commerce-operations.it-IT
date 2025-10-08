---
title: Processi Cron
description: Scopri i gruppi cron e come creare processi cron personalizzati in Adobe Commerce. Scopri la configurazione dell’attività pianificata e del gruppo cron.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Processi Cron

In questi argomenti viene illustrato come impostare un processo cron personalizzato e, facoltativamente, un gruppo cron personalizzato. Se l&#39;estensione Commerce richiede l&#39;esecuzione periodica di attività pianificate, è possibile utilizzare questi argomenti per impostare un _processo_ cron (l&#39;attività pianificata) e, facoltativamente, un _gruppo_ cron, che esegue contemporaneamente attività personalizzate.

Se si utilizza un gruppo cron fornito da Commerce, non è necessario definire un gruppo cron personalizzato. Tuttavia, se si desidera che i processi cron vengano eseguiti con una pianificazione diversa o che vengano eseguiti tutti insieme, è necessario definire un gruppo cron

L&#39;applicazione Commerce fornisce i seguenti gruppi cron:

- `default`, che contiene la maggior parte dei processi cron
- `index`, che aggiorna [indici](../cli/manage-indexers.md)
- `consumers`, che esegue la coda di messaggi [consumer](../cli/start-message-queues.md)
- Questi argomenti sono disponibili solo in Adobe Commerce
   - `staging`, che esegue [Attività relative alla gestione temporanea](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging)
   - `catalog_event`, che esegue le attività per la destinazione e le regole del carrello acquisti

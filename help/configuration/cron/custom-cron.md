---
title: Processi Cron
description: Scopri i gruppi cron e come creare processi cron personalizzati in Adobe Commerce. Scopri la configurazione dell’attività pianificata e del gruppo cron.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
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
source-wordcount: '179'
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
  - `staging`, che esegue [Attività relative alla gestione temporanea](https://experienceleague.adobe.com/it/docs/commerce-admin/content-design/staging/content-staging)
  - `catalog_event`, che esegue le attività per la destinazione e le regole del carrello acquisti

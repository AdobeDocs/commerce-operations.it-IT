---
title: Best practice di configurazione per l’elaborazione degli ordini
description: Scopri le best practice di configurazione per migliorare le prestazioni di checkout e elaborazione degli ordini.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: fb30b18c9b9f6a9f538189eeafda9ee7a29d436c
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Best practice di configurazione per l’elaborazione degli ordini

Con l’aumento del volume degli ordini sui siti Commerce, puoi ottimizzare le prestazioni del checkout e l’elaborazione degli ordini abilitando le seguenti opzioni di configurazione dello store:

- **[!UICONTROL Asynchronous indexing]**- Abilita questa opzione per impedire i blocchi del database e l&#39;elaborazione rallentata che possono verificarsi quando un numero elevato di ordini viene inserito contemporaneamente.
- **[!UICONTROL Asynchronous email notifications]**- Abilita questa opzione per velocizzare le prestazioni del checkout inviando notifiche e-mail per l’elaborazione degli ordini a intervalli definiti, anziché inviarle immediatamente.
- **[!UICONTROL Enable Archiving]**- Abilita questa opzione per migliorare le prestazioni di ordini, fatture, spedizioni e note di credito e mantieni l&#39;area di lavoro priva di informazioni superflue, in modo da poter concentrarsi sull&#39;attività corrente. Vedi [Abilita archiviazione](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Abilitare l’elaborazione asincrona dell’ordine

I passaggi per abilitare l’elaborazione asincrona dell’ordine dipendono dalla modalità di distribuzione:

- Per Adobe Commerce su infrastrutture cloud e siti on-premise in modalità Produzione, utilizza il seguente comando CLI di Magento per abilitare l’indicizzazione asincrona:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Per i siti on-premise Adobe Commerce in modalità Predefinita o Produzione, abilita l’indicizzazione asincrona aggiornando la configurazione Grid Settings (Impostazioni griglia) nell’amministratore.

   Vedi [Abilita gli aggiornamenti programmati della griglia e la reindicizzazione](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Verifica sempre le modifiche di configurazione nell’ambiente di staging prima di aggiornare l’ambiente di produzione.

## Informazioni aggiuntive

- [Best practice di configurazione](../../../performance/configuration.md)
- [Riferimento a percorsi di configurazione generali e avanzati](../../../configuration/reference/config-reference-general.md)
- [Elaborazione dell&#39;ordine ad alta velocità](../../../performance/high-throughput-order-processing.md)

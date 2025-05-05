---
title: Best practice di configurazione per l’elaborazione degli ordini
description: Scopri le best practice di configurazione per migliorare le prestazioni di pagamento ed elaborazione degli ordini.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Best practice di configurazione per l’elaborazione degli ordini

Con l&#39;aumento del volume degli ordini nei siti Commerce, è possibile ottimizzare le prestazioni di pagamento e l&#39;elaborazione degli ordini abilitando le seguenti opzioni di configurazione dello store:

- **[!UICONTROL Asynchronous indexing]** - Abilitare questa opzione per evitare blocchi del database e rallentamenti dell&#39;elaborazione che possono verificarsi quando un numero elevato di ordini viene effettuato contemporaneamente.
- **[!UICONTROL Asynchronous email notifications]** - Abilitare questa opzione per velocizzare le prestazioni di estrazione inviando le notifiche e-mail di estrazione e di elaborazione dell&#39;ordine a intervalli definiti anziché inviarle immediatamente.
- **[!UICONTROL Enable Archiving]** - Abilitare questa opzione per migliorare le prestazioni di ordini, fatture, spedizioni e note di accredito e mantenere l&#39;area di lavoro libera da informazioni non necessarie, in modo da poter concentrarsi sulle attività correnti. Vedi [Abilita archiviazione](https://experienceleague.adobe.com/it/docs/commerce-admin/stores-sales/order-management/orders/order-archive).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Abilita elaborazione ordine asincrona

I passaggi per abilitare l’elaborazione asincrona dell’ordine dipendono dalla modalità di distribuzione:

- Per Adobe Commerce su infrastrutture cloud e siti locali in modalità di produzione, utilizza il seguente comando CLI di Magento per abilitare l’indicizzazione asincrona:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Per i siti Adobe Commerce locali in modalità predefinita o Produzione, abilita l’indicizzazione asincrona aggiornando la configurazione delle Impostazioni griglia in Amministratore.

  Vedi [Abilitare gli aggiornamenti pianificati della griglia e la reindicizzazione](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html?lang=it#enable-scheduled-grid-updates-and-reindexing)

  >[!WARNING]
  >
  >Prima di aggiornare l’ambiente di produzione, verifica sempre le modifiche alla configurazione nell’ambiente di staging.

## Informazioni aggiuntive

- [Best practice di configurazione](../../../performance/configuration.md)
- [Riferimento ai percorsi di configurazione generali e avanzati](../../../configuration/reference/config-reference-general.md)
- [Elaborazione degli ordini con throughput elevato](../../../performance/high-throughput-order-processing.md)

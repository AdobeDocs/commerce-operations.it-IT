---
title: Best practice per l’inserimento nell’elenco dei prodotti
description: Scopri come ottimizzare le prestazioni di Adobe Commerce gestendo il numero di prodotti visualizzati su ogni pagina del catalogo di vetrina.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per l’inserimento nell’elenco dei prodotti

Per ottenere prestazioni ottimali, visualizza un massimo di 48 prodotti per pagina.

Puoi configurare Adobe Commerce per consentire agli acquirenti di visualizzare tutti i prodotti di categoria su una singola pagina. Se il numero di prodotti di categoria supera in modo significativo i 48 prodotti, aggiorna la configurazione del catalogo per i controlli di impaginazione di vetrina.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Aggiornare la configurazione dell’elenco dei prodotti

Se hai più di 48 prodotti in qualsiasi categoria, aggiorna la configurazione del catalogo di vetrina per disabilitare l’opzione per **Consenti tutti i prodotti per pagina**.

Dopo aver disabilitato questa opzione, Adobe Commerce utilizza i controlli di impaginazione della vetrina per gestire il numero di prodotti che vengono visualizzati nei componenti della vetrina. Per istruzioni, consulta [Configurare i controlli di impaginazione](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Informazioni aggiuntive

- [Configurare gli elenchi di prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)

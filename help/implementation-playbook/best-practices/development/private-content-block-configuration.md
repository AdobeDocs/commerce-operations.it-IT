---
title: Best practice per i blocchi di contenuto privati
description: Scopri le best practice per configurare blocchi di contenuto privati per ottimizzare le prestazioni della vetrina.
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Best practice per i blocchi di contenuto privati

Quando un blocco di contenuto privato contiene `_isScopePrivate` , il blocco non è memorizzabile in cache. Poiché il blocco privato non è memorizzato in cache, Adobe Commerce deve recuperare gli stessi dati per ogni richiesta del cliente, il che aumenta il carico del server.

Invece di utilizzare `_isScopePrivate` per contenuti privati, crea un blocco e un modello per visualizzare dati indipendenti dall’utente. Questi dati vengono sostituiti con dati specifici dell’utente dal componente dell’interfaccia utente di Adobe Commerce, che gestisce in modo più efficiente i dati di pre-rendering. Per istruzioni, consulta [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) nel _[!DNL Commerce PHP Extensions Guide]_.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Potenziale impatto sulle prestazioni

Siti con blocchi di contenuto privati contenenti `_isScopePrivate` Le variabili attivano le richieste AJAX per recuperare gli stessi dati per ogni richiesta del cliente. Questo aumenta i tempi di risposta e utilizza risorse aggiuntive che potrebbero essere utilizzate per gestire operazioni più importanti per lo storefront, come la registrazione dei clienti, gli aggiornamenti del carrello, l’invio degli ordini e le transazioni di pagamento.

## Informazioni aggiuntive

- [Contenuto privato](../../../performance/configuration.md#client-side-optimization-settings)
- [Le richieste AJAX a throughput elevato causano prestazioni insoddisfacenti](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)

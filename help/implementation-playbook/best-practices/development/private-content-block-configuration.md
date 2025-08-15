---
title: Best practice per i blocchi di contenuto privati
description: Scopri le best practice per configurare blocchi di contenuto privati per ottimizzare le prestazioni della vetrina.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Best practice per i blocchi di contenuto privati

Quando un blocco di contenuto privato contiene la variabile `_isScopePrivate`, il blocco non è memorizzabile in cache. Poiché il blocco privato non è memorizzato in cache, Adobe Commerce deve recuperare gli stessi dati per ogni richiesta del cliente, il che aumenta il carico del server.

Invece di utilizzare la variabile `_isScopePrivate` per il contenuto privato, crea un blocco e un modello per visualizzare dati indipendenti dall&#39;utente. Questi dati vengono sostituiti con dati specifici dell’utente dal componente dell’interfaccia utente di Adobe Commerce, che gestisce in modo più efficiente i dati di pre-rendering. Per istruzioni, vedere [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in _[!DNL Commerce PHP Extensions Guide]_.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Potenziale impatto sulle prestazioni

I siti con blocchi di contenuto privati contenenti le variabili `_isScopePrivate` attivano le richieste di AJAX per recuperare gli stessi dati per ogni richiesta del cliente. Questo aumenta i tempi di risposta e utilizza risorse aggiuntive che potrebbero essere utilizzate per gestire operazioni più importanti per lo storefront, come la registrazione dei clienti, gli aggiornamenti del carrello, l’invio degli ordini e le transazioni di pagamento.

## Informazioni aggiuntive

- [Contenuto privato](../../../performance/configuration.md#client-side-optimization-settings)
- [Le richieste di AJAX con throughput elevato causano prestazioni insoddisfacenti](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)

---
title: Best practice per i blocchi di contenuto privati
description: Scopri le best practice per configurare blocchi di contenuto privati per ottimizzare le prestazioni di vetrina.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Best practice per i blocchi di contenuto privati

Quando un blocco di contenuto privato contiene `_isScopePrivate` il blocco non è memorizzabile nella cache. Poiché il blocco privato non è memorizzato nella cache, Adobe Commerce deve recuperare gli stessi dati per ogni richiesta del cliente che aumenta il carico del server.

Invece di utilizzare il `_isScopePrivate` per il contenuto privato, crea un blocco e un modello per visualizzare dati agnostici dell’utente. Questi dati vengono sostituiti con dati specifici dell’utente dal componente dell’interfaccia utente di Adobe Commerce, che gestisce i dati di pre-rendering in modo più efficiente. Per istruzioni, consulta [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in _[!DNL Commerce PHP Extensions Guide]_.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Impatto potenziale sulle prestazioni

Siti con blocchi di contenuto privati contenenti `_isScopePrivate` le variabili attivano richieste AJAX per recuperare gli stessi dati per ogni richiesta del cliente. Questo aumenta il tempo di risposta e utilizza risorse aggiuntive che potrebbero essere utilizzate per gestire operazioni di vetrina più importanti per il business, come la registrazione dei clienti, gli aggiornamenti del carrello, l&#39;invio degli ordini e le transazioni di pagamento.

## Informazioni aggiuntive

- [Contenuto privato](../../../performance/configuration.md#client-side-optimization-settings)
- [Le richieste di AJAX ad alto throughput causano prestazioni scadenti](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)



---
title: Best practice per i blocchi contenuto privati
description: Scopri best practice per la configurazione di blocchi di contenuto privati al fine di ottimizzare le prestazioni della vetrina del negozio.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Best practice per i blocchi contenuto privati

Quando un blocco contenuto privato contiene la `_isScopePrivate` variabile, il blocco non è memorizzabile in cache. Poiché il blocco privato non è memorizzato nella cache, Adobe Systems Commerce deve recuperare gli stessi dati per ogni cliente richiesta il che aumenta il carico del server.

Invece di utilizzare la variabile per contenuto `_isScopePrivate` privati, crea un blocco e un modello per visualizzare i dati indipendenti dal utente. Questi dati vengono sostituiti con dati utente specifici dal componente interfaccia Adobe Systems Commerce, che gestisce i dati di pre-rendering in modo più efficiente. Per istruzioni, vedere [Contenuto](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) privato in _[!DNL Commerce PHP Extensions Guide]_.

## Prodotti e versioni interessati

[Tutte le versioni](../../../release/versions.md) supportate di:

- Adobe Systems Commerce su infrastruttura cloud
- Adobe Systems Commerce locale

## Potenziale impatto sulle prestazioni

Sites che hanno blocchi di contenuto privati contenenti le variabili attivano AJAX `_isScopePrivate` richieste per recuperare gli stessi dati per ogni richiesta del cliente. Ciò aumenta i tempi di risposta e utilizza risorse aggiuntive che potrebbero essere utilizzate per gestire più operazioni di vetrina critico aziendali come registrazione clienti, aggiornamenti del carrello acquisti, invio degli ordini e transazioni di pagamento.

## Informazioni aggiuntive

- [Contenuto privato](../../../performance/configuration.md#client-side-optimization-settings)
- [Un throughput elevato AJAX richieste causa prestazioni ridotte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html?lang=it)

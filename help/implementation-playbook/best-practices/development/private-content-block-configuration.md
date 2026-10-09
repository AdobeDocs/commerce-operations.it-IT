---
title: Best practice per i blocchi di contenuto privati
description: Scopri le best practice per configurare blocchi di contenuto privati per ottimizzare le prestazioni della vetrina.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Best practice per i blocchi di contenuto privati

Quando un blocco di contenuto privato contiene la variabile `_isScopePrivate`, il blocco non è memorizzabile in cache. Poiché il blocco privato non è memorizzato in cache, Adobe Commerce deve recuperare gli stessi dati per ogni richiesta del cliente, il che aumenta il carico del server.

Invece di utilizzare la variabile `_isScopePrivate` per il contenuto privato, crea un blocco e un modello per visualizzare dati indipendenti dall&#39;utente. Questi dati vengono sostituiti con dati specifici dell’utente dal componente dell’interfaccia utente di Adobe Commerce, che gestisce in modo più efficiente i dati di pre-rendering. Per istruzioni, vedere [Contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content) in _[!DNL Commerce PHP Extensions Guide]_.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Potenziale impatto sulle prestazioni

I siti con blocchi di contenuto privati contenenti le variabili `_isScopePrivate` attivano le richieste di AJAX per recuperare gli stessi dati per ogni richiesta del cliente. Questo aumenta i tempi di risposta e utilizza risorse aggiuntive che potrebbero essere utilizzate per gestire operazioni più importanti per lo storefront, come la registrazione dei clienti, gli aggiornamenti del carrello, l’invio degli ordini e le transazioni di pagamento.

## Informazioni aggiuntive

- [Contenuto privato](../../../performance/configuration.md#client-side-optimization-settings)
- [Blocchi privati e memorizzabili in cache](https://developer.adobe.com/commerce/php/development/cache/page/private-content#cacheable-and-private-blocks) in _[!DNL Commerce PHP Extensions Guide]_

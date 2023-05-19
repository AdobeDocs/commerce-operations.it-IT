---
title: Allineamento dell’infrastruttura Adobe Commerce e Adobe Experience Manager
description: Allinea l’infrastruttura Adobe Commerce e Adobe Experience Manager per impostare timeout e limiti di connessione accettabili.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Allineamenti dell’infrastruttura (timeout e limiti di connessione)

Esistono impostazioni con AEM e Adobe Commerce e l’infrastruttura circostante, come i load balancer, che richiedono un allineamento, relative ai limiti di connessione e alle impostazioni di timeout.

Un disallineamento tra questi limiti significherebbe che le connessioni potrebbero finire per essere limitate sul lato AEM, mentre Adobe Commerce è in grado di gestire più connessioni. Allo stesso modo, per le impostazioni di timeout, un disallineamento potrebbe indicare che si verificano errori di timeout sul lato AEM, mentre Adobe Commerce sta ancora elaborando una richiesta.

Per le impostazioni di timeout, le impostazioni devono essere riviste e allineate per evitare errori di timeout 503 durante il caricamento. Sono disponibili diverse impostazioni di timeout dell’infrastruttura e dell’applicazione da rivedere:

![Schema numerato che descrive i timeout e i limiti di connessione per l’AEM](../assets/commerce-at-scale/timeout-settings.svg)

## Bilanciatore di carico AEM

Supponendo che nell’infrastruttura siano presenti un load balancer per applicazioni AWS e più dispatcher/publisher, è necessario considerare le seguenti impostazioni per il load balancer:

1. È necessario rivedere i controlli di integrità dell’editore per evitare che i dispatcher abbandonino inutilmente il servizio prima delle impennate di carico. Le impostazioni di timeout del controllo di integrità del load balancer devono essere allineate alle impostazioni di timeout del publisher.

   ![Schermata che mostra i controlli di integrità del load balancer AEM](../assets/commerce-at-scale/health-checks.png)

1. È possibile disabilitare la fedeltà del gruppo target del Dispatcher e utilizzare l’algoritmo di bilanciamento del carico Round Robin. Ciò presuppone che non siano utilizzate funzionalità specifiche per l’AEM o sessioni utente per l’AEM che richiedano l’impostazione della fedeltà di sessione. Presuppone che la gestione dell’accesso utente e della sessione sia disponibile solo in Adobe Commerce tramite GraphQL.

   ![Schermata che mostra gli attributi di adesività della sessione AEM](../assets/commerce-at-scale/session-stickiness.png)

1. Tieni presente che se abiliti la persistenza della sessione, ciò potrebbe causare la mancata memorizzazione in cache delle richieste Fastly, poiché per impostazione predefinita Fastly non memorizza in cache le pagine con l’intestazione Set-Cookies. Adobe Commerce imposta i cookie anche sulle pagine memorizzabili in cache (TTL > 0), ma l’impostazione predefinita Fastly VCL elimina tali cookie sulle pagine memorizzabili in cache per consentire il funzionamento del caching Fastly. Se le pagine non vengono memorizzate in cache, controlla eventuali cookie personalizzati in uso, carica il file Fastly VCL e ricontrolla il sito.

## Impostazioni di timeout di Dispatcher

L’opzione /timeout nelle opzioni di &quot;rendering&quot; del dispatcher specifica il timeout di connessione per accedere all’istanza di pubblicazione dell’AEM, espresso in millisecondi. Questa impostazione deve essere rivista e l’impostazione predefinita &quot;0&quot; (timeout indefinito) deve essere utilizzata se è presente un load balancer separato per gestire le impostazioni di timeout.

Se nell’infrastruttura non è presente alcun load balancer, le impostazioni di timeout devono essere specificate nelle impostazioni /timeout di Dispatcher, con un valore corrispondente alle impostazioni di timeout di GraphQL nell’editore.

## Editori

Limiti di connessione e timeout di Publisher GraphQL: inizialmente, il numero massimo di connessioni HTTP nelle impostazioni OSGI di Adobe Commerce CIF GraphQL Client Configuration Factory deve essere impostato sul numero massimo di connessioni Fastly predefinito, attualmente impostato su 200. Anche se nella farm dell’AEM sono presenti più editori, il limite deve essere impostato allo stesso modo per ogni editore, in base all’impostazione Fastly. Il motivo è che in alcuni casi un editore potrebbe gestire più traffico degli altri editori, ad esempio se un dispatcher associato viene rimosso dalla farm. Questo significherebbe che tutto il traffico verrà instradato attraverso il singolo dispatcher e gli editori rimanenti; in questo caso, il singolo editore potrebbe quindi aver bisogno di tutte le connessioni HTTP.

Il &quot;metodo HTTP predefinito&quot; deve essere impostato da POST a GET. Nella cache di Adobe Commerce GraphQL vengono memorizzate solo le richieste GET, pertanto il metodo predefinito deve essere sempre impostato su GET.

Il timeout della connessione http e il timeout del socket http devono essere impostati su un valore corrispondente al timeout Fastly.

L&#39;immagine seguente mostra il Magento CIF GraphQL Client Configuration Factory. Le impostazioni mostrate di seguito sono solo esempi e devono essere regolate caso per caso:

![Schermata delle impostazioni di configurazione del framework di integrazione Commerce](../assets/commerce-at-scale/cif-config.png)

Le immagini seguenti mostrano le configurazioni di back-end Fastly. Le impostazioni mostrate di seguito sono solo esempi e devono essere regolate caso per caso:

![Schermata delle impostazioni di configurazione dell’amministratore Commerce per Fastly](../assets/commerce-at-scale/cif-config-advanced.png)

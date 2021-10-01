---
title: Allineamento dell'infrastruttura Adobe Commerce e Adobe Experience Manager
description: Allinea la tua infrastruttura Adobe Commerce e Adobe Experience Manager per impostare timeout e limiti di connessione accettabili.
source-git-commit: 6ad72d5110ae3e3a7cf341282f2af9b700874f09
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---


# Allineamenti dell&#39;infrastruttura (timeout e limiti di connessione)

Esistono impostazioni con AEM e Commerce Adobe e infrastrutture circostanti, come i load balancer che necessitano di allineamento, che sono correlati ai limiti di connessione e alle impostazioni di timeout.

Un disallineamento tra questi limiti significherebbe che le connessioni potrebbero finire per essere limitate AEM lato, mentre il commercio Adobe è in grado di gestire più connessioni. Analogamente, per le impostazioni di timeout, un disallineamento potrebbe significare che si verificano errori di timeout AEM lato, mentre Adobe Commerce sta ancora elaborando una richiesta.

Per le impostazioni di timeout, le impostazioni devono essere riviste e allineate in modo da evitare che vengano visualizzati errori di timeout 503 durante il caricamento. Sono disponibili diverse impostazioni di timeout dell&#39;infrastruttura e dell&#39;applicazione da esaminare:

![Diagramma numerato che descrive timeout e limiti di connessione per AEM](../assets/commerce-at-scale/timeout-settings.svg)

## Bilanciamento del carico AEM

Supponendo che nell’infrastruttura sia presente un load balancer dell’applicazione AWS e che siano presenti più dispatcher/editori, per il load balancer devono essere considerate le seguenti impostazioni:

1. I controlli di integrità degli editori devono essere rivisti per evitare che i dispatcher abbandonino il servizio in modo inutilmente precoce a causa di ondate di carico. Le impostazioni di timeout del controllo di integrità del load balancer devono essere allineate con le impostazioni di timeout dell’editore.

   ![Schermata che mostra i controlli di integrità del load balancer AEM](../assets/commerce-at-scale/health-checks.png)

1. È possibile disabilitare l’accostamento al gruppo di destinazione del Dispatcher e utilizzare l’algoritmo di bilanciamento del carico di Round Robin. Ciò presuppone che non vi siano funzionalità specifiche AEM o sessioni utente AEM utilizzate che richiederebbero l’impostazione dello stickiness delle sessioni. Si parte dal presupposto che la gestione dell’accesso e delle sessioni degli utenti sia disponibile solo su Adobe Commerce tramite GraphQL.

   ![Schermata che mostra gli attributi di persistenza AEM sessione](../assets/commerce-at-scale/session-stickiness.png)

1. Nota che se abiliti l’accostamento della sessione, questo potrebbe causare la mancata memorizzazione in cache delle richieste in Flast, come per impostazione predefinita, Flast non memorizza in cache le pagine con l’intestazione Set-Cookies. Adobe Commerce imposta i cookie anche su pagine memorizzabili in cache (TTL > 0), ma il codice Flast VCL predefinito li elimina sulle pagine memorizzabili in cache per il corretto funzionamento della memorizzazione in cache. Se le pagine non vengono memorizzate nella cache, controlla eventuali cookie personalizzati che puoi utilizzare e carica anche Flast VCL e ricontrolla il sito.

## Impostazioni di timeout del dispatcher

Le opzioni /timeout nel dispatcher &quot;renders&quot; specificano il timeout di connessione che accede all’istanza di pubblicazione AEM in millisecondi. Questo deve essere rivisto e l&#39;impostazione predefinita di &quot;0&quot; (timeout indefinito) deve essere utilizzata se è presente un load balancer separato per gestire le impostazioni di timeout.

Se nell’infrastruttura non è presente alcun load balancer, le impostazioni di timeout devono essere specificate nelle impostazioni /timeout del dispatcher, con un valore che corrisponde alle impostazioni di timeout GraphQL nell’editore.

## Editori

Limiti e timeout della connessione GraphQL di Publisher: Inizialmente, le connessioni HTTP massime nelle impostazioni OSGI di Adobe Commerce CIF GraphQL Client Configuration Factory devono essere impostate sul limite massimo di connessioni Flast predefinito, attualmente impostato su 200. Anche se nella farm AEM sono presenti più editori, il limite deve essere impostato allo stesso modo per ogni editore, in base all’impostazione Flast. Il motivo è che in alcuni casi, un editore potrebbe gestire più traffico rispetto agli altri editori, ad esempio se un dispatcher associato viene rimosso dalla farm. Questo significa che tutto il traffico verrebbe instradato attraverso il singolo dispatcher ed editori rimanenti, in questo caso il singolo editore potrebbe avere bisogno di tutte le connessioni HTTP.

Il &quot;metodo HTTP predefinito&quot; deve essere impostato da POST a GET. Solo le richieste di GET sono memorizzate nella cache di Adobe Commerce GraphQL e pertanto il metodo predefinito deve sempre essere impostato su GET.

Il timeout della connessione http e il timeout del socket http devono essere impostati su un valore che corrisponda al timeout finale.

L’immagine seguente mostra il Magento CIF GraphQL Client Configuration Factory. Le impostazioni mostrate qui sono solo esempi e devono essere regolate caso per caso:

![Schermata delle impostazioni di configurazione del framework di integrazione Commerce](../assets/commerce-at-scale/cif-config.png)

Le immagini seguenti mostrano le configurazioni di back-end Flast. Le impostazioni mostrate qui sono solo esempi e devono essere regolate caso per caso:

![Schermata delle impostazioni di configurazione di Commerce Admin per Flast](../assets/commerce-at-scale/cif-config-advanced.png)

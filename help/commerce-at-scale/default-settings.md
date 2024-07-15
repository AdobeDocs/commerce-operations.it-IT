---
title: Ottimizzazione delle prestazioni di Adobe Commerce
description: Prepara il progetto Adobe Commerce per utilizzare Adobe Experience Manager as a CMS modificando alcune impostazioni predefinite.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Ottimizzazione delle prestazioni di Adobe Commerce

## Ubicazione geografica dell’AEM e infrastruttura Adobe Commerce

Per ridurre la latenza tra l’editore dell’AEM e Adobe Commerce GraphQL durante la creazione delle pagine, il provisioning iniziale delle due infrastrutture separate deve essere ospitato nella stessa area AWS (o Azure). Anche la posizione geografica scelta per entrambi i cloud dovrebbe essere la più vicina alla maggior parte della base di clienti, in modo che le richieste GraphQL lato client vengano gestite da una posizione geograficamente vicina alla maggior parte dei clienti.

## Memorizzazione in cache di GraphQL in Adobe Commerce

Quando il browser dell’utente o l’editore dell’AEM chiama il GraphQL di Adobe Commerce, alcune chiamate verranno memorizzate nella cache
in Fastly. Le query memorizzate nella cache sono generalmente quelle che contengono dati non personali e che probabilmente non cambiano spesso. Ad esempio: categorie, categoryList e prodotti. Quelli che non sono esplicitamente memorizzati nella cache sono quelli che cambiano regolarmente e se memorizzati nella cache potrebbero rappresentare rischi per i dati personali e le operazioni del sito, ad esempio query come cart e customerPaymentTokens.

GraphQL consente di eseguire più query in una singola chiamata. È importante notare che se specifichi una sola query che Adobe Commerce non memorizza in cache insieme a molte altre che non possono essere memorizzate in cache, Adobe Commerce ignorerà la cache per tutte le query nella chiamata. Questo aspetto deve essere tenuto in considerazione dagli sviluppatori quando combinano più query per garantire che le query potenzialmente memorizzabili nella cache non vengano involontariamente ignorate‡.

>[!NOTE]
>
> Per ulteriori informazioni sulle query memorizzabili nella cache e non memorizzabili nella cache, consulta la [documentazione per gli sviluppatori](https://devdocs.magento.com/guides/v2.4/graphql/caching.html) di Adobe Commerce.

## Tabella a schermo piatto catalogo

Non è raccomandato l’uso di tabelle piatte per prodotti e categorie. L’utilizzo di questa funzione obsoleta può causare deterioramenti delle prestazioni e problemi di indicizzazione, pertanto il catalogo flat deve essere disabilitato tramite l’amministratore Adobe Commerce, nella sezione storefront. Alcuni moduli e personalizzazioni di terze parti richiedono il corretto funzionamento delle tabelle sequenziali: si consiglia di effettuare una valutazione per comprendere gli impatti e i rischi associati alla necessità di utilizzare le tabelle sequenziali quando si sceglie di utilizzare queste estensioni o personalizzazioni.

## Schermatura di origine rapida

Per impostazione predefinita, la schermatura dell’origine Fastly non è abilitata. Lo scopo della schermatura dell’origine di Fastly è quello di ridurre il traffico direttamente verso l’origine Adobe Commerce: quando viene ricevuta una richiesta, Fastly Edge Location (o &quot;punto di presenza&quot; / POP) controlla i contenuti memorizzati in cache e li fornisce. Se non è memorizzato in cache, continua fino a Shield POP per verificare se è memorizzato in cache (se il contenuto è stato precedentemente richiesto anche da un altro POP globale, verrà memorizzato in cache). Infine, se non viene memorizzato nella cache dello Shield POP, solo allora si passerà al server Origin.

La schermatura dell’origine rapida può essere abilitata nelle impostazioni di back-end della configurazione Fastly dell’amministratore di Adobe Commerce. Per ottenere le migliori prestazioni, è necessario scegliere la posizione dello schermo più vicina al centro dati di origine di Adobe Commerce.

## Ottimizzazione rapida delle immagini

Una volta abilitata la schermatura dell’origine Fastly, questo consente di attivare anche Fastly Image Optimizer. Dove le immagini del catalogo dei prodotti sono memorizzate su Adobe Commerce, questo servizio consente di scaricare sull’origine Fastly e off dall’origine Adobe Commerce tutte le immagini del catalogo dei prodotti, ad uso intensivo di risorse, che vengono trasformate. Anche i tempi di risposta dell’utente finale sono migliorati per i tempi di caricamento delle pagine, in quanto le immagini vengono trasformate nella posizione edge di, il che elimina la latenza riducendo il numero di richieste all’origine Adobe Commerce.

L’ottimizzazione Fastly Image può essere abilitata &quot;abilita l’ottimizzazione deep image&quot; nella configurazione Fastly in admin, anche se solo dopo l’attivazione dello schermo di origine. Ulteriori dettagli sulle configurazioni per l&#39;ottimizzazione Fastly Image sono disponibili nella [documentazione per gli sviluppatori](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) di Adobe Commerce.

![Schermata delle impostazioni di ottimizzazione immagine Fastly nell&#39;amministrazione di Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Disabilita moduli inutilizzati

Se esegui Adobe Commerce headless, distribuendo le richieste solo tramite l’endpoint GraphQL e non viene distribuita alcuna pagina store front-end direttamente da Adobe Commerce, molti moduli diventano ridondanti e non vengono utilizzati. Disattivando i moduli inutilizzati, la base di codice di Adobe Commerce diventa più piccola, meno complessa e potrebbe quindi offrire miglioramenti delle prestazioni. La disattivazione dei moduli su Adobe Commerce può essere gestita tramite Compositore. Quali moduli possono essere disabilitati dipendono dai requisiti del sito; pertanto, non è possibile fornire un elenco consigliato, in quanto sarebbe specifico per l’implementazione di Adobe Commerce da parte di ciascun cliente.

## Attivazione connessione MySQL e Redis

Per impostazione predefinita, le connessioni MySQL e Redis Slave non sono attivate in Adobe Commerce sul cloud. Questo perché queste impostazioni sono adatte solo ai clienti che si aspettano un carico molto elevato. La latenza Cross-AZ (cross-Availability Zones) è più elevata con le connessioni slave attivate; pertanto, questa impostazione riduce effettivamente le prestazioni di un’istanza Adobe Commerce su un’istanza cloud nel caso in cui l’istanza riceva solo livelli di carico regolari.

Se l&#39;istanza di Adobe Commerce prevede un carico estremo, l&#39;attivazione di master-slave per MySQL e Redis contribuirà alle prestazioni distribuendo il carico sul database MySQL o Redis su nodi diversi.

Come guida, negli ambienti con carico normale, l’abilitazione di Connessioni slave rallenterà le prestazioni del 10-15%. Tuttavia, nei cluster con carico e traffico elevati, le prestazioni aumentano del 10-15% circa. Pertanto, è importante eseguire un test di carico dell’ambiente con i livelli di traffico previsti per valutare se questa impostazione sarebbe utile per i tempi di prestazioni in condizioni di carico.

Per abilitare/disabilitare le connessioni slave per mysql e redis, è necessario modificare il file `.magento.env.yaml` in modo che includa quanto segue:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Per l’architettura in scala (architettura divisa, vedi sotto), le connessioni slave Redis non devono essere abilitate, in quanto questo causerebbe la visualizzazione di errori. Nel caso di un’architettura divisa, si consiglia invece di implementare il caching L2 per Redis.

## Passaggio a un’architettura Adobe Commerce su cloud scalata (suddivisa)

Se dopo tutte le configurazioni di cui sopra, i risultati del test di carico o l’analisi delle prestazioni dell’infrastruttura live indicano ancora che i livelli di carico per Adobe Commerce sono di un livello che massimizza in modo coerente la CPU e altre risorse di sistema, è necessario prendere in considerazione il passaggio a un’architettura scalata (divisa).

Con un’architettura Pro standard, sono disponibili 3 nodi, ciascuno dei quali contiene uno stack tecnologico completo. Convertendo in architettura a livello diviso, questo cambia in un minimo di 6 nodi: 3 dei quali contengono Elasticsearch, MariaDB, Redis e altri servizi core; gli altri 3 per l&#39;elaborazione del traffico web contengono phpfpm e NGINX. Sono disponibili maggiori possibilità di scalabilità con livelli divisi: i nodi principali contenenti database possono essere scalati verticalmente; i nodi web possono essere scalati orizzontalmente e verticalmente, offrendo una grande flessibilità per espandere l’infrastruttura su richiesta per un determinato periodo di elevata attività di carico e su nodi in cui sono necessarie risorse aggiuntive.

Se è stato deciso di passare a un’architettura a livello diviso a causa di pesanti aspettative di carico per il sito, è necessario avviare una discussione con il team dell’account Adobe sui passaggi necessari per abilitare questa funzionalità.

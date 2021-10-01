---
title: Ottimizzazione delle prestazioni di Adobe Commerce
description: Prepara il tuo progetto Adobe Commerce per utilizzare Adobe Experience Manager as a CMS modificando alcune impostazioni predefinite.
source-git-commit: 63f153365398c3ae7dc7e6214b67705c8a4c7686
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ottimizzazione delle prestazioni di Adobe Commerce

## Posizione geografica dell&#39;infrastruttura AEM e di Adobe Commerce

Per ridurre la latenza tra l’editore AEM e Commerce GraphQL di Adobe durante la creazione di pagine, il provisioning iniziale delle due infrastrutture separate deve essere ospitato all’interno della stessa area AWS (o Azure). Anche la posizione geografica scelta per entrambi i cloud dovrebbe essere più vicina alla maggior parte della base clienti, in modo che le richieste GraphQL lato client vengano servite da una posizione geograficamente vicina alla maggior parte dei clienti.

## Memorizzazione in cache di GraphQL in Adobe Commerce

Quando il browser dell’utente o l’editore di AEM chiama GraphQL di Adobe Commerce, alcune chiamate verranno memorizzate nella cache
Flast. Le query memorizzate nella cache sono generalmente quelle che contengono dati non personali e che non possono essere modificate spesso. Ad esempio: categorie, categoryList e prodotti. Quelli che non sono esplicitamente memorizzati nella cache sono quelli che cambiano regolarmente e se memorizzati nella cache possono comportare rischi per i dati personali e le operazioni sul sito, ad esempio query come cart e customerPaymentTokens.

GraphQL ti consente di eseguire più query in una singola chiamata. È importante notare che se specifichi anche una query per cui Adobe Commerce non memorizza in cache con molti altri che non sono memorizzabili in cache, Adobe Commerce ignorerà la cache per tutte le query nella chiamata. Questo dovrebbe essere considerato dagli sviluppatori quando si combinano più query per garantire che le query potenzialmente memorizzabili nella cache non vengano ignorate accidentalmente da .

>[!NOTE]
>
> Per ulteriori informazioni sulle query memorizzabili in cache e non memorizzabili in cache, consulta la documentazione per gli sviluppatori Adobe Commerce [](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Tabella a forma piatto del catalogo

Si sconsiglia l&#39;uso di tabelle piatte per prodotti e categorie. L’utilizzo di questa funzione obsoleta può causare degradazioni delle prestazioni e problemi di indicizzazione, pertanto il catalogo piatto deve essere disabilitato tramite l’amministratore di Adobe Commerce, nella sezione storefront. Alcuni moduli e personalizzazioni di terze parti richiedono il corretto funzionamento delle tabelle piatte. È consigliabile eseguire una valutazione per comprendere gli impatti e i rischi associati all’utilizzo di tabelle piatte quando si sceglie di utilizzare queste estensioni o personalizzazioni.

## Schermatura all&#39;origine

Per impostazione predefinita, la schermatura dell&#39;origine Flast non è abilitata. Lo scopo della schermatura dell’origine di Flast è quello di ridurre il traffico direttamente verso l’origine del Commercio Adobe: quando viene ricevuta una richiesta, una posizione Flast edge (o &quot;punto di presenza&quot; / POP) controlla il contenuto memorizzato nella cache e lo fornisce. Se non è memorizzato nella cache, continua a selezionare l’opzione POP schermatura per verificare se è memorizzato nella cache (se il contenuto è stato precedentemente richiesto anche da un altro POP globale, verrà memorizzato nella cache). Infine, se non è memorizzato nella cache del POP dello scudo, passerà solo al server Origin.

La protezione dell’origine può essere abilitata nelle impostazioni di back-end della configurazione amministratore di Commerce di Adobe. Scegli una posizione di protezione più vicina al datacenter di origine Adobe Commerce per ottenere le migliori prestazioni.

## Ottimizzazione delle immagini

Una volta che la schermatura dell&#39;origine è abilitata, questo consente anche di attivare Flast Image Optimizer. Se le immagini del catalogo dei prodotti sono memorizzate in Adobe Commerce, questo servizio consente di scaricare tutta l’elaborazione della trasformazione delle immagini del catalogo dei prodotti ad uso intensivo di risorse su Fwide e off dall’origine Commerce di Adobe. I tempi di risposta dell’utente finale vengono migliorati anche per i tempi di caricamento delle pagine, in quanto le immagini vengono trasformate nella posizione edge, eliminando la latenza riducendo il numero di richieste fino all’origine Adobe Commerce.

L&#39;ottimizzazione delle immagini finali può essere attivata &quot;abilitando l&#39;ottimizzazione profonda delle immagini&quot; nella configurazione Flast in admin, anche se solo dopo l&#39;attivazione dello scudo di origine. Maggiori dettagli sulle configurazioni per l&#39;ottimizzazione Flast Image sono disponibili nella documentazione per gli sviluppatori Adobe Commerce [](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Schermata delle impostazioni di ottimizzazione delle immagini Flast nell’amministratore di Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Disattivazione dei moduli non utilizzati

Se si esegue Adobe Commerce headless, solo per il server delle richieste tramite l’endpoint GraphQL e non vengono servite pagine di archivio front-end direttamente da Adobe Commerce, molti moduli diventano ridondanti e non vengono utilizzati. Disabilitando i moduli non utilizzati, la base di codice Commerce di Adobe diventa più piccola, meno complessa e potrebbe quindi offrire miglioramenti delle prestazioni. La disattivazione dei moduli su Adobe Commerce può essere gestita tramite il compositore. I moduli che possono essere disattivati dipendono dai requisiti del sito e quindi non è possibile fornire un elenco consigliato in quanto sarebbe specifico per l’implementazione di Commerce di Adobe da parte di ogni cliente.

## Attivazione connessione MySQL e Redis

Per impostazione predefinita, le connessioni MySQL e Redis Slave non vengono attivate in Adobe Commerce su cloud. Questo perché queste impostazioni sono adatte solo ai clienti che si aspettano un carico molto elevato. La latenza Cross-AZ (Cross-Availability Zones) è più alta con le connessioni slave attivate e quindi questa impostazione in realtà riduce le prestazioni di un Adobe Commerce sull&#39;istanza cloud nel caso in cui l&#39;istanza stia ricevendo solo livelli di carico regolari.

Se l&#39;istanza Commerce di Adobe prevede un carico estremo, l&#39;attivazione di master-slave per MySQL e Redis contribuirà alle prestazioni distribuendo il carico sul database MySQL o su Redis tra nodi diversi.

Come guida, negli ambienti con carico normale, l’abilitazione di Connessioni slave rallenta le prestazioni del 10-15%. Ma sui cluster con carico e traffico pesanti, c&#39;è un aumento delle prestazioni di circa il 10-15%. Pertanto, è importante caricare l’ambiente con i livelli di traffico previsti per valutare se questa impostazione sarebbe vantaggiosa per i tempi di prestazioni in condizioni di carico.

Per abilitare/disabilitare le connessioni slave per mysql e redis, devi modificare il file `.magento.env.yaml` in modo da includere quanto segue:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Per l’architettura scalata (architettura divisa - vedi di seguito), le connessioni slave Redis non devono essere abilitate, in quanto ciò causerà errori. Nel caso di un’architettura divisa, si consiglia invece di implementare la memorizzazione in cache L2 per Redis.

## Passaggio a un’architettura Adobe Commerce su cloud scaled (split)

Se dopo tutte le configurazioni di cui sopra, i risultati dei test di carico o l&#39;analisi delle prestazioni dell&#39;infrastruttura in tempo reale indicano ancora che i livelli di carico su Adobe Commerce sono di un livello che compensa in modo coerente la CPU e altre risorse di sistema, allora deve essere considerato un passaggio a un&#39;architettura in scala (divisa).

Con un&#39;architettura Pro standard, ci sono 3 nodi, ciascuno dei quali contiene uno stack di tecnologia completo. Convertendo in architettura a livello suddiviso, questo diventa almeno 6 nodi: 3 dei quali contengono Elasticsearch, MariaDB, Redis e altri servizi di base; gli altri 3 per l&#39;elaborazione del traffico web contengono phpfpm e NGINX. Ci sono maggiori possibilità di scalabilità con livello di divisione: i nodi di base contenenti database possono essere ridimensionati verticalmente; i nodi web possono essere ridimensionati orizzontalmente e verticalmente, offrendo un&#39;ampia flessibilità per espandere l&#39;infrastruttura su richiesta per un determinato periodo di elevata attività di caricamento e su nodi in cui sono necessarie risorse aggiuntive.

Se è stata presa la decisione di passare a un’architettura a livello suddiviso a causa di grandi aspettative di carico per il sito, è necessario discutere con il Customer Success Manager i passaggi necessari per abilitare questa opzione.
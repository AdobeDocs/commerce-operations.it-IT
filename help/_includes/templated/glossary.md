---
source-git-commit: 405c1d7073e5936aefc7fb3c6eb1d5dd4d69a066
workflow-type: tm+mt
source-wordcount: '6574'
ht-degree: 0%

---
# Glossario di Adobe Commerce

## A

### sopra la piega

_aggettivo_

In una finestra del browser, il contenuto visibile immediatamente dopo il caricamento di una pagina web e prima che un utente scorra la pagina.
Durante la progettazione del layout, utilizza formati flessibili per visualizzare al meglio i prodotti, le caratteristiche, le vendite, le notifiche, le opzioni e così via con la massima priorità in questo settore.

Con dispositivi mobili e tablet, l&#39;area sopra la piega differisce notevolmente, specialmente per quanto riguarda le dimensioni e le dimensioni dello schermo e l&#39;orientamento durante la visualizzazione (verticale rispetto orizzontale).
L’utilizzo di temi e test reattivi può aiutare a trovare la giusta combinazione di contenuti e layout.

_Attributi del termine:_

* _Campo: progettazione_

### ramo attivo

_sostantivo_

Un ramo o un ambiente attivo è un ramo connesso a un&#39;istanza implementata o in esecuzione con accesso ai servizi.
Quando si disattiva, la connessione ai servizi e all&#39;istanza in esecuzione viene rimossa, ma il codice viene mantenuto.
Diventa un ramo git ordinario.

_Attributi del termine:_

* _Campo: cloud_

### adattatore

_sostantivo_

Classe che consente a due sistemi altrimenti incompatibili di lavorare insieme senza modificare il codice sorgente del sistema.
Gli esempi includono adattatori di database, adattatori di cache, adattatori di filesystem, adattatori di librerie post-processore e altri tipi di schede di elaborazione.

_Attributi del termine:_

* _Campo: programmazione_

### admin

_sostantivo_

Nel software, un ruolo utente con privilegi di amministratore completi per gestire tutte le funzionalità.
In Adobe Commerce, gli utenti amministratori hanno autorizzazioni complete e accesso a tutte le funzioni, opzioni e funzionalità dell’amministratore.
Possono anche creare utenti e ruoli.

Ulteriori informazioni: [Aggiunta di utenti](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Attributi del termine:_

* _Campo: software commerce_
* _Sinonimi: amministratore, super utente_
* _Termini correlati: amministratore di commercio_

### Area amministratore

_sostantivo_

Il back office protetto da password del tuo negozio dove vengono gestiti ordini, catalogo, contenuti e configurazioni.
Gli utenti possono accedere all’area Amministratore per gestire lo store, inclusi prodotti, ordini, spedizioni, contenuti CMS, progettazione della vetrina, informazioni sui clienti e così via.
Gli utenti amministratori hanno un ruolo associato alle autorizzazioni che controllano l’accesso a funzioni, opzioni e funzionalità.

Ulteriori informazioni: [Guida utente di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributi del termine:_

* _Campo: software commerce_
* _Sinonimi: Amministrazione, pannello di amministrazione, back-end, interfaccia di amministrazione, interfaccia di amministrazione_
* _Termini correlati: admin_

### Variabili AMMINISTRATORE

_sostantivo_

Le variabili AMMINISTRATORE sono variabili dell’ambiente di progetto che consentono di ignorare le impostazioni di configurazione per l’account utente amministratore per accedere all’interfaccia utente amministratore.

Ulteriori informazioni: [Variabili AMMINISTRATORE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Attributi del termine:_

* _Campo: amministratore, cloud_

### adminhtml

_sostantivo_

Nome dell&#39;area interna assegnata all&#39;amministratore.

Ulteriori informazioni: [Guida utente di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: area, amministrazione commerce_

### area

_sostantivo_

Area è un termine astratto per un ambito applicazione Magento.
Le aree sono componenti logici che organizzano il codice per l’elaborazione ottimizzata delle richieste.
Le aree riducono i requisiti di memoria degli oggetti di configurazione a cui si accede dalla vetrina e semplificano le chiamate al servizio Web caricando solo il codice dipendente richiesto.
Ogni area può contenere codice completamente diverso per elaborare URL e richieste.

Le aree di Adobe Commerce includono:

* Amministratore (amministratore)
* Vetrina
* REST API Web (webapi_rest)

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: componente commercio, vetrina_

### attributo

_sostantivo_

Caratteristica o proprietà di un prodotto che descrive alcuni aspetti del prodotto.
Gli utenti di Adobe Commerce o Magento Open Source possono creare attributi personalizzati da aggiungere al set di attributi predefinito o a un set di attributi personalizzato.
Crea questi attributi tramite l’amministratore o a livello di programmazione.
Esempi: colore, dimensione, peso, prezzo, età, genere e così via.

Gli attributi personalizzati sono un tipo di attributo Entity-Attribute-Value (EAV).

Per integrazioni come Google Shopping ads Channel e Amazon Sales Channel, mappa gli attributi Commerce in attributi di terze parti per visualizzare e vendere correttamente prodotti, annunci di visualizzazione.

Ulteriori informazioni: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Sinonimi: attributo di prodotto, attributo personalizzato_
* _Termini correlati: attributo di estensione_

### gruppo di attributi

_sostantivo_

Un raggruppamento logico di attributi all’interno di un set di attributi.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: attributo_

### insieme di attributi

_sostantivo_

Una raccolta di gruppi di attributi personalizzati per un prodotto specifico.
Esempio: Un set di attributi di T-shirt può includere colore, dimensioni, genere e marchio.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: attributo_

### costo medio delle scorte

_sostantivo_

Prezzo del prodotto, meno coupon o sconti, più le tasse di trasporto e applicabili.
La media viene determinata aggiungendo ogni mese il costo iniziale delle scorte, più il costo finale delle scorte per l&#39;ultimo mese del periodo.

_Attributi del termine:_

* _Campo: prodotto, prezzo, inventario_

## B

### valuta di base

_sostantivo_

La valuta principale utilizzata per visualizzazione store per tutti i pagamenti online.
I negozi possono accettare valute provenienti da più di 200 paesi in tutto il mondo.
La vetrina fornisce un selettore di valuta per più valute accettate per un paese o impostazioni internazionali specifici.
I simboli di valuta vengono visualizzati nei prezzi dei prodotti e nei documenti di vendita, ad esempio ordini e fatture.
È possibile personalizzare i simboli di valuta in base alle esigenze e impostare la visualizzazione del prezzo separatamente per ogni negozio o vista.

Ulteriori informazioni: [Valuta](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Attributi del termine:_

* _Campo: prezzo_

### elaborazione batch

_sostantivo_

Per eseguire un&#39;attività o modificare più elementi contemporaneamente, senza ripetizioni manuali.

_Attributi del termine:_

* _Campo: programmazione_
* _Sinonimi: operazioni alla rinfusa_

### blocco

_sostantivo_

Unità di output della pagina che esegue il rendering di contenuti distintivi, ovvero informazioni, un elemento dell’interfaccia utente, qualsiasi elemento visivamente tangibile per l’utente finale.
[Blocchi](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) sono implementati e forniti da moduli.
I blocchi utilizzano i modelli per generare HTML.
Esempi di blocchi includono un elenco di categorie, un mini carrello, tag di prodotto e un elenco di prodotti.

[Blocchi dinamici](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) fornire contenuti in base alla logica, ad esempio regole di prezzo.

Page Builder amplia l’interattività e la creazione di [blocchi](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) e [blocchi dinamici](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Attributi del termine:_

* _Campo: software commerce_
* _Sinonimi: Blocchi dinamici_
* _Termini correlati: blocco cms, blocco statico, contenitore, layout_

### brand

_sostantivo, verbo_

Un&#39;identità univoca che definisce un prodotto o un gruppo specifico di prodotti dal produttore o da Designer.
Tra questi figurano marchi di denominazione per abbigliamento, elettrodomestici, articoli di lusso e così via.
La tua azienda può anche essere il marchio, vendere prodotti con più marchi in base alla business unit, al pubblico target e così via.

Utilizza gli attributi personalizzati per salvare le informazioni sul marchio per i prodotti.

Alcune estensioni e integrazioni possono utilizzare o richiedere un marchio per i tuoi prodotti, come Google Shopping ads Channel e Amazon Sales Channel.

_Attributi del termine:_

* _Campo: business_

### muratore

_aggettivo_

Un&#39;attività al dettaglio con una posizione fisica permanente, in contrapposizione a quelle che funzionano virtualmente o unicamente tramite Internet.

Per [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) e [Gestione degli ordini](https://omsdocs.magento.com/getting-started/terminology/), questo negozio è un&#39;origine per il tracciamento delle quantità di prodotti, degli ordini di spedizione e per il supporto del ritiro in negozio.

_Attributi del termine:_

* _Campo: business, inventario_

### operazioni alla rinfusa

_sostantivo_

Le operazioni in blocco sono azioni eseguite su larga scala.
Ad esempio, le operazioni in serie includono l&#39;importazione o l&#39;esportazione di articoli, la modifica dei prezzi su scala di massa e l&#39;assegnazione di prodotti a un magazzino.

Ulteriori informazioni: [Operazioni in blocco DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Attributi del termine:_

* _Campo: programmazione_

### prodotto combinato

_sostantivo_

Consente ai clienti di assemblare un prodotto personalizzabile &quot;costruisci autonomamente&quot; da varie opzioni e configurazioni.
Ogni elemento del bundle è un prodotto semplice o virtuale separato.

Ulteriori informazioni: [Prodotti configurabili](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: prodotto semplice, prodotto virtuale, tipi di prodotto_

### estensione bundle

_sostantivo_

Il codice che estende o personalizza il comportamento di Adobe Commerce è considerato un’estensione Bundled.
Può includere moduli, temi e Language Pack.

_Attributi del termine:_

* _Campo: estensione bundle, estensione_
* _Sinonimi: estensione_
* _Termini correlati: estensione, estensione bundle fornitore_

## C

### backend cache

_sostantivo_

Memorizza i record della cache in un sistema back-end a due livelli all&#39;interno del framework predefinito di Zend.
Una cache di primo livello è veloce, ad esempio un backend APC o Memcache, ma è limitata e non supporta l’assegnazione di tag e il raggruppamento delle voci di cache.
Una cache di secondo livello, ad esempio un file system o un backend Redis, è più lenta ma supporta l’assegnazione di tag e il raggruppamento.

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: backend_

### frontali della cache

_sostantivo_

Specifica il tipo di dati memorizzato nel backend della cache.

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: frontale_

### tipo di cache

_sostantivo_

Una cache memorizza i dati in modo che le chiamate future per tali dati vengano caricate più rapidamente.

Adobe Commerce include i seguenti tipi:
* Configurazione
* Layout
* Uscita HTML a blocchi
* Dati raccolta
* Dati di riflessione
* Operazioni DDL database
* Configurazione compilata
* Tipi e attributi EAV
* Notifica al cliente
* Configurazione delle integrazioni
* Configurazione API Integrations
* Cache pagina (la più nota)
* Configurazione servizi web
* Traduzioni
* Regola di destinazione
* Google Product Cache
* Vertex

È possibile creare e definire altri tipi.

_Attributi del termine:_

* _Campo: programmazione_

### catturare

_verbo_

Processo di conversione di un importo dell&#39;ordine autorizzato in una transazione fatturabile.
Le transazioni non possono essere acquisite fino a quando non sono state autorizzate e le autorizzazioni non possono essere acquisite fino a quando i beni o i servizi non sono stati spediti.

_Attributi del termine:_

* _Campo: business_
* _Termini correlati: autorizzazione, stato dell&#39;ordine_

### titolare della carta

_sostantivo_

Persona autorizzata da un istituto finanziario a effettuare acquisti su un conto di carte di credito.

_Attributi del termine:_

* _Campo: business, ordine_

### regole del carrello

_sostantivo_

Regole di prezzo applicate al carrello e che attivano un&#39;azione in risposta a un set di condizioni.
Utilizzato per creare promozioni.

_Attributi del termine:_

* _Campo: software di commercio, prezzi, prodotti_
* _Termini correlati: regole del catalogo, carrello_

### catalogo

_sostantivo_

Per i commercianti, il catalogo rappresenta il loro inventario dei prodotti.
Nell’architettura di Adobe Commerce, il catalogo è costituito da categorie, prodotti e attributi di prodotto.

Ogni negozio Commerce dispone di un solo catalogo di prodotti, condiviso da tutte le viste Store.
In un&#39;installazione multi-store, ogni negozio può avere un catalogo separato o condividere il catalogo.
Il catalogo store corrente è determinato dalla categoria principale predefinita, visibile all&#39;utente nella navigazione superiore (menu principale) dello store.
(Il termine &quot;categoria principale&quot; può confondere, perché la &quot;categoria principale&quot; non è in realtà una categoria, ma un contenitore per il menu, che è costituito da categorie e sottocategorie.)

È possibile creare tutte le categorie principali desiderate, ma è possibile utilizzarne una sola (impostazione predefinita) alla volta.

_Attributi del termine:_

* _Campo: software di commercio, prezzi, prodotti_
* _Termini correlati: catalogo condiviso, regola di catalogo_

### regole del catalogo

_sostantivo_

Regole di prezzo applicate a prodotti specifici e che attivano un&#39;azione in risposta a un insieme di condizioni.
Utilizzato per creare promozioni.

_Attributi del termine:_

* _Campo: software di commercio, prezzi, prodotti_
* _Termini correlati: regole del carrello, catalogo_

### categoria

_sostantivo_

Un gruppo di prodotti che hanno qualcosa in comune.
Il menu principale del negozio è organizzato in categorie e sottocategorie di prodotti.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_

### pagamento

_sostantivo_

Il processo di raccolta delle informazioni di pagamento e spedizione necessarie per completare l&#39;acquisto di articoli nel carrello.
Dopo che il cliente esamina le informazioni e invia l’ordine, viene inviata al cliente una conferma e-mail.

L’acquisto dispone di molte opzioni e configurazioni pronte all’uso e tramite estensione .

Ulteriori informazioni: [Esercitazione sull’estrazione](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Attributi del termine:_

* _Campo: business, design, ordine, prodotto, programmazione_

### variabili cloud

_sostantivo_

Le variabili cloud sono variabili d’ambiente specifiche di Adobe Commerce sull’infrastruttura cloud e utilizzano l’ **`MAGENTO_CLOUD`** Prefisso.

Ulteriori informazioni: [Variabili cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Attributi del termine:_

* _Campo: cloud_

### Blocco CMS

_sostantivo_

Una variante speciale di [blocco](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) che può essere creato solo nell&#39;amministratore e non può essere referenziato tramite file di layout.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: blocco statico_

### dati complessi

_sostantivo_

Dati associati a più opzioni di prodotto.

_Attributi del termine:_

* _Campo: programmazione_

### component

_sostantivo_

Utilizzato per fare riferimento a un modulo, un tema o un pacchetto di linguaggio in Adobe Commerce.

_Attributi del termine:_

* _Campo: software commerce_
* _Sinonimi: component_
* _Termini correlati: componente interfaccia_

### prodotto configurabile

_sostantivo_

Un prodotto configurabile assomiglia a un singolo prodotto con elenchi a discesa di opzioni per ogni variante.
Ogni opzione è in realtà un prodotto semplice separato con una SKU unica, che consente di monitorare l&#39;inventario per ogni variazione di prodotto.
Per ottenere un effetto simile, è possibile utilizzare un prodotto semplice con opzioni personalizzate, ma senza la possibilità di tenere traccia dell’inventario per ogni variante.
I prodotti con più opzioni sono talvolta denominati prodotti compositi.

Anche se un prodotto configurabile utilizza più SKU e inizialmente potrebbe richiedere un po&#39; più di tempo per la configurazione, può risparmiare tempo alla fine.
Se prevedi di incrementare la tua attività, il tipo di prodotto configurabile potrebbe essere una scelta migliore per un prodotto con più opzioni.

Esempio: T-shirt che sono disponibili in due colori e tre dimensioni.
Sei varianti devono essere create come singoli prodotti (ciascuna con la propria SKU).
Quindi, tutte le varianti vengono aggiunte a un prodotto configurabile in cui i clienti possono scegliere la dimensione e il colore, quindi aggiungerlo al carrello.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: tipi di prodotto_

### tasso di conversione

_sostantivo_

La percentuale di visitatori convertiti in acquirenti.

_Attributi del termine:_

* _Campo: business, ordine_

### scalabilità a livello principale

_sostantivo_

Il ridimensionamento del livello di base è costituito da tre nodi di servizio per l’archiviazione dei dati, la cache e i servizi, come OpenSearch, Elasticsearch, MariaDB, Redis.

_Attributi del termine:_

* _Campo: cloud_

### nota di accredito

_sostantivo_

Documento rilasciato dal commerciante al cliente per la cancellazione di un saldo in essere a causa di sovrattassa, sconto o restituzione di beni.
Il promemoria ripristina i fondi sul conto del cliente.

_Attributi del termine:_

* _Campo: business, ordine_

### commento nota di credito

_sostantivo_

Dettagli del motivo per cui un importo per memoria di credito è stato accreditato al cliente.

_Attributi del termine:_

* _Campo: business, ordine_

### voce nota di accredito

_sostantivo_

Articolo fatturato per il quale un commerciante crea una nota di accredito.

_Attributi del termine:_

* _Campo: business, ordine_

### vendere

_sostantivo, aggettivo, verbo_

Prodotto visualizzato accanto al carrello.
Quando un cliente accede alla pagina del carrello, questi prodotti vengono visualizzati come venduti incrociati agli articoli già presenti nel carrello.
Sono simili agli acquisti di impulso, come riviste e caramelle ai registri di cassa nei negozi di alimentari.

_Attributi del termine:_

* _Campo: business, prodotto_
* _Termini correlati: upselling_

### CVM

_sostantivo_

Abbreviazione del &quot;metodo di verifica del titolare della carta&quot;.
Un modo per verificare l&#39;identità del cliente confermando un codice di sicurezza della carta di credito a 3 o 4 cifre con il responsabile del pagamento.

_Attributi del termine:_

* _Campo: business, ordine_
* _Sinonimi: Metodo di verifica del titolare della carta_
* _Termini correlati: codice di sicurezza_

## D

### schema di database

_sostantivo_

Struttura dei dati in un database.
Definisce la modalità di organizzazione dei dati e la modalità di gestione delle relazioni con i dati, compresi tutti i vincoli applicati ai dati.
Un modulo può contenere frammenti dello schema del database se tale modulo contiene dati che devono essere memorizzati nel database.

_Attributi del termine:_

* _Campo: programmazione_
* _Sinonimi: schema_

### iniezione di dipendenza

_sostantivo_

Un modello di progettazione software che consente a una classe di specificare le proprie dipendenze senza doverle costruire.
Questa classe delega la responsabilità di inserire la dipendenza nella classe chiamante.
Utilizzato per semplificare i test.
Per definire le dipendenze per le classi, modifica il file di configurazione di di.xml.

_Attributi del termine:_

* _Campo: programmazione_

### chiave di distribuzione

_sostantivo_

Una chiave di distribuzione è la chiave pubblica SSH del tuo progetto e consente l’accesso in sola lettura o in lettura/scrittura (se abilitato) a un archivio Git.

Ulteriori informazioni: [Connessioni protette](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Attributi del termine:_

* _Campo: cloud_

### doppio consenso

_sostantivo, verbo_

Un processo di verifica dell’e-mail che richiede ai potenziali abbonati di completare un secondo passaggio che conferma la loro intenzione di effettuare l’abbonamento.

_Attributi del termine:_

* _Campo: business_

### prodotto scaricabile

_sostantivo_

Prodotto scaricabile digitalmente costituito da uno o più file scaricati, ad esempio eBook, musica, video, applicazioni software o un aggiornamento.
È possibile offrire un album in vendita e vendere ogni singola canzone.
Un prodotto scaricabile può fornire una versione elettronica del catalogo dei prodotti.

I file scaricabili possono risiedere sul server o essere forniti come URL a qualsiasi altro server o rete di distribuzione dei contenuti.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: tipi di prodotto_

### contenuto dinamico

_sostantivo_

Contenuto generato dal codice anziché letto da un modello statico.
Una volta eseguito inizialmente il rendering del contenuto dinamico quando un utente visita una pagina, a volte il contenuto può essere memorizzato nella cache e riutilizzato senza che sia necessario un’altra chiamata dinamica per una revisione.

_Attributi del termine:_

* _Campo: progettazione_
* _Termini correlati: php_

### URL di elementi multimediali dinamici

_sostantivo_

Indirizzo URL generato dinamicamente dal sistema per fare riferimento a un&#39;immagine o ad altri contenuti multimediali.
L’indirizzo si collega direttamente alle risorse memorizzate su un server o su una rete di distribuzione dei contenuti.
Per utilizzare un URL statico, modifica l’impostazione di configurazione.
Tuttavia, se al momento della disattivazione dell’impostazione gli URL del file multimediale dinamico vengono inclusi nel catalogo, ogni riferimento nel catalogo diventa un collegamento non funzionante.
I collegamenti possono essere ripristinati abilitando nuovamente gli URL di contenuti multimediali dinamici.
L’utilizzo degli URL di contenuti multimediali dinamici può influire sulle prestazioni di ricerca del catalogo.

Formato del codice: media url=&quot;path/to/image.jpg&quot;

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: rete di distribuzione dei contenuti, url_

## E

### pacchetto ece-tools

_sostantivo_

Un set di script e strumenti progettati per gestire e distribuire l’applicazione Commerce. Questo pacchetto semplifica molti processi Adobe Commerce nei processi dell’infrastruttura cloud, tra cui la distribuzione in un ambiente Docker, la gestione dei cronometri, la verifica della configurazione del progetto e l’applicazione di patch di Adobe.

Ulteriori informazioni: [pacchetto ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Attributi del termine:_

* _Campo: cli, cloud, distribuzione_

### entity

_sostantivo_

Unità o oggetto univoco nella programmazione.
Contiene attributi o parametri che possono essere modificati.
Gli esempi includono la gestione temporanea, in cui un aggiornamento può modificare entità quali regole di prezzo, prodotti o categorie, e record di database, in cui i contratti di servizio includono strutture di dati inviate e ricevute.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: attributo, regole del carrello, regole del catalogo_

### valore dell&#39;attributo dell&#39;entità

_sostantivo_

Per le entità di database, un modello dati che codifica in modo efficiente le entità.
Memorizza l’ID entità, il nome attributo e il valore come triplo, consentendo la creazione di nuovi nomi di attributi di entità in qualsiasi momento.
Nella codifica, il numero di attributi che possono essere utilizzati per descrivere le entità può essere esteso, ma il numero che si applica a una determinata entità viene ridotto a icona.
Questo modello dati è flessibile, ma può essere lento.

Ulteriori informazioni: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributi del termine:_

* _Campo: programmazione_
* _Sinonimi: eav_

### contenuto sempreverde

_sostantivo_

Contenuti che possono essere riutilizzati per una lunga durata o per contenuti.

_Attributi del termine:_

* _Campo: business_

### estensione

_sostantivo_

Codice che estende o personalizza il comportamento di Adobe Commerce.
Facoltativamente, puoi creare un pacchetto e distribuire un&#39;estensione su Commerce Marketplace o su un altro sistema di distribuzione dell&#39;estensione.
Un’estensione Commerce può includere moduli, temi e Language Pack.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: componente, modulo, pacchetto_

### attributo di estensione

_sostantivo_

Estendi le funzionalità e utilizza spesso tipi di dati più complessi rispetto agli attributi personalizzati. Questi attributi non vengono visualizzati sull&#39;interfaccia grafica.

Ulteriori informazioni: [Aggiunta di attributi di estensione all’entità](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: attributo, valore dell’attributo dell’entità_

## F

### merci a bordo

_sostantivo_

Nel trasporto marittimo internazionale, questo termine significa che la parte ricevente è responsabile delle spese di spedizione.
La FOB può essere basata sul luogo di origine o di destinazione ed essere designata come raccolta merci o come merce prepagata.

_Attributi del termine:_

* _Campo: business, ordine, prezzi_
* _Sinonimi: fesso_

### frontale

_aggettivo_

In un&#39;applicazione client-server sono presenti il backend e il front-end.
Il componente front-end, o client, è un’interfaccia che consente agli utenti di manipolare o interagire con il codice backend sottostante.
Il codice di backend viene eseguito su un server.
Un utente non può accedere direttamente al codice backend.
Un utente interagisce con la vetrina, che a sua volta utilizza il codice in esecuzione sul server Commerce.

Nota: In passato, la vetrina è stata definita &quot;front&quot; e l’amministratore è stato indicato come &quot;back-end&quot;. Questo utilizzo non è più supportato.

_Attributi del termine:_

* _Campo: progettazione, programmazione_
* _Sinonimi: lato client_
* _Termini correlati: back-end, vetrina, front-end cache_

### proprietà frontend

_sostantivo_

Proprietà che determinano la presentazione e il comportamento di un attributo dal punto di vista del cliente nel tuo negozio.

_Attributi del termine:_

* _Campo: progettazione, programmazione_

### realizzazione

_sostantivo_

Il processo di gestione delle spedizioni dei clienti.

_Attributi del termine:_

* _Campo: business_

## G

### carta regalo

_sostantivo_

Una carta o un certificato regalo prepagato che può essere utilizzato per effettuare acquisti nel negozio.
A ogni carta regalo viene assegnato un codice univoco che viene inserito al momento del pagamento.
Il valore della carta regalo si riflette nel saldo del conto della carta regalo.
Ci sono tre tipi di carte regalo:

* Le carte regalo &quot;fisiche&quot; possono essere prodotte da materiale plastico o di carta, spedite al cliente.
* Le carte regalo &quot;virtuali&quot; vengono inviate via e-mail.
* Le carte regalo &quot;combinate&quot; sono una combinazione dei due, spedite al destinatario come una carta fisica e anche consegnate via e-mail.
Le carte regalo sono configurabili, comprese le opzioni per l’idoneità del prodotto e la selezione di importi aperti o fissi.

Su richiesta del cliente, l&#39;amministratore del negozio può riscattare una carta regalo anche quando l&#39;ordine viene creato nel backend.

Le carte regalo aiutano anche le promozioni, in quanto gli amministratori del negozio possono creare manualmente gli account della carta regalo nel backend e inviare i codici della carta regalo al segmento di cliente specifico.
Le carte regalo possono fungere da programma fedeltà mirato ai clienti più attivi che effettuano numerosi acquisti dal web store o una specifica campagna promozionale durante le vacanze.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: tipi di prodotto_

### margine lordo

_sostantivo_

La differenza tra il costo e il prezzo di un prodotto.

_Attributi del termine:_

* _Campo: business_

### prodotto raggruppato

_sostantivo_

Un tipo di prodotto con diversi prodotti simili e autonomi raggruppati su una singola pagina.
Può essere offerto con varianti di un singolo prodotto o raggruppandole per stagione o per tema per creare un set coordinato.
Ogni prodotto può essere acquistato separatamente o come parte del gruppo.

Ad esempio, per un coltello disponibile in quattro dimensioni, tutti e quattro i coltelli possono essere visualizzati in una pagina di prodotto raggruppata.
I clienti possono selezionare le dimensioni desiderate e aggiungerle al carrello da questa pagina.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: prodotto semplice, tipi di prodotto_

## H

### impugnatura

_sostantivo_

In genere, un handle è un modo per fare riferimento a un oggetto.
In Adobe Commerce, le maniglie vengono utilizzate in molte posizioni, più comunemente per identificare una pagina.
Per gli handle di pagina, il nome dell&#39;handle viene derivato dall&#39;URL, quindi utilizzato per individuare e caricare i file di layout per la pagina a cui si fa riferimento.
Ad esempio, nel modulo Cliente è presente un file di layout denominato &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Qui &quot;frontend&quot; è il nome dell’area e &quot;checkout_cart_index&quot; è il nome dell’handle, entrambi derivati dall’URL.

_Attributi del termine:_

* _Campo: programmazione_
* _Sinonimi: handle di pagina_

### scala orizzontale

_sostantivo_

Il ridimensionamento orizzontale (noto anche come ridimensionamento) è il processo di aggiunta di nodi o macchine aggiuntivi all&#39;infrastruttura per soddisfare la crescente domanda.

_Attributi del termine:_

* _Campo: cloud_

## I

### intercettazione

_sostantivo_

Il processo di inserimento di un nuovo codice prima, dopo o intorno a una funzione pubblica esistente di una classe PHP.

Per intercettare una funzione, un plug-in implementa il codice aggiuntivo da richiamare.
I plug-in sono associati ai punti di intercettazione dal file di configurazione dell’iniezione di dipendenza (di.xml).
Se più plug-in sono definiti sulla stessa funzione, la configurazione dell’iniezione di dipendenza definisce l’ordine in cui vengono richiamati i plug-in, consentendo l’utilizzo senza conflitti di più plug-in.

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: spina_

## L

### layout

_sostantivo_

Nella costruzione di una pagina Commerce, un layout è una serie di blocchi assemblati in una gerarchia che rappresenta la struttura della pagina.

I file di layout di pagina si concentrano sul livello più alto di struttura della pagina (intestazione, piè di pagina, area contenuto principale, barra laterale sinistra e così via).
I file di layout assemblano quindi i contenuti (blocchi) in queste diverse aree della pagina.

_Attributi del termine:_

* _Campo: software di progettazione, commercio_
* _Termini correlati: istruzioni di layout, blocco_

### istruzioni di layout

_sostantivo_

Marcatura in un file di layout che descrive le modifiche da applicare a una struttura di elementi strutturati composta da blocchi, contenitori e componenti dell’interfaccia utente.
Un singolo file di layout può contenere più istruzioni di layout.
Le istruzioni di layout sono codificate in XML nei file di layout.

_Attributi del termine:_

* _Campo: progettazione, programmazione_
* _Termini correlati: layout, blocco, contenitore, componente ui_

### aggiornamento del layout

_sostantivo_

Utilizzato per snippet di codice aggiunti per modificare il layout XML o per importare le istruzioni di layout da un altro file.

_Attributi del termine:_

* _Campo: software di progettazione, commercio_

### Proprietario licenza

_sostantivo_

Il Titolare della licenza (noto anche come Proprietario account) è la persona designata in un&#39;organizzazione aziendale che gestisce i pagamenti e altri problemi aziendali relativi all&#39;account Adobe Commerce sull&#39;infrastruttura cloud.
Questa persona funge da punto di contatto con l&#39;Adobe.
Dopo l’acquisto di un abbonamento a un’infrastruttura cloud da parte di un’azienda, l’accesso iniziale al progetto e al codice è disponibile solo per la persona designata come proprietario della licenza.

_Attributi del termine:_

* _Campo: business_

## M

### MAGEID

_sostantivo_

MAGEID è in genere il contatto di fatturazione sull’account Adobe Commerce (e potrebbe non essere il proprietario del progetto Adobe Commerce sul progetto di infrastruttura cloud).
Per poter accedere ad Adobe Commerce e Adobe Commerce sui pacchetti di infrastruttura cloud, devi utilizzare le chiavi di accesso associate a un MAGEID a cui è stato concesso l’accesso.

Ulteriori informazioni: [Ottieni le chiavi di autenticazione](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Attributi del termine:_

* _Campo: software commerce_

### markup

_sostantivo_

Nel settore del marketing e della vendita al dettaglio, una percentuale aggiunta al costo di un articolo per determinare il prezzo al dettaglio.
[Configurare il markup](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html)o markdown di un prodotto tramite opzioni personalizzabili del prodotto.

In fase di sviluppo, un linguaggio computer che controlla l&#39;elaborazione, la presentazione e la formattazione del testo.
Inoltre, i tag di marcatura sono frammenti di codice che aggiungono funzionalità o contenuto a una pagina o a un blocco CMS.

_Attributi del termine:_

* _Campo: business, programmazione_
* _Sinonimi: Markdown_

### ambiente principale

_sostantivo_

Su Adobe Commerce su infrastruttura cloud, i progetti Pro utilizzano un ambiente Platform as a Service (PaaS) attivo denominato master che include una copia del database dell’ambiente di produzione e del server web.

_Attributi del termine:_

* _Campo: cloud_

### conto commerciale

_sostantivo_

Conto presso una banca o un istituto finanziario che consente di accettare transazioni con carta di credito.

_Attributi del termine:_

* _Campo: business_

### MFTF

_sostantivo_

Il sistema multilaterale di negoziazione è [Framework di test funzionale](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Fornisce un framework di test per sviluppatori Commerce e ingegneri software, come specialisti QA, sviluppatori PHP e integratori di sistema.
Gli sviluppatori e il controllo qualità possono scrivere test per tentare le interazioni degli utenti con applicazioni web, verificare le funzionalità e automatizzare i test di regressione.

_Attributi del termine:_

* _Campo: software commerce, programmazione_
* _Termini correlati: blocco cms, blocco statico, contenitore, layout_

### modulo

_sostantivo_

Codice che modifica o estende le funzionalità fornite dall&#39;applicazione Magento.
Un modulo è contenuto in una struttura di directory che contiene file PHP e XML (configurazione, blocchi, controller, helper, modelli e così via) relativi a una funzionalità specifica per fornire una raccolta distinta di funzionalità di prodotto.
Lo scopo di ciascun modulo è quello di fornire caratteristiche specifiche del prodotto implementando nuove funzionalità o estendendo le funzionalità di altri moduli.
Ciascun modulo è progettato per funzionare in modo indipendente, in modo che l’inclusione o l’esclusione di un particolare modulo non influisca sulla funzionalità di altri moduli.

Un modulo può anche implementare i widget, che sono elementi di pagina che possono essere personalizzati dagli utenti aziendali in Admin.

I moduli possono essere disattivati o rimossi senza interrompere la coerenza dell’applicazione di Magento.
Un&#39;eccezione: Quando il modulo dipende da altri moduli, che richiede la disattivazione o la rimozione dei moduli dipendenti.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: php, xml, blocco_

## O

### OMS

_sostantivo_

[OMS](https://omsdocs.magento.com) è l&#39;offerta Adobe Order Management System.

OMS è una soluzione flessibile ed economica per la gestione, la vendita e la realizzazione delle scorte da qualsiasi canale di vendita.
OMS offre una customer experience senza soluzione di continuità, che aumenta le vendite riducendo i costi e accelera i tempi di commercializzazione.

Le funzionalità OMS includono:

* Visibilità globale e gestione di tutto l&#39;inventario
* Possibilità di spedire da e verso qualsiasi luogo
* Servizio clienti più semplice e reattivo
* Migliore esperienza cliente e fedeltà

Ulteriori informazioni: [Guida introduttiva ad OMS](https://omsdocs.magento.com/en/getting-started/), [Sito della documentazione OMS](https://omsdocs.magento.com/en/)

_Attributi del termine:_

* _Campo: funzionalità, software commerce, gestione ordini_
* _Sinonimi: gestione degli ordini, MOM, sistema di gestione degli ordini, Magento Order Management_
* _Termini correlati: gestione degli ordini_

### occultamento dell&#39;origine

_sostantivo_

Il cloaking dell’origine è una funzione di sicurezza che consente ad Adobe Commerce sull’infrastruttura cloud di bloccare qualsiasi traffico non Flast per prevenire attacchi DDoS, passando all’infrastruttura cloud (origine).

Ulteriori informazioni: [FST di origine cloaking](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Attributi del termine:_

* _Campo: sicurezza_
* _Termini correlati: firewall per applicazioni web_

## P

### Page Builder

_sostantivo_

Page Builder è un’estensione Commerce per la creazione di pagine ricche di contenuti tramite trascinamento e rilascio di controlli predefiniti per definire layout personalizzati.
Questi controlli sono noti anche come &quot;tipi di contenuto&quot;.
I commercianti possono progettare layout e pagine senza esperienza di codifica.
Il supporto per le estensioni è fornito agli sviluppatori per estendere Page Builder.

Ulteriori informazioni: [Guida utente di Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [DevDocs di Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Attributi del termine:_

* _Campo: software di commercio, progettazione_
* _Sinonimi: Amministrazione, pannello di amministrazione, back-end, interfaccia di amministrazione, interfaccia di amministrazione_
* _Termini correlati: admin_

### gateway dei pagamenti

_sostantivo_

Un gateway di pagamento è un servizio di terze parti che elabora senza soluzione di continuità le transazioni con carta di credito senza che il cliente lasci il sito del commerciante.

_Attributi del termine:_

* _Campo: business, ordine, programmazione_

## R

### prodotto correlato

_sostantivo_

Una selezione di prodotti presentata come incentivo all’acquisto di articoli aggiuntivi.
Ad esempio, se il cliente sta visualizzando la pagina del prodotto di una telecamera, i prodotti correlati potrebbero includere altre telecamere simili, una custodia per telecamera e un treppiede.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_

## S

### regole di vendita

_sostantivo_

Include le regole del carrello e del catalogo, che vengono utilizzate per determinare il prezzo di un prodotto per le promozioni.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: regole del carrello, regole del catalogo_

### scope

_sostantivo_

In Adobe Commerce, l&#39;ambito descrive l&#39;estensione della gerarchia di archiviazione che può influenzare un&#39;impostazione.
L&#39;ambito di applicazione può essere applicato ai seguenti elementi:

* Globale: tutti i siti web, i negozi e le visualizzazioni store
* Sito web — il sito web selezionato e tutti i negozi e le viste store sotto di esso
* Archivia: lo store selezionato e tutte le viste store al suo interno
* Vista store — la vista store selezionata.

All’interno della gerarchia, le impostazioni applicate a un livello inferiore possono sovrascrivere alcune impostazioni di livello superiore.

_Attributi del termine:_

* _Campo: software commerce_

### contratto di servizio

_sostantivo_

Un set di interfacce PHP definite per un modulo.
Un contratto di servizio include interfacce di dati che conservano l’integrità dei dati e interfacce di servizio, che nascondono i dettagli della logica di business ai richiedenti di servizi quali controller, servizi web e altri moduli.
Le API web possono essere associate a contratti di servizio tramite file di configurazione.

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: php, web api_

### insediamento

_sostantivo_

Il regolamento si verifica quando la banca incorporante e i fondi di cambio dell&#39;emittente e i proventi sono depositati nel conto dell&#39;esercente.

_Attributi del termine:_

* _Campo: business_

### Catalogo condiviso

_sostantivo_

Funzione che consente ai commercianti di creare un catalogo che può fungere da catalogo intero o da sottoinsieme di esso, e quindi di assegnare prezzi personalizzati per uno o più prodotti.
I commercianti possono quindi assegnare questo catalogo a una o più società.

Ad esempio, un commerciante B2B ha tre clienti che hanno negoziato tariffe specifiche per il sito di distribuzione elettronica del commerciante.
Utilizzando la funzione di catalogo condiviso, il commerciante ha:

* Un catalogo principale
* Un cliente 1 catalogo (forse sono solo tre SKU con forti sconti su di loro dal catalogo principale)
* Catalogo cliente 2 (potrebbe essere l&#39;intero catalogo con 10% di sconto)
* Catalogo Customer 3 (alcune decine di prodotti con sconti dal catalogo principale che vanno dal 5% - 60%).

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: catalogo, b2b_

### spedizione

_sostantivo_

Una spedizione contiene i prodotti da consegnare e genera un record dei prodotti in un ordine spedito.
È possibile associare più spedizioni a un singolo ordine.

_Attributi del termine:_

* _Campo: business, ordine_

### documento di spedizione

_sostantivo_

Documento che accompagna una spedizione. Il documento elenca i prodotti e le relative quantità nel pacchetto di consegna.

_Attributi del termine:_

* _Campo: business, ordine_

### vettore

_sostantivo_

Un&#39;azienda che trasporta pacchetti. I vettori comuni includono UPS, FedEx, DHL e USPS.

_Attributi del termine:_

* _Campo: business, ordine_

### carrello

_sostantivo_

Il set di prodotti che un cliente ha selezionato per l’acquisto, ma che non ha ancora acquistato.
Fa anche riferimento a un&#39;area di un sito di e-commerce in cui è possibile trovare questi prodotti per la revisione e il pagamento.

_Attributi del termine:_

* _Campo: business, design, prodotto, programmazione_
* _Sinonimi: carrello_
* _Termini correlati: regole del carrello_

### prodotto semplice

_sostantivo_

Il tipo di prodotto più basilare, un articolo fisico con una singola SKU.
I prodotti semplici dispongono di vari controlli dei prezzi e degli input che consentono di vendere varianti del prodotto.
I prodotti semplici possono essere utilizzati in associazione con prodotti raggruppati, raggruppati e configurabili.
Un prodotto semplice con opzioni personalizzate è talvolta denominato prodotto composito.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: tipi di prodotto_

### SKU

_sostantivo_

Abbreviazione per unità di conservazione delle scorte.
Numero o codice assegnato a un prodotto per identificare il prodotto, le opzioni, il prezzo e il produttore.

_Attributi del termine:_

* _Campo: business, prezzi, prodotto, programmazione_
* _Termini correlati: catalogo condiviso_

### pagina iniziale

_sostantivo_

una pagina promozionale con un prodotto o un annuncio; normalmente visualizzato prima della home page.

_Attributi del termine:_

* _Campo: progettazione_

### blocco statico

_sostantivo_

Unità modulare di contenuto che può essere inserita da un utente nel CMS su una pagina per visualizzare testo e immagini o per eseguire snippet di codice.
I blocchi statici contengono contenuto modificabile e possono fungere da pagine di destinazione per le categorie di prodotti.
I widget possono essere aggiunti ai blocchi statici per fornire funzionalità aggiuntive.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: blocco cms, blocco_

### contenuto statico

_sostantivo_

Contenuto generato dall’utente (non generato dal codice) che non viene modificato frequentemente.

_Attributi del termine:_

* _Campo: progettazione_
* _Termini correlati: contenuto dinamico_

### file statici

_sostantivo_

La raccolta di risorse, ad esempio CSS, font, immagini e JavaScript utilizzata da un tema.

_Attributi del termine:_

* _Campo: software commerce_

### archiviare

_sostantivo_

Il livello di ambito Commerce di &quot;store&quot; è il secondo livello della gerarchia del tuo sito web, che va come segue: sito web > store > visualizzazione store.
I negozi possono essere organizzati in uno o più negozi. Ogni archivio, potenzialmente, ha la propria categoria principale e tutti condividono i dati del catalogo e dei clienti.

Ogni negozio può avere più viste del negozio, che in genere vengono utilizzate per presentare la vetrina in un&#39;altra lingua e impostazioni internazionali.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: punto vendita, sito web_

### vista store

_sostantivo_

Il livello di ambito Commerce di &quot;visualizzazione store&quot; si riferisce al terzo livello nella gerarchia dei siti web, dei negozi e delle viste store.
Le viste Store presentano tipicamente la vetrina in una lingua e in un&#39;altra lingua.
Per modificare le viste Store, utilizza il selettore store nell&#39;intestazione.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: negozio, sito web_

### vetrina

_sostantivo_

Il negozio online che i clienti sperimentano quando visitano il tuo sito Commerce.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_

## T

### regola fiscale

_sostantivo_

Combinazione di una classe di imposta sui prodotti, una classe di imposta sui clienti e un&#39;aliquota fiscale. Questa regola definisce quale calcolo dell&#39;imposta viene applicato.

_Attributi del termine:_

* _Campo: business_

### template

_sostantivo_

Breve per modello HTML o modello PHTML.
Un file PHTML contiene un insieme di codice PHP e di markup HTML per inserire contenuto dinamico in HTML.
Nella maggior parte dei blocchi è presente almeno un file PHTML (template) contenente il HTML statico generato dal blocco.
Nei modelli Admin, e-mail e newsletter, per produrre contenuti personalizzati inviati dal sistema, è possibile combinare testo, immagini e variabili con il markup HTML.

_Attributi del termine:_

* _Campo: software commerce_
* _Termini correlati: blocco_

### tema

_sostantivo_

Contiene informazioni grafiche e sull&#39;aspetto.
Personalizza l&#39;aspetto del negozio.
Adobe Commerce può distribuire i temi nei pacchetti (Compositore).
Ma i temi possono essere inseriti in app / design, che non è spedito in un pacchetto.
I pacchetti sono l&#39;unità di download per Compositore e, tramite Commerce Marketplace, gli utenti Commerce possono scaricare CE o EE come una serie di pacchetti, in cui i pacchetti contengono moduli, temi o pacchetti linguistici.

_Attributi del termine:_

* _Campo: software commerce_

## U

### Componente interfaccia

_sostantivo_

Tag progettato per il software Adobe Commerce per consentire un rendering dell’interfaccia utente (UI) più semplice e flessibile.
Gli obiettivi del sistema di componenti dell’interfaccia utente includono:

* Semplificazione del layout Gestione dei file XML
* Spostamento degli elementi dell’interfaccia utente amministratore da HTML+JavaScript a un sistema di widget personalizzato &quot;pure JavaScript&quot;
* Creazione di componenti dell’interfaccia utente più complessi con componenti più piccoli
* Pre-rendering dei dati per i componenti dell’interfaccia utente come JSON, associazione strettamente agli oggetti dati di backend
* Utilizzo di AJAX per aggiornare i dati dei componenti
* Introduzione di un nuovo DSL per la creazione degli elementi di cui sopra

Ulteriori informazioni: [Guida ai componenti dell’interfaccia utente](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: JavaScript, layout, componente, generatore di pagine_

### VERSO L&#39;ALTO

_sostantivo_

[PWA Studi](https://github.com/magento/pwa-studio) utilizza [VERSO L&#39;ALTO](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) nello sviluppo.
UPWARD è un acronimo per Definizione della risposta progressiva unificata dell&#39;app web.
Un file di definizione UPWARD descrive come un server web fornisce e supporta un Progressive Web Application.

I file di definizione UPWARD forniscono dettagli sul comportamento del server utilizzando un linguaggio dichiarativo indipendente dalla piattaforma.
Questo consente a Progressive Web Application di eseguire su un server compatibile con UPWARD in qualsiasi lingua in qualsiasi stack di tecnologia, perché l&#39;applicazione è preoccupata solo del comportamento dell&#39;endpoint HTTP dal server UPWARD.

Un server UPWARD utilizza un file di definizione per determinare il processo o il servizio appropriato per una richiesta da una shell di applicazione.
Descrive come il server deve gestire una richiesta e generare la risposta per essa.

Un progetto PWA può includere un file di definizione UPWARD per specificare le dipendenze del servizio.

_Attributi del termine:_

* _Campo: progettazione, software commerce, programmazione_
* _Sinonimi: Definizione della risposta a un&#39;app Web progressiva unificata di PWA Studi_
* _Termini correlati: pwa_

## V

### Estensione bundle fornitore

_sostantivo_

Il codice prodotto dal fornitore che estende o personalizza il comportamento Commerce e opera come estensione di terze parti è considerato un’estensione Bundled fornitore (VBE).
I VBE vengono testati accuratamente e inclusi in ogni versione supportata di Magenti Open Source e Adobe Commerce.
Un VBE può includere moduli, temi e pacchetti linguistici.

Ulteriori informazioni nel [Argomento relativo all&#39;estensione nel pacchetto fornitore](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Attributi del termine:_

* _Campo: estensione commerce, estensione bundle fornitore, estensione, VBE_
* _Sinonimi: estensione, VBE_
* _Termini correlati: estensione, estensione bundle_

### scala verticale

_sostantivo_

Il ridimensionamento verticale (scaling up) si riferisce all&#39;aumento della potenza di elaborazione di un singolo server o cluster mediante l&#39;aggiunta di un disco o di una rete I/O, CPU o RAM.

_Attributi del termine:_

* _Campo: ambiente_

### prodotto virtuale

_sostantivo_

Rappresenta un prodotto non fisico che può essere venduto, ad esempio un abbonamento, un servizio, una garanzia o un abbonamento.
I prodotti virtuali possono essere venduti singolarmente o inclusi tra i seguenti tipi di prodotto: prodotto raggruppato e prodotto bundle.
Non richiede spedizione o inventario.

Il processo di creazione di un prodotto virtuale e di un prodotto semplice è quasi lo stesso.
Tuttavia, poiché un prodotto virtuale non viene spedito, non esiste un campo Peso o un&#39;opzione per includere una carta regalo.

_Attributi del termine:_

* _Campo: software di commercio, prodotto_
* _Termini correlati: tipi di prodotto_

### tipo virtuale

_sostantivo_

I tipi virtuali sono un modo per inserire dipendenze diverse nelle classi PHP esistenti senza influenzare altre classi e senza dover creare un file di classe.
È possibile fare riferimento ai tipi virtuali solo tramite sostituzioni di argomenti in un `<type>` elemento all’interno di file di di.xml, mai nel codice sorgente.
Non possono essere estesi e non possono essere riferimenti come dipendenze in un costruttore di classi.

_Attributi del termine:_

* _Campo: programmazione_
* _Termini correlati: php_

## W

### sito web

_sostantivo_

Nel software Adobe Commerce, il livello più alto di una gerarchia di siti web, sopra la visualizzazione store e store.
Puoi avere più siti web e ogni sito web può avere un nome di dominio diverso.
I siti web possono essere impostati per condividere i dati dei clienti o per non condividerli.

_Attributi del termine:_

* _Campo: software di commercio, progettazione, prodotto_
* _Termini correlati: store, visualizzazione store_

### widget

_sostantivo_

A [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) è un frammento di codice preparato che può essere utilizzato per posizionare blocchi, collegamenti e contenuti dinamici in posizioni specifiche sulle pagine del negozio.
Puoi utilizzare i widget per creare pagine di destinazione per campagne di marketing e visualizzare contenuti promozionali in posizioni specifiche in tutto il negozio.
I widget possono anche essere utilizzati per aggiungere elementi interattivi e blocchi di azione per sistemi di revisione esterni, chat video, moduli di voto e sottoscrizione, o per fornire elementi di navigazione per tag cloud e cursori di immagini.

_Attributi del termine:_

* _Campo: business, software di commercio, progettazione_
* _Termini correlati: blocco_

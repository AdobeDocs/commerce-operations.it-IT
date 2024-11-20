---
source-git-commit: 0d5eeb691281d7c62aa64a9d8cd042f18504a67f
workflow-type: tm+mt
source-wordcount: '6370'
ht-degree: 0%

---
# Glossario di Adobe Commerce

## A

### sopra la piega

_aggettivo_

In una finestra del browser, il contenuto immediatamente visibile dopo il caricamento di una pagina web e prima che un utente scorresse la pagina verso il basso.
Durante la progettazione del layout, utilizza formati flessibili per visualizzare al meglio prodotti, funzionalità, vendite, notifiche, opzioni e così via con la massima priorità in quest’area.

Con i dispositivi mobili e i tablet, l&#39;area di sopra la piega differisce notevolmente, soprattutto per le dimensioni e le dimensioni dello schermo e l&#39;orientamento durante la visualizzazione (verticale vs orizzontale).
L’utilizzo di temi e test reattivi può aiutare a trovare la giusta combinazione di contenuto e layout.

_Attributi termine:_

* _Campo: design_

### ramo attivo

_sostantivo_

Un ramo o ambiente attivo è un ramo connesso a un’istanza implementata o in esecuzione con accesso ai servizi.
Quando si disattiva, la connessione ai servizi e all’istanza in esecuzione viene rimossa, ma il codice viene mantenuto.
Diventa un ramo Git ordinario.

_Attributi termine:_

* _Campo: cloud_

### adattatore

_sostantivo_

Classe che consente a due sistemi altrimenti incompatibili di lavorare insieme senza modificare il codice sorgente dei sistemi.
Alcuni esempi includono schede di database, schede di cache, schede di file system, schede di librerie di postprocessore e altri tipi di schede di elaborazione.

_Attributi termine:_

* _Campo: programmazione_

### admin

_sostantivo_

Nel software, un ruolo utente con privilegi di amministratore completi per gestire tutte le funzionalità.
In Adobe Commerce, gli utenti amministratori dispongono di autorizzazioni complete e hanno accesso a tutte le funzioni, le opzioni e le funzionalità di Admin.
Possono anche creare utenti e ruoli.

Ulteriori informazioni: [Aggiunta di utenti](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Attributi termine:_

* _Campo: software commerce_
* _Sinonimi: amministratore, utente privilegiato_
* _Termini correlati: commerce admin_

### Area di amministrazione

_sostantivo_

Il back office protetto da password del negozio in cui vengono gestiti ordini, cataloghi, contenuti e configurazioni.
Gli utenti accedono all&#39;area di amministrazione per gestire il punto vendita, inclusi prodotti, ordini, spedizioni, contenuti CMS, progettazione della vetrina, informazioni sui clienti e così via.
Agli utenti amministratori è associato un ruolo con autorizzazioni che controlla l’accesso a funzioni, opzioni e funzionalità.

Ulteriori informazioni: [Guida utente di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributi termine:_

* _Campo: software commerce_
* _Sinonimi: Amministratore, Pannello di amministrazione, backend, Interfaccia di amministrazione, Interfaccia di amministrazione_
* _Termini correlati: admin_

### Variabili ADMIN

_sostantivo_

Le variabili ADMIN sono variabili di ambiente del progetto che sostituiscono le impostazioni di configurazione dell’account utente Admin per accedere all’interfaccia utente di Admin.

Ulteriori informazioni: [Variabili ADMIN](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Attributi termine:_

* _Campo: admin, cloud_

### adminhtml

_sostantivo_

Nome dell’area interna assegnato all’amministratore.

Ulteriori informazioni: [Guida utente di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: area, amministrazione commerciale_

### area

_sostantivo_

Area è un termine astratto per un ambito di applicazione di Magento.
Le aree sono componenti logici che organizzano il codice per l’elaborazione ottimizzata delle richieste.
Le aree riducono le richieste di memoria degli oggetti di configurazione a cui si accede dalla vetrina e semplificano le chiamate al servizio web caricando solo il codice dipendente richiesto.
Ogni area può contenere codice completamente diverso per elaborare URL e richieste.

Le aree di Adobe Commerce includono:

* Amministratore (adminhtml)
* Vetrina
* REST API web (webapi_rest)

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: commerce component, storefront_

### attributo

_sostantivo_

Caratteristica o proprietà di un prodotto che descrive alcuni aspetti del prodotto.
Gli utenti di Adobe Commerce possono creare attributi personalizzati da aggiungere al set di attributi predefinito o a un set di attributi personalizzato.
Crea questi attributi tramite Admin o a livello di programmazione.
Esempi: colore, dimensione, peso, prezzo, età, genere e così via.

Gli attributi personalizzati sono un tipo di attributo Entity-Attribute-Value (EAV).

Per integrazioni quali Google Shopping ads Channel e Amazon Sales Channel, mappi gli attributi Commerce agli attributi di terze parti per visualizzare e vendere correttamente prodotti e annunci.

Ulteriori informazioni: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Sinonimi: attributo di prodotto, attributo personalizzato_
* _Termini correlati: attributo di estensione_

### gruppo di attributi

_sostantivo_

Raggruppamento logico di attributi all&#39;interno di un set di attributi.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: attribute_

### set di attributi

_sostantivo_

Una raccolta di gruppi di attributi, personalizzati per un prodotto specifico.
Esempio: un set di attributi di T-shirt può includere colore, dimensione, genere e marchio.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: attribute_

### costo medio di magazzino

_sostantivo_

Prezzo del prodotto, meno coupon, o sconti, più trasporto e imposte applicabili.
La media viene determinata sommando il costo iniziale del magazzino ogni mese e il costo finale del magazzino per l&#39;ultimo mese del periodo.

_Attributi termine:_

* _Campo: prodotto, prezzi, inventario_

## B

### valuta di base

_sostantivo_

Valuta principale utilizzata per la visualizzazione punto vendita per tutti i pagamenti online.
I negozi possono accettare valute da più di 200 paesi in tutto il mondo.
La vetrina fornisce un selettore di valuta per più valute accettate per un paese o una lingua specifici.
I simboli di valuta vengono visualizzati nei documenti relativi ai prezzi dei prodotti e alle vendite, ad esempio ordini e fatture.
È possibile personalizzare i simboli di valuta in base alle esigenze e impostare la visualizzazione del prezzo separatamente per ogni negozio o vista.

Ulteriori informazioni: [Valuta](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Attributi termine:_

* _Campo: determinazione prezzi_

### elaborazione batch

_sostantivo_

Per eseguire un&#39;operazione o modificare più elementi contemporaneamente, senza ripetizione manuale.

_Attributi termine:_

* _Campo: programmazione_
* _Sinonimi: operazioni in blocco_

### blocco

_sostantivo_

Un’unità di output della pagina che genera alcuni contenuti distintivi (informazioni, elementi dell’interfaccia utente) visibili all’utente finale.
[I blocchi](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) sono implementati e forniti dai moduli.
I blocchi utilizzano i modelli per generare HTML.
Esempi di blocchi includono un elenco di categorie, un mini carrello, tag di prodotti ed elenco di prodotti.

[I blocchi dinamici](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) forniscono contenuto in base alla logica, ad esempio in base alle regole di prezzo.

Page Builder approfondisce l&#39;interattività e la creazione di [blocchi](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) e [blocchi dinamici](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Attributi termine:_

* _Campo: software commerce_
* _Sinonimi: Blocchi Dinamici_
* _Termini correlati: blocco cms, blocco statico, contenitore, layout_

### brand

_sostantivo, verbo_

Identità univoca che definisce un particolare prodotto o gruppo di prodotti da parte del produttore o del Designer.
Questi includono marchi di nomi per abbigliamento, elettrodomestici, articoli di lusso e così via.
La tua azienda potrebbe essere anche il marchio, che vende prodotti con più marchi in base alla business unit, al pubblico di destinazione e così via.

Utilizza gli attributi personalizzati per salvare le informazioni sul marchio dei prodotti.

Alcune estensioni e integrazioni possono utilizzare o richiedere un marchio per i prodotti, ad esempio Google Shopping ads Channel e Amazon Sales Channel.

_Attributi termine:_

* _Campo: business_

### mattoni e malta

_aggettivo_

Un&#39;attività di vendita al dettaglio con una sede fisica permanente, a differenza delle attività che funzionano virtualmente o esclusivamente tramite Internet.

Per [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) e [Order Management](#oms), questo archivio è un&#39;origine per la registrazione delle quantità di prodotti, degli ordini di spedizione e il supporto del prelievo in-store.

_Attributi termine:_

* _Campo: business, inventory_

### operazioni in serie

_sostantivo_

Le operazioni in blocco sono azioni eseguite su larga scala.
Esempio di operazioni in blocco le attività includono l&#39;importazione o l&#39;esportazione di articoli, la modifica dei prezzi su scala di massa e l&#39;assegnazione di prodotti a un magazzino.

Ulteriori informazioni: [Operazioni in blocco DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Attributi termine:_

* _Campo: programmazione_

### prodotto bundle

_sostantivo_

Consente ai clienti di assemblare un prodotto personalizzabile &quot;build your own&quot; da varie opzioni e configurazioni.
Ogni elemento nel bundle è un prodotto semplice o virtuale separato.

Ulteriori informazioni: [Prodotti configurabili](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: prodotto semplice, prodotto virtuale, tipi di prodotto_

### estensione in bundle

_sostantivo_

Il codice che estende o personalizza il comportamento di Adobe Commerce è considerato un’estensione in bundle.
Può includere moduli, temi e pacchetti di lingue.

_Attributi termine:_

* _Campo: estensione nel bundle, estensione_
* _Sinonimi: estensione_
* _Termini correlati: estensione, estensione del bundle del fornitore_

## C

### back-end cache

_sostantivo_

Memorizza i record della cache in un sistema back-end a due livelli all&#39;interno del framework predefinito di Zend.
Una cache di primo livello è veloce, ad esempio un back-end APC o Memcached, ma è limitata e non supporta il tagging e il raggruppamento delle voci della cache.
Una cache di secondo livello, ad esempio un file system o un back-end Redis, è più lenta ma supporta i tag e i raggruppamenti.

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: backend_

### cache front-end

_sostantivo_

Specifica il tipo di dati memorizzati nel backend della cache.

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: frontend_

### tipo di cache

_sostantivo_

Una cache memorizza i dati in modo che le chiamate future per tali dati vengano caricate più rapidamente.

Adobe Commerce include i seguenti tipi:
* Configurazione
* Layout
* Blocca output HTML
* Dati delle raccolte
* Dati di riflessione
* Operazioni DDL del database
* Configurazione compilata
* Tipi e attributi EAV
* Notifica cliente
* Configurazione integrazioni
* Configurazione API integrazioni
* Cache pagine (la più nota)
* Configurazione servizi Web
* Traduzioni
* Regola di destinazione
* Cache prodotti Google
* Vertice

È possibile creare e definire altri tipi.

_Attributi termine:_

* _Campo: programmazione_

### acquisire

_verbo_

Processo di conversione di un importo di ordine autorizzato in una transazione fatturabile.
Le transazioni non possono essere acquisite fino a quando non vengono autorizzate e le autorizzazioni non possono essere acquisite fino a quando i beni o i servizi non sono stati spediti.

_Attributi termine:_

* _Campo: business_
* _Termini correlati: autorizzazione, stato ordine_

### titolare della carta

_sostantivo_

Persona autorizzata da un istituto finanziario a effettuare acquisti su un conto con carta di credito.

_Attributi termine:_

* _Campo: business, order_

### regole carrello

_sostantivo_

Regole di prezzo applicate al carrello e che attivano un’azione in risposta a una serie di condizioni.
Utilizzato per creare promozioni.

_Attributi termine:_

* _Campo: software commerciale, prezzi, prodotto_
* _Termini correlati: regole catalogo, carrello_

### catalogo

_sostantivo_

Per i commercianti, il catalogo rappresenta il loro inventario di prodotti.
Nell’architettura di Adobe Commerce, il catalogo è costituito da categorie, prodotti e attributi di prodotto.

Ogni store di Commerce dispone di un solo catalogo dei prodotti, che viene condiviso da tutte le visualizzazioni dello store.
In un&#39;installazione multi-store, ogni store può avere un catalogo separato o condividere il catalogo.
Il catalogo dello store corrente è determinato dalla categoria principale predefinita, visibile all’utente nella navigazione superiore (menu principale) dello store.
(Il termine &quot;categoria principale&quot; può confondere, perché la &quot;categoria principale&quot; non è in realtà una categoria, ma un contenitore per il menu, che consiste di categorie e sottocategorie.)

Puoi creare tutte le categorie principali che desideri, ma è possibile utilizzare una sola (impostazione predefinita) alla volta.

_Attributi termine:_

* _Campo: software commerciale, prezzi, prodotto_
* _Termini correlati: catalogo condiviso, regola catalogo_

### regole di catalogo

_sostantivo_

Regole di prezzo applicate a prodotti specifici e che attivano un’azione in risposta a una serie di condizioni.
Utilizzato per creare promozioni.

_Attributi termine:_

* _Campo: software commerciale, prezzi, prodotto_
* _Termini correlati: regole carrello, catalogo_

### categoria

_sostantivo_

Un gruppo di prodotti che hanno qualcosa in comune.
Il menu principale del negozio è organizzato in categorie e sottocategorie di prodotti.

_Attributi termine:_

* _Campo: software commerce, prodotto_

### pagamento

_sostantivo_

Il processo di raccolta delle informazioni di pagamento e spedizione necessarie per completare l’acquisto degli articoli nel carrello.
Dopo che il cliente rivede le informazioni e invia l’ordine, gli viene inviata una conferma e-mail.

Checkout dispone di molte opzioni e configurazione pronte all’uso e tramite l’estensione.

Ulteriori informazioni: [Esercitazione estrazione](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Attributi termine:_

* _Campo: business, design, order, product, programming_

### variabili cloud

_sostantivo_

Le variabili cloud sono variabili di ambiente specifiche di Adobe Commerce sull&#39;infrastruttura cloud e utilizzano il prefisso **`MAGENTO_CLOUD`**.

Ulteriori informazioni: [Variabili cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Attributi termine:_

* _Campo: cloud_

### Blocco CMS

_sostantivo_

Una variante speciale di [blocco](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) che può essere creata solo in Admin e a cui non è possibile fare riferimento tramite file di layout.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: blocco, blocco statico_

### dati complessi

_sostantivo_

Dati associati a più opzioni di prodotto.

_Attributi termine:_

* _Campo: programmazione_

### componente

_sostantivo_

Utilizzato per fare riferimento a un modulo, un tema o un pacchetto di linguaggio in Adobe Commerce.

_Attributi termine:_

* _Campo: software commerce_
* _Sinonimi: componente_
* _Termini correlati: componente interfaccia utente_

### prodotto configurabile

_sostantivo_

Un prodotto configurabile si presenta come un singolo prodotto con elenchi a discesa di opzioni per ogni variante.
Ogni opzione è in realtà un prodotto semplice separato con una SKU univoca, che consente di tenere traccia dell’inventario per ogni variante di prodotto.
Per ottenere un effetto simile, un prodotto semplice può essere utilizzato con opzioni personalizzate, ma senza la possibilità di tenere traccia dell’inventario per ogni variante.
I prodotti con più opzioni sono talvolta denominati prodotti compositi.

Sebbene un prodotto configurabile utilizzi più SKU e la configurazione iniziale possa richiedere un po’ di tempo, alla fine potrai risparmiare tempo.
Se prevedi di espandere la tua attività, il tipo di prodotto configurabile potrebbe essere la scelta migliore per un prodotto con più opzioni.

Esempio: T-shirt disponibili in due colori e tre dimensioni.
È necessario creare sei varianti come singoli prodotti (ciascuna con la propria SKU).
Quindi, tutte le varianti vengono aggiunte a un prodotto configurabile in cui i clienti possono scegliere la dimensione e il colore e quindi aggiungerlo al carrello.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: tipi di prodotto_

### tasso di conversione

_sostantivo_

La percentuale di visitatori che vengono convertiti in acquirenti.

_Attributi termine:_

* _Campo: business, order_

### scalabilità a livello core

_sostantivo_

La scalabilità a livello core è costituita da tre nodi di servizio per l’archiviazione dei dati, la cache e i servizi, come OpenSearch, Elasticsearch, MariaDB, Redis.

_Attributi termine:_

* _Campo: cloud_

### nota di accredito

_sostantivo_

Documento emesso dall&#39;esercente nei confronti di un cliente per cancellare un saldo residuo a causa di sovrattassa, sconto o restituzione di beni.
La nota ripristina i fondi sul conto del cliente.

_Attributi termine:_

* _Campo: business, order_

### commento nota di credito

_sostantivo_

Dettagli sul motivo per cui un importo della nota di credito è stato accreditato al cliente.

_Attributi termine:_

* _Campo: business, order_

### voce nota di credito

_sostantivo_

Articolo fatturato per il quale un commerciante crea una nota di accredito.

_Attributi termine:_

* _Campo: business, order_

### effettuare azioni di cross-selling

_sostantivo, aggettivo, verbo_

Prodotto visualizzato accanto al carrello.
Quando un cliente passa alla pagina del carrello, questi prodotti vengono visualizzati come cross-selling per gli articoli già presenti nel carrello.
Sono simili agli acquisti d&#39;impulso, come riviste e caramelle ai registratori di cassa nei negozi di alimentari.

_Attributi termine:_

* _Campo: business, prodotto_
* _Termini correlati: upselling_

### CVM

_sostantivo_

Abbreviazione di &quot;Cardholder Verification Method&quot;.
Un modo per verificare l’identità del cliente confermando un codice di sicurezza della carta di credito a 3 o 4 cifre con il processore dei pagamenti.

_Attributi termine:_

* _Campo: business, order_
* _Sinonimi: Metodo di verifica del titolare della carta_
* _Termini correlati: codice di sicurezza_

## D

### schema di database

_sostantivo_

Struttura dei dati in un database.
Definisce il modo in cui i dati vengono organizzati e in cui vengono gestite le relazioni tra i dati, inclusi tutti i vincoli applicati ai dati.
Un modulo può contenere frammenti dello schema del database se tale modulo contiene dati che devono essere memorizzati nel database.

_Attributi termine:_

* _Campo: programmazione_
* _Sinonimi: schema_

### iniezione di dipendenza

_sostantivo_

Schema di progettazione software che consente a una classe di specificare le proprie dipendenze senza doverle costruire.
Questa classe delega la responsabilità di inserire la dipendenza alla classe chiamante.
Utilizzato per semplificare i test.
Per definire le dipendenze per le classi, modificare il file di configurazione di.xml.

_Attributi termine:_

* _Campo: programmazione_

### chiave di distribuzione

_sostantivo_

Una chiave di distribuzione è la chiave pubblica SSH del progetto e consente l’accesso in sola lettura o in lettura e scrittura (se abilitata) a un archivio Git.

Ulteriori informazioni: [Connessioni sicure](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Attributi termine:_

* _Campo: cloud_

### doppio consenso

_sostantivo, verbo_

Un processo di verifica e-mail che richiede ai potenziali abbonati di completare un secondo passaggio che conferma la loro intenzione di abbonarsi.

_Attributi termine:_

* _Campo: business_

### prodotto scaricabile

_sostantivo_

Prodotto scaricabile digitalmente costituito da uno o più file scaricati, ad esempio eBook, musica, video, applicazione software o aggiornamento.
È possibile offrire un album in vendita e vendere ogni singola canzone.
Un prodotto scaricabile può fornire una versione elettronica del catalogo dei prodotti.

I file scaricabili possono risiedere sul server o essere forniti come URL a qualsiasi altro server o rete di distribuzione dei contenuti.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: tipi di prodotto_

### contenuto dinamico

_sostantivo_

Contenuto generato dal codice anziché letto da un modello statico.
Dopo il rendering iniziale del contenuto dinamico quando un utente visita una pagina, a volte il contenuto può essere memorizzato in cache e riutilizzato senza richiedere un’altra chiamata dinamica in seguito a una nuova visita.

_Attributi termine:_

* _Campo: design_
* _Termini correlati: php_

### URL elemento multimediale dinamico

_sostantivo_

Indirizzo URL generato dinamicamente dal sistema per fare riferimento a un&#39;immagine o a un altro supporto.
L’indirizzo si collega direttamente alle risorse memorizzate su un server o su una rete di distribuzione di contenuti.
Per utilizzare un URL statico, modifica l’impostazione di configurazione.
Tuttavia, se gli URL di elementi multimediali dinamici sono inclusi nel catalogo quando disattivi l’impostazione, ogni riferimento nel catalogo diventa un collegamento non funzionante.
I collegamenti possono essere ripristinati abilitando nuovamente gli URL di elementi multimediali dinamici.
L’utilizzo degli URL di Dynamic Media può influire sulle prestazioni di ricerca del catalogo.

Formato del codice: media url=&quot;path/to/image.jpg&quot;

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: content delivery network, url_

## E

### pacchetto strumenti ece

_sostantivo_

Un insieme di script e strumenti progettati per gestire e distribuire l&#39;applicazione Commerce. Questo pacchetto semplifica molti processi dell’infrastruttura cloud di Adobe Commerce, tra cui l’implementazione in un ambiente Docker, la gestione delle istanze, la verifica della configurazione del progetto e l’applicazione di patch Adobe.

Ulteriori informazioni: [pacchetto ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Attributi termine:_

* _Campo: cli, cloud, deploy_

### entità

_sostantivo_

Unità o oggetto univoco nella programmazione.
Contiene attributi o parametri che possono essere modificati.
Alcuni esempi includono la gestione temporanea, in cui un aggiornamento può modificare entità quali regole di prezzo, prodotti o categorie, e record di database, in cui i contratti di assistenza includono strutture di dati inviate e ricevute.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: attributo, regole carrello, regole catalogo_

### valore attributo entità

_sostantivo_

Per le entità di database, modello dati che codifica in modo efficiente le entità.
Memorizza l’ID entità, il nome attributo e il valore come una tripla, consentendo la creazione di nuovi nomi di attributi entità in qualsiasi momento.
Nella codifica, il numero di attributi che possono essere utilizzati per descrivere le entità può essere ridimensionato in modo esteso, ma il numero che si applica a una determinata entità è ridotto al minimo.
Questo modello dati è flessibile, ma può essere lento.

Ulteriori informazioni: [EAV e extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Attributi termine:_

* _Campo: programmazione_
* _Sinonimi: eav_

### contenuto sempreverde

_sostantivo_

Contenuti con una lunga durata di conservazione o che possono essere riutilizzati.

_Attributi termine:_

* _Campo: business_

### estensione

_sostantivo_

Codice che estende o personalizza il comportamento di Adobe Commerce.
Facoltativamente, puoi creare un pacchetto e distribuire un’estensione su Commerce Marketplace o su un altro sistema di distribuzione delle estensioni.
Un’estensione Commerce può includere moduli, temi e Language Pack.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: componente, modulo, pacchetto_

### attributo di estensione

_sostantivo_

Estendere le funzionalità e spesso utilizzare tipi di dati più complessi rispetto agli attributi personalizzati. Questi attributi non vengono visualizzati nella GUI.

Ulteriori informazioni: [Aggiunta di attributi di estensione all&#39;entità](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: attributo, valore attributo entità_

## F

### trasporto merci a bordo

_sostantivo_

Nel trasporto marittimo internazionale, questo termine significa che la parte ricevente è responsabile delle spese di spedizione.
Il FOB può essere basato sul luogo di origine o di destinazione ed essere designato come carico incassato o trasporto prepagato.

_Attributi termine:_

* _Campo: business, order, pricing_
* _Sinonimi: fob_

### front-end

_aggettivo_

In un’applicazione client-server, c’è il back-end e il front-end.
Il componente front-end, o client, è un’interfaccia che consente agli utenti di manipolare o interagire con il codice back-end sottostante.
Il codice di back-end viene eseguito su un server.
Un utente non può accedere direttamente al codice back-end.
Un utente interagisce con la vetrina, che a sua volta utilizza il codice in esecuzione sul server Commerce.

Nota: in passato, la vetrina era indicata come &quot;front-end&quot; e l’amministratore come &quot;back-end&quot;. Questo utilizzo non è più supportato.

_Attributi termine:_

* _Campo: progettazione, programmazione_
* _Sinonimi: lato client_
* _Termini correlati: backend, storefront, cache front-end_

### proprietà front-end

_sostantivo_

Proprietà che determinano la presentazione e il comportamento di un attributo dal punto di vista del cliente nel punto vendita.

_Attributi termine:_

* _Campo: progettazione, programmazione_

### adempimento

_sostantivo_

Processo di gestione delle spedizioni dei clienti.

_Attributi termine:_

* _Campo: business_

## G

### gift card

_sostantivo_

Una carta prepagata o un buono regalo che possono essere utilizzati per effettuare acquisti nel negozio.
A ogni gift card viene assegnato un codice univoco che viene immesso al momento del pagamento.
Il valore della gift card si riflette nel saldo del conto della gift card.
Esistono tre tipi di gift card:

* Le carte regalo &quot;fisiche&quot; possono essere prodotte da materiale plastico o cartoline, spedite al cliente.
* Le gift card &quot;virtuali&quot; vengono inviate tramite e-mail.
* Le gift card &quot;combinate&quot; sono una combinazione delle due, spedite al destinatario come una gift card fisica e consegnate anche via e-mail.
Le gift card sono configurabili, incluse le opzioni per l&#39;idoneità del prodotto e la selezione di importi aperti o fissi.

Una gift card può anche essere riscattata dall&#39;amministratore del negozio su richiesta del cliente quando l&#39;ordine viene creato nel backend.

Le gift card sono utili anche per le promozioni, in quanto gli amministratori dei negozi possono creare manualmente gli account delle gift card nel backend e inviare i codici delle gift card al segmento di clienti specifico.
Le carte regalo possono fungere da programma fedeltà rivolto ai clienti più attivi che effettuano numerosi acquisti dal negozio web o una specifica campagna promozionale durante le vacanze.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: tipi di prodotto_

### margine lordo

_sostantivo_

La differenza tra il costo e il prezzo di un prodotto.

_Attributi termine:_

* _Campo: business_

### prodotto raggruppato

_sostantivo_

Un tipo di prodotto con diversi prodotti simili e autonomi raggruppati in una singola pagina.
Possono essere offerti con varianti di un singolo prodotto o raggruppandoli per stagione o tema per creare un set coordinato.
Ogni prodotto può essere acquistato separatamente o come parte del gruppo.

Ad esempio, per un coltello disponibile in quattro taglie, è possibile visualizzare tutti e quattro i coltelli in una pagina di prodotto raggruppata.
I clienti possono selezionare le dimensioni desiderate e aggiungerle al carrello da questa pagina.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: prodotto semplice, tipi di prodotto_

## H

### maniglia

_sostantivo_

In genere, un handle è un modo per fare riferimento a un oggetto.
In Adobe Commerce, gli handle vengono utilizzati in molte posizioni, più comunemente per identificare una pagina.
Per gli handle di pagina, il nome dell’handle deriva dall’URL e viene quindi utilizzato per individuare e caricare i file di layout per la pagina di riferimento.
Ad esempio, nel modulo Cliente è presente un file di layout denominato &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Qui &quot;frontend&quot; è il nome dell’area e &quot;checkout_cart_index&quot; è il nome dell’handle, entrambi derivati dall’URL.

_Attributi termine:_

* _Campo: programmazione_
* _Sinonimi: handle pagina_

### ridimensionamento orizzontale

_sostantivo_

Il ridimensionamento orizzontale (o scaling out) è il processo di aggiunta di ulteriori nodi o macchine all&#39;infrastruttura per soddisfare la domanda crescente.

_Attributi termine:_

* _Campo: cloud_

## I

### intercettazione

_sostantivo_

Il processo di inserimento di un nuovo codice prima, dopo o intorno a una funzione pubblica esistente di una classe PHP.

Per intercettare una funzione, un plug-in implementa il codice aggiuntivo da richiamare.
I plug-in sono associati ai punti di intercettazione dal file di configurazione dell’iniezione di dipendenza (di.xml).
Se sulla stessa funzione sono definiti più plug-in, la configurazione dell’iniezione di dipendenza definisce l’ordine in cui i plug-in vengono richiamati, consentendo l’utilizzo di più plug-in senza conflitti.

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: plug-in_

## L

### layout

_sostantivo_

Nella costruzione di una pagina Commerce, un layout è una serie di blocchi assemblati in una gerarchia, che rappresentano la struttura della pagina.

I file di layout di pagina si concentrano sul livello più alto della struttura della pagina (intestazione, piè di pagina, area del contenuto principale, barra laterale a sinistra e così via).
I file di layout assemblano quindi il contenuto (i blocchi) in queste diverse aree della pagina.

_Attributi termine:_

* _Campo: progettazione, software commerce_
* _Termini correlati: istruzioni di layout, blocco_

### istruzioni di layout

_sostantivo_

Markup in un file di layout che descrive le modifiche da applicare a una struttura ad elementi strutturati composta da blocchi, contenitori e componenti dell’interfaccia utente.
Un singolo file di layout può contenere più istruzioni di layout.
Le istruzioni di layout sono codificate in XML nei file di layout.

_Attributi termine:_

* _Campo: progettazione, programmazione_
* _Termini correlati: layout, blocco, contenitore, componente interfaccia utente_

### aggiornamento del layout

_sostantivo_

Utilizzato per snippet di codice aggiunti per modificare il layout XML o per importare le istruzioni di layout da un altro file.

_Attributi termine:_

* _Campo: progettazione, software commerce_

### Proprietario licenza

_sostantivo_

Il proprietario della licenza (noto anche come proprietario dell’account) è la persona designata in un’organizzazione aziendale che gestisce i pagamenti e altri problemi aziendali per l’account Adobe Commerce sull’infrastruttura cloud.
Questa persona funge da punto di contatto con Adobe.
Dopo che un’azienda ha acquistato un abbonamento a un’infrastruttura cloud di Adobe Commerce, il progetto iniziale e l’accesso al codice sono disponibili solo per la persona designata come proprietario della licenza.

_Attributi termine:_

* _Campo: business_

## M

### MAGEID

_sostantivo_

MAGEID è in genere il contatto di fatturazione sull’account Adobe Commerce (e potrebbe non essere il proprietario del progetto Adobe Commerce on Cloud Infrastructure).
Per poter accedere ai pacchetti di infrastruttura cloud Adobe Commerce e Adobe Commerce, devi utilizzare le chiavi di accesso associate a un MAGEID a cui è stato concesso l’accesso a tali pacchetti.

Ulteriori informazioni: [Ottieni le chiavi di autenticazione](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Attributi termine:_

* _Campo: software commerce_

### markup

_sostantivo_

Nel marketing e nel retail, una percentuale aggiunta al costo di un articolo per determinare il prezzo di vendita al dettaglio.
[Configurare il markup](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html), o markdown, di un prodotto tramite le opzioni personalizzabili del prodotto.

Nello sviluppo, lingua del computer che controlla l&#39;elaborazione, la presentazione e la formattazione del testo.
Inoltre, i tag di markup sono snippet di codice che aggiungono funzionalità o contenuto a una pagina o a un blocco di CMS.

_Attributi termine:_

* _Campo: business, programmazione_
* _Sinonimi: Markdown_

### ambiente principale

_sostantivo_

In Adobe Commerce sull’infrastruttura cloud, i progetti Pro utilizzano un ambiente Platform as a Service (PaaS) attivo denominato master che include una copia del database e del server web dell’ambiente di produzione.

_Attributi termine:_

* _Campo: cloud_

### account esercente

_sostantivo_

Conto presso una banca o un istituto finanziario che consente di accettare transazioni con carta di credito.

_Attributi termine:_

* _Campo: business_

### MFTF

_sostantivo_

MFTF è un [framework di test funzionali](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Fornisce un framework di test per sviluppatori Commerce e ingegneri software, come specialisti di controllo qualità, sviluppatori PHP e integratori di sistemi.
Sviluppatori e QA possono scrivere test per tentare interazioni dell’utente con le applicazioni web, verificare la funzionalità e automatizzare i test di regressione.

_Attributi termine:_

* _Campo: software commerce, programmazione_
* _Termini correlati: blocco cms, blocco statico, contenitore, layout_

### modulo

_sostantivo_

Codice che modifica o estende le funzioni fornite dall&#39;applicazione di Magento.
Un modulo è contenuto in una struttura di directory che contiene file PHP e XML (configurazione, blocchi, controller, helper, modelli e così via) relativi a una funzionalità specifica per fornire una raccolta distinta di funzioni di prodotto.
Ogni modulo ha lo scopo di fornire caratteristiche specifiche al prodotto implementando nuove funzionalità o estendendo quelle di altri moduli.
Ogni modulo è progettato per funzionare in modo indipendente, pertanto l&#39;inclusione o l&#39;esclusione di un particolare modulo non influisce sulla funzionalità di altri moduli.

Un modulo può anche implementare dei widget, elementi di pagina che possono essere personalizzati dagli utenti aziendali in Amministrazione.

I moduli possono essere disattivati o rimossi senza interrompere la coerenza dell’applicazione di Magento.
Una eccezione: quando il modulo dipende da altri moduli, che richiede la disattivazione o la rimozione dei moduli dipendenti.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: php, xml, block_

## O

### OMS

_sostantivo_

OMS è l&#39;offerta Order Management System di Adobe.

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS) ha raggiunto la fine del ciclo di vita e non è più supportato.

OMS è una soluzione flessibile e conveniente per la gestione, la vendita e l&#39;evasione dell&#39;inventario da qualsiasi canale di vendita.
OMS offre ai clienti un&#39;esperienza fluida, che aumenta le vendite riducendo i costi e velocizza il time-to-market.

Le funzionalità di OMS includono:

* Visibilità globale e gestione di tutti gli inventari
* Possibilità di effettuare spedizioni da e verso qualsiasi luogo
* Servizio clienti più semplice e reattivo
* Migliore esperienza e fedeltà dei clienti

Ulteriori informazioni: [Sito documenti OMS archiviato](https://commerce-docs.github.io/oms-documentation-archive/)

_Attributi termine:_

* _Campo: funzionalità, software commerce, gestione ordini_
* _Sinonimi: gestione ordini, MOM, sistema di gestione ordini, Magento Order Management_
* _Termini correlati: gestione ordini_

### cloaking dell&#39;origine

_sostantivo_

Il cloaking dell’origine è una funzione di sicurezza che consente ad Adobe Commerce sull’infrastruttura cloud di bloccare qualsiasi traffico non Fastly per evitare attacchi DDoS, indirizzandolo all’infrastruttura cloud (origine).

Ulteriori informazioni: [Cloaking dell&#39;origine veloce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Attributi termine:_

* _Campo: protezione_
* _Termini correlati: web application firewall_

## P

### Page Builder

_sostantivo_

Page Builder è un’estensione di Commerce che consente di creare pagine ricche di contenuti trascinando controlli predefiniti per definire layout personalizzati.
Questi controlli sono anche noti come &quot;tipi di contenuto&quot;.
I commercianti possono progettare layout e pagine senza esperienza di codifica.
Il supporto per le estensioni è fornito agli sviluppatori per estendere Page Builder.

Ulteriori informazioni: [Guida utente di Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [DevDocs di Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Attributi termine:_

* _Campo: software commerce, progettazione_
* _Sinonimi: Amministratore, Pannello di amministrazione, backend, Interfaccia di amministrazione, Interfaccia di amministrazione_
* _Termini correlati: admin_

### gateway di pagamento

_sostantivo_

Un gateway di pagamento è un servizio di terze parti che elabora senza interruzioni le transazioni con carta di credito senza che il cliente lasci la sede del commerciante.

_Attributi termine:_

* _Campo: business, order, programming_

## R

### prodotto correlato

_sostantivo_

Una selezione di prodotti presentata come incentivo all’acquisto di articoli aggiuntivi.
Ad esempio, se il cliente visualizza la pagina di prodotto di una fotocamera, i prodotti correlati potrebbero includere altre fotocamere simili, una custodia per la fotocamera e un treppiede.

_Attributi termine:_

* _Campo: software commerce, prodotto_

## S

### regole di vendita

_sostantivo_

Include le regole del carrello e del catalogo, utilizzate per determinare il prezzo di un prodotto per le promozioni.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: regole carrello, regole catalogo_

### ambito

_sostantivo_

In Adobe Commerce, l’ambito descrive l’estensione della gerarchia di archivi su cui può influire un’impostazione.
L’ambito può essere applicato ai seguenti elementi:

* Globale: tutti i siti Web, i negozi e le visualizzazioni dello store
* Sito Web: il sito Web selezionato e tutti i negozi e le visualizzazioni dello store al suo interno
* Store: lo store selezionato e tutte le visualizzazioni dello store al suo interno
* Visualizzazione store - la visualizzazione store selezionata.

All’interno della gerarchia, le impostazioni applicate a un livello inferiore possono ignorare alcune impostazioni di livello superiore.

_Attributi termine:_

* _Campo: software commerce_

### contratto di assistenza

_sostantivo_

Un insieme di interfacce PHP definite per un modulo.
Un contratto di servizio include le interfacce dati, che preservano l&#39;integrità dei dati, e le interfacce di servizio, che nascondono i dettagli della logica di business ai richiedenti del servizio come controller, servizi Web e altri moduli.
Le API web possono essere associate a contratti di servizio tramite file di configurazione.

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: php, api Web_

### liquidazione

_sostantivo_

Il regolamento ha luogo quando la banca acquirente e i fondi di cambio dell&#39;emittente e i proventi sono depositati nel conto dell&#39;esercente.

_Attributi termine:_

* _Campo: business_

### Catalogo condiviso

_sostantivo_

Funzione che consente ai commercianti di creare un catalogo da utilizzare come intero catalogo o come sottoinsieme di catalogo e quindi di assegnare prezzi personalizzati per uno o più prodotti.
I commercianti possono quindi assegnare questo catalogo a una o più società.

Ad esempio, un commerciante B2B ha tre clienti che hanno negoziato tariffe specifiche per il sito di distribuzione di elettronica del commerciante.
Utilizzando la funzione di catalogo condiviso, l’esercente dispone di:

* Un catalogo principale
* Un catalogo del cliente 1 (forse sono solo tre SKU con forti sconti dal catalogo principale)
* Catalogo cliente 2 (potrebbe essere l&#39;intero catalogo con uno sconto del 10%)
* Catalogo del cliente 3 (alcune decine di prodotti con sconti fuori catalogo principale che vanno dal 5% al 60%).

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: catalogo, b2b_

### spedizione

_sostantivo_

Una spedizione contiene i prodotti da consegnare e genera una registrazione dei prodotti in un ordine che sono stati spediti.
È possibile associare più spedizioni a un singolo ordine.

_Attributi termine:_

* _Campo: business, order_

### documento di spedizione

_sostantivo_

Documento che accompagna una spedizione. Il documento elenca i prodotti e i relativi quantitativi nella confezione di consegna.

_Attributi termine:_

* _Campo: business, order_

### corriere

_sostantivo_

Azienda che trasporta pacchetti. I vettori comuni includono UPS, FedEx, DHL e USPS.

_Attributi termine:_

* _Campo: business, order_

### carrello

_sostantivo_

Il set di prodotti che un cliente ha selezionato per l’acquisto, ma non ha ancora acquistato.
Si riferisce anche a un’area di un sito di e-commerce in cui è possibile trovare questi prodotti per la revisione e il pagamento.

_Attributi termine:_

* _Campo: business, design, product, programming_
* _Sinonimi: carrello, carrello_
* _Termini correlati: regole carrello_

### prodotto semplice

_sostantivo_

Il tipo di prodotto più semplice, un articolo fisico con una singola SKU.
I prodotti semplici dispongono di vari controlli dei prezzi e degli input che consentono di vendere varianti del prodotto.
I prodotti semplici possono essere utilizzati in associazione a prodotti raggruppati, in bundle e configurabili.
Un prodotto semplice con opzioni personalizzate è talvolta indicato come prodotto composito.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: tipi di prodotto_

### SKU

_sostantivo_

Abbreviazione di Stock Keeping Unit.
Numero o codice assegnato a un prodotto per identificare il prodotto, le opzioni, il prezzo e il produttore.

_Attributi termine:_

* _Campo: business, prezzi, prodotto, programmazione_
* _Termini correlati: catalogo condiviso_

### pagina iniziale

_sostantivo_

Una pagina promozionale con un prodotto o un annuncio pubblicitario, normalmente visualizzata prima della home page.

_Attributi termine:_

* _Campo: design_

### blocco statico

_sostantivo_

Un’unità modulare di contenuto che può essere inserita da un utente nel CMS su una pagina per visualizzare testo e immagini o eseguire snippet di codice.
I blocchi statici contengono contenuto modificabile e possono fungere da pagine di destinazione per le categorie di prodotti.
I widget possono essere aggiunti a blocchi statici per fornire funzionalità aggiuntive.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: blocco cms, blocco_

### contenuto statico

_sostantivo_

Contenuti generati dall&#39;utente (non generati dal codice) che non cambiano frequentemente.

_Attributi termine:_

* _Campo: design_
* _Termini correlati: contenuto dinamico_

### file statici

_sostantivo_

La raccolta di risorse, come CSS, font, immagini e JavaScript, utilizzate da un tema.

_Attributi termine:_

* _Campo: software commerce_

### archiviare

_sostantivo_

Il livello di ambito Commerce di &quot;store&quot; è il secondo livello della gerarchia del sito Web, che va come segue: sito Web > store > vista store.
I negozi possono essere organizzati in uno o più. Ogni archivio, potenzialmente, ha la propria categoria principale e tutti condividono i dati di catalogo e cliente.

Ogni negozio può avere più visualizzazioni dello store, che in genere vengono utilizzate per presentare la vetrina in una lingua e in una lingua diverse.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: visualizzazione archivio, sito Web_

### visualizzazione store

_sostantivo_

Il livello di ambito Commerce di &quot;visualizzazione archivio&quot; si riferisce al terzo livello nella gerarchia di siti web, store e visualizzazioni archivio.
Le visualizzazioni dello store presentano in genere la vetrina in una lingua e in una lingua diverse.
Per modificare le visualizzazioni dello store, utilizza il selettore store nell’intestazione.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: store, sito Web_

### vetrina

_sostantivo_

Il negozio online visitato dai clienti quando visitano il sito Commerce.

_Attributi termine:_

* _Campo: software commerce, prodotto_

## T

### regola fiscale

_sostantivo_

Combinazione di una classe fiscale prodotto, di una classe fiscale cliente e di un&#39;aliquota. Questa regola definisce quale calcolo dell&#39;imposta viene applicato.

_Attributi termine:_

* _Campo: business_

### modello

_sostantivo_

Abbreviazione per modello HTML o modello PHTML.
Un file PHTML contiene una combinazione di markup HTML e codice PHP per inserire contenuto dinamico nel HTML.
La maggior parte dei blocchi dispone di almeno un file PHTML (template) che contiene il HTML statico generato dal blocco.
Nei modelli Amministratore, e-mail e newsletter combinano testo, immagini e variabili con il markup HTML per produrre contenuti personalizzati inviati dal sistema.

_Attributi termine:_

* _Campo: software commerce_
* _Termini correlati: blocco_

### tema

_sostantivo_

Contiene informazioni sulla grafica e sull&#39;aspetto.
Personalizza l&#39;aspetto del negozio.
Adobe Commerce può inviare i temi nei pacchetti (Composer).
Ma i temi possono essere posizionati sotto app / design, che non è spedito in un pacchetto.
I pacchetti sono l&#39;unità di download per Composer e, tramite Commerce Marketplace, gli utenti di Commerce possono scaricare CE o EE come una serie di pacchetti, in cui i pacchetti contengono moduli, temi o pacchetti di lingue.

_Attributi termine:_

* _Campo: software commerce_

## U

### Componente interfaccia utente

_sostantivo_

Tag progettato per il software Adobe Commerce per consentire un rendering dell’interfaccia utente più semplice e flessibile.
Gli obiettivi del sistema dei componenti dell’interfaccia utente includono:

* Semplificazione della gestione del layout dei file XML
* Spostamento degli elementi dell’interfaccia utente di amministrazione da HTML+JavaScript a un sistema di widget personalizzato &quot;JavaScript puro&quot;
* Creazione di componenti dell’interfaccia utente più complessi a partire da componenti più piccoli
* Pre-rendering dei dati per i componenti dell’interfaccia utente come JSON, associazione stretta agli oggetti dati back-end
* Utilizzo dell’AJAX per aggiornare i dati dei componenti
* Presentazione di un nuovo DSL per la creazione degli elementi sopra indicati

Ulteriori informazioni: [Guida ai componenti dell&#39;interfaccia utente](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: JavaScript, layout, componente, page builder_

### VERSO L&#39;ALTO

_sostantivo_

[PWA Studi](https://github.com/magento/pwa-studio) utilizza [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) nello sviluppo.
UPWARD è un acronimo di Unified Progressive Web App Response Definition.
Un file di definizione UPWARD descrive come un server web distribuisce e supporta un Progressive Web Application.

I file di definizione UPWARD forniscono dettagli sul comportamento del server utilizzando un linguaggio dichiarativo indipendente dalla piattaforma.
Questo consente a un Progressive Web Application di eseguire su un server compatibile con UPWARD in qualsiasi lingua su qualsiasi stack tecnologico, perché l’applicazione è interessata solo al comportamento dell’endpoint HTTP dal server UPWARD.

Un server UPWARD utilizza un file di definizione per determinare il processo o il servizio appropriato per una richiesta da una shell dell&#39;applicazione.
Descrive il modo in cui il server deve gestire una richiesta e generare la risposta per essa.

Un progetto PWA può includere un file di definizione UPWARD per specificare le dipendenze del servizio.

_Attributi termine:_

* _Campo: progettazione, software commerciale, programmazione_
* _Sinonimi: PWA Studi, Definizione risposta app Web progressiva unificata_
* _Termini correlati: pwa_

## V

### Estensione in bundle fornitore

_sostantivo_

Il codice prodotto dal fornitore che estende o personalizza il comportamento di Commerce e funziona come estensione di terze parti è considerato un’estensione in bundle con il fornitore (VBE).
Le VBE vengono testate accuratamente e incluse in ogni versione supportata di Adobe Commerce.
Un VBE può includere moduli, temi e pacchetti di lingue.

Ulteriori informazioni sono disponibili nell&#39;argomento [Estensione in bundle fornitore](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Attributi termine:_

* _Campo: estensione commerce, estensione bundle fornitore, estensione, VBE_
* _Sinonimi: estensione, VBE_
* _Termini correlati: estensione, estensione nel pacchetto_

### ridimensionamento verticale

_sostantivo_

Per ridimensionamento verticale si intende l&#39;aumento della potenza di elaborazione di un singolo server o cluster mediante l&#39;aggiunta di I/O su disco o di rete, CPU o RAM.

_Attributi termine:_

* _Campo: environment_

### prodotto virtuale

_sostantivo_

Rappresenta un prodotto non fisico che può essere venduto, ad esempio iscrizione, servizio, garanzia o abbonamento.
I prodotti virtuali possono essere venduti singolarmente o inclusi nei seguenti tipi di prodotto: prodotto raggruppato e prodotto bundle.
Non richiede spedizione o inventario.

Il processo di creazione di un prodotto virtuale e di un prodotto semplice è quasi lo stesso.
Tuttavia, poiché un prodotto virtuale non viene spedito, non è disponibile alcun campo o opzione Peso per includere una gift card.

_Attributi termine:_

* _Campo: software commerce, prodotto_
* _Termini correlati: tipi di prodotto_

### tipo virtuale

_sostantivo_

I tipi virtuali sono un modo per inserire dipendenze diverse nelle classi PHP esistenti senza influenzare altre classi e senza dover creare un file di classe.
È possibile fare riferimento ai tipi virtuali solo tramite sostituzioni di argomenti in un elemento `<type>` all&#39;interno di file di.xml, mai nel codice sorgente.
Non possono essere estese e non possono essere riferimenti come dipendenze in un costruttore di classi.

_Attributi termine:_

* _Campo: programmazione_
* _Termini correlati: php_

## L

### sito web

_sostantivo_

Nel software Adobe Commerce, il livello più alto della gerarchia di un sito Web, sopra la visualizzazione store e store.
È possibile avere più siti Web e ogni sito Web può avere un nome di dominio diverso.
I siti Web possono essere configurati per la condivisione dei dati dei clienti o per non condividere i dati.

_Attributi termine:_

* _Campo: software commerciale, progettazione, prodotto_
* _Termini correlati: store, visualizzazione store_

### widget

_sostantivo_

Un [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) è un frammento di codice preparato che può essere utilizzato per inserire blocchi, collegamenti e contenuto dinamico in posizioni specifiche nelle pagine dell&#39;archivio.
Puoi utilizzare i widget per creare pagine di destinazione per campagne di marketing e visualizzare contenuti promozionali in posizioni specifiche in tutto il negozio.
I widget possono essere utilizzati anche per aggiungere elementi interattivi e blocchi di azione per sistemi di revisione esterni, chat video, votazioni e moduli di abbonamento, o per fornire elementi di navigazione per cloud di tag e cursori di immagini.

_Attributi termine:_

* _Campo: business, software commerciale, progettazione_
* _Termini correlati: blocco_

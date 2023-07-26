---
title: Note sulla versione
description: Scopri le patch disponibili per Adobe Commerce e i problemi che risolvono.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: aa52895b45363ca0fb3585f603bfe66a73803427
workflow-type: tm+mt
source-wordcount: '13735'
ht-degree: 0%

---

# Note sulla versione

Il [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) distribuisce singole patch sviluppate da Adobe e dalla comunità di Magenti Open Source. Consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce o del Magento Open Source. Puoi applicare patch ai progetti Adobe Commerce e Magento Open Source indipendentemente da chi ha sviluppato la patch. Ad esempio, puoi applicare ai progetti Adobe Commerce una patch sviluppata dalla community.

>[!INFO]
>
>Consulta [Applicare le patch](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) per istruzioni sull’applicazione di patch ai progetti Adobe Commerce o Magento Open Source. Consulta [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella Guida all&#39;aggiornamento software per esaminare l&#39;elenco completo delle patch rilasciate.

>[!INFO]
>
>Per informazioni su [!DNL quality patches] creato dalla community per il Magento Open Source, vedi [note sulla versione](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui l’indirizzo di spedizione predefinito nella fase di spedizione del pagamento viene compilato automaticamente con un indirizzo di prelievo in-store selezionato in precedenza.
* **ACSD-52041** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema se il messaggio di errore: *[ERRORE] [!DNL Page Builder] è stato eseguito il rendering per 5 secondi senza rilasciare blocchi.* viene visualizzato nel browser Chrome quando si salva il contenuto modificato con [!DNL Page Builder].
* **ACSD-52095** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema se `manage_stock` il valore veniva erroneamente impostato su 0 nel file CSV dopo l’esportazione del prodotto.
* **ACSD-51358** (per Adobe Commerce >=2.4.5 &lt;2.4.7): è stato risolto il problema che causava la rimozione di un aggiornamento pianificato senza data di fine, con la conseguente rimozione di altri aggiornamenti pianificati per la stessa entità.
* **ACSD-48070** (per Adobe Commerce >=2.3.7 &lt;2.4.7): risolve il problema se la modifica di un aggiornamento pianificato attiva un’eccezione.
* **ACSD-51890** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema se [!UICONTROL Submit review] può essere cliccato più volte senza [!DNL Google reCAPTCHA] Convalida v3.
* **ACSD-51984** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema se non è selezionata *[!UICONTROL Use Default Value]* e *[!UICONTROL non-default product field]* I valori non vengono salvati per la seconda visualizzazione del sito Web, dello store e dello store.
* **ACSD-52398** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l’errore *La quantità richiesta non è disponibile* ciò si verifica quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
* **ACSD-52786** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6): risolve il problema se una condizione della regola del catalogo *SKU è* si applica a tutti i prodotti che iniziano con lo SKU specificato.
* **ACSD-52921** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): risolve il problema relativo a un errore interno che si verificava se si richiedevano i dettagli del carrello a GraphQL in presenza di un prodotto configurabile esaurito nel carrello.
* **ACSD-51683** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): risolve il problema che impediva l’aggiunta di un’opzione personalizzabile al carrello tramite GraphQL.
* **ACSD-52133** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): risolve il problema che impediva il salvataggio di un account cliente dopo un aggiornamento.
* **ACSD-52202** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui la quantità vendibile delle scorte predefinite viene erroneamente modificata in 0 quando le scorte non predefinite vengono modificate in 0 qtà per l&#39;evasione degli ordini.
* **ACSD-51265** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema con `catalog_product_price` prestazioni di reindicizzazione quando nel sistema sono presenti troppi prodotti in bundle.
* **ACSD-52831** (per Adobe Commerce >=2.3.7 &lt;2.4.7): risolve il problema che impediva ai clienti di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.
* **ACSD-51845** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7): è stato risolto il problema che impediva l’aggiornamento in blocco asincrono dell’API REST dei prodotti successivi con prezzi di livello e set di attributi diversi.
* **ACSD-52815** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l’input per il campo della quantità di un’origine non predefinita supporta solo fino a 6 cifre, a differenza di 8 per un titolo predefinito.
* **ACSD-51149** (per Adobe Commerce >=2.3.7 &lt;2.4.7): è stato risolto il problema per cui l’Importazione pianificata con autorizzazioni di catalogo abilitate invalida gli indicizzatori e quindi effettua il flushing della cache in base alla cron.
* **ACSD-50815** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6): risolve il problema se la quantità decimale per un prodotto semplice non può essere utilizzata per una nuova opzione Prodotto in bundle.
* Versioni aggiornate per ACSD-47803.
* Titolo aggiornato per ACSD-51892.
* Aggiornamento di ACSD-51379.
* Aggiornamento di ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema se un utente amministratore non viene reindirizzato correttamente dopo aver selezionato una visualizzazione store durante la creazione di un nuovo ordine in Admin.
* **ACSD-50813** (per Adobe Commerce >=2.4.5 &lt;2.4.7): è stato risolto il problema che impediva all’amministratore di aggiungere prodotti in bundle contenenti una barra nello SKU con [!UICONTROL Add Products by SKU] all&#39;ordine di amministrazione.
* **ACSD-51630** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): è stato risolto il problema che rallentava il download delle pagine di amministrazione a causa della grande quantità di messaggi di sistema.
* **ACSD-51853** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corregge il problema per cui gli stili di testo copiati non vengono applicati quando si utilizza [!UICONTROL Page Builder].
* **ACSD-52160** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7): risolve il problema per cui il risultato della convalida del prodotto in base alla regola del prezzo del carrello non veniva valutato correttamente in base alla condizione della regola &quot;Se un articolo viene TROVATO/NON TROVATO nel carrello con Tutte/Qualsiasi di queste condizioni true&quot;.
* **ACSD-51636** (per Adobe Commerce >=2.4.5 &lt;2.4.7): è stato risolto il problema che impediva all’amministratore della società di aggiungere nuovi utenti dalla sezione account cliente nonostante l’esistenza di tutti i ruoli e le autorizzazioni necessari.
* **ACSD-51739** (per Adobe Commerce >=2.4.6 &lt;2.4.7): risolve il problema della restituzione di un errore quando il `structure_id` è richiesto in una richiesta CompanyTeam GraphQL.
* **ACSD-51857** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7): risolve il problema della lentezza delle prestazioni del `aggregate_sales_report_bestsellers_data` report cron su sales_order e `sales_order_item` tabelle di database dovute al modo in cui è stata scritta la query di dati principale.
* **ACSD-48448** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo a una situazione di tipo &quot;race condition&quot; che si verifica durante l’annullamento dell’ordine e causa la duplicazione della voce `inventory_reservation` tabella.
* **ACSD-52689** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6): è stato risolto il problema che impediva il caricamento delle immagini nell’archiviazione Amazon S3 utilizzando l’API REST.
* **B2B-2674** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiungi funzionalità di caching alla query 1customAttributeMetadata1 GraphQL.
* Sono state aggiunte nuove versioni di ACSD-44938.
* Sono stati aggiunti requisiti per ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corregge il comando di rollback del database per un caso in cui il dump del database contiene trigger e un *delimitatore* Comando SQL.
* **ACSD-50512** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il *Errore: il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova.* errore che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto.
* **ACSD-50949** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7): risolve il problema se il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti quando viene utilizzato insieme al filtro SKU.
* **ACSD-51645** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): corregge l’errore generato durante il salvataggio di una nuova Regola prezzo carrello se l’estensione `Magento_OfflineShipping` è disabilitato.
* **ACSD-50895** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema se [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
* **ACSD-51102** (per Adobe Commerce >=2.4.2 &lt;2.4.7): risolve il problema se una regola di catalogo applicata a un numero elevato di prodotti non viene indicizzata correttamente quando la regola è abilitata da un aggiornamento pianificato.
* **ACSD-50368** (per Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corregge il problema se il `group_id` viene ignorato quando un cliente viene creato tramite Async REST API o Async Bulk REST API.
* **ACSD-51497** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Risolve il problema che impediva al cliente di ordinare una pagina di catalogo per attributo personalizzato del tipo a discesa.
* **ACSD-51408** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt; 2.4.7) - Corregge il problema se lo stato dell’articolo dell’ordine non è impostato correttamente su *[!UICONTROL Backordered]*.
* **ACSD-51735** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge il problema se lo stato dell’articolo dell’ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando lo stock del prodotto è *0*.
* **ACSD-51792** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6): risolve il problema se una pagina non ha l’evento di impression quando [!DNL Google Tag Manager] 4 è attivato.
* **ACSD-51471** (per Adobe Commerce >=2.4.3 &lt;2.4.7): risolve il problema che impediva a un utente amministratore di salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
* **ACSD-51700** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): è stato corretto l’errore che si verificava quando si cambiavano le visualizzazioni dello store in una pagina di modifica del prodotto scaricabile nell’amministratore.
* **ACSD-51120** (per Adobe Commerce >=2.3.7 &lt;2.4.3): è stato risolto il problema per cui la cache delle richieste di GraphQL GET non veniva cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging.
* **ACSD-51240** (per Adobe Commerce >=2.4.4 &lt;2.4.6): risolve il problema relativo alla mancanza del file caricato se la registrazione viene effettuata tramite il modulo di registrazione della società.
* **ACSD-51907** (per Adobe Commerce >=2.4.2 &lt;2.4.3): risolve il problema che impediva a un utente amministratore con restrizioni di creare una nota di credito con rimborso offline.
* **ACSD-52148** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema se [!DNL Google V3 reCAPTCHA] Talvolta l’accesso come amministratore non riesce.
* **ACSD-51431** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema se lo stato di un indicizzatore è *funzionante* anche se non sono presenti nuove voci nel changelog.
* **ACSD-51892** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema di prestazioni che si verificava quando i file di configurazione venivano caricati più volte.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema se [!UICONTROL Page Builder's] se si verificano più errori, l’amministratore non può salvare un prodotto senza autorizzazioni per il contenuto.
* **ACSD-51305** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che impediva la disponibilità di prodotti secondari configurabili esauriti nella risposta di GraphQL.
* **ACSD-50621** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema se [!UICONTROL Tier Prices] per i diversi siti web del catalogo condiviso non sono visibili quando si tenta di modificarli in un ambiente multi-sito.
* **ACSD-51041** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Migliora le prestazioni dell’indicizzatore dei prezzi.
* **ACSD-51379** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema relativo alle modifiche apportate al contenuto di testo della pagina tramite [!UICONTROL Page Builder] non vengono salvate.
* **ACSD-49480** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): risolve il problema se al carrello viene applicata una sola regola di prezzo del carrello.
* **ACSD-51230** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema di eliminazione del conto gift card quando viene elaborato un rimborso parziale di un prodotto semplice da un ordine.
* **ACSD-51238** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7): risolve il problema della rimozione dell’origine dell’inventario quando si aggiornano i prodotti configurabili e si modifica il prezzo.
* **ACSD-50794** (per Adobe Commerce >=2.4.1 &lt;2.4.7): risolve il problema per cui i dettagli del messaggio regalo o della confezione regalo non vengono aggiornati nel database quando vengono rimossi tramite GraphQL.
* **ACSD-51528** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema se *x_forwarded_for* la colonna contiene valori Null nel *sales_order* tabella.
* **ACSD-50849** (per Adobe Commerce >=2.4.4 &lt;2.4.6): è stato risolto il problema che causava una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti quando si aggiungeva un nuovo prodotto alla categoria dopo aver cancellato la cache.
* **ACSD-51294** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): risolve il problema per cui prezzo GTM/GA, quantità, imposte, spedizione e ricavi vengono inviati come stringa a [!DNL Google Analytics] e GTM.
* **ACSD-51204** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): risolve il problema che impedisce la restituzione di un prodotto completamente venduto dopo la creazione di una nota di credito.
* **ACSD-51291** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Corregge il problema per cui un amministratore con accesso limitato a un sito web può aggiungere immagini/video al prodotto assegnato a più siti web.
* Sono state aggiunte nuove versioni di ACSD-50336.
* Sostituzione delle patch ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Corregge il problema per cui Recaptcha v2 non si ricarica dopo l’invio di un pagamento non riuscito.
* **ACSD-50817** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Ottimizza il processo Cron `sales_clean_quotes` per eseguire più velocemente.
* **ACSD-49392** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corregge il problema se lo stato dell&#39;ordine cambia in chiuso dopo un rimborso parziale per un prodotto nel pacchetto.
* **ACSD-51036** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5): è stato risolto il problema che causava la sovrascrittura delle informazioni sullo stato della spedizione nelle chiamate API REST simultanee in [!UICONTROL Items Ordered] tabella.
* **ACSD-50858** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Migliora le prestazioni per il caricamento dei contenuti dei banner.
* Sono state aggiunte nuove versioni per MDVA-39305-v2, ACSD-45169.
* Sono state aggiornate le patch ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (per Adobe Commerce e Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Corregge il problema per cui le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo disponibile o il prezzo viene modificato.
* **ACSD-50367** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva il funzionamento dell’esportazione dell’indirizzo del cliente quando si creava un attributo dell’indirizzo del cliente senza valori a selezione multipla.
* **ACSD-49877** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema se la riproduzione automatica video non funziona su dispositivi mobili [!DNL Safari] quando il video è collegato direttamente a un file video remoto e non a un servizio di streaming.
* **ACSD-50165** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l’errore *Impossibile eliminare il file. Avviso!unlink: file o directory non esistente* durante lo svuotamento della cache JS/CSS dall’amministratore.
* **ACSD-49737** (per Adobe Commerce e Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Corregge il problema relativo al caso in cui un coupon venga erroneamente contrassegnato come utilizzato dopo un pagamento non riuscito con carta.
* **ACSD-50814** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che impediva all’utente amministratore di creare una nota di credito.
* **ACSD-50116** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva all’utente amministratore di creare una riscrittura URL per sottocategorie di livello 3 o inferiore.
* **ACSD-49513** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5): è stato risolto il problema che impediva la sincronizzazione dell’archiviazione remota a causa di file da 0 byte.
* **ACSD-46683** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema relativo al prezzo di spedizione *Non ancora calcolato*.
* **ACSD-49129** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema se *[!UICONTROL content]* (codice immagine base64) non viene restituito in `rest/V1/products/sku/media` risposte API di product media.
* **ACSD-50276** (per Adobe Commerce >=2.4.0 &lt;2.4.7): risolve il problema se il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla.
* **ACSD-50527** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge l’errore che si verifica quando si salva una pagina con un blocco dinamico vuoto.
* **ACSD-49973** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Migliora le prestazioni del recupero dei prodotti in bundle tramite GraphQL.
* **ACSD-51114** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): risolve il problema della scomparsa casuale di un prodotto da cataloghi di grandi dimensioni quando l’indicizzazione asincrona è abilitata. Migliora le prestazioni della reindicizzazione asincrona per i cataloghi di grandi dimensioni.
* **B2B-2598** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiunta della funzionalità di caching al [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], e [!UICONTROL storeConfig] Query GraphQL.
* Sono state aggiunte nuove versioni per MDVA-42806, ACSD-48627 e ACSD-46815.
* Aggiornamento dei metadati delle patch per ACSD-49773, ACSD-47179 e ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui un’e-mail pronta per il ritiro viene inviata dall’API quando l’ordine non è pronto per il ritiro.
* **ACSD-49822** (per Adobe Commerce >=2.3.7 &lt;2.4.7): risolve il problema se gli aggiornamenti in [!UICONTROL Requisition List] pagina non si riflettono sul [!UICONTROL Print Requisition List].
* **ACSD-48771** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): è stato risolto il problema relativo all’aggiornamento del tipo di contenuto column-block da una versione precedente [!DNL Page Builder] versioni.
* **ACSD-49464** (per Adobe Commerce >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva lo spostamento di fatture, spedizioni e note di accredito dall’archivio se l’ID dell’ordine è diverso.
* **ACSD-49773** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6): è stato risolto il problema che impediva l’esportazione del prodotto se AWS S3 veniva utilizzato come archiviazione remota.
* **ACSD-49748** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli inviti non possono essere inviati.
* **ACSD-49502** (per Adobe Commerce >=2.4.3 &lt;2.4.7): è stato risolto il problema che impediva l’aggiornamento corretto del collegamento scaricabile dopo l’applicazione di un aggiornamento di staging al prodotto scaricabile.
* **ACSD-49527** (per Adobe Commerce >=2.4.2 &lt;2.4.7): è stato risolto il problema che impediva la corretta visualizzazione della paginazione nei ruoli aziendali di GraphQL.
* **ACSD-49706** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema se il valore predefinito viene salvato per un attributo di campione visivo quando non viene selezionato alcun valore.
* **ACSD-49835** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui il valore della casella di controllo Usa predefinito non viene salvato correttamente a livello di archivio per un attributo a selezione multipla.
* **ACSD-49898** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): è stato risolto il problema che causava la generazione di un’eccezione da parte della griglia prodotti quando un prodotto in bundle aveva un prezzo speciale che superava i 1000.
* **ACSD-50234** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.5) - Risolve il problema con il nome del cliente errato nell’e-mail di conferma se si effettua un ordine con [!DNL PayPal].
* **ACSD-49960** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui il filtro per data non funziona per la griglia degli ordini del cliente.
* **ACSD-49849** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6): risolve il problema della sostituzione dell’e-mail del cliente con [!DNL PayPal] e-mail quando effettui un ordine con [!DNL PayPal Express] tramite GraphQL.
* **ACSD-49839** (per Adobe Commerce >=2.3.7 &lt;2.4.7): risolve il problema relativo alla visualizzazione di un errore in Amministrazione quando i prodotti presentano virgolette singole o doppie in SKU.
* **ACSD-49970** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge la gestione errata degli errori di GraphQL quando [!DNL New Relic] il reporting è attivato.
* **ACSD-50260** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): risolve il problema se i risultati della ricerca dei prodotti GraphQL sono limitati solo a 10.000.
* **ACSD-48813** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui la ricerca non mostra risultati rilevanti in base al peso della ricerca degli attributi.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corregge il problema per cui una regola del prezzo di catalogo creata in base all’attributo Sì/No non considera l’ambito selezionato.
* **ACSD-47704** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema se il prodotto in bundle mostra il prezzo dei soli prodotti in stock.
* **ACSD-49370** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema se *Data e ora* l’attributo del prodotto ha un *FilterMatchTypeInput* digita nello schema di GraphQL.
* **ACSD-48807** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corregge il problema per cui le recensioni dei prodotti dei clienti non vengono filtrate tramite storeview tramite GraphQL.
* **ACSD-49433** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui l’importo predefinito viene visualizzato come subtotale nel carrello per gift card con un importo aperto.
* **ACSD-48866** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che si verificava in caso di errore durante la richiesta del feed RSS per le categorie.
* **ACSD-48784** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che causava la memorizzazione errata nella cache dei prezzi del segmento cliente tra i gruppi di clienti.
* **ACSD-48857** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui un utente non è in grado di salvare le modifiche dopo la modifica con Page Builder.
* **ACSD-49065** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema per cui gli elementi delle offerte non sono visibili in Amministrazione se assegnati solo alle azioni personalizzate.
* **ACSD-49179** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il rapporto Ordini mostra importi non corretti in caso di valute diverse per negozi diversi.
* **ACSD-49286** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): risolve il problema se un prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.
* **ACSD-49574** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Aggiunge funzionalità per supportare gli aggiornamenti dei prodotti Gift Card nel carrello tramite GraphQL.
* Aggiornamento della patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (per Adobe Commerce >=2.4.1 &lt;2.4.7): risolve il problema relativo all’utilizzo dell’indirizzo di spedizione predefinito anziché di uno nuovo quando si effettua un ordine utilizzando un preventivo negoziabile.
* **ACSD-48059** (per Adobe Commerce >=2.3.7 &lt;2.4.7): risolve il problema che impediva agli esercenti di salvare il file &quot;[!UICONTROL Match product by rule]&quot; nella categoria.
* **ACSD-48216** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corregge il problema dove [!UICONTROL AUTO_INCREMENT] del [!UICONTROL inventory_source_item] aumento della tabella in corrispondenza di [!UICONTROL UPDATE] operazione.
* **ACSD-47908** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corregge l’errore &quot;È previsto un valore minore o uguale a 0&quot; quando si selezionano l’origine e la quantità nella fase di spedizione durante il pagamento.
* **ACSD-49497** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema se un ordine rimane nello stato di elaborazione dopo la spedizione e viene applicato un rimborso parziale.
* **ACSD-48694** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Corregge il problema se l’errore &quot;Richiesta di modifica dello stato non valido&quot; impedisce a un cliente di effettuare un ordine.
* **ACSD-49013** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui la conferma e-mail non viene tradotta nelle impostazioni internazionali del sito web quando si creano clienti utilizzando l’API in blocco.
* **ACSD-48164** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui un amministratore con restrizioni non può salvare un valore a livello di sito Web.
* **ACSD-48404** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema per cui &quot;Ricorda paginazione categoria = Sì&quot; causa un errore quando si preme il pulsante Indietro del browser.
* **ACSD-48634** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge gli errori JS in una pagina di aggiornamento dell’area di gestione temporanea quando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; è abilitato.
* **ACSD-49042** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Risolve il problema che impediva di ordinare da Storefront un prodotto con ordine inevaso.
* Aggiornate patch: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (per Adobe Commerce e Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Corregge il problema per cui le notifiche di calo dei prezzi non vengono sempre inviate a causa del caching a livello di applicazione.
* **ACSD-48661** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): risolve il problema se il limite di credito della società è maggiore di 999, il separatore con virgola impedisce il salvataggio della società a causa di un errore di convalida.
* **ACSD-48773** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema se il modello e-mail dei punti premio viene prelevato dall’archivio errato.
* **ACSD-48587** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva ai caratteri speciali HTML nelle regole di corrispondenza del widget prodotti di visualizzare i prodotti corrispondenti.
* **ACSD-48212** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6): risolve il problema se l’importazione del prodotto assegna il prodotto all’origine errata.
* **ACSD-47988** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6): risolve il problema relativo alla rimozione dei tag HTML dalla descrizione del prodotto page builder.
* **ACSD-48366** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): risolve il problema se l’immagine del prodotto non viene visualizzata nel modello e-mail Torna a magazzino.
* **ACSD-48417** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): risolve il problema della visualizzazione di un errore SQL dopo la creazione di una modifica della pianificazione per un prodotto e il salvataggio di un altro prodotto.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6): risolve il problema se la reindicizzazione dei prezzi del prodotto non funziona se il prodotto bundle non viene assegnato ad alcun sito web.
* **ACSD-48262** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6): risolve il problema se i prodotti non sono visibili sul front-end quando &quot;Consenti tutti i prodotti per pagina&quot; è impostato su Sì.
* **ACSD-48293** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4): risolve il problema relativo al esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte.
* **ACSD-47520** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che determinava la perdita di punti premio da parte dei clienti al momento della creazione di una nota di credito.
* **ACSD-48044** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema se l’applicazione di più carte regalo a un singolo ordine con spedizione multipla impedisce l’inserimento di ordini.
* **ACSD-48300** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema che impediva la creazione di un reso se il prodotto configurabile veniva rimosso.
* **ACSD-47910** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema di ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie di entità.
* **ACSD-47292** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): è stato risolto il problema che impediva la disponibilità di prodotti in bundle esauriti nella risposta di GraphQL se &quot;show out-of-stock products&quot; (Mostra prodotti esauriti) era impostato su Sì.
* **ACSD-48234** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui il risultato della ricerca nel catalogo mostra un conteggio degli articoli di categoria errato quando l’opzione &quot;mostra esaurito&quot; è abilitata.
* **ACSD-48313** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Risolve il problema per cui la colonna &quot;configurable_variables&quot; non viene analizzata se il valore dell’attributo contiene una virgola. Lo stesso algoritmo di analisi viene utilizzato per &quot;additional_attributes.
* **ACSD-48627** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui il prodotto configurabile esaurito causa un errore durante l’invio di una richiesta GraphQL per ottenere i dettagli del carrello.
* Aggiornamento della patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui non vengono generati URL compatibili con SEO per i prodotti che hanno *url_key* attributi sostituiti a livello di visualizzazione store.
* **ACSD-46865** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): è stato risolto il problema che impediva il popolamento della griglia delle note di spedizione e di credito se l’indicizzazione asincrona era abilitata.
* **ACSD-47004** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6): risolve il problema se l’IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.
* **ACSD-47803** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che causava la visualizzazione dei campioni di prodotto configurabili esauriti come disponibili.
* **ACSD-47137** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Migliora la velocità di caricamento della galleria di immagini quando la cartella pub/media è molto grande.
* **ACSD-46770** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): risolve il problema dell’invio delle e-mail degli ordini di amministrazione anche quando *Conferma ordine e-mail* non è selezionato.
* **ACSD-47955** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui GraphQL non visualizza correttamente lo sconto sul carrello.
* **ACSD-46617** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema se *Continua con l&#39;estrazione* il pulsante è disattivato anche se il subtotale è maggiore del *Importo minimo ordine*.
* **ACSD-47079** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5): risolve il problema per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei sottoprodotti cambia tramite REST API POST /rest/V1/inventory/source-items.
* **ACSD-47336** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Correzioni *Si è verificato un errore.* durante l’eliminazione delle notifiche nell’amministrazione di Commerce.
* **ACSD-47559** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema se l’area Anteprima modello e-mail non è completamente visibile.
* **ACSD-47920** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che consentiva di effettuare gli ordini tramite l’API Rest come utente guest anche quando *Consenti estrazione guest* è disattivato.
* Patch sostituite: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che impediva a un amministratore con accesso limitato a un ambito specifico di eliminare le revisioni dei prodotti.
* **ACSD-47107** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5): risolve il problema se lo sconto Regola prezzo catalogo viene applicato alle opzioni di prodotto personalizzate.
* **ACSD-47232** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): risolve il problema che impediva l’applicazione di coupon con condizioni di peso totale nell’amministratore.
* **ACSD-46519** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corregge il problema se la richiesta categoryList di GraphQL restituisce un valore product_count errato per una categoria di ancoraggio.
* **ACSD-47027** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge una richiesta lenta di aggiornamentoCompanyRole GraphQL.
* **ACSD-47666** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che impediva il funzionamento della funzione filtro nella griglia Amministrazione > Sistema > Autorizzazioni > Ruoli utente > Ruolo > Utenti ruolo.
* **ACSD-47497** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che impediva alla scheda Servizi di essere visibile in Configurazione in Admin.
* Aggiornamento della patch: ACSD-47743.
* Patch sostituite: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Corregge i _Tentativo di accedere all&#39;offset dell&#39;array sul valore del tipo booleano_ errore durante l’accesso a determinati percorsi di categoria non esistenti per prodotti noti in PHP 7.4.
* **ACSD-47332** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): risolve il problema relativo a un errore cron, che viene segnalato solo se si esegue tra le 00:00 e le 00:59 UTC.
* **ACSD-47280** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che impediva il corretto funzionamento della funzione di catalogo condiviso in un ambito specifico.
* **ACSD-47106** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): risolve il problema che impediva il salvataggio di un valore in un nuovo attributo personalizzato nella pagina di creazione di una società.
* Aggiornamento della patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6): è stato risolto il problema che si verificava se un utente riceveva un errore durante l’assegnazione di un numero elevato di origini di prodotto.
* **ACSD-46856** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): migliora le prestazioni aggiornando i prezzi dei livelli tramite Sistema > Configurazione > Importazione > Advanced Pricing.
* **ACSD-46541** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4): è stato risolto il problema che impediva a un utente amministratore di creare una nota di credito in caso di eliminazione di una voce dell’ordine.
* **ACSD-46581** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): risolve il problema se il totale delle imposte stimato non viene aggiornato dopo aver selezionato un paese nel carrello.
* **ACSD-46618** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che causava la visualizzazione di prezzi non corretti nella cache da parte del widget dell’elenco di prodotti per un cliente che aveva effettuato l’accesso.
* **ACSD-46674** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): risolve il problema della visualizzazione delle opzioni personalizzate di un tipo di immagine come HTML nelle e-mail dei clienti.
* **ACSD-46988** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): è stato risolto il problema che si verificava se la richiesta API &quot;currency&quot; di GraphQL restituiva valori NULL per una valuta personalizzata.
* **ACSD-47076** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corregge il problema per cui i video Vimeo non possono essere riprodotti nella vetrina.
* **ACSD-45071** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corregge il problema se l’origine predefinita viene aggiunta al prodotto durante l’importazione.
* **AC-3023** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Aggiornare lo schema DHL alla versione 10.0 più recente.
* Patch aggiornate: MDVA-42584.
* Patch sostituite: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema per cui un utente ottiene uno stato dell&#39;ordine errato quando viene rimborsato utilizzando il credito del negozio.
* **ACSD-46703** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Risolve il problema che impediva il trascinamento delle opzioni personalizzate in una pagina di modifica del prodotto.
* **ACSD-44851** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corregge il problema che impediva l’apertura o l’espansione di una categoria con sottocategorie.
* **ACSD-46815** (*per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corregge il problema se la richiesta della struttura ad albero delle categorie è limitata a 20 categorie.
* **ACSD-45675** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Risolve il problema per cui l&#39;esportazione del prodotto utilizza i nomi di categoria del *Visualizzazione store predefinita* ambito.
* **ACSD-46869** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corregge il problema per cui un prodotto configurabile nel carrello non viene aggiornato tramite un *API REST DI PUT* richiesta senza modificare la quantità del prodotto.
* **MDVA-42768-V2** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui il prodotto Configurabile visualizza il prezzo regolare come *0* quando *Visualizza esaurito* è *Sì*.
* Patch aggiornate: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleta: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema se la richiesta della struttura ad albero delle categorie è limitata a 20 categorie.
* **ACSD-45781** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corregge il problema per cui il campo di ricerca della vetrina non viene visualizzato sul dispositivo mobile.
* **ACSD-46192** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;2.4.5*) - Corregge il problema relativo all&#39;utilizzo di `async/bulk/V1/configurable-products/bySku/options` endpoint.
* **ACSD-46404** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - È stato risolto il problema che impediva all&#39;utente amministratore di accedere dopo l&#39;aggiornamento alla versione 2.4.4.
* Patch aggiornate: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui la mutazione di un prodotto GraphQL per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all’archivio richiesto.
* **ACSD-46146** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corregge il problema per cui due e-mail di conferma dell’ordine vengono inviate dopo aver effettuato un ordine dall’Amministratore.
* **ACSD-45255** (*per Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corregge un&#39;eccezione nella pagina Report scorte in esaurimento per un utente amministratore con restrizioni.
* **ACSD-45488** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corregge il problema per cui un prodotto configurabile con più sorgenti non viene restituito automaticamente in In Stock.
* **ACSD-45754** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui i punti Ricompensa non vengono aggiunti dopo l&#39;applicazione di un coupon al carrello.
* **ACSD-45849** (*per Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corregge il problema della perdita dei metadati video dopo l&#39;applicazione di un aggiornamento di staging.
* **ACSD-45257** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corregge il problema per cui GraphQL non visualizza correttamente uno sconto sul carrello.
* **ACSD-44938** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema in cui `VAT_ID` non può essere applicato in una richiesta GraphQL per un utente guest.
* Patch aggiornate: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corregge il problema relativo al calcolo errato della quantità di scorte per un prodotto virtuale dopo la creazione di una nota di credito.
* **ACSD-43887** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema che causa la visualizzazione di dettagli non corretti nella pagina Pagamento di pagamento checkout quando sono abilitati gli ordini di acquisto per le società.
* **ACSD-45143** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema in cui il `setShippingAddressesOnCart` la mutazione non consente di impostare il codice di area numerico come *area geografica*.
* **ACSD-44591** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corregge l’errore che si verifica quando un ordine viene effettuato senza conferma CAPTCHA.
* **ACSD-45520** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corregge il problema per cui le opzioni dei campioni non sono preselezionate nella pagina dei dettagli del prodotto quando un utente modifica prodotti configurabili dal carrello.
* **ACSD-45169** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6*) - Corregge il problema in cui [!DNL Visual Merchandiser] non visualizza il prezzo e le azioni corretti per un prodotto configurabile dopo l’applicazione di un aggiornamento di staging.
* **ACSD-45424** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corregge il problema che causa la creazione di un compenso errato per la prenotazione dopo un rimborso parziale (nota di credito).
* **MDVA-42807** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui il simbolo di valuta personalizzato non viene visualizzato sulla vetrina.
* Aggiornate patch: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Risolve il problema relativo ai calcoli errati dei totali degli ordini nel rapporto Ordini per l&#39;utente amministratore con restrizioni.
* **MDVA-44940** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge l&#39;errore SQL che si verifica durante il salvataggio della categoria dall&#39;amministratore.
* **MDVA-44562** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corregge il problema per cui l&#39;ID store non predefinito per gli articoli dell&#39;offerta viene sostituito dall&#39;ID store predefinito, nonostante la richiesta GraphQL provenga dalla vista store non predefinita.
* **MDVA-43167** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui l&#39;azione di massa griglia ordini amministratore non è applicabile per più pagine quando l&#39;utente amministratore seleziona tutti gli ordini.
* **MDVA-44044** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Risolve il problema che impediva la visualizzazione di un prodotto sulla pagina della categoria dopo l&#39;assegnazione a un nuovo sito Web.
* **MDVA-42509** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corregge il problema che impediva il caricamento di un file CSV per un ordine rapido, generando un *Impossibile inviare il cookie* errore.
* Patch aggiornate: MDVA-41061, MDVA-42584.
* Il prefisso per il nuovo [!DNL Quality Patches Tool] le patch verranno modificate da *MDVA* a *ACSD* a causa di modifiche di processo interne.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui non è possibile aggiungere un articolo al carrello se la quantità minima dell&#39;articolo è già nel carrello.
* **MDVA-44887** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corregge il *Sintassi non rilevataErrore: token imprevisto &#39;const&#39;* nel pannello di amministrazione.
* **MDVA-43718** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correzioni *Il consumatore non è autorizzato ad accedere a %resources.* errore visualizzato quando si accede a un catalogo condiviso da un’integrazione personalizzata.
* **MDVA-44660** (*per Adobe Commerce e Magento Open Source >=2,4.2-p1 &lt;2,4.5*) - Corregge il problema in cui il carattere accento grave ``` ` ``` non può essere usato per il nome e il cognome di un cliente.
* **MDVA-40896** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il *Errore: TypeError: argomento 3 passato al Magento* errore nell’API di massa del prodotto asincrona.
* **MDVA-38559** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corregge il */V1/customers/search API* per i clienti con più di un abbonamento.
* **MDVA-44533** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.4*) - Risolve il problema relativo all&#39;errata applicazione dello sconto a un prodotto secondario del bundle.
* Patch aggiornate: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema se i prodotti *Non visibile singolarmente* viene comunque visualizzato nei risultati della ricerca avanzata del catalogo.
* **MDVA-44100** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui tutti gli FPT vengono assegnati all’ultimo prodotto nel carrello e reimpostati per altri prodotti.
* **MDVA-43605** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui i dati dell’ordine restituiscono valori negativi per i totali delle righe quando si utilizza l’API Rest.
* **MDVA-43102** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui la quantità vendibile non viene aggiornata correttamente quando viene effettuato un rimborso tramite API REST.
* **MDVA-43178** (*per Adobe Commerce e Magento Open Source >=2,4,3-p2 &lt;2,4,5*) - Corregge il problema per cui non è possibile recuperare in GraphQL un token cliente per un archivio personalizzato.
* **MDVA-43859** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema in cui l&#39;errore *Nessuna entità di questo tipo con customerId =* viene registrato quando un cliente eliminato tenta di accedere.
* **MDVA-44147** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui una richiesta GraphQL non restituisce gli elenchi delle richieste di acquisto.
* **MDVA-44505** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge i problemi in cui l&#39;applicazione di punti premio GraphQL non aggiorna il totale complessivo e in cui il credito del negozio viene applicato più volte durante il posizionamento dell&#39;ordine.
* Patch aggiornate: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge il problema per cui la Regola prodotto correlata funziona solo quando Segmento cliente è impostato su *Tutti*.
* **MDVA-39605** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il valore TTL (data di scadenza) della cache Redis è errato.
* **MDVA-43862** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corregge il problema per cui il cliente non può aggiornare gli articoli del carrello a causa di un GraphQL *Mutazione UpdateCartItems* errore.
* **MDVA-43824** (*per Adobe Commerce e Magento Open Source >=2,3,6 &lt;=2,3,7-p3 || >=2,4,1 &lt;2,4,5*) - Corregge il problema relativo alla visualizzazione di un errore in caso di annullamento di ordini con uno sconto.
* **MDVA-43451** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema in cui l&#39;errore *Impossibile trovare l&#39;archivio richiesto. Verifica l’archivio e riprova.* viene visualizzato durante la configurazione di un catalogo condiviso per un sito Web specifico.
* **MDVA-43491** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corregge il problema per cui l&#39;etichetta dell&#39;immagine di base non viene aggiornata durante l&#39;importazione di prodotti per un sito Web multi-store.
* **MDVA-43601** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo ai trigger mancanti dopo la reindicizzazione completa.
* **MDVA-42046** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2,4,0 &lt;2,4,5*) - Risolve il problema relativo all&#39;assegnazione di un valore errato a un attributo di prodotto con un campo di immissione data durante l&#39;aggiornamento di un prodotto.
* **MDVA-43935** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema relativo alla visualizzazione doppia del prodotto Upselling.
* **MDVA-44188** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema relativo alle e-mail inviate dal sistema con `.-` negli indirizzi non vengono inviati.
* **MDVA-42283** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il formato data-ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali in francese non è valido.
* Patch aggiornate: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Sono stati aggiunti i metadati delle patch per [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui l&#39;utente può modificare l&#39;ora di inizio di un aggiornamento pianificato attivo.
* **MDVA-42410** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui nei rapporti coupon viene visualizzata solo la valuta di base predefinita.
* **MDVA-41136** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema in cui la data di scadenza del `mage-cache-sessid` non viene esteso, con conseguente pulizia dei dati del cliente.
* **MDVA-39993** (*per Adobe Commerce e Magento Open Source >=2,3,5 &lt;=2,3,7-p2 || >=2,4,0 &lt;2,4,4*): risolve il problema per cui le modifiche di inventario eseguite tramite API non vengono applicate alla pagina del prodotto sul front-end.
* **MDVA-42855** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui un nuovo indirizzo del cliente non viene salvato nella rubrica durante il pagamento.
* **MDVA-42645** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*): risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito del negozio è disabilitata.
* **MDVA-43414** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corregge l&#39;errore irreversibile PHP che si verifica quando si esegue `inventory.reservations.updateSalabilityStatus` mette in coda il consumatore negli SKU numerici.
* **MDVA-41628** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*): è stato corretto il problema per cui gli utenti amministratori con restrizioni esistenti accedono alle nuove risorse quando vengono aggiunti nuovi moduli.
* **MDVA-43348** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la richiesta GraphQL di gift card mostra un errore se `gift_card_options` contain *uid*.
* **MDVA-39546** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui la data di inizio per l&#39;aggiornamento della gestione temporanea poteva essere impostata su una data precedente alla data corrente durante la modifica.
* **MDVA-42950** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui i video non vengono riprodotti sulla pagina del prodotto.
* **MDVA-42689** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui Adobe Commerce genera un *Violazione del vincolo di integrità* errore durante l’aggiornamento delle categorie di prodotto durante l’importazione.
* **MDVA-41229** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - È stato risolto il problema per cui le immagini disponibili sul back-end non venivano visualizzate sul front-end dopo l’importazione dei prodotti configurabili.
* **MDVA-43731** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema in cui *Sinonimi di ricerca* non funziona più quando il valore viene aggiunto in *Condizioni minime da rispettare*.
* **MDVA-43232** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema relativo all’ordinamento dei prodotti in [!DNL Visual Merchandiser] In base al prezzo speciale in basso/superiore viene generato un errore durante il salvataggio della categoria.
* **MDVA-43726** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*): è stato risolto il problema che impediva l’applicazione della regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di store dopo una reindicizzazione parziale.
* Patch aggiornate: MDVA-36464, MDVA-37478, MDVA-38608.
* Sono stati aggiunti i metadati delle patch per [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui gli attributi del prezzo del prodotto non possono essere aggiornati per un sito Web specifico tramite API REST.
* **MDVA-41350** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema relativo alla generazione di un&#39;eccezione quando un utente amministratore con accesso limitato aggiunge un prodotto al di fuori del proprio ambito di ruolo da parte di SKU in un ordine.
* **MDVA-42269** (*per Adobe Commerce e Magento Open Source >=2,4,3-p1 &lt;2,4,5*): è stato risolto il problema che impediva a un utente amministratore di accedere a Admin a causa del *TypeError: strtotime() prevede che il parametro 1 sia una stringa, dato null* errore.
* **MDVA-40830** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il credito del negozio viene applicato più volte durante il posizionamento dell&#39;ordine.
* **MDVA-42237** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui un prezzo speciale del prodotto configurabile non viene aggiornato in seguito a modifiche nel prezzo del sottoprodotto.
* **MDVA-42520** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Risolve il problema relativo all&#39;applicazione doppia dell&#39;aliquota se *Abilitare il commercio transfrontaliero* viene utilizzato.
* Patch aggiornate: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleta: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.5*) - Corregge il problema per cui l&#39;aggiornamento di massa degli attributi crea la riscrittura degli URL per l&#39;archivio predefinito solo dopo la modifica *Visibilità del prodotto*.
* **MDVA-43091** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per il quale ordinare un prodotto bundle dall’amministratore nel back-end causava l’errore *Impossibile utilizzare la quantità decimale per questo prodotto*.
* **MDVA-40816** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-41305** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la mutazione GraphQL non restituisce opzioni di prodotto configurabili dopo l’aggiunta del prodotto alla lista dei desideri.
* **MDVA-39181** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-42584** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui lo stato delle scorte configurabili nel backend non viene aggiornato dopo la modifica della quantità e dello stato delle scorte tramite Importazione o API.
* **MDVA-40175** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corregge il problema in cui *Fare clic per modificare il metodo di spedizione* non mostra i pulsanti di scelta per selezionare i metodi di spedizione nell’Amministratore durante il riordino.
* **MDVA-42768** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui in Configurable product (Prodotto configurabile) viene visualizzato il prezzo regolare come 0 quando *Visualizza esaurito* è Sì.
* **MDVA-43201** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema relativo alla presenza di un errore nell&#39;accesso del cliente quando si utilizza l&#39;attributo DOB con determinate impostazioni internazionali.
* Patch aggiornate: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo al malfunzionamento dei filtri di data quando il fuso orario di Adobe Commerce è diverso da quello dell’ambiente locale.
* **MDVA-42657** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*): è stato risolto il problema che impediva all’utente amministratore di selezionare le categorie nelle condizioni del segmento cliente.
* **MDVA-42806** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema se una *Nuova registrazione società* L’e-mail viene inviata ogni volta che una società esistente viene aggiornata tramite API REST.
* **MDVA-37984** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema in cui il [!DNL Visual Merchandiser] *Corrispondenza prodotto per regola* La funzionalità non filtra correttamente i prodotti con aggiornamenti di staging.
* **MDVA-40488** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo.
* **MDVA-42507** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema di pulizia della cache di pagina intera dopo l’applicazione dell’aggiornamento di staging per la regola del carrello.
* **MDVA-39163** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corregge il problema per cui i metodi di spedizione non sono disponibili quando viene registrato un nuovo utente e i prodotti nel carrello provengono dalla sessione ospite.
* **MDVA-38626** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*): è stato risolto il problema che impediva all&#39;utente amministratore di effettuare un ordine sul backend utilizzando [!DNL PayPal Payflow Pro] pagamento.
* **MDVA-38666** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*): è stato risolto il problema che impediva all’utente amministratore di modificare le opzioni di prodotto configurabili nel carrello del cliente.
* **MDVA-38526** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*): è stato risolto il problema che impediva all&#39;utente amministratore di accedere al [!DNL Site-Wide Analysis tool].
* Patch aggiornate: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui gli utenti ricevono l&#39;errore 500 dopo aver impostato il *messaggi immagine* cookie se esiste già, ma non sono presenti nuovi messaggi.
* **MDVA-41139** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui i prodotti configurabili diventano esauriti dopo l’importazione del prodotto quando la quantità=0 di un prodotto semplice per una delle sue origini.
* **MDVA-42326** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2,4,1 &lt;2,4,4*) - Corregge il problema per cui i clienti ricevono un errore al momento del pagamento dopo un timeout della sessione anche se il carrello acquisti persistente è abilitato.
* **MDVA-42341** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema in cui il `categoryList` La query GraphQL non filtra i risultati se una richiesta ha l’intestazione Store.
* **MDVA-38393** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema per cui le regole del catalogo cessano di funzionare per un prodotto configurabile se il relativo prodotto semplice viene rinominato.
* **MDVA-39153** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema relativo al calcolo errato dell&#39;importo dello sconto durante il riordino in Admin.
* Patch aggiornate: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - È stato risolto il problema che impediva agli utenti amministratori di accedere alla griglia del cliente dopo l&#39;eliminazione del sito web.
* **MDVA-40311** (*per Adobe Commerce e Magento Open Source >=2,4.2-p2 &lt;2,4.4*) - È stato corretto il problema a causa del quale gli utenti amministratori ricevevano il messaggio di errore *Chiave modulo o protezione non valida. Aggiorna la pagina* dopo aver effettuato l’accesso all’amministratore, se è stato configurato il percorso di amministrazione personalizzato e la chiave segreta è abilitata.
* **MDVA-41631** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema di errore che si verifica quando si tenta di recuperare le informazioni sull’ordine senza un *telefono* tramite GraphQL.
* **MDVA-27239** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Risolve il problema che impediva la visualizzazione dei prodotti di cross-selling.
* Patch aggiornate: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corregge il problema relativo ai prodotti mancanti sul front-end durante la reindicizzazione.
* **MDVA-40120** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema che impedisce l&#39;utilizzo di DESC/ASC per l&#39;ordinamento di GraphQL con prodotti che hanno la stessa rilevanza o prezzo.
* **MDVA-41399** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*): è stato corretto il problema che impediva agli utenti amministratori di accedere al *Gestisci carrello* pagina se un cliente aggiunge un prodotto alla lista dei desideri.
* **MDVA-40609** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui i dati dei prodotti disabilitati sono assenti nel `cataloginventory_stock_status` tabella indice, con quantità di prodotti disabilitati non corrette.
* **MDVA-39031** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui è possibile aggiungere un prodotto al carrello tramite GraphQL anche se non è assegnato al sito web di destinazione.
* **MDVA-41597** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*): è stato corretto il problema a causa del quale gli utenti ricevevano un errore durante l’aggiunta di più prodotti configurabili al carrello con GraphQL.
* **MDVA-27456** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corregge il problema relativo all’errore restituito dagli utenti durante il caricamento di [!DNL Swagger].
* **MDVA-32776** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui lo stato delle scorte non viene aggiornato quando viene effettuato un ordine ma non viene spedito.
* **MDVA-30862** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corregge il problema relativo alla data dell&#39;ordine errata nella fattura PDF stampata.
* È stata migliorata la pagina di indice per [!DNL Quality Patch Tool]. Sono stati aggiunti una pratica funzione di ricerca e filtro per [!DNL quality patches] versione più recente dello strumento.
* Patch aggiornate: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema che impediva la creazione di un nuovo aggiornamento o la modifica di un aggiornamento pianificato esistente per un prodotto se la Data di fine era stata precedentemente rimossa.
* **MDVA-41046** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui sono disponibili prodotti semplici con opzioni personalizzate da assegnare a prodotti configurabili/raggruppati.
* **MDVA-40545** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui veniva recuperato solo il primo nodo per una pagina, anche se erano presenti più nodi per la stessa pagina.
* **MDVA-41164** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*): risolve il problema che impediva all&#39;utente amministratore di salvare o modificare un&#39;azienda con un attributo cliente personalizzato per un tipo di file o immagine.
* **MDVA-39229** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema che causa la visualizzazione del seguente errore dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento della gestione temporanea della regola del catalogo: *Errore di staging_synchronize_entities_period per il processo di creazione della copia: impossibile eliminare l&#39;aggiornamento attivo.*
* **MDVA-40619** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui le modifiche alla gerarchia delle pagine CMS causano un errore 500 quando si tenta di eseguire la modifica in linea su una pagina CMS.
* **MDVA-41061** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*): risolve il problema se lo stato delle scorte viene reimpostato su vendibile quando un prodotto viene salvato dall&#39;amministratore.
* **MDVA-31763** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema che causa il ripristino (o la mancata applicazione) delle regole del prezzo di catalogo fino alla reindicizzazione manuale.
* **MDVA-37748** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*): è stato risolto il problema che si verificava se una query GraphQL restituiva prodotti non assegnati a un catalogo condiviso.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite API REST.
* **MDVA-40101** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.0*) - Corregge il problema per cui gli elementi non vengono rimossi dal mini carrello dopo un posizionamento dell&#39;ordine riuscito utilizzando [!DNL PayPal Express] Pagamento.
* **MDVA-40401** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2,4,1 &lt;2,4,4*) - Risolve il problema relativo alla modifica del valore di utilizzo del coupon anche in caso di esito negativo dell&#39;ordine.
* **MDVA-40537** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*): risolve il problema relativo all’errore restituito dagli utenti durante la creazione di una visualizzazione store, se esistono più pagine CMS con la stessa chiave URL.
* **MDVA-37725** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corregge il problema per cui le e-mail con ordine asincrono inviate da siti Web non predefiniti contengono gli URL del logo del sito Web predefinito.
* **MDVA-39482** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2,4,1 &lt;2,4,4*) - Risolve il problema relativo a un prodotto esaurito se importato con quantità pari a &quot;0&quot; quando gli ordini inevasi sono abilitati.
* **MDVA-40435** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Risolve il problema con uno sconto errato sui prodotti bundle con prezzi dinamici quando applicati tramite GraphQL.
* **MC-42528** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corregge il problema in cui il `categoryList` La query GraphQL restituisce sia le categorie assegnate che quelle non assegnate.
* **MDVA-29400** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2,4,0 &lt;=2,4,0-p1*) - Corregge il problema relativo agli ordini duplicati effettuati con [!DNL PayPal Express Checkout].
* **MDVA-26005** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Risolve il problema che impediva la selezione di una categoria in una struttura di categorie per le condizioni della regola Prezzo carrello.
* **MDVA-25631** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Migliora le prestazioni per la modifica e il salvataggio di segmenti di clienti che contengono un numero elevato di clienti.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui le query di ricerca di GraphQL non vengono visualizzate nei termini di ricerca più comuni in Admin.
* **MDVA-40601** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corregge il problema di errore che si verifica quando si tenta di ottenere informazioni sulla categoria modificata tramite aggiornamento pianificato tramite GraphQL.
* **MDVA-37234** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2,4,1 &lt;=2,4,2-p2*) - Corregge il problema per cui aggiungendo più volte un elemento al carrello (richiesta parallela) per lo stesso SKU si crea una riga duplicata per lo stesso ID carrello.
* **MDVA-33606** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corregge il problema per cui gli utenti ricevono un *Violazione vincolo univoco* durante il salvataggio di una pagina CMS assegnata a una gerarchia.
* **MDVA-31590** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - È stato risolto il problema che impediva agli utenti di aggiornare gli attributi in blocco utilizzando le code asincrone MySQL.
* **MDVA-36309** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corregge il problema relativo al rallentamento della ricerca di prodotti in base agli attributi nelle griglie di amministrazione.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui la fattura con FPT mostra un totale complessivo errato quando l&#39;ordine viene pagato dal credito del negozio.
* **MDVA-37364** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corregge il problema per cui l’attributo cliente personalizzato con tipo di data interrompe l’interfaccia utente della griglia del cliente.
* **MDVA-39195** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corregge il problema in cui *Aggiungi al carrello* sulla pagina della categoria il pulsante non era attivo quando era abilitato il reindirizzamento al carrello.
* **MDVA-37115** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corregge il problema se un *Solo 0 rimasti* nella pagina del prodotto configurabile.
* **MDVA-39521** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema che impediva all&#39;utente di impostare gli indirizzi di spedizione sul carrello con un numero di telefono vuoto tramite GraphQL.
* **MDVA-39384** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2,4,1 &lt;=2,4,3*) - Corregge il problema per cui l&#39;attributo cliente personalizzato per un utente aziendale non viene salvato.
* **MDVA-39043** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corregge il problema per cui l’utente amministratore con accesso limitato riceve un errore durante il tentativo di aggiungere il *Prodotti* alla pagina CMS.
* **MDVA-39966** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2,4,0 &lt;=2,4,0-p1*) - È stato risolto il problema relativo alla distribuzione di impostazioni internazionali non corrette.
* **MDVA-38852** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corregge il problema che causa il blocco delle tabelle di cataloghi per progettazione per aggiornamenti che riducono notevolmente le prestazioni nei casi in cui si disponga di diversi ordini paralleli.
* **MDVA-39986** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - È stato risolto il problema che impediva all&#39;utente di effettuare un ordine in Admin on MacOS utilizzando il browser Safari.
* **MDVA-38447** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge due problemi: dove *Non visibile singolarmente* I prodotti secondari configurabili vengono restituiti nella risposta di GraphQL e ottimizzano la query MySQL per la query dei prodotti GraphQL con il filtro categoria.
* **MDVA-40134** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui GraphQL non restituisce prodotti correlati quando è abilitato Shared Catalog.
* **MDVA-39935** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui GraphQL restituisce prodotti secondari configurabili disabilitati a livello di sito Web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema in cui il *Chiamata a una funzione membro getId()* viene visualizzato nella pagina dei dettagli dell’ordine in Admin.
* **MDVA-34948** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2,4,0 &lt;=2,4,0-p1*) - Risolve il problema relativo alle query con tempi di esecuzione lunghi, come `GET_LOCK`.
* **MDVA-39305** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corregge il problema che impediva ai clienti registrati di accedere con Google ReCaptcha abilitato.
* **MDVA-37897** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema relativo a un reindirizzamento errato quando un cliente tenta di aggiungere prodotti con opzioni del widget Visualizzato di recente.

## v1.1.0 {#v1-1-0}

* Sono state introdotte categorie di patch per migliorare l’esperienza utente e facilitare la ricerca delle patch necessarie per i clienti.
* Il `patches.json` il file è stato rinominato `support-patches.json`.
* **MDVA-38799** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui i prodotti scaricabili non venivano salvati dopo la creazione di un aggiornamento di staging.
* **MDVA-37592** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corregge il problema che si verificava quando l&#39;ordinamento per prezzo non funzionava correttamente per i prodotti con un prezzo zero assegnato al catalogo condiviso.
* **MDVA-38827** (*per Adobe Commerce >=2,3,3-p1 &lt;2,4,4*) - Corregge il problema per cui i clienti ricevono un messaggio e-mail di spedizione dell&#39;ordine contenente un messaggio di errore.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*per Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corregge l&#39;errore durante il salvataggio delle pagine CMS: *Esiste già un elemento con lo stesso ID PAGE_ID*.
* **MDVA-34680** (*per Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2,4,1 &lt;2,4,3*) - Corregge il problema per cui l&#39;ora di creazione dell&#39;account cliente non viene filtrata correttamente nella griglia clienti.
* **MDVA-37068** (*per Adobe Commerce >=2.3.1 &lt;2.4.4*) - Corregge il problema relativo alla visualizzazione dell&#39;aliquota non corretta quando il carrello presenta solo prodotti virtuali.
* **MDVA-38608** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla mancata eliminazione delle tabelle temporanee al termine della reindicizzazione.
* **MDVA-38308** (*per Adobe Commerce >=2,3,5 &lt;=2,3,6-p1 || >=2,4,0 &lt;=2,4,1-p1 || >=2,4,2 &lt;2,4,4*) - Corregge i problemi relativi all’aggiunta di [!DNL Vimeo] video ai prodotti.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema per cui il cliente non viene reindirizzato alla pagina di conferma del pagamento quando si utilizza [!DNL Paypal Payment Advanced] metodo.
* **MDVA-37082** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Risolve il problema che si verificava quando si salvava la scorta personalizzata di prodotti raggruppati e causava la visualizzazione del prodotto esaurito nel front-end.
* **MDVA-36572** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*) - È stato risolto il problema che si verificava quando gli aggiornamenti delle note di credito non causavano più la presenza di aggiornamenti duplicati per la prenotazione del prodotto nel database.
* **MDVA-38132** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corregge il problema quando il pannello Admin (Amministrazione) non è raggiungibile a causa di un *troppi reindirizzamenti* errore.
* **MDVA-38270** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Risolve il problema relativo alle informazioni mancanti sulla gift card nel totale dell&#39;ordine in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*per Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Corregge il problema relativo all’aggiunta di un prodotto configurabile al carrello tramite GraphQL quando l’ID del sito web non coincide con l’ID del negozio.
* **MDVA-36832** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corregge il problema relativo alla presenza di immagini duplicate sulle pagine con larghezza di visualizzazione di 768 px.
* **MDVA-37874** (*per Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2,4,1 &lt;=2,4,2-p1*) - Corregge il problema in cui *Importo sconto fisso per l&#39;intero carrello* viene erroneamente applicato a un prodotto bundle contenente più di un’opzione.
* **MDVA-37913** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*): risolve il problema relativo alla scomparsa dei collegamenti scaricabili se il prodotto scaricabile viene aggiornato tramite API.
* **MDVA-34330** (*per Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corregge il problema per cui gli ordini nella griglia Ordini non vengono filtrati in base al fuso orario Amministratore.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*per Adobe Commerce >=2.3.0 &lt;=2.3.7*): è stato corretto il problema a causa del quale Adobe Commerce generava un errore durante la creazione di una fattura parziale per gli ordini effettuati con il *Pagamento in acconto* metodo di pagamento tramite API REST.
* **MDVA-37362** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corregge il problema per cui i valori delle opzioni di prodotto configurabili e gli attributi della variante erano vuoti nella risposta di GraphQL.
* **MDVA-37288** (*per Adobe Commerce 2.4.2*) - Corregge il problema relativo alla restituzione di prezzi di livello errati dopo la richiesta GraphQL.
* **MDVA-37225** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Risolve il problema relativo al blocco del processo di caricamento durante la creazione rapida degli ordini, quando è presente un valore intero negli SKU importati.
* **MDVA-37224** (*per Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corregge il problema che impediva ai clienti di pagare un preventivo negoziabile con [!DNL PayFlow Pro] con un altro prodotto nel carrello.
* **MDVA-36286** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Corregge il problema in cui l&#39;anteprima del widget prodotti Page Builder si interrompe se lo stesso SKU ha una posizione diversa nelle sottocategorie.
* **MDVA-30186** (*per Adobe Commerce >=2,3,4 &lt;=2,3,5-p2, >=2,4,0 &lt;=2,4,0-p1, >=2,4,2 &lt;=2,4,2-p1*) - Corregge il problema per cui le opzioni attributo sono ordinate per valore di opzione invece del conteggio degli elementi attributo nella risposta di GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*per Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corregge il problema per cui le vecchie opzioni personalizzate rimangono dopo essere state modificate tramite API.
* **MDVA-35773** (*per Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2,4,1 &lt;=2,4,2*) - Risolve il problema che impediva la visualizzazione del totale complessivo come zero sulla fattura per gli ordini con sconto del 100%.
* **MDVA-36833** (*per Adobe Commerce 2.4.2*) - Risolve il problema relativo ai risultati della ricerca, che mostravano numeri casuali di prodotti per pagina dopo l&#39;esclusione di alcuni prodotti dal catalogo condiviso.
* **MDVA-37182** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corregge il problema relativo all’ottenimento di risultati di ricerca errati in entrambi [!DNL Elasticsearch] versioni 6 e 7.
* **MDVA-36253** (*per Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Corregge il problema per cui il subtotale errato viene visualizzato nel mini carrello dopo l&#39;eliminazione dell&#39;elemento.
* **MDVA-36853** (*per Adobe Commerce 2.4.2*) - È stato risolto il problema che impediva la visualizzazione di immagini durante il caricamento di gallerie multimediali di grandi dimensioni.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*per Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corregge il problema relativo ai prodotti in bundle mancanti nelle pagine delle categorie.
* **MDVA-36615** (*per Adobe Commerce 2.4.2*) - Corregge il problema relativo al numero di prodotti errato nella griglia di amministrazione del prodotto.
* **MDVA-36464** (*per Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Corregge il problema per il quale la configurazione della notifica e-mail non funziona a livello di visualizzazione store.
* **MDVA-36138** (*per Adobe Commerce ^2.3.2*) - Corregge il problema che causa la mancata rettifica del prezzo di spedizione e la visualizzazione del prezzo di spedizione completo ai clienti se non tutti gli articoli nel carrello sono idonei per la regola del carrello di spedizione gratuito.
* **MDVA-36424** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2,0,0 &lt;2,2,0*) - Corregge il problema per cui le immagini multimediali allegate agli elementi del Page Builder scompaiono quando il contenuto viene modificato ripetutamente, se l&#39;URL di base del back-end è diverso dall&#39;URL di base dello storefront.
* **MDVA-35984** (*per Adobe Commerce ^2.4.0*) - Corregge il problema relativo alla quantità di prodotto errata e alla quantità vendibile dopo la creazione di più spedizioni simultanee per lo stesso prodotto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Questo risolve il problema in cui la query GraphQL non viene memorizzata in cache utilizzando il tag cache delle categorie.
* **MDVA-33168** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*): risolve il problema durante l’aggiornamento di un attributo di prodotto tramite API se tutti gli altri attributi cambiano in un valore vuoto.
* **MDVA-19640** (*per Adobe Commerce >=2.3.0*) - Corregge il problema in cui [!DNL Advanced Reporting] non mostra alcun dato.
* **MDVA-11189** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*): è stato risolto il problema che si verificava se, dopo l’importazione di un file CSV per aggiornare il materiale promozionale, le righe da `cataloginventory_stock` la tabella viene eliminata.
* **MDVA-26639** (*per Adobe Commerce >=2,3,3-p1 &lt;2,3,6*) - Corregge il problema per cui se viene creato un nuovo modello e-mail di conferma dell’ordine, gli elementi dell’ordine mancano nell’e-mail dell’ordine.
* **MDVA-15546** (*per Adobe Commerce >=2.3.0*) - Corregge il problema per cui dopo la creazione di un ordine *Column entity_id dove la clausola è ambigua* viene visualizzato un errore nel registro eccezioni.
* **MDVA-21095** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema quando una query `INSERT INTO search_tmp` non terminerà dopo l&#39;aggiornamento di massa del valore dell&#39;attributo.
* **MDVA-23845** (*per Adobe Commerce >=2,3.2-p2 &lt;2,3.5*) - È stato risolto il problema che impediva la visualizzazione in anteprima dei modelli e-mail dopo l’abilitazione della minimizzazione JavaScript.
* **MDVA-22026** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema per cui l’importazione di prodotti da file CSV, incluse immagini da URL esterni, non riesce.
* **MDVA-22383** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema per cui il salvataggio di un prodotto richiede molto tempo e la pagina si interrompe.
* **MC-41359** (*per Adobe Commerce >=2,3,6-p1 &lt;2,3,7, >=2,4,2 &lt;2,4,3*) - È stato risolto il problema relativo alle impostazioni errate dei parametri dei cookie SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*per Adobe Commerce 2.4.1*) - Corregge il problema per cui Page Builder genera il seguente errore: *Si è verificato un errore durante l&#39;avvio di Page Builder. Contattare il supporto tecnico.*
* **MDVA-35356** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla restituzione errata del credito del negozio dopo l&#39;annullamento dell&#39;ordine parzialmente fatturato.
* **MDVA-33289** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corregge il problema relativo alla visualizzazione del codice JavaScript non elaborato nell&#39;interfaccia utente degli indirizzi di fatturazione durante il pagamento se [!DNL Google Tag Manager] è abilitato.
* **MDVA-35982** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui gli utenti amministratori limitati a un sito Web specifico non possono creare una spedizione per l&#39;ordine effettuato sullo stesso sito Web.
* **MDVA-35155** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Risolve il problema relativo all&#39;impossibilità di acquistare un prodotto bundle in caso di modifica del titolo dell&#39;opzione.
* **MDVA-35910** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - È stato risolto il problema che impediva la creazione di un nuovo account cliente dopo la disattivazione della funzionalità Accedi come cliente.
* **MDVA-34474** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - È stato risolto il problema relativo all’aggiunta di un prodotto all’elenco delle richieste di acquisto tramite l’API.
* **MDVA-34591** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo a un calcolo errato dello sconto delle regole del carrello per *Sconto quantità massima applicato a* e *Incremento Qtà Sconto (Acquista X)*.
* **MDVA-33704** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corregge il problema in cui il *Ritiro in negozio* l’opzione di spedizione non viene visualizzata, anche se è configurata per essere disponibile.
* **MDVA-34928** (*per Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Risolve il problema relativo alla visualizzazione indefinita del caricatore di pagina dopo la rimozione del credito del negozio dal pagamento.
* **MDVA-35254** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corregge i problemi relativi al CAPTCHA durante il pagamento.
* **MDVA-35569** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema in cui il *imposte sui prodotti fisse* il campo non viene popolato nella risposta di GraphQL quando viene specificato lo stato.
* **MDVA-35847** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corregge il problema B2B per cui il modulo Utenti società si interrompe se viene utilizzato un attributo cliente personalizzato.
* **MDVA-31307** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corregge il problema in presenza di *Memoria insufficiente* errori in alcune categorie a causa di problemi con l’inserimento di CSP dinamici nella whitelist per i blocchi memorizzati in cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge l’errore *in corso* lo stato del messaggio sul corretto *completo* messaggio per il consumatore `quoteItemCleaner` dopo aver eliminato diversi prodotti.
* **MDVA-34102** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge se la quantità di Scorta predefinita è zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell&#39;area Amministratore.
* **MDVA-35286** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - Risolve il problema relativo alla presenza di un errore se un cliente ha raggruppato i prodotti nel carrello e passa dal pagamento tramite più indirizzi al pagamento tramite Onepage.
* **MDVA-35312** (*per Adobe Commerce >=2,4.1-p1 &lt;2,4.2*) - Corregge il codice di risposta 500 quando una richiesta GraphQL vuota.
* **MDVA-34189** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corregge il timeout del primo byte di 503 su [!DNL Visual Merchandiser] query durante il caricamento della pagina Categoria amministratore.
* **MDVA-34695** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correzioni negative `children_count` dopo l’eliminazione delle categorie.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corregge il problema in cui il *Usa valore predefinito* La casella di controllo viene deselezionata dopo l&#39;applicazione delle modifiche pianificate. Il problema viene visualizzato quando le modifiche pianificate non sono più in vigore.
* **MDVA-35064** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui non vengono generate riscritture URL per prodotti configurabili creati tramite API.
* **MDVA-34943** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema relativo alla memorizzazione nella cache degli SKU immessi in precedenza.
* **MDVA-35197** (*per Adobe Commerce >=2.3.5 &lt;2.4.0*) - Risolve il problema relativo alla presenza di un errore durante l&#39;aggiunta al carrello tramite GraphQL se i prodotti aggiunti in precedenza non sono più disponibili.
* **MDVA-34850** (*per Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corregge il problema per cui le opzioni esaurite di un prodotto configurabile non vengono visualizzate invece di essere visualizzate come barrate.
* **MDVA-34867** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui i valori di un campo condizione impostato per un aggiornamento pianificato non vengono salvati.
* **MDVA-35092** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corregge il problema che impediva agli utenti di aggiungere [!DNL Vimeo] video a causa di obsoleti [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*): risolve il problema relativo alle interruzioni dell’anteprima del tipo di contenuto Prodotti Page Builder se i prodotti corrispondenti hanno prezzi diversi per ciascun sito web.
* **MDVA-32634** (*per Adobe Commerce ^2.3.1*) - Corregge il problema in cui il `url_path` della categoria assegnata a tutti gli archivi rimane invariata dopo lo spostamento della categoria nella gerarchia.
* **MDVA-33344** (*per Adobe Commerce ^2.3.0*) - Corregge il problema relativo alla posizione `rma_item` viene utilizzato l’ID del set di attributi predefinito dell’entità invece del valore proveniente dal database.
* **MDVA-34192** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corregge il problema che rende impossibile modificare/specificare la data di nascita del cliente nel formato gg/mm/aaaa.
* **MDVA-34847** (*per Adobe Commerce ^2.3.0*) - Corregge la conversione del tipo ID archivio in numero intero per la condizione SQL nelle raccolte amministratore per l’utente amministratore con autorizzazioni personalizzate.
* **MDVA-34886** (*per Adobe Commerce ^2.3.2*) - Corregge il problema per cui la ricerca non restituisce risultati se *peso* l’attributo di prodotto è configurato come ricercabile.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema di [!DNL PayPal Payflow Pro] pagamento non riuscito con errore di formato elenco parametri di reindirizzamento.
* **MDVA-34023** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema in cui l&#39;errore *Nessuna entità di questo tipo con addressId* viene visualizzato in modo casuale nei browser dei visitatori.
* **MDVA-32759** (*for Adobe Commerce >=2.3.1 &lt;2.4.3 con estensione B2B*): risolve il problema relativo all’eliminazione, da parte dei cataloghi condivisi, dei prezzi a livello esistente.
* **MDVA-33482** (*per Adobe Commerce ^2.3.5*) - Corregge il problema per il quale la generazione di una nota di accredito a fronte di una fattura parziale determina un&#39;imposta per l&#39;ordine totale anziché l&#39;imposta per la fattura parziale.
* **MDVA-33393** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge l&#39;errore *Il countryId fornito non esiste*.
* **MDVA-33632** (*per Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fornisce una correzione in cui il messaggio di eccezione *Il prodotto è esaurito* viene ora visualizzato a un utente amministratore quando tenta di riordinare un prodotto esaurito.
* **MDVA-34469** (*per Adobe Commerce >=2.4.1 &lt;2.4.2*): risolve il problema relativo al mancato funzionamento delle mutazioni GraphQL sul carrello di un cliente quando si utilizzano più visualizzazioni dello store.
* **MDVA-33976** (*per Adobe Commerce >=2.3.0 &lt;2.3.7*) - Corregge il problema per cui il prodotto bundle viene visualizzato esaurito sulla vetrina dopo la rimozione della seconda opzione dal prodotto bundle.
* **MDVA-33894** (*per Adobe Commerce >=2.4.0 &lt;2.4.1 con estensione B2B*): sono stati risolti diversi problemi relativi alla funzionalità Ordine rapido, tra cui l’aggiunta e la rimozione di più prodotti e la distinzione tra maiuscole e minuscole nello SKU.
* **MDVA-27664** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - È stato risolto il problema nel modulo di registrazione del cliente che causava la visualizzazione di un errore: *ERRORE - La data di nascita non deve essere successiva alla data odierna.*
* **MDVA-33970** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema relativo al segno di valuta errato nella nota di credito quando l&#39;ambito dell&#39;attributo del prezzo è impostato su sito Web.
* **MDVA-33992** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema della visualizzazione errata dei prezzi speciali B2B durante il pagamento.
* **MDVA-34100** (*for Adobe Commerce >=2.3.4 &lt;2.4.2 con estensione B2B*) - Corregge il problema che impediva la creazione di un account aziendale dalla pagina della struttura aziendale.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*per Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Corregge il problema relativo alle immagini duplicate dopo l’importazione del prodotto da un file CSV.
* **MDVA-33382** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): sono stati risolti i problemi di invalidazione degli indicizzatori dopo la rimozione dei prodotti da una categoria.
* **MDVA-28511** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corregge il problema quando non è possibile completare [!DNL PayPal] controlla se il campo Nome contiene determinati caratteri (come lettere maiuscole accentate).
* **MDVA-31519** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corregge il problema relativo ai timeout di attesa nel pagamento degli ospiti quando viene utilizzata una regola di vendita a livello di sito.
* **MDVA-33281** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corregge il problema relativo a un errore irreversibile in `inventory:reservation:list-inconsistencies` a causa di un tipo di parametro SKU errato.
* **MDVA-24201** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema per cui i prezzi non riflettono la regola del prezzo del carrello pianificato fino a quando non vengono reindicizzati manualmente.
* **MDVA-32694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2,4,0 &lt;2,4,2*): è stato risolto il problema che impediva a un utente amministratore di aggiungere un prodotto a un preventivo negoziabile se è correlato a un archivio non predefinito.
* **MDVA-33516** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema per il quale la modifica di un prodotto bundle in un elenco di richieste di acquisto genera un errore.
* **MDVA-33975** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*): sono stati risolti diversi problemi relativi al calcolo dei prezzi nelle richieste GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema con [!DNL PayPal] I rapporti sulle liquidazioni non sono disponibili in **Rapporti** > **Vendite** > **[!DNL PayPal]** Liquidazione come previsto.
* **MCP-87** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*) - È stato migliorato il tempo di indicizzazione per gli indicizzatori di prodotti e azioni per i profili di grandi dimensioni.
* **MDVA-33106** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui le modifiche al prodotto riprogrammate vengono cancellate dopo il cron `run` viene eseguito.
* **MDVA-19391** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema in cui `analytics_collect_data` sta generando un errore a causa di record di descrizione NULL nel `catalog_category_entity_text` tabella.
* **MDVA-20376** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Risolve il problema con *Nessuna entità di questo tipo con customerId = 1* errore in `exception.log` per i clienti connessi dopo l’inserimento dell’ordine.
* **MDVA-23764** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
* **MDVA-13203** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema in cui il *Tabella search_tmp_ della violazione del vincolo di integrità* dopo una reindicizzazione completa viene visualizzato un errore.
* **MDVA-23426** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*) - Corregge il problema per cui le e-mail di notifica inviate da Adobe Commerce contengono un corpo vuoto il cui contenuto viene aggiunto come allegato.
* **MDVA-22150** (*per Adobe Commerce >=2.3.1 &lt;2.3.4*): risolve il problema per cui i clienti con un prodotto configurabile nel carrello e un coupon applicato non possono accedere se tale prodotto configurabile è disabilitato in Amministrazione.
* **MDVA-32545** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui le fatture non vengono inviate automaticamente durante la creazione di ordini dall&#39;amministratore.
* **MDVA-32714** (*per Adobe Commerce >=2.3.4 &lt;2.4.1*): è stato risolto il problema che impediva il corretto funzionamento del prezzo di gruppo del cliente nella query di prodotto di GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Aggiunge il *Subtotale (Incl. Imposta)* opzione alle condizioni della regola di prezzo.
* **MDVA-31236** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - È stato risolto il problema che impediva agli amministratori con accesso personalizzato alle risorse di impostare 2FA o di effettuare l’accesso.
* **MDVA-30845** (*per Adobe Commerce >=2.3.5 &lt;2.3.7*) - Corregge il problema in cui il *Al momento non sono disponibili offerte per questo ordine* viene visualizzato un errore quando non è possibile connettersi a UPS XML/USPS/DHL e non è disponibile alcun altro metodo di spedizione.
* **MDVA-32133** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema relativo al mancato caricamento della raccolta multimediale da Page Builder in alcuni casi.
* **MDVA-12304** (*per Adobe Commerce >=2.3.0*) - Aumenta il numero massimo di cookie da 50 a 200.
* **MDVA-32632** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*): risolve il problema relativo alla visualizzazione degli ordini nel sistema di pagamento ma non in Adobe Commerce.
* **MDVA-32449** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con estensione B2B*) - Corregge il problema relativo al caricamento molto lento o nullo della cronologia degli ordini.
* **MDVA-32739** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui, se si abilita Notifiche e-mail asincrone, vengono inviate e-mail di vendita precedenti.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*per Adobe Commerce 2.3.6, 2.4.1*) - Corregge il problema in cui il *Creare un account* rimane disattivato dopo la correzione di dati non validi nella *Crea nuovo account cliente* modulo.
* **MDVA-31006** (*per Adobe Commerce 2.3.0, 2.3.1*) - Risolve il problema relativo alla visualizzazione di ordini duplicati dopo l&#39;inserimento di un ordine utilizzando [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*per Adobe Commerce 2.3.0*) - Corregge un problema con [!DNL PayPal Payflow Pro] metodo di pagamento e trattamento dei cookie come `SameSite=Lax` per impostazione predefinita, nel browser Chrome 80 e la risposta API reindirizza alla pagina di accesso del cliente.

## v1.0.10 {#v1-0-10}

Correzioni minori per le versioni patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui la Regola prezzo carrello con coupon non si applica tramite GraphQL quando *Sconto importo fisso per carrello intero* viene utilizzata l&#39;azione.
* **MDVA-30889** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema relativo alla comparsa di un errore dopo la fatturazione di un bundle con prodotti virtuali e semplici come opzioni.
* **MDVA-31791** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*) - Migliora le prestazioni della pagina prodotto nei casi in cui vengono utilizzate regole target o prodotti collegati.
* **MDVA-31168** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): è stato corretto il problema che impediva la visualizzazione del file CSV di esportazione del prodotto, a causa del quale si verificava un errore di allocazione della memoria.
* **MDVA-32313** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema per cui i prodotti configurabili potevano essere aggiunti alla lista dei desideri con opzioni di configurazione errate.
* **MDVA-31759** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i prodotti non vengono aggiornati con *elenco a discesa* e *textarea* valori degli attributi durante l’importazione CSV.
* **MDVA-32012** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i codici postali in Corea e Argentina non possono essere convalidati.
* **MDVA-31640** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2,4,0 &lt;2,4,1*) - Corregge il problema che impediva l’aggiornamento di un prezzo speciale tramite API REST.
* **MDVA-28651** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 con estensione B2B*) - Corregge il problema relativo a problemi di prestazioni nel caricamento di preventivi negoziabili tramite API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*per Adobe Commerce >=2.3.0 &lt;2.4.1 con estensione B2B*) - Corregge il problema relativo alla visualizzazione di un segno di valuta errato nella griglia della nota di credito.
* **MDVA-31295** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i punti premio non vengono calcolati quando viene completato un ordine parziale e gli elementi vengono tassati.
* **MDVA-30112** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Risolve il problema se il numero di ordini supera il *dimensione-mazzo* valore, Adobe Commerce considera gli ordini con *in sospeso* stato come incoerenze.
* **MDVA-31150** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i saldi delle carte di credito e delle carte regalo del negozio non vengono restituiti dalla chiamata API Rest fattura GET, quando la fattura è stata registrata dalla chiamata API Rest e l&#39;ordine è stato parzialmente pagato dai conti delle carte di credito e delle carte regalo del negozio.
* **MDVA-30963** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui i risultati del filtro dei prodotti impostati per contengono solo i valori specificati per *Tutte le visualizzazioni dello store* in Admin, includi i prodotti con valori sostituiti a livello di visualizzazione store.
* **MDVA-29954** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con estensione B2B*) - Corregge il problema in cui il *Nuova richiesta di registrazione società* e *Sei stato collegato a un’azienda* le e-mail vengono inviate dall’indirizzo errato.
* **MDVA-28357** (*per Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2,4,0 &lt;2,4,1*) - Sostituisce l&#39;analizzatore standard con un analizzatore personalizzato con un tokenizzatore per parole chiave per il campo SKU nel [!DNL ElasticSearch] indice per far funzionare le query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per il quale lo stato dell&#39;ordine personalizzato veniva modificato in *Elaborazione* dopo la creazione parziale della spedizione tramite WebApi.
* **MDVA-30428** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corregge il problema per cui i clienti non possono aggiungere un prodotto alla lista dei desideri se questo prodotto è assegnato a un&#39;origine inventario personalizzata.
* **MDVA-30594** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che impediva il salvataggio di un ordine con più indirizzi durante il pagamento quando FPT è configurato.
* **MDVA-29148** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): è stato risolto il problema che si verificava durante la creazione di un prodotto tramite una chiamata API, l’attributo personalizzato del prodotto di `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) il tipo non utilizza il proprio valore predefinito se non è stato fornito alcun valore nel payload.
* **MDVA-30837** (*per Adobe Commerce >=2.3.1 &lt;2.3.5*) - È stata aggiunta un’impostazione di configurazione *Includi imposta nell&#39;importo: Sì/No* nella configurazione del metodo Spedizione gratuita. Quando *Includi imposta in importo* è impostato su *Sì*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale + Imposta. Quando *Includi imposta in importo* è impostato su *No*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale
* **MDVA-25028** (*per Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2,3,5 &lt; 2,3,6*) - Corregge il problema che si verifica quando gli ordini vengono effettuati utilizzando [!DNL PayPal Payflow Pro] non sono impostati sullo stato Sospetto di frode quando vengono attivati i filtri di frode.
* **MDVA-31224** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*) - Migliora le prestazioni del `catalog_product_price` operazione di reindicizzazione per i prodotti bundle.
* **MDVA-31321** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge una pagina vuota (errore) quando *Mostra tutto* è selezionato. [!DNL Elasticsearch] restituisce un elenco esteso di id prodotto. In questo scenario la clausola order by viene convertita in un formato SQL non corretto.
* **MDVA-30815** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema per cui quando si modifica il numero di risultati da visualizzare nella pagina dei risultati di ricerca, Adobe Commerce visualizza una pagina vuota. [!DNL Elasticsearch] ora visualizza correttamente i risultati dalle pagine delle categorie quando modifichi il numero di risultati di ricerca visualizzati per pagina.
* **MDVA-30782** (*per Adobe Commerce >=2.3.5 &lt;2.4.2*) - Risolve il problema relativo alla visualizzazione del blocco dinamico indipendentemente dalla regola del carrello.
* **MDVA-31021** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema relativo ai problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`. Se sono presenti più di ~100.000 record in `catalog_product_option` , la convalida di un nuovo file CSV con un singolo prodotto richiede meno di 10 secondi.
* **MDVA-31007** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*): è stato risolto il problema che impediva la corretta visualizzazione degli attributi dell&#39;indirizzo personalizzato nella pagina dei dettagli dell&#39;ordine nell&#39;area my account (il mio account) e nel back-end.
* **MDVA-29389** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema relativo alla funzione di generazione rapporti avanzata in cui `analytics_collect_data` cronjob scrive: *La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*.
* **MDVA-31343** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corregge il problema relativo alla classe body rimossa `page-layout-category-full-width` quando una categoria è pianificata.
* **MDVA-30945** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui viene visualizzato un messaggio di errore irreversibile durante l&#39;aggiornamento dei carrelli `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*per Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa il *Il valore minimo deve corrispondere* funzionalità e ricerca parziale [!DNL Elasticsearch] motore. Risolve i problemi relativi ai trattini nelle query di ricerca.
* **MDVA-30102** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*) - È stato risolto il problema che causava la rapida crescita della cache Redis, in quanto le cache di layout non avevano TTL.
* **MDVA-30599** (*per Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corregge il problema per cui le offerte dei clienti guest create utilizzando l’API vengono contrassegnate in modo errato come offerte per i clienti connessi.
* **MDVA-29446** (*per Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corregge il problema per cui il prezzo del metodo di spedizione non applicabile viene visualizzato come zero durante il pagamento.
* **MDVA-30357** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corregge il problema relativo alla creazione di URL di immagine errati durante la generazione di una sitemap tramite cron.
* **MDVA-30565** (*per Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Corregge il problema in cui *Nessuna entità di questo tipo con cartid = 0* se il carrello acquisti persistente è abilitato, viene visualizzato un errore per il cliente ospite al momento del pagamento della vetrina.
* **MDVA-29787** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Corregge il problema per il quale la regola di destinazione per i prodotti correlati non funziona quando *è uno di* La condizione viene utilizzata per definire i prodotti da visualizzare.
* **MDVA-30977** (*per Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Risolve il problema relativo alla mancanza di prodotti casuali dalle categorie dopo la reindicizzazione.
* **MDVA-28202** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corregge il problema per cui la funzione di navigazione a livelli non filtra correttamente i prodotti configurabili quando viene utilizzato MSI.
* **MDVA-28300** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui la richiesta GQL non riflette le modifiche di prezzo dalle regole di prezzo del catalogo.
* **MDVA-31006** (*per Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Risolve il problema relativo alla visualizzazione di ordini duplicati dopo l&#39;inserimento di un ordine utilizzando [!DNL Paypal Express] pagamento.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corregge il problema della navigazione a livelli, in cui il *No* il valore per gli attributi di prodotto di tipo booleano non è stato incluso nella navigazione a livelli se [!DNL Elasticsearch] è stato utilizzato come motore di ricerca.
* **MDVA-28191** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema relativo all&#39;assenza di metodi di pagamento caricati durante la creazione dell&#39;ordine tramite l&#39;amministratore.
* **MDVA-29959** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 con estensione B2B*) - Corregge il problema se l&#39;utente amministratore con restrizioni con *Aziende* autorizzazioni non consentite per eliminare l’account aziendale.
* **MDVA-30265** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema che causa il mancato funzionamento del collegamento di registrazione spedizione dopo la creazione della fattura.
* **MDVA-28409** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corregge il problema in cui il `sales_clean_quotes` processo cron non riuscito con *memoria insufficiente* errore quando il numero di virgolette scadute nel database è enorme.
* **MDVA-30593** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema per cui le virgolette scadute in base all&#39;impostazione della durata delle virgolette non vengono eliminate.
* **MDVA-30107** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*): è stato risolto il problema che impediva al commutatore store di funzionare come previsto se venivano utilizzati URL di base diversi per le visualizzazioni dello store.
* **MDVA-28763** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema relativo alla duplicazione dell’immagine del prodotto dopo l’aggiornamento delle informazioni di prodotto tramite l’API REST più di una volta.
* **MDVA-30284** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): è stato corretto il problema che causava l’errore dell’indicizzatore Catalog Search a causa dei seguenti *[!DNL Elasticsearch]errore: è stato superato il limite dei campi totali nell’indice.*
* **MDVA-29042** (*per Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 con estensione B2B*) - Corregge il problema in cui le autorizzazioni del catalogo venivano modificate in *Consenti* automaticamente dopo l’aggiunta di un nuovo prodotto al catalogo condiviso.
* **MDVA-30428** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui i clienti non possono aggiungere un prodotto alla lista dei desideri se questo prodotto è assegnato a un&#39;origine inventario personalizzata.
* **MDVA-28661** (*per Adobe Commerce >=2.3.0 &lt;2.4.2 con estensione B2B*) - Risolve il problema relativo alla generazione di un errore nella sezione dell&#39;account aziendale Utenti dopo la modifica dell&#39;amministratore della società.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*per Adobe Commerce 2.3.1 - 2.3.4-p2*): è stato risolto il problema che causava il fallimento dei processi cron se il nome del database era troppo lungo, con conseguente mancato aggiornamento delle categorie sul front-end.
* **MDVA-30106** (*per Adobe Commerce ^2.3.0*) - Corregge un problema per cui durante l&#39;estrazione i pagamenti non vengono caricati con *Impossibile leggere la proprietà &quot;length&quot; di null* errore nella console JS.
* **MDVA-28656** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2,4,0 &lt;2,4,2*) - Corregge il problema per il quale se un ordine è stato effettuato senza che fossero richieste informazioni di pagamento (ad esempio, con uno sconto del 100%) ed è stata creata una fattura per l&#39;ordine, lo stato dell&#39;ordine cambia in *Chiuso* invece di Complete.
* **MDVA-30209** (*per Adobe Commerce 2.3.0 - 2.3.3-p1*): risolve il problema relativo alla modifica del gruppo di clienti in predefinito, se il cliente aggiornava le informazioni sul proprio account.
* **MDVA-30123** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*): è stato risolto il problema che impediva la corretta traduzione delle etichette delle opzioni attributo per le query GraphQL.
* **MDVA-29996** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui, dopo aver abilitato l’autorizzazione per la categoria, la pagina della categoria non viene memorizzata nella cache dalla cache di pagina intera.
* **MDVA-30164** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*): è stato risolto il problema che impediva l&#39;esportazione dei record dei clienti dalla griglia Clienti in presenza di attributi cliente personalizzati.
* **MDVA-30444** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema per cui non viene inviata alcuna e-mail di conferma per gli ordini effettuati tramite GraphQL.
* **MDVA-30490** (*per Adobe Commerce 2.3.4 - 2.3.5-p2*) - Risolve il problema per cui se per uno dei prodotti è presente una breve descrizione vuota, il confronto tra i prodotti genera la pagina di errore 500.
* **MDVA-30232** (*per Adobe Commerce >=2.3.1 &lt;2.4.1*) - Corregge il problema relativo all&#39;impossibilità di riordinare l&#39;ordine se l&#39;ordine originale contiene una gift card.
* **MDVA-29965** (*per Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corregge il problema relativo all’errore &quot;Form Key&quot; non valido restituito dai clienti quando si aggiunge un prodotto al carrello.
* **MDVA-30008** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema B2B che impediva di effettuare ordini tramite Admin API per un prodotto presente in un catalogo pubblico.
* **MDVA-22469** (*per Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - È stato risolto il problema che impediva il funzionamento di Page Builder nel pannello di amministrazione dopo l’aggiornamento ad Adobe Commerce 2.3.3 e il caricamento di alcuni file JS e CSS.
* **MC-35984** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema che impediva ai commercianti di interagire con gli elementi della pagina Restituzioni dopo la creazione di un&#39;etichetta di spedizione per un&#39;autorizzazione di restituzione del materiale promozionale (RMA, Return Merchandise Authorization).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*per Adobe Commerce 2.3.0 - 2.3.4*) - Corregge il problema con [!DNL PayPal Payflow Pro] metodo di pagamento e trattamento dei cookie come `SameSite=Lax` per impostazione predefinita, nel browser Chrome 80 e la risposta API reindirizza alla pagina di accesso del cliente.
* **MDVA-26694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corregge il problema relativo alle cache di prodotti e cataloghi che scadono ogni giorno, anche se con una pianificazione diversa.
* **MDVA-27825** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema che impediva l&#39;esportazione di grandi quantità di dati a causa di una perdita di memoria.
* **MDVA-29085** (*per Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corregge il problema B2B che non invia le e-mail aziendali nuove richieste se una società viene creata tramite API.
* **MDVA-29344** (*per Adobe Commerce >=2,3,5 &lt;=2,4,0-p1*) - Corregge il problema relativo al blocco di Page Builder dopo la copia di testo da un elemento intestazione a un elemento testo.
* **MDVA-29835** (*per Adobe Commerce >2.3.1 &lt;2.4.2*) - Corregge il problema per cui gli ordini gift card contenevano due codici invece di uno.
* **MDVA-30052** (*per Adobe Commerce >=2,3.2-p2 &lt;2,3.5*) - È stato risolto il problema relativo al mancato popolamento corretto dei contenuti privati (archiviazione locale), che causava problemi di prestazioni.
* **MDVA-30131** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Corregge il problema della navigazione a livelli, in cui il *No* il valore per gli attributi di prodotto di tipo booleano non è stato incluso nella navigazione a livelli se [!DNL Elasticsearch] è stato utilizzato come motore di ricerca.
* **MDVA-35514** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema relativo alla creazione di un&#39;etichetta di spedizione e all&#39;aggiunta di prodotti ordinati a un pacchetto nella finestra modale Crea pacchetti.

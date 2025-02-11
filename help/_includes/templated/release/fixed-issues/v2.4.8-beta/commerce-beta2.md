---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Problemi risolti in Adobe Commerce (v2.4.8-beta2)

## Sono stati risolti dei problemi in v2.4.8-beta2.

Sono stati risolti 206 problemi nel codice core di Adobe Commerce 2.4.8. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

* _ACP2E-3236_: l&#39;operazione asincrona non riesce quando manca lo SKU nel payload
   * _Correzione nota_: operazioni asincrone e di sincronizzazione non riuscite in precedenza a causa di errori di salvataggio del prodotto se sku non è presente nel payload. Dopo la correzione, le operazioni dell’API rest di salvataggio del prodotto asincrono e sincrono non riescono e viene visualizzato il messaggio di eccezione pertinente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Impossibile aggiornare i prezzi di base utilizzando l&#39;API REST (il valore di &#39;value_id&#39; in &#39;catalog_product_entity_decimal&#39; non viene incrementato correttamente).
   * _Nota sulla correzione_: in precedenza, quando si chiamava rest api /rest/default/V1/products/base-price, l&#39;ID incremento veniva aumentato erroneamente, lasciando un intervallo tra i valori. Dopo la correzione l’ID incremento viene aumentato come previsto, in modo incrementale. Anche l’intervallo del campo value_id è stato aumentato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: i valori predefiniti non sono impostati per gli attributi di data e ora con i prodotti RestAPI
   * _Correzione nota_: i valori predefiniti ora vengono impostati correttamente per gli attributi di data e data e ora tramite RestAPI
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### API, carrello e pagamento

* _ACP2E-3343_: errore 500 critico: Magento\Framework\Webapi\Exception correlato all&#39;intestazione HTTP Accept
   * _Correzione nota_: dopo la correzione, non si verifica alcun problema quando si specifica l&#39;intestazione &quot;Accept&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### API, GraphQL

* _ACP2E-3348_: nessun graphQl disponibile per la sottoscrizione degli aggiornamenti dei punti premio per il cliente
   * _Correzione nota_: in precedenza, per la correzione, non era possibile aggiornare l&#39;attributo cliente reward_warning_notification tramite la chiamata API Rest e la mutazione GraphQL. Ora può essere aggiornato come l’attributo del cliente reward_update_notification.

### Account

* _AC-10886_: aggiornamento password amministratore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: ciclo di reindirizzamento se l&#39;URL contiene lettere maiuscole
   * _Correzione nota_: il sistema ora converte automaticamente i caratteri maiuscoli negli URL in caratteri minuscoli, impedendo un ciclo di reindirizzamento durante l&#39;accesso alla home page. In precedenza, l’utilizzo di caratteri maiuscoli nell’URL della base sicura causava un ciclo di reindirizzamento continuo quando si tentava di accedere alla home page.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: casella di controllo per l&#39;accesso come consenso del cliente non traducibile
   * _Correzione nota_: il sistema ora consente di impostare i campi &quot;Accedi come cliente opt-in casella di controllo&quot; e &quot;Accedi come cliente descrizione comando casella di controllo&quot; nell&#39;ambito &quot;Visualizzazione archivio&quot;, abilitando le traduzioni per diverse visualizzazioni archivio. In precedenza, questi campi venivano impostati solo nell’ambito &quot;Sito web&quot;, impedendo le traduzioni per le singole visualizzazioni dello store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: dopo l&#39;accesso, i prodotti aggiunti all&#39;elenco di confronto come utenti guest non sono visibili.
   * _Correzione nota_: i prodotti aggiunti all&#39;elenco di confronto dei prodotti prima dell&#39;accesso come cliente ora vengono mantenuti dopo l&#39;accesso.
In precedenza, dopo l’accesso, i prodotti aggiunti all’elenco di confronto come utenti guest non erano visibili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: la configurazione di Consenti paesi causa problemi nelle configurazioni degli indirizzi dei clienti
   * _Correzione nota_: la selezione della configurazione Consenti paesi non influisce sui paesi mostrati per i quali non è stato specificato l&#39;ambito. Consenti in precedenza la configurazione di Paesi influenzata dall’attributo dell’indirizzo del cliente al di fuori dell’ambito specificato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: il registro degli omaggi condivisi mostra la data dell&#39;evento come 1 giorno prima
   * _Correzione nota_: la data del registro regali è ora visualizzata correttamente in Storefront

### Account, API, GraphQL

* _ACP2E-3246_: API Cliente - Il Numero Di Errori Di Accesso Non È Riuscito A Ripristinare 0 Dopo Il Corretto Accesso
   * _Correzione nota_: ora il numero di errore viene reimpostato su zero nella tabella delle entità cliente dopo che il cliente ha eseguito correttamente l&#39;accesso tramite gli endpoint API.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Account, interfaccia utente amministratore, B2B

* _ACP2E-3038_: gli utenti amministratori con restrizioni non possono sempre visualizzare cataloghi condivisi personalizzati
   * _Nota sulla correzione_: gli utenti amministratori con restrizioni possono ora visualizzare e gestire in modo coerente i clienti e tutti i cataloghi condivisi a cui sono assegnati i prodotti, purché abbiano accesso all&#39;archivio specifico. In precedenza, un utente amministratore con accesso limitato a un particolare archivio non poteva sempre visualizzare tutti i cataloghi condivisi a cui erano assegnati i prodotti oppure poteva vedere clienti che non potevano salvare, con conseguenti incongruenze nel sistema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>

### Account, carrello e pagamento

* _AC-2341_: l&#39;attributo di indirizzo cliente personalizzato &quot;select&quot; non viene riprodotto per il nuovo indirizzo cliente
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/34950>

### Interfaccia utente amministratore

* _AC-10705_: [Problema] Aggiungi controllo autorizzazioni per il pulsante &quot;Ricarica dati&quot;
   * _Correzione nota_: il sistema ora include un controllo delle autorizzazioni per il pulsante &quot;Ricarica dati&quot;, che garantisce che venga visualizzato e accessibile solo agli utenti con le autorizzazioni appropriate. In precedenza, il pulsante &quot;Ricarica dati&quot; era visibile e cliccabile per tutti gli utenti, portando a una pagina &quot;non consentita&quot; quando gli utenti facevano clic senza le autorizzazioni necessarie.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38283>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38279>
* _AC-13131_: [Problema] Correzione Avviso: &quot;filters&quot; chiave di matrice non definita
   * _Correzione nota_: il sistema ora gestisce scenari in cui un nuovo utente non ha ancora interagito con i segnalibri, impedendo la registrazione di un avviso &quot;filters&quot; di chiave array non definita. In precedenza, questo avviso veniva registrato quando un nuovo utente non aveva interagito con i segnalibri.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: il file CSV di importazione prodotti con caratteri speciali non riesce a causa di modifiche al codice nel file Validate.php
   * _Correzione nota_: il sistema ora convalida e importa correttamente i file CSV dei prodotti contenenti caratteri speciali, consentendo il corretto trasferimento dei dati. In precedenza, se si tentava di importare un file CSV di un prodotto con caratteri speciali, si verificava un errore che impediva il processo di importazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: quando il numero massimo di richieste di reimpostazione password è impostato su un valore maggiore di 0. Esempio: 3 , &quot;I messaggi di errore relativi al limite superiore vengono inviati prima del raggiungimento del limite, ovvero dalla seconda volta&quot;
* _AC-13768_: sebbene il numero massimo di richieste di reimpostazione password sia impostato su 0( disattivato) , &quot;i messaggi di errore relativi al limite superiore vengono inviati dalla seconda volta&quot;
* _AC-7962_: nessun collegamento alla spedizione durante i pagamenti in pagamento nella visualizzazione per telefono cellulare
   * _Correzione nota_: il sistema ora assicura che i titoli/collegamenti di pagamento &quot;Spedizione&quot; e &quot;Revisione e pagamenti&quot; siano sempre visibili nella parte superiore della pagina nella visualizzazione per dispositivi mobili, consentendo agli utenti di spostarsi facilmente tra i passaggi e apportare le correzioni necessarie. In precedenza, questi titoli/collegamenti erano nascosti nella visualizzazione per dispositivi mobili, rendendo difficile per gli utenti conoscere il passaggio corrente o tornare ai passaggi precedenti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: i commenti di spedizione della query ordini cliente created_at vengono restituiti in un fuso orario +0 non configurato nell&#39;archivio
   * _Correzione nota_: il sistema ora visualizza correttamente il campo &#39;created_at&#39; dai commenti sulla spedizione nel fuso orario configurato del cliente quando si utilizza la query Ordini cliente. In precedenza, il campo &quot;created_at&quot; veniva visualizzato nel fuso orario +0, indipendentemente dal fuso orario configurato del cliente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36947>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: lo stato dell&#39;indirizzo di spedizione non viene aggiornato automaticamente
   * _Nota sulla correzione_: prima della correzione, l&#39;area dell&#39;indirizzo di spedizione (o l&#39;ID di regione) non era sincronizzato con le informazioni di fatturazione dell&#39;indirizzo. Ora, sia l&#39;area dell&#39;indirizzo di spedizione che l&#39;ID di regione vengono aggiornati correttamente quando vengono modificate le informazioni sull&#39;indirizzo di fatturazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: il pulsante Reimposta non funziona su Aggiungi/Modifica utente amministratore
   * _Correzione nota_: in precedenza, il pulsante Reimposta non funzionava nella pagina Aggiungi/Modifica utente amministratore. Ora, nel pannello Amministratore in Sistema -> Autorizzazioni -> Tutti gli utenti, il pulsante Reimposta funziona correttamente nella pagina Aggiungi/Modifica utente amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: convalida interrotta per &quot;Quantità massima consentita nel carrello&quot;
   * _Correzione nota_: in precedenza, quando `Maximum Qty Allowed in Shopping Cart` veniva inserito vuoto, non veniva generata alcuna eccezione, ma qui non veniva accettato un valore vuoto. In seguito all’applicazione di questa correzione, se si inserisce una stringa vuota verranno generate delle eccezioni e non sarà possibile salvare il prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema interfaccia utente di anteprima Pagebuilder] I pulsanti nella colonna Page Builder non sono allineati correttamente
   * _Correzione nota_: i pulsanti nelle colonne di Page Builder sono ora allineati correttamente. In precedenza, non erano allineati nelle colonne di Page Builder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: l&#39;esportazione del report Prodotti ordinati non è consentita. Errore 404.
   * _Correzione nota_: il rapporto Prodotti ordinati esportato in formato CSV e XML ora funziona come previsto
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: errore TinyMCE JS nella console dopo l&#39;abilitazione della minimizzazione Js con modalità di produzione
   * _Correzione nota_: in precedenza, l&#39;abilitazione della minimizzazione di JavaScript in modalità di produzione nel pannello di amministrazione causava la visualizzazione degli errori di JavaScript relativi a TinyMCE 7 nella console del browser, influendo sulla funzionalità e sull&#39;esperienza utente. Ora questo problema è stato risolto, garantendo che TinyMCE 7 funzioni senza errori, anche quando è abilitata la minimizzazione JS.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: richiesta di modifiche aggiuntive per completare completamente la correzione ACP2E-3375
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Interfaccia utente amministratore, metodi di pagamento/pagamento, ordine

* _AC-13520_: autorizzazione transazione non visualizzata nella scheda Transazione dopo l&#39;ordine dei pulsanti avanzati PayPal
   * _Correzione nota_: il sistema visualizza ora correttamente l&#39;autorizzazione della transazione nella scheda Transazione dopo che è stato effettuato un ordine utilizzando lo Smart Button PayPal. In precedenza, la transazione di autorizzazione non veniva visualizzata nella scheda Transazione dopo aver fatto clic sul pulsante &quot;Autorizza&quot; e non veniva creata alcuna nuova transazione di tipo &quot;Autorizzazione&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Interfaccia utente amministratore, staging e anteprima

* _ACP2E-3424_: [Cloud] La rimozione del modello con immagini mancanti determina l&#39;eliminazione di pub/supporti
   * _Correzione nota_: in precedenza, se per un modello di pagebuilder mancava il nome dell&#39;immagine di anteprima, la cartella pub/media veniva eliminata. Dopo la correzione, verranno eliminati solo il modello e l’immagine di anteprima, se trovata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Generazione rapporti

* _AC-9922_: Errore CSP Google Analytics https://region1.analytics.google.com
   * _Correzione nota_: il sistema ora consente correttamente le connessioni a &#39;https://region1.analytics.google.com&#39; quando Google Analytics è abilitato, evitando errori Content Security Policy (CSP). In precedenza, l’abilitazione di Google Analytics e la visualizzazione del sito web dall’UE generavano errori nella console CSP a causa del rifiuto di connettersi a &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_: in GTM manca l&#39;evento addToCart in dataLayer per il prodotto configurabile con opzione personalizzata
   * _Correzione nota_: in precedenza, l&#39;evento addToCart non veniva attivato per i prodotti configurabili. Ora l’evento viene aggiunto correttamente alla variabile GTM dataLayer.
* _ACP2E-3183_: lo script inlineJS per il monitoraggio del browser NewRelic causa errori CSP
   * _Correzione nota_: gli script di monitoraggio di NewRelic Browser ora vengono inseriti dall&#39;applicazione al posto dell&#39;agente APM per la conformità con i criteri CSP (Content Security Policy, criteri sulla sicurezza dei contenuti). In precedenza, gli script di monitoraggio del browser NewRelic inseriti dall’agente APM non erano conformi a CSP e causavano la mancata esecuzione degli script.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: le query INSERT nella tabella sales_bestsellers_aggregated_daily diventano lente in un progetto con un volume di ordini di vendita elevato
   * _Correzione nota_: in precedenza la generazione del report giornaliero aggregato dei bestseller richiedeva molto tempo per un grande volume di ordini effettuati. Ora il rapporto viene generato in modo tempestivo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: i report dell&#39;ordine mostrano il simbolo di valuta errato
   * _Nota di correzione_: il simbolo di valuta per gli importi degli ordini nel report Ordine è stato erroneamente ricavato da valuta/opzioni/base. Ora è stato corretto per utilizzare valuta/opzioni/valore predefinito per una generazione rapporti accurata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Cloud] Calcoli non corretti nel report sull&#39;utilizzo del coupon
   * _Nota di correzione_: il totale delle vendite nella griglia del report coupon viene ora calcolato in modo accurato incorporando sia &quot;Importo compensazione imposta sconto&quot; che &quot;Importo compensazione imposta sconto spedizione&quot;. In precedenza, tali importi mancavano dal calcolo, causando discrepanze tra il totale delle vendite e i dati degli ordini di vendita.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: problemi con &quot;&lt;project_id>/var/tmp&quot; condiviso
   * _Correzione nota_: i file temporanei Analytics DataExport utilizzeranno la directory sys tmp, più adatta per l&#39;accesso frequente e per le modifiche. Per evitare conflitti nel caso in cui più istanze siano in esecuzione sullo stesso server, il percorso tmp è stato aggiornato per utilizzare l’ID univoco di un’istanza
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics / Reporting, cloud

* _ACP2E-3187_: la metrica in NR potrebbe essere fuorviante per le transazioni in background- Seguito di ACP2E-3067
   * _Correzione nota_: per le transazioni in background (cron) verrà utilizzato il nome dell&#39;app New Relic definito nelle impostazioni di configurazione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: errore del pacchetto Enterprise Edition 2.4.8-beta102 con eccezioni dell&#39;applicazione
* _AC-13816_: impossibile abilitare la funzione b2b nell&#39;amministratore back-end per la prima volta
* _ACP2E-2139_: i prodotti assegnati al catalogo condiviso non si riflettono sul front-end quando viene eseguito l&#39;indice parziale
   * _Nota sulla correzione_: i prodotti assegnati al catalogo condiviso tramite API REST ora sono immediatamente visibili nella vetrina dopo il completamento dell&#39;indicizzazione parziale. In precedenza, i prodotti erano visibili solo dopo una reindicizzazione completa.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: cron sales_clean_quotes elimina i preventivi dagli ordini di acquisto non ancora approvati
   * _Correzione nota_: le offerte utilizzate negli ordini fornitore non verranno eliminate dal processo cron sales_clean_quotes
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: il pulsante Inserisci ordine scompare nei dettagli ordine di acquisto
   * _Correzione nota_: è stato risolto un problema a causa del quale il pulsante Inserisci ordine era nascosto per gli ordini fornitore approvati quando nella scheda era specificato un numero minimo di varianti di prodotto
* _ACP2E-3474_: [CLOUD] Nessuna entità di questo tipo con ID = 0 con modulo b2b
   * _Nota corretta_: l&#39;utente connesso può aggiungere il prodotto al carrello quando le funzioni di Catalogo condiviso sono abilitate.
L’aggiunta precedente del prodotto al carrello causava un errore di tipo &quot;nessuna entità di questo tipo con ID = 0&quot;

### B2B, carrello e pagamento

* _AC-13817_: impossibile visualizzare i prodotti nel carrello quando tutte le funzionalità b2b sono abilitate

### B2B, GraphQL

* _ACP2E-3391_: [Cloud] Impossibile impostare custom_attributes durante la creazione della società tramite chiamata graphql
   * _Correzione nota_: dopo la correzione, è possibile impostare l&#39;attributo &quot;custom_attributes&quot; dell&#39;amministratore della società durante la creazione della società utilizzando la richiesta graphql.

### Bundle

* _AC-10826_: numero di messaggi di errore di convalida del bundle Storefront maggiore di 1
   * _Correzione nota_: il sistema visualizza ora un solo messaggio di errore di convalida quando si fa clic sul pulsante &quot;Aggiungi al carrello&quot; senza selezionare alcuna opzione di casella di controllo per un prodotto incluso. In precedenza, il sistema visualizzava più messaggi di errore di convalida per ogni casella di controllo non selezionata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: eccezione Magento generata in alcuni test case correlati all&#39;ordine
   * _Correzione nota_: il sistema ora gestisce correttamente il passaggio &#39;sendGuestPaymentInformation&#39; in vari casi di test, impedendo la generazione di eccezioni Magento. In precedenza, queste eccezioni si verificavano a causa di un metodo di pagamento null, causando errori in diversi casi di test.

### Carrello e pagamento

* _AC-11914_: [Problema] Calcolo CartFixed della regola di vendita: importo sconto non corretto
   * _Nota sulla correzione_: il sistema ora calcola correttamente l&#39;importo dello sconto per le regole di vendita con importi fissi del carrello, assicurando l&#39;applicazione di sconti precisi indipendentemente dalle modifiche apportate agli articoli del carrello. In precedenza, l’importo dello sconto poteva variare in modo errato quando gli articoli del carrello cambiavano, risultando a volte in sconti notevolmente più grandi del previsto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38694>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_: la casella di controllo Termini e condizioni non consente l&#39;utilizzo di HTML nella vetrina
   * _Correzione nota_: il sistema ora supporta la formattazione di HTML nel testo della casella di controllo &quot;Termini e condizioni&quot; nella vetrina, consentendo una personalizzazione e una leggibilità migliorate. In precedenza, il testo della casella di controllo veniva visualizzato in formato testo normale, ignorando eventuali tag di HTML utilizzati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: la regola del prezzo del carrello creata per l&#39;utente connesso non viene applicata correttamente per l&#39;utente non connesso
   * _Correzione nota_: il sistema ora rimuove correttamente la regola del prezzo del carrello per gli utenti connessi quando vengono disconnessi automaticamente a causa della scadenza dei cookie, assicurandosi che lo sconto non venga applicato agli utenti non connessi. In precedenza, la regola del prezzo del carrello veniva ancora applicata anche quando l’utente veniva disconnesso, causando l’applicazione di uno sconto errato agli utenti non connessi.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38944>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Problema] [FUNZIONALITÀ] Ottimizzazione delle prestazioni dei grandi carrelli acquisti impedendo...
   * _Correzione nota_: il sistema ora ottimizza le prestazioni per i carrelli acquisti di grandi dimensioni impedendo chiamate getActions duplicate, migliorando la velocità e l&#39;efficienza delle operazioni del carrello. In precedenza, per un carrello con più elementi, la funzione getActions veniva chiamata più volte, rallentando le prestazioni del sistema.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39292>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39290>
* _AC-13797_: il collegamento del Registro di sistema per gli omaggi non funziona correttamente
* _ACP2E-3176_: [Cloud] ordina rapidamente grandi quantità di prestazioni SKU
   * _Nota corretta_: le prestazioni di estrazione sono state migliorate quando gli attributi utilizzati nelle regole di prezzo del carrello non sono presenti per tutti i prodotti e quando la funzione MAP (Prezzo minimo annunciato) è abilitata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: elementi duplicati nel carrello
   * _Correzione nota_: il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello in Storefront generava più righe per lo stesso SKU.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: la conferma dell&#39;ordine di estrazione viene inviata alle e-mail immesse in Nome/Cognome
   * _Nota sulla correzione_: la conferma e-mail dell&#39;ordine di pagamento, inviata in precedenza quando nei campi Nome e Cognome è stato inserito un pattern simile a quello dell&#39;e-mail, non verrà più inviata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: Estrai il modulo dell&#39;indirizzo di spedizione e ottieni l&#39;aggiornamento con un indirizzo errato
   * _Correzione nota_: shippingAddressFromData è ora salvato nell&#39;archivio locale per sito Web. In precedenza, un indirizzo del sito Web errato poteva essere inserito automaticamente nel modulo dell’indirizzo di spedizione durante il pagamento se nell’URL veniva utilizzato un codice store e il pagamento veniva avviato da più siti Web durante la stessa sessione guest.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_: [CLOUD] L&#39;estrazione non mantiene l&#39;indirizzo di fatturazione selezionato quando la ricerca indirizzi è abilitata
   * _Nota sulla correzione_: la pagina Pagamento estratto conserverà l&#39;indirizzo di fatturazione selezionato quando la ricerca degli indirizzi è abilitata. In precedenza, se &quot;Limite numero di indirizzi cliente&quot; è configurato su 1 e il cliente ha più di un indirizzo, l’indirizzo di fatturazione selezionato scompare dopo il ricaricamento della pagina.
* _ACP2E-3407_: Prodotto gift card | Unione carrello: unione delle gift card
   * _Correzione nota_: i prodotti Giftcard ora sono stati uniti correttamente nel carrello
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: i dati delle virgolette esistenti non sono aggiornati/non visibili, ma crea un nuovo record delle virgolette quando trigger_recollect = 1
   * _Nota corretta_: gli elementi del carrello del cliente non scompaiono più a causa dell&#39;eliminazione di un prodotto dopo che è stato aggiunto al carrello.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogo

* _AC-11970_: impossibile riordinare i prodotti configurabili con una casella di controllo selezionata come opzione personalizzata
   * _Correzione nota_: il sistema ora elabora correttamente il riordino dei prodotti configurabili con una singola opzione personalizzata di casella di controllo selezionata, consentendo la corretta creazione del carrello. In precedenza, il tentativo di riordinare tali prodotti causava un errore e impediva l’aggiunta degli articoli al carrello.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38736>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_: opzioni a discesa mancanti
   * _Correzione nota_: il sistema ora visualizza correttamente tutti i valori nel menu a discesa quando crea un nuovo attributo con più di 20 valori. In precedenza venivano visualizzati solo i primi 20 valori o un altro valore di pagina selezionato, causando la mancanza dei valori rimanenti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problema] Utilizza l&#39;ID di archiviazione corrente per la cache runtime delle categorie
   * _Correzione nota_: il sistema ora utilizza correttamente l&#39;ID archivio corrente per la cache runtime delle categorie, impedendo la sostituzione dei dati quando viene utilizzata l&#39;emulazione o quando il codice personalizzato salva la categoria in archivi diversi. In precedenza, l’oggetto archiviato in fase di esecuzione poteva provenire da un archivio errato, con conseguente sostituzione dei dati.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39310>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update genera un&#39;eccezione
   * _Correzione nota_: il sistema ora accetta correttamente un valore booleano quando si utilizza l&#39;opzione —no-update nel comando sampledata:deploy, evitando errori durante la distribuzione dei dati di esempio. In precedenza, veniva generato un errore durante l’utilizzo di questo comando, poiché il sistema prevedeva erroneamente un valore intero.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39344>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problema] Correzione dell&#39;utilizzo del tipo di cache EAV
   * _Correzione nota_: il sistema ora utilizza correttamente il tipo di cache EAV in tutte le posizioni pertinenti, garantendo una memorizzazione coerente ed efficiente dei dati nella cache. In precedenza, il tipo di cache EAV non veniva utilizzato in modo coerente, con potenziali inefficienze e incoerenze nella memorizzazione dei dati nella cache.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32322>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: la ricerca avanzata del catalogo con dati vuoti viene visualizzata nella pagina dei risultati della ricerca[2.4.dev branch]
   * _Correzione nota_: il sistema ora mantiene correttamente gli utenti nella pagina Ricerca avanzata e visualizza un messaggio di errore quando tentano di eseguire una ricerca senza immettere alcun dato. In precedenza, l’esecuzione di una ricerca vuota reindirizzava gli utenti alla pagina Ricerca avanzata catalogo con un messaggio che chiedeva di modificare la ricerca.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_: impossibile rimuovere il bordo bianco dopo aver disabilitato product_image_white_edges per il tema personalizzato
* _ACP2E-3103_: il feed RSS dei nuovi prodotti non viene aggiornato con i nuovi prodotti a causa della cache
   * _Nota sulla correzione_: il feed Rss per i nuovi prodotti viene aggiornato quando un prodotto viene impostato come nuovo e salvato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [cloud] problema di zoom e spostamento a due dita sul dispositivo mobile reale
   * _Correzione nota_: il sistema ora garantisce una funzionalità di zoom coerente delle immagini sui dispositivi mobili, fornendo un&#39;esperienza utente fluida e prevedibile. In precedenza, la funzione di zoom dell’immagine era incoerente e improvvisamente si riduceva dopo un certo punto quando veniva visualizzata su un dispositivo mobile.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: quando si rimuovono le assegnazioni di prodotti dal catalogo condiviso, i prodotti della lista dei desideri non vengono cancellati
   * _Correzione nota_: se un prodotto non è disponibile nel catalogo condiviso, nella lista dei desideri non sarà visibile alcun elemento. In precedenza, la pagina della lista dei desideri mostrava erroneamente un conteggio di &quot;1 elemento&quot; anche quando nessun elemento era effettivamente disponibile nella lista dei desideri.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Prodotti correlati Seleziona tutto/Deseleziona tutto
   * _Correzione nota_: in precedenza, i pulsanti &quot;Seleziona tutto&quot;/&quot;Deseleziona tutto&quot; per i prodotti correlati non funzionavano correttamente se un prodotto era stato selezionato manualmente. Dopo la correzione, questi pulsanti ora funzionano in modo coerente, anche dopo la selezione manuale, garantendo che tutti i prodotti siano selezionati correttamente o deselezionati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Traduzione dell&#39;avviso tramite posta elettronica Stock nella lingua errata
   * _Correzione nota_: quando si inviano avvisi su azioni/prezzi per un sito Web con più visualizzazioni dello store che utilizzano lingue diverse, nell&#39;e-mail verrà utilizzata la lingua per la visualizzazione dello store in cui è stato creato l&#39;avviso.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: i nomi delle categorie disabilitate non sono più disattivati nella struttura delle categorie
   * _Correzione nota_: in precedenza, le categorie disabilitate non erano disattivate nella struttura delle categorie. Ora vengono visualizzate con un effetto di grigio.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: il caricamento del modulo di modifica del prodotto configurabile causa timeout e esaurimento della memoria
   * _Nota sulla correzione_: prima della correzione, le varianti di prodotto configurabili erano costruite in base a tutte le possibili combinazioni di opzioni di attributo. Nei casi in cui gli attributi disponevano di numerose opzioni, l’operazione risultava lunga e dispendiosa in termini di risorse. Ora le varianti di prodotto configurabili sono costruite in base agli attributi di prodotto secondari esistenti. Ciò comporta un numero molto inferiore di calcoli, quindi un migliore utilizzo delle risorse.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama non carica il video correttamente quando si utilizzano i campioni e l&#39;opzione è preselezionata tramite URL
   * _Nota corretta_: se l&#39;URL contiene le opzioni selezionate, ora i video dei prodotti verranno riprodotti correttamente nella pagina dei dettagli del prodotto configurabile.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: il widget Carosello PageBuilder mostra prodotti che non soddisfano le condizioni
   * _Nota corretta_: l&#39;elenco dei prodotti utilizzato nei widget rispetta ora la condizione della categoria
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Errore di convalida attivato per tutti i prodotti del gruppo quando una quantità non è valida
   * _Correzione nota_: ora l&#39;errore di convalida viene attivato correttamente per tutti i prodotti del gruppo quando un prodotto ha una quantità non valida, cosa che non si verificava in precedenza.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: le tabelle temporanee degli indicizzatori non vengono pulite se il processo viene terminato
   * _Nota corretta_: le tabelle temporanee dell&#39;indicizzatore CatalogRule vengono ora pulite se il processo di indicizzazione viene terminato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] errori di unit test di base in 2.4.7-p3
   * _Nota sulla correzione_: le note sulla versione per questo test non sono necessarie perché si tratta di un miglioramento di unit test.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogo, contenuto

* _ACP2E-3063_: la cache [Cloud] non viene invalidata.
   * _Correzione nota_: in precedenza, quando si salvava una pagina CMS con un layout di progettazione aggiornato, la visualizzazione non veniva eseguita correttamente nel front-end. Una volta applicata questa correzione, il layout di progettazione appropriato sarà visibile nel front-end quando si modifica il layout di progettazione e si salva la pagina CMS.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Categorie di ancoraggio/non di ancoraggio cloud] invertite nel widget del contenuto
   * _Correzione nota_: in precedenza, quando si selezionava Visualizza su -> Categorie di ancoraggio, venivano visualizzate tutte le categorie che non riflettevano la relazione padre-figlio tra l&#39;ancoraggio e il non ancoraggio. Dopo l&#39;applicazione di questa correzione, Visualizza attivato -> Categorie di ancoraggio visualizza solo le Categorie di ancoraggio (selezionabile), mentre Visualizza attivato -> Categorie non di ancoraggio visualizza le Categorie non di ancoraggio (selezionabile)
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: categorie che non funzionano con i widget
   * _Correzione nota_: in precedenza, se il blocco CMS veniva salvato per diverse categorie di ancoraggio/non di ancoraggio, non funzionava per le categorie figlio visualizzate nel front-end. Dopo l’applicazione di questa correzione, il blocco viene visualizzato nel front-end per diverse categorie.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catalogo, GraphQL

* _ACP2E-3312_: i prezzi di livello restituiscono un valore errato nei prodotti GraphQL (rispetto a Storefront)
   * _Nota sulla correzione_: dopo la correzione, i prezzi del livello del prodotto restituiti per le richieste graphql hanno prezzo per un elemento.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: problema di categoria tramite GraphQL
   * _Correzione nota_: dopo la correzione, la query graphql delle categorie restituisce le categorie con l&#39;autorizzazione Consenti anche se la categoria principale non dispone dell&#39;autorizzazione Consentita.

### Catalogo, Ricerca

* _ACP2E-3345_: errore di tipo durante la creazione dell&#39;oggetto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Nota sulla correzione_: dopo la correzione, è possibile creare un&#39;istanza della classe Magento\CatalogSearch\Model\Indexer\Fulltext senza specificare $data.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [Il problema di CLOUD] con i prodotti non è visibile in Frontend dopo il salvataggio in Magento Admin
   * _Correzione nota_: dopo la correzione, i prodotti configurabili con prodotti secondari con nomi lunghi non verranno persi nella vetrina.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogo, spedizione

* _ACP2E-3195_: indirizzo di spedizione vuoto durante l&#39;invio di un ordine per un articolo del Registro di sistema relativo a regali
   * _Correzione nota_: in precedenza, per gli elementi del registro regali degli utenti ospiti, quando venivano restituiti dalla funzione e-mail, veniva generato un indirizzo vuoto, che non era corretto per l&#39;ordine. Dopo l&#39;applicazione di questa correzione, il Registro di sistema per i regali controlla gli utenti connessi/ospiti e gli indirizzi assegnati, se presenti.

### Contenuto

* _AC-12692_: l&#39;albero delle categorie del widget non è visualizzato correttamente
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39008>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: impossibile visualizzare il messaggio &quot;Utilizzo del valore predefinito&quot; durante la modifica del tema nella pagina di configurazione della progettazione
   * _Correzione nota_: il sistema ora include una colonna separata per visualizzare il messaggio &quot;Utilizzo del valore predefinito&quot; a seconda del tema selezionato nella pagina di configurazione della progettazione. Questo garantisce chiarezza e visibilità dello stato del valore predefinito. In precedenza, il messaggio &quot;Using Default value&quot; (Utilizzo del valore predefinito) non veniva visualizzato, generando confusione sullo stato del tema selezionato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problema] Ripristina nuovamente la compatibilità con le versioni precedenti dei plug-in TinyMCE (dopo...
   * _Correzione nota_: il sistema ora ripristina la compatibilità con le versioni precedenti dei plug-in TinyMCE, consentendo la chiamata delle funzioni definite all&#39;interno del plug-in quando si utilizza il widget da un&#39;altra posizione. In precedenza, a causa di una modifica nella versione TinyMCE, i plug-in non restituivano i widget come oggetto, causando un errore quando si tentava di chiamare alcune funzioni sull’istanza del widget.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39262>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [CLOUD] Il pulsante Carica immagine non funziona
   * _Correzione nota_: prima del pulsante Carica immagine per il banner e il dispositivo di scorrimento da PageBuilder non funzionava come previsto e ora, premendo, si apre il file manager locale per selezionare l&#39;immagine da caricare.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Cloud] - Il cursore di CMS non riflette le ultime modifiche
   * _Correzione nota_: il problema è stato risolto assicurandosi che l&#39;elenco di dispositivi di scorrimento venga aggiornato mentre l&#39;evento di salvataggio viene attivato nella schermata Modifica diapositiva. In precedenza, si attivava e causava il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: si è verificato un errore nella pagina CSM quando i blocchi CMS vengono inseriti utilizzando il generatore di pagine in un ordine specifico
   * _Correzione nota_: in precedenza, in alcune versioni di PHP e OS (Linux), il rendering dei blocchi che facevano riferimento ad altri blocchi CMS tramite PageBuilder non sarebbe riuscito con un &quot;Errore sconosciuto. Riprova.&quot;. Ora il contenuto dei blocchi cms viene riprodotto correttamente all’interno di un contenuto controllato da PageBuilder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [I blocchi dinamici del cloud] non funzioneranno correttamente
   * _Correzione nota_: i segmenti dei clienti connessi vengono ora cancellati dopo la disconnessione, impedendo alla sessione guest di ereditare i segmenti precedentemente connessi
* _ACP2E-3430_: ultimi aggiornamenti di sicurezza con dimensione font mancante in TinyMCE 7
   * _Nota corretta_: i selettori di dimensione e famiglia di caratteri sono ora disponibili nell&#39;editor di WYSIWYG. Prima di questa correzione, con TinyMCE 7 queste non erano disponibili nell’interfaccia dell’editor.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Cliente/clienti

* _AC-13060_: il segmento cliente > Condizione > Cronologia prodotto* > &quot;prodotto visualizzato&quot; non funziona
   * _Correzione nota_: il sistema ora visualizza correttamente i clienti registrati corrispondenti nella condizione &quot;Prodotto visualizzato&quot; in Segmenti cliente, quando la condizione viene soddisfatta. In precedenza, anche quando la condizione veniva soddisfatta, il numero di clienti registrati corrispondenti rimaneva pari a zero.
* _AC-8499_: il campo di testo dell&#39;area geografica non viene reimpostato quando viene modificato il menu a discesa del paese
   * _Correzione nota_: il sistema ora reimposta il campo di testo dell&#39;area geografica quando il paese viene modificato nel menu a discesa, assicurandosi che i valori precedenti non persistano. In precedenza, la modifica del paese dall’elenco a discesa non reimpostava il campo area e veniva mantenuto l’ultimo valore salvato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: l&#39;eliminazione del cliente non comporta la pulizia di tutti i dati della sessione del browser su Storefront per il cliente connesso ed eliminato
   * _Correzione nota_: l&#39;eliminazione di un cliente ora elimina tutti i dati della sessione del browser dalla vetrina per i clienti connessi ed eliminati come previsto. L’acquirente può continuare a fare acquisti e il browser tratta la sua sessione come una sessione ospite. In precedenza, quando l’account del cliente per un acquirente connesso veniva eliminato dall’amministratore, il browser dell’acquirente generava errori JavaScript.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10738_: la configurazione Vernice non esclude tutti i parametri di marketing
   * _Correzione nota_: il sistema ora esclude correttamente tutti i parametri di marketing comuni nella configurazione di Vernice, garantendo un tracciamento e un&#39;analisi accurati. In precedenza, alcuni parametri di marketing, come gad_source, srsltid e msclkid, non venivano esclusi, generando potenziali imprecisioni nella raccolta dei dati.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [Problema] Consenti solo preferenze valide durante l&#39;installazione:di:compilazione
   * _Correzione nota_: il sistema ora genera un errore durante il comando setup:di:compile se viene creata una preferenza per una classe che non esiste o che è specificamente esclusa, assicurandosi che siano consentite solo le preferenze valide. In precedenza, questi scenari avrebbero avuto esito negativo in silenzio, rendendo potenzialmente inutili i plug-in associati alle classi originali.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38517>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [Problema] Trasmettere gli attributi personalizzati al collegamento corrente tramite XML
   * _Correzione nota_: il sistema ora consente di passare attributi personalizzati al collegamento corrente tramite XML, garantendo che tali attributi vengano visualizzati correttamente anche quando il collegamento è la pagina corrente. In precedenza, gli attributi personalizzati non venivano visualizzati per il collegamento della pagina corrente perché il metodo getAttributesHtml() non veniva utilizzato per il collegamento corrente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38500>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/30070>
* _AC-12127_: [Problema] per evitare un loop infinito di configurazione errata
   * _Correzione nota_: il sistema ora evita un ciclo infinito impedendo la mappatura autoreferenziale nelle configurazioni dei tipi virtuali. In questo modo l’applicazione non si blocca in un ciclo infinito quando si tenta di dereferenziare un nodo autoreferenziale. In precedenza, se una configurazione di tipo virtuale fosse autoreferenziale, l’applicazione girerebbe indefinitamente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38822>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: Gestione oggetti non utilizzato per Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Correzione nota_: il sistema ora utilizza correttamente Object Manager durante la creazione dell&#39;oggetto ModeConfigured, consentendo l&#39;utilizzo di plug-in in questo oggetto. In precedenza, Object Manager non veniva utilizzato, impedendo l’applicazione dei plug-in all’oggetto ModeConfigured.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38875>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: commento non accurato del blocco di documenti negli avvisi su azioni e prezzi dei prodotti
   * _Correzione nota_: il commento di blocco del documento per il metodo deleteCustomer negli avvisi su azioni e prezzi del prodotto è stato corretto per riflettere con precisione che il metodo elimina tutti gli avvisi su azioni o prezzi associati a un determinato cliente e sito Web, non il cliente dal sito Web. In precedenza, il commento affermava erroneamente che il metodo era quello di eliminare un cliente dal sito web.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38939>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39001>
* _AC-12857_: estensione FTP rimossa da PHP 8.2.15
   * _Correzione nota_: il sistema ora include l&#39;estensione FTP come dipendenza nel file compositore.json, garantendo la corretta configurazione delle importazioni CSV tramite FTP. In precedenza, veniva generato un errore durante il tentativo di configurare le importazioni CSV tramite FTP a causa dell’assenza dell’estensione FTP nel pacchetto PHP.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: possibilità di definire l&#39;area per il comando dev:di:info CLI
   * _Correzione nota_: il sistema ora consente agli sviluppatori di definire un&#39;area per il comando dev:di:info CLI, migliorando il processo di sviluppo e debug. In precedenza, questo comando consentiva di visualizzare solo le informazioni relative all&#39;area GLOBAL.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: installazione:aggiornamento non riuscito con la versione MariaDB 11.4 a causa di modifiche a set di caratteri e regole di confronto
* _AC-13279_: [Problema] Rimuovi tutti i parametri di marketing get per ridurre al minimo la cache
   * _Correzione nota_: il sistema ora rimuove tutti i parametri di marketing get per ottimizzare l&#39;utilizzo della cache, rispecchiando la logica utilizzata quando è in uso Vernice. In precedenza, questi parametri potevano causare il gonfiore della cache e ridurre le prestazioni.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39266>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problema] [PHPDOC] Correzione di phpdoc non valido Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Correzione nota_: il metodo PHPDoc per AllowedCountries::getAllowedCountries() è stato corretto per fornire informazioni accurate, migliorando la chiarezza e l&#39;utilità della documentazione. Precedentemente, il PHPDoc per questo metodo conteneva informazioni errate, che potevano portare a confusione o uso improprio del metodo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39246>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Problema] Rimuove parte del codice per le versioni PHP non più supportate.
   * _Correzione nota_: rimozione del codice per le versioni PHP non più supportate in Magento
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39361>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problema] Rendere la scheda ImageMagick compatibile con php8 (conversione implicita da float a int)
   * _Correzione nota_: il sistema ora garantisce la compatibilità con PHP8 gestendo correttamente i numeri in virgola mobile durante il calcolo delle dimensioni dell&#39;immagine, evitando errori dovuti a una conversione implicita da virgola mobile a int. In precedenza, il calcolo delle dimensioni dell’immagine poteva causare numeri in virgola mobile che, se arrotondati in modo implicito, generavano un errore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39402>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problema] [PHPDOC] Correzione di phpdoc non valido Magento\Framework\App\Config\ScopeConfigInterface
   * _Correzione nota_: questo aggiornamento corregge le annotazioni PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface per riflettere con precisione il tipo di argomento $scopeCode per i metodi getValue e isSetFlag.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39492>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [Problema] Migliorare la registrazione degli errori cron
   * _Correzione nota_: il sistema ora acquisisce e registra sia STDERR che STDOUT per i processi cron, fornendo preziose informazioni diagnostiche negli scenari in cui i processi cron non riescono. In precedenza, eventuali messaggi di errore all’interno dei processi cron non venivano registrati e STDERR e STDOUT per i gruppi cron in esecuzione in processi separati andavano persi.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_: la modifica della lunghezza della colonna tramite db_schema.xml non funziona in caso di chiavi esterne
   * _Correzione nota_: la modifica di una colonna con una chiave esterna tramite uno schema dichiarativo ora non genera errori con MariaDB
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: alcuni dei record delle relazioni vengono salvati nel database al salvataggio del record dell&#39;ordine
   * _Nota di correzione_: prima della correzione venivano attivate query UPDATE non necessarie che possono avere un impatto sulle prestazioni. Dopo la correzione, le query UPDATE non necessarie sono state eliminate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [CLOUD] In admin sono presenti molti errori JavaScript nella console
   * _Correzione nota_: in precedenza, nel pannello di amministrazione erano presenti molti errori JavaScript nella console. Ora, nel pannello di amministrazione, non ci saranno errori JavaScript nella console e tutte le funzioni predefinite di JavaScript verranno eseguite correttamente senza alcun problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: il messaggio della coda è stato eliminato
   * _Correzione nota_: i messaggi della coda vengono cancellati correttamente. Prima della correzione, dato che il sistema della coda SQL era in uso, i nuovi messaggi potevano essere eliminati se il messaggio della coda di pulizia era in esecuzione allo stesso tempo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Framework, Framework interfaccia utente

* _ACP2E-3324_: possibilità di sovrascrivere il valore di configurazione anche se è bloccato
   * _Nota sulla correzione_: in precedenza, la configurazione della progettazione non poteva essere impostata tramite il comando bin/magento config:set e i valori bloccati potevano essere modificati modificando il modulo che li visualizzava. Dopo la correzione i valori bloccati impostati da cli con —lock-env o —lock-conf non possono più essere aggiornati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: le traduzioni per gli attributi restituiti dai clienti non si riflettono nell&#39;API GraphQL per il rispettivo StoreView
   * _Correzione nota_: le traduzioni per gli attributi restituiti dai clienti si riflettono nell&#39;API GraphQL per il rispettivo StoreView.
In precedenza, gli attributi di restituzione dei clienti per i rispettivi StoreView non venivano riportati nell’API di GraphQL.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [Cloud] problema con l&#39;autenticazione utente e l&#39;accesso ai token intersito nella configurazione multisito
   * _Correzione nota_: le query GraphQl su informazioni cliente e carrello in Configurazione multisito controllano se il cliente esiste su un sito Web non predefinito.
La query precedente funzionava senza assicurarsi che il cliente esistesse su un sito Web non predefinito in Configurazione multisito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: è necessario specificare il valore del modello [GRAPHQL] per ottenere customerCart
   * _Correzione nota_: la query &#39;customerCart&#39; di GraphQL può ora creare un carrello vuoto anche quando il preventivo non è disponibile nel database. In precedenza, questa operazione non riusciva a causa di problemi di convalida del paese durante la creazione del carrello vuoto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [Gli elementi della lista dei desideri GraphQl] sono visibili tramite GraphQl ma non nella vetrina
   * _Correzione nota_: prodotti della lista dei desideri in cui non sono elencati correttamente quando richiesto tramite GraphQL. Adesso, i prodotti della lista dei desideri vengono filtrati in base al contesto del negozio fornito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Ripristina incoerenza e-mail password tra contenuto e oggetto/collegamento
   * _Correzione nota_: il problema è stato risolto simulando l&#39;archivio corretto in cui è registrato l&#39;account del cliente al momento dell&#39;invio della richiesta di reimpostazione della password, indipendentemente dall&#39;archivio del sito Web.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] prodotti La query GraphQL restituisce prodotti correlati non assegnati al sito Web corrente
   * _Correzione nota_: in precedenza, per la query graphQL, i prodotti correlati a più store non venivano visualizzati correttamente per la query del prodotto. Dopo l’applicazione di questa correzione, per i prodotti, graphQL esegue una query sui prodotti correlati a più store visualizzati di conseguenza.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: l&#39;utilizzo di un ID archivio errato nell&#39;intestazione di GraphQL causa un errore irreversibile di memoria
   * _Correzione nota_: l&#39;invio di codice archivio errato nella richiesta GraphQL non comporta più un consumo eccessivo di memoria.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Cloud] 500 risposta a Graphql vuota nella versione 2.4.7
   * _Correzione nota_: dopo la correzione, le richieste graphql non valide non verranno registrate nel file exception.log.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_: aumento della complessità massima predefinita delle query GraphQL a 1000

### GraphQL, Cerca

* _ACP2E-948_: query GraphQL di elenco prodotti limitata a un totale di 10.000 prodotti
   * _Nota sulla correzione_: dopo la correzione, il risultato della ricerca non è limitato ai prodotti 10000, è possibile ottenere tutti i prodotti che corrispondono ai criteri di ricerca anche se il conteggio è superiore a 10000.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, framework di prova

* _ACP2E-3363_: errore test integrazione Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importa/esporta

* _ACP2E-3172_: pulsante Importa mancante
   * _Correzione nota_: per risolvere il problema di mancanza del pulsante Importa dopo la verifica dei dati con record corretti e non corretti nel file CSV. In precedenza, il pulsante di importazione non veniva visualizzato dopo il controllo dei dati con record corretti e non corretti nel file CSV.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: impossibile importare l&#39;indirizzo del cliente esportato
   * _Correzione nota_: l&#39;importazione dell&#39;indirizzo del cliente procederà come previsto. In precedenza, un file di importazione dell’indirizzo di un cliente non superava la convalida se Condividi account del cliente = Globale ed esistono due siti web in cui il sito web predefinito ha un elenco di paesi limitato e l’indirizzo che viene importato è per un altro sito web in cui i paesi consentiti sono diversi
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] La quantità errata nel file CSV non ha restituito alcun errore
   * _Correzione nota_: ora l&#39;importazione di origini di magazzino genererà un errore di convalida per i valori non numerici nella colonna Quantità. In precedenza, l&#39;importazione di origini di scorte con valore non numerico nella colonna Quantità comportava l&#39;impostazione della quantità su 0.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: l&#39;esportazione del prodotto causa OOM anche con il limite di memoria 4G
   * _Nota sulla correzione_: prima di questa correzione, l&#39;esportazione del prodotto non è riuscita se gli attributi del prodotto avevano migliaia di valori di opzione anche con memoria 4G disponibile. Dopo questa correzione, l’esportazione del prodotto dovrebbe terminare l’esportazione del file CSV.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Importazione/esportazione, prestazioni

* _ACP2E-3476_: [Cloud] Il tempo di importazione del prodotto è aumentato in modo significativo
   * _Nota sulla correzione_: prima della correzione, l&#39;importazione di prodotti catalogo con più di 10.000 voci presentava una notevole riduzione del tempo. Dopo la correzione, l’importazione del prodotto catalogo viene eseguita in modo tempestivo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Installazione e amministrazione

* _AC-13242_: aggiornamento Magento non riuscito in MariaDB 11.4 + 2.4.8-beta1
   * _Correzione nota_: l&#39;aggiornamento dovrebbe essere eseguito senza errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>

### Inventario/MSI

* _ACP2E-3335_: impossibile spedire l&#39;ordine quando l&#39;archivio di ritiro MSI è abilitato
   * _Correzione nota_: sono state migliorate le prestazioni di inventario per creare la spedizione in caso di numerose origini con prelievo in-store
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: la reindicizzazione Cron non riesce ad aggiornare la disponibilità del prodotto sul front-end
   * _Correzione nota_: in precedenza, i prodotti rimanevano esauriti sul front-end dopo l&#39;aggiornamento dello stato dell&#39;ordine arretrato tramite l&#39;API REST. Ora, dopo aver aggiornato lo stato dell’ordine inevaso tramite l’API REST, i prodotti vengono visualizzati come in stock.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: l&#39;aggiunta di immagini a configurabile non funziona quando MSI è abilitato.
   * _Nota corretta_: il caricamento dell&#39;immagine per il prodotto configurabile ora funziona come previsto quando viene utilizzato il modulo inventario. In precedenza, il caricamento dell’immagine non funzionava
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/fdf409aa>

### Magazzino/MSI, Ricerca

* _ACP2E-3413_: tutti i prodotti sono indicizzati con [is_out_of_stock] = 1 quando lo SKU non è impostato come attributo ricercabile
   * _Nota sulla correzione_: dopo la correzione, &quot;is_out_of_stock&quot; nell&#39;indice di ricerca del catalogo è corretto, anche quando lo SKU non è ricercabile.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>

### Ordine

* _ACP2E-3311_: [Cloud] Impossibile creare l&#39;ordine in admin su un archivio se non è stato impostato solo l&#39;indirizzo di fatturazione predefinito
   * _Correzione nota_: messaggio di errore pertinente &quot;Un cliente con lo stesso indirizzo e-mail esiste già in un sito Web associato&quot;. viene visualizzato se un cliente non ha un indirizzo di fatturazione predefinito e tenta di creare un ordine in un altro negozio.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: richieste di ordine di luogo duplicate inviate dall&#39;amministratore
   * _Correzione nota_: in precedenza, era possibile fare clic più volte sul pulsante &quot;Invia ordine&quot; nel pannello di amministrazione o attivarlo premendo ripetutamente il tasto &quot;Invio&quot;, causando invii duplicati o ordini con errore. Ora, impedendo ulteriori azioni fino a quando l’ordine non è completamente elaborato, garantendo che venga inviato un solo ordine.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: l&#39;amministratore può ancora effettuare l&#39;ordine anche senza il metodo di pagamento
   * _Nota sulla correzione_: il metodo di pagamento selezionato in precedenza viene mantenuto quando il metodo di pagamento viene nuovamente visualizzato nell&#39;elenco dei pagamenti disponibili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Ordine, Pagamenti

* _ACP2E-3233_: l&#39;amministratore può ancora effettuare l&#39;ordine anche senza il metodo di pagamento
   * _Correzione nota_: in precedenza, il commerciante poteva effettuare ordini dal pannello di amministrazione senza selezionare un metodo di pagamento. Ora, il commerciante è richiesto un metodo di pagamento per procedere con l&#39;effettuazione di un ordine.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Altro

* _LYNX-426_: la percentuale di sconto non è calcolata per i prodotti bundle con prezzo dinamico
* _LYNX-485_: i prodotti del bundle mostrano ancora &quot;IN_STOCK&quot; quando uno dei suoi prodotti del bundle è esaurito
* _LYNX-486_: not_available_message e only_x_left_in_stock non mostra lo stesso stock disponibile
* _LYNX-488_: il campo original_row_total restituisce un valore errato
* _LYNX-503_: la miniatura del prodotto raggruppato deve essere visualizzata in base alla configurazione     .
* _LYNX-510_: errore durante la query di selected_options in OrderAddress
* _LYNX-512_: original_item_price non include sconti
* _LYNX-530_: il messaggio Non disponibile non mostra la quantità di magazzino disponibile
* _LYNX-532_: lo stato &quot;OUT_OF_STOCK&quot; viene restituito su Semplice con opzioni personalizzate e prodotti con opzioni a selezione multipla
* _LYNX-533_: Errore (GQL): cart.itemsV2.items.product.custom_attributesV2 restituisce un errore del server
* _LYNX-536_: orders/date_of_first_order restituisce sempre null
* _LYNX-544_: il cliente non deve essere in grado di annullare un ordine parzialmente spedito
* _LYNX-548_: codici di errore per l&#39;annullamento dell&#39;ordine in base al messaggio di errore
* _LYNX-581_: torna indietro le proprietà relative ai cookie da private a protected

### Altri strumenti per sviluppatori

* _AC-12731_: problemi CSP combinati con dev/css/use_css_critical_path
   * _Correzione nota_: il sistema ora carica correttamente i file CSS in modo asincrono nelle pagine di estrazione, anche quando l&#39;impostazione &#39;dev/css/use_css_critical_path&#39; è abilitata, assicurandosi che tali pagine vengano sottoposte a rendering con gli stili CSS appropriati. In precedenza, i criteri sulla sicurezza dei contenuti (CSP) con restrizioni impedivano l’esecuzione di JavaScript in linea, causando il mancato caricamento dei file CSS come previsto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39020>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: utilizzando il tipo virtuale per configurare il plug-in, il metodo intercettore non può essere generato correttamente nel comando setup:di:compile
   * _Correzione nota_: il sistema ora genera correttamente i metodi intercettore quando utilizza un tipo virtuale per configurare un plug-in, garantendo risultati coerenti sia in modalità precompilata che in modalità runtime. In precedenza, il sistema generava risultati errati se precompilato rispetto alla compilazione in fase di esecuzione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/33980>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: impossibile scaricare file dall&#39;agente di raccolta dati
   * _Correzione nota_: il download del backup non mostra più una pagina vuota invece di scaricare il file.

### Pagamenti

* _ACP2E-3143_: il rimborso dell&#39;ordine PayPal risulta in una nota di credito duplicata
   * _Correzione nota_: è stato risolto un problema di concorrenza delle note di credito create tramite IPN per il servizio di pagamento PayPal.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: la regola del prezzo del carrello non funziona per Paypal
   * _Nota sulla correzione_: l&#39;importo corretto viene visualizzato sul lato PayPal quando lo sconto viene applicato con il metodo di pagamento
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Cloud] Gli utenti con un ruolo specifico non possono accedere
   * _Correzione nota_: l&#39;utente amministratore con un ruolo che contiene solo l&#39;accesso alla sezione PayPal ora può accedere senza errori
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>

### Prestazioni

* _AC-11932_: problema impostazioni attributi prodotto predefinite
   * _Correzione nota_: il sistema ora consente agli utenti di deselezionare un&#39;opzione predefinita per un attributo di prodotto, assicurandosi che non sempre sia impostato un attributo predefinito. In precedenza, una volta impostato un valore predefinito per un attributo di prodotto, non era possibile deselezionarlo, in modo che l’attributo avesse sempre un valore predefinito.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38703>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: supporto per CommandLoaderInterface di Symfony in Magento CLI
   * _Correzione nota_: questa modifica riduce il tempo di inizializzazione dell&#39;app Magento CLI consentendo l&#39;inizializzazione differita dei comandi fino a quando non sono necessari.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29266>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29355>

### Prodotto

* _AC-13173_: [Problema] Correzione dell&#39;errore di battitura nel blocco PHPDoc
   * _Correzione nota_: il sistema ora rimuove correttamente una variabile di riferimento sconosciuta in PHPDoc per la dichiarazione della variabile $helper, migliorando la chiarezza e la precisione del codice. In precedenza, questa variabile di riferimento sconosciuta in PHPDoc causava confusione e potenziali imprecisioni nel codice.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38961>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] è stato corretto il bundle interrotto e il layout delle pagine di prodotto scaricabili in Magento >= 2.4.7
   * _Correzione nota_: il layout per il bundle e le pagine di prodotto scaricabili è stato corretto, garantendo una visualizzazione coerente e corretta su tutti i dispositivi. In precedenza, in queste pagine si verificavano problemi di layout a causa di una ridisposizione del blocco multimediale di informazioni sul prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [Cloud] Prodotti nella categoria - Aggiungi prodotti - Assegna - Seleziona tutto
   * _Correzione nota_: gli utenti possono ora selezionare o deselezionare i prodotti utilizzando l&#39;interruttore.

### Promozione

* _ACP2E-3139_: la regola di vendita con l&#39;attributo Passo quantità sconto (X acquisto) causa l&#39;applicazione di altre regole
   * _Correzione nota_: la regola del prezzo del carrello non annulla le regole applicate in precedenza se la quantità del prodotto nel carrello non è sufficiente per applicare la regola.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: problema di prestazioni nella regola del prezzo del carrello - Modulo regola vendite anticipate
   * _Correzione nota_: aggiunti indici DB mancanti per filtri AdvancedSalesRule
* _ACP2E-3332_: emettere le regole di vendita con sconto di importo fisso e &quot;Sconto quantità massima applicato a&quot;
   * _Nota corretta_: è stato risolto un problema relativo allo sconto sulle regole del carrello, quando lo sconto sull&#39;importo fisso è configurato per essere applicato per una quantità limitata di prodotti ed è il carrello. In precedenza, il valore &quot;Sconto quantità massima viene applicato a&quot; veniva utilizzato per calcolare il prezzo dell’articolo corrente nel carrello, non solo per calcolare lo sconto della regola.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: [L&#39;aggiornamento del Magento CLOUD] ha causato la distinzione tra maiuscole e minuscole per i coupon
   * _Correzione nota_: prima della correzione era necessario digitare il codice coupon esattamente come configurato, tenendo conto delle lettere maiuscole o minuscole. Ora il coupon viene convalidato nel backend indipendentemente dalla configurazione del codice in maiuscolo o in minuscolo.
* _ACP2E-3349_: regole del carrello &quot;Sconto importo fisso per carrello intero&quot;  L&#39;azione applica gli sconti in modo errato
   * _Correzione nota_: i codici coupon verranno convalidati correttamente indipendentemente dalla maiuscola o dalla minuscola, se utilizzati per la creazione degli ordini dall&#39;area di amministrazione. In precedenza, il codice del coupon non veniva convalidato se non corrispondeva esattamente alla lettera maiuscola del codice della regola del carrello configurato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: nel back-end, i valori di archivio predefiniti per gli attributi del prodotto (anziché i valori di amministrazione previsti)
   * _Correzione nota_: ora nel back-end vengono utilizzati i valori di amministrazione invece dei valori di archivio predefiniti per gli attributi di prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: l&#39;azione &quot;Sconto importo fisso per carrello intero&quot; delle regole del carrello applica gli sconti in modo errato quando si aggiungono prodotti bundle
   * _Nota fissa_: le regole del carrello a importo fisso non venivano applicate correttamente per i prodotti bundle. Ora, quando si calcola l&#39;importo dello sconto totale, vengono presi in considerazione i prodotti secondari del bundle, con conseguente calcolo dello sconto corretto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: le regole di prezzo del carrello calcolano erroneamente lo sconto
   * _Nota sulla correzione_: gli sconti sull&#39;importo fisso vengono ora calcolati correttamente. Prima della correzione, gli sconti sull&#39;importo fisso non venivano totalizzati correttamente per i prodotti bundle.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: le categorie nidificate nelle condizioni della regola non vengono visualizzate
   * _Nota corretta_: è stato corretto un problema a causa del quale le categorie nidificate nella categoria di livello 3 non venivano visualizzate nelle regole di marketing per la condizione della categoria
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit e uses_per_customer non vengono aggiornati nella tabella salesrule_coupon
   * _Correzione nota_: l&#39;aggiornamento degli usi per coupon e degli usi per cliente nella regola prezzo carrello ora influisce sui coupon generati automaticamente esistenti. In precedenza, i nuovi valori interessavano solo i nuovi coupon
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: la regola del prezzo del carrello non considera la categoria padre quando si utilizza la condizione &quot;è uguale o maggiore di&quot;.
   * _Correzione nota_: le regole del prezzo del carrello ora considerano correttamente la categoria padre quando viene utilizzata in condizioni avanzate
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: calcolo sconto non valido con priorità
   * _Nota sulla correzione_: nel caso dell&#39;importo fisso applicato per l&#39;intero tipo di sconto del carrello, l&#39;importo non veniva calcolato correttamente per gli articoli del carrello già scontati da una promozione precedente. Ora, gli sconti sono correttamente sommati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_: valore di sconto errato quando più regole di prezzo del carrello vengono applicate contemporaneamente a prodotti scontati/a prezzi speciali
   * _Nota sulla correzione_: prima della correzione, l&#39;importo fisso per le regole dell&#39;intero carrello non veniva applicato correttamente se ne veniva applicato più di uno. Ora, le regole del carrello sconti per importo fisso vengono applicate correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Restituisce

* _ACP2E-3330_: [CLOUD] Gli utenti amministratori con restrizioni possono visualizzare il menu e i pulsanti restituiti
   * _Correzione nota_: gli utenti amministratori con restrizioni ora non hanno accesso ai controlli relativi a RMA (menu e pulsanti).
Gli utenti amministratori con restrizioni precedenti potevano visualizzare il menu e i pulsanti di ritorno.
* _ACP2E-3443_: la schermata di ritorno è incasinata quando si aggiorna la schermata
   * _Correzione nota_: l&#39;utente può aggiornare la pagina senza che si verifichi una distorsione dello schermo.

### Vendite

* _AC-13750_: il totale complessivo e il totale complessivo di base non corrispondono ai passaggi dei risultati del test
* _AC-13751_: la regola del prezzo del secondo carrello non viene applicata se la regola Primo carrello è già applicata

### Ricerca

* _AC-13053_: Recupero di &quot;Immettere un termine di ricerca e riprovare&quot;. errore nella pagina di ricerca avanzata in storefront nella versione 2.4.8-beta1
   * _Nota sulla correzione_: i risultati della ricerca vengono ora visualizzati correttamente nella pagina Ricerca avanzata quando un attributo di prodotto è impostato su &quot;No&quot;. In precedenza, se si impostava un attributo di prodotto su &quot;No&quot; e si eseguiva una ricerca, veniva visualizzato un messaggio di errore di tipo &quot;Inserisci un termine di ricerca e riprova&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search dipende da un ramo opensearch-php non esistente
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: tabella search_query di grandi dimensioni che influisce notevolmente sul tempo di caricamento front-end
   * _Correzione nota_: è stato migliorato il tempo di caricamento della pagina dell&#39;elenco ricerche. Prima della correzione, la pagina dell’elenco di ricerca subiva un ritardo a causa di una query non ottimizzata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Sicurezza

* _ACP2E-3273_: ReCaptcha V2 non viene visualizzato correttamente al momento dell&#39;estrazione per la lingua tedesca
   * _Correzione nota_: in precedenza i recaptcha da sotto l&#39;indirizzo e-mail da checkout venivano visualizzati in modo non stilizzato per le lingue con parole lunghe, come il tedesco. Dopo questo il recaptcha si presenta come tutti gli elementi recaptcha dal resto delle aree.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha all&#39;accesso amministratore non richiede interazione per alcuni utenti
   * _Correzione nota_: ReCaptcha per l&#39;accesso amministratore è stato convalidato come previsto

### Spedizione

* _AC-12938_: aggiornamenti delle istruzioni di installazione REST &quot;sandbox&quot; e &quot;prod&quot; di UPS in devdoc
* _ACP2E-3340_: l&#39;API Track FedEx non funziona con le credenziali REST
   * _Correzione nota_: in precedenza l&#39;integrazione FedEx non richiedeva chiavi API aggiuntive per l&#39;API di tracciamento. Ora è stata aggiunta una nuova configurazione per supportare le chiavi API di tracciamento.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] tariffe negoziate FedEx non restituite su REST
   * _Nota sulla correzione_: prima della correzione, le tariffe specifiche dell&#39;account FedEx non venivano inviate nella risposta, anche se in base alla documentazione FedEx dovevano essere state inviate. Dopo la correzione, i tassi specifici dell’account vengono inviati alla risposta modificando la richiesta dal nostro lato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Staging e anteprima

* _ACP2E-3453_: impossibile aggiornare l&#39;aggiornamento pianificato quando si utilizza un attributo di categoria personalizzato univoco
   * _Correzione nota_: è stato risolto un problema che impediva l&#39;aggiornamento pianificato di una categoria se questa aveva un attributo univoco
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Imposta

* _ACP2E-3193_: l&#39;FPT (Fixed Product Tax) non funziona con i prodotti configurabili
   * _Correzione nota_: FPT per il corretto funzionamento delle varianti di prodotto configurabili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Framework di test

* _AC-13362_: [Problema] Controllo ortografico della correzione PHPDoc
   * _Correzione nota_: il sistema ora riconosce correttamente i metodi obsoleti negli IDE a causa di una correzione ortografica nel PHPDoc. In precedenza, un errore ortografico nel PHPDoc causava il mancato riconoscimento da parte degli IDE di alcuni metodi come obsoleti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/31399>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: controllo del comportamento con il carrello permanente dopo la scadenza della sessione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: test di integrazione non riusciti Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest
   * _Correzione nota_: mftfs corretti
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Framework interfaccia utente

* _AC-12432_: Campo File Componente Interfaccia Utente
   * _Correzione nota_: il sistema ora convalida correttamente il campo del file in un modulo componente dell&#39;interfaccia utente, consentendo l&#39;invio del modulo senza errori quando viene selezionato un file. In precedenza, la convalida non riusciva anche quando veniva selezionato un file, impedendo l’invio del modulo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38908>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problema] Formato data migliorato nella console js: passa da 12 ore a 24 ore per...
   * _Correzione nota_: formato data migliorato nella console js: passaggio da 12 ore a 24 ore
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38983>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problema] aggiungi la generazione sourceMap per meno file in modalità sviluppatore
   * _Correzione nota_: il sistema ora genera mappe di origine per un numero inferiore di file in modalità sviluppatore, semplificando l&#39;identificazione dell&#39;origine di uno stile. In precedenza, identificare la sorgente di uno stile era difficile quando si eseguiva il sistema in modalità sviluppatore con compilazione senza lato server.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38982>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: comportamento incoerente nell&#39;ordinamento &quot;esaurito&quot; con soglia minima di stock
   * _Correzione nota_: il sistema ora ordina correttamente i prodotti nel catalogo in base ai livelli di stock, rispettando la soglia minima impostata e spostando in modo coerente gli elementi esauriti nella parte inferiore dell&#39;elenco. In precedenza, il comportamento di ordinamento era incoerente: gli elementi non venivano sempre visualizzati nell’ordine corretto in base ai livelli di stock e le modifiche nell’ordinamento potevano verificarsi in modo imprevedibile dopo il salvataggio, l’aggiornamento o la modifica della gerarchia di categorie.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: suggerimenti per migliorare la segnalazione degli errori per i problemi di caricamento di require.js
   * _Correzione nota_: questa PR migliora il messaggio di errore quando Requjs non riesce a caricare un componente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [Problema] Rimuovi riepilogo revisioni script non necessarie
   * _Correzione nota_: il sistema ora ottimizza il tempo di caricamento delle pagine rimuovendo gli script JavaScript non necessari dalla sezione di valutazione, invece di utilizzare gli stili CSS in linea per un codice più efficiente e leggibile. In precedenza, l’utilizzo di script JavaScript per la sezione di valutazione poteva potenzialmente rallentare il tempo di caricamento delle pagine.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: intestazione sito | Caratteri speciali che interrompono la sezione di benvenuto del cliente
   * _Nota di correzione_: dopo la correzione, i caratteri speciali vengono visualizzati correttamente nella sezione di benvenuto del cliente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

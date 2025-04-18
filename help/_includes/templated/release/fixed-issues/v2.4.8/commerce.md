---
source-git-commit: ae8701cf2486ef0a79c96bd264e16b0e7803a8f6
workflow-type: tm+mt
source-wordcount: '28386'
ht-degree: 0%

---
# Problemi risolti in Adobe Commerce (v2.4.8)

## Problemi risolti nella versione v2.4.8

Sono stati risolti 582 problemi nel codice core di Adobe Commerce 2.4.8. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

* _AC-10042_: /V1/transaction L&#39;API REST restituisce un errore quando parent_txn_id = txn_id
   * _Correzione nota_: il sistema ora gestisce correttamente le transazioni di concetto padre e figlio in cui l&#39;ID della transazione padre è uguale all&#39;ID della transazione, impedendo un ciclo infinito durante la query dell&#39;endpoint REST API /V1/transaction. In precedenza, questo scenario generava un errore irreversibile dovuto al superamento del tempo massimo di esecuzione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] problema di tipo in 2.4.7
   * _Correzione nota_: il sistema ora gestisce correttamente i valori interi nella funzione GetCustomSelectedOptionAttributes durante l&#39;esecuzione di una query GraphQL, evitando errori relativi al tipo. In precedenza, l&#39;avvio di una query GraphQL che utilizzava GetCustomSelectedOptionAttributes con un argomento Integer generava un errore di tipo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: caratteri speciali nella categoria url_key (se creati tramite API REST)
   * _Correzione nota_: in precedenza in category_url_key il carattere speciale non è presente dopo la correzione in quanto mostra il carattere speciale in category_url_key
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35577>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2703_: API REST che mostra gli ordini da un altro sito Web. 
   * _Correzione nota_: il sistema ora supporta l&#39;accesso autorizzato dell&#39;ambito per i token di amministrazione API REST e gli endpoint Magento_Sales, garantendo che l&#39;API REST visualizzi solo gli ordini a cui l&#39;amministratore ha accesso. In precedenza, l’API REST visualizzava gli ordini da tutti i siti web, indipendentemente dal sito web assegnato dall’utente amministratore.
* _ACP2E-2755_: problema con l&#39;api rest dopo l&#39;abilitazione di 2FA Duo
   * _Correzione nota_: 2FA con opzione di sicurezza Duo ora genera la firma corretta per l&#39;API REST
   * _Contributo codice GitHub_: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [REST API]: l&#39;utilizzo del valore predefinito nella vista Store non rimane controllato dopo l&#39;aggiunta di configurazioni per un prodotto configurabile
   * _Correzione nota_: il problema è stato risolto assicurando le voci di database corrette per le opzioni personalizzabili per un archivio non predefinito. La casella di controllo per l’archivio personalizzato nella sezione &quot;admin > Catalog > Product Edit > Customizable Options&quot; (Amministrazione > Catalogo > Modifica prodotto > Opzioni personalizzabili) era stata precedentemente deselezionata a causa di voci di database non accurate, anche se il titolo dell’opzione per l’archivio personalizzato rimaneva lo stesso dell’archivio predefinito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: API REST non è in grado di effettuare richieste con barra (/) nello SKU quando si utilizza Oauth1
   * _Nota sulla correzione_: prima della correzione non era possibile effettuare una chiamata API per un prodotto con &quot;/&quot; nello SKU. Ora è possibile inviare una richiesta API per ottenere i dettagli del prodotto, anche se lo SKU contiene una barra.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: aggiornamento dell&#39;indirizzo del cliente non riuscito durante l&#39;aggiornamento tramite API REST se &quot;validateDefaultAddress&quot; abilitato
   * _Correzione nota_: l&#39;endpoint API funziona ora come previsto dopo che il problema con la chiave ID mancante nel payload API è stato risolto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Cloud] Creazione del gruppo di clienti di prezzo del sito Web duplicato nell&#39;API prezzi di livello.
   * _Nota di correzione_: l&#39;API Rest prezzo ora livello non consente di creare il gruppo di clienti di prezzo gruppo sito Web duplicato.
In precedenza era possibile creare il gruppo di clienti prezzo gruppo sito web duplicato nell’API prezzi livello che non avrebbe superato la convalida in Amministratore durante il salvataggio del prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: impossibile aggiungere il commento dell&#39;ordine con stato tramite API REST
   * _Correzione nota_: il problema è stato risolto consentendo la modifica dello stato dell&#39;ordine se proviene solo dallo stato corrente. In precedenza, non rispettava lo stato dell’ordine e impediva modifiche in qualsiasi stato dell’ordine, anche se proveniva dallo stesso stato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_: l&#39;operazione asincrona non riesce quando manca lo SKU nel payload
   * _Correzione nota_: operazioni asincrone e di sincronizzazione non riuscite in precedenza a causa di errori di salvataggio del prodotto se sku non è presente nel payload. Dopo la correzione, le operazioni dell’API rest di salvataggio del prodotto asincrono e sincrono non riescono e viene visualizzato il messaggio di eccezione pertinente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Impossibile aggiornare i prezzi di base utilizzando l&#39;API REST (il valore di &#39;value_id&#39; in &#39;catalog_product_entity_decimal&#39; non viene incrementato correttamente).
   * _Nota sulla correzione_: in precedenza, quando si chiamava rest api /rest/default/V1/products/base-price, l&#39;ID incremento veniva aumentato erroneamente, lasciando un intervallo tra i valori. Dopo la correzione l’ID incremento viene aumentato come previsto, in modo incrementale. Anche l’intervallo del campo value_id è stato aumentato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: gli elementi dell&#39;ordine non sono visibili nelle e-mail delle note di credito per l&#39;API POST V1/order/:orderId/return
   * _Correzione nota_: in precedenza, prima di questa correzione, quando un cliente crea una nota di credito da una richiesta API di notifica send_email, la griglia dei dettagli del prodotto non era presente. Dopo questa correzione, il cliente invia una richiesta API per la nota di credito e troverà i dettagli dell’elemento del prodotto che compaiono nell’e-mail.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
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

### API, GraphQL, imposta

* _AC-12060_: sia Luma (Rest API) che Graphql non calcolano le imposte quando viene fornito solo il codice postale.
   * _Correzione nota_: il sistema ora calcola correttamente le imposte quando viene fornito solo un codice postale, garantendo stime accurate delle imposte sia per Luma (Rest API) che per GraphQL. In precedenza venivano calcolate solo le stime di spedizione e non venivano incluse le imposte quando veniva fornito solo un codice postale.

### Account

* _AC-10782_: il modulo Indirizzo cliente consente l&#39;utilizzo di codice casuale nei campi del nome
   * _Correzione nota_: il sistema ora convalida l&#39;input nei campi Nome e Cognome nel modulo dell&#39;indirizzo del cliente, impedendo l&#39;utilizzo di codice casuale. In precedenza, il sistema consentiva l’utilizzo di codice casuale in questi campi senza generare un errore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: aggiornamento password amministratore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: arresto anomalo del mio account durante il salvataggio
   * _Correzione nota_: il sistema ora salva correttamente gli indirizzi dei clienti anche quando il campo dell&#39;area non è visualizzato, impedendo un arresto anomalo durante il processo di salvataggio. In precedenza, se si tentava di aggiungere o modificare un indirizzo senza un campo area visualizzato, si verificava un errore di eccezione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38406>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: ciclo di reindirizzamento se l&#39;URL contiene lettere maiuscole
   * _Correzione nota_: il sistema ora converte automaticamente i caratteri maiuscoli negli URL in caratteri minuscoli, impedendo un ciclo di reindirizzamento durante l&#39;accesso alla home page. In precedenza, l’utilizzo di caratteri maiuscoli nell’URL della base sicura causava un ciclo di reindirizzamento continuo quando si tentava di accedere alla home page.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: nome intermedio non salvato per gli account guest
   * _Correzione nota_: il sistema ora salva correttamente il secondo nome per gli account guest durante l&#39;estrazione, rendendolo accessibile nel modello di e-mail. In precedenza, il secondo nome non veniva salvato nella tabella dei preventivi e non era accessibile nel modello di e-mail per gli account guest.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38593>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Amministratore: pulsanti Azioni pagina mobili a sinistra anziché a destra
   * _Correzione nota_: il sistema ora allinea correttamente i pulsanti Azioni pagina al lato destro dell&#39;intestazione fissa nel pannello di amministrazione, migliorando l&#39;aspetto professionale. In precedenza, questi pulsanti si spostavano erroneamente sul lato sinistro dell’intestazione fissa.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: errore `dev:di:info` in magento 2.4.7
   * _Correzione nota_: i parametri del costruttore vengono ora visualizzati correttamente durante l&#39;esecuzione del comando `dev:di:info`, evitando il verificarsi di errori. In precedenza, l’esecuzione di questo comando generava un errore a causa di una mancata corrispondenza del tipo nell’argomento.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: casella di controllo per l&#39;accesso come consenso del cliente non traducibile
   * _Correzione nota_: il sistema ora consente di impostare i campi &quot;Accedi come cliente opt-in casella di controllo&quot; e &quot;Accedi come cliente descrizione comando casella di controllo&quot; nell&#39;ambito &quot;Visualizzazione archivio&quot;, abilitando le traduzioni per diverse visualizzazioni archivio. In precedenza, questi campi venivano impostati solo nell’ambito &quot;Sito web&quot;, impedendo le traduzioni per le singole visualizzazioni dello store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32359>
* _AC-14299_: la home page dell&#39;interfaccia utente front-end nel menu a discesa del mio profilo non è presente.(in modo intermittente)
* _AC-6071_: il cliente ha eseguito l&#39;accesso ma visualizza l&#39;errore 404 in front-end.
   * _Correzione nota_: la pagina della dashboard del cliente storefront ora viene caricata come previsto quando un cliente effettua l&#39;accesso. In precedenza, i clienti potevano accedere, ma questa pagina mostrava un errore 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: impossibile salvare le informazioni sugli attributi del cliente nella sezione del cliente Admin Edit;
   * _Correzione nota_: l&#39;ID archivio del cliente è ora implementato correttamente per ambito sito Web per il modulo di modifica clienti amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_: [Cloud] Non è possibile creare il cliente tramite API quando le vendite private sono abilitate
   * _Correzione nota_: ora è possibile creare il cliente tramite un utente amministratore autenticato e un token di integrazione autenticato tramite API REST quando la restrizione del sito Web è abilitata.
* _ACP2E-3329_: dopo l&#39;accesso, i prodotti aggiunti all&#39;elenco di confronto come utenti guest non sono visibili.
   * _Correzione nota_: i prodotti aggiunti all&#39;elenco di confronto dei prodotti prima dell&#39;accesso come cliente ora vengono mantenuti dopo l&#39;accesso.
In precedenza, dopo l’accesso, i prodotti aggiunti all’elenco di confronto come utenti guest non erano visibili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: la configurazione di Consenti paesi causa problemi nelle configurazioni degli indirizzi dei clienti
   * _Correzione nota_: la selezione della configurazione Consenti paesi non influisce sui paesi mostrati per i quali non è stato specificato l&#39;ambito. Consenti in precedenza la configurazione di Paesi influenzata dall’attributo dell’indirizzo del cliente al di fuori dell’ambito specificato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: il registro degli omaggi condivisi mostra la data dell&#39;evento come 1 giorno prima
   * _Correzione nota_: la data del registro regali è ora visualizzata correttamente in Storefront
* _ACP2E-3501_: VAPT: errore di logica di business - data futura come data di nascita del cliente
   * _Correzione nota_: non è possibile impostare la data di nascita del cliente oltre la data odierna
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

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
* _AC-11427_: [Problema] Etichette non coerenti per gli attributi nelle regole di marketing
   * _Correzione nota_: il sistema ora compila correttamente le etichette in modo coerente per le opzioni categoria e attributo nella regola prezzo carrello
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/31232>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: la convalida dei dati ha esito positivo e il pulsante Importa è presente durante l&#39;importazione di prodotti con il comportamento Sostituisci
   * _Correzione nota_: il sistema ora convalida correttamente i dati e nasconde il pulsante &quot;Importa&quot; durante il processo di importazione del prodotto con il comportamento &quot;Sostituisci&quot;, impedendo qualsiasi sostituzione involontaria dei dati. In precedenza, il sistema convalidava i dati in modo errato e visualizzava il pulsante &quot;Importa&quot;, causando potenziali incongruenze nei dati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Magento 2.4.7 non consente foto di prodotto con estensione maiuscola.
   * _Nota corretta_: il sistema ora accetta caricamenti di immagini di prodotto con estensioni di file in maiuscolo, garantendo un processo di creazione del prodotto fluido. In precedenza, i caricamenti di immagini con estensioni di file in maiuscolo venivano rifiutati, costringendo gli utenti a cambiare l’estensione del file in minuscolo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38831>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: elenco a discesa nascosto nelle griglie con azione di selezione (ad esempio Contenuto > Elementi > Pagine)
   * _Correzione nota_: il sistema è stato corretto in modo simile nell&#39;elenco a discesa di tutte le griglie.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38891>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39371>
* _AC-13131_: [Problema] Correzione Avviso: &quot;filters&quot; chiave di matrice non definita
   * _Correzione nota_: il sistema ora gestisce scenari in cui un nuovo utente non ha ancora interagito con i segnalibri, impedendo la registrazione di un avviso &quot;filters&quot; di chiave array non definita. In precedenza, questo avviso veniva registrato quando un nuovo utente non aveva interagito con i segnalibri.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: il file CSV di importazione prodotti con caratteri speciali non riesce a causa di modifiche al codice nel file Validate.php
   * _Correzione nota_: il sistema ora convalida e importa correttamente i file CSV dei prodotti contenenti caratteri speciali, consentendo il corretto trasferimento dei dati. In precedenza, se si tentava di importare un file CSV di un prodotto con caratteri speciali, si verificava un errore che impediva il processo di importazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: quando il numero massimo di richieste di reimpostazione password è impostato su un valore maggiore di 0. Esempio: 3 , &quot;I messaggi di errore relativi al limite superiore vengono inviati prima del raggiungimento del limite, ovvero dalla seconda volta&quot;
* _AC-13768_: sebbene il numero massimo di richieste di reimpostazione password sia impostato su 0( disattivato) , &quot;i messaggi di errore relativi al limite superiore vengono inviati dalla seconda volta&quot;
* _AC-13850_: nessun asterisco rosso nel campo del numero di telefono obbligatorio
   * _Correzione nota_: l&#39;asterisco rosso precedente non veniva visualizzato per il numero di telefono, ma  numero di telefono obbligatorio. Che è ora un asterisco rosso fisso può essere visto sul numero di telefono come un campo obbligatorio.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c699c206>
* _AC-14300_: in Admin Quando si tenta di riordinare il pulsante di invio dell&#39;ordine non è selezionabile. (in modo intermittente)
* _AC-6975_: [Problema] Imposta la modalità di indicizzazione predefinita su &#39;pianificazione&#39;
   * _Correzione nota_: per impostazione predefinita, tutti i nuovi indicizzatori sono in modalità **[!UICONTROL Update by Schedule]**.  In precedenza, la modalità predefinita era **[!UICONTROL Update on Save]**. Gli indicizzatori esistenti non vengono interessati. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36419>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problema] Eliminare le tabelle del registro modifiche dell&#39;indicizzatore all&#39;annullamento dell&#39;abbonamento a mview
   * _Correzione nota_: il sistema rimuove automaticamente le tabelle del registro modifiche non utilizzate quando un indice viene cambiato da &quot;aggiorna secondo pianificazione&quot; a &quot;aggiorna al salvataggio&quot;, contrassegnando l&#39;indice come non valido per garantire che non vengano perse voci. In precedenza, il passaggio di un indice a &quot;aggiorna al salvataggio&quot; lasciava le tabelle del registro modifiche inutilizzate nel sistema e contrassegnava tutti gli indici modificati come &quot;validi&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29789>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: nessun collegamento alla spedizione durante i pagamenti in pagamento nella visualizzazione per telefono cellulare
   * _Correzione nota_: il sistema ora assicura che i titoli/collegamenti di pagamento &quot;Spedizione&quot; e &quot;Revisione e pagamenti&quot; siano sempre visibili nella parte superiore della pagina nella visualizzazione per dispositivi mobili, consentendo agli utenti di spostarsi facilmente tra i passaggi e apportare le correzioni necessarie. In precedenza, questi titoli/collegamenti erano nascosti nella visualizzazione per dispositivi mobili, rendendo difficile per gli utenti conoscere il passaggio corrente o tornare ai passaggi precedenti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: i commenti di spedizione della query ordini cliente created_at vengono restituiti in un fuso orario +0 non configurato nell&#39;archivio
   * _Correzione nota_: il sistema ora visualizza correttamente il campo &#39;created_at&#39; dai commenti sulla spedizione nel fuso orario configurato del cliente quando si utilizza la query Ordini cliente. In precedenza, il campo &quot;created_at&quot; veniva visualizzato nel fuso orario +0, indipendentemente dal fuso orario configurato del cliente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36947>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrase interrompe l&#39;integrità delle traduzioni
   * _Correggi nota_: il comando `bin/magento i18n:collect-phrases -o` raccoglie e aggiunge correttamente nuove frasi dai file JavaScript e .phtml, garantendo che le traduzioni vengano riflesse correttamente nel file di traduzione. In precedenza, il sistema non era in grado di includere frasi di traduzione multilinea da file JavaScript e frasi da file .phtml nel file di traduzione, il che portava a traduzioni incomplete o errate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_: problema di autorizzazione per l&#39;accesso al blocco dinamico
   * _Correzione nota_: in precedenza, per l&#39;amministratore con restrizioni, l&#39;aggiunta di un nuovo blocco dinamico generava un errore. Dopo aver implementato questa correzione, l’amministratore con restrizioni può aggiungere correttamente il blocco dinamico e modificarlo senza errori
* _ACP2E-2787_: il nome dell&#39;apostrofo nella visualizzazione punto vendita è sostituito da &#39;
   * _Correzione nota_: i filtri di visualizzazione archivio della griglia ora visualizzano correttamente gli apostrofi
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38395>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: il caricamento Favicon non riesce a convalidare i file .ico
   * _Correzione nota_: l&#39;errore di convalida del file è stato aggiornato a &quot;Convalida del file non riuscita. Verifica le impostazioni di elaborazione delle immagini nella configurazione dell&#39;archivio.&quot; In precedenza, si trattava semplicemente di &quot;Convalida file non riuscita&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: nella raccolta di PageBuilder viene visualizzata la miniatura dell&#39;immagine precedente invece dell&#39;immagine appena caricata
   * _Correzione nota_: rigenera anteprime immagini per le immagini eliminate e ricaricate con lo stesso nome tramite la raccolta multimediale nel contenuto del Page Builder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: il salvataggio di un prodotto da parte di un utente amministratore con ambito ruolo diverso sovrascrive/elimina le informazioni di prodotto correlate esistenti nel prodotto
   * _Nota sulla correzione_: in precedenza, prima della correzione, i prodotti correlati venivano reimpostati e diventavano vuoti quando l&#39;utente amministratore secondario faceva clic sul pulsante Salva senza modificare il prodotto correlato. Dopo questa correzione, l’utente amministratore secondario fa clic sul pulsante Salva e il prodotto non viene reimpostato e salvato correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: impossibile esportare più di 200 ordini
   * _Correzione nota_: i limiti del server per la dimensione della richiesta degli ID selezionati inviati in precedenza sono stati ignorati modificando la richiesta HTTP da GET a POST per risolvere il problema. In precedenza, a causa delle limitazioni del server per la dimensione della richiesta GET, si verificava il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: messaggio di convalida pagina di estrazione non corretto.
   * _Correzione nota_: se un campo obbligatorio viene lasciato vuoto, ad esempio &quot;address&quot;, la convalida lato server non visualizzerà il messaggio. La convalida lato client garantirà la visualizzazione della notifica di errore del campo obbligatorio, indicando &quot;Questo campo è obbligatorio&quot;. In precedenza, se un campo obbligatorio veniva lasciato vuoto, veniva visualizzato il messaggio &quot;address is required&quot; (indirizzo richiesto), in aggiunta al messaggio di convalida lato client.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: problema del modello di reimpostazione password con l&#39;utente amministratore
   * _Correzione nota_: il problema è stato risolto utilizzando la chiave corretta, che ora include il nome utente amministratore nel modello e-mail e completa correttamente l&#39;oggetto. In precedenza, il problema derivava da una chiave obsoleta in uso.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: doppie barre nell&#39;URL del segmento cliente
   * _Correzione nota_: le barre doppie non vengono visualizzate nell&#39;URL quando si fa clic su &#39;Reimposta filtro&#39; nella griglia.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: COD non disponibile per i paesi specifici consentiti
   * _Correzione nota_: ora il contante alla consegna è disponibile per i paesi specifici consentiti ogni volta che è necessario e   AC-3216 funziona come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: impossibile aggiornare lo stato dell&#39;ordine creato personalizzato
   * _Correzione nota_: &#39;
Ora è possibile aggiornare gli stati degli ordini creati su misura, mentre in precedenza era possibile modificare lo stato solo se lo stato corrente era &quot;elaborazione&quot; o &quot;frode&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38659>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: lo stato dell&#39;indirizzo di spedizione non viene aggiornato automaticamente
   * _Nota sulla correzione_: prima della correzione, l&#39;area dell&#39;indirizzo di spedizione (o l&#39;ID di regione) non era sincronizzato con le informazioni di fatturazione dell&#39;indirizzo. Ora, sia l&#39;area dell&#39;indirizzo di spedizione che l&#39;ID di regione vengono aggiornati correttamente quando vengono modificate le informazioni sull&#39;indirizzo di fatturazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: il pulsante Reimposta non funziona su Aggiungi/Modifica utente amministratore
   * _Correzione nota_: in precedenza, il pulsante Reimposta non funzionava nella pagina Aggiungi/Modifica utente amministratore. Ora, nel pannello Amministratore in Sistema -> Autorizzazioni -> Tutti gli utenti, il pulsante Reimposta funziona correttamente nella pagina Aggiungi/Modifica utente amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: rilevamento errato e errori CORS dell&#39;URL di amministrazione di Magento
   * _Nota sulla correzione_: dopo la correzione, se il dominio amministratore personalizzato è un sottodominio del dominio principale, l&#39;amministratore è accessibile solo dal sottodominio configurato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37663>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: convalida interrotta per &#39;Quantità massima consentita nel carrello&#39;
   * _Correzione nota_: in precedenza, quando `Maximum Qty Allowed in Shopping Cart` veniva inserito vuoto, non veniva generata alcuna eccezione, ma qui non veniva accettato un valore vuoto. In seguito all’applicazione di questa correzione, se si inserisce una stringa vuota verranno generate delle eccezioni e non sarà possibile salvare il prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema interfaccia utente di anteprima Pagebuilder] I pulsanti nella colonna Page Builder non sono allineati correttamente
   * _Correzione nota_: i pulsanti nelle colonne di Page Builder sono ora allineati correttamente. In precedenza, non erano allineati nelle colonne di Page Builder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: l&#39;esportazione del report Prodotti ordinati non è consentita. Errore 404.
   * _Correzione nota_: il rapporto Prodotti ordinati esportato in formato CSV e XML ora funziona come previsto
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: errore TinyMCE JS nella console dopo l&#39;abilitazione della minimizzazione Js con modalità di produzione
   * _Correzione nota_: in precedenza, l&#39;abilitazione della minimizzazione di JavaScript in modalità di produzione nel pannello di amministrazione causava la visualizzazione degli errori di JavaScript relativi a TinyMCE 6 nella console del browser, influendo sulla funzionalità e sull&#39;esperienza utente. Ora, questo problema è stato risolto, garantendo che TinyMCE 6 funzioni senza errori, anche quando la minimizzazione JS è abilitata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: richiesta di modifiche aggiuntive per completare completamente la correzione ACP2E-3375
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: abilitazione automatica delle nuove autorizzazioni ACL
   * _Correzione nota_: le nuove autorizzazioni aggiunte ai moduli personalizzati non concederanno più automaticamente l&#39;accesso a tutti i ruoli utente esistenti, a meno che non siano configurate in modo esplicito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: il report utente del registro delle azioni amministratore non mostra i dettagli per adminhtml_user_delete
   * _Correzione nota_: adminhtml_user_delete registra correttamente i dettagli importanti. In precedenza, i registri non venivano generati per le eliminazioni degli utenti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: regola carrello con condizione di spedizione non applicabile quando si effettua l&#39;ordine dall&#39;amministratore
   * _Correzione nota_: in precedenza, se la regola del prezzo del carrello aveva uno sconto sul metodo di spedizione con il coupon, non poteva essere applicata tramite l&#39;interfaccia utente di amministrazione. Dopo l’applicazione di questa correzione, lo sconto della regola di prezzo del carrello con un coupon per un metodo di spedizione specifico verrà applicato correttamente dall’interfaccia utente di amministrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [FRESH] il codice HEX non viene aggiornato correttamente in SWATCH
   * _Nota corretta_: il codice HEX immesso manualmente dall&#39;utente nel selettore colore Campione visivo non viene più modificato dal sistema. In precedenza, alcuni codici HEX subivano lievi regolazioni a causa di errori di conversione tra i modelli di colore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Interfaccia utente amministratore, B2B

* _AC-13628_: l&#39;accesso B2B come intestazione del cliente ha ancora il marchio Magento
   * _Correzione nota_: in precedenza nell&#39;intestazione della vetrina veniva visualizzato &quot;Sei connesso come &lt;nome cliente> al &lt;nome negozio>&quot; con il marchio Magento. Che è ora fisso e l’intestazione viene visualizzata con il branding ADOBE.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/96dec499>

### Interfaccia utente amministratore, Catalogo

* _ACP2E-2708_: impossibile modificare le posizioni per i prodotti della categoria nel sito Web consentito come utente amministratore con restrizioni
   * _Nota corretta_: consenti a un utente amministratore con restrizioni di aggiungere e ordinare prodotti in una categoria contenuta nella categoria principale assegnata al sito Web con restrizioni.

### Interfaccia utente amministratore, metodi di pagamento/pagamento, ordine

* _AC-13520_: autorizzazione transazione non visualizzata nella scheda Transazione dopo l&#39;ordine dei pulsanti avanzati PayPal
   * _Correzione nota_: il sistema visualizza ora correttamente l&#39;autorizzazione della transazione nella scheda Transazione dopo che è stato effettuato un ordine utilizzando lo Smart Button PayPal. In precedenza, la transazione di autorizzazione non veniva visualizzata nella scheda Transazione dopo aver fatto clic sul pulsante &quot;Autorizza&quot; e non veniva creata alcuna nuova transazione di tipo &quot;Autorizzazione&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Interfaccia utente amministratore, Prestazioni

* _ACP2E-3169_: dopo l&#39;aggiornamento a 2.4.5-p8 si verificano 500 errori durante la creazione dell&#39;ordine dall&#39;amministratore
   * _Correzione nota_: in precedenza, quando si abilitava la minimizzazione di HTML, non era possibile effettuare un ordine dall&#39;amministratore. Ora, con la minimizzazione di HTML abilitata, l’ordine dall’amministratore può essere effettuato correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Interfaccia utente amministratore, Spedizione

* _ACP2E-2519_: il conteggio dei codici coupon non viene aggiornato in   &quot;Tempo utilizzato&quot; nella scheda Gestisci codici coupon se un ordine viene effettuato con la spedizione multipla.
   * _Correzione nota_: in precedenza, quando un ordine era stato effettuato con spedizione multipla, il conteggio del codice coupon non veniva aggiornato nella colonna &quot;Tempo utilizzato&quot; della scheda Gestisci codici coupon. Ora, il conteggio corretto viene visualizzato in entrambi i &quot;Tempo utilizzato&quot; che riflettono i valori desiderati con la spedizione multipla.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### Interfaccia utente amministratore, staging e anteprima

* _ACP2E-3424_: [Cloud] La rimozione del modello con immagini mancanti determina l&#39;eliminazione di pub/supporti
   * _Correzione nota_: in precedenza, se per un modello di pagebuilder mancava il nome dell&#39;immagine di anteprima, la cartella pub/media veniva eliminata. Dopo la correzione, verranno eliminati solo il modello e l’immagine di anteprima, se trovata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/Generazione rapporti

* _AC-9922_: Errore CSP Google Analytics https://region1.analytics.google.com
   * _Correzione nota_: il sistema ora consente correttamente le connessioni a &#39;https://region1.analytics.google.com&#39; quando Google Analytics è abilitato, evitando errori Content Security Policy (CSP). In precedenza, l’abilitazione di Google Analytics e la visualizzazione del sito web dall’UE generavano errori nella console CSP a causa del rifiuto di connettersi a &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: il report preliminare non funziona
   * _Correzione nota_: il sistema ora supporta la generazione di file di dati di Advanced Reporting per set di dati di dimensioni eccessive caricando e scrivendo report in batch di 10.000. In precedenza, il modulo di reporting avanzato non era in grado di generare file di dati per set di dati di dimensioni eccessive, causando errori di tipo &quot;MySQL Server has gone away&quot; durante l’esecuzione del processo analytics_collect_data cron.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: problema di visibilità dell&#39;intervallo di date del rapporto Prodotti ordinati dall&#39;amministratore.
   * _Correzione nota_: l&#39;utente potrà selezionare una data qualsiasi dal report prodotti ordinati. In precedenza, dopo l’aggiornamento di una tabella, selezionando la data &quot;DA&quot; si reimpostava la data &quot;A&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: intestazioni curl errate che impediscono il funzionamento di `newrelic:create:deploy-marker`
   * _Correzione nota_: il sistema ora formatta correttamente le intestazioni curl, consentendo al comando `newrelic:create:deploy-marker` di creare correttamente un marcatore di distribuzione in New Relic. In precedenza, intestazioni curl errate impedivano la creazione di un marcatore di distribuzione in New Relic.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37641>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
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

### Analytics/Reporting, B2B

* _ACP2E-2300_: B2B - la mappa del sito include prodotti/categorie non assegnati al catalogo condiviso
   * _Correzione nota_: limita le categorie e i prodotti generati da sitemap alle categorie e ai prodotti assegnati solo al catalogo condiviso pubblico e/o all&#39;impostazione delle autorizzazioni per le categorie di catalogo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Reporting, cloud

* _ACP2E-3067_: Magento elimina la maggior parte delle transazioni New Relic cron #34108
   * _Nota corretta_: AC sta segnalando correttamente le transazioni relative al processo cron a NewRelic. In precedenza, alcune transazioni relative a lavori cron venivano indicate come &quot;OtherTransaction/Action/unknown&quot; in NR
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: la metrica in NR potrebbe essere fuorviante per le transazioni in background- Seguito di ACP2E-3067
   * _Correzione nota_: per le transazioni in background (cron) verrà utilizzato il nome dell&#39;app New Relic definito nelle impostazioni di configurazione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: errore del pacchetto Enterprise Edition 2.4.8-beta102 con eccezioni dell&#39;applicazione
* _ACP2E-2139_: i prodotti assegnati al catalogo condiviso non si riflettono sul front-end quando viene eseguito l&#39;indice parziale
   * _Nota sulla correzione_: i prodotti assegnati al catalogo condiviso tramite API REST ora sono immediatamente visibili nella vetrina dopo il completamento dell&#39;indicizzazione parziale. In precedenza, i prodotti erano visibili solo dopo una reindicizzazione completa.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_: [Cloud] La visualizzazione del prezzo nelle versioni mobile e desktop non è la stessa nelle &quot;Mie quotazioni&quot;
   * _Nota di correzione_: la riga Includi imposta non necessaria non viene più visualizzata nel preventivo negoziabile quando viene spesa la sezione del prezzo totale del catalogo.
* _ACP2E-3044_: bordi non necessari nella sezione Ordini personali
   * _Correzione nota_: in precedenza era stato creato un contenitore aggiuntivo (riferimenti ordine) che applicava classi CSS aggiuntive, causando la visualizzazione di linee di bordo non necessarie sotto il numero ordine nella sezione Ordini personali, che ora non è visibile.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: cron sales_clean_quotes elimina i preventivi dagli ordini di acquisto non ancora approvati
   * _Correzione nota_: le offerte utilizzate negli ordini fornitore non verranno eliminate dal processo cron sales_clean_quotes
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: il pulsante Inserisci ordine scompare nei dettagli ordine di acquisto
   * _Correzione nota_: è stato risolto un problema a causa del quale il pulsante Inserisci ordine era nascosto per gli ordini fornitore approvati quando nella scheda era specificato un numero minimo di varianti di prodotto
* _ACP2E-3474_: [CLOUD] Nessuna entità di questo tipo con ID = 0 con modulo b2b
   * _Nota corretta_: l&#39;utente connesso può aggiungere il prodotto al carrello quando le funzioni di Catalogo condiviso sono abilitate.
L’aggiunta precedente del prodotto al carrello causava un errore di tipo &quot;nessuna entità di questo tipo con ID = 0&quot;
* _ACP2E-3562_: non viene visualizzato alcun messaggio di errore per i prodotti di magazzino quando si esegue l&#39;aggiunta in blocco dall&#39;elenco richieste di acquisto
   * _Nota sulla correzione_: prima della correzione veniva visualizzato un messaggio di successo indipendentemente dal numero di prodotti che non era stato possibile aggiungere al carrello. Ora vengono visualizzati messaggi separati per i prodotti aggiunti correttamente al carrello e per i prodotti con errori.
* _ACP2E-3628_: problema con gli aggiornamenti SKU dopo gli aggiornamenti pianificati che causano autorizzazioni prodotto errate (-2 Nega)
   * _Correzione nota_: la modifica della SKU di un prodotto con aggiornamenti pianificati in precedenza non rende più il prodotto inaccessibile ai clienti del catalogo condiviso autorizzati a visualizzare il prodotto.

### B2B, catalogo

* _ACP2E-2860_: prodotti/categorie visibili durante la reindicizzazione quando si utilizzano autorizzazioni NoDDL e Categoria
   * _Correzione nota_: evitare la visualizzazione nelle categorie con restrizioni della vetrina e del relativo contenuto durante l&#39;indicizzazione delle autorizzazioni del catalogo.

### B2B, Framework

* _AC-9607_: Il Filtro Della Griglia Aziendale E Il Tentativo Di Esportazione CSV Della Griglia Non Riusciranno E Genereranno Un&#39;Eccezione
   * _Correzione nota_: il sistema ora consente l&#39;esportazione CSV dei dati della griglia Aziende nel pannello di amministrazione, anche quando vengono applicati filtri come &quot;Saldo in sospeso&quot; e &quot;Tipo di società&quot;. In precedenza, l’applicazione di determinati filtri e il tentativo di esportare i dati della griglia generavano un errore e un’eccezione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### B2B, GraphQL

* _ACP2E-3391_: [Cloud] Impossibile impostare custom_attributes durante la creazione della società tramite chiamata graphql
   * _Correzione nota_: dopo la correzione, è possibile impostare l&#39;attributo &quot;custom_attributes&quot; dell&#39;amministratore della società durante la creazione della società utilizzando la richiesta graphql.

### Braintree

* _AC-14293_: il pulsante Estrazione rapida amministratore è disabilitato.
* _BUNDLE-3367_: pagamento tramite LPM
   * _Correzione nota_: il sistema ora esegue correttamente il rendering dei metodi di pagamento locali (LPM) al caricamento iniziale, anche quando gli indirizzi di spedizione e fatturazione di un cliente connesso non corrispondono, garantendo un processo di pagamento fluido. In precedenza, una mancata corrispondenza tra gli indirizzi di spedizione e di fatturazione di un cliente impediva il rendering di LPM, causando potenziali interruzioni durante il pagamento.
* _BUNDLE-3368_: configurabile con prodotto virtuale come secondario
   * _Correzione nota_: il sistema ora consente metodi di pagamento rapido per prodotti configurabili che hanno un prodotto figlio virtuale, garantendo un processo di pagamento senza problemi. In precedenza, i metodi di pagamento rapido non erano disponibili quando al carrello veniva aggiunto un prodotto configurabile con un prodotto figlio virtuale.
* _BUNDLE-3369_: errore di verifica CVV non riuscita
* _BUNDLE-3370_: archiviazione tramite l&#39;area dell&#39;account problemi 247
   * _Correzione nota_: il sistema ora consente ai clienti di salvare le informazioni relative alla nuova carta o all&#39;account PayPal in più siti Web senza riscontrare errori di autorizzazione. In precedenza, i clienti non erano in grado di salvare nuovi metodi di pagamento tra siti web diversi e ricevevano un messaggio di errore di autorizzazione.
* _BUNDLE-3371_: invia a un indirizzo di un altro paese
   * _Correzione nota_: il sistema ora consente l&#39;elaborazione delle transazioni senza errori durante la spedizione a un indirizzo di un altro paese, garantendo un processo di pagamento senza problemi. In precedenza, il tentativo di spedire un indirizzo da un altro paese generava errori nella console, nonostante non fossero visibili errori nel front-end.
* _BUNDLE-3372_: carta di credito - funzione Teardown
   * _Correzione nota_: il sistema ora gestisce correttamente il ripristino dei componenti di Braintree PayPal quando un cliente torna dalla pagina di pagamento alla pagina di spedizione, evitando errori e assicurandosi che i pulsanti PayPal Express vengano riprodotti correttamente. In precedenza, tornando alla pagina di spedizione dalla pagina di pagamento a volte si verificava un errore durante il tentativo di eliminare i componenti PayPal di Braintree.
* _BUNDLE-3373_: richiamata di spedizione per PayPal Express
   * _Correzione nota_: il sistema ora visualizza correttamente i metodi di spedizione disponibili nel modale PayPal Express, consentendo ai clienti di selezionare il metodo di spedizione preferito prima di passare alla pagina di revisione o completare la transazione. In precedenza, non era disponibile alcun metodo di spedizione da selezionare nel modale PayPal Express, che richiedeva ai clienti di selezionare un metodo di spedizione in una pagina di revisione separata prima di poter completare la transazione.

### Bundle

* _AC-10826_: numero di messaggi di errore di convalida del bundle Storefront maggiore di 1
   * _Correzione nota_: il sistema visualizza ora un solo messaggio di errore di convalida quando si fa clic sul pulsante &quot;Aggiungi al carrello&quot; senza selezionare alcuna opzione di casella di controllo per un prodotto incluso. In precedenza, il sistema visualizzava più messaggi di errore di convalida per ogni casella di controllo non selezionata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: eccezione Magento generata in alcuni test case correlati all&#39;ordine
   * _Correzione nota_: il sistema ora gestisce correttamente il passaggio &#39;sendGuestPaymentInformation&#39; in vari casi di test, impedendo la generazione di eccezioni Magento. In precedenza, queste eccezioni si verificavano a causa di un metodo di pagamento null, causando errori in diversi casi di test.

### Carrello e pagamento

* _AC-10660_: l&#39;eccezione non viene gestita correttamente durante l&#39;aggiunta di un prodotto al carrello nella pagina di confronto dei prodotti
   * _Correzione nota_: il sistema ora gestisce correttamente le eccezioni quando aggiunge un prodotto al carrello dalla pagina di confronto del prodotto, visualizzando un messaggio di gestione dei messaggi nel controller. In precedenza, un’eccezione generava la restituzione di una pagina con codifica JSON invece di essere rilevata e gestita correttamente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38200>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag non invia i prezzi e i totali delle transazioni.
   * _Correzione nota_: il sistema ora invia correttamente i prezzi e i totali delle transazioni a Google Tag quando GTag è abilitato, garantendo il tracciamento accurato dei dati di e-commerce. In precedenza, la valuta veniva erroneamente inviata come parte degli ordini &quot;all&quot;, piuttosto che essere associata al singolo ordine.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37348>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problema] [Pagamento] Direttive dipendenti aggiornate nel modello e-mail di pagamento non riuscito
   * _Correzione nota_: il sistema ora omette correttamente l&#39;indirizzo di spedizione e il metodo di spedizione dal modello e-mail di pagamento non riuscito per i prodotti virtuali, assicurandosi che nell&#39;e-mail vengano incluse solo le informazioni rilevanti. In precedenza, l’e-mail di pagamento non riuscito per i prodotti virtuali includeva erroneamente l’indirizzo di spedizione e il metodo di spedizione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32781>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: l&#39;accesso a Magento 2 durante l&#39;estrazione con il cliente esistente restituisce l&#39;errore della console in Firefox nel browser
   * _Correzione nota_: il sistema ora consente agli utenti di accedere durante il processo di pagamento senza incontrare errori della console nel browser Firefox. In precedenza, se si tentava di accedere come cliente esistente durante il check-out, si verificava un errore della console in Firefox.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38557>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Problema] Regressione delle regole di vendita nella versione 2.4.7
   * _Correzione nota_: il sistema ora convalida correttamente le regole di vendita, impedendo l&#39;applicazione di un codice coupon a un carrello quando la condizione del prodotto non corrisponde ad alcun nome di prodotto. In precedenza, era possibile applicare una regola di vendita e applicare uno sconto sull’importo della spedizione anche quando la condizione del prodotto non corrispondeva a nessun nome di prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38671>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Problema] Calcolo CartFixed della regola di vendita: importo sconto non corretto
   * _Nota sulla correzione_: il sistema ora calcola correttamente l&#39;importo dello sconto per le regole di vendita con importi fissi del carrello, assicurando l&#39;applicazione di sconti precisi indipendentemente dalle modifiche apportate agli articoli del carrello. In precedenza, l’importo dello sconto poteva variare in modo errato quando gli articoli del carrello cambiavano, risultando a volte in sconti notevolmente più grandi del previsto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38694>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problema] Il caricatore blocca i metodi di spedizione dopo la modifica del codice postale e le regole di convalida delle tariffe di spedizione
   * _Correzione nota_: il sistema ora gestisce correttamente i metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione, assicurandosi che il caricatore non blocchi i metodi di spedizione dopo la modifica del codice postale nell&#39;indirizzo di spedizione durante l&#39;estrazione. In precedenza, la modifica del codice postale nell’indirizzo di spedizione durante il pagamento causava il blocco dei metodi di spedizione da parte del caricatore, che non scompariva quando venivano utilizzati metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38742>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: la funzionalità Codice coupon non funziona correttamente nella pagina di pagamento di Magento 2.4.7
   * _Correzione nota_: il sistema ora abilita il campo di input del codice sconto/coupon nella pagina di pagamento per i prodotti virtuali e scaricabili, consentendo agli utenti di applicare i codici sconto come previsto. In precedenza, l’input del codice sconto/coupon veniva disattivato e il testo del titolo del pulsante visualizzato come &quot;Annulla coupon&quot;, impedendo agli utenti di applicare codici sconto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38826>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
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
* _AC-13797_: il prodotto del Registro regali non viene visualizzato correttamente
* _AC-13841_: il prodotto del Registro regali non viene visualizzato correttamente
* _AC-8103_: IVA di traduzione nel modulo di rendering indirizzi
   * _Correzione nota_: il sistema ora consente la traduzione del testo &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nei renderer degli indirizzi, consentendo agli utenti di tradurre questi termini nella lingua specifica del negozio. In precedenza, questi termini non erano traducibili, costringendo gli utenti a utilizzare una soluzione alternativa.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36942>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: ordini duplicati con lo stesso ID preventivo e poche differenze di tempo
   * _Correzione nota_: è stato risolto il problema che si verificava quando i clienti di Adobe Commerce rilevavano ordini duplicati con lo stesso QuoteID
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: carrello permanente cancellato durante il passaggio di pagamento
   * _Correzione nota_: dopo la correzione, la selezione del metodo di pagamento durante l&#39;estrazione senza accesso non interrompe la sessione persistente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: il riordino aggiunge al carrello il prodotto non assegnato
   * _Correzione nota_: in precedenza, per i diversi store, i prodotti potevano essere riordinati dall&#39;altro store. Dopo aver applicato questa correzione solo allo stesso archivio, è possibile riordinare lo stesso prodotto di ambito quando è abilitata la condivisione dei conti cliente
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: in admin, il &quot;carrello&quot; a sinistra non viene aggiornato quando si selezionano gli elementi e il &quot;carrello&quot; a destra
   * _Correzione nota_: il &quot;carrello&quot; a sinistra viene aggiornato quando si selezionano gli articoli e il &quot;passaggio al carrello&quot; a destra nell&#39;amministratore. In precedenza questa funzionalità non funzionava perché gli elementi del carrello trasformati non venivano vuoti dalla sessione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Regola di vendita cloud] non applicata al primo ordine di spedizione multipla
   * _Nota sulla correzione_: dopo la correzione, lo sconto viene visualizzato correttamente per ogni ordine dello stesso preventivo di spedizione multipla.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Cloud] Richieste Parallele Di Produzione Per Aggiungere Lo Stesso Prodotto Al Carrello Risultano In Due Elementi Separati Nell&#39;API REST Carrello
   * _Correzione nota_: il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello tramite l’API REST generava più elementi di riga per lo stesso SKU.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_: problema con l&#39;ordine dal registro regali di Magento 2.4.4 Enterprise/Commerce
   * _Correzione nota_: il problema che impedisce l&#39;acquisto di un prodotto da un registro regali è stato risolto, consentendo l&#39;inserimento di ordini e l&#39;aggiornamento appropriato del registro regali. In precedenza, si verificava un errore durante il tentativo di effettuare un ordine da un registro regali, che impediva il completamento dell&#39;acquisto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_: impossibile inviare il cookie. Dimensione dei &#39;messaggi-immagine&#39; durante il tentativo di riordinare
   * _Correzione nota_: il processo di riordinamento non genererà più i propri errori. Si baserà sull&#39;elenco del carrello assegni articoli incorporati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: l&#39;indirizzo di spedizione predefinito non è selezionato al momento dell&#39;estrazione
   * _Correzione nota_: l&#39;evento di selezione dell&#39;indirizzo di spedizione predefinito è in corso nel contesto della ricerca degli indirizzi abilitata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [Problema API addProductsToCart graphql di CLOUD] con opzione personalizzata
   * _Correzione nota_: GraphQL aggiunge correttamente al carrello lo stesso prodotto con opzioni personalizzate diverse
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_: [Cloud] Le regole dei prodotti correlati non funzionano quando si modifica la visualizzazione archivio
   * _Correzione nota_: il problema è stato risolto confermando che il valore della proprietà personalizzata è stato ricevuto correttamente nella pagina del carrello. In precedenza, non veniva recuperato correttamente quando si cambiava negozio nella pagina del carrello della vetrina.
* _ACP2E-2923_: più indirizzi aggiunti all&#39;account al momento dell&#39;estrazione come nuovo cliente
   * _Correzione nota_: il sistema ora salva un nuovo indirizzo del cliente una sola volta se l&#39;ordine non è stato creato, impedendo la creazione di più indirizzi identici in caso di errori di inserimento dell&#39;ordine. In precedenza, il sistema salvava un nuovo indirizzo ogni volta che veniva effettuato un tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine fosse stato creato correttamente o meno.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: il riordinamento dell&#39;ordine cliente tramite il modulo d&#39;ordine ospite genera un carrello vuoto
   * _Correzione nota_: in precedenza, quando si effettuava un riordino tramite la pagina Ordini e restituzioni, il cliente veniva reindirizzato alla pagina di accesso. Dopo l’applicazione di questa correzione, il cliente registrato viene reindirizzato correttamente alla pagina Visualizza carrello al momento del riordino. Il flusso funziona come i clienti guest.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: l&#39;utente amministratore con risorse ruolo limitate non è in grado di visualizzare i carrelli acquisti
   * _Correzione nota_: in precedenza, l&#39;amministratore con restrizioni non poteva visualizzare il carrello abbandonato dal pannello di amministrazione per un sito Web associato. Dopo aver applicato questa correzione, l’amministratore con restrizioni può visualizzare il carrello abbandonato dal pannello di amministrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
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
* _ACP2E-3415_: la persistenza del carrello non viene rispettata alla disconnessione
   * _Correzione nota_: aggiunta della funzionalità Memorizza utente mancante dall&#39;accesso del cliente alla finestra a comparsa per l&#39;autenticazione e l&#39;accesso alle estrazioni.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: i dati delle virgolette esistenti non sono aggiornati/non visibili, ma crea un nuovo record delle virgolette quando trigger_recollect = 1
   * _Nota corretta_: gli elementi del carrello del cliente non scompaiono più a causa dell&#39;eliminazione di un prodotto dopo che è stato aggiunto al carrello.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_: quando si acquista un articolo del Registro di sistema relativo a regali, il cliente visualizza gli articoli non presenti nel Registro di sistema
   * _Correzione nota_: l&#39;aggiornamento del Registro di sistema per i regali non include più elementi che non appartengono al Registro di sistema per i regali.
* _ACP2E-3510_: [Cloud] problema con il popup di conferma &quot;Rimuovi tutto&quot; Rimozione degli elementi dal carrello senza conferma
   * _Correzione nota_: ora facendo clic sul pulsante &quot;Rimuovi tutto&quot; per i prodotti per i quali è richiesta l&#39;attenzione, viene visualizzata una finestra a comparsa di conferma per assicurarsi che gli elementi vengano rimossi solo con la conferma. In precedenza, gli elementi venivano rimossi immediatamente senza alcuna conferma
* _ACP2E-3618_: [CLOUD] Riordina la funzionalità del pulsante
   * _Correggi nota_: riordinando un ordine dall&#39;area di amministrazione, verranno aggiunti al preventivo prodotti con scorte anche se nell&#39;ordine originale sono presenti alcuni prodotti che non dispongono più di scorte. Prima della correzione non veniva aggiunto alcun prodotto al nuovo preventivo se il prodotto senza scorte era nell’ordine originale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: gli archivi ricerche non funzionano per codice postale
   * _Correzione nota_: la ricerca delle posizioni di prelievo per codice postale non funzionava correttamente per le localizzazioni olandesi. Dopo la correzione, la ricerca della posizione di prelievo fornirà risultati in base al codice postale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/344fce23>

### Carrello e pagamento, Pagamento/ Pagamento di una pagina

* _AC-9386_: [BUG casuale] Il campo E-mail non viene visualizzato o richiede molto tempo nella pagina Pagamento o spedizione pagamento
   * _Correzione nota_: Commerce ora esegue il rendering del campo **[!UICONTROL Email]** nelle pagine di pagamento e spedizione di pagamento di pagamento come previsto. In precedenza, questo campo era assente o visualizzato lentamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/e1babcfd>

### Carrello e pagamento, ordine

* _ACP2E-3097_: Datepicker per prodotto con più opzioni personalizzabili con campi data non funzionanti quando si effettua l&#39;ordine dall&#39;amministratore
   * _Nota sulla correzione_: il sistema ora visualizza correttamente il selettore data per tutti i campi della data durante la configurazione di un prodotto con più opzioni di data personalizzabili nel processo di creazione dell&#39;ordine di amministrazione. In precedenza, il selettore data veniva visualizzato solo per il primo campo data, lasciando i campi rimanenti senza un selettore data.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Carrello e pagamento, spedizione

* _AC-12119_: acquisto immediato &quot;spedizione più economica&quot; interrotto per prodotti configurabili
   * _Correzione nota_: la funzione Acquisto immediato ha selezionato erroneamente l&#39;opzione di consegna in-store più costosa per i prodotti configurabili anziché il metodo più economico. Questa correzione assicura che venga scelto il metodo di spedizione corretto in base al prezzo effettivo.&quot;
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38811>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogo

* _AC-10910_: la pulizia della tabella del database cron_schedule non esegue la pulizia dei processi non esistenti
   * _Correzione nota_: il sistema ora ripulisce automaticamente la tabella del database cron_schedule, rimuovendo le voci per i processi che non esistono più nel sistema. In questo modo è possibile garantire prestazioni ottimali mantenendo un numero minimo di righe nella tabella. In precedenza, le voci per i processi da moduli inattivi o rimossi non venivano pulite, generando un’inutile accumulazione di dati nella tabella cron_schedule.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38217>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: il prezzo di livello non verrà eliminato dal prodotto configurabile
   * _Correzione nota_: il sistema ora rimuove correttamente il prezzo di livello di un prodotto quando viene convertito da prodotto semplice a prodotto configurabile, garantendo una corretta visualizzazione del prezzo sul front-end. In precedenza, il prezzo di livello di un prodotto configurabile non veniva eliminato quando un prodotto veniva convertito da prodotto semplice a prodotto configurabile, determinando una mancata corrispondenza nel prezzo visualizzato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38390>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: la descrizione della categoria WYSIWYG è vuota in una visualizzazione archivio non predefinita
   * _Correzione nota_: il sistema ora salva e visualizza correttamente la descrizione della categoria nell&#39;editor di WYSIWYG quando modifica una categoria a livello di visualizzazione archivio. In precedenza, l’editor WYSIWYG risultava vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38622>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38623>
* _AC-11970_: impossibile riordinare i prodotti configurabili con una casella di controllo selezionata come opzione personalizzata
   * _Correzione nota_: il sistema ora elabora correttamente il riordino dei prodotti configurabili con una singola opzione personalizzata di casella di controllo selezionata, consentendo la corretta creazione del carrello. In precedenza, il tentativo di riordinare tali prodotti causava un errore e impediva l’aggiunta degli articoli al carrello.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38736>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_: [Problema] Correzione del testo dell&#39;elemento filtro nella navigazione a livelli
   * _Correzione nota_: il sistema ora utilizza correttamente le parole &quot;item&quot; e &quot;items&quot; nell&#39;elemento del filtro di navigazione con livelli, migliorando la chiarezza e la precisione delle descrizioni del filtro. In precedenza, queste parole venivano utilizzate in modo errato, generando potenziale confusione per gli utenti che navigavano nelle opzioni del filtro.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: il formato di data e ora per l&#39;opzione personalizzata non funziona
   * _Correzione nota_: il sistema ora applica correttamente il formato data configurato alle opzioni personalizzate del prodotto di tipo Data, garantendo che il formato data venga visualizzato correttamente nel front-end. In precedenza, le modifiche alla configurazione del formato della data non venivano applicate al front-end per le opzioni personalizzate del prodotto di tipo Data.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38925>
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
* _AC-13622_: [Problema] Layout del prodotto basato su attribute_set
   * _Correzione nota_: il sistema ora consente la regolazione del layout del prodotto in base al set di attributi, fornendo un modo più pratico ed efficiente per gestire la visualizzazione del prodotto nell&#39;archivio front-end. In precedenza, il layout poteva essere regolato solo per SKU o per tipi di prodotto, il che non era sempre pratico per molti prodotti o articoli specifici.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38790>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: chiave univoca mancante nella tabella eav_attribute_option_value
   * _Correzione nota_: il sistema ora include una chiave univoca nelle colonne &#39;option_id&#39; e &#39;store_id&#39; nella tabella &#39;eav_attribute_option_value&#39;, impedendo la possibilità che un&#39;opzione abbia più valori per la stessa visualizzazione archivio. In precedenza, un codice errato poteva causare la presenza di più valori per la stessa visualizzazione archivio, causando problemi durante la modifica di prodotti o attributi.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/24718>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problema] Utilizza la classe di visibilità per l&#39;indicizzatore di prodotti di categoria, anziché valori hardcoded
   * _Correzione nota_: il sistema ora utilizza la classe di visibilità per l&#39;indicizzatore del prodotto della categoria invece dei valori hardcoded, migliorando la modularità. In precedenza, venivano utilizzati valori hardcoded nell’indicizzatore dei prodotti per categoria, limitando la flessibilità e l’adattabilità.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37200>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: il codice valuta non viene modificato nel widget Nuovo prodotto
   * _Correzione nota_: il sistema ora aggiorna correttamente il codice valuta nel widget Nuovo prodotto quando la valuta viene modificata nel front-end, garantendo la coerenza nella visualizzazione della valuta in tutto il sito. In precedenza, la modifica della valuta nel front-end non influenzava il codice di valuta visualizzato nel widget Nuovo prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37898>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: il prezzo normale non viene visualizzato nel PLP per il prodotto configurabile
   * _Nota sulla correzione_: il prezzo normale viene ora visualizzato nelle pagine dell&#39;elenco dei prodotti per i prodotti configurabili con prodotti secondari con prezzo speciale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: le informazioni sul magazzino non vengono visualizzate correttamente nella griglia di merchandising visivo
   * _Correzione nota_: il materiale è ora visualizzato in base all&#39;archivio selezionato.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: il contenuto del widget non viene aggiornato nella pagina cms
   * _Correzione nota_: il sistema ora aggiorna il contenuto del widget in una pagina di CMS quando un prodotto viene impostato come nuovo e salvato, assicurandosi che nella pagina venga visualizzata la raccolta di prodotti aggiornata. In precedenza, la pagina non veniva aggiornata per mostrare il nuovo prodotto a causa di identità di cache non corrette utilizzate per il widget nella cache.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: problemi relativi al salvataggio dei prezzi avanzati sui prodotti bundle
   * _Correzione nota_: miglioramento delle prestazioni di risparmio prodotto nel bundle.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [Il processo di reindicizzazione on-premise] non è efficiente durante la creazione delle regole di prezzo catalogo
   * _Correzione nota_: il salvataggio della regola del prezzo di catalogo non invaliderà gli indicizzatori, ma reindicizzerà solo i prodotti interessati
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: aggiornamento degli attributi di prodotto di tipo Data e Ora tramite importazione CSV
   * _Correzione nota_: ora gli attributi datetime avranno una parte temporale nei dati esportati. Sarà inoltre possibile aggiornare l’ora per tali attributi utilizzando l’importazione. Inoltre, se è abilitata l&#39;opzione &quot;Raccoglimento campi&quot;, i valori degli attributi nella colonna &quot;additional_attributes&quot; saranno racchiusi tra virgolette doppie.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38306>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: nessun messaggio di errore appropriato quando l&#39;ID del sito Web è errato nella richiesta
   * _Correzione nota_: ora è stato aggiunto il messaggio di errore appropriato da visualizzare quando l&#39;ID del sito Web nella richiesta non è corretto. In precedenza non vi era alcuna convalida quando l’ID del sito web nella richiesta era errato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: l&#39;immagine del prodotto viene persa dopo l&#39;eliminazione di un aggiornamento pianificato esistente che non influisce sull&#39;immagine
   * _Correzione nota_: le immagini del prodotto non vengono rimosse durante l&#39;eliminazione dell&#39;aggiornamento di staging.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Prezzo del prodotto del bundle errato se utilizzato con i prezzi dei livelli
   * _Correzione nota_: in precedenza, quando si calcolavano determinati sconti percentuali arrotondati a 2 punti decimali, venivano generati prezzi finali diversi per il carrello e la pagina dei dettagli della pagina di elenco prodotti/prodotti. Dopo l’applicazione di questa correzione, il prezzo finale per il prodotto bundle è lo stesso della pagina dei dettagli del prodotto, della pagina di elenco dei prodotti e della pagina del mini carrello.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38091>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: la regola delle promozioni del catalogo non funziona con l&#39;attributo quantity_and_stock_status
   * _Correzione nota_: l&#39;attributo quantity_and_stock_status verrà ora preso in considerazione dalla regola di promozione del catalogo, che non era stata presa in considerazione in precedenza durante la generazione di un nuovo prodotto dal lato amministratore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35627>
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: i valori della colonna update_at dell&#39;entità prodotto non vengono aggiornati durante l&#39;aggiornamento del prezzo tramite API REST
   * _Nota corretta_: la colonna &quot;ultimo aggiornamento alle&quot; del prodotto da parte dell&#39;amministratore viene aggiornata alla data e all&#39;ora corrette durante l&#39;aggiornamento dei prodotti esistenti tramite l&#39;API REST. In precedenza, la colonna &quot;Ultimo aggiornamento alle&quot; non veniva aggiornata correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: è possibile impostare valori non univoci tramite l&#39;importazione del prodotto
   * _Correzione nota_: il sistema ora applica correttamente il vincolo del valore univoco per gli attributi di prodotto univoci durante l&#39;importazione del prodotto, impedendo la presenza di valori duplicati per tale attributo. In precedenza, era possibile impostare valori non univoci per gli attributi del prodotto configurati per avere valori univoci tramite l’importazione del prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38445>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: i prodotti sul front-end utilizzano dati specifici dell&#39;archivio quando è abilitata la modalità Archivio singolo
   * _Correzione nota_: in precedenza, quando si abilitava la modalità archivio singolo per la visualizzazione archivio predefinita, le modifiche non venivano migrate nell&#39;ambito a livello di sito Web. Dopo l’applicazione di questa correzione, quando abilitiamo la modalità archivio singolo, i dati predefiniti della visualizzazione archivio verranno sincronizzati con i dati specifici a livello di sito web e risolveranno i possibili conflitti per prodotti e categorie.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: impossibile impostare l&#39;opzione di ordinamento predefinita in una categoria utilizzando l&#39;API rest
   * _Correzione nota_: aggiornamento corretto di default_sort_by in una categoria tramite richiesta REST/SOAP APi
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] Il commerciante sta riscontrando problemi con il numero di lista dei desideri
   * _Correzione nota_: l&#39;aggiunta di un prodotto alla lista dei desideri in un negozio non aumenta più il numero di elenchi dei desideri in altri negozi aperti nello stesso browser. In precedenza, se entrambi gli store fossero caricati nello stesso browser, il numero di lista dei desideri aumenterebbe anche nell’altro store.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: la pagina Categoria sul front-end mostra gli slot vuoti quando si utilizza un prodotto bundle
   * _Nota corretta_: i prodotti del bundle non vendibili nel contesto dell&#39;archivio corrente non sono più indicizzati.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_: [CHIARIMENTO] Problemi relativi alla tabella della sequenza di prodotti del bundle
   * _Nota corretta_: i record nelle tabelle delle sequenze di prodotti del bundle (sequence_product_bundle_option, sequence_product_bundle_selection) vengono ora rimossi quando il prodotto del bundle viene eliminato o le opzioni di prodotto del bundle vengono eliminate.
In precedenza, i record nelle tabelle della sequenza di prodotti Bundle non venivano rimossi.
* _ACP2E-2905_: [Cloud] problema di preventivo nell&#39;architettura multisito
   * _Correzione nota_: in precedenza, l&#39;architettura di più siti Web con valute e gruppi di clienti diversi non era in grado di applicare correttamente gli sconti allo store. Dopo l’implementazione di questa correzione, l’architettura multi-sito con diversi sconti sui prezzi del gruppo di clienti verrà applicata con successo ai diversi store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38506>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 TipoErrore non rilevato: dataRecord.slice durante la modifica di prodotti bundle
   * _Correzione nota_: nessun errore JavaScript nella console del browser durante l&#39;eliminazione dell&#39;opzione dal prodotto del bundle.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38505>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Prezzo errato del prodotto del bundle nella conferma dell&#39;ordine
   * _Nota di correzione_: viene visualizzato l&#39;importo corretto per le opzioni del bundle in ordine su Storefront quando è stata utilizzata una valuta diversa da quella di base.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: bug nell&#39;aggiunta di video YouTube
   * _Correzione nota_: le immagini e i video dei prodotti sono configurati nell&#39;ambito globale. Poiché non è possibile avere un video di prodotto in un ambito e non in un altro, l’impostazione della chiave API di Youtube è stata impostata su ambito globale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Aggiornamento URL cloud] solo per store_id=0
   * _Correzione nota_: il &quot;percorso URL&quot; è ora archiviato con l&#39;ID archivio corretto. In precedenza, l’ID archivio era errato e durante lo spostamento delle categorie continuavano a rimanere nel database percorsi URL errati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all eseguito e creato un errore.
   * _Correzione nota_: i dati di collegamento del prodotto errati nelle chiamate API REST non causano più errori critici.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Problema cloud] Problema mobile Impossibile solo pizzicare l&#39;immagine PDP
   * _Correzione nota_: il sistema ora supporta la funzionalità di zoom e pizzicamento sulle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili in Chrome, migliorando l&#39;esperienza di utilizzo mobile. In precedenza, il doppio tocco sull’immagine nella visualizzazione per dispositivi mobili su Chrome non consentiva di ingrandire l’immagine come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: etichetta mancante in LayeredNavigation con nome opzione 0
   * _Correzione nota_: il problema è stato risolto saltando una verifica del valore vuoto per il valore di attributo 0. In precedenza, veniva considerata vuota e causava il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: i clienti visualizzano i prezzi di altri gruppi di clienti
   * _Correzione nota_: è stato corretto un problema a causa del quale le informazioni relative al gruppo di clienti venivano salvate in un segmento errato a causa del valore precedente di X-Magento-Vary nella richiesta
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: errore durante l&#39;eliminazione delle opzioni del bundle
   * _Correzione nota_: il sistema ora elimina correttamente le opzioni del bundle senza attivare un errore o causando la mancata risposta della pagina. In precedenza, se si tentava di eliminare le opzioni del bundle, si verificava un errore &quot;Page Unresponsive&quot; (Non risponde pagina) e si impediva il salvataggio del prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_: problema di browser con autorizzazioni per categorie esaurite
   * _Nota corretta_: l&#39;interfaccia utente delle autorizzazioni per le categorie è stata riprogettata per consentire il rendering di una grande quantità di autorizzazioni utilizzando il componente dell&#39;interfaccia utente predefinito e l&#39;impaginazione. In precedenza, le autorizzazioni per la categoria causavano l’arresto anomalo del browser con una grande quantità di autorizzazioni assegnate alla categoria.
* _ACP2E-3100_: [Il file di immagine Cloud] non esiste nel registro errori di New Relic
   * _Correzione nota_: il sistema ora sincronizza le immagini segnaposto personalizzate con l&#39;archiviazione locale, assicurandosi che vengano riprodotte correttamente quando si utilizza l&#39;archiviazione remota, ad esempio AWS S3. In precedenza, il rendering delle immagini segnaposto personalizzate non riusciva quando si utilizzava l’archiviazione remota, causando una visualizzazione delle immagini interrotta e registri di errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: il feed RSS dei nuovi prodotti non viene aggiornato con i nuovi prodotti a causa della cache
   * _Nota sulla correzione_: il feed Rss per i nuovi prodotti viene aggiornato quando un prodotto viene impostato come nuovo e salvato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: [Cloud] La risposta GQL di Product Media Gallery non è ordinata in base alla posizione dell&#39;immagine
   * _Correzione nota_: il sistema ora ordina correttamente gli elementi nella raccolta multimediale in base alla posizione nella risposta di GraphQL, garantendo un ordine di visualizzazione accurato. In precedenza, gli elementi nella raccolta multimediale non venivano ordinati in base alla posizione, causando un ordine di visualizzazione errato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Gli elementi della sottocategoria Cloud] non vengono visualizzati nella modifica dei widget sul backend di amministrazione
   * _Correzione nota_: la struttura delle categorie nella nuova pagina widget non deve più presentare problemi durante il caricamento delle categorie di livello 5+. In precedenza, mancavano alcune categorie durante il caricamento della struttura oltre le categorie di livello 5.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
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
* _ACP2E-3513_: [CLOUD] Il prezzo speciale non viene visualizzato nel prodotto configurabile
   * _Nota sulla correzione_: dopo la correzione, la modifica del valore &quot;Usato nell&#39;elenco dei prodotti&quot; per l&#39;attributo di prezzo speciale non influisce sulla visualizzazione del prezzo speciale per i prodotti configurabili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: le tabelle temporanee degli indicizzatori non vengono pulite se il processo viene terminato
   * _Nota corretta_: le tabelle temporanee dell&#39;indicizzatore CatalogRule vengono ora pulite se il processo di indicizzazione viene terminato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] errori di unit test di base in 2.4.7-p3
   * _Nota sulla correzione_: le note sulla versione per questo test non sono necessarie perché si tratta di un miglioramento di unit test.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: problema di prestazioni nel recupero della quantità di magazzino per i prodotti raggruppati con più origini
   * _Nota sulla correzione_: la pagina di modifica di prodotto raggruppato e bundle è ora ottimizzata quando i prodotti assegnati hanno un numero elevato di sorgenti di inventario.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Correzione https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Correzione nota_: prestazioni migliorate della pagina categoria amministratore in caso di numero elevato di categorie di ancoraggio
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

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

### Catalogo, Framework

* _AC-9111_: Recupero ordine (Spedizioni|Creditmemos|Fattura)Raccolta - Non caricare la raccolta
   * _Correzione nota_: il sistema ora assicura che le raccolte per le spedizioni e le note di accredito non vengano precaricate quando vengono recuperate da un ordine, consentendo l&#39;applicazione di filtri o ordini aggiuntivi a tali raccolte. In precedenza, queste raccolte venivano caricate automaticamente, impedendo ulteriori modifiche.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37561>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [Cloud]Completamento: mancata corrispondenza in Confronto dati durante la verifica della presenza di modifiche nei dati
   * _Correzione nota_: in precedenza, l&#39;oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica ai dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Inoltre, non controlla i numeri mobili incapsulati da stringa. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Catalogo, GraphQL

* _ACP2E-3090_: gestione dei filtri delle categorie in GraphQL: includeDirectChildrenOnly e category_uid
   * _Correzione nota_: vengono recuperate solo le categorie figlio dirette mentre si filtra per category_uid.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [L&#39;ordinamento del prodotto Graphql cloud] non funziona
   * _Nota corretta_: l&#39;ordinamento dei prodotti GraphQl per più campi quando i campi vengono passati nelle variabili ora funziona come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: i prezzi di livello restituiscono un valore errato nei prodotti GraphQL (rispetto a Storefront)
   * _Nota sulla correzione_: dopo la correzione, i prezzi del livello del prodotto restituiti per le richieste graphql hanno prezzo per un elemento.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: problema di categoria tramite GraphQL
   * _Correzione nota_: dopo la correzione, la query graphql delle categorie restituisce le categorie con l&#39;autorizzazione Consenti anche se la categoria principale non dispone dell&#39;autorizzazione Consentita.

### Catalogo, prezzi, staging e anteprima

* _ACP2E-2672_: [Cloud] L&#39;endpoint API a prezzo speciale restituisce un errore quando si aggiornano contemporaneamente numerosi prodotti
   * _Correzione nota_: ora l&#39;API di aggiornamento in blocco del prezzo speciale creerà una singola campagna per ogni intervallo di date invece di più aggiornamenti pianificati per ogni prodotto e intervallo di date. Inoltre, supporterà le richieste API simultanee per un’elaborazione più rapida di un gran numero di SKU.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>

### Catalogo, prodotto

* _AC-7050_: la struttura di selezione delle categorie in Modifica prodotto non è nello stesso ordine impostato in Catalogo->Categorie
   * _Correzione nota_: il sistema ora visualizza correttamente la struttura di selezione delle categorie nella sezione di modifica dei prodotti nello stesso ordine impostato in Catalogo->Categorie, semplificando l&#39;amministrazione dei prodotti nei cataloghi di grandi dimensioni. In precedenza, la struttura ad albero delle categorie nella sezione di modifica del prodotto veniva visualizzata in ordine di creazione delle categorie, indipendentemente dall’ordine di visualizzazione impostato in Catalogo->Categorie.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catalogo, SEO

* _ACP2E-3653_: URL canonico non corretto per la categoria quando pagina > 1
   * _Correzione nota_: in precedenza, l&#39;URL canonico per il contenuto di più pagine non funzionava correttamente, visualizzando in modo coerente l&#39;URL di base. Tuttavia, dopo l’implementazione della correzione, l’URL canonico per i contenuti con più pagine ora visualizza correttamente l’URL con l’ID pagina.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Catalogo, Ricerca

* _ACP2E-2757_: i prodotti non vengono visualizzati nella categoria e nella ricerca, ma i collegamenti diretti funzionano
   * _Correzione nota_: in precedenza, l&#39;attributo personalizzato Sì/No con price_* attribute_code non funzionava con l&#39;indicizzazione. Dopo questa correzione, l’attributo personalizzato Sì/No funziona come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Errore di ricerca elastica in alcune pagine categoria
   * _Correzione nota_: in precedenza, con il ticket di configurazione indicato, quando si inseriva il prezzo 0 per più prodotti, veniva generata un&#39;eccezione nella pagina della categoria front-end. Dopo che questa correzione è stata applicata quando più prezzi del prodotto 0 e la pagina della categoria viene caricata in front-end, non viene generata alcuna eccezione e la pagina della categoria viene caricata correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: errore di tipo durante la creazione dell&#39;oggetto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Nota sulla correzione_: dopo la correzione, è possibile creare un&#39;istanza della classe Magento\CatalogSearch\Model\Indexer\Fulltext senza specificare $data.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [Il problema di CLOUD] con i prodotti non è visibile in Frontend dopo il salvataggio in Magento Admin
   * _Correzione nota_: dopo la correzione, i prodotti configurabili con prodotti secondari con nomi lunghi non verranno persi nella vetrina.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogo, spedizione

* _ACP2E-3195_: indirizzo di spedizione vuoto durante l&#39;invio di un ordine per un articolo del Registro di sistema relativo a regali
   * _Correzione nota_: in precedenza, per gli elementi del registro regali degli utenti ospiti, quando venivano restituiti dalla funzione e-mail, veniva generato un indirizzo vuoto, che non era corretto per l&#39;ordine. Dopo l&#39;applicazione di questa correzione, il Registro di sistema per i regali controlla gli utenti connessi/ospiti e gli indirizzi assegnati, se presenti.

### Cloud

* _ACP2E-3010_: [Cloud] PHPSESSID sta modificando ogni richiesta POST
   * _Correzione nota_: PHPSESSID non viene più rigenerato nelle richieste POST nell&#39;area front-end per un cliente connesso se la cache L2 Redis è abilitata e il cliente è stato aggiornato dal back-end
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Avvisi di generazione sitemap
   * _Correzione nota_: dopo la correzione, la mappa del sito viene generata nella directory tmp del sistema e copiata nella destinazione finale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

### Contenuto

* _AC-10539_: [Problema] relativo alla visualizzazione del prezzo nel widget Visualizzato di recente
   * _Correzione nota_: il sistema ora visualizza correttamente il prezzo dei prodotti semplici esauriti nel widget &quot;Prodotto visualizzato di recente&quot;, garantendo la coerenza tra tutti i widget e le pagine dell&#39;elenco di prodotti. In precedenza, il prezzo dei prodotti semplici esauriti non veniva visualizzato nel widget &quot;Prodotto visualizzato di recente&quot; a causa di una condizione nei modelli di caricamento del prezzo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38167>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problema] Digitare e grammatica corretti nel file acl.xsd
   * _Correzione nota_: il sistema ora corregge un errore di battitura e grammatica nel file acl.xsd, migliorando la chiarezza e l&#39;accuratezza della documentazione. In precedenza, il file acl.xsd conteneva un errore ortografico e grammaticale non corretto che poteva causare confusione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38061>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: immagine del banner Pagebuilder non visibile nella raccolta
   * _Correzione nota_: il sistema ora visualizza correttamente le immagini del banner caricate nelle cartelle appena create nella raccolta Pagebuilder, eliminando gli errori della console precedente. Prima di questa correzione, le immagini del banner non erano visibili nella raccolta se venivano caricate in una nuova cartella, causando un errore nella console.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Prefisso non impostato&quot; dopo l&#39;aggiornamento a 2.4.5-p8
   * _Correzione nota_: il sistema ora completa correttamente il processo di distribuzione del contenuto statico quando il modulo Magento_CSP è abilitato e &quot;dev/js/translate_strategy&quot; è impostato su &quot;embedded&quot;, senza attivare l&#39;errore &quot;indicativo di località non impostato&quot;. In precedenza, in queste condizioni, il processo di distribuzione del contenuto statico non riusciva e veniva visualizzato un errore di tipo &quot;Codice di area non impostato&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38845>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38922>
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
* _AC-9638_: [Problema] relativo al caricamento di file nell&#39;editor di WYSIWYG nella pagina del prodotto
   * _Correzione nota_: la struttura delle cartelle viene ora visualizzata correttamente e nell&#39;editor di WYSIWYG è possibile caricare le immagini nella pagina del prodotto, anche dopo l&#39;espansione della scheda &#39;Immagini e video&#39;. In precedenza, l’espansione della scheda &quot;Immagini e video&quot; causava prima la mancata visualizzazione della struttura delle cartelle e un messaggio di errore durante il caricamento di un’immagine nell’editor di WYSIWYG.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] problema blocco dinamico
   * _Correzione nota_: il rendering dei widget è ora eseguito correttamente all&#39;interno di blocchi dinamici.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_: l&#39;URL nocookie di YouTube non funziona in Page Builder
   * _Correzione nota_: ora il generatore di pagine consente l&#39;URL senza cookie di youtube nelle impostazioni degli elementi modulo delle regole di convalida. In precedenza, l’URL youtube senza cookie non funzionava in pagebuilder.
* _ACP2E-2693_: [Cloud] Il front-end non viene caricato a causa di un problema nel modello di newsletter
   * _Correzione nota_: l&#39;aggiunta di blocchi tramite la sezione del contenuto di una pagina CMS non genera più un&#39;eccezione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Eccezione di analisi trovata nel registro: InvalidArgumentException: la classe non esiste in vendor/magento/module-rule/Model/ConditionFactory.php
   * _Correzione nota_: la rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder non causa più la registrazione di un&#39;eccezione nei file di registro. In precedenza, la rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder causava la registrazione di un’eccezione critica nei registri, nonostante non causasse problemi sul front-end.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: passaggio alla modalità archivio singolo - il contenuto globale non viene più visualizzato
   * _Correzione nota_: il sistema ora sincronizza le configurazioni di progettazione della visualizzazione archivio con le configurazioni di progettazione del sito Web quando si abilita la modalità di archiviazione singola, assicurandosi che gli aggiornamenti del contenuto siano visibili sul front-end. In precedenza, il passaggio alla modalità single store impediva che gli aggiornamenti dei contenuti venissero rispecchiati nella vetrina.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: il Page Builder sostituisce l&#39;immagine quando tenta di aggiungere un collegamento e altri errori di usabilità.
   * _Correzione nota_: facendo clic su un&#39;immagine, i collegamenti nell&#39;editor wysiwyg nell&#39;elemento di testo Page Builder verranno caricati i dati corretti nella finestra di dialogo per la configurazione di collegamenti e immagini. Anche l’aggiunta di un collegamento a un’immagine nell’editor ora funziona correttamente. In precedenza, l’immagine veniva sostituita da un collegamento.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: la raccolta multimediale precedente non riesce a eseguire il rendering delle immagini quando si inserisce un&#39;immagine a 0 byte nella directory
   * _Correzione nota_: il sistema ora gestisce le immagini a 0 byte nella raccolta multimediale senza interrompere la funzionalità, consentendo la visualizzazione e la selezione di altre immagini nella directory come previsto. In precedenza, la presenza di un&#39;immagine a 0 byte nella raccolta multimediale impediva la visualizzazione o la selezione di tutte le immagini nella directory.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: errore di Page Builder durante la modifica del blocco CMS
   * _Correzione nota_: il sistema ora salva correttamente le modifiche apportate nell&#39;area di amministrazione utilizzando Page Builder, senza generare l&#39;errore &quot;Page Builder ha eseguito il rendering per 5 secondi senza rilasciare blocchi&quot;. nella console del browser. In precedenza, questo errore si verificava quando si tentava di salvare le modifiche, impedendo il corretto aggiornamento del contenuto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Nessun pulsante di pagamento o modifica del carrello nella sezione carrello
   * _Nota sulla correzione_: il bundle è stato aggiunto al carrello tramite widget senza errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_: l&#39;anteprima della gestione temporanea del contenuto nelle pagine delle categorie non mostra i widget del prodotto
   * _Correzione nota_: il problema è stato risolto verificando che le voci di prodotto per la categoria aggiuntiva collegata al blocco CMS siano state registrate correttamente nel database. In precedenza, restituiva un set di risultati vuoto quando veniva richiesta la pagina di anteprima della categoria.
* _ACP2E-3122_: [CLOUD] Il pulsante Carica immagine non funziona
   * _Correzione nota_: prima del pulsante Carica immagine per il banner e il dispositivo di scorrimento da PageBuilder non funzionava come previsto e ora, premendo, si apre il file manager locale per selezionare l&#39;immagine da caricare.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): il #2 dell&#39;argomento ($height) deve essere maggiore di 0. Impossibile caricare un’immagine specifica
   * _Correzione nota_: il problema è stato risolto causando errori nell&#39;amministratore durante il caricamento di immagini con altezza 0 tramite la raccolta multimediale ed è stata eseguita correttamente la sincronizzazione delle risorse tramite il comando sync. In precedenza non era possibile caricare l’immagine tramite la raccolta multimediale e il comando di sincronizzazione ha esito negativo anche quando un’immagine specifica si trova nella raccolta.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from in conflitto con l&#39;API di Google Maps
   * _Correzione di nota_: le mappe di Google ora vengono riprodotte correttamente nell&#39;editor di PageBuilder. In precedenza, un errore JavaScript impediva il corretto rendering di Google Maps.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Cloud] - Il cursore di CMS non riflette le ultime modifiche
   * _Correzione nota_: il problema è stato risolto assicurandosi che l&#39;elenco di dispositivi di scorrimento venga aggiornato mentre l&#39;evento di salvataggio viene attivato nella schermata Modifica diapositiva. In precedenza, si attivava e causava il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: si è verificato un errore nella pagina CSM quando i blocchi CMS vengono inseriti utilizzando il generatore di pagine in un ordine specifico
   * _Correzione nota_: in precedenza, in alcune versioni di PHP e OS (Linux), il rendering dei blocchi che facevano riferimento ad altri blocchi CMS tramite PageBuilder non sarebbe riuscito con un &quot;Errore sconosciuto. Riprova.&quot;. Ora il contenuto dei blocchi cms viene riprodotto correttamente all’interno di un contenuto controllato da PageBuilder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [I blocchi dinamici del cloud] non funzioneranno correttamente
   * _Correzione nota_: i segmenti dei clienti connessi vengono ora cancellati dopo la disconnessione, impedendo alla sessione guest di ereditare i segmenti precedentemente connessi
* _ACP2E-3428_: errore di anteprima del modello Pagebuilder per il contenuto di grandi dimensioni
   * _Nota corretta_: a causa di contenuti di grandi dimensioni l&#39;elemento canvas superava i limiti del browser e restituiva un valore errato. Il codice di back-end non veniva decodificato correttamente. È stato corretto limitando le dimensioni dell’area di lavoro al limite del browser universale.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: ultimi aggiornamenti di sicurezza con dimensione font mancante in TinyMCE 7
   * _Nota corretta_: i selettori di dimensione e famiglia di caratteri sono ora disponibili nell&#39;editor di WYSIWYG. Prima di questa correzione, con TinyMCE 7 queste non erano disponibili nell’interfaccia dell’editor.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: dimensione font dell&#39;editor TinyMCE 7 nell&#39;amministratore in PT e non in PX, chiarisci
   * _Correzione nota_: prima della correzione non era possibile specificare la dimensione del carattere in pixel nelle aree WYSIWYG. Ora è possibile impostare la dimensione del carattere in px anziché in pt.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: Il Tipo Di Contenuto Del Prodotto In Page Builder Viene Compresso Senza Messaggi Corretti
   * _Correzione nota_: prima della correzione, l&#39;html di anteprima non veniva generato correttamente se il widget non conteneva prodotti. Ora la risposta vuota viene generata correttamente e il widget prodotti viene visualizzato correttamente nell’anteprima.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [Page Builder]Aggiunta dell&#39;elenco dei prodotti per bloccare i risultati in errori
   * _Correzione nota_: l&#39;aggiunta dell&#39;elenco dei prodotti del bundle al blocco tramite Page Builder non genera errori
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/344fce23>

### Contenuto, SEO

* _ACP2E-2870_: la gerarchia delle pagine CMS può causare problemi di riscrittura degli URL
   * _Correzione nota_: in precedenza, per la riscrittura permanente degli URL personalizzati per le pagine root non appartenenti al sito Web, veniva eseguito un reindirizzamento infinito e la pagina non veniva mai caricata. Dopo l’applicazione di questa correzione, la riscrittura dell’URL personalizzato per la pagina principale non del sito web funziona come previsto e non si verifica alcun ciclo di reindirizzamento.

### Contenuto, staging e anteprima

* _ACP2E-2979_: la regola del prezzo del catalogo non viene visualizzata quando è impostata per la pianificazione con blocchi dinamici
   * _Nota sulla correzione_: il sistema visualizza correttamente il contenuto dinamico associato alle regole del prezzo di catalogo programmato nella pagina dei dettagli del prodotto. In precedenza, il caricamento del contenuto dinamico non riusciva quando venivano pianificate le regole del prezzo di catalogo.

### Cliente/clienti

* _AC-12162_: front-end - convalida della data di nascita non riuscita nella pagina di creazione del cliente
   * _Correzione nota_: assicurati che tutta la convalida funzioni dopo la dipendenza di sistema di moment.js dall&#39;aggiornamento alla versione secondaria più recente
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_: il segmento cliente > Condizione > Cronologia prodotto* > &quot;prodotto visualizzato&quot; non funziona
   * _Correzione nota_: il sistema ora visualizza correttamente i clienti registrati corrispondenti nella condizione &quot;Prodotto visualizzato&quot; in Segmenti cliente, quando la condizione viene soddisfatta. In precedenza, anche quando la condizione veniva soddisfatta, il numero di clienti registrati corrispondenti rimaneva pari a zero.
* _AC-8499_: il campo di testo dell&#39;area geografica non viene reimpostato quando viene modificato il menu a discesa del paese
   * _Correzione nota_: il sistema ora reimposta il campo di testo dell&#39;area geografica quando il paese viene modificato nel menu a discesa, assicurandosi che i valori precedenti non persistano. In precedenza, la modifica del paese dall’elenco a discesa non reimpostava il campo area e veniva mantenuto l’ultimo valore salvato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: l&#39;eliminazione del cliente non comporta la pulizia di tutti i dati della sessione del browser su Storefront per il cliente connesso ed eliminato
   * _Correzione nota_: l&#39;eliminazione di un cliente ora elimina tutti i dati della sessione del browser dalla vetrina per i clienti connessi ed eliminati come previsto. L’acquirente può continuare a fare acquisti e il browser tratta la sua sessione come una sessione ospite. In precedenza, quando l’account del cliente per un acquirente connesso veniva eliminato dall’amministratore, il browser dell’acquirente generava errori JavaScript.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Framework

* _AC-10037_: [Domanda]Configurazione tipo inutilizzato in `app/code/Magento/Translation/etc/di.xml`
   * _Correzione nota_: il sistema ora rimuove le dipendenze inutilizzate nella configurazione, migliorando la pulizia complessiva del codice e l&#39;efficienza. In precedenza, nella configurazione vi erano dipendenze non utilizzate che non contribuivano ad alcuna funzionalità.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38030>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: V1/customers/password endpoint question/issue
   * _Correzione nota_: il sistema ora rispetta i vincoli impostati nell&#39;interfaccia grafica di gestione durante l&#39;elaborazione delle richieste di modifica della password tramite l&#39;API, impedendo il potenziale abuso della funzione di reimpostazione della password. In precedenza, l’API poteva elaborare richieste di modifica della password al di fuori delle regole definite nell’interfaccia grafica di gestione, consentendo potenzialmente un flusso costante di e-mail di reimpostazione se erano note e-mail valide.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: la configurazione Vernice non esclude tutti i parametri di marketing
   * _Correzione nota_: il sistema ora esclude correttamente tutti i parametri di marketing comuni nella configurazione di Vernice, garantendo un tracciamento e un&#39;analisi accurati. In precedenza, alcuni parametri di marketing, come gad_source, srsltid e msclkid, non venivano esclusi, generando potenziali imprecisioni nella raccolta dei dati.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: processo di indicizzazione errori processo indice di ricerca catalogo
   * _Correzione nota_: il sistema ora completa il comando di reindicizzazione senza errori, indipendentemente dalla versione libxml compilata con PHP. In precedenza, l’esecuzione del comando di reindicizzazione causava un errore di &quot;Errore di processo dell’indice di ricerca del catalogo durante il processo di indicizzazione&quot; quando PHP veniva compilato con determinate versioni di libxml.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: sono stati aggiunti i filtri created_at, status e grand_total alla query Ordini cliente e sono stati corretti più errori di filtro
   * _Correzione nota_: il sistema ora supporta l&#39;utilizzo dei filtri created_at, status e grand_total nelle query Ordini cliente e ha risolto un problema che impediva la corretta applicazione di più filtri. In precedenza, il sistema non supportava questi filtri e non applicava tutti i filtri quando in una query ne veniva utilizzato più di uno.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: le query provenienti da blocchi correlati, di upselling e di cross-selling e l&#39;indicizzazione dei prezzi vengono inviate in modo casuale
   * _Correzione nota_: il sistema ora ottimizza le query da blocchi correlati, di upselling e di cross-selling, migliorando le prestazioni e impedendo al sito di andare giù a causa di query eccessive. In precedenza, il sistema poteva essere sovraccarico di query provenienti da questi blocchi, causando rallentamenti significativi e potenzialmente riducendo il sito.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36667>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Eccezione: Avviso: tentativo di accedere all&#39;offset dell&#39;array in... -> Calendar.php dall&#39;aggiornamento a ICU 74.1 (PHP Intl)
   * _Correzione nota_: Commerce non registra più la seguente eccezione nel registro eccezioni ogni volta che un acquirente o un commerciante visita la vetrina o l&#39;amministratore: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38214>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problema] Risolvere i problemi relativi ai dati dei clienti quando il modulo contiene un elemento con nome `method`
   * _Correzione nota_: il sistema ora identifica correttamente l&#39;attributo &#39;method&#39; nell&#39;invio del modulo, anche quando nel modulo è presente un elemento denominato &#39;method&#39;. In questo modo i dati dei clienti vengono elaborati con precisione. In precedenza, se un elemento modulo fosse denominato &quot;metodo&quot;, interferirebbe con l’identificazione dell’attributo &quot;metodo&quot; nell’invio dei moduli, causando potenziali problemi con la gestione dei dati dei clienti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38484>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problema] Correzione di PHPDocs per \Magento\Framework\Data\Collection::getItemById
   * _Correzione nota_: i PHPDocs per il metodo \Magento\Framework\Data\Collection::getItemById sono stati aggiornati per includere null come possibile tipo restituito, risolvendo i problemi con gli strumenti di analisi statica. In precedenza, i PHPDocs del metodo non specificavano null come possibile tipo restituito, generando avvisi o errori nell&#39;analisi statica quando il metodo veniva utilizzato nelle istruzioni condizionali.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38485>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [Problema] Consenti solo preferenze valide durante l&#39;installazione:di:compilazione
   * _Correzione nota_: il sistema ora genera un errore durante il comando setup:di:compile se viene creata una preferenza per una classe che non esiste o che è specificamente esclusa, assicurandosi che siano consentite solo le preferenze valide. In precedenza, questi scenari avrebbero avuto esito negativo in silenzio, rendendo potenzialmente inutili i plug-in associati alle classi originali.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38517>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento sta tentando di modificare la proprietà di sola lettura nel metodo __wakeup di LoggerProxy
   * _Correzione nota_: il sistema ora consente la modifica delle proprietà di sola lettura precedenti nel metodo di riattivazione __LoggerProxy, garantendo un funzionamento senza problemi senza costringere gli utenti a utilizzare una soluzione alternativa. In precedenza, si verificavano problemi se si tentava di riassegnare il valore di una proprietà di sola lettura nel metodo di riattivazione __LoggerProxy.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38526>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Problema] AC-2039 AC-1667 aggiornamento riferimenti TinyMCE
   * _Correzione nota_: aggiornata la versione più recente di tinymce in compositore.json
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38533>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker non funziona in più thread
   * _Correzione nota_: il sistema ora supporta Process Fork per l&#39;indicizzazione MView, evitando errori durante l&#39;esecuzione dell&#39;indicizzatore quando si opera su più thread. In precedenza, l’esecuzione di ChangelogBatchWalker su più thread determinava l’eliminazione delle tabelle utilizzate da altri thread, causando un errore durante l’esecuzione dell’indicizzatore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38246>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problema] Rinominare la variabile con nome errato
   * _Correzione nota_: il sistema ora assegna correttamente un nome alla variabile che contiene l&#39;importo di denaro che può ancora essere rimborsato, evitando confusione durante il debug. In precedenza, questa variabile veniva erroneamente denominata totalRefund, il che poteva generare malintesi per gli sviluppatori.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38609>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Problema] Trasmettere gli attributi personalizzati al collegamento corrente tramite XML
   * _Correzione nota_: il sistema ora consente di passare attributi personalizzati al collegamento corrente tramite XML, garantendo che tali attributi vengano visualizzati correttamente anche quando il collegamento è la pagina corrente. In precedenza, gli attributi personalizzati non venivano visualizzati per il collegamento della pagina corrente perché il metodo getAttributesHtml() non veniva utilizzato per il collegamento corrente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38500>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/30070>
* _AC-11819_: la cache FPC integrata è interrotta nella versione 2.4.7 per alcune configurazioni
   * _Correzione nota_: il sistema ora memorizza correttamente nella cache le pagine quando è impostato il parametro MAGE_RUN_CODE, garantendo prestazioni ottimali. In precedenza, le pagine non venivano memorizzate nella cache in queste condizioni, causando potenziali problemi di prestazioni.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38626>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problema] Correggere l&#39;incoerenza nella gestione delle eccezioni tra le modalità di sviluppo e produzione
   * _Correzione nota_: il sistema ora gestisce in modo coerente le eccezioni tra le modalità di sviluppo e di produzione, evitando il reindirizzamento imprevisto alla pagina di accesso quando viene generata un&#39;eccezione. In precedenza, un’incoerenza nella gestione delle eccezioni poteva causare un reindirizzamento alla pagina di accesso in modalità di produzione invece di visualizzare il messaggio di eccezione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38639>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Sostituisci la traduzione &#39;Conto PayPal&#39; in token_list.phtml
   * _Correzione nota_: il sistema ora etichetta la sezione per i metodi di pagamento con conto &quot;tokenizable&quot; come &quot;Account&quot; invece di &quot;Conto PayPal&quot; nella pagina Metodi di pagamento memorizzati, rendendola più rappresentativa della sua funzione. In precedenza, questa sezione era specificamente etichettata come &quot;Conto PayPal&quot;, che era fuorviante quando sono stati aggiunti altri metodi di pagamento per account tokenizable.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35622>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: compatibilità con le versioni precedenti persa nella classe Magento\Catalog\Model\ProductRepository
   * _Nota corretta_: la classe ProductRepository ora mantiene la compatibilità con le versioni precedenti ripristinando la classe Initialization Helper come secondo parametro, garantendo che i moduli che si estendono da questa classe funzionino come previsto. In precedenza, la rimozione di Initialization Helper dal costruttore nella classe ProductRepository comportava una perdita di compatibilità con le versioni precedenti, costringendo gli utenti a utilizzare una soluzione alternativa.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problema] Distribuzione contenuto statico - Errore di tipo
   * _Correzione nota_: il sistema ora gestisce correttamente i file LESS vuoti durante la distribuzione del contenuto statico, visualizzando il messaggio di errore &quot;LESS file is empty&quot;. In precedenza, veniva generato un errore di tipo errato quando si incontrava un file LESS vuoto durante la distribuzione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Problema] [Visualizzazione] Spazio aggiuntivo rimosso nel tag link e script
   * _Correzione nota_: il sistema ora garantisce che non vi siano spazi aggiuntivi nei tag di collegamento e script, fornendo un codice più pulito ed efficiente. In precedenza, si trovavano doppi spazi tra gli attributi nei tag link e script.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32919>
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
* _AC-12594_: [Problema] Utilizza la configurazione compilata per i dati generati invece della configurazione generale
   * _Correzione nota_: il sistema ora utilizza la configurazione compilata per i dati generati anziché la configurazione generale, riducendo il trasferimento di rete e il sovraccarico dei dati che dipendono da una determinata versione del codice. Questa modifica impedisce l’override della cache nelle istanze condivise durante lo scambio dei contenitori, migliorando la stabilità e riducendo i tempi di inattività. In precedenza, alcune classi principali utilizzavano il tipo di configurazione condiviso, che poteva causare l’override della cache o tempi di inattività dell’applicazione a causa delle differenze nelle versioni del codice tra più server.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Rimuovere i riferimenti ai file da extjs rimossi in e1ccdb...
   * _Correzione nota_: il sistema ora rimuove i riferimenti ai file da extjs che erano stati precedentemente rimossi, eliminando gli errori nella console del browser e nel file di registro del sistema. In precedenza, questi riferimenti causavano errori a causa dell’assenza dei file di riferimento.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Problema] Pulizia minore: è stato corretto l&#39;utilizzo errato di sprintf. Sono necessari solo 2 segnaposto qui e...
   * _Correzione nota_: il sistema ora utilizza correttamente la funzione sprintf con il numero appropriato di segnaposto, migliorando la pulizia e la coerenza del codice. In precedenza, la funzione sprintf veniva erroneamente utilizzata con un argomento aggiuntivo, che non causava problemi importanti ma non era l’utilizzo corretto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: estensione FTP rimossa da PHP 8.2.15
   * _Correzione nota_: il sistema ora include l&#39;estensione FTP come dipendenza nel file compositore.json, garantendo la corretta configurazione delle importazioni CSV tramite FTP. In precedenza, veniva generato un errore durante il tentativo di configurare le importazioni CSV tramite FTP a causa dell’assenza dell’estensione FTP nel pacchetto PHP.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Problema] Corregge le classi errate a cui si fa riferimento nei moduli di Magento.
   * _Correzione nota_: il sistema ora fa correttamente riferimento alle classi nei moduli, garantendo un funzionamento più fluido e impedendo arresti anomali dovuti a classi non esistenti. Ciò include un bug nei moduli Indexer e Creditmemo e l&#39;implementazione di HttpGetActionInterface nella classe PrintAction. In precedenza, i riferimenti di classe errati causavano errori e potenziali arresti anomali del sistema, e alcune funzionalità, come il nome del file creditmemo PDF e la reindicizzazione delle scorte, non funzionavano come previsto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: possibilità di definire l&#39;area per il comando CLI `dev:di:info`
   * _Correzione nota_: il sistema ora consente agli sviluppatori di definire un&#39;area per il comando CLI `dev:di:info`, migliorando il processo di sviluppo e debug. In precedenza, questo comando consentiva di visualizzare solo le informazioni relative all&#39;area GLOBAL.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problema] aggiungere la proprietà isMultipleFiles al modello di elemento modulo immagine
   * _Correzione nota_: questa correzione impedisce che il pulsante &quot;Sfoglia per trovare o trascinare l&#39;immagine qui&quot; scompaia quando un&#39;immagine viene aggiunta in un elemento modulo immagine con più file.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39219>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36325>
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
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http dipende dalla frase del motivo OK
   * _Correzione nota_: la verifica della frase &quot;OK&quot; è stata rimossa da Magento\Framework\Filesystem\Driver\Http::isExists
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39546>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: l&#39;indicizzatore Griglia cliente non funziona correttamente in modalità Aggiornamento tramite pianificazione
   * _Nota sulla correzione_: la griglia del cliente precedente è stata aggiornata immediatamente ma dopo la correzione la griglia del cliente viene aggiornata dopo l&#39;esecuzione della cron ma non viene visualizzata immediatamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: errore di battitura in un file js.
   * _Correzione nota_: il sistema ora utilizza correttamente il termine &quot;sottoscrittori&quot; nel file JavaScript, garantendo la funzionalità corretta delle funzionalità correlate. In precedenza, un errore tipografico nel file JavaScript causava l’uso errato del termine &quot;abbonati&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36163>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problema] Rimuovi tag `@author` non consentito
   * _Correzione nota_: il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37253>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problema] Rimuovi il tag `@author` non consentito da `Magento_Customer` (parte 2)
   * _Correzione nota_: il sistema ora rispetta lo standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37250>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: lo spazio nella sintassi editorconfig interrompe la regola per [{compositore,auth}.json]
   * _Correzione nota_: il sistema ora applica correttamente un rientro di 4 spazi ai file compositore e auth.json, in seguito a una correzione di un errore di sintassi in editorconfig. In precedenza, a causa di uno spazio nella sintassi editorconfig, questi file non venivano formattati correttamente con un rientro a 2 spazi.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37394>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [Problema] Migliorare la registrazione degli errori cron
   * _Correzione nota_: il sistema ora acquisisce e registra sia STDERR che STDOUT per i processi cron, fornendo preziose informazioni diagnostiche negli scenari in cui i processi cron non riescono. In precedenza, eventuali messaggi di errore all’interno dei processi cron non venivano registrati e STDERR e STDOUT per i gruppi cron in esecuzione in processi separati andavano persi.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Problema] Aggiunge altri colori all&#39;output di alcuni comandi cli di installazione
   * _Correzione nota_: il sistema ora aggiunge più colori all&#39;output di alcuni comandi CLI (Command Line Interface) di installazione, migliorando la leggibilità e l&#39;esperienza utente. In precedenza, l&#39;output di questi comandi era più difficile da leggere a causa della mancanza di differenziazione dei colori.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: l&#39;aggiornamento di Magento reimposta General/region/state_required quando viene aggiunto un nuovo paese con lo stato o l&#39;area geografica richiesti.
   * _Correzione nota_: il sistema ora aggiunge il paese modificato alla configurazione &#39;general/region/state_required&#39; solo quando viene aggiunto un nuovo paese con stati required, evitando interruzioni del codice personalizzato che presuppongono la disabilitazione dell&#39;area. In precedenza, l’aggiunta di un nuovo paese con stati obbligatori reimpostava la configurazione &quot;general/region/state_required&quot; sui paesi predefiniti con uno stato obbligatorio, potenzialmente interrompendo il negozio.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37796>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: differenza in termini di compilazione inferiore tra la libreria php e nodejs (grunt) con espressioni `calc` complicate
   * _Correggi nota_: correggi la differenza di compilazione tra la libreria php e nodejs (grunt) dopo l&#39;aggiornamento wikimedia/less.php:^5.x
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37841>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: errore &quot;Tabella o vista di base non trovata&quot; durante l&#39;esecuzione dell&#39;indicizzazione parziale
   * _Nota corretta_: la reindicizzazione parziale ora funziona correttamente con il registro modifiche grande in caso di connessione database secondaria
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: problemi dopo l&#39;aggiornamento di MariaDB a 10.5.1 o versione successiva
   * _Correzione nota_: è stato risolto il problema che si verificava quando i valori datetime in un database venivano convertiti in 0000-00-00 00:00:00 dopo l&#39;aggiornamento di Mysql
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: mancata corrispondenza dei tipi in Confronto dati durante la verifica della presenza di modifiche nei dati
   * _Correzione nota_: in precedenza, l&#39;oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica ai dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: l&#39;importazione [Cloud] non può essere utilizzata con il var della directory
   * _Correzione nota_: il prodotto può essere importato correttamente indipendentemente dal nome del file.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: in ipad mini il menu e l&#39;intestazione vengono caricati come dispositivi mobili, ma come desktop.
   * _Correzione nota_: il sistema ora tratta i dispositivi con una larghezza di 768 px come desktop, assicurandosi che il menu e l&#39;intestazione vengano caricati correttamente. In precedenza, i dispositivi con una larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_: errore di visualizzazione o tabella di base non trovata durante l&#39;esecuzione di mview cron durante un&#39;operazione DDL
   * _Correzione nota_: il sistema ora gestisce correttamente le operazioni di aggiornamento del database mentre l&#39;aggiornamento mview è in esecuzione in background, impedendo il verificarsi di errori di tipo &#39;Tabella di base o vista non trovata&#39;. In precedenza, alcune operazioni di aggiornamento del database potevano causare un errore di tipo &quot;Tabella di base o vista non trovata&quot;, se l’aggiornamento di mview era in esecuzione contemporaneamente.
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
* _ACP2E-3537_: le voci chiave della cache corrispondenti non sono disponibili nei tag della cache, pertanto la pulizia della cache non funziona correttamente
   * _Correzione nota_: la modalità LUA è ora attivata per impostazione predefinita per il Garbage Collector della cache Redis per evitare race condition
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: valore MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK ignorato
   * _Nota di correzione_: dopo la correzione, una variabile ENV impostata su &quot;false&quot; verrà trattata come bool false, non come stringa &#39;false&#39;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Framework, GraphQL

* _AC-7976_: [Problema] È stato introdotto il supporto di tipi scalari personalizzati per lo schema GraphQL
   * _Correzione nota_: il sistema ora supporta i tipi scalari personalizzati per lo schema di GraphQL, consentendo agli sviluppatori di definire tipi e implementazioni scalari personalizzati. Questa funzione può essere particolarmente utile per esprimere valori che possono richiedere la convalida, come HTML, e-mail, URL, date e così via, e per casi più avanzati come gli attributi EAV. In precedenza, il sistema non supportava l’elaborazione di tipi scalari personalizzati in GraphQL.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36877>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, prodotto

* _AC-13011_: i rapporti EE 2.4.8-beta1 non vengono generati a causa dell&#39;eccezione Magento

### Framework, Framework interfaccia utente

* _ACP2E-3324_: possibilità di sovrascrivere il valore di configurazione anche se è bloccato
   * _Nota sulla correzione_: in precedenza, la configurazione della progettazione non poteva essere impostata tramite il comando bin/magento config:set e i valori bloccati potevano essere modificati modificando il modulo che li visualizzava. Dopo la correzione i valori bloccati impostati da cli con —lock-env o —lock-conf non possono più essere aggiornati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_: Magento_GraphQl esegue l&#39;elaborazione delle intestazioni anche se il valore dell&#39;intestazione non supera la convalida
   * _Correzione nota_: il sistema ora assicura che l&#39;elaborazione dell&#39;intestazione venga eseguita una sola volta e solo se il valore dell&#39;intestazione supera la convalida, migliorando la sicurezza e impedendo potenziali vulnerabilità. In precedenza, l’elaborazione dell’intestazione veniva eseguita anche se il valore dell’intestazione non superava la convalida, generando potenziali vulnerabilità e comportamenti imprevisti dovuti alla doppia elaborazione dei valori dell’intestazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: le opzioni Giftcard fisiche non hanno l&#39;ordinamento corretto
   * _Correzione nota_: il sistema ora ordina correttamente le opzioni dei prodotti gift card fisici quando viene eseguita una query tramite GraphQL, garantendo un rendering coerente con il tema Luma. In precedenza, l’ordinamento era errato in base al tema luma, causando una visualizzazione e un ordinamento errati delle opzioni, ad esempio nome del mittente, nome del destinatario e importo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: la cache del resolver [GraphQL] è invalidata durante la creazione, la modifica, lo spostamento o l&#39;eliminazione di un aggiornamento di gestione temporanea
   * _Correzione nota_: il sistema ora garantisce che la cache del resolver non venga invalidata durante la creazione, la modifica, lo spostamento o l&#39;eliminazione di un aggiornamento di gestione temporanea, ma solo quando l&#39;aggiornamento di gestione temporanea viene applicato all&#39;entità. In precedenza, la cache del risolutore veniva invalidata prematuramente, anche prima dell’applicazione dell’aggiornamento di staging, il che portava a inutili invalidamenti della cache.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: cache rapida non cancellata per l&#39;aggiornamento della gestione temporanea del contenuto
   * _Correzione nota_: ora GraphQL con cache di risposta dei contenuti di PageBuilder viene invalidato quando le entità correlate al contenuto di PageBuilder vengono aggiornate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: disabilitazione della navigazione a livelli - non rimuove l&#39;aggregazione da Graphql
   * _Correzione nota_: il problema è stato risolto dopo l&#39;applicazione del controllo durante la richiesta di una ricerca di prodotti con aggregazioni di categorie tramite una query di GraphQL quando l&#39;impostazione di configurazione dell&#39;amministratore è &quot;Catalogo > Navigazione a livelli > Visualizza filtro categorie&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: la chiamata Prodotti GraphQL contenente il filtro prezzi {from:&quot;0&quot;} non restituisce alcun risultato
   * _Correzione nota_: in precedenza, la ricerca di prodotti graphql con filtro a prezzi zero non restituiva alcun risultato a causa di un&#39;eccezione generata. Ora la ricerca restituisce i risultati come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: le traduzioni per gli attributi restituiti dai clienti non si riflettono nell&#39;API GraphQL per il rispettivo StoreView
   * _Correzione nota_: le traduzioni per gli attributi restituiti dai clienti si riflettono nell&#39;API GraphQL per il rispettivo StoreView.
In precedenza, gli attributi di restituzione dei clienti per i rispettivi StoreView non venivano riportati nell’API di GraphQL.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [Cloud] chiamata GraphQL interrotta per getPurchaseOrder con virgolette nodi
   * _Correzione nota_: la chiamata GraphQL dell&#39;ordine di acquisto sarà in grado di eseguire l&#39;attività senza errori interni del server.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Prodotti configurabili cloud] non visualizzati nel sito di produzione se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;
   * _Correzione nota_: il sistema ora visualizza correttamente i prodotti configurabili nel sito anche se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;, ma è abilitato in ambiti di visualizzazione dello store specifici.
In precedenza, se un prodotto veniva disabilitato in &quot;Tutte le visualizzazioni store&quot; e abilitato solo in ambiti di visualizzazione specifici, gli attributi del prodotto non venivano visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [Grafql prodotti cloud] con errore quando lo stesso prodotto semplice è stato assegnato a più prodotti configurabili
   * _Correzione nota_: in precedenza, con prodotti configurabili separati con lo stesso prodotto semplice, grapQL restituiva un errore. Dopo l’applicazione di questa correzione, diversi prodotti configurabili con lo stesso prodotto semplice, grapQL restituisce il risultato senza errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Cloud] problema con l&#39;autenticazione utente e l&#39;accesso ai token intersito nella configurazione multisito
   * _Correzione nota_: le query GraphQl su informazioni cliente e carrello in Configurazione multisito controllano se il cliente esiste su un sito Web non predefinito.
La query precedente funzionava senza assicurarsi che il cliente esistesse su un sito Web non predefinito in Configurazione multisito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: la paginazione di GraphQL cart itemsV2 non funziona correttamente
   * _Correzione nota_: il problema è stato risolto passando il valore corretto per l&#39;argomento della pagina corrente nella query di raccolta. In precedenza, veniva trasmesso un valore errato per impostare la pagina corrente, causando il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
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
* _ACP2E-3492_: [Cloud] problemi con API Graphql
   * _Correzione nota_: prima della correzione tramite il server applicazioni Graphql, la richiesta dell&#39;indirizzo del cliente non ha restituito i dati più recenti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: il prodotto disabilitato viene ancora visualizzato negli elementi correlati, di upselling e di cross-selling nella query grpahQL
   * _Correzione nota_: Graphql ora fornisce la risposta corretta per i prodotti relared, upselling e cross-selling disabilitati
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [CLOUD]: Errore GraphQl Errore interno del server. Mutazione placeOrder
   * _Correzione nota_: la mutazione &quot;placeOrder&quot; con le informazioni sul codice coupon nella richiesta non genera più un&#39;eccezione di errore interna. L&#39;ordine è stato inserito correttamente. In precedenza, non riusciva con &quot;Errore interno del server&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: la percentuale di sconto non è calcolata per i prodotti bundle con prezzo dinamico
   * _Correzione nota_: la correzione aggiunta per sconto_percentuale di prodotto.dettagli_prezzo non mostra il valore corretto per i prodotti bundle con prezzo dinamico abilitato e coupon di sconto applicato.
* _LYNX-485_: i prodotti del bundle mostrano ancora &quot;IN_STOCK&quot; quando uno dei suoi prodotti del bundle è esaurito
   * _Correzione nota_: è stato risolto il problema che causava la visualizzazione di &quot;IN_STOCK&quot; dei prodotti bundle anche quando uno dei prodotti inclusi era esaurito.
* _LYNX-486_: not_available_message e only_x_left_in_stock non mostra lo stesso stock disponibile
   * _Correzione nota_: è stato risolto il problema che causava la mancata disponibilità delle scorte tra not_available_message e only_x_left_in_stock
* _LYNX-488_: il campo original_row_total restituisce un valore errato
   * _Correzione nota_: è stato risolto il problema con il campo original_row_total, che restituiva valori errati quando venivano selezionate opzioni personalizzate
* _LYNX-503_: la miniatura del prodotto raggruppato deve essere visualizzata in base alla configurazione     .
   * _Correzione nota_: il problema è stato risolto per garantire che la miniatura del prodotto raggruppato venga visualizzata in base alle impostazioni di configurazione
* _LYNX-510_: errore durante la query di selected_options in OrderAddress
   * _Correzione nota_: AttributeSelectedOptions è stato aggiornato a custom_attributesV2 nella risposta GraphQL dell&#39;indirizzo dell&#39;ordine.
* _LYNX-512_: original_item_price non include sconti
   * _Correzione nota_: il valore original_item_price è stato aggiornato per includere gli sconti.
* _LYNX-530_: il messaggio Non disponibile non mostra la quantità di magazzino disponibile
   * _Correzione nota_: il messaggio di errore e il codice di errore per la mutazione AddProductsToCart sono stati risolti per allinearli alla configurazione del messaggio &quot;not available&quot;
* _LYNX-532_: lo stato &quot;OUT_OF_STOCK&quot; viene restituito su Semplice con opzioni personalizzate e prodotti con opzioni a selezione multipla
   * _Correzione nota_: il resolver StockStatusProvider è stato aggiornato nel pacchetto di inventario per correggere stock_status per i prodotti semplici con opzioni personalizzate.
* _LYNX-533_: Errore (GQL): cart.itemsV2.items.product.custom_attributesV2 restituisce un errore del server
   * _Correzione nota_: è stato risolto l&#39;errore del server che si verificava quando una query del carrello includeva gli attributi personalizzati di un prodotto aggiungendo un prodotto senza attributi personalizzati.
* _LYNX-536_: orders/date_of_first_order restituisce sempre null
   * _Correzione nota_: è stato risolto il problema a causa del quale ordini > data_del_primo_ordine restituivano sempre null.
* _LYNX-544_: il cliente non deve essere in grado di annullare un ordine parzialmente spedito
   * _Correzione nota_: è stata aggiunta la convalida per impedire ai clienti di annullare un ordine parzialmente spedito.
* _LYNX-548_: codici di errore per l&#39;annullamento dell&#39;ordine in base al messaggio di errore
   * _Correzione nota_: i codici di errore per l&#39;annullamento dell&#39;ordine ora si basano sul messaggio di errore specifico.
* _LYNX-581_: torna indietro le proprietà relative ai cookie da private a protected
   * _Correzione nota_: ripristina la visibilità delle proprietà del costruttore di classe Magento\Framework\App\PageCache\Version da private a protected
* _LYNX-600_: aumento della complessità massima predefinita delle query GraphQL a 1000
   * _Correzione nota_: la complessità massima predefinita delle query GraphQL è stata aumentata da 300 a 1000.
* _LYNX-620_: GQL - itemsV2 > Riga totale originale. I prezzi del range di prezzi vengono restituiti come $0,00 per il prodotto scaricabile con opzioni di file con prezzi separati.
   * _Correzione nota_: è stato risolto un problema a causa del quale i prodotti scaricabili con opzioni di acquisto di collegamento separate abilitate restituivano 0 dollari per gli elementiV2 > Totale riga originale e l&#39;intervallo di prezzo restituiva 0 dollari per i prodotti con opzioni di file con prezzi separati.
* _LYNX-711_: schema di una tabella quando viene creato nuovo di zecca diverso da quello dell&#39;aggiornamento
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;aggiunta di una nuova colonna VARCHAR a una tabella esistente causava errori di test a causa di differenze di schema tra nuove installazioni e aggiornamenti. Il metodo modifyColumn() ora gestisce correttamente le colonne VARCHAR impostando il set di caratteri e le regole di confronto predefiniti.
* _LYNX-772_: compatibilità GraphQl per la versione PHP-8.4
   * _Correzione nota_: sono stati risolti problemi di compatibilità di GraphQL con PHP 8.4 in più resolver, garantendo funzionalità senza problemi. Sono stati aggiornati i file interessati nei moduli CatalogRule, Customer, GiftMessage, GiftCard e GiftWrapping.

### GraphQL, Inventory/MSI

* _ACP2E-2607_: la mutazione MergeCart genera un&#39;eccezione quando i carrelli di origine e di destinazione hanno gli stessi elementi bundle
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, inventario/MSI, prestazioni

* _ACP2E-1716_: sito inattivo dopo l&#39;aggiornamento
   * _Nota corretta_: le prestazioni del recupero dei prodotti bundle tramite GraphQl sono migliorate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Prestazioni

* _AC-9569_: [I dati del resolver di GraphQL] non sono stati invalidati dall&#39;importazione
   * _Correzione nota_: la cache del resolver clienti di GraphQL ora viene invalidata come previsto quando un cliente viene modificato o eliminato tramite importazioni. In precedenza, la cache non veniva invalidata e i dati dei clienti potevano essere modificati o eliminati durante l’importazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Cerca

* _ACP2E-2809_: l&#39;ordinamento dell&#39;elenco di prodotti GraphQL in base a più parametri non funziona
   * _Nota corretta_: l&#39;ordinamento dei prodotti in base a più campi in GraphQl ora funziona come descritto nella documentazione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: query GraphQL di elenco prodotti limitata a un totale di 10.000 prodotti
   * _Nota sulla correzione_: dopo la correzione, il risultato della ricerca non è limitato ai prodotti 10000, è possibile ottenere tutti i prodotti che corrispondono ai criteri di ricerca anche se il conteggio è superiore a 10000.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, framework di prova

* _ACP2E-3363_: errore test integrazione Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importa/esporta

* _AC-12172_: problema durante l&#39;importazione del prodotto se fornito con il tipo di opzione personalizzato: file (il prodotto creato non contiene il prezzo per l&#39;opzione personalizzata e mostra solo la prima estensione del tipo di file fornita)
   * _Correzione nota_: il sistema ora importa correttamente i dati del prodotto con opzioni personalizzate di tipo &quot;file&quot;, assicurandosi che vengano visualizzate tutte le estensioni di file fornite e che venga incluso il prezzo per l&#39;opzione personalizzata. In precedenza, durante l’importazione del prodotto, se un’opzione personalizzata di tipo &quot;file&quot; veniva fornita con più di un’estensione di file, veniva visualizzata solo la prima estensione e mancava il prezzo per l’opzione personalizzata.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38805>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: tempo di esecuzione errato per l&#39;operazione di importazione nella griglia Cronologia importazione
   * _Correzione nota_: il tempo di esecuzione del report di importazione viene visualizzato correttamente indipendentemente dalle impostazioni locali dell&#39;amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: clienti duplicati creati con lo stesso indirizzo e-mail utilizzando l&#39;importazione
   * _Correzione nota_: l&#39;importazione del cliente mentre la condivisione account è impostata su Globale, il cliente importato esistente nel sistema viene aggiornato.
Il cliente importato in precedenza è stato duplicato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Aggiungi/aggiorna importazione su prodotti che duplicano opzioni personalizzabili
   * _Correzione nota_: il problema è stato risolto assegnando l&#39;archivio corretto alle opzioni prodotto durante le importazioni CSV delle opzioni prodotto.
In precedenza, venivano assegnati all’archivio di amministrazione invece che al rispettivo archivio.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: data &quot;created_at&quot; cliente non convertita in fuso orario di archiviazione al momento dell&#39;esportazione
   * _Correzione nota_: un valore di data colonna &#39;created_at&#39; viene convertito nel formato di data corretto in base al fuso orario dell&#39;archivio nella sezione CSV di esportazione del cliente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] Viene visualizzato un errore durante la verifica dei dati nei dati di importazione tramite CSV
   * _Correzione nota_: nessun errore durante il controllo dei dati durante l&#39;importazione CSV. In precedenza, il messaggio di errore visualizzato era: &quot;Impossibile trovare un cliente che corrisponda a questo indirizzo e-mail e al codice del sito web nelle righe: 1&quot; quando si controllano i dati nella sezione di importazione utilizzando il file CSV dell’amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_: pulsante Importa mancante
   * _Correzione nota_: per risolvere il problema di mancanza del pulsante Importa dopo la verifica dei dati con record corretti e non corretti nel file CSV. In precedenza, il pulsante di importazione non veniva visualizzato dopo il controllo dei dati con record corretti e non corretti nel file CSV.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: impossibile importare l&#39;indirizzo del cliente esportato
   * _Correzione nota_: l&#39;importazione dell&#39;indirizzo del cliente procederà come previsto. In precedenza, un file di importazione dell’indirizzo di un cliente non superava la convalida se Condividi account del cliente = Globale ed esistono due siti web in cui il sito web predefinito ha un elenco di paesi limitato e l’indirizzo che viene importato è per un altro sito web in cui i paesi consentiti sono diversi
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Cloud] La quantità errata nel file CSV non ha restituito alcun errore
   * _Correzione nota_: ora l&#39;importazione di origini di magazzino genererà un errore di convalida per i valori non numerici nella colonna Quantità. In precedenza, l&#39;importazione di origini di scorte con valore non numerico nella colonna Quantità comportava l&#39;impostazione della quantità su 0.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: il messaggio di errore relativo alla chiave URL duplicata generato durante l&#39;importazione di un prodotto non è corretto quando la chiave URL appartiene già a una categoria
   * _Correzione nota_: viene visualizzato il messaggio di errore corretto durante il controllo dell&#39;importazione del prodotto, quando il cliente ha tentato di importare il prodotto quando il codice URL del prodotto appartiene già a una categoria.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: l&#39;esportazione del prodotto causa OOM anche con il limite di memoria 4G
   * _Nota sulla correzione_: prima di questa correzione, l&#39;esportazione del prodotto non è riuscita se gli attributi del prodotto avevano migliaia di valori di opzione anche con memoria 4G disponibile. Dopo questa correzione, l’esportazione del prodotto dovrebbe terminare l’esportazione del file CSV.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [Processi di importazione cloud] che interferiscono tra loro
   * _Nota sulla correzione_: i messaggi corretti vengono visualizzati se lo stesso utente amministratore esegue due o più operazioni di importazione utilizzando la stessa sessione utente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

### Importazione/esportazione, prestazioni

* _ACP2E-3476_: [Cloud] Il tempo di importazione del prodotto è aumentato in modo significativo
   * _Nota sulla correzione_: prima della correzione, l&#39;importazione di prodotti catalogo con più di 10.000 voci presentava una notevole riduzione del tempo. Dopo la correzione, l’importazione del prodotto catalogo viene eseguita in modo tempestivo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Installazione e amministrazione

* _AC-13242_: aggiornamento Magento non riuscito in MariaDB 11.4 + 2.4.8-beta1
   * _Correzione nota_: l&#39;aggiornamento dovrebbe essere eseguito senza errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: nessun pulsante Esporta VCL per vernice 7 nel pannello di amministrazione
   * _Correzione nota_: il pulsante &quot;Esporta VCL per vernice 7&quot; è stato aggiunto al pannello di amministrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventario/MSI

* _AC-10750_: l&#39;aggiornamento dell&#39;inventario del prodotto configurabile non riesce quando il database utilizza prefissi
   * _Correzione nota_: il sistema aggiorna correttamente l&#39;inventario dei prodotti configurabili quando il database utilizza i prefissi, evitando messaggi di errore e assicurando il salvataggio della quantità corretta. In precedenza, se il database utilizzava i prefissi, si verificava un errore durante il tentativo di salvare la quantità di magazzino per i prodotti semplici all’interno di un prodotto configurabile.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: la chiave API Google google non funziona durante l&#39;aggiunta della mappa con attributi
   * _Correzione nota_: il sistema ora supporta la versione più recente dell&#39;API di Google Maps 3.56, consentendo agli utenti di aggiungere correttamente un blocco di contenuto Map dal menu PageBuilder all&#39;area di visualizzazione senza riscontrare errori. In precedenza, gli utenti non potevano aggiungere un blocco di contenuto Mappa a causa di problemi di compatibilità con la versione dell’API Google Maps, causando un messaggio di errore &quot;si è verificato un errore&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: impossibile creare la spedizione per l&#39;articolo dell&#39;ordine con più origini e SKU danneggiata
   * _Correzione nota_: in precedenza, quando gli spazi sono stati aggiunti per errore nello SKU tramite il database, si verificava un errore nella pagina di spedizione che ora è corretta e il ritaglio automatico è considerato un errore di facile utilizzo e non è stato trovato alcun impatto. La spedizione è stata quindi creata correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Test] prodotti bundle con 0 inventario visualizzati sul lato negozio
   * _Correzione nota_: il prodotto del bundle non viene visualizzato nei siti Web aggiuntivi utilizzando materiale aggiuntivo.
* _ACP2E-2794_: [Cloud] problema critico con l&#39;elenco dei prodotti con spazi vuoti
   * _Correzione nota_: il sistema visualizza correttamente gli elenchi di prodotti senza spazi vuoti quando i prodotti sono impostati su &quot;esaurito&quot;, garantendo una visualizzazione coerente e accurata dei prodotti disponibili. In precedenza, se si impostava un prodotto su &quot;Esaurito&quot;, nell’elenco dei prodotti veniva visualizzato uno spazio vuoto, che causava interruzioni del layout e poteva confondere i clienti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: impossibile spedire l&#39;ordine quando l&#39;archivio di ritiro MSI è abilitato
   * _Correzione nota_: sono state migliorate le prestazioni di inventario per creare la spedizione in caso di numerose origini con prelievo in-store
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: la reindicizzazione Cron non riesce ad aggiornare la disponibilità del prodotto sul front-end
   * _Correzione nota_: in precedenza, i prodotti rimanevano esauriti sul front-end dopo l&#39;aggiornamento dello stato dell&#39;ordine arretrato tramite l&#39;API REST. Ora, dopo aver aggiornato lo stato dell’ordine inevaso tramite l’API REST, i prodotti vengono visualizzati come in stock.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: l&#39;aggiunta di immagini a configurabile non funziona quando MSI è abilitato.
   * _Nota corretta_: il caricamento dell&#39;immagine per il prodotto configurabile ora funziona come previsto quando viene utilizzato il modulo inventario. In precedenza, il caricamento dell’immagine non funzionava
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: problema con il prodotto del bundle + MSI in Clean M2.4.7-p3
   * _Correzione nota_: in precedenza, per i prodotti del bundle di inventario dopo la duplicazione con lo stesso prodotto semplice, il prodotto semplice non poteva essere salvato. Dopo l’applicazione di questa correzione, il prodotto semplice può essere salvato correttamente senza eccezioni.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39358>
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/0208e433>

### Magazzino/MSI, Ricerca

* _ACP2E-3413_: tutti i prodotti sono indicizzati con [is_out_of_stock] = 1 quando lo SKU non è impostato come attributo ricercabile
   * _Nota sulla correzione_: dopo la correzione, &quot;is_out_of_stock&quot; nell&#39;indice di ricerca del catalogo è corretto, anche quando lo SKU non è ricercabile.
   * _Contributo codice GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>

### Ordine

* _AC-10828_: schermata di panoramica ordine back-end: quantità in inevaso non visibile a livello di articolo ordine
   * _Correzione nota_: il sistema visualizza ora il numero di articoli in inevaso nella colonna Quantità della schermata di panoramica ordine inevaso. In questo modo gli utenti possono tenere traccia con precisione dello stato di tutti gli elementi di un ordine. In precedenza, la colonna Quantità mostrava solo il numero di articoli ordinati, fatturati e spediti, ma non il numero di articoli in inevaso.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] ID archivio errato utilizzato nel modulo di rendering degli indirizzi dell&#39;ordine
   * _Correzione nota_: il sistema ora utilizza correttamente l&#39;ID store associato a un ordine durante il rendering dell&#39;indirizzo dell&#39;ordine, assicurandosi che gli indirizzi siano formattati correttamente in base al rispettivo ID store. In precedenza, il sistema utilizzava erroneamente l’ID store corrente, il che poteva causare una formattazione degli indirizzi errata nei casi in cui occorreva inviare più e-mail di ordine da diversi store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38412>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: problema di caching JoinProcessor
   * _Correzione nota_: il sistema ora applica correttamente il JoinProcessor per ogni iterazione, anche con chiamate consecutive, garantendo un recupero accurato dei dati. In precedenza, JoinProcessor veniva erroneamente contrassegnato come già applicato in iterazioni consecutive, causando errori nel recupero dei dati.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/27504>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Numero] Prezzo di spedizione diverso nel PDF stampato
   * _Nota sulla correzione_: i prezzi di spedizione vengono ora visualizzati correttamente nei PDF stampati in base alle impostazioni di configurazione dell&#39;imposta, garantendo la coerenza tra la pagina di visualizzazione della fattura dell&#39;ordine di vendita e la fattura stampata. In precedenza, il prezzo di spedizione visualizzato nel PDF stampato escludeva le imposte, indipendentemente dalle impostazioni di configurazione delle imposte.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: riordina con un prodotto configurabile padre eliminato
   * _Correzione nota_: durante il riordino con il prodotto eliminato il sistema non mostrerà il pulsante Riordina da riordinare
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39568>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Problema] Correzione non valida \Magento\Sales\Model\Order\Email\Container\Template::$id property
   * _Correzione nota_: in questo modo viene corretto il phpdoc non valido per \Magento\Sales\Model\Order\Email\Container\Template::$id, in realtà $id è di tipo int ma in realtà è string.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39151>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: impossibile salvare le modifiche al numero di telefono nei dettagli dell&#39;ordine esistenti
   * _Correzione nota_: ora l&#39;utente può aggiungere il prefisso internazionale 00 nel campo telefono dell&#39;indirizzo ordine
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38201>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: impossibile inviare le e-mail
   * _Correzione nota_: il sistema ora include un&#39;opzione di configurazione async_sending_attempted per specificare il numero di tentativi di invio di un&#39;e-mail prima dell&#39;arresto, migliorando la gestione degli invii di e-mail non riusciti quando &quot;Invio asincrono&quot; è abilitato. In precedenza, se l’invio di un’e-mail non riusciva, il sistema tentava continuamente di inviarla nuovamente, generando un ciclo infinito di messaggi di errore nel registro del sistema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Cloud] lo stato dell&#39;ordine è stato modificato in completo quando si effettua il rimborso parziale di un ordine spedito parzialmente
   * _Nota di correzione_: quando si emette una nota di accredito, lo stato dell&#39;ordine non viene più modificato in &quot;completato&quot; se sono presenti articoli non ancora spediti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] Non è possibile disabilitare l&#39;invio di e-mail dall&#39;interfaccia utente di amministrazione come mostra la documentazione per sviluppatori
   * _Correzione nota_: il sistema ora impedisce correttamente l&#39;invio di e-mail di vendita quando la comunicazione e-mail è disabilitata. Queste e-mail non verranno più inviate quando la comunicazione e-mail verrà riattivata. In precedenza, le e-mail di vendita avviate mentre la comunicazione e-mail era disabilitata venivano comunque inviate una volta riabilitata la comunicazione e-mail.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: ordine chiuso senza rimborso completo
   * _Correzione nota_: il sistema ora gestisce correttamente lo stato dell&#39;ordine come &quot;Elaborazione&quot; e lo stato della fattura come &quot;In sospeso&quot; quando viene creata una spedizione per un ordine con un pagamento non acquisito. In questo modo gli ordini vengono contrassegnati come &#39;Chiusi&#39; solo dopo essere stati completamente rimborsati. In precedenza, la creazione di una spedizione per un ordine con una fattura in sospeso avrebbe erroneamente modificato lo stato dell’ordine in &quot;Chiuso&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Cloud] Impossibile creare l&#39;ordine in admin su un archivio se non è stato impostato solo l&#39;indirizzo di fatturazione predefinito
   * _Correzione nota_: messaggio di errore pertinente &quot;Un cliente con lo stesso indirizzo e-mail esiste già in un sito Web associato&quot;. viene visualizzato se un cliente non ha un indirizzo di fatturazione predefinito e tenta di creare un ordine in un altro negozio.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: richieste di ordine di luogo duplicate inviate dall&#39;amministratore
   * _Correzione nota_: in precedenza, era possibile fare clic più volte sul pulsante &quot;Invia ordine&quot; nel pannello di amministrazione o attivarlo premendo ripetutamente il tasto &quot;Invio&quot;, causando invii duplicati o ordini con errore. Ora, impedendo ulteriori azioni fino a quando l’ordine non è completamente elaborato, garantendo che venga inviato un solo ordine.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: l&#39;amministratore può ancora effettuare l&#39;ordine anche senza il metodo di pagamento
   * _Nota sulla correzione_: il metodo di pagamento selezionato in precedenza viene mantenuto quando il metodo di pagamento viene nuovamente visualizzato nell&#39;elenco dei pagamenti disponibili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3518_: gli elementi vengono duplicati dopo aver creato un ordine da Admin on - Mozilla Firefox Browser
   * _Correzione nota_: i prodotti aggiunti utilizzando &quot;Aggiungi prodotti da SKU&quot; non vengono più duplicati in Firefox durante la creazione di un ordine in admin.

### Ordine, Pagamenti

* _ACP2E-3233_: l&#39;amministratore può ancora effettuare l&#39;ordine anche senza il metodo di pagamento
   * _Correzione nota_: in precedenza, il commerciante poteva effettuare ordini dal pannello di amministrazione senza selezionare un metodo di pagamento. Ora, il commerciante è richiesto un metodo di pagamento per procedere con l&#39;effettuazione di un ordine.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Ordine, restituzioni

* _ACP2E-2982_: il rimborso dell&#39;ordine risulta in una nota di credito duplicata
   * _Correzione nota_: l&#39;emissione del rimborso tramite l&#39;API REST quando due richieste identiche sono state eseguite contemporaneamente non creerà più note di credito duplicate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Ordine, imposta

* _ACP2E-3003_: [CLOUD] Base_row_total non corretta nell&#39;API dell&#39;ordine RESTFUL quando si abilitano transazioni transfrontaliere e si applicano sconti coupon
   * _Correzione nota_: ora viene restituito il valore base_row_total corretto dall&#39;API dell&#39;ordine RESTFUL quando è abilitata la transazione transfrontaliera e viene applicato lo sconto coupon.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Altro

* _BUNDLE-3394_: [Braintree] Rimborso della transazione di archiviazione online come transactionid-rimborso
* _BUNDLE-3421_: [Braintree] + [CLOUD] Ordini Braintree (carta di credito) non in grado di dividere le spese
* _BUNDLE-3422_: [Braintree] [Cloud]Il certificato SSL di Braintree scade il 30 giugno
* _LYNX-339_: cookie private_content_version restituito nelle query GQL
   * _Correzione nota_: è stato risolto un problema a causa del quale il cookie private_content_version veniva restituito nelle query di GraphQL, anche quando il cookie di sessione era disabilitato. Il cookie non viene più incluso nelle risposte di GraphQL quando la sessione è disabilitata, come previsto.
* _LYNX-366_: errore del server nelle proprietà e-mail nelle query con gift card fisiche
   * _Correzione nota_: è stato corretto un problema a causa del quale le query per sender_email e recipient_email sulle gift card fisiche generavano un errore del server. Queste proprietà ora vengono restituite correttamente per le carte regalo virtuali e il comportamento di query è coerente.
* _LYNX-380_: l&#39;attributo is_available in CartItemInterface restituisce sempre false per i prodotti configurabili
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;attributo is_available in CartItemInterface restituiva sempre false per i prodotti configurabili in magazzino. Ora riflette correttamente la disponibilità come true quando applicabile.
* _LYNX-382_: l&#39;attributo is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto
   * _Correzione nota_: è stato risolto il problema a causa del quale l&#39;attributo is_available in CartItemInterface restituiva erroneamente true anche quando la quantità dell&#39;articolo del carrello superava le scorte vendibili.
* _LYNX-395_: l&#39;attributo only_x_left_in_stock in ProductInterface non è accurato nei prodotti configurabili
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;attributo only_x_left_in_stock in ProductInterface non rifletteva con precisione le scorte disponibili per le varianti di prodotto configurabili nel carrello. Ora, il valore only_x_left_in_stock corrisponde correttamente ai livelli di scorte varianti effettivi, garantendo che vengano restituiti dati di inventario accurati nella query GQL del carrello.
* _LYNX-399_: la miniatura segnaposto viene restituita quando un prodotto semplice viene aggiunto al carrello all&#39;interno di un prodotto raggruppato
   * _Nota corretta_: è stato risolto un problema che causava la restituzione di un&#39;immagine di miniatura segnaposto da parte dell&#39;aggiunta di un prodotto semplice (parte di un prodotto raggruppato) al carrello, anche quando al prodotto era stata assegnata un&#39;immagine.
Dettagli correzione:
* Ora la miniatura del prodotto mostra correttamente l’immagine assegnata, se disponibile.
* La selezione delle miniature rispetta la configurazione di amministrazione in:
Negozi > Configurazione > Vendite > Pagamento > Carrello acquisti > Immagine prodotto raggruppato.
In questo modo si garantisce un comportamento coerente delle miniature per i prodotti raggruppati in base alle impostazioni dello store.
* _LYNX-400_: gli attributi di opzione personalizzati del cliente non funzionano con valori interi
   * _Correzione nota_: è stato risolto un problema che impediva il funzionamento degli attributi di opzione personalizzati del cliente se il valore restituito era un numero intero. Le opzioni personalizzate ora gestiscono e restituiscono correttamente i valori interi come previsto.
* _LYNX-402_: errore interno del server durante il tentativo di ottenere priceDetails per i prodotti Bundle con prezzo dinamico
   * _Correzione nota_: è stato risolto un problema che causava un errore interno del server a causa della query di price_details per i prodotti bundle con prezzo dinamico tramite GraphQL. Questo miglioramento garantisce la stabilità delle query sul carrello quando si lavora con prodotti bundle configurati con prezzi dinamici.
* _LYNX-403_: only_x_left_in_stock restituisce sempre 0 per i prodotti configurabili
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;attributo only_x_left_in_stock restituiva sempre 0 per i prodotti configurabili quando aggiunti utilizzando lo SKU padre con opzioni.
Dettagli correzione:
* Il valore only_x_left_in_stock ora riflette con precisione il materiale grezzo della variante figlio selezionata invece dello SKU padre.
* In questo modo i livelli delle scorte vengono visualizzati correttamente per le varianti di prodotto configurabili nel carrello e nelle pagine dei prodotti.
* _LYNX-405_: Errore GraphQL: tipo di file non supportato nella query delle opzioni personalizzabili
   * _Correzione nota_: è stato risolto un problema a causa del quale GraphQL restituiva un errore per le opzioni personalizzabili di tipo &#39;file&#39; negli elementi del carrello. La query ora restituisce correttamente i dettagli per tutti i tipi di opzioni personalizzabili, comprese le opzioni basate su file, senza causare errori.
* _LYNX-411_: la query GraphQL non restituisce il prezzo normale calcolato corretto per i prodotti personalizzabili
   * _Correzione nota_: è stato risolto un problema a causa del quale GraphQL non restituiva il prezzo normale calcolato corretto per i prodotti personalizzabili. La query ora include correttamente il prezzo regolare calcolato con valori personalizzabili applicati (ad esempio, $ 125) nella proprietà price, che riflette sia il prezzo di base che eventuali costi di personalizzazione aggiuntivi.
* _LYNX-412_: le imposte applicate tramite EstimatedTotals persistono con mutazioni aggiornate
   * _Correzione nota_: è stato risolto un problema con la mutazione EstimatedTotals a causa del quale le imposte applicate persistevano su un carrello anche dopo l&#39;aggiornamento dell&#39;area geografica o del codice postale. La mutazione ora aggiorna correttamente le imposte applicate quando si cambia tra i valori di area e codice postale, garantendo che venga applicata solo la regola fiscale corretta in base ai dati del carrello correnti.
* _LYNX-420_: l&#39;attributo is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;attributo is_available in CartItemInterface restituiva erroneamente true anche quando le scorte vendibili erano inferiori alla quantità di prodotto richiesta. Il campo is_available ora restituisce correttamente false quando la quantità del prodotto supera le scorte disponibili.
* _LYNX-421_: impossibile aggiungere il coupon al carrello per lo sconto solo spedizione
   * _Correzione nota_: è stato risolto un problema che impediva l&#39;applicazione di un coupon a un carrello per gli sconti solo per la spedizione. Il coupon viene ora applicato correttamente all’importo di spedizione quando si utilizza una regola di vendita senza condizioni di prodotto, garantendo l’applicazione dello sconto previsto alle spese di spedizione.
* _LYNX-425_: prezzo regolare del prodotto con 12 decimali e valore errato
   * _Correzione nota_: è stato risolto un problema a causa del quale il valore regular_price nei percorsi GraphQL product.price_range.maximum_price e minimum_price non corrispondeva al prezzo del catalogo quando venivano applicate più aliquote fiscali. Il prezzo_regolare ora riflette in modo coerente il prezzo di catalogo in tutte le configurazioni di imposta, garantendo prezzi unitari accurati, calcoli del costo totale di riga e assegni di sconto nel Riepilogo carrello.
* _LYNX-430_: errore del server GraphQL nel carrello con prodotto in bundle esaurito
   * _Correzione nota_: è stato risolto un problema a causa del quale GraphQL restituiva un errore interno del server durante il recupero di un carrello contenente un prodotto in bundle con un elemento esaurito, in particolare quando la query includeva la proprietà itemsV2. GraphQL ora restituisce correttamente un elenco di elementi con messaggi di errore pertinenti associati alla voce dell’elemento del prodotto nel pacchetto, come previsto.
* _LYNX-441_: impossibile creare un indirizzo con attributi personalizzati
   * _Correzione nota_: è stato risolto un problema relativo alla mutazione createCustomerAddress che impediva la creazione di indirizzi con attributi personalizzati obbligatori. La mutazione ora gestisce correttamente gli attributi degli indirizzi personalizzati quando viene fornito il payload appropriato.
* _LYNX-447_: errore del server GraphQL nel carrello con only_x_left_in_stock nel prodotto incluso
   * _Correzione nota_: è stato risolto un problema che causava un errore interno del server quando si recuperava un carrello contenente un prodotto in bundle con il campo only_x_left_in_stock nella query di GraphQL. GraphQL ora restituisce correttamente un valore float o null per il campo only_x_left_in_stock senza errori.
* _LYNX-464_: errore GraphQL durante la rimozione di altri prodotti con prodotto configurabile insufficiente nel carrello
   * _Correzione nota_: è stato risolto un problema a causa del quale il tentativo di rimuovere dal carrello i prodotti in magazzino causava un errore di GraphQL di tipo &quot;La quantità richiesta non è disponibile&quot; se il carrello conteneva anche prodotti configurabili con scorte insufficienti. La rimozione ora funziona come previsto senza errori di attivazione.
* _LYNX-469_: impossibile aggiungere prodotti perché la mutazione SKU fa distinzione tra maiuscole e minuscole
   * _Correzione nota_: è stato risolto un problema a causa del quale la mutazione addProductsToCart restituiva un errore &quot;PRODUCT_NOT_FOUND&quot; quando si utilizzavano SKU con maiuscole e minuscole diverse. La mutazione ora gestisce gli SKU senza distinzione tra maiuscole e minuscole, garantendo la coerenza con le query di Catalog Service e il comportamento PDP.
* _LYNX-603_: l&#39;attributo del prodotto > ™ del formato breve del marchio registrato viene restituito come ™
   * _Correzione nota_: è stato risolto un problema di codifica dei caratteri relativo al nome del prodotto per l&#39;API GraphQL
* _LYNX-619_: problema di mutazione updateCustomerEmail
   * _Correzione nota_: è stato risolto un problema relativo alla mutazione updateCustomerEmail a causa del quale i clienti che non disponevano degli attributi personalizzati richiesti (aggiunti dopo la creazione dell&#39;account) non potevano aggiornare l&#39;e-mail.
* _LYNX-626_: Mutation setShippingAddressesOnCart genera un errore quando si utilizza pickup_location_code
   * _Correzione nota_: è stato risolto un problema a causa del quale la mutazione setShippingAddressesOnCart restituiva un errore quando si utilizzava pickup_location_code senza specificare customer_address_id o address. La mutazione ora consente correttamente di impostare un indirizzo di spedizione con solo il codice pickup_location_code.
* _LYNX-627_: l&#39;elenco CustomerOrder.items_idonee_for_return deve essere coerente con gli elementi dell&#39;ordine
   * _Correzione nota_: sono state risolte incoerenze con l&#39;idoneità alla restituzione negli ordini:
1. L&#39;elenco CustomerOrder.items_idonea_for_return è ora coerente con gli articoli dell&#39;ordine effettivi.
2. Il campo OrderItemInterface.idonea_per_return restituisce correttamente false quando è già stata restituita la quantità completa.
3. CustomerOrder.items_idonea_for_return ora include solo gli articoli che non sono già in fase di restituzione.
* _LYNX-628_: aggiungere il campo quantity_return_requested
   * _Correzione nota_: il campo quantity_return_requested è stato aggiunto all&#39;interfaccia OrderItemInterface per consentire di identificare la quantità di articoli per i quali è stata inviata una restituzione. In questo modo viene migliorata la registrazione dei resi insieme al campo quantity_returned esistente.
* _LYNX-634_: le azioni disponibili per l&#39;ordine non devono contenere la restituzione dopo le restituzioni create per tutti gli articoli nella quantità completa
   * _Correzione nota_: è stato risolto un problema a causa del quale il campo available_actions nella query customer.orders di GraphQL includeva erroneamente la funzione RESTITUISCI dopo la creazione di una restituzione completa per tutti gli elementi. L’azione RETURN viene ora rimossa correttamente al termine del processo di restituzione.
* _LYNX-637_: Compatibilità Storefront - Logica di aggiornamento per ottenere il nome della tabella con prefisso e altri miglioramenti minori
   * _Correzione nota_: logica aggiornata per recuperare il nome della tabella con il prefisso (relativo alle modifiche SCP).
* _LYNX-643_: il salvataggio nella rubrica non funziona quando si utilizza il campo same_as_shipping di setBillingAddressOnCart GQL
   * _Correzione nota_: è stato risolto un problema a causa del quale l&#39;indirizzo di spedizione non veniva salvato nella rubrica del cliente quando si utilizzava la mutazione GraphQL setBillingAddressOnCart con il campo same_as_shipping impostato su true. Ora l&#39;indirizzo di spedizione viene memorizzato correttamente come previsto.
* _LYNX-650_: standardizzare order_id nelle mutazioni
   * _Correzione nota_: l&#39;input order_id è stato standardizzato nelle mutazioni e il modello e-mail di conferma dell&#39;annullamento dell&#39;ordine è stato aggiornato in modo da esporre l&#39;ID incremento invece dell&#39;ID ordine.
* _LYNX-651_: CustomerOrder non visualizza i commenti dell&#39;ordine
   * _Correzione nota_: è stato risolto un problema relativo a CustomerOrder per includere i commenti degli ordini nelle query GraphQL per gli ordini dei clienti e dei clienti.
* _LYNX-652_: original_item_price non deve includere alcuno sconto
   * _Correzione nota_: è stata aggiornata la logica per original_item_price nei prezzi degli articoli del carrello di GraphQL per escludere gli sconti.
* _LYNX-681_: i prodotti del bundle mostrano ancora &quot;IN_STOCK&quot; quando uno dei suoi prodotti del bundle è esaurito
   * _Correzione nota_: è stato risolto un problema a causa del quale product.stock_status per i prodotti bundle mostrava ancora &quot;IN_STOCK&quot; anche quando uno degli elementi inclusi nel bundle era esaurito.
* _LYNX-686_: la query del cliente restituisce un errore server interno se per un cliente esiste un valore per l&#39;attributo personalizzato eliminato
   * _Correzione nota_: è stato risolto il problema a causa del quale la query del cliente restituiva un errore interno del server quando un attributo personalizzato eliminato presentava ancora un valore memorizzato. Ora, se viene richiesto un attributo non esistente, viene restituito un messaggio di errore corretto. La cache necessaria viene invalidata al momento dell’eliminazione dell’attributo personalizzato del cliente.
* _LYNX-687_: Parametro azione per i collegamenti di conferma di restituzione e annullamento
   * _Correzione nota_: è stato aggiunto il parametro Azione per i collegamenti correlati all&#39;e-mail di conferma per la restituzione e l&#39;annullamento
* _LYNX-688_: l&#39;URL di conferma dell&#39;utente ospite viene reindirizzato alla pagina di stato dell&#39;ordine perché manca orderRef (per GuestRMA)
   * _Correzione nota_: è stato aggiunto il parametro orderRef al collegamento nell&#39;e-mail di conferma RMA guest
* _LYNX-689_: l&#39;URL di conferma dell&#39;utente ospite viene reindirizzato alla pagina di stato dell&#39;ordine perché manca orderRef
   * _Correzione nota_: è stato aggiunto il parametro orderRef al collegamento nell&#39;e-mail di conferma per l&#39;annullamento dell&#39;ordine ospite
* _LYNX-690_: problemi con la query del cliente quando RMA è disabilitato
   * _Correzione nota_: è stata aggiornata la logica di GraphQL per garantire che le restituzioni create in precedenza rimangano accessibili anche quando RMA è disabilitato a livello globale. Il messaggio di errore è stato rimosso per migliorare l’interfaccia utente di storefront, consentendo ai clienti di visualizzare ancora i resi passati.
* _LYNX-696_: GraphQL non restituisce i dati del carrello aggiornati quando vengono applicati coupon in conflitto
   * _Correzione nota_: è stato risolto un problema che causava la visualizzazione di un messaggio di errore in seguito all&#39;applicazione di un coupon in conflitto con priorità più elevata senza la restituzione dei dati del carrello aggiornati. Ora, quando un nuovo coupon invalida quello esistente, la mutazione restituisce correttamente il carrello con il coupon valido applicato.
* _LYNX-699_: impossibile restituire null per il campo &quot;TaxItem.title&quot; non nullable in placeOrder GQL
   * _Correzione nota_: è stato corretto un problema a causa del quale la mutazione placeOrder non riusciva e si verificava un errore interno del server a causa di un valore null per il campo TaxItem.title non nullable. Ora, il campo restituisce sempre un valore valido, garantendo il corretto inserimento dell’ordine.
* _LYNX-702_: EstimateTotals: gli sconti sono nulli per i tipi di prodotto virtuali
   * _Correzione nota_: è stato risolto il problema a causa del quale la mutazione estimateTotals restituiva valore null per gli sconti quando un codice sconto veniva applicato a un carrello contenente prodotti virtuali.
* _LYNX-703_: il prodotto del bundle non restituisce la percentuale e l&#39;importo di sconto corretti
   * _Nota sulla correzione_: sono state introdotte nuove proprietà &quot;catalog_discount&quot; e &quot;row_catalog_discount&quot; affinché i prezzi degli articoli del catalogo visualizzino gli importi e le percentuali di sconto corretti sia a livello di riga che a livello di singolo articolo.
* _LYNX-714_: configurazione messaggio regalo a livello di prodotto
   * _Correzione nota_: è stato risolto un problema a causa del quale i messaggi regalo non venivano applicati a livello di prodotto se disabilitati a livello globale. Ora, se i messaggi regalo sono abilitati per un prodotto specifico, possono essere aggiunti correttamente utilizzando la mutazione updateCartItems e verranno salvati e riflessi correttamente.
* _LYNX-717_: problema con la rimozione della confezione regalo dall&#39;elemento del carrello
   * _Correzione nota_: è stato risolto il problema che impediva la rimozione della confezione regalo da un elemento del carrello utilizzando la mutazione updateCartItems. Ora, sia l&#39;applicazione che la rimozione di confezione regalo funzionano correttamente senza errori.
* _LYNX-751_: la funzionalità del cliente registrato corrispondente non funziona in Boilerplate e la mutazione trackViewedProduct deve essere abilitata per gli ospiti.
   * _Correzione nota_: è stata esposta la mutazione trackViewedProduct per tenere traccia dell&#39;evento di visualizzazione prodotto per clienti e ospiti
* _LYNX-757_: la query cart.rules restituisce un errore invece di un array vuoto se non vengono applicate regole attive del carrello
   * _Correzione nota_: la query cart.rules è stata corretta in modo da restituire un array vuoto anziché un errore quando non vengono applicate regole del carrello attive.
* _LYNX-758_: problema durante il recupero delle confezioni regalo per gli elementi del carrello
   * _Correzione nota_: è stata aggiornata la logica di recupero per restituire le opzioni di confezione regalo per gli elementi del carrello quando è disabilitata a livello globale ma abilitata a livello di prodotto
* _LYNX-778_: le chiamate di GraphQL con il metodo OPTIONS restituiscono il codice di risposta 500 quando è installato il pacchetto di compatibilità adobe-commerce/storefront
   * _Correzione di una nota_: è stato risolto un problema a causa del quale le chiamate di GraphQL eseguite con il metodo OPTIONS restituivano un errore interno del server 500 quando è stato installato il pacchetto di compatibilità adobe-commerce/storefront-compatibility. L’endpoint ora restituisce correttamente una risposta 200/204 come previsto.

### Altri strumenti per sviluppatori

* _AC-10658_: [Problema] Correggere l&#39;errore di sintassi HTML in visual.phtml
   * _Correzione nota_: il sistema ora chiude correttamente il tag di inizio nel file visual.phtml, garantendo la sintassi HTML corretta. In precedenza, il tag di inizio non veniva chiuso correttamente, causando un errore di sintassi HTML.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38247>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problema] cambiato &quot;attivo&quot; in &quot;abilitato&quot; nel comando bin/magento maintenance:status
   * _Correzione nota_: il sistema ora fornisce messaggi di stato più precisi per il comando della modalità di manutenzione, cambiando lo stato da &quot;attivo&quot; a &quot;abilitato&quot; e da &quot;non attivo&quot; a &quot;disabilitato&quot;. In precedenza, il messaggio di stato per il comando della modalità di manutenzione veniva visualizzato come &quot;attivo&quot; o &quot;non attivo&quot;, il che poteva creare confusione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38486>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: la navigazione nella struttura delle categorie genera errori in Redis: &quot;La sessione Redis ha superato le connessioni simultanee&quot;
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38851>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0611e750>
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
* _ACP2E-3631_: errore degli unit test di Adobe Commerce 2.4.7-p3
   * _Nota di correzione_: non sono richieste note sulla versione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Metodi di pagamento, ordine

* _AC-13699_: i dettagli della carta di credito papale salvati per un uso successivo non vengono visualizzati nella pagina del metodo di pagamento memorizzata
   * _Nota sulla correzione_: i dettagli della carta di credito papale salvati in precedenza per un uso successivo non venivano visualizzati nella pagina del metodo di pagamento memorizzata, che ora è impostata come dettagli della carta di credito fissa, vengono visualizzati nella pagina del metodo di pagamento memorizzato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/96dec499>

### Pagamenti

* _AC-13414_: pagamento con carta di credito (collegamento payflow) non funzionante
   * _Correzione nota_: in precedenza si verificava un errore (pagamento rifiutato) durante l&#39;inserimento dell&#39;ordine con carta di credito dopo la correzione dell&#39;ordine.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: il flusso di pagamento crea una nuova transazione ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione
   * _Correzione nota_: il sistema ora recupera correttamente le informazioni sulla transazione senza creare una nuova transazione di pagamento ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione. In precedenza, facendo clic sul pulsante Recupera, veniva erroneamente creata una nuova transazione di pagamento per un ordine già pagato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: il messaggio Paylater non viene visualizzato in PDP per l&#39;account commerciante paypal canadese
   * _Nota sulla correzione_: il sistema ora visualizza correttamente il messaggio PayLater per gli account esercente PayPal canadesi nella pagina Dettagli prodotto (PDP) quando il paese dell&#39;acquirente può essere determinato dall&#39;indirizzo di fatturazione o dalla spedizione del conto. In precedenza, il messaggio PayLater non veniva visualizzato a causa di un parametro mancante, causando un errore nella console del browser.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
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
* _AC-12000_: [Problema] Pulizia del codice, aggiunta di un nuovo blocco di intestazione critico e spostamento di CSS critico prima delle risorse
   * _Correzione nota_: il sistema ora include un nuovo blocco di intestazione critico e sposta CSS critico prima delle risorse, consentendo una maggiore personalizzazione e ottimizzazione delle prestazioni nel front-end. In precedenza, il CSS critico non veniva posizionato prima delle risorse, limitando le opportunità di personalizzazione e ottimizzazione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: la compilazione del tema si interrompe quando l&#39;host Mysql contiene informazioni sulla porta
   * _Correzione nota_: il sistema ora gestisce correttamente la configurazione host MySQL che include le informazioni sulla porta, garantendo la corretta compilazione del tema. In precedenza, la compilazione del tema non riusciva se la configurazione host MySQL nella connessione al database includeva informazioni sulla porta.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38799>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: supporto per CommandLoaderInterface di Symfony in Magento CLI
   * _Correzione nota_: questa modifica riduce il tempo di inizializzazione dell&#39;app Magento CLI consentendo l&#39;inizializzazione differita dei comandi fino a quando non sono necessari.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29266>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: problema di prestazioni durante il caricamento degli attributi del prodotto nelle regole del carrello
   * _Correzione nota_: sono state migliorate le prestazioni delle query per le regole di vendita, da circa 150 ms a ms a una cifra.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: prestazioni di indicizzazione parziale del prezzo
   * _Correzione nota_: le prestazioni di indicizzazione parziale del prezzo sono state migliorate ottimizzando alcune delle query di eliminazione utilizzate nel processo di indicizzazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: l&#39;ordine viene rifiutato nella configurazione di più store quando si utilizza l&#39;elaborazione asincrona dell&#39;ordine + Termini e condizioni
   * _Correzione nota_: gli ordini effettuati da siti Web non predefiniti con termini e condizioni abilitati vengono ora elaborati.
Prima che venissero automaticamente rifiutati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: l&#39;esecuzione della chiamata API per il resto dell&#39;ordine richiede molto tempo
   * _Correzione nota_: il sistema ora esegue la chiamata API per il resto dell&#39;ordine in un lasso di tempo ragionevole, migliorando le prestazioni quando si recupera un numero elevato di ordini. In precedenza, l’esecuzione della chiamata API per il resto dell’ordine impiegava molto tempo, causando ritardi durante il recupero di un numero elevato di ordini.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/001e5188>

### Prestazioni, Promozione

* _ACP2E-2617_: l&#39;esecuzione dell&#39;indicizzatore della regola di vendita è stata interrotta
   * _Correzione nota_: l&#39;indicizzatore della regola di vendita è stato completato correttamente dal sistema anche con un numero elevato di gruppi di filtri combinati, in modo che le condizioni della regola del carrello vengano applicate al carrello come previsto. In precedenza, l’indicizzatore della regola di vendita non veniva completato quando si registrava un numero elevato di gruppi di filtri combinati, generando un messaggio di errore e impedendo l’applicazione delle condizioni della regola del carrello.

### Prezzi

* _AC-11810_: Magento2.4.6-p4 Ordina API Articolo semplice prezzo mancante
   * _Correzione nota_: il sistema ora visualizza correttamente il prezzo dei prodotti semplici quando viene eseguita una query tramite l&#39;API dell&#39;ordine, garantendo una rappresentazione accurata dei dati. In precedenza, il prezzo dei prodotti semplici veniva erroneamente visualizzato come zero nella risposta API.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: errore di arrotondamento in centesimi nella regola del catalogo
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/276e0acd>

### Prodotto

* _AC-10535_: i caratteri speciali nel nome configurabile del prodotto associato vengono convertiti in entità HTML.
   * _Correzione nota_: il sistema ora mantiene correttamente i caratteri speciali nei nomi dei prodotti associati durante la modifica di un prodotto configurabile, impedendo che vengano convertiti in entità HTML. In precedenza, i caratteri speciali nei nomi dei prodotti associati venivano convertiti in entità HTML quando il prodotto configurabile veniva modificato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38146>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: la funzione ProductRepository GetById non crea la chiave cache corretta
   * _Correzione nota_: il sistema ora crea correttamente una chiave cache nella funzione GetById del ProductRepository, indipendentemente dal fatto che l&#39;ID archivio venga passato come stringa o come numero intero. In questo modo il prodotto viene recuperato dalla memoria nelle chiamate successive, migliorando le prestazioni. In precedenza, il sistema recuperava il prodotto dal database ogni volta che la funzione veniva chiamata, anche con gli stessi parametri, a causa di una creazione errata della chiave della cache.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38384>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Problema] [MFTF] Aggiunto AdminClickAddOptionForBundleItemsActionGroup
   * _Correzione nota_: il sistema ora include AdminClickAddOptionForBundleItemsActionGroup, migliorando le funzionalità del pannello di amministrazione. In precedenza, questo gruppo di azioni non era disponibile.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/30857>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/30838>
* _AC-13173_: [Problema] Correzione dell&#39;errore di battitura nel blocco PHPDoc
   * _Correzione nota_: il sistema ora rimuove correttamente una variabile di riferimento sconosciuta in PHPDoc per la dichiarazione della variabile $helper, migliorando la chiarezza e la precisione del codice. In precedenza, questa variabile di riferimento sconosciuta in PHPDoc causava confusione e potenziali imprecisioni nel codice.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38961>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] è stato corretto il bundle interrotto e il layout delle pagine di prodotto scaricabili in Magento >= 2.4.7
   * _Correzione nota_: il layout per il bundle e le pagine di prodotto scaricabili è stato corretto, garantendo una visualizzazione coerente e corretta su tutti i dispositivi. In precedenza, in queste pagine si verificavano problemi di layout a causa di una ridisposizione del blocco multimediale di informazioni sul prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Il #2 dell&#39;argomento ($storeId) deve essere di tipo int, stringa specificata
   * _Correzione nota_: il sistema ora attiva correttamente le e-mail di avviso sul prodotto verificando che l&#39;identificatore dell&#39;archivio sia del tipo di dati corretto. In precedenza, le e-mail di avviso sul prodotto non venivano inviate a causa di una mancata corrispondenza del tipo nell’identificatore dello store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35602>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [La funzione addFilterToMap del cloud] non funziona per alcune colonne
   * _Correzione nota_: ora è possibile utilizzare il modulo personalizzato nella griglia dell&#39;ordine. Errori precedenti durante l’utilizzo di un modulo personalizzato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3471_: [Cloud] Prodotti nella categoria - Aggiungi prodotti - Assegna - Seleziona tutto
   * _Correzione nota_: gli utenti possono ora selezionare o deselezionare i prodotti utilizzando l&#39;interruttore.

### Promozione

* _ACP2E-2602_: attributo cliente non visibile durante la creazione dell&#39;account dall&#39;invito
   * _Correzione nota_: gli attributi del cliente sono disponibili durante la creazione dell&#39;account da un invito.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: il codice coupon con limite Usi per coupon non viene rilasciato per il pagamento non riuscito con annullamento ordine
   * _Correzione nota_: il sistema aggiorna immediatamente gli utilizzi dei coupon quando un ordine viene creato o annullato e aggiunge gli utilizzi delle regole a una coda per evitare potenziali deadlock. In questo modo, viene rilasciato un codice coupon con un limite &quot;Usi per coupon&quot; che può essere riutilizzato in caso di annullamento di un ordine a causa di un pagamento non riuscito. In precedenza, il sistema non rilasciava il codice coupon per il riutilizzo in tali casi, causando un messaggio di errore che indicava che il codice coupon non era valido.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] L&#39;indicizzatore di prodotto della regola del catalogo di reindicizzazione genera SQLSTATE[HY000]: errore generale: il server MySQL 2006 non è più disponibile.
   * _Correzione nota_: il sistema ora gestisce correttamente il valore &quot;batchCount&quot; personalizzato nel file di.xml per &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, impedendo errori SQL quali &quot;Errore generale: il server MySQL 2006 non è più disponibile&quot; durante la reindicizzazione dell&#39;indicizzatore del prodotto della regola catalogo a causa delle dimensioni non corrette del batch in cataloghi di grandi dimensioni
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_: [CLOUD]Regola prezzo carrello per visitatori segmento clienti non applicando lo sconto sul carrello
   * _Correzione nota_: il sistema ora applica correttamente le regole di prezzo del carrello per i segmenti cliente dei visitatori, anche se la regola non utilizza un coupon, assicurandosi che al carrello vengano applicati gli sconti appropriati. In precedenza, gli sconti non venivano applicati al carrello per i segmenti dei clienti visitatore, a meno che la regola del prezzo del carrello non utilizzasse un coupon.
* _ACP2E-3024_: attributo &quot;Type&quot; mancante nella scheda &quot;Products to Match&quot; delle regole prodotto correlate
   * _Nota corretta_: l&#39;attributo &quot;Type&quot; è ora disponibile come opzione di filtro nella scheda &quot;Products to Match&quot; del modulo &quot;Related Product Rules&quot;, consentendo una definizione più precisa della regola. In precedenza, questo attributo mancava dalla scheda &quot;Products to Match&quot; (Prodotti da abbinare), limitando la possibilità di creare criteri di corrispondenza accurati.
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
* _ACP2E-3472_: [CLOUD] Il calcolo della spedizione non considera la regola del carrello acquisti
   * _Nota sulla correzione_: prima della correzione, una regola del carrello con condizione di area non veniva applicata in modo coerente. Dopo la correzione, le regole del carrello con condizioni di area vengono applicate correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: la condizione dello SKU della regola del carrello non riesce per la fattura.
   * _Nota di correzione_: lo sconto sul prodotto del bundle con prezzo dinamico ora viene riportato correttamente nella fattura. In precedenza, lo sconto non veniva riportato sulla fattura.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: valore di sconto errato quando più regole di prezzo del carrello vengono applicate contemporaneamente a prodotti scontati/a prezzi speciali
   * _Nota sulla correzione_: prima della correzione, l&#39;importo fisso per le regole dell&#39;intero carrello non veniva applicato correttamente se ne veniva applicato più di uno. Ora, le regole del carrello sconti per importo fisso vengono applicate correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Restituisce

* _ACP2E-3330_: [CLOUD] Gli utenti amministratori con restrizioni possono visualizzare il menu e i pulsanti restituiti
   * _Correzione nota_: gli utenti amministratori con restrizioni ora non hanno accesso ai controlli relativi a RMA (menu e pulsanti).
Gli utenti amministratori con restrizioni precedenti potevano visualizzare il menu e i pulsanti di ritorno.
* _ACP2E-3443_: la schermata di ritorno è incasinata quando si aggiorna la schermata
   * _Correzione nota_: l&#39;utente può aggiornare la pagina senza che si verifichi una distorsione dello schermo.

### SEO

* _AC-11907_: l&#39;aggiunta di riscritture URL con un accento causa un caricamento infinito
   * _Correzione nota_: il sistema ora crea e funziona l&#39;URL riscrive con accenti, impedendo il caricamento infinito durante il processo di salvataggio. In precedenza, l’aggiunta della riscrittura di un URL con un accento causava un problema di caricamento infinito.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38692>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: riscrittura URL di categoria errata in più store per la categoria di terzo livello
   * _Correzione nota_: genera riscritture URL corrette per gli elementi figlio con chiave URL con ambito personalizzato
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: i caratteri a doppio byte (caratteri speciali) nel campo Nome prodotto bloccano la creazione del prodotto nel back-end
   * _Correzione nota_: è stata aggiunta una nuova impostazione che consente di applicare o meno la traslitterazione all&#39;URL del prodotto. L’impostazione è disponibile qui: Negozi > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca: &quot;Applica traslitterazione per URL prodotto&quot;
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: creazione di voci url_rewrite non corretta con più archivi in un unico gruppo di archivi
   * _Nota sulla correzione_: prima della correzione, era possibile generare riscritture URL solo a livello di sito Web durante la modifica di un prodotto. Con la correzione, è stata introdotta una nuova impostazione (Stores > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca, &quot;URL prodotto - Ambito di riscrittura&quot; con opzioni &quot;Visualizzazione archivio&quot;, &quot;Sito web&quot;) che consente di generare riscritture URL a livello di visualizzazione archivio o sito web.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/2d627301>

### Vendite

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

* _AC-11855_: [Problema] Popup Font CSP Paylater mancante
   * _Correzione nota_: il sistema ora consente il caricamento del tipo di carattere &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; senza violare la direttiva Content Security Policy, garantendo la corretta visualizzazione del popup Paylater. In precedenza, il caricamento del font veniva rifiutato a causa di una violazione della direttiva Content Security Policy, causando problemi di visualizzazione con il Popup Paylater.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Problema] Aggiornamento del testo DOM js.js reinterpretato come HTML
   * _Correzione nota_: l&#39;utilizzo di innerText evita il rischio di inserimento di HTML, poiché queste proprietà eliminano automaticamente qualsiasi carattere speciale HTML nel testo fornito. Questa correzione, aiuta a prevenire le vulnerabilità cross-site scripting (XSS) trattando l’input come testo normale anziché come HTML interpretato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 non viene visualizzato correttamente al momento dell&#39;estrazione per la lingua tedesca
   * _Correzione nota_: in precedenza i recaptcha da sotto l&#39;indirizzo e-mail da checkout venivano visualizzati in modo non stilizzato per le lingue con parole lunghe, come il tedesco. Dopo questo il recaptcha si presenta come tutti gli elementi recaptcha dal resto delle aree.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha all&#39;accesso amministratore non richiede interazione per alcuni utenti
   * _Correzione nota_: ReCaptcha per l&#39;accesso amministratore è stato convalidato come previsto
   * _Contributo codice GitHub_: <https://github.com/magento/security-package/commit/8f64ab3c>

### Spedizione

* _AC-10757_: [Problema] È stato corretto un errore di battitura in tracking.phtml - le funzioni JS sono state rinominate &quot;currier&quot; in &quot;carrier&quot;
   * _Correzione nota_: il sistema ora utilizza correttamente il termine &quot;carrier&quot; invece del &quot;currier&quot; errato nelle funzioni del gestore JavaScript utilizzate nel modello di tracciamento degli ordini, garantendo la corretta denominazione delle funzioni e la chiarezza del codice. In precedenza, veniva utilizzato il termine errato &quot;currier&quot;, che portava a una potenziale confusione e incoerenza nella base di codice.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;Una spedizione non può avere come unità di misura KGS/IN, LBS/CM o OZS/CM&quot;
   * _Correzione nota_: assicurarsi che le tariffe UPS siano visibili nel carrello e nell&#39;estrazione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38618>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-12938_: aggiornamenti delle istruzioni di installazione REST &quot;sandbox&quot; e &quot;prod&quot; di UPS in devdoc
* _AC-13172_: [Problema] Correggere l&#39;ortografia delle variabili per l&#39;indirizzo del cliente
   * _Correzione nota_: il sistema ora scrive correttamente le variabili per gli indirizzi dei clienti, garantendo una visualizzazione accurata nell&#39;area account del front-end. In precedenza, l’ortografia errata di queste variabili poteva causare errori durante le revisioni del codice locale.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32817>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: la finestra di tracciamento mostra una data di consegna prevista errata
   * _Correzione nota_: visualizza la data di consegna corretta per il gestore Fedex.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Le Tariffe Della Tabella Continuano A Essere Visualizzate Anche Se È Applicata La Spedizione Gratuita
   * _Correzione nota_: il metodo di spedizione delle tariffe della tabella viene visualizzato anche se la spedizione gratuita diventa disponibile dopo l&#39;applicazione del coupon
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: test MFTF AdminCreatingShippingLabelTest non riuscito a causa di credenziali non aggiunte nell&#39;ambiente Jenkins
   * _Correzione nota_: correzione test mftf
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: l&#39;API Track FedEx non funziona con le credenziali REST
   * _Correzione nota_: in precedenza l&#39;integrazione FedEx non richiedeva chiavi API aggiuntive per l&#39;API di tracciamento. Ora è stata aggiunta una nuova configurazione per supportare le chiavi API di tracciamento.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Cloud] tariffe negoziate FedEx non restituite su REST
   * _Nota sulla correzione_: prima della correzione, le tariffe specifiche dell&#39;account FedEx non venivano inviate nella risposta, anche se in base alla documentazione FedEx dovevano essere state inviate. Dopo la correzione, i tassi specifici dell’account vengono inviati alla risposta modificando la richiesta dal nostro lato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Staging e anteprima

* _ACP2E-2901_: le impostazioni di aggiornamento pianificato non vengono salvate se originariamente aggiunte eseguendo l&#39;aggiornamento
   * _Correzione nota_: il sistema ora cancella correttamente i valori degli attributi del prodotto negli aggiornamenti pianificati successivi quando tali attributi vengono modificati nell&#39;aggiornamento in esecuzione. In precedenza, quando un attributo di prodotto veniva modificato da un aggiornamento pianificato in esecuzione, non era possibile cancellare tali valori durante la creazione di un nuovo aggiornamento pianificato, richiedendo all’utente di modificarli nuovamente dopo la creazione.
* _ACP2E-2999_: la regola del prezzo del carrello dalla data e fino alla data non è sincronizzata con l&#39;aggiornamento della gestione temporanea
   * _Nota di correzione_: le date vengono salvate in base agli aggiornamenti per la gestione temporanea delle regole di prezzo del carrello.
* _ACP2E-3104_: errore JS nell&#39;anteprima di staging
   * _Correzione nota_: ora il file form-mini-stub.js viene caricato correttamente senza errori di sintassi Js negli strumenti di sviluppo.
* _ACP2E-3162_: impossibile aggiornare il contenuto di staging del prezzo speciale del prodotto
   * _Correzione nota_: il sistema ora consente di modificare la data di fine di una campagna di aggiornamento dei prezzi dopo l&#39;avvio, in modo che gli utenti possano apportare le modifiche necessarie alle campagne. In precedenza, veniva generato un errore durante il tentativo di aggiornare la data di fine di una campagna attiva, impedendo agli utenti di apportare modifiche.
* _ACP2E-3453_: impossibile aggiornare l&#39;aggiornamento pianificato quando si utilizza un attributo di categoria personalizzato univoco
   * _Correzione nota_: è stato risolto un problema che impediva l&#39;aggiornamento pianificato di una categoria se questa aveva un attributo univoco
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Targeting

* _AC-9432_: [Problema] Consente l&#39;utilizzo di intervalli CIDR nell&#39;elenco consentiti di manutenzione
   * _Correzione nota_: il sistema ora supporta l&#39;utilizzo di intervalli CIDR nell&#39;elenco Consenti elenco indirizzi IP in modalità di manutenzione, consentendo a un intervallo di indirizzi IP di ignorare la modalità di manutenzione. In precedenza, la modalità di manutenzione Consenti elenco IP consentiva solo a singoli indirizzi IP di ignorare la modalità di manutenzione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37943>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/30699>

### Imposta

* _AC-13295_: [Problema] Promozione proprietà costruttore funzionalità/php8.1 ql grafico wee
   * _Correzione nota_: sostituire quasi tutte le proprietà con la promozione delle proprietà del costruttore nel modulo wee graph ql:
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39309>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: l&#39;FPT (Fixed Product Tax) non funziona con i prodotti configurabili
   * _Correzione nota_: FPT per il corretto funzionamento delle varianti di prodotto configurabili.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Framework di test

* _AC-11654_: test di integrazione non riuscito in testDbSchemaUpToDate a causa del tipo di colonna JSON
   * _Correzione nota_: il sistema ora riconosce correttamente i tipi di colonna JSON nello schema del database durante gli integration test, evitando errori di test a causa di una mancata corrispondenza tra lo schema del database e lo schema dichiarativo. In precedenza, il sistema identificava erroneamente i tipi di colonna JSON come LONGTEXT in MariaDB, causando l’errore dei test di integrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Problema] Controllo ortografico della correzione PHPDoc
   * _Correzione nota_: il sistema ora riconosce correttamente i metodi obsoleti negli IDE a causa di una correzione ortografica nel PHPDoc. In precedenza, un errore ortografico nel PHPDoc causava il mancato riconoscimento da parte degli IDE di alcuni metodi come obsoleti.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/31399>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: controllo del comportamento con il carrello permanente dopo la scadenza della sessione
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: test di integrazione non riusciti Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_: [Database Compare] Errore irreversibile se il database contiene record relativi alla regola di destinazione senza condizioni
   * _Correzione nota_: in precedenza, se il database contiene record sulla regola di destinazione senza alcuna condizione, si verificavano errori irreversibili ma dopo che lo strumento Correggi confronto database è stato completato senza errori irreversibili.
* _AC-13848_: correggi i test statici per abilitare l&#39;utilizzo da parte di estensioni di terze parti
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [Errore interno] di applicazione della correzione non visualizzato durante l&#39;esecuzione o nei registri
   * _Correzione nota_: &#39;-
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest
   * _Correzione nota_: mftfs corretti
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Framework interfaccia utente

* _AC-12128_: correzione della vulnerabilità di sicurezza di Prototype.js CVE-2020-27511
   * _Correzione nota_: il sistema è stato aggiornato per risolvere la vulnerabilità di sicurezza CVE-2020-27511 in Prototype.js 1.7.3, migliorando la sicurezza complessiva del sistema. Prima di questo aggiornamento, il sistema era suscettibile a un’espressione regolare Denial of Service (ReDOS) attraverso la rimozione di tag HTML creati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less utilizza il prefisso pub/ per sourcemaps
   * _Correzione nota_: il sistema ora genera meno sourcemap/css senza il prefisso /pub per i percorsi quando si utilizza grunt, eliminando la necessità di una soluzione alternativa nella configurazione del server Web. In precedenza, l’utilizzo del prefisso /pub nei percorsi sourcemaps richiedeva una configurazione specifica nel server web per funzionare correttamente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38837>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38840>
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
* _AC-1306_: il contenuto statico è in distribuzione per i moduli disabilitati
   * _Correzione nota_: il sistema ora esclude i CSS relativi ai moduli disabilitati dai file di output CSS finali, garantendo che non vengano caricati stili non necessari. In precedenza, i CSS relativi ai moduli disattivati venivano inclusi nei file di output CSS finali, determinando il caricamento di stili aggiuntivi e non necessari.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/24666>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: comportamento incoerente nell&#39;ordinamento &quot;esaurito&quot; con soglia minima di stock
   * _Correzione nota_: il sistema ora ordina correttamente i prodotti nel catalogo in base ai livelli di stock, rispettando la soglia minima impostata e spostando in modo coerente gli elementi esauriti nella parte inferiore dell&#39;elenco. In precedenza, il comportamento di ordinamento era incoerente: gli elementi non venivano sempre visualizzati nell’ordine corretto in base ai livelli di stock e le modifiche nell’ordinamento potevano verificarsi in modo imprevedibile dopo il salvataggio, l’aggiornamento o la modifica della gerarchia di categorie.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: suggerimenti per migliorare la segnalazione degli errori per i problemi di caricamento di require.js
   * _Correzione nota_: questa PR migliora il messaggio di errore quando Requjs non riesce a caricare un componente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: errori di deprecazione di PHP 8.4 che causano errori di compilazione in 2.4-development
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Problema] Non caricare il contesto del blocco di back-end sul front-end
   * _Correzione nota_: il sistema ora garantisce che il contesto del blocco back-end non venga caricato sul front-end, impedendo la creazione di sessioni backend non necessarie e potenziali blocchi di sessione. In precedenza, il sistema caricava erroneamente il contesto del blocco back-end sul front-end, determinando la creazione di sessioni back-end e potenziali blocchi di sessione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Problema] Rimuovi riepilogo revisioni script non necessarie
   * _Correzione nota_: il sistema ora ottimizza il tempo di caricamento delle pagine rimuovendo gli script JavaScript non necessari dalla sezione di valutazione, invece di utilizzare gli stili CSS in linea per un codice più efficiente e leggibile. In precedenza, l’utilizzo di script JavaScript per la sezione di valutazione poteva potenzialmente rallentare il tempo di caricamento delle pagine.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: eccezione durante la verifica del saldo di una gift card quando Recaptcha è abilitato
   * _Correzione nota_: gli utenti potranno recuperare il saldo della gift card nella schermata Visualizza e modifica carrello. In precedenza, questi dettagli non venivano visualizzati quando reCAPTCHA era abilitato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [CHIARIMENTO] Richiesta di funzionalità Conformità ADA
   * _Correzione nota_: il sistema ora garantisce la conformità ADA rimuovendo le proprietà CSS non supportate e sostituendole con quelle supportate nel file print.css. In precedenza, l’utilizzo di proprietà CSS non supportate causava problemi di compatibilità con il browser.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Codice libreria di confusione in effect-drop.js di AC 2.4.4-p8
   * _Correzione nota_: il sistema ora implementa correttamente la libreria effect-drop.js, garantendo il corretto funzionamento degli effetti dell&#39;interfaccia utente jQuery. In precedenza, la libreria effect-drop.js veniva erroneamente sovrascritta con la libreria effect-clip.js, causando potenziali problemi con gli effetti dell’interfaccia utente jQuery.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: intestazione sito | Caratteri speciali che interrompono la sezione di benvenuto del cliente
   * _Nota di correzione_: dopo la correzione, i caratteri speciali vengono visualizzati correttamente nella sezione di benvenuto del cliente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: l&#39;edizione del segmento cliente non riesce con l&#39;intervallo di dati
   * _Correzione nota_: è possibile salvare il segmento del cliente con la condizione Intervallo date quando è stata modificata solo una delle date.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>

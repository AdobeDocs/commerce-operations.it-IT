---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '27924'
ht-degree: 0%

---
# Problemi risolti in Adobe Commerce (v2.4.8)

## Problemi risolti nella versione v2.4.8

Sono stati risolti 581 problemi nel codice core di Adobe Commerce 2.4.8. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### /V1/transaction REST API restituisce un errore quando parent_txn_id = txn_id

Il sistema ora gestisce correttamente le transazioni dei concetti padre e figlio in cui l&#39;ID della transazione padre è uguale all&#39;ID della transazione, impedendo un ciclo infinito durante la query dell&#39;endpoint REST API /V1/transaction. In precedenza, questo scenario generava un errore irreversibile dovuto al superamento del tempo massimo di esecuzione.

_AC-10042 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### [Problema di tipo Graphql] in 2.4.7

Il sistema ora gestisce correttamente i valori interi nella funzione GetCustomSelectedOptionAttributes durante l&#39;esecuzione di una query GraphQL, evitando errori relativi al tipo. In precedenza, l&#39;avvio di una query GraphQL che utilizzava GetCustomSelectedOptionAttributes con un argomento Integer generava un errore di tipo.

_AC-11878 - [Problema GitHub](https://github.com/magento/magento2/issues/38662) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38663)_

#### Caratteri speciali nella categoria url_key (se creati tramite API REST)

Precedente In category_url_key il carattere speciale non è presente dopo la correzione in cui viene visualizzato in category_url_key

_AC-3223 - [Problema GitHub](https://github.com/magento/magento2/issues/35577) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### API REST che mostra gli ordini da un altro sito web. 

Il sistema ora supporta l’accesso autorizzato dell’ambito per i token di amministrazione dell’API REST e gli endpoint Magento_Sales, garantendo che l’API REST visualizzi solo gli ordini a cui l’amministratore ha accesso. In precedenza, l’API REST visualizzava gli ordini da tutti i siti web, indipendentemente dal sito web assegnato dall’utente amministratore.

_ACP2E-2703_

#### Problema con l’api rest dopo l’abilitazione di 2FA Duo

L’opzione di sicurezza 2FA con Duo genera ora la firma corretta per l’API Rest

_ACP2E-2755 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/412fa642)_

#### [REST API]: l&#39;utilizzo del valore predefinito nella vista Store non rimane controllato dopo l&#39;aggiunta di configurazioni per un prodotto configurabile

Il problema è stato risolto garantendo le voci di database corrette per le opzioni personalizzabili per un archivio non predefinito. La casella di controllo per l’archivio personalizzato nella sezione &quot;admin > Catalog > Product Edit > Customizable Options&quot; (Amministrazione > Catalogo > Modifica prodotto > Opzioni personalizzabili) era stata precedentemente deselezionata a causa di voci di database non accurate, anche se il titolo dell’opzione per l’archivio personalizzato rimaneva lo stesso dell’archivio predefinito.

_ACP2E-2927 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### API REST: impossibile effettuare richieste con barra (/) nello SKU quando si utilizza OAuth1

Prima della correzione, non era possibile effettuare una chiamata API per un prodotto con &quot;/&quot; nello SKU. Ora è possibile inviare una richiesta API per ottenere i dettagli del prodotto, anche se lo SKU contiene una barra.

_ACP2E-2969 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Aggiornamento dell’indirizzo del cliente non riuscito durante l’aggiornamento tramite API REST se &quot;validateDefaultAddress&quot; abilitato

L’endpoint API ora funziona come previsto dopo che il problema con la chiave ID mancante nel payload API è stato risolto.

_ACP2E-3079 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### [Cloud] Creazione del gruppo di clienti prezzi gruppo sito Web duplicato nell&#39;API prezzi livello.

Ora l’API Rest prezzo di livello non consente di creare il gruppo di clienti prezzo di gruppo del sito web duplicato.
In precedenza era possibile creare il gruppo di clienti prezzo gruppo sito web duplicato nell’API prezzi livello che non avrebbe superato la convalida in Amministratore durante il salvataggio del prodotto.

_ACP2E-3091 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Impossibile aggiungere il commento dell’ordine con stato tramite API REST

Il problema è stato risolto consentendo la modifica dello stato dell’ordine se proviene solo dallo stato corrente. In precedenza, non rispettava lo stato dell’ordine e impediva modifiche in qualsiasi stato dell’ordine, anche se proveniva dallo stesso stato.

_ACP2E-3130 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### L’operazione asincrona non riesce se manca lo SKU dal payload

Operazioni asincrone e di sincronizzazione non riuscite in precedenza a causa di errori di salvataggio del prodotto se lo SKU manca nel payload. Dopo la correzione, le operazioni dell’API rest di salvataggio del prodotto asincrono e sincrono non riescono e viene visualizzato il messaggio di eccezione pertinente.

_ACP2E-3236 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD] Impossibile aggiornare i prezzi base utilizzando l&#39;API REST (il valore di &#39;value_id&#39; in &#39;catalog_product_entity_decimal&#39; non viene incrementato correttamente).

In precedenza a questa correzione, quando veniva chiamato rest api /rest/default/V1/products/base-price, l’ID incremento veniva aumentato erroneamente, lasciando un gap tra i valori. Dopo la correzione l’ID incremento viene aumentato come previsto, in modo incrementale. Anche l’intervallo del campo value_id è stato aumentato.

_ACP2E-3376 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Gli elementi dell&#39;ordine non sono visibili nelle e-mail della nota di accredito per l&#39;API POST V1/order/:orderId/return

In precedenza, prima di questa correzione, quando un cliente crea una nota di credito da una richiesta API di notifica send_email, non contiene la griglia dei dettagli del prodotto. Dopo questa correzione, il cliente invia una richiesta API per la nota di credito e troverà i dettagli dell’elemento del prodotto che compaiono nell’e-mail.

_ACP2E-3460 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### I valori predefiniti non sono impostati per gli attributi di data e ora con i prodotti RestAPI

I valori predefiniti ora vengono impostati correttamente per gli attributi di data e data e ora tramite RestAPI

_ACP2E-3486 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### API, carrello e pagamento

#### Errore critico 500: Magento\Framework\Webapi\Exception relativo all&#39;intestazione HTTP Accept

Dopo la correzione, non si verifica alcun problema quando si specifica l’intestazione &quot;Accept&quot; (Accetta).

_ACP2E-3343 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### API, GraphQL

#### nessun graphQl disponibile per l’abbonamento agli aggiornamenti dei Punti premio per il cliente

In precedenza alla correzione, l’attributo del cliente reward_warning_notification non poteva essere aggiornato tramite la mutazione GraphQL e la chiamata API Rest. Ora può essere aggiornato come l’attributo del cliente reward_update_notification.

_ACP2E-3348_

### API, GraphQL, imposta

#### Sia Luma (Rest API) che Graphql non calcolano le imposte quando viene fornito solo il codice postale.

Il sistema ora calcola correttamente le imposte quando viene fornito solo un codice postale, garantendo stime accurate delle imposte sia per Luma (Rest API) che per GraphQL. In precedenza venivano calcolate solo le stime di spedizione e non venivano incluse le imposte quando veniva fornito solo un codice postale.

_AC-12060_

### Account

#### Il modulo dell’indirizzo del cliente consente un codice casuale nei campi del nome

Il sistema ora convalida l’input nei campi Nome e Cognome nel modulo dell’indirizzo del cliente, impedendo l’utilizzo di codice casuale. In precedenza, il sistema consentiva l’utilizzo di codice casuale in questi campi senza generare un errore.

_AC-10782 - [Problema GitHub](https://github.com/magento/magento2/issues/38331) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38345)_

#### aggiornamento password amministratore.

_AC-10886 - [Problema GitHub](https://github.com/magento/magento2/issues/38352) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4bca5dfe)_

#### il mio account aggiungi l&#39;arresto anomalo dell&#39;indirizzo al salvataggio

Il sistema ora salva correttamente gli indirizzi dei clienti anche quando il campo dell&#39;area non viene visualizzato, evitando un arresto anomalo durante il processo di salvataggio. In precedenza, se si tentava di aggiungere o modificare un indirizzo senza un campo area visualizzato, si verificava un errore di eccezione.

_AC-10990 - [Problema GitHub](https://github.com/magento/magento2/issues/38406) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38407)_

#### Ciclo di reindirizzamento quando l’URL contiene lettere maiuscole

Il sistema ora converte automaticamente i caratteri maiuscoli negli URL in minuscoli, impedendo un ciclo di reindirizzamento durante l’accesso alla pagina home. In precedenza, l’utilizzo di caratteri maiuscoli nell’URL della base sicura causava un ciclo di reindirizzamento continuo quando si tentava di accedere alla home page.

_AC-11718 - [Problema GitHub](https://github.com/magento/magento2/issues/38538) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38539)_

#### middlename(s) non salvato per gli account guest

Il sistema ora salva correttamente il secondo nome per gli account guest durante il pagamento, rendendolo accessibile nel modello e-mail. In precedenza, il secondo nome non veniva salvato nella tabella dei preventivi e non era accessibile nel modello di e-mail per gli account guest.

_AC-11755 - [Problema GitHub](https://github.com/magento/magento2/issues/38593) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39067)_

#### Amministratore: pulsanti Azioni pagina mobili a sinistra anziché a destra

Il sistema ora allinea correttamente i pulsanti Azioni pagina al lato destro dell’intestazione fissa nel pannello di amministrazione, migliorando l’aspetto professionale. In precedenza, questi pulsanti si spostavano erroneamente sul lato sinistro dell’intestazione fissa.

_AC-11919 - [Problema GitHub](https://github.com/magento/magento2/issues/38701) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### Errore `dev:di:info` in magento 2.4.7

Il sistema visualizza correttamente i parametri del costruttore durante l&#39;esecuzione del comando `dev:di:info`, evitando il verificarsi di errori. In precedenza, l’esecuzione di questo comando generava un errore a causa di una mancata corrispondenza del tipo nell’argomento.

_AC-11999 - [Problema GitHub](https://github.com/magento/magento2/issues/38740) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Casella di selezione per l’accesso come cliente non traducibile

Il sistema ora consente di impostare i campi &quot;Login as Customer opt-in checkbox&quot; e &quot;Login as Customer checkbox tooltip&quot; nell&#39;ambito &quot;Visualizzazione store&quot;, consentendo la traduzione per diverse visualizzazioni dello store. In precedenza, questi campi venivano impostati solo nell’ambito &quot;Sito web&quot;, impedendo le traduzioni per le singole visualizzazioni dello store.

_AC-13000 - [Problema GitHub](https://github.com/magento/magento2/issues/32329) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32359)_

#### La home page dell’interfaccia utente front-end nel menu a discesa del profilo non è presente.(in modo intermittente)

_AC-14299_

#### Il cliente ha effettuato l’accesso ma visualizza l’errore 404 in front-end.

La pagina della dashboard del cliente storefront ora viene caricata come previsto quando un cliente effettua l’accesso. In precedenza, i clienti potevano accedere, ma questa pagina mostrava un errore 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [Problema GitHub](https://github.com/magento/magento2/issues/35838) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36263)_

#### Impossibile salvare le informazioni sugli attributi del cliente nella sezione del cliente Admin Edit;

L’ID store del cliente ora è implementato correttamente per ambito del sito web per il modulo di modifica cliente amministratore.

_ACP2E-2791 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/488c1034)_

#### [Cloud] non riesce a creare il cliente tramite API quando è abilitato il servizio Vendite private

Ora è possibile creare il cliente da un utente amministratore autenticato e con un token di integrazione autenticato tramite API REST quando la restrizione del sito web è abilitata.

_ACP2E-3115_

#### Dopo l’accesso, i prodotti aggiunti all’elenco di confronto come utenti guest non sono visibili.

I prodotti aggiunti all’elenco di confronto dei prodotti prima di effettuare l’accesso come cliente ora vengono mantenuti dopo l’accesso.
In precedenza, dopo l’accesso, i prodotti aggiunti all’elenco di confronto come utenti guest non erano visibili.

_ACP2E-3329 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### La configurazione Consenti paesi causa problemi nelle configurazioni degli indirizzi del cliente

La selezione della configurazione Consenti paesi non influisce sui paesi mostrati per al di fuori dell’ambito specificato. Consenti in precedenza la configurazione di Paesi influenzata dall’attributo dell’indirizzo del cliente al di fuori dell’ambito specificato

_ACP2E-3433 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Il registro degli omaggi condivisi mostra la data dell’evento come 1 giorno prima

La data del registro dei regali è ora visualizzata correttamente su Storefront

_ACP2E-3445_

#### VAPT: errore di logica di business - data futura come data di nascita del cliente

La data di nascita del cliente non può essere posticipata a oggi

_ACP2E-3501 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Account, API, GraphQL

#### API cliente: il numero di errori di accesso non è stato reimpostato su 0 dopo il corretto accesso

Ora il numero di errore viene reimpostato su zero nella tabella delle entità cliente dopo l’accesso del cliente tramite gli endpoint API.

_ACP2E-3246 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Account, interfaccia utente amministratore, B2B

#### Gli utenti amministratori con restrizioni non possono sempre visualizzare cataloghi condivisi personalizzati

Gli utenti amministratori con restrizioni possono ora visualizzare e gestire in modo coerente i clienti e tutti i cataloghi condivisi a cui i prodotti sono assegnati, a condizione che abbiano accesso allo store specifico. In precedenza, un utente amministratore con accesso limitato a un particolare archivio non poteva sempre visualizzare tutti i cataloghi condivisi a cui erano assegnati i prodotti oppure poteva vedere clienti che non potevano salvare, con conseguenti incongruenze nel sistema.

_ACP2E-3038 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

### Account, carrello e pagamento

#### L’attributo personalizzato &quot;select&quot; (seleziona indirizzo cliente) non viene riprodotto per il nuovo indirizzo cliente

_AC-2341 - [Problema GitHub](https://github.com/magento/magento2/issues/34950)_

### Interfaccia utente amministratore

#### [Problema]: pulsante per aggiungere le autorizzazioni per &quot;ricaricare i dati&quot;

Il sistema ora include un controllo delle autorizzazioni per il pulsante &quot;Ricarica dati&quot;, che garantisce che venga visualizzato e accessibile solo agli utenti con le autorizzazioni appropriate. In precedenza, il pulsante &quot;Ricarica dati&quot; era visibile e cliccabile per tutti gli utenti, portando a una pagina &quot;non consentita&quot; quando gli utenti facevano clic senza le autorizzazioni necessarie.

_AC-10705 - [Problema GitHub](https://github.com/magento/magento2/issues/38283) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38279)_

#### [Problema] Etichette non coerenti per gli attributi nelle regole di marketing

Il sistema ora compila correttamente le etichette in modo coerente per le opzioni di categoria e attributo nella regola prezzo carrello

_AC-11427 - [Problema GitHub](https://github.com/magento/magento2/issues/31232) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31231)_

#### La convalida dei dati ha esito positivo ed è presente il pulsante Importa durante l&#39;importazione di prodotti con il comportamento Sostituisci

Il sistema ora convalida correttamente i dati e nasconde il pulsante &quot;Importa&quot; durante il processo di importazione del prodotto con il comportamento &quot;Sostituisci&quot;, impedendo qualsiasi sostituzione involontaria dei dati. In precedenza, il sistema convalidava i dati in modo errato e visualizzava il pulsante &quot;Importa&quot;, causando potenziali incongruenze nei dati.

_AC-11588 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Bug] Magento 2.4.7 non consente foto di prodotto con estensione maiuscola.

Il sistema ora accetta caricamenti di immagini di prodotto con estensioni di file in formato maiuscolo, garantendo un processo di creazione del prodotto fluido. In precedenza, i caricamenti di immagini con estensioni di file in maiuscolo venivano rifiutati, costringendo gli utenti a cambiare l’estensione del file in minuscolo.

_AC-12167 - [Problema GitHub](https://github.com/magento/magento2/issues/38831) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Menu a discesa nascosto nelle griglie con l’azione di selezione (ad esempio Contenuto > Elementi > Pagine)

Ora il sistema è stato corretto tutti i menu a discesa simili per tutte le griglie.

_AC-12319 - [Problema GitHub](https://github.com/magento/magento2/issues/38891) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39371)_

#### [Problema] Correzione Avviso: chiave di matrice &quot;filters&quot; non definita

Il sistema ora gestisce gli scenari in cui un nuovo utente non ha ancora interagito con i segnalibri, impedendo la registrazione di un avviso di &quot;filtri&quot; della chiave di array non definita. In precedenza, questo avviso veniva registrato quando un nuovo utente non aveva interagito con i segnalibri.

_AC-13131 - [Problema GitHub](https://github.com/magento/magento2/issues/39013) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38996)_

#### Il file CSV di importazione del prodotto con caratteri speciali non riesce a causa di modifiche al codice nel file Validate.php

Il sistema ora convalida e importa correttamente i file CSV dei prodotti contenenti caratteri speciali, consentendo il corretto trasferimento dei dati. In precedenza, se si tentava di importare un file CSV di un prodotto con caratteri speciali, si verificava un errore che impediva il processo di importazione.

_AC-13529 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Quando il numero massimo di richieste di reimpostazione password è impostato su maggiore di 0, ad esempio: 3, i messaggi di errore &quot;Limite superato&quot; vengono inviati prima del raggiungimento del limite, ovvero dalla seconda volta

_AC-13767_

#### Anche se il numero massimo di richieste di reimpostazione password è impostato su 0 (disattivato) , &quot;i messaggi di errore relativi al limite superiore vengono inviati dalla seconda volta&quot;

_AC-13768_

#### Non è presente alcun asterisco rosso per il campo del numero di telefono obbligatorio

In precedenza l&#39;asterisco rosso non veniva visualizzato per il numero di telefono, ma  numero di telefono obbligatorio. Che è ora un asterisco rosso fisso può essere visto sul numero di telefono come un campo obbligatorio.

_AC-13850 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### In Amministratore Quando si tenta di riordinare l’ordine, il pulsante non è selezionabile. (in modo intermittente)

_AC-14300_

#### [Problema] Imposta la modalità di indicizzazione predefinita su &#39;pianificazione&#39;

Per impostazione predefinita, tutti i nuovi indicizzatori sono in modalità **[!UICONTROL Update by Schedule]**.  In precedenza, la modalità predefinita era **[!UICONTROL Update on Save]**. Gli indicizzatori esistenti non vengono interessati. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [Problema GitHub](https://github.com/magento/magento2/issues/36419) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0b410856)_

#### [Problema] Elimina le tabelle del registro modifiche dell&#39;indicizzatore in caso di annullamento dell&#39;abbonamento a mview

Il sistema ora rimuove automaticamente le tabelle del registro delle modifiche inutilizzate quando un indice viene cambiato da &quot;aggiorna secondo pianificazione&quot; a &quot;aggiorna al salvataggio&quot;, contrassegnando l&#39;indice come non valido per assicurarsi che non vengano saltate voci. In precedenza, il passaggio di un indice a &quot;aggiorna al salvataggio&quot; lasciava le tabelle del registro modifiche inutilizzate nel sistema e contrassegnava tutti gli indici modificati come &quot;validi&quot;.

_AC-7700 - [Problema GitHub](https://github.com/magento/magento2/issues/29789) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/25859)_

#### Nessun collegamento per la spedizione durante i pagamenti in pagamento nella vista per cellulare

Il sistema ora assicura che i titoli/collegamenti di pagamento &quot;Shipping&quot; e &quot;Review &amp; Payments&quot; siano sempre visibili nella parte superiore della pagina nella vista mobile, consentendo agli utenti di spostarsi facilmente tra i vari passaggi e apportare le correzioni necessarie. In precedenza, questi titoli/collegamenti erano nascosti nella visualizzazione per dispositivi mobili, rendendo difficile per gli utenti conoscere il passaggio corrente o tornare ai passaggi precedenti.

_AC-7962 - [Problema GitHub](https://github.com/magento/magento2/issues/36856) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36982)_

#### cliente I commenti di spedizione per query ordini create_at vengono restituiti in fuso orario +0 non in store fuso orario configurato

Il sistema ora visualizza correttamente il campo &quot;created_at&quot; dai commenti sulla spedizione nel fuso orario configurato del cliente quando si utilizza la query Ordini cliente. In precedenza, il campo &quot;created_at&quot; veniva visualizzato nel fuso orario +0, indipendentemente dal fuso orario configurato del cliente.

_AC-8109 - [Problema GitHub](https://github.com/magento/magento2/issues/36947) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases interrompe l&#39;integrità delle traduzioni

Il comando `bin/magento i18n:collect-phrases -o` ora raccoglie e aggiunge correttamente nuove frasi dai file JavaScript e .phtml, garantendo che le traduzioni vengano riflesse correttamente nel file di traduzione. In precedenza, il sistema non era in grado di includere frasi di traduzione multilinea da file JavaScript e frasi da file .phtml nel file di traduzione, il che portava a traduzioni incomplete o errate.

_AC-9843 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Problema di autorizzazione per l’accesso al blocco dinamico

In precedenza, per l’amministratore con restrizioni, l’aggiunta di un nuovo blocco dinamico generava un errore. Dopo aver implementato questa correzione, l’amministratore con restrizioni può aggiungere correttamente il blocco dinamico e modificarlo senza errori

_ACP2E-2687_

#### L&#39;apostrofo nel nome della visualizzazione punto vendita è sostituito da &#039;

I filtri di visualizzazione archivio della griglia ora visualizzano correttamente gli apostrofi

_ACP2E-2787 - [Problema GitHub](https://github.com/magento/magento2/issues/38395) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Il caricamento dei favicon non riesce a convalidare i file .ico

L’errore di convalida del file è stato aggiornato a &quot;Convalida del file non riuscita. Verifica le impostazioni di elaborazione delle immagini nella configurazione dell&#39;archivio.&quot; In precedenza, si trattava semplicemente di &quot;Convalida file non riuscita&quot;.

_ACP2E-2847 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La raccolta in PageBuilder mostra la miniatura dell&#39;immagine precedente invece dell&#39;immagine appena caricata

Rigenera le anteprime delle immagini per le immagini eliminate e ricaricate con lo stesso nome tramite la raccolta multimediale nel contenuto del Page Builder.

_ACP2E-2957 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188)_

#### Il salvataggio del prodotto da parte dell’utente amministratore con un diverso ambito del ruolo sovrascrive/elimina le informazioni esistenti sul prodotto correlate

In precedenza, prima della correzione, i prodotti correlati venivano reimpostati e diventavano vuoti quando l’utente amministratore secondario faceva clic sul pulsante Salva senza modificare il prodotto correlato. Dopo questa correzione, l’utente amministratore secondario fa clic sul pulsante Salva e il prodotto non viene reimpostato e salvato correttamente.

_ACP2E-2978 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### Impossibile esportare più di 200 ordini

I limiti del server per la dimensione della richiesta degli ID selezionati inviati in precedenza sono stati trascurati modificando la richiesta HTTP da GET a POST per risolvere il problema. In precedenza, a causa delle limitazioni del server per la dimensione della richiesta GET, si verificava il problema.

_ACP2E-3033 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Messaggio di convalida della pagina di estrazione non corretto.

Se un campo obbligatorio viene lasciato vuoto, ad esempio &quot;address&quot;, la convalida lato server non visualizza il messaggio. La convalida lato client garantirà la visualizzazione della notifica di errore del campo obbligatorio, indicando &quot;Questo campo è obbligatorio&quot;. In precedenza, se un campo obbligatorio veniva lasciato vuoto, veniva visualizzato il messaggio &quot;address is required&quot; (indirizzo richiesto), in aggiunta al messaggio di convalida lato client.

_ACP2E-3037 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### Problema del modello di reimpostazione della password con l’utente amministratore

Il problema è stato risolto utilizzando la chiave corretta, che ora include il nome utente amministratore nel modello e-mail e completa correttamente l’oggetto. In precedenza, il problema derivava da una chiave obsoleta in uso.

_ACP2E-3125 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Barre doppie nell’URL del segmento cliente

Le barre doppie non vengono visualizzate nell’URL quando si fa clic su &quot;Reimposta filtro&quot; nella griglia.

_ACP2E-3149 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### COD non disponibile per i paesi specifici consentiti

Ora Cash on delivery è disponibile per i paesi specifici consentiti ogni volta che è richiesto e   AC-3216 funziona come previsto.

_ACP2E-3171 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Impossibile aggiornare lo stato dell’ordine creato personalizzato

&quot;Ora è possibile aggiornare gli stati degli ordini creati su misura, mentre in precedenza era possibile modificare lo stato solo se lo stato corrente era &quot;elaborazione&quot; o &quot;frode&quot;.&quot;

_ACP2E-3178 - [Problema GitHub](https://github.com/magento/magento2/issues/38659) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Lo stato dell&#39;indirizzo di spedizione non viene aggiornato automaticamente

Prima della correzione, l’area dell’indirizzo di spedizione (o l’ID di regione) non era sincronizzata con le informazioni di fatturazione dell’indirizzo. Ora, sia l&#39;area dell&#39;indirizzo di spedizione che l&#39;ID di regione vengono aggiornati correttamente quando vengono modificate le informazioni sull&#39;indirizzo di fatturazione.

_ACP2E-3294 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Il pulsante Reimposta non funziona su Aggiungi/Modifica utente amministratore

In precedenza, il pulsante Reimposta non funzionava nella pagina Aggiungi/Modifica utente amministratore. Ora, nel pannello Amministratore in Sistema -> Autorizzazioni -> Tutti gli utenti, il pulsante Reimposta funziona correttamente nella pagina Aggiungi/Modifica utente amministratore.

_ACP2E-3364 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Rilevamento errato e errori CORS nel routing degli URL dell’amministratore di Magento

Dopo la correzione, se il dominio amministratore personalizzato è un sottodominio del dominio principale, l’amministratore è accessibile solo dal sottodominio configurato.

_ACP2E-3373 - [Problema GitHub](https://github.com/magento/magento2/issues/37663) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Convalida interrotta per &quot;Quantità massima consentita nel carrello&quot;

In precedenza, quando `Maximum Qty Allowed in Shopping Cart` veniva inserito vuoto, non veniva generata alcuna eccezione, anche se qui non viene accettato un valore vuoto. In seguito all’applicazione di questa correzione, se si inserisce una stringa vuota verranno generate delle eccezioni e non sarà possibile salvare il prodotto.

_ACP2E-3392 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Problema nell&#39;interfaccia utente di Anteprima Page Builder] I pulsanti nella colonna Page Builder non sono allineati correttamente

I pulsanti nelle colonne di Page Builder ora sono allineati correttamente. In precedenza, non erano allineati nelle colonne di Page Builder.

_ACP2E-3408 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### Il rapporto Prodotti ordinati non viene esportato. Errore 404.

L&#39;esportazione del rapporto Prodotti ordinati in formato CSV e XML ora funziona come previsto

_ACP2E-3431 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### Errore TinyMCE JS nella console dopo l’abilitazione della minimizzazione Js con la modalità di produzione

In precedenza, l’abilitazione della minimizzazione di JavaScript in modalità di produzione all’interno del pannello di amministrazione causava la visualizzazione degli errori JavaScript relativi a TinyMCE 6 nella console del browser, influendo sulla funzionalità e sull’esperienza utente. Ora, questo problema è stato risolto, garantendo che TinyMCE 6 funzioni senza errori, anche quando la minimizzazione JS è abilitata.

_ACP2E-3457 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### Richiesta di modifiche aggiuntive per completare completamente la correzione ACP2E-3375

&quot;-

_ACP2E-3459 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Abilitazione automatica di nuove autorizzazioni ACL

Le nuove autorizzazioni aggiunte ai moduli personalizzati non concederanno più automaticamente l’accesso a tutti i ruoli utente esistenti, a meno che non siano configurate in modo esplicito.

_ACP2E-3503 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Il report utente del registro azioni amministratore non mostra i dettagli per adminhtml_user_delete

Il file adminhtml_user_delete registra correttamente i dettagli importanti. In precedenza, i registri non venivano generati per le eliminazioni degli utenti.

_ACP2E-3509 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4de008a9)_

#### Regola carrello con condizione di spedizione non applicabile quando si effettua un ordine dall’amministratore

In precedenza, se la regola del prezzo del carrello aveva uno sconto sul metodo di spedizione associato al coupon, non poteva essere applicata tramite l’interfaccia utente di amministrazione. Dopo l’applicazione di questa correzione, lo sconto della regola di prezzo del carrello con un coupon per un metodo di spedizione specifico verrà applicato correttamente dall’interfaccia utente di amministrazione.

_ACP2E-3536 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/11ce816b)_

#### Il codice HEX [FRESH] non viene aggiornato correttamente nel CAMPIONE

Il codice HEX immesso manualmente dall’utente nel selettore colore Campione visivo non viene più modificato dal sistema. In precedenza, alcuni codici HEX subivano lievi regolazioni a causa di errori di conversione tra i modelli di colore.

_ACP2E-3559 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1ef984c0)_

### Interfaccia utente amministratore, B2B

#### L’accesso B2B come intestazione del cliente presenta ancora il marchio Magento

In precedenza, l’intestazione della vetrina mostra &quot;Ora sei connesso come &lt;nome cliente> a &lt;nome negozio>&quot; con il branding Magento. Che è ora fisso e l’intestazione viene visualizzata con il branding ADOBE.

_AC-13628 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Interfaccia utente amministratore, Catalogo

#### Impossibile modificare le posizioni per i prodotti della categoria nel sito web consentito come utente amministratore con restrizioni

Consente a un utente amministratore con restrizioni di aggiungere e ordinare prodotti in una categoria contenuta nella categoria principale assegnata al sito web con restrizioni.

_ACP2E-2708_

### Interfaccia utente amministratore, metodi di pagamento/pagamento, ordine

#### Autorizzazione transazione non visualizzata nella scheda Transazione dopo l&#39;ordine dei pulsanti avanzati PayPal

Il sistema ora visualizza correttamente l&#39;autorizzazione della transazione nella scheda Transazione dopo aver effettuato un ordine utilizzando lo Smart Button PayPal. In precedenza, la transazione di autorizzazione non veniva visualizzata nella scheda Transazione dopo aver fatto clic sul pulsante &quot;Autorizza&quot; e non veniva creata alcuna nuova transazione di tipo &quot;Autorizzazione&quot;.

_AC-13520 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Interfaccia utente amministratore, Prestazioni

#### Dopo l’aggiornamento a 2.4.5-p8 si verificano 500 errori durante la creazione dell’ordine da admin

In precedenza, quando si abilitava la minimizzazione di HTML, non era possibile effettuare un ordine dall’amministratore. Ora, con la minimizzazione di HTML abilitata, l’ordine dall’amministratore può essere effettuato correttamente.

_ACP2E-3169 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Interfaccia utente amministratore, Spedizione

#### Il conteggio dei codici coupon non viene aggiornato nel   &quot;Tempo utilizzato&quot; nella scheda Gestisci codici coupon se un ordine viene effettuato con la spedizione multipla.

In precedenza, quando un ordine veniva effettuato con la spedizione multipla, il conteggio del codice coupon non veniva aggiornato nella colonna &quot;Tempo utilizzato&quot; della scheda Gestisci codici coupon. Ora, il conteggio corretto viene visualizzato in entrambi i &quot;Tempo utilizzato&quot; che riflettono i valori desiderati con la spedizione multipla.

_ACP2E-2519 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4745100c)_

### Interfaccia utente amministratore, staging e anteprima

#### [Cloud] La rimozione del modello con immagini mancanti causa l&#39;eliminazione di pub/supporti

Precedentemente a questa correzione, se per un modello di pagebuilder mancava il nome dell’immagine di anteprima, la cartella pub/media veniva eliminata. Dopo la correzione, verranno eliminati solo il modello e l’immagine di anteprima, se trovata.

_ACP2E-3424 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/Generazione rapporti

#### Errore Google Analytics CSP https://region1.analytics.google.com

Il sistema ora consente correttamente le connessioni a &quot;https://region1.analytics.google.com&#39; quando Google Analytics è abilitato, evitando errori Content Security Policy (CSP). In precedenza, l’abilitazione di Google Analytics e la visualizzazione del sito web dall’UE generavano errori nella console CSP a causa del rifiuto di connettersi a &quot;https://region1.analytics.google.com&#39;&quot;.

_AC-9922 - [Problema GitHub](https://github.com/magento/magento2/issues/37750) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38991)_

#### Il rapporto Avanzamento non funziona

Il sistema ora supporta la generazione di file di dati di reporting avanzato per set di dati di dimensioni eccessive caricando e scrivendo rapporti in batch di 10.000. In precedenza, il modulo di reporting avanzato non era in grado di generare file di dati per set di dati di dimensioni eccessive, causando errori di tipo &quot;MySQL Server has gone away&quot; durante l’esecuzione del processo analytics_collect_data cron.

_ACP2E-2570 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Problema di visibilità dell’intervallo di date del rapporto Prodotti ordinati dall’amministratore.

L’utente potrà selezionare una data qualsiasi dal rapporto prodotti ordinati. In precedenza, dopo l’aggiornamento di una tabella, selezionando la data &quot;DA&quot; si reimpostava la data &quot;A&quot;.

_ACP2E-3080 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Intestazioni curl non corrette che impediscono il funzionamento di `newrelic:create:deploy-marker`

Il sistema ora formatta correttamente le intestazioni curl, consentendo al comando `newrelic:create:deploy-marker` di creare correttamente un marcatore di distribuzione in New Relic. In precedenza, intestazioni curl errate impedivano la creazione di un marcatore di distribuzione in New Relic.

_ACP2E-3096 - [Problema GitHub](https://github.com/magento/magento2/issues/37641) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### GTM mancante dell’evento addToCart in dataLayer per il prodotto configurabile con opzione personalizzata

In precedenza, l’evento addToCart non veniva attivato per i prodotti configurabili. Ora l’evento viene aggiunto correttamente alla variabile GTM dataLayer.

_ACP2E-3146_

#### Lo script inlineJS per il monitoraggio del browser NewRelic causa errori CSP

Gli script di monitoraggio di NewRelic Browser ora vengono inseriti dall’applicazione al posto dell’agente APM per la conformità con CSP (Content Security Policy, criteri per la sicurezza dei contenuti). In precedenza, gli script di monitoraggio del browser NewRelic inseriti dall’agente APM non erano conformi a CSP e causavano la mancata esecuzione degli script.

_ACP2E-3183 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Le query INSERT nella tabella sales_bestsellers_aggregated_daily diventano lente in caso di progetti con volumi di ordini di vendita elevati

In precedenza, la generazione del rapporto giornaliero aggregato dei bestseller richiedeva molto tempo per un grande volume di ordini effettuati. Ora il rapporto viene generato in modo tempestivo.

_ACP2E-3189 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Report ordine con il simbolo di valuta errato

Il simbolo di valuta per gli importi degli ordini nel rapporto Ordine è stato erroneamente ricavato da valuta/opzioni/base. Ora è stato corretto per utilizzare valuta/opzioni/valore predefinito per una generazione rapporti accurata.

_ACP2E-3276 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] Calcoli non corretti nel report sull&#39;utilizzo del coupon

Il totale delle vendite nella griglia del rapporto coupon viene ora calcolato in modo accurato incorporando sia &quot;Importo compensazione imposta sconto&quot; che &quot;Importo compensazione imposta sconto spedizione&quot;. In precedenza, tali importi mancavano dal calcolo, causando discrepanze tra il totale delle vendite e i dati degli ordini di vendita.

_ACP2E-3302 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Problemi con &quot;&lt;project_id>/var/tmp&quot; condiviso

I file temporanei Analytics DataExport utilizzeranno la directory sys tmp, più adatta per l’accesso frequente e le modifiche. Per evitare conflitti nel caso in cui più istanze siano in esecuzione sullo stesso server, il percorso tmp è stato aggiornato per utilizzare l’ID univoco di un’istanza

_ACP2E-3339 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Reporting, B2B

#### B2B - La mappa del sito include prodotti/categorie non assegnati al catalogo condiviso

Limita le categorie e i prodotti generati da sitemap alle categorie e ai prodotti assegnati solo al catalogo condiviso pubblico e/o all’impostazione delle autorizzazioni per la categoria del catalogo.

_ACP2E-2300 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics / Reporting, cloud

#### Magento elimina la maggior parte delle transazioni New Relic cron #34108

AC sta segnalando correttamente le transazioni relative al processo cron a NewRelic. In precedenza, alcune transazioni relative a lavori cron venivano indicate come &quot;OtherTransaction/Action/unknown&quot; in NR

_ACP2E-3067 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Metrica in NR potrebbe essere fuorviante per le transazioni in background - Seguito di ACP2E-3067

Le transazioni in background (cron) utilizzeranno il nome dell’app New Relic definito nelle impostazioni di configurazione

_ACP2E-3187 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### Errore del pacchetto Enterprise Edition 2.4.8-beta102 con eccezioni dell&#39;applicazione

_AC-13501_

#### I prodotti assegnati al catalogo condiviso non si riflettono sul front-end quando viene eseguito l’indice parziale

I prodotti assegnati al catalogo condiviso tramite API REST ora sono immediatamente visibili sulla vetrina dopo il completamento dell’indicizzazione parziale. In precedenza, i prodotti erano visibili solo dopo una reindicizzazione completa.

_ACP2E-2139 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud] La visualizzazione del prezzo nelle versioni mobile e desktop non è la stessa in &quot;Le mie quotazioni&quot;

Non necessario Includi linea imposta non viene più visualizzata in Offerta negoziabile quando viene spesa la sezione prezzo totale del catalogo.

_ACP2E-2873_

#### Bordi non necessari nella sezione Ordini personali

In precedenza veniva creato un contenitore aggiuntivo (riferimenti ordine) che applicava classi CSS aggiuntive, causando la visualizzazione di linee di bordo non necessarie sotto il numero ordine all’interno della sezione Ordini personali, che ora non è visibile.

_ACP2E-3044 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron elimina i preventivi dagli ordini di acquisto ancora approvati

I preventivi utilizzati ora negli ordini fornitore non verranno eliminati dal processo cron sales_clean_quotes

_ACP2E-3247 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Il pulsante Inserisci ordine scompare nei dettagli ordine di acquisto

È stato risolto un problema a causa del quale il pulsante Inserisci ordine era nascosto per gli ordini fornitore approvati quando una variante di prodotto aveva un numero minimo nella scheda specificata

_ACP2E-3465_

#### [CLOUD] Nessuna entità di questo tipo con ID = 0 con modulo b2b

L’utente connesso può aggiungere un prodotto al carrello quando sono abilitate le funzioni di Catalogo condiviso.
L’aggiunta precedente del prodotto al carrello causava un errore di tipo &quot;nessuna entità di questo tipo con ID = 0&quot;

_ACP2E-3474_

#### Non viene visualizzato alcun messaggio di errore per i prodotti di magazzino quando si esegue l’aggiunta in blocco dall’elenco delle richieste di acquisto

Prima della correzione veniva visualizzato un messaggio di successo indipendentemente dal numero di prodotti che non erano stati aggiunti al carrello. Ora vengono visualizzati messaggi separati per i prodotti aggiunti correttamente al carrello e per i prodotti con errori.

_ACP2E-3562_

#### Problema con gli aggiornamenti SKU dopo gli aggiornamenti pianificati che causano autorizzazioni prodotto errate (-2 Rifiuti)

La modifica della SKU di un prodotto con gli aggiornamenti pianificati precedenti non rende più il prodotto inaccessibile ai clienti del catalogo condiviso autorizzati a visualizzare il prodotto.

_ACP2E-3628_

### B2B, catalogo

#### Prodotti/categorie visibili durante la reindicizzazione quando si utilizzano autorizzazioni NoDDL e Categoria

Evita la visualizzazione nelle categorie con restrizioni della vetrina e del relativo contenuto durante l’indicizzazione delle autorizzazioni del catalogo.

_ACP2E-2860_

### B2B, Framework

#### Il Filtro Della Griglia Aziendale E Il Tentativo Di Esportazione CSV Della Griglia Non Riusciranno E Genereranno Un’Eccezione

Il sistema ora consente l’esportazione CSV dei dati della griglia Aziende nel pannello di amministrazione, anche quando vengono applicati filtri come &quot;Saldo in sospeso&quot; e &quot;Tipo di azienda&quot;. In precedenza, l’applicazione di determinati filtri e il tentativo di esportare i dati della griglia generavano un errore e un’eccezione.

_AC-9607 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

#### [Cloud] Impossibile impostare custom_attributes durante la creazione della società tramite la chiamata graphql

Dopo la correzione, è possibile impostare l’attributo &quot;custom_attributes&quot; dell’amministratore della società durante la creazione della società utilizzando la richiesta graphql.

_ACP2E-3391_

### Braintree

#### Il pulsante Estrazione rapida amministratore è disabilitato.

_AC-14293_

#### Pagamento tramite LPM

Il sistema ora esegue correttamente il rendering dei metodi di pagamento locali (LPM) al caricamento iniziale, anche quando gli indirizzi di spedizione e fatturazione di un cliente connesso non corrispondono, garantendo un processo di pagamento fluido. In precedenza, una mancata corrispondenza tra gli indirizzi di spedizione e di fatturazione di un cliente impediva il rendering di LPM, causando potenziali interruzioni durante il pagamento.

_BUNDLE-3367_

#### Configurabile con prodotto virtuale come secondario

Il sistema ora consente metodi di pagamento rapidi per i prodotti configurabili che hanno un prodotto secondario virtuale, garantendo un processo di pagamento fluido. In precedenza, i metodi di pagamento rapido non erano disponibili quando al carrello veniva aggiunto un prodotto configurabile con un prodotto figlio virtuale.

_BUNDLE-3368_

#### Errore di verifica CVV non riuscita

_BUNDLE-3369_

#### Vaulting Tramite l&#39;account Area Issues 247

Il sistema ora consente ai clienti di salvare le informazioni sulla nuova carta o sul conto PayPal su più siti Web senza dover riscontrare errori di autorizzazione. In precedenza, i clienti non erano in grado di salvare nuovi metodi di pagamento tra siti web diversi e ricevevano un messaggio di errore di autorizzazione.

_BUNDLE-3370_

#### Spedisci a un indirizzo di un altro paese

Il sistema ora consente di elaborare le transazioni senza errori durante la spedizione a un indirizzo di un altro paese, garantendo un processo di pagamento fluido. In precedenza, il tentativo di spedire un indirizzo da un altro paese generava errori nella console, nonostante non fossero visibili errori nel front-end.

_BUNDLE-3371_

#### Carta di credito - Funzione Teardown

Il sistema ora gestisce correttamente il ripristino dei componenti di Braintree PayPal quando un cliente torna dalla pagina di pagamento alla pagina di spedizione, prevenendo eventuali errori e assicurandosi che i pulsanti PayPal Express vengano visualizzati correttamente. In precedenza, tornando alla pagina di spedizione dalla pagina di pagamento a volte si verificava un errore durante il tentativo di eliminare i componenti PayPal di Braintree.

_BUNDLE-3372_

#### Callback di spedizione per PayPal Express

Il sistema ora visualizza correttamente i metodi di spedizione disponibili nel modale PayPal Express, consentendo ai clienti di selezionare il metodo di spedizione preferito prima di passare alla pagina di revisione o completare la transazione. In precedenza, non era disponibile alcun metodo di spedizione da selezionare nel modale PayPal Express, che richiedeva ai clienti di selezionare un metodo di spedizione in una pagina di revisione separata prima di poter completare la transazione.

_BUNDLE-3373_

### Bundle

#### Il conteggio dei messaggi di errore di convalida del bundle Storefront supera 1

Il sistema visualizza ora un solo messaggio di errore di convalida quando si fa clic sul pulsante &quot;Aggiungi al carrello&quot; senza selezionare alcuna opzione di casella di controllo per un prodotto incluso. In precedenza, il sistema visualizzava più messaggi di errore di convalida per ogni casella di controllo non selezionata.

_AC-10826 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### Eccezione Magento generata in alcuni casi di test correlati all’ordine

Il sistema ora gestisce correttamente il passaggio &quot;sendGuestPaymentInformation&quot; in vari casi di test, impedendo la generazione di eccezioni Magento. In precedenza, queste eccezioni si verificavano a causa di un metodo di pagamento null, causando errori in diversi casi di test.

_AC-13321_

### Carrello e pagamento

#### L’eccezione non viene gestita correttamente durante l’aggiunta di un prodotto al carrello nella pagina di confronto dei prodotti

Il sistema ora gestisce correttamente le eccezioni quando si aggiunge un prodotto al carrello dalla pagina di confronto dei prodotti, visualizzando un messaggio di gestione dei messaggi nel controller. In precedenza, un’eccezione generava la restituzione di una pagina con codifica JSON invece di essere rilevata e gestita correttamente.

_AC-10660 - [Problema GitHub](https://github.com/magento/magento2/issues/38200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38257) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag non invia i prezzi e i totali delle transazioni.

Il sistema ora invia correttamente i prezzi delle transazioni e i totali a Google Tag quando viene abilitato GTag, garantendo un tracciamento accurato dei dati di e-commerce. In precedenza, la valuta veniva erroneamente inviata come parte degli ordini &quot;all&quot;, piuttosto che essere associata al singolo ordine.

_AC-10698 - [Problema GitHub](https://github.com/magento/magento2/issues/37348) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37504) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37349)_

#### [Problema] [Estrazione] Direttive dipendenti aggiornate nel modello e-mail di pagamento non riuscito

Il sistema ora omette correttamente l&#39;indirizzo di spedizione e il metodo di spedizione dal modello e-mail di pagamento non riuscito per i prodotti virtuali, assicurandosi che nell&#39;e-mail vengano incluse solo le informazioni pertinenti. In precedenza, l’e-mail di pagamento non riuscito per i prodotti virtuali includeva erroneamente l’indirizzo di spedizione e il metodo di spedizione.

_AC-11641 - [Problema GitHub](https://github.com/magento/magento2/issues/32781) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32511)_

#### Accesso a Magento 2 all&#39;interno del pagamento con il cliente esistente dare l&#39;errore della console nel browser Firefox

Il sistema ora consente agli utenti di accedere durante il processo di pagamento senza incontrare errori della console nel browser Firefox. In precedenza, se si tentava di accedere come cliente esistente durante il check-out, si verificava un errore della console in Firefox.

_AC-11717 - [Problema GitHub](https://github.com/magento/magento2/issues/38557) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39509)_

#### [Problema] Regressione delle regole di vendita in 2.4.7

Il sistema ora convalida correttamente le regole di vendita, impedendo l’applicazione di un codice coupon a un carrello quando la condizione del prodotto non corrisponde a nessun nome di prodotto. In precedenza, era possibile applicare una regola di vendita e applicare uno sconto sull’importo della spedizione anche quando la condizione del prodotto non corrispondeva a nessun nome di prodotto.

_AC-11876 - [Problema GitHub](https://github.com/magento/magento2/issues/38671) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Problema] Calcolo CartFixed della regola di vendita: importo sconto non corretto

Il sistema ora calcola correttamente l&#39;importo dello sconto per le regole di vendita con importi fissi del carrello, assicurando l&#39;applicazione di sconti precisi indipendentemente dalle modifiche negli articoli del carrello. In precedenza, l’importo dello sconto poteva variare in modo errato quando gli articoli del carrello cambiavano, risultando a volte in sconti notevolmente più grandi del previsto.

_AC-11914 - [Problema GitHub](https://github.com/magento/magento2/issues/38694) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### [Problema] Il caricatore blocca i metodi di spedizione dopo la modifica del codice postale e le regole di convalida delle tariffe di spedizione

Il sistema ora gestisce correttamente i metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione, assicurandosi che il caricatore non blocchi i metodi di spedizione dopo la modifica del codice postale nell&#39;indirizzo di spedizione durante il pagamento. In precedenza, la modifica del codice postale nell’indirizzo di spedizione durante il pagamento causava il blocco dei metodi di spedizione da parte del caricatore, che non scompariva quando venivano utilizzati metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione.

_AC-11993 - [Problema GitHub](https://github.com/magento/magento2/issues/38742) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La funzione del codice coupon non funziona correttamente nella pagina di pagamento di Magento 2.4.7

Il sistema ora abilita il campo di input del codice sconto/coupon nella pagina di pagamento per i prodotti virtuali e scaricabili, consentendo agli utenti di applicare i codici sconto come previsto. In precedenza, l’input del codice sconto/coupon veniva disattivato e il testo del titolo del pulsante visualizzato come &quot;Annulla coupon&quot;, impedendo agli utenti di applicare codici sconto.

_AC-12170 - [Problema GitHub](https://github.com/magento/magento2/issues/38826) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La casella di controllo dei termini e delle condizioni non consente l&#39;utilizzo di HTML nella vetrina

Il sistema ora supporta la formattazione HTML nel testo della casella di controllo &quot;Termini e condizioni&quot; nella vetrina, consentendo una personalizzazione e una leggibilità migliorate. In precedenza, il testo della casella di controllo veniva visualizzato in formato testo normale, ignorando eventuali tag di HTML utilizzati.

_AC-12479 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### La regola del prezzo del carrello creata per l’utente connesso viene erroneamente applicata per l’utente non connesso

Il sistema ora rimuove correttamente la regola del prezzo del carrello per gli utenti connessi quando vengono disconnessi automaticamente a causa della scadenza dei cookie, garantendo che lo sconto non venga applicato agli utenti non connessi. In precedenza, la regola del prezzo del carrello veniva ancora applicata anche quando l’utente veniva disconnesso, causando l’applicazione di uno sconto errato agli utenti non connessi.

_AC-12541 - [Problema GitHub](https://github.com/magento/magento2/issues/38944) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] [FUNZIONALITÀ] Ottimizzazione delle prestazioni dei grandi carrelli acquisti impedendo...

Il sistema ora ottimizza le prestazioni per i carrelli acquisti di grandi dimensioni impedendo chiamate getActions duplicate, migliorando la velocità e l’efficienza delle operazioni del carrello. In precedenza, per un carrello con più elementi, la funzione getActions veniva chiamata più volte, rallentando le prestazioni del sistema.

_AC-13302 - [Problema GitHub](https://github.com/magento/magento2/issues/39292) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39290)_

#### Il prodotto del registro degli omaggi non viene visualizzato correttamente

_AC-13797_

#### Il prodotto del registro degli omaggi non viene visualizzato correttamente

_AC-13841_

#### IVA traduzione nel modulo di rendering indirizzi

Il sistema ora consente la traduzione del testo &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nei renderer degli indirizzi, consentendo agli utenti di tradurre questi termini nella lingua specifica del negozio. In precedenza, questi termini non erano traducibili, costringendo gli utenti a utilizzare una soluzione alternativa.

_AC-8103 - [Problema GitHub](https://github.com/magento/magento2/issues/36942) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36943)_

#### Ordini duplicati con lo stesso ID preventivo contemporaneamente con poche differenze di tempo

È stato risolto il problema che si verificava quando i clienti di Adobe Commerce riscontravano ordini duplicati con lo stesso QuoteID.

_ACP2E-2055 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Carrello acquisti persistente cancellato durante il passaggio di pagamento

Dopo la correzione, la selezione del metodo di pagamento durante l’estrazione senza accesso non interrompe la sessione persistente.

_ACP2E-2470 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Riordina aggiunge al carrello un prodotto non assegnato

In precedenza, per i diversi punti vendita, i prodotti potevano essere riordinati dall&#39;altro. Dopo aver applicato questa correzione solo allo stesso archivio, è possibile riordinare lo stesso prodotto di ambito quando è abilitata la condivisione dei conti cliente

_ACP2E-2518 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### In admin, il &quot;Carrello acquisti&quot; a sinistra non viene aggiornato quando si selezionano gli articoli e il &quot;Carrello acquisti&quot; a destra

Il &quot;Carrello acquisti&quot; a sinistra viene aggiornato quando si selezionano gli articoli e &quot;Sposta nel carrello&quot; a destra nel lato amministratore. In precedenza questa funzionalità non funzionava perché gli elementi del carrello trasformati non venivano vuoti dalla sessione.

_ACP2E-2620 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Cloud] Regola di vendita non applicata al primo ordine di spedizione multipla

Dopo la correzione, lo sconto viene visualizzato correttamente per ogni ordine dello stesso preventivo di spedizione multipla.

_ACP2E-2646 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### [Cloud] Richieste Parallele Di Produzione Per Aggiungere Lo Stesso Prodotto Al Carrello Risultano In Due Elementi Separati Nell&#39;API REST Carrello

Il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello tramite l’API REST generava più elementi di riga per lo stesso SKU.

_ACP2E-2664 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problema con l’ordine dal registro regali di Magento 2.4.4 Enterprise/Commerce

È stato risolto il problema che impediva l&#39;acquisto di un prodotto da un registro regali, consentendo l&#39;inserimento di ordini e l&#39;aggiornamento appropriato del registro regali. In precedenza, si verificava un errore durante il tentativo di effettuare un ordine da un registro regali, che impediva il completamento dell&#39;acquisto.

_ACP2E-2676 - [Problema GitHub](https://github.com/magento/magento2/issues/35432)_

#### Recupero impossibile inviare il cookie. Dimensione dei &#39;messaggi-immagine&#39; durante il tentativo di riordinare

Il processo di riordinamento non genera ora i propri errori. Si baserà sull&#39;elenco del carrello assegni articoli incorporati.

_ACP2E-2704 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### L&#39;indirizzo di spedizione predefinito non è selezionato al momento del pagamento

L’evento di selezione dell’indirizzo di spedizione predefinito viene ora eseguito nel contesto della ricerca degli indirizzi abilitata.

_ACP2E-2798 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [Problema API addProductsToCart graphql] di CLOUD con opzione personalizzata

GraphQL aggiunge correttamente al carrello lo stesso prodotto con diverse opzioni personalizzate

_ACP2E-2897 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] Le regole dei prodotti correlati non funzionano quando si modifica la visualizzazione dello store

Il problema è stato risolto confermando che il valore della proprietà personalizzata è stato ricevuto correttamente sulla pagina del carrello. In precedenza, non veniva recuperato correttamente quando si cambiava negozio nella pagina del carrello della vetrina.

_ACP2E-2917_

#### Più indirizzi aggiunti all&#39;account al momento dell&#39;estrazione come nuovo cliente

Il sistema ora salva un nuovo indirizzo cliente una sola volta se l&#39;ordine non è stato creato, impedendo la creazione di più indirizzi identici in caso di errori di inserimento dell&#39;ordine. In precedenza, il sistema salvava un nuovo indirizzo ogni volta che veniva effettuato un tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine fosse stato creato correttamente o meno.

_ACP2E-2923 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/2ebcef39)_

#### Il nuovo ordine dei clienti tramite il modulo d&#39;ordine degli ospiti genera un carrello vuoto

In precedenza, quando si effettuava un nuovo ordine attraverso la pagina Ordini e restituzioni, il cliente veniva reindirizzato alla pagina di accesso. Dopo l’applicazione di questa correzione, il cliente registrato viene reindirizzato correttamente alla pagina Visualizza carrello al momento del riordino. Il flusso funziona come i clienti guest.

_ACP2E-3004 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### L’utente amministratore con risorse ruolo limitate non può visualizzare i carrelli acquisti

In precedenza, l’amministratore con restrizioni non poteva visualizzare il carrello abbandonato dal pannello di amministrazione per un sito web associato. Dopo aver applicato questa correzione, l’amministratore con restrizioni può visualizzare il carrello abbandonato dal pannello di amministrazione.

_ACP2E-3025 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### [Cloud] ordina rapidamente grandi quantità di prestazioni SKU

Le prestazioni di checkout sono state migliorate quando gli attributi utilizzati nelle regole di prezzo del carrello non sono presenti per tutti i prodotti e quando la funzione MAP (Prezzo minimo annunciato) è abilitata.

_ACP2E-3176 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Articoli duplicati nel carrello

Il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello in Storefront generava più righe per lo stesso SKU.

_ACP2E-3211 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### La conferma e-mail dell’ordine di pagamento viene inviata alle e-mail inserite in Nome/Cognome

La conferma e-mail dell’ordine di pagamento, precedentemente inviata quando nei campi Nome e Cognome veniva inserito un pattern simile a un’e-mail, non viene più inviata.

_ACP2E-3296 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Estrai il modulo dell&#39;indirizzo di spedizione ottieni l&#39;aggiornamento con l&#39;indirizzo sbagliato

shippingAddressFromData viene ora salvato nell&#39;archivio locale per sito Web. In precedenza, un indirizzo del sito Web errato poteva essere inserito automaticamente nel modulo dell’indirizzo di spedizione durante il pagamento se nell’URL veniva utilizzato un codice store e il pagamento veniva avviato da più siti Web durante la stessa sessione guest.

_ACP2E-3402 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [L&#39;estrazione di CLOUD] non mantiene l&#39;indirizzo di fatturazione selezionato quando la ricerca degli indirizzi è abilitata

Nella pagina Pagamento cassa viene mantenuto l&#39;indirizzo di fatturazione selezionato quando è abilitata la ricerca degli indirizzi. In precedenza, se &quot;Limite numero di indirizzi cliente&quot; è configurato su 1 e il cliente ha più di un indirizzo, l’indirizzo di fatturazione selezionato scompare dopo il ricaricamento della pagina.

_ACP2E-3405_

#### Prodotto gift card | Unione carrello: unione delle gift card

I prodotti Giftcard ora vengono uniti correttamente nel carrello

_ACP2E-3407 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### La persistenza del carrello non viene rispettata alla disconnessione

È stata aggiunta la funzionalità Memorizza utente dall’accesso del cliente alla finestra a comparsa per l’autenticazione e gli accessi di pagamento.

_ACP2E-3415 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_

#### I dati delle offerte esistenti non sono aggiornati/non visibili, ma si crea un nuovo record delle offerte quando trigger_recollect = 1

Gli articoli del carrello del cliente non scompaiono più a seguito dell’eliminazione di un prodotto dopo che è stato aggiunto al carrello.

_ACP2E-3488 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Quando si acquista un articolo del Registro di sistema relativo ai regali, il cliente visualizza gli articoli non presenti nel Registro di sistema

L&#39;aggiornamento del registro degli omaggi non include più elementi che non appartengono al registro degli omaggi.

_ACP2E-3495_

#### [Cloud] problema con il popup di conferma &quot;Rimuovi tutto&quot; rimozione elementi dal carrello senza conferma

Ora, facendo clic sul pulsante &quot;Rimuovi tutto&quot; per i prodotti con attenzione richiesta, viene visualizzata una finestra a comparsa di conferma per assicurarsi che gli articoli vengano rimossi solo con la conferma. In precedenza, gli elementi venivano rimossi immediatamente senza alcuna conferma

_ACP2E-3510_

#### [CLOUD] Riordina la funzionalità del pulsante

Riordinare un ordine dall&#39;area di amministrazione ora aggiungerà prodotti con scorte al preventivo anche se nell&#39;ordine originale sono presenti alcuni prodotti che non dispongono più di scorte. Prima della correzione non veniva aggiunto alcun prodotto al nuovo preventivo se il prodotto senza scorte era nell’ordine originale.

_ACP2E-3618 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### I negozi di ricerca non funzionano per codice postale

La ricerca delle posizioni di prelievo per codice postale non funzionava correttamente per le localizzazioni olandesi. Dopo la correzione, la ricerca della posizione di prelievo fornirà risultati in base al codice postale.

_ACP2E-3622 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Carrello e pagamento, Pagamento/ Pagamento di una pagina

#### [BUG casuale] Il campo E-mail non viene visualizzato o richiede molto tempo nella pagina Pagamento o Spedizione cassa

Commerce ora esegue il rendering del campo **[!UICONTROL Email]** nelle pagine di pagamento e spedizione di pagamento di checkout come previsto. In precedenza, questo campo era assente o visualizzato lentamente.

_AC-9386 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e1babcfd)_

### Carrello e pagamento, ordine

#### Datepicker per prodotto con più opzioni personalizzabili con campi data che non funzionano quando si effettua un ordine dall’amministratore

Il sistema ora visualizza correttamente il selettore data per tutti i campi della data durante la configurazione di un prodotto con più opzioni di data personalizzabili nel processo di creazione degli ordini di amministrazione. In precedenza, il selettore data veniva visualizzato solo per il primo campo data, lasciando i campi rimanenti senza un selettore data.

_ACP2E-3097 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Carrello e pagamento, spedizione

#### Acquisto immediato &quot;spedizione più economica&quot; interrotta per prodotti configurabili

La funzione Acquisto istantaneo ha selezionato erroneamente l&#39;opzione di consegna in-store più costosa per i prodotti configurabili invece del metodo più economico. Questa correzione assicura che venga scelto il metodo di spedizione corretto in base al prezzo effettivo.&quot;

_AC-12119 - [Problema GitHub](https://github.com/magento/magento2/issues/38811) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38819) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29fe9097)_

### Catalogo

#### La pulizia della tabella del database cron_schedule non esegue la pulizia dei processi non esistenti

Il sistema ora ripulisce automaticamente la tabella di database cron_schedule, rimuovendo le voci per i processi che non esistono più nel sistema. In questo modo è possibile garantire prestazioni ottimali mantenendo un numero minimo di righe nella tabella. In precedenza, le voci per i processi da moduli inattivi o rimossi non venivano pulite, generando un’inutile accumulazione di dati nella tabella cron_schedule.

_AC-10910 - [Problema GitHub](https://github.com/magento/magento2/issues/38217) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38693)_

#### Il prezzo di livello non viene eliminato dal prodotto configurabile

Il sistema ora rimuove correttamente il prezzo di livello di un prodotto quando viene convertito da prodotto semplice a prodotto configurabile, garantendo una visualizzazione precisa del prezzo sul front-end. In precedenza, il prezzo di livello di un prodotto configurabile non veniva eliminato quando un prodotto veniva convertito da prodotto semplice a prodotto configurabile, determinando una mancata corrispondenza nel prezzo visualizzato.

_AC-10953 - [Problema GitHub](https://github.com/magento/magento2/issues/38390) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38427)_

#### Descrizione categoria WYSIWYG vuota in una visualizzazione archivio non predefinita

Il sistema ora salva e visualizza correttamente la descrizione della categoria nell&#39;editor di WYSIWYG quando si modifica una categoria a livello di visualizzazione store. In precedenza, l’editor WYSIWYG risultava vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione store.

_AC-11804 - [Problema GitHub](https://github.com/magento/magento2/issues/38622) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38623)_

#### Impossibile riordinare i prodotti configurabili con una casella di controllo selezionata per l’opzione personalizzata

Il sistema ora elabora correttamente il riordino dei prodotti configurabili con una singola opzione personalizzata di casella di controllo selezionata, consentendo la corretta creazione del carrello. In precedenza, il tentativo di riordinare tali prodotti causava un errore e impediva l’aggiunta degli articoli al carrello.

_AC-11970 - [Problema GitHub](https://github.com/magento/magento2/issues/38736) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1d144bce)_

#### [Problema] Correzione del testo dell&#39;elemento filtro nella navigazione a livelli

Il sistema ora utilizza correttamente le parole &quot;item&quot; (elemento) e &quot;items&quot; (elementi) nell&#39;elemento del filtro di navigazione a livelli, migliorando la chiarezza e la precisione delle descrizioni del filtro. In precedenza, queste parole venivano utilizzate in modo errato, generando potenziale confusione per gli utenti che navigavano nelle opzioni del filtro.

_AC-12076 - [Problema GitHub](https://github.com/magento/magento2/issues/38789) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37852)_

#### Il formato di data e ora per l’opzione personalizzata non funziona

Il sistema ora applica correttamente il formato data configurato alle opzioni personalizzate del prodotto di tipo Data, garantendo che il formato data venga visualizzato correttamente sul front-end. In precedenza, le modifiche alla configurazione del formato della data non venivano applicate al front-end per le opzioni personalizzate del prodotto di tipo Data.

_AC-12164 - [Problema GitHub](https://github.com/magento/magento2/issues/32990) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38925)_

#### Opzioni elenco a discesa mancanti

Ora il sistema visualizza correttamente tutti i valori nel menu a discesa quando crea un nuovo attributo con più di 20 valori. In precedenza venivano visualizzati solo i primi 20 valori o un altro valore di pagina selezionato, causando la mancanza dei valori rimanenti.

_AC-13068 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Utilizza l&#39;ID archivio corrente per la cache runtime delle categorie

Il sistema ora utilizza correttamente l’ID archivio corrente per la cache runtime delle categorie, impedendo la sostituzione dei dati quando viene utilizzata l’emulazione o quando il codice personalizzato salva la categoria in archivi diversi. In precedenza, l’oggetto archiviato in fase di esecuzione poteva provenire da un archivio errato, con conseguente sostituzione dei dati.

_AC-13296 - [Problema GitHub](https://github.com/magento/magento2/issues/39310) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata:deploy - no-update genera un&#39;eccezione

Il sistema ora accetta correttamente un valore booleano quando si utilizza l&#39;opzione —no-update nel comando sampledata:deploy, evitando errori durante la distribuzione dei dati di esempio. In precedenza, veniva generato un errore durante l’utilizzo di questo comando, poiché il sistema prevedeva erroneamente un valore intero.

_AC-13324 - [Problema GitHub](https://github.com/magento/magento2/issues/39344) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39345)_

#### [Problema] è stato corretto l&#39;utilizzo del tipo di cache EAV

Il sistema ora utilizza correttamente il tipo di cache EAV in tutte le posizioni rilevanti, garantendo un caching dei dati coerente ed efficiente. In precedenza, il tipo di cache EAV non veniva utilizzato in modo coerente, con potenziali inefficienze e incoerenze nella memorizzazione dei dati nella cache.

_AC-13355 - [Problema GitHub](https://github.com/magento/magento2/issues/32322) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31264)_

#### Ricerca avanzata nel catalogo con dati vuoti consente di passare alla pagina dei risultati di ricerca[2.4.dev branch]

Il sistema ora mantiene correttamente gli utenti nella pagina Ricerca avanzata e visualizza un messaggio di errore quando tentano di eseguire una ricerca senza immettere alcun dato. In precedenza, l’esecuzione di una ricerca vuota reindirizzava gli utenti alla pagina Ricerca avanzata catalogo con un messaggio che chiedeva di modificare la ricerca.

_AC-13596 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### [Problema] Layout del prodotto basato su attribute_set

Il sistema ora consente di regolare il layout del prodotto in base al set di attributi, fornendo un modo più pratico ed efficiente per gestire la visualizzazione del prodotto nel negozio front-end. In precedenza, il layout poteva essere regolato solo per SKU o per tipi di prodotto, il che non era sempre pratico per molti prodotti o articoli specifici.

_AC-13622 - [Problema GitHub](https://github.com/magento/magento2/issues/38790) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36244)_

#### Chiave univoca mancante nella tabella eav_attribute_option_value

Il sistema ora include una chiave univoca nelle colonne &#39;option_id&#39; e &#39;store_id&#39; nella tabella &#39;eav_attribute_option_value&#39;, impedendo la possibilità che un&#39;opzione contenga più valori per la stessa vista store. In precedenza, un codice errato poteva causare la presenza di più valori per la stessa visualizzazione archivio, causando problemi durante la modifica di prodotti o attributi.

_AC-6738 - [Problema GitHub](https://github.com/magento/magento2/issues/24718) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/28796)_

#### [Problema] Utilizza la classe di visibilità per l&#39;indicizzatore di prodotti di categoria, anziché valori hardcoded

Il sistema ora utilizza la classe di visibilità per l’indicizzatore di prodotto della categoria invece dei valori hardcoded, migliorando la modularità. In precedenza, venivano utilizzati valori hardcoded nell’indicizzatore dei prodotti per categoria, limitando la flessibilità e l’adattabilità.

_AC-8297 - [Problema GitHub](https://github.com/magento/magento2/issues/37200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37199)_

#### Il codice valuta non viene modificato nel widget Nuovo prodotto

Il sistema ora aggiorna correttamente il codice della valuta nel widget Nuovo prodotto quando la valuta viene modificata nel front-end, garantendo la coerenza nella visualizzazione della valuta in tutto il sito. In precedenza, la modifica della valuta nel front-end non influenzava il codice di valuta visualizzato nel widget Nuovo prodotto.

_AC-9375 - [Problema GitHub](https://github.com/magento/magento2/issues/37898) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37899)_

#### Il prezzo normale non viene visualizzato su PLP per il prodotto configurabile

Ora sulle pagine degli elenchi dei prodotti viene visualizzato il prezzo normale per i prodotti configurabili con prodotti secondari a prezzo speciale.

_ACP2E-2224 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Informazioni sul magazzino non visualizzate a destra nella griglia di Visual Merchandising

Il materiale viene ora visualizzato in base al negozio selezionato.

_ACP2E-2478 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

#### Il contenuto del widget non viene aggiornato nella pagina cms

Ora il sistema aggiorna il contenuto del widget su una pagina CMS quando un prodotto viene impostato come nuovo e salvato, assicurandosi che nella pagina venga visualizzata la raccolta di prodotti aggiornata. In precedenza, la pagina non veniva aggiornata per mostrare il nuovo prodotto a causa di identità di cache non corrette utilizzate per il widget nella cache.

_ACP2E-2621 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problemi relativi al risparmio di prezzi avanzati sui prodotti bundle

Miglioramento delle prestazioni con risparmio sui prodotti.

_ACP2E-2630 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [Processo di reindicizzazione locale] inefficiente durante la creazione delle regole di prezzo catalogo

Il salvataggio della regola del prezzo di catalogo non invalida gli indicizzatori, ma solo i prodotti interessati

_ACP2E-2652 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Aggiornamento degli attributi di prodotto di tipo Data e Ora tramite importazione CSV

Ora gli attributi datetime avranno una parte temporale nei dati esportati. Sarà inoltre possibile aggiornare l’ora per tali attributi utilizzando l’importazione. Inoltre, se è abilitata l&#39;opzione &quot;Raccoglimento campi&quot;, i valori degli attributi nella colonna &quot;additional_attributes&quot; saranno racchiusi tra virgolette doppie.

_ACP2E-2679 - [Problema GitHub](https://github.com/magento/magento2/issues/38306) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Nessun messaggio di errore appropriato quando l’ID del sito web nella richiesta non è corretto

Ora è stato aggiunto il messaggio di errore appropriato da visualizzare quando l’ID del sito web nella richiesta non è corretto. In precedenza non vi era alcuna convalida quando l’ID del sito web nella richiesta era errato.

_ACP2E-2689 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### L&#39;immagine del prodotto viene persa dopo l&#39;eliminazione di un aggiornamento pianificato esistente che non influisce sull&#39;immagine

Le immagini del prodotto non vengono rimosse durante l’eliminazione dell’aggiornamento di staging.

_ACP2E-2785 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### [Cloud] Prezzo del prodotto del bundle errato se utilizzato con prezzi di livello

Precedentemente, quando si calcolavano determinati sconti percentuali arrotondati a 2 punti decimali, si generavano prezzi finali diversi per il carrello e la pagina di elenco dei prodotti/i dettagli del prodotto. Dopo l’applicazione di questa correzione, il prezzo finale per il prodotto bundle è lo stesso della pagina dei dettagli del prodotto, della pagina di elenco dei prodotti e della pagina del mini carrello.

_ACP2E-2799 - [Problema GitHub](https://github.com/magento/magento2/issues/38091) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### La regola Promozioni catalogo non funziona con l’attributo quantity_and_stock_status

L’attributo quantity_and_stock_status verrà ora preso in considerazione dalla regola di promozione del catalogo, che non era stata precedentemente presa in considerazione durante la generazione di un nuovo prodotto dal lato amministratore.

_ACP2E-2805 - [Problema GitHub](https://github.com/magento/magento2/issues/35627) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/cf34971d)_

#### I valori della colonna update_at dell’entità prodotto non vengono aggiornati durante l’aggiornamento del prezzo tramite API REST

La colonna &quot;Data ultimo aggiornamento&quot; del prodotto da parte dell’amministratore viene aggiornata alla data e all’ora corrette durante l’aggiornamento dei prodotti esistenti tramite l’API REST. In precedenza, la colonna &quot;Ultimo aggiornamento alle&quot; non veniva aggiornata correttamente.

_ACP2E-2837 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### È possibile impostare valori non univoci tramite l’importazione del prodotto

Il sistema ora applica correttamente il vincolo del valore univoco per gli attributi di prodotto univoci durante l’importazione del prodotto, impedendo la presenza di valori duplicati per tale attributo. In precedenza, era possibile impostare valori non univoci per gli attributi del prodotto configurati per avere valori univoci tramite l’importazione del prodotto.

_ACP2E-2840 - [Problema GitHub](https://github.com/magento/magento2/issues/38445) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### I prodotti sul front-end utilizzano dati specifici dell’archivio quando è abilitata la modalità Single-Store

In precedenza, quando si abilitava la modalità archivio singolo per la visualizzazione archivio predefinita, le modifiche non venivano migrate nell’ambito a livello di sito web. Dopo l’applicazione di questa correzione, quando abilitiamo la modalità archivio singolo, i dati predefiniti della visualizzazione archivio verranno sincronizzati con i dati specifici a livello di sito web e risolveranno i possibili conflitti per prodotti e categorie.

_ACP2E-2843 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Impossibile impostare &quot;Ordinamento predefinito&quot; in una categoria utilizzando l’API rest

Aggiornare correttamente default_sort_by in una categoria tramite una richiesta REST/SOAP APi

_ACP2E-2857 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] Il commerciante sta riscontrando problemi con il conteggio della lista dei desideri

L’aggiunta di un prodotto alla lista dei desideri in un negozio non aumenta più il numero di elenchi dei desideri in altri negozi aperti nello stesso browser. In precedenza, se entrambi gli store fossero caricati nello stesso browser, il numero di lista dei desideri aumenterebbe anche nell’altro store.

_ACP2E-2871 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### La pagina Categoria in front-end mostra gli slot vuoti quando si utilizza un prodotto bundle

I prodotti bundle non vendibili nel contesto del negozio corrente non vengono più indicizzati.

_ACP2E-2874 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bc37ec76)_

#### [CHIARIMENTO] problemi relativi alla tabella di sequenza di prodotto del bundle

I record nelle tabelle della sequenza di prodotti del bundle (sequence_product_bundle_option, sequence_product_bundle_selection) vengono ora rimossi quando il prodotto del bundle viene eliminato o le opzioni di prodotto del bundle vengono eliminate.
In precedenza, i record nelle tabelle della sequenza di prodotti Bundle non venivano rimossi.

_ACP2E-2888_

#### [Cloud] problema di offerta nell&#39;architettura di più siti Web

In precedenza, l’architettura multisito con valute e gruppi di clienti diversi non poteva applicare correttamente gli sconti al negozio. Dopo l’implementazione di questa correzione, l’architettura multi-sito con diversi sconti sui prezzi del gruppo di clienti verrà applicata con successo ai diversi store.

_ACP2E-2905 - [Problema GitHub](https://github.com/magento/magento2/issues/38506) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658 TypeError non rilevato: dataRecord.slice durante la modifica di prodotti bundle

Nella console del browser non è presente alcun errore JavaScript durante l’eliminazione dell’opzione dal prodotto bundle.

_ACP2E-2909 - [Problema GitHub](https://github.com/magento/magento2/issues/38505) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### [Cloud] Bundle Prezzi errati del prodotto nella conferma dell&#39;ordine

L&#39;importo corretto viene visualizzato per le opzioni del bundle in ordine su Storefront quando è stata utilizzata una valuta diversa da quella di base.

_ACP2E-2950 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Bug aggiunta video YouTube

Le immagini e i video dei prodotti sono configurati in ambito globale. Poiché non è possibile avere un video di prodotto in un ambito e non in un altro, l’impostazione della chiave API di Youtube è stata impostata su ambito globale.

_ACP2E-2956 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Aggiornamento URL cloud] solo per store_id=0

Il &quot;Percorso URL&quot; viene ora memorizzato con l’ID archivio corretto. In precedenza, l’ID archivio era errato e durante lo spostamento delle categorie continuavano a rimanere nel database percorsi URL errati.

_ACP2E-2964 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all eseguito e creato un errore.

I dati di collegamento del prodotto errati nelle chiamate API REST non causano più errori critici.

_ACP2E-3009 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Cloud] problema mobile Solo non è in grado di pizzicare l&#39;immagine PDP

Il sistema ora supporta la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili su Chrome, migliorando l’esperienza di utilizzo mobile. In precedenza, il doppio tocco sull’immagine nella visualizzazione per dispositivi mobili su Chrome non consentiva di ingrandire l’immagine come previsto.

_ACP2E-3029 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Etichetta mancante in LayeredNavigation con nome opzione 0

Il problema è stato risolto saltando una verifica del valore vuoto per il valore di attributo 0. In precedenza, veniva considerata vuota e causava il problema.

_ACP2E-3058 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### I clienti visualizzano i prezzi di altri gruppi di clienti

È stato risolto un problema a causa del quale le informazioni relative al gruppo di clienti venivano salvate in un segmento errato a causa del vecchio valore di X-Magento-Vary nella richiesta.

_ACP2E-3069 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Errore durante l’eliminazione delle opzioni del bundle

Il sistema ora elimina correttamente le opzioni del bundle senza attivare un errore o impedire la risposta della pagina. In precedenza, se si tentava di eliminare le opzioni del bundle, si verificava un errore &quot;Page Unresponsive&quot; (Non risponde pagina) e si impediva il salvataggio del prodotto.

_ACP2E-3076 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Problema relativo alle autorizzazioni per categoria con browser esaurito

L’interfaccia utente Autorizzazioni categoria è stata riprogettata per consentire il rendering di una grande quantità di autorizzazioni utilizzando il componente dell’interfaccia utente predefinito e la paginazione. In precedenza, le autorizzazioni per la categoria causavano l’arresto anomalo del browser con una grande quantità di autorizzazioni assegnate alla categoria.

_ACP2E-3094_

#### Il file di immagine [Cloud] non esiste nel registro errori di New Relic

Il sistema ora sincronizza le immagini segnaposto personalizzate con l’archiviazione locale, garantendo che vengano riprodotte correttamente quando si utilizza l’archiviazione remota, ad esempio AWS S3. In precedenza, il rendering delle immagini segnaposto personalizzate non riusciva quando si utilizzava l’archiviazione remota, causando una visualizzazione delle immagini interrotta e registri di errori.

_ACP2E-3100 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Il feed RSS dei nuovi prodotti non viene aggiornato con i nuovi prodotti a causa della cache

Il feed Rss per i nuovi prodotti viene ora aggiornato quando un prodotto viene impostato come nuovo e salvato

_ACP2E-3103 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La risposta GQL di [Cloud] Product Media Gallery non è ordinata per posizione immagine

Il sistema ora ordina correttamente gli elementi nella raccolta multimediale in base alla posizione nella risposta del GraphQL, garantendo un ordine di visualizzazione accurato. In precedenza, gli elementi nella raccolta multimediale non venivano ordinati in base alla posizione, causando un ordine di visualizzazione errato.

_ACP2E-3126 - [Problema GitHub](https://github.com/magento/magento2/issues/37671) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### [Gli elementi della sottocategoria cloud] non vengono visualizzati nella modifica dei widget nel backend di amministrazione

La struttura delle categorie nella nuova pagina widget non dovrebbe più presentare problemi nel caricamento delle categorie di livello 5+. In precedenza, mancavano alcune categorie durante il caricamento della struttura oltre le categorie di livello 5.

_ACP2E-3136 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [cloud] problema di zoom e spostamento a due dita sul dispositivo mobile reale

Il sistema ora garantisce una funzionalità di zoom coerente delle immagini sui dispositivi mobili, fornendo un&#39;esperienza utente fluida e prevedibile. In precedenza, la funzione di zoom dell’immagine era incoerente e improvvisamente si riduceva dopo un certo punto quando veniva visualizzata su un dispositivo mobile.

_ACP2E-3198 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Quando si annulla l’assegnazione di prodotti al catalogo condiviso, i prodotti della lista dei desideri non vengono cancellati

Ora, se un prodotto non è disponibile nel catalogo condiviso, non sarà visibile alcun elemento nella lista dei desideri. In precedenza, la pagina della lista dei desideri mostrava erroneamente un conteggio di &quot;1 elemento&quot; anche quando nessun elemento era effettivamente disponibile nella lista dei desideri.

_ACP2E-3282 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Prodotti correlati Seleziona tutto/Deseleziona tutto

In precedenza, i pulsanti &quot;Seleziona tutto&quot;/&quot;Deseleziona tutto&quot; per i prodotti correlati non funzionavano correttamente se un prodotto veniva selezionato manualmente. Dopo la correzione, questi pulsanti ora funzionano in modo coerente, anche dopo la selezione manuale, garantendo che tutti i prodotti siano selezionati correttamente o deselezionati.

_ACP2E-3286 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Cloud] Traduzione dell&#39;avviso tramite posta elettronica Stock nella lingua errata

Quando si inviano avvisi su azioni/prezzi per un sito web con più visualizzazioni del negozio utilizzando lingue diverse, nell’e-mail verrà utilizzata la lingua per la visualizzazione del negozio in cui è stato creato l’avviso.

_ACP2E-3336 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### I nomi delle categorie disabilitate non sono più disattivati nella struttura delle categorie

In precedenza, le categorie disabilitate non erano disattivate nella struttura delle categorie. Ora vengono visualizzate con un effetto di grigio.

_ACP2E-3350 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Il caricamento del modulo di modifica del prodotto può causare timeout e esaurimento della memoria

Prima della correzione, le varianti di prodotto configurabili erano costruite in base a tutte le possibili combinazioni di opzioni di attributo. Nei casi in cui gli attributi disponevano di numerose opzioni, l’operazione risultava lunga e dispendiosa in termini di risorse. Ora le varianti di prodotto configurabili sono costruite in base agli attributi di prodotto secondari esistenti. Ciò comporta un numero molto inferiore di calcoli, quindi un migliore utilizzo delle risorse.

_ACP2E-3410 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Fotorama non carica correttamente il video quando utilizza i campioni e l’opzione è preselezionata tramite URL

Ora i video dei prodotti vengono riprodotti correttamente nella pagina dei dettagli dei prodotti configurabile, se l’URL contiene opzioni selezionate.

_ACP2E-3454 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Il widget Carosello PageBuilder mostra prodotti che non soddisfano le condizioni

L’elenco dei prodotti utilizzati nei widget ora rispetta la condizione della categoria

_ACP2E-3461 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Errore di convalida attivato per tutti i prodotti del gruppo quando una quantità non è valida

Ora, l’errore di convalida viene attivato correttamente per tutti i prodotti del gruppo quando un prodotto ha una quantità non valida, il che non si verificava in precedenza.

_ACP2E-3469 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### [CLOUD] Il prezzo speciale non viene visualizzato nel prodotto configurabile

Dopo la correzione, la modifica del valore &quot;Usato nell’elenco dei prodotti&quot; per l’attributo di prezzo speciale non influirà sulla visualizzazione del prezzo speciale per i prodotti configurabili.

_ACP2E-3513 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### Indicizzatori Le tabelle temporanee non vengono pulite se il processo viene terminato

Le tabelle temporanee dell&#39;indicizzatore CatalogRule vengono ora pulite se il processo di indicizzazione viene terminato

_ACP2E-3516 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [QUANS] errori di unit test di base in 2.4.7-p3

Le note sulla versione di questo test non sono necessarie in quanto si tratta di un miglioramento di unit test.

_ACP2E-3520 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Problema di prestazioni nel recupero della quantità delle scorte per i prodotti raggruppati con più origini

La pagina di modifica di prodotto raggruppato e bundle è ora ottimizzata quando i prodotti assegnati hanno un numero elevato di sorgenti di inventario.

_ACP2E-3533 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/0208e433)_

#### Ripristina ACP2E-3389

Sono state migliorate le prestazioni della pagina categoria amministratore in caso di numero elevato di categorie di ancoraggio

_ACP2E-3641 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogo, contenuto

#### La cache [Cloud] non viene invalidata.

In precedenza, quando si salvava una pagina CMS con un layout di progettazione aggiornato, questa non veniva riflessa in modo appropriato nel front-end. Una volta applicata questa correzione, il layout di progettazione appropriato sarà visibile nel front-end quando si modifica il layout di progettazione e si salva la pagina CMS.

_ACP2E-3063 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [Categorie di ancoraggio/non di ancoraggio di Cloud] invertite nel widget contenuto

In precedenza, quando si selezionava Visualizza su -> Categorie di ancoraggio, venivano visualizzate tutte le categorie che non riflettevano la relazione padre-figlio tra l&#39;ancoraggio e il non ancoraggio. Dopo l&#39;applicazione di questa correzione, Visualizza attivato -> Categorie di ancoraggio visualizza solo le Categorie di ancoraggio (selezionabile), mentre Visualizza attivato -> Categorie non di ancoraggio visualizza le Categorie non di ancoraggio (selezionabile)

_ACP2E-3131 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Categorie che non funzionano con i widget

In precedenza, se salvavamo il blocco CMS per diverse categorie di ancoraggio/non di ancoraggio, non funzionava per le categorie figlio quando veniva visualizzato sul front-end. Dopo l’applicazione di questa correzione, il blocco viene visualizzato nel front-end per diverse categorie.

_ACP2E-3152 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

### Catalogo, Framework

#### Recupero ordine(Spedizioni|Note di accredito|Fattura)Raccolta - La raccolta non deve essere caricata

Il sistema ora assicura che le raccolte per le spedizioni e le note di credito non vengano precaricate quando vengono recuperate da un ordine, consentendo l&#39;applicazione di filtri o ordini aggiuntivi a tali raccolte. In precedenza, queste raccolte venivano caricate automaticamente, impedendo ulteriori modifiche.

_AC-9111 - [Problema GitHub](https://github.com/magento/magento2/issues/37561) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37562)_

#### [Cloud]Completamento: mancata corrispondenza nel confronto dei dati durante la verifica della presenza di modifiche nei dati

In precedenza, l’oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica di dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Inoltre, non controlla i numeri mobili incapsulati da stringa. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa

_ACP2E-2949 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

### Catalogo, GraphQL

#### Gestione dei filtri delle categorie in GraphQL: includeDirectChildrenOnly e category_uid

Durante il filtraggio per category_uid vengono recuperate solo le categorie figlio dirette.

_ACP2E-3090 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### [L&#39;ordinamento dei prodotti Graphql per cloud] non funziona

L’ordinamento dei prodotti GraphQl per più campi quando i campi vengono passati nelle variabili ora funziona come previsto.

_ACP2E-3166 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### I prezzi di livello restituiscono un valore errato nei prodotti GraphQL (rispetto a Storefront)

Dopo la correzione, i prezzi del livello del prodotto restituiti per le richieste graphql hanno prezzo per un articolo.

_ACP2E-3312 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] B2B: problema di categoria tramite GraphQL

Dopo la correzione, la query graphql delle categorie restituisce le categorie con l’autorizzazione Consenti anche se la categoria principale non dispone dell’autorizzazione Consenti.

_ACP2E-3385_

### Catalogo, prezzi, staging e anteprima

#### L&#39;endpoint API a prezzo speciale di [Cloud] restituisce un errore quando si aggiornano contemporaneamente numerosi prodotti

Ora l’API per l’aggiornamento in blocco dei prezzi speciali creerà una singola campagna per ogni intervallo di date invece di più aggiornamenti pianificati per ogni prodotto e intervallo di date. Inoltre, supporterà le richieste API simultanee per un’elaborazione più rapida di un gran numero di SKU.

_ACP2E-2672 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

### Catalogo, prodotto

#### La struttura di selezione delle categorie in Modifica prodotto non è nello stesso ordine impostato in Catalogo->Categorie

Il sistema ora visualizza correttamente la struttura di selezione delle categorie nella sezione di modifica del prodotto nello stesso ordine impostato in Catalogo->Categorie, semplificando l’amministrazione dei prodotti nei cataloghi di grandi dimensioni. In precedenza, la struttura ad albero delle categorie nella sezione di modifica del prodotto veniva visualizzata in ordine di creazione delle categorie, indipendentemente dall’ordine di visualizzazione impostato in Catalogo->Categorie.

_AC-7050 - [Problema GitHub](https://github.com/magento/magento2/issues/36101) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36104)_

### Catalogo, SEO

#### URL canonico errato per la categoria quando pagina > 1

In precedenza, l’URL canonico per il contenuto multipagina non funzionava correttamente, visualizzando in modo coerente l’URL di base. Tuttavia, dopo l’implementazione della correzione, l’URL canonico per i contenuti con più pagine ora visualizza correttamente l’URL con l’ID pagina.

_ACP2E-3653 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogo, Ricerca

#### I prodotti non vengono visualizzati nella categoria e nella ricerca, ma i collegamenti diretti funzionano

In precedenza, l’attributo personalizzato Sì/No con price_* attribute_code non funzionava con l’indicizzazione. Dopo questa correzione, l’attributo personalizzato Sì/No funziona come previsto.

_ACP2E-2757 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### [Cloud] Errore di ricerca elastica in alcune pagine della categoria

In precedenza, con il ticket di configurazione menzionato, quando si inseriva il prezzo 0 per più prodotti, veniva generata un’eccezione nella pagina della categoria front-end. Dopo che questa correzione è stata applicata quando più prezzi del prodotto 0 e la pagina della categoria viene caricata in front-end, non viene generata alcuna eccezione e la pagina della categoria viene caricata correttamente.

_ACP2E-3053 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Errore di tipo durante la creazione dell&#39;oggetto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception

Dopo la correzione, è possibile creare un&#39;istanza della classe Magento\CatalogSearch\Model\Indexer\Fulltext senza specificare $data.

_ACP2E-3345 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [Il problema di CLOUD] con i prodotti non è visibile in FrontEnd dopo il salvataggio in Magento Admin

Dopo la correzione i prodotti configurabili che hanno prodotti secondari con nomi lunghi non verranno persi nella vetrina.

_ACP2E-3521 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Catalogo, spedizione

#### Indirizzo di spedizione vuoto durante l&#39;invio di un ordine per un articolo del registro regali

In precedenza, per gli elementi del registro regali degli utenti ospiti, quando venivano restituiti dalla funzione e-mail, veniva generato un indirizzo vuoto, che non era corretto per l’ordine. Dopo l&#39;applicazione di questa correzione, il Registro di sistema per i regali controlla gli utenti connessi/ospiti e gli indirizzi assegnati, se presenti.

_ACP2E-3195_

### Cloud

#### [Cloud] PHPSESSID sta modificando ogni richiesta POST

PHPSESSID non viene più rigenerato nelle richieste POST sull&#39;area front-end per un cliente connesso se la cache L2 Redis è abilitata e il cliente è stato aggiornato dal back-end

_ACP2E-3010 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Avvisi di generazione sitemap

Dopo la correzione, la mappa del sito viene generata nella directory tmp del sistema e copiata nella destinazione finale.

_ACP2E-3532 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Contenuto

#### [Problema] relativo alla visualizzazione del prezzo nel widget Visualizzato di recente

Il sistema ora visualizza correttamente il prezzo dei prodotti semplici esauriti nel widget &quot;Prodotto visualizzato di recente&quot;, garantendo la coerenza tra tutti i widget e le pagine dell’elenco dei prodotti. In precedenza, il prezzo dei prodotti semplici esauriti non veniva visualizzato nel widget &quot;Prodotto visualizzato di recente&quot; a causa di una condizione nei modelli di caricamento del prezzo.

_AC-10539 - [Problema GitHub](https://github.com/magento/magento2/issues/38167) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38159)_

#### [Problema] Digitare e grammatica corretti nel file acl.xsd

Il sistema ora corregge un errore di battitura e grammatica nel file acl.xsd, migliorando la chiarezza e l’accuratezza della documentazione. In precedenza, il file acl.xsd conteneva un errore ortografico e grammaticale non corretto che poteva causare confusione.

_AC-10596 - [Problema GitHub](https://github.com/magento/magento2/issues/38061) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38046)_

#### L&#39;immagine del banner di Pagebuilder non è visibile nella raccolta

Il sistema ora visualizza correttamente le immagini del banner caricate nelle cartelle appena create nella raccolta Pagebuilder, eliminando gli errori precedenti della console. Prima di questa correzione, le immagini del banner non erano visibili nella raccolta se venivano caricate in una nuova cartella, causando un errore nella console.

_AC-10845 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### &quot;Codice di zona non impostato&quot; dopo l’aggiornamento a 2.4.5-p8

Il sistema ora completa correttamente il processo di distribuzione del contenuto statico quando il modulo Magento_CSP è abilitato e &quot;dev/js/translate_strategy&quot; è impostato su &quot;embedded&quot;, senza attivare l’errore &quot;indicativo di località non impostato&quot;. In precedenza, in queste condizioni, il processo di distribuzione del contenuto statico non riusciva e veniva visualizzato un errore di tipo &quot;Codice di area non impostato&quot;.

_AC-12283 - [Problema GitHub](https://github.com/magento/magento2/issues/38845) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38922)_

#### La struttura delle categorie del widget non viene rappresentata correttamente

_AC-12692 - [Problema GitHub](https://github.com/magento/magento2/issues/39008) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/58e40ceb)_

#### Impossibile visualizzare il messaggio &quot;Using Default value&quot; (Utilizzo del valore predefinito) quando si modifica il tema nella pagina di configurazione della progettazione

Il sistema ora include una colonna separata per visualizzare il messaggio &quot;Using Default value&quot; (Uso del valore predefinito) a seconda del tema selezionato nella pagina di configurazione della progettazione. Questo garantisce chiarezza e visibilità dello stato del valore predefinito. In precedenza, il messaggio &quot;Using Default value&quot; (Utilizzo del valore predefinito) non veniva visualizzato, generando confusione sullo stato del tema selezionato.

_AC-13054 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Ripristina nuovamente la compatibilità con i plug-in TinyMCE (dopo...

Il sistema ora ripristina la compatibilità con le versioni precedenti dei plug-in TinyMCE, consentendo di chiamare le funzioni definite all&#39;interno del plug-in quando si utilizza il widget da un&#39;altra posizione. In precedenza, a causa di una modifica nella versione TinyMCE, i plug-in non restituivano i widget come oggetto, causando un errore quando si tentava di chiamare alcune funzioni sull’istanza del widget.

_AC-13569 - [Problema GitHub](https://github.com/magento/magento2/issues/39262) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39258)_

#### [Problema] problema di caricamento file nell&#39;editor di WYSIWYG nella pagina del prodotto

Il sistema ora visualizza correttamente la struttura ad albero delle cartelle e consente il caricamento di immagini nell’editor WYSIWYG sulla pagina del prodotto, anche dopo aver espanso prima la scheda &quot;Immagine e video&quot;. In precedenza, l’espansione della scheda &quot;Immagini e video&quot; causava prima la mancata visualizzazione della struttura delle cartelle e un messaggio di errore durante il caricamento di un’immagine nell’editor di WYSIWYG.

_AC-9638 - [Problema GitHub](https://github.com/magento/magento2/issues/38026) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38025)_

#### [On-PREM] problema di blocco dinamico

Il rendering dei widget ora viene eseguito correttamente all’interno dei blocchi dinamici.

_ACP2E-2392 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### L’URL nocookie di YouTube non funziona in Page Builder

Ora il generatore di pagine consente l’URL senza cookie di youtube nelle impostazioni dell’elemento modulo delle regole di convalida. In precedenza, l’URL youtube senza cookie non funzionava in pagebuilder.

_ACP2E-2606_

#### [Cloud] Frontend non si carica a causa di un problema nel modello di newsletter

L’aggiunta di blocchi tramite la sezione del contenuto di una pagina CMS non causa più un’eccezione

_ACP2E-2693 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Cloud] Rilevata eccezione di analisi nel registro: InvalidArgumentException: la classe non esiste in vendor/magento/module-rule/Model/ConditionFactory.php

La rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder non causa più la registrazione di un&#39;eccezione nei file di registro. In precedenza, la rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder causava la registrazione di un’eccezione critica nei registri, nonostante non causasse problemi sul front-end.

_ACP2E-2836 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### Passaggio alla modalità archivio singolo: il contenuto globale non viene più visualizzato

Ora il sistema sincronizza le configurazioni di progettazione della vista archivio con le configurazioni di progettazione del sito web quando si abilita la modalità di archiviazione singola, garantendo che gli aggiornamenti del contenuto siano visibili sul front-end. In precedenza, il passaggio alla modalità single store impediva che gli aggiornamenti dei contenuti venissero rispecchiati nella vetrina.

_ACP2E-2842 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Page Builder sostituisce l’immagine quando tenta di aggiungere un collegamento e altri errori di usabilità.

Facendo clic su un&#39;immagine, i collegamenti nell&#39;editor wysiwyg nell&#39;elemento di testo Page Builder verranno caricati i dati corretti nella finestra di dialogo immagine, configurazione collegamento. Anche l’aggiunta di un collegamento a un’immagine nell’editor ora funziona correttamente. In precedenza, l’immagine veniva sostituita da un collegamento.

_ACP2E-2903 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### La galleria di vecchi supporti non riesce a eseguire il rendering delle immagini quando si inserisce un&#39;immagine a 0 byte nella directory

Il sistema ora gestisce le immagini a 0 byte nella raccolta multimediale senza interrompere la funzionalità, consentendo la visualizzazione e la selezione di altre immagini nella directory come previsto. In precedenza, la presenza di un&#39;immagine a 0 byte nella raccolta multimediale impediva la visualizzazione o la selezione di tutte le immagini nella directory.

_ACP2E-2970 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Errore di Page Builder durante la modifica del blocco CMS

Il sistema ora salva correttamente le modifiche apportate nell’area di amministrazione utilizzando Page Builder, senza generare l’errore &quot;Page Builder ha eseguito il rendering per 5 secondi senza rilasciare blocchi&quot;. nella console del browser. In precedenza, questo errore si verificava quando si tentava di salvare le modifiche, impedendo il corretto aggiornamento del contenuto.

_ACP2E-3064 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [CLOUD] Nessun pulsante di estrazione o modifica del carrello nella sezione carrello

Il prodotto bundle ora viene aggiunto al carrello tramite widget senza errori.

_ACP2E-3092 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### L’anteprima di staging del contenuto nelle pagine delle categorie non mostra i widget del prodotto

Il problema è stato risolto assicurando che le voci dei prodotti per la categoria aggiuntiva collegata al blocco CMS siano state correttamente registrate nel database. In precedenza, restituiva un set di risultati vuoto quando veniva richiesta la pagina di anteprima della categoria.

_ACP2E-3113_

#### [CLOUD] Il pulsante Carica immagine non funziona

Prima il pulsante Carica immagine per il banner e il cursore da PageBuilder non funzionava come previsto e ora quando si preme si apre il file manager locale per selezionare l&#39;immagine da caricare.

_ACP2E-3122 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor(): il #2 dell&#39;argomento ($height) deve essere maggiore di 0. Impossibile caricare un’immagine specifica

È stato risolto il problema che causava errori nell’amministratore durante il caricamento di immagini con altezza pari a 0 tramite la raccolta multimediale ed è stata eseguita con successo la sincronizzazione delle risorse tramite il comando sync. In precedenza non era possibile caricare l’immagine tramite la raccolta multimediale e il comando di sincronizzazione ha esito negativo anche quando un’immagine specifica si trova nella raccolta.

_ACP2E-3127 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js Array.from è in conflitto con l’API di Google Maps

Google Maps ora viene eseguito correttamente nell’editor di PageBuilder. In precedenza, un errore JavaScript impediva il corretto rendering di Google Maps.

_ACP2E-3154 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] - Il cursore di CMS non riflette le ultime modifiche

Il problema è stato risolto assicurandosi che l’elenco di dispositivi di scorrimento venga aggiornato mentre l’evento di salvataggio viene attivato nella schermata di modifica della diapositiva. In precedenza, si attivava e causava il problema.

_ACP2E-3275 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Si verifica un errore nella pagina CSM quando i blocchi CMS vengono inseriti utilizzando il generatore di pagine in un determinato ordine

In precedenza, su alcune versioni di PHP e OS (Linux), il rendering dei blocchi che facevano riferimento ad altri blocchi CMS attraverso PageBuilder non sarebbe riuscito con un &quot;Si è verificato un errore sconosciuto. Riprova.&quot;. Ora il contenuto dei blocchi cms viene riprodotto correttamente all’interno di un contenuto controllato da PageBuilder.

_ACP2E-3326 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### [Cloud] blocchi dinamici non funzioneranno correttamente

I segmenti dei clienti connessi vengono ora cancellati dopo la disconnessione, impedendo alla sessione guest di ereditare i segmenti precedentemente connessi

_ACP2E-3388_

#### Errore di anteprima del modello Pagebuilder per contenuti di grandi dimensioni

Contenuto di grandi dimensioni causava l’overflow dell’elemento canvas nei limiti del browser e la restituzione di un valore errato, con conseguente interruzione del codice di back-end (impossibile decodificare correttamente l’immagine). È stato corretto limitando le dimensioni dell’area di lavoro al limite del browser universale.

_ACP2E-3428 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### Ultimi aggiornamenti di sicurezza con dimensione font mancante per TinyMCE 7

I selettori delle dimensioni e della famiglia di caratteri sono ora disponibili in WYSIWYG Editor. Prima di questa correzione, con TinyMCE 7 queste non erano disponibili nell’interfaccia dell’editor.

_ACP2E-3430 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### Dimensione font dell’editor TinyMCE 7 nell’amministratore in PT e non PX, chiarisci

Prima della correzione non era possibile specificare la dimensione del font in pixel nelle aree WYSIWYG. Ora è possibile impostare la dimensione del carattere in px anziché in pt.

_ACP2E-3483 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### Il tipo di contenuto del prodotto in Page Builder viene compresso senza messaggi corretti

Prima della correzione, l’html di anteprima non veniva generato correttamente se il widget non conteneva prodotti. Ora la risposta vuota viene generata correttamente e il widget prodotti viene visualizzato correttamente nell’anteprima.

_ACP2E-3490 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [Page Builder]L&#39;aggiunta dell&#39;elenco dei prodotti per bloccare i risultati genera errori

L’aggiunta dell’elenco dei prodotti del bundle al blocco tramite Page Builder non genera errori

_ACP2E-3534 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Contenuto, SEO

#### La gerarchia delle pagine CMS può causare problemi di riscrittura degli URL

In precedenza, per la riscrittura permanente degli URL personalizzata per le pagine principali non relative al sito web, il reindirizzamento era infinito e la pagina non veniva mai caricata. Dopo l’applicazione di questa correzione, la riscrittura dell’URL personalizzato per la pagina principale non del sito web funziona come previsto e non si verifica alcun ciclo di reindirizzamento.

_ACP2E-2870_

### Contenuto, staging e anteprima

#### La regola del prezzo di catalogo non viene visualizzata se è impostata per la pianificazione con blocchi dinamici

Il sistema ora visualizza correttamente il contenuto dinamico associato alle regole del prezzo di catalogo programmato nella pagina dei dettagli del prodotto. In precedenza, il caricamento del contenuto dinamico non riusciva quando venivano pianificate le regole del prezzo di catalogo.

_ACP2E-2979_

### Cliente/clienti

#### Front-end - Convalida della data di nascita non riuscita nella pagina di creazione del cliente

Assicurati che tutta la convalida funzioni dopo la dipendenza del sistema moment.js dall’aggiornamento alla versione secondaria più recente

_AC-12162 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Segmento cliente > Condizione > Cronologia prodotto* > &quot;prodotto visualizzato&quot; non funziona

Ora il sistema visualizza correttamente i clienti registrati corrispondenti nella condizione &quot;Prodotto visualizzato&quot; in Segmenti cliente, quando la condizione viene soddisfatta. In precedenza, anche quando la condizione veniva soddisfatta, il numero di clienti registrati corrispondenti rimaneva pari a zero.

_AC-13060_

#### Il campo di testo dell’area geografica non viene reimpostato quando viene modificato il menu a discesa del paese

Il sistema ora reimposta il campo di testo dell&#39;area geografica quando il paese viene modificato nel menu a discesa, assicurandosi che i valori precedenti non persistano. In precedenza, la modifica del paese dall’elenco a discesa non reimpostava il campo area e veniva mantenuto l’ultimo valore salvato.

_AC-8499 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### L&#39;eliminazione del cliente non cancella tutti i dati della sessione del browser su Storefront per il cliente connesso ed eliminato

L’eliminazione di un cliente ora pulisce tutti i dati della sessione del browser dalla vetrina per i clienti che hanno effettuato l’accesso e per quelli eliminati, come previsto. L’acquirente può continuare a fare acquisti e il browser tratta la sua sessione come una sessione ospite. In precedenza, quando l’account del cliente per un acquirente connesso veniva eliminato dall’amministratore, il browser dell’acquirente generava errori JavaScript.

_AC-9240 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

### Framework

#### [Domanda]Configurazione tipo inutilizzato in `app/code/Magento/Translation/etc/di.xml`

Il sistema ora rimuove le dipendenze inutilizzate nella configurazione, migliorando la pulizia e l’efficienza complessiva del codice. In precedenza, nella configurazione vi erano dipendenze non utilizzate che non contribuivano ad alcuna funzionalità.

_AC-10037 - [Problema GitHub](https://github.com/magento/magento2/issues/38030) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38064)_

#### V1/customers/password endpoint question/issue

Il sistema ora rispetta i vincoli impostati all&#39;interno dell&#39;interfaccia grafica di gestione quando elabora le richieste di modifica della password tramite l&#39;API, impedendo il potenziale abuso della funzione di reimpostazione della password. In precedenza, l’API poteva elaborare richieste di modifica della password al di fuori delle regole definite nell’interfaccia grafica di gestione, consentendo potenzialmente un flusso costante di e-mail di reimpostazione se erano note e-mail valide.

_AC-10654 - [Problema GitHub](https://github.com/magento/magento2/issues/38238) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### La configurazione della vernice non esclude tutti i parametri di marketing

Il sistema ora esclude correttamente tutti i parametri di marketing comuni nella configurazione di Vernice, garantendo un tracciamento e un’analisi accurati. In precedenza, alcuni parametri di marketing, come gad_source, srsltid e msclkid, non venivano esclusi, generando potenziali imprecisioni nella raccolta dei dati.

_AC-10738 - [Problema GitHub](https://github.com/magento/magento2/issues/38298) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39188)_

#### Processo di indicizzazione errori processo indice di ricerca catalogo

Il sistema ora completa correttamente il comando di reindicizzazione senza incontrare errori, indipendentemente dalla versione libxml compilata con PHP. In precedenza, l’esecuzione del comando di reindicizzazione causava un errore di &quot;Errore di processo dell’indice di ricerca del catalogo durante il processo di indicizzazione&quot; quando PHP veniva compilato con determinate versioni di libxml.

_AC-10838 - [Problema GitHub](https://github.com/magento/magento2/issues/38254) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38553) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Sono stati aggiunti i filtri created_at, status e grand_total alla query Ordini del cliente e sono stati corretti più errori di filtro

Il sistema ora supporta l’utilizzo di filtri created_at, status e grand_total nelle query Ordini cliente e ha risolto un problema che impediva la corretta applicazione di più filtri. In precedenza, il sistema non supportava questi filtri e non applicava tutti i filtri quando in una query ne veniva utilizzato più di uno.

_AC-10941 - [Problema GitHub](https://github.com/magento/magento2/issues/38392) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36949)_

#### Ricevere in modo casuale inondazioni di query da blocchi correlati / upselling / crossselling e indicizzazione dei prezzi

Il sistema ora ottimizza le query da blocchi correlati, di upselling e di cross-selling, migliorando le prestazioni ed evitando che il sito si abbassi a causa di query eccessive. In precedenza, il sistema poteva essere sovraccarico di query provenienti da questi blocchi, causando rallentamenti significativi e potenzialmente riducendo il sito.

_AC-10991 - [Problema GitHub](https://github.com/magento/magento2/issues/36667) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38050)_

#### Eccezione: Avviso: tentativo di accedere all&#39;offset dell&#39;array in... -> Calendar.php dall&#39;aggiornamento a ICU 74.1 (PHP Intl)

Commerce non registra più la seguente eccezione in exception.log ogni volta che un acquirente o un commerciante visita la vetrina o l&#39;amministratore: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [Problema GitHub](https://github.com/magento/magento2/issues/38214) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38364)_

#### [Problema] Correggi i problemi relativi ai dati dei clienti quando il modulo contiene un elemento con nome `method`

Il sistema ora identifica correttamente l’attributo &quot;method&quot; nell’invio del modulo, anche quando nel modulo è presente un elemento denominato &quot;method&quot;. In questo modo i dati dei clienti vengono elaborati con precisione. In precedenza, se un elemento modulo fosse denominato &quot;metodo&quot;, interferirebbe con l’identificazione dell’attributo &quot;metodo&quot; nell’invio dei moduli, causando potenziali problemi con la gestione dei dati dei clienti.

_AC-11476 - [Problema GitHub](https://github.com/magento/magento2/issues/38484) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38449)_

#### [Problema] Correzione dei PHPDocs per \Magento\Framework\Data\Collection::getItemById

I PHPDocs per il metodo \Magento\Framework\Data\Collection::getItemById sono stati aggiornati per includere null come possibile tipo restituito, risolvendo i problemi con gli strumenti di analisi statica. In precedenza, i PHPDocs del metodo non specificavano null come possibile tipo restituito, generando avvisi o errori nell&#39;analisi statica quando il metodo veniva utilizzato nelle istruzioni condizionali.

_AC-11489 - [Problema GitHub](https://github.com/magento/magento2/issues/38485) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38439)_

#### [Problema] Consenti solo preferenze valide durante `setup:di:compile`

Se viene creata una preferenza per una classe che non esiste o che è specificamente esclusa, il sistema genera ora un errore durante il comando `setup:di:compile`, assicurandosi che siano consentite solo le preferenze valide. In precedenza, questi scenari avrebbero avuto esito negativo in silenzio, rendendo potenzialmente inutili i plug-in associati alle classi originali.

_AC-11592 - [Problema GitHub](https://github.com/magento/magento2/issues/38517) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33161)_

#### Magento sta tentando di modificare la proprietà di sola lettura nel metodo __wakeup di LoggerProxy

Il sistema ora consente di modificare le proprietà di sola lettura precedenti nel metodo di riattivazione __LoggerProxy, garantendo un funzionamento senza forzare gli utenti a utilizzare una soluzione alternativa. In precedenza, si verificavano problemi se si tentava di riassegnare il valore di una proprietà di sola lettura nel metodo di riattivazione __LoggerProxy.

_AC-11651 - [Problema GitHub](https://github.com/magento/magento2/issues/38526) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### [Problema] AC-2039 AC-1667 aggiornamento riferimenti TinyMCE

Versione aggiornata più recente di tinymce in compositore.json

_AC-11681 - [Problema GitHub](https://github.com/magento/magento2/issues/38533) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36543) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker non funziona in più thread

Il sistema ora supporta il fork di processo per l&#39;indicizzazione MView, evitando errori durante l&#39;esecuzione dell&#39;indicizzatore quando si opera su più thread. In precedenza, l’esecuzione di ChangelogBatchWalker su più thread determinava l’eliminazione delle tabelle utilizzate da altri thread, causando un errore durante l’esecuzione dell’indicizzatore.

_AC-11696 - [Problema GitHub](https://github.com/magento/magento2/issues/38246) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38248)_

#### [Problema] Rinominare la variabile con nome errato

Il sistema ora assegna correttamente i nomi alla variabile che contiene la quantità di denaro che può ancora essere rimborsata, evitando confusione durante il debug. In precedenza, questa variabile veniva erroneamente denominata totalRefund, il che poteva generare malintesi per gli sviluppatori.

_AC-11781 - [Problema GitHub](https://github.com/magento/magento2/issues/38609) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36205)_

#### [Problema] Trasmettere gli attributi personalizzati al collegamento corrente tramite XML

Il sistema ora consente di passare gli attributi personalizzati al collegamento corrente tramite XML, garantendo che vengano visualizzati correttamente anche quando il collegamento è nella pagina corrente. In precedenza, gli attributi personalizzati non venivano visualizzati per il collegamento della pagina corrente perché il metodo getAttributesHtml() non veniva utilizzato per il collegamento corrente.

_AC-11809 - [Problema GitHub](https://github.com/magento/magento2/issues/38500) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30070)_

#### La cache FPC integrata è interrotta nella versione 2.4.7 per alcune configurazioni

Ora il sistema memorizza correttamente nella cache le pagine quando è impostato il parametro MAGE_RUN_CODE, garantendo prestazioni ottimali. In precedenza, le pagine non venivano memorizzate nella cache in queste condizioni, causando potenziali problemi di prestazioni.

_AC-11819 - [Problema GitHub](https://github.com/magento/magento2/issues/38626) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38646) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [Problema] è stata corretta l&#39;incoerenza nella gestione delle eccezioni tra le modalità di sviluppo e produzione

Il sistema ora gestisce in modo coerente le eccezioni tra le modalità di sviluppo e di produzione, evitando il reindirizzamento imprevisto alla pagina di accesso quando viene generata un’eccezione. In precedenza, un’incoerenza nella gestione delle eccezioni poteva causare un reindirizzamento alla pagina di accesso in modalità di produzione invece di visualizzare il messaggio di eccezione.

_AC-11829 - [Problema GitHub](https://github.com/magento/magento2/issues/38639) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37712)_

#### Sostituisci la traduzione &#39;PayPal Account&#39; in token_list.phtml

Il sistema ora etichetta la sezione per i metodi di pagamento con conto &quot;tokenizable&quot; come &quot;Account&quot; invece di &quot;Conto PayPal&quot; nella pagina Metodi di pagamento memorizzati, rendendola più rappresentativa della sua funzione. In precedenza, questa sezione era specificamente etichettata come &quot;Conto PayPal&quot;, che era fuorviante quando sono stati aggiunti altri metodi di pagamento per account tokenizable.

_AC-11852 - [Problema GitHub](https://github.com/magento/magento2/issues/35622) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37959)_

#### Compatibilità con le versioni precedenti persa nella classe Magento\Catalog\Model\ProductRepository

La classe ProductRepository ora mantiene la compatibilità con le versioni precedenti ripristinando la classe Initialization Helper come secondo parametro, garantendo che i moduli che si estendono da questa classe funzionino come previsto. In precedenza, la rimozione di Initialization Helper dal costruttore nella classe ProductRepository comportava una perdita di compatibilità con le versioni precedenti, costringendo gli utenti a utilizzare una soluzione alternativa.

_AC-11874 - [Problema GitHub](https://github.com/magento/magento2/issues/38669)_

#### [Problema] Distribuzione contenuto statico - Errore di tipo

Il sistema ora gestisce correttamente i file LESS vuoti durante la distribuzione del contenuto statico, visualizzando un messaggio di errore &quot;LESS file is empty&quot;. In precedenza, veniva generato un errore di tipo errato quando si incontrava un file LESS vuoto durante la distribuzione.

_AC-11905 - [Problema GitHub](https://github.com/magento/magento2/issues/38682) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38683)_

#### [Problema] [Visualizzazione] Spazio aggiuntivo rimosso nel tag collegamento e script

Il sistema ora assicura che non vi siano spazi aggiuntivi nei tag di collegamento e script, fornendo un codice più pulito ed efficiente. In precedenza, si trovavano doppi spazi tra gli attributi nei tag link e script.

_AC-12002 - [Problema GitHub](https://github.com/magento/magento2/issues/32920) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32919)_

#### [Problema]: evitare un ciclo infinito di configurazione errata

Il sistema ora evita un ciclo infinito impedendo la mappatura autoreferenziale nelle configurazioni di tipo virtuale. In questo modo l’applicazione non si blocca in un ciclo infinito quando si tenta di dereferenziare un nodo autoreferenziale. In precedenza, se una configurazione di tipo virtuale fosse autoreferenziale, l’applicazione girerebbe indefinitamente.

_AC-12127 - [Problema GitHub](https://github.com/magento/magento2/issues/38822) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38794)_

#### Object Manager non utilizzato per Magento\Csp\Model\Mode\Data\ModeConfigured

Il sistema ora utilizza correttamente Object Manager durante la creazione dell&#39;oggetto ModeConfigured, consentendo l&#39;utilizzo di plug-in su questo oggetto. In precedenza, Object Manager non veniva utilizzato, impedendo l’applicazione dei plug-in all’oggetto ModeConfigured.

_AC-12299 - [Problema GitHub](https://github.com/magento/magento2/issues/38875) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38886)_

#### Commento non accurato per blocchi di documenti in Avvisi su scorte di prodotto e prezzi

Il commento del blocco del documento per il metodo deleteCustomer negli avvisi di prezzo e scorte prodotto è stato corretto per riflettere con precisione il fatto che il metodo elimina tutti gli avvisi di prezzo o prodotto di magazzino associati a un determinato cliente e sito Web, non il cliente dal sito Web. In precedenza, il commento affermava erroneamente che il metodo era quello di eliminare un cliente dal sito web.

_AC-12540 - [Problema GitHub](https://github.com/magento/magento2/issues/38939) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39001)_

#### [Problema] Utilizza la configurazione compilata per i dati generati invece della configurazione generale

Il sistema ora utilizza la configurazione compilata per i dati generati invece della configurazione generale, riducendo il trasferimento di rete e il sovraccarico dei dati che dipende da una determinata versione del codice. Questa modifica impedisce l’override della cache nelle istanze condivise durante lo scambio dei contenitori, migliorando la stabilità e riducendo i tempi di inattività. In precedenza, alcune classi principali utilizzavano il tipo di configurazione condiviso, che poteva causare l’override della cache o tempi di inattività dell’applicazione a causa delle differenze nelle versioni del codice tra più server.

_AC-12594 - [Problema GitHub](https://github.com/magento/magento2/issues/38785) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29954)_

#### [Problema] Rimozione dei riferimenti ai file da extjs rimossi in e1ccdb...

Il sistema ora rimuove i riferimenti ai file da extjs che erano stati precedentemente rimossi, eliminando gli errori nella console del browser e nel file di registro del sistema. In precedenza, questi riferimenti causavano errori a causa dell’assenza dei file di riferimento.

_AC-12597 - [Problema GitHub](https://github.com/magento/magento2/issues/38960) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38951)_

#### [Problema] Pulizia minore: è stato corretto l&#39;utilizzo errato di sprintf. Sono necessari solo due segnaposto qui e...

Il sistema ora utilizza correttamente la funzione sprintf con il numero appropriato di segnaposto, migliorando la pulizia e la coerenza del codice. In precedenza, la funzione sprintf veniva erroneamente utilizzata con un argomento aggiuntivo, che non causava problemi importanti ma non era l’utilizzo corretto.

_AC-12778 - [Problema GitHub](https://github.com/magento/magento2/issues/39062) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38628)_

#### PHP 8.2.15 ha rimosso l&#39;estensione FTP

Il sistema ora include l’estensione FTP come dipendenza nel file compositore.json, garantendo la corretta configurazione delle importazioni CSV tramite FTP. In precedenza, veniva generato un errore durante il tentativo di configurare le importazioni CSV tramite FTP a causa dell’assenza dell’estensione FTP nel pacchetto PHP.

_AC-12857 - [Problema GitHub](https://github.com/magento/magento2/issues/39083) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Corregge le classi errate a cui si fa riferimento nei moduli Magento.

Il sistema ora fa correttamente riferimento alle classi nei moduli, garantendo un funzionamento più fluido ed evitando arresti anomali dovuti a classi non esistenti. Ciò include un bug nei moduli Indexer e Creditmemo e l&#39;implementazione di HttpGetActionInterface nella classe PrintAction. In precedenza, i riferimenti di classe errati causavano errori e potenziali arresti anomali del sistema, e alcune funzionalità, come il nome del file creditmemo PDF e la reindicizzazione delle scorte, non funzionavano come previsto.

_AC-12869 - [Problema GitHub](https://github.com/magento/magento2/issues/39126) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37784)_

#### Possibilità di definire l&#39;area per il comando CLI `dev:di:info`

Il sistema ora consente agli sviluppatori di definire un&#39;area per il comando CLI `dev:di:info`, migliorando il processo di sviluppo e debug. In precedenza, questo comando consentiva di visualizzare solo le informazioni relative all&#39;area GLOBAL.

_AC-12964 - [Problema GitHub](https://github.com/magento/magento2/issues/38758) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38759)_

#### [Problema] aggiungere la proprietà isMultipleFiles al modello di elemento del modulo dell&#39;immagine

Questa correzione evita che il pulsante &quot;Sfoglia per trovare o trascinare l’immagine qui&quot; scompaia quando un’immagine viene aggiunta in un elemento modulo immagine con più file.

_AC-13149 - [Problema GitHub](https://github.com/magento/magento2/issues/39219) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36325)_

#### setup:upgrade non riesce con la versione MariaDB 11.4 a causa di modifiche a charset e regole di confronto

_AC-13247_

#### [Problema] Rimuovi tutti i parametri di marketing get per ridurre la cache

Il sistema ora rimuove tutti i parametri di marketing get per ottimizzare l’utilizzo della cache, rispecchiando la logica utilizzata quando è in uso vernice. In precedenza, questi parametri potevano causare il gonfiore della cache e ridurre le prestazioni.

_AC-13279 - [Problema GitHub](https://github.com/magento/magento2/issues/39266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39099)_

#### [Problema] [PHPDOC] Correzione phpdoc non valido Magento\Directory\Model\AllowedCountries::getAllowedCountries()

Il metodo PHPDoc per AllowedCountries::getAllowedCountries() è stato corretto per fornire informazioni accurate, migliorando la chiarezza e l’utilità della documentazione. Precedentemente, il PHPDoc per questo metodo conteneva informazioni errate, che potevano portare a confusione o uso improprio del metodo.

_AC-13345 - [Problema GitHub](https://github.com/magento/magento2/issues/39246) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39241)_

#### [Problema] Rimuove parte del codice per le versioni PHP non più supportate.

Rimozione del codice per le versioni PHP non più supportate in Magento

_AC-13348 - [Problema GitHub](https://github.com/magento/magento2/issues/39361) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39202)_

#### [Problema] Rendere l&#39;adattatore ImageMagick compatibile con php8 (conversione implicita da float a int)

Il sistema ora garantisce la compatibilità con PHP8 gestendo correttamente i numeri in virgola mobile durante il calcolo delle dimensioni dell&#39;immagine, evitando errori dovuti alla conversione implicita da virgola mobile a int. In precedenza, il calcolo delle dimensioni dell’immagine poteva causare numeri in virgola mobile che, se arrotondati in modo implicito, generavano un errore.

_AC-13417 - [Problema GitHub](https://github.com/magento/magento2/issues/39402) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37362)_

#### [Problema] [PHPDOC] Correzione di phpdoc non valido Magento\Framework\App\Config\ScopeConfigInterface

Questo aggiornamento corregge le annotazioni PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface per riflettere con precisione il tipo di argomento $scopeCode per i metodi getValue e isSetFlag.

_AC-13537 - [Problema GitHub](https://github.com/magento/magento2/issues/39492) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http dipende dalla frase del motivo OK

È stato rimosso il controllo della frase &quot;OK&quot; da Magento\Framework\Filesystem\Driver\Http::isExists

_AC-13725 - [Problema GitHub](https://github.com/magento/magento2/issues/39546) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39558)_

#### L&#39;indicizzatore Griglia cliente non funziona correttamente in modalità Aggiornamento per pianificazione

La griglia del cliente precedente è stata aggiornata istantaneamente ma dopo la correzione la griglia del cliente viene aggiornata dopo l’esecuzione della cron ma non viene visualizzata immediatamente.

_AC-13810 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### errore di battitura in un file js.

Il sistema ora utilizza correttamente il termine &quot;abbonati&quot; nel file JavaScript, garantendo la corretta funzionalità delle relative funzioni. In precedenza, un errore tipografico nel file JavaScript causava l’uso errato del termine &quot;abbonati&quot;.

_AC-6754 - [Problema GitHub](https://github.com/magento/magento2/issues/36163) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36171)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.

_AC-8353 - [Problema GitHub](https://github.com/magento/magento2/issues/37253) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37003)_

#### [Problema] Rimuovi il tag `@author` non consentito da `Magento_Customer` (parte 2)

Il sistema ora rispetta lo standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.

_AC-8356 - [Problema GitHub](https://github.com/magento/magento2/issues/37250) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37000)_

#### Lo spazio nella sintassi editorconfig interrompe la regola per `[&lbrace;composer,auth&rbrace;.json]`

Il sistema ora applica correttamente un rientro a 4 spazi ai file compositore e auth.json, in seguito a una correzione di un errore di sintassi nell&#39;editor config. In precedenza, a causa di uno spazio nella sintassi editorconfig, questi file non venivano formattati correttamente con un rientro a 2 spazi.

_AC-8659 - [Problema GitHub](https://github.com/magento/magento2/issues/37394) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37395)_

#### [Problema] Migliorare la registrazione degli errori cron

Il sistema ora acquisisce e registra sia STDERR che STDOUT per i processi cron, fornendo informazioni diagnostiche preziose in scenari in cui i processi cron falliscono. In precedenza, eventuali messaggi di errore all’interno dei processi cron non venivano registrati e STDERR e STDOUT per i gruppi cron in esecuzione in processi separati andavano persi.

_AC-8662 - [Problema GitHub](https://github.com/magento/magento2/issues/37453) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32690)_

#### [Problema] Aggiunge altri colori all&#39;output di alcuni comandi cli di installazione

Il sistema ora aggiunge più colori all&#39;output di alcuni comandi CLI (Command Line Interface) di installazione, migliorando la leggibilità e l&#39;esperienza utente. In precedenza, l&#39;output di questi comandi era più difficile da leggere a causa della mancanza di differenziazione dei colori.

_AC-8984 - [Problema GitHub](https://github.com/magento/magento2/issues/29335) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29298)_

#### L&#39;aggiornamento di Magento reimposta General/region/state_required quando viene aggiunto un nuovo paese con lo stato o l&#39;area geografica richiesti.

Il sistema ora aggiunge il paese modificato alla configurazione &quot;general/region/state_required&quot; solo quando viene aggiunto un nuovo paese con stati required, evitando interruzioni del codice personalizzato che presuppongono la disabilitazione della regione. In precedenza, l’aggiunta di un nuovo paese con stati obbligatori reimpostava la configurazione &quot;general/region/state_required&quot; sui paesi predefiniti con uno stato obbligatorio, potenzialmente interrompendo il negozio.

_AC-9630 - [Problema GitHub](https://github.com/magento/magento2/issues/37796) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38076)_

#### Differenza nella compilazione minore tra la libreria php e nodejs (grunt) con espressioni `calc` complicate

Correggi la differenza in meno compilazione tra libreria php e nodejs (grunt) dopo aggiornamento wikimedia/less.php:^5.x

_AC-9712 - [Problema GitHub](https://github.com/magento/magento2/issues/37841) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### Si verifica un errore di tipo &quot;Impossibile trovare la tabella o la vista di base&quot; quando viene eseguita un’indicizzazione parziale

La reindicizzazione parziale ora funziona correttamente con il changelog grande in caso di connessione db secondaria

_ACP2E-2692 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Problemi dopo l’aggiornamento di MariaDB a 10.5.1 o versione successiva

È stato risolto il problema che si verificava quando i valori datetime in un database venivano convertiti in 0000-00-00 00:00:00 dopo l&#39;aggiornamento di Mysql.

_ACP2E-2844 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Mancata corrispondenza nel confronto dei dati durante la verifica della presenza di modifiche nei dati

In precedenza, l’oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica di dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa.

_ACP2E-2855 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### Impossibile utilizzare l&#39;importazione [Cloud] con il var di directory

Il prodotto può essere importato correttamente indipendentemente dal nome file.

_ACP2E-2959 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### In ipad mini il menu e l’intestazione vengono caricati come dispositivi mobili, ma come desktop.

Il sistema ora tratta i dispositivi con una larghezza di 768 px come desktop, garantendo che il menu e l&#39;intestazione vengano caricati correttamente. In precedenza, i dispositivi con una larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile.

_ACP2E-2966 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### Errore di tabella o visualizzazione di base non trovata durante l&#39;esecuzione di mview cron durante un&#39;operazione DDL

Il sistema ora gestisce correttamente le operazioni di aggiornamento del database mentre mview update è in esecuzione in background, evitando il verificarsi di errori di tipo &quot;Tabella di base o vista non trovata&quot;. In precedenza, alcune operazioni di aggiornamento del database potevano causare un errore di tipo &quot;Tabella di base o vista non trovata&quot;, se l’aggiornamento di mview era in esecuzione contemporaneamente.

_ACP2E-3046_

#### La modifica della lunghezza della colonna tramite db_schema.xml non funziona in caso di chiavi esterne

La modifica della colonna con chiave esterna tramite lo schema dichiarativo ora non genera errori con MariaDB

_ACP2E-3230 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Alcuni dei record delle relazioni vengono salvati nel database quando il record dell&#39;ordine viene salvato

Prima della correzione venivano attivate query UPDATE non necessarie che potevano avere un impatto sulle prestazioni. Dopo la correzione, le query UPDATE non necessarie sono state eliminate.

_ACP2E-3361 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] In admin sono presenti molti errori JavaScript nella console

In precedenza, nel pannello di amministrazione erano presenti molti errori JavaScript nella console. Ora, nel pannello di amministrazione, non ci saranno errori JavaScript nella console e tutte le funzioni predefinite di JavaScript verranno eseguite correttamente senza alcun problema.

_ACP2E-3375 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento: il messaggio della coda è stato eliminato

I messaggi della coda ora vengono cancellati correttamente. Prima della correzione, dato che il sistema della coda SQL era in uso, i nuovi messaggi potevano essere eliminati se il messaggio della coda di pulizia era in esecuzione allo stesso tempo.

_ACP2E-3387 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Le voci corrispondenti della chiave della cache non sono disponibili nei tag della cache, pertanto la pulizia della cache non funziona correttamente

La modalità LUA è ora abilitata per impostazione predefinita per il Garbage Collector della cache Redis per evitare race condition

_ACP2E-3537 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### Valore Magento_DC_INDEXER__USE_APPLICATION_LOCK ignorato

Dopo la correzione, una variabile ENV impostata su &quot;false&quot; verrà trattata come bool false, non come stringa &#39;false&#39;.

_ACP2E-3681 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

#### [Problema] È stato introdotto il supporto di tipi scalari personalizzati per lo schema GraphQL

Il sistema ora supporta i tipi scalari personalizzati per lo schema di GraphQL, consentendo agli sviluppatori di definire tipi e implementazioni scalari personalizzati. Questa funzione può essere particolarmente utile per esprimere valori che possono richiedere la convalida, come HTML, e-mail, URL, date e così via, e per casi più avanzati come gli attributi EAV. In precedenza, il sistema non supportava l’elaborazione di tipi scalari personalizzati in GraphQL.

_AC-7976 - [Problema GitHub](https://github.com/magento/magento2/issues/36877) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/34651) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, prodotto

#### I rapporti EE 2.4.8-beta1 non vengono generati a causa dell’eccezione Magento

_AC-13011_

### Framework, Framework interfaccia utente

#### Possibilità di sovrascrivere il valore di configurazione anche se è bloccato

In precedenza a questa correzione, non era possibile impostare la configurazione di progettazione tramite il comando bin/magento config:set e i valori bloccati potevano essere modificati modificando il modulo che li visualizzava. Dopo la correzione i valori bloccati impostati da cli con —lock-env o —lock-conf non possono più essere aggiornati.

_ACP2E-3324 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl esegue l’elaborazione delle intestazioni anche se il valore dell’intestazione non supera la convalida

Il sistema ora garantisce che l’elaborazione dell’intestazione venga eseguita una sola volta e solo se il valore dell’intestazione supera la convalida, migliorando la sicurezza e impedendo potenziali vulnerabilità. In precedenza, l’elaborazione dell’intestazione veniva eseguita anche se il valore dell’intestazione non superava la convalida, generando potenziali vulnerabilità e comportamenti imprevisti dovuti alla doppia elaborazione dei valori dell’intestazione.

_AC-11729 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Le opzioni Giftcard fisiche non hanno l&#39;ordinamento corretto

Il sistema ora ordina correttamente le opzioni dei prodotti gift card fisici quando viene richiesto tramite GraphQL, garantendo un rendering coerente con il tema Luma. In precedenza, l’ordinamento era errato in base al tema luma, causando una visualizzazione e un ordinamento errati delle opzioni, ad esempio nome del mittente, nome del destinatario e importo.

_AC-8951 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La cache del resolver [GraphQL] è invalidata durante la creazione, la modifica, lo spostamento o l&#39;eliminazione di un aggiornamento di gestione temporanea

Il sistema ora assicura che la cache del risolutore non venga invalidata durante la creazione, la modifica, lo spostamento o l’eliminazione di un aggiornamento di staging, ma solo quando l’aggiornamento di staging viene applicato all’entità. In precedenza, la cache del risolutore veniva invalidata prematuramente, anche prima dell’applicazione dell’aggiornamento di staging, il che portava a inutili invalidamenti della cache.

_AC-9157 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Cache veloce non cancellata per l’aggiornamento della gestione temporanea del contenuto

Ora GraphQL con cache di risposta dei contenuti di PageBuilder viene invalidato quando le entità correlate al contenuto di PageBuilder vengono aggiornate.

_ACP2E-2642 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Disabilitazione della navigazione a livelli: non rimuove l’aggregazione da Graphql

Il problema è stato risolto dopo l’applicazione del controllo durante la richiesta di una ricerca di prodotto con aggregazioni di categorie tramite una query GraphQL quando l’impostazione di configurazione dell’amministratore è &quot;Catalogo > Navigazione a livelli > Visualizza filtro categorie&quot;.

_ACP2E-2653 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### La chiamata dei prodotti GraphQL contenente il filtro prezzi `&lbrace;from:&quot;0&quot;&rbrace;` non restituisce alcun risultato

In precedenza, la ricerca di prodotti graphql con filtro per prezzi zero non restituiva alcun risultato a causa di un’eccezione generata. Ora la ricerca restituisce i risultati come previsto.

_ACP2E-2928 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Le traduzioni per gli attributi di restituzione del cliente non si riflettono nell’API di GraphQL per il rispettivo StoreView

Le traduzioni per gli attributi di restituzione del cliente si riflettono nell&#39;API di GraphQL per il rispettivo StoreView.
In precedenza, gli attributi di restituzione dei clienti per i rispettivi StoreView non venivano riportati nell’API di GraphQL.

_ACP2E-2974 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] chiamata GraphQL interrotta per getPurchaseOrder con preventivo del nodo

La chiamata GraphQL dell’ordine di acquisto sarà in grado di eseguire l’attività senza incontrare errori interni al server.

_ACP2E-3128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### [Cloud] prodotti configurabili non visualizzati nel sito di produzione se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;

Il sistema ora visualizza correttamente i prodotti configurabili nel sito anche se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;, ma è abilitato in ambiti specifici di visualizzazione dello store.
In precedenza, se un prodotto veniva disabilitato in &quot;Tutte le visualizzazioni store&quot; e abilitato solo in ambiti di visualizzazione specifici, gli attributi del prodotto non venivano visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.

_ACP2E-3184 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/3f300077)_

#### [Grafql prodotti cloud] con errore quando lo stesso prodotto semplice è stato assegnato a più prodotti configurabili

In precedenza, con prodotti configurabili separati con lo stesso prodotto semplice, grapQL restituiva un errore. Dopo l’applicazione di questa correzione, diversi prodotti configurabili con lo stesso prodotto semplice, grapQL restituisce il risultato senza errori.

_ACP2E-3190 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Problema cloud] con l&#39;autenticazione utente e l&#39;accesso ai token intersito nella configurazione multisito

Le query relative a informazioni sul cliente e sul carrello GraphQl in Configurazione multisito controllano se il cliente è presente sul sito web non predefinito.
La query precedente funzionava senza assicurarsi che il cliente esistesse su un sito Web non predefinito in Configurazione multisito.

_ACP2E-3215 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### La paginazione di GraphQL cart itemsV2 non funziona correttamente

Il problema è stato risolto passando il valore corretto per l&#39;argomento pagina corrente nella query di raccolta. In precedenza, veniva trasmesso un valore errato per impostare la pagina corrente, causando il problema.

_ACP2E-3253 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### È necessario specificare il valore del modello [GRAPHQL] per ottenere customerCart

La query &quot;customerCart&quot; di GraphQL ora può creare un carrello vuoto anche quando il preventivo non è disponibile nel database. In precedenza, questa operazione non riusciva a causa di problemi di convalida del paese durante la creazione del carrello vuoto.

_ACP2E-3255 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Gli elementi della lista dei desideri GraphQl] sono visibili tramite GraphQl ma non in vetrina

Prodotti della lista dei desideri che non sono stati correttamente elencati quando richiesto tramite GraphQL. Adesso, i prodotti della lista dei desideri vengono filtrati in base al contesto del negozio fornito.

_ACP2E-3380 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL] Incoerenza e-mail reimpostazione password tra contenuto e oggetto/collegamento

Il problema è stato risolto simulando il negozio corretto in cui è registrato l’account del cliente al momento dell’invio della richiesta di reimpostazione della password, indipendentemente dallo store del sito web.

_ACP2E-3404 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### [Prodotti cloud] La query GraphQL restituisce prodotti correlati non assegnati al sito Web corrente

In precedenza, per la query graphQL, i prodotti correlati a più store non venivano visualizzati correttamente per la query del prodotto. Dopo l’applicazione di questa correzione, per i prodotti, graphQL esegue una query sui prodotti correlati a più store visualizzati di conseguenza.

_ACP2E-3419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### L’utilizzo di un ID archivio errato nell’intestazione di GraphQL causa un errore irreversibile di memoria

L’invio di codice archivio errato nella richiesta GraphQL non comporta più un consumo eccessivo di memoria.

_ACP2E-3447 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Risposta cloud] 500 a una risposta Graphql vuota nella versione 2.4.7

Dopo la correzione, le richieste graphql non valide non verranno registrate nel file exception.log.

_ACP2E-3467 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Problemi con l&#39;API Graphql]

Prima della correzione tramite il server applicazioni Graphql, la richiesta dell&#39;indirizzo del cliente non restituiva i dati più recenti.

_ACP2E-3492 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Il prodotto disabilitato viene ancora visualizzato negli articoli correlati, di upselling e di cross-selling nella query GraphQL

Graphql fornisce ora una risposta corretta per i prodotti relared, upselling e cross-selling disabilitati

_ACP2E-3505 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD]: errore GraphQl Errore interno del server. Mutazione placeOrder

La mutazione &quot;placeOrder&quot; con le informazioni sul codice coupon nella richiesta non genera più un’eccezione di errore interna, l’ordine è stato effettuato correttamente. In precedenza, non riusciva con &quot;Errore interno del server&quot;.

_ACP2E-3647 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

#### La percentuale di sconto non viene calcolata per i prodotti bundle con prezzo dinamico

Correzione aggiunta per sconto_percentuale di product.price_details che non mostra il valore corretto per i prodotti bundle con prezzo dinamico abilitato e coupon di sconto applicato.

_LYNX-426_

#### I prodotti del bundle mostrano ancora &quot;IN_STOCK&quot; quando uno dei loro prodotti in bundle è esaurito

Risoluzione del problema per cui i prodotti bundle mostravano ancora &quot;IN_STOCK&quot; anche quando uno dei loro prodotti bundle era esaurito.

_LYNX-485_

#### not_available_message e only_x_left_in_stock non mostra lo stesso materiale disponibile

È stato risolto il problema che causava la visualizzazione incoerente della disponibilità delle scorte in not_available_message e only_x_left_in_stock

_LYNX-486_

#### il campo original_row_total restituisce un valore errato

È stato risolto il problema relativo al campo original_row_total, che restituiva valori errati quando venivano selezionate opzioni personalizzate.

_LYNX-488_

#### La miniatura del prodotto raggruppato deve essere visualizzata in base alla configurazione     .

È stato risolto il problema per garantire che la miniatura del prodotto raggruppato venga visualizzata in base alle impostazioni di configurazione

_LYNX-503_

#### Errore durante la query di selected_options in OrderAddress

AttributeSelectedOptions è stato aggiornato a custom_attributesV2 nella risposta GraphQL dell&#39;indirizzo dell&#39;ordine.

_LYNX-510_

#### original_item_price non include gli sconti

Original_item_price è stato aggiornato per includere gli sconti.

_LYNX-512_

#### Il messaggio Non disponibile non mostra la quantità di magazzino disponibile

È stato risolto il messaggio di errore e il codice di errore per la mutazione AddProductsToCart in modo da allinearlo alla configurazione del messaggio &quot;not available&quot; (non disponibile)

_LYNX-530_

#### Lo stato &quot;OUT_OF_STOCK&quot; viene restituito su Semplice con opzioni personalizzate e prodotti con opzioni a selezione multipla

È stato aggiornato il risolutore StockStatusProvider nel pacchetto di inventario per correggere stock_status per i prodotti semplici con opzioni personalizzate.

_LYNX-532_

#### Errore (GQL): cart.itemsV2.items.product.custom_attributesV2 restituisce un errore del server

È stato risolto l’errore del server che si verificava quando una query sul carrello includeva gli attributi personalizzati di un prodotto aggiungendo un prodotto senza attributi personalizzati.

_LYNX-533_

#### orders/date_of_first_order restituisce sempre null

È stato risolto il problema per cui orders > date_of_first_order restituiva sempre null.

_LYNX-536_

#### Il cliente non deve essere in grado di annullare un ordine spedito parzialmente

È stata aggiunta la convalida per impedire ai clienti di annullare un ordine spedito parzialmente.

_LYNX-544_

#### Codici di errore per l’annullamento dell’ordine in base al messaggio di errore

I codici di errore per l’annullamento dell’ordine ora si basano sul messaggio di errore specifico.

_LYNX-548_

#### Torna indietro le proprietà relative ai cookie da private a protected

Ripristina la visibilità delle proprietà del costruttore di classe Magento\Framework\App\PageCache\Version da private a protected

_LYNX-581_

#### Aumenta la complessità massima predefinita delle query GraphQL a 1000

La complessità massima predefinita delle query GraphQL è stata aumentata da 300 a 1000.

_LYNX-600_

#### GQL - itemsV2 > Original row total, i prezzi della fascia di prezzo vengono restituiti come $ 0,00 per il prodotto scaricabile con opzioni di file che ha prezzi separati.

È stato risolto un problema a causa del quale i prodotti scaricabili con opzioni di acquisto di collegamento separate abilitate restituivano $ 0 per gli articoliV2 > Totale riga originale e l’intervallo di prezzo restituiva $ 0,00 per i prodotti con opzioni di file con prezzi separati.

_LYNX-620_

#### Schema di una tabella quando viene creato nuovo di zecca diverso da quando si esegue l’aggiornamento

È stato risolto un problema a causa del quale l’aggiunta di una nuova colonna VARCHAR a una tabella esistente causava errori di test a causa di differenze di schema tra nuove installazioni e aggiornamenti. Il metodo modifyColumn() ora gestisce correttamente le colonne VARCHAR impostando il set di caratteri e le regole di confronto predefiniti.

_LYNX-711_

#### Compatibilità di GraphQl per la versione PHP-8.4

Sono stati risolti i problemi di compatibilità di GraphQL con PHP 8.4 su più resolver, garantendo funzionalità senza problemi. Sono stati aggiornati i file interessati nei moduli CatalogRule, Customer, GiftMessage, GiftCard e GiftWrapping.

_LYNX-772_

### GraphQL, Inventory/MSI

#### La mutazione MergeCart genera un’eccezione quando i carrelli di origine e di destinazione hanno gli stessi elementi bundle

&quot;-

_ACP2E-2607 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, inventario/MSI, prestazioni

#### Sito inattivo dopo l&#39;aggiornamento

Sono state migliorate le prestazioni di recupero dei prodotti bundle tramite GraphQl.

_ACP2E-1716 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Prestazioni

#### [GraphQL Resolver] I dati del resolver del cliente non sono invalidati dall&#39;importazione

La cache del resolver clienti GraphQL ora viene invalidata come previsto quando un cliente viene modificato o eliminato tramite importazioni. In precedenza, la cache non veniva invalidata e i dati dei clienti potevano essere modificati o eliminati durante l’importazione.

_AC-9569 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Cerca

#### L’ordinamento dell’elenco dei prodotti GraphQL in base a più parametri non funziona

L’ordinamento dei prodotti per più campi in GraphQl ora funziona come descritto nella documentazione

_ACP2E-2809 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Query GraphQL dell’elenco prodotti limitata solo a total_count 10.000 prodotti

Dopo la correzione, il risultato della ricerca non è limitato ai prodotti 10000, ma diventa possibile ottenere tutti i prodotti che corrispondono ai criteri di ricerca anche se il conteggio è superiore a 10000.

_ACP2E-948 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, framework di prova

#### Test di integrazione Magento\GraphQl\App\GraphQlCustomerMutationsTest.php non riuscito

&quot;-

_ACP2E-3363 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importa/esporta

#### Problema durante l’importazione del prodotto quando viene fornito con il tipo di opzione personalizzato: file (il prodotto creato non contiene il prezzo per l’opzione personalizzata e mostra solo la prima estensione del tipo di file fornita)

Il sistema ora importa correttamente i dati del prodotto con opzioni personalizzate di tipo &quot;file&quot;, assicurandosi che vengano visualizzate tutte le estensioni di file fornite e che venga incluso il prezzo per l’opzione personalizzata. In precedenza, durante l’importazione del prodotto, se un’opzione personalizzata di tipo &quot;file&quot; veniva fornita con più di un’estensione di file, veniva visualizzata solo la prima estensione e mancava il prezzo per l’opzione personalizzata.

_AC-12172 - [Problema GitHub](https://github.com/magento/magento2/issues/38805) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38926)_

#### Tempo di esecuzione errato per l&#39;operazione di importazione nella griglia Cronologia importazione

Il tempo di esecuzione dell’importazione del rapporto viene visualizzato correttamente, indipendentemente dalle impostazioni locali dell’amministratore.

_ACP2E-2710 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Clienti duplicati creati con lo stesso indirizzo e-mail utilizzando l’importazione

Viene aggiornata l&#39;importazione del cliente mentre Condivisione account è impostato su Globale, cliente importato che esiste nel sistema.
Il cliente importato in precedenza è stato duplicato.

_ACP2E-2737 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Aggiungi/aggiorna importazione su prodotti che duplicano opzioni personalizzabili

Il problema è stato risolto assegnando l’archivio corretto alle opzioni del prodotto durante le importazioni CSV delle opzioni del prodotto.
In precedenza, venivano assegnati all’archivio di amministrazione invece che al rispettivo archivio.

_ACP2E-2902 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Data &quot;created_at&quot; cliente non convertita in fuso orario del negozio al momento dell’esportazione

Un valore di data colonna &quot;created_at&quot; viene convertito nel formato di data corretto in base al fuso orario dell’archivio nella sezione CSV di esportazione del cliente.

_ACP2E-2990 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### [Cloud] Ricezione di un errore durante la verifica dei dati nei dati di importazione tramite CSV

Non viene generato alcun errore durante il controllo dei dati durante l’importazione CSV. In precedenza, il messaggio di errore visualizzato era: &quot;Impossibile trovare un cliente che corrisponda a questo indirizzo e-mail e al codice del sito web nelle righe: 1&quot; quando si controllano i dati nella sezione di importazione utilizzando il file CSV dell’amministratore.

_ACP2E-3165 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Pulsante Importa mancante

Per risolvere il problema di mancanza del pulsante Importa, segui una verifica dei dati con record corretti e non corretti nel file CSV. In precedenza, il pulsante di importazione non veniva visualizzato dopo il controllo dei dati con record corretti e non corretti nel file CSV.

_ACP2E-3172 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1819fe73)_

#### Impossibile importare l&#39;indirizzo del cliente esportato

L’importazione dell’indirizzo del cliente procederà come previsto. In precedenza, un file di importazione dell’indirizzo di un cliente non superava la convalida se Condividi account del cliente = Globale ed esistono due siti web in cui il sito web predefinito ha un elenco di paesi limitato e l’indirizzo che viene importato è per un altro sito web in cui i paesi consentiti sono diversi

_ACP2E-3382 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Cloud] La quantità errata nel file CSV non ha restituito alcun errore

Ora l’importazione delle origini delle scorte genera un errore di convalida per i valori non numerici nella colonna Quantità. In precedenza, l&#39;importazione di origini di scorte con valore non numerico nella colonna Quantità comportava l&#39;impostazione della quantità su 0.

_ACP2E-3448 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

#### Il messaggio di errore relativo alla chiave URL duplicata generato durante l’importazione di un prodotto non è corretto se la chiave URL appartiene già a una categoria

Visualizzazione del messaggio di errore corretto durante il controllo dell’importazione del prodotto, quando il cliente ha tentato di importare un prodotto quando il codice URL del prodotto appartiene già a una categoria.

_ACP2E-3455 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### L&#39;esportazione del prodotto causa OOM anche con il limite di memoria 4G

Prima di questa correzione, l’esportazione del prodotto non riusciva se gli attributi del prodotto avevano migliaia di valori di opzione anche con la memoria disponibile 4G. Dopo questa correzione, l’esportazione del prodotto dovrebbe terminare l’esportazione del file CSV.

_ACP2E-3475 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Processi di importazione cloud] che interferiscono tra loro

I messaggi corretti vengono visualizzati se lo stesso utente amministratore esegue due o più operazioni di importazione utilizzando la stessa sessione utente.

_ACP2E-3527 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Importazione/esportazione, prestazioni

#### [Cloud] Il tempo di importazione del prodotto è aumentato in modo significativo

Prima della correzione, l’importazione di prodotti catalogo con più di 10.000 voci presentava una notevole riduzione del tempo. Dopo la correzione, l’importazione del prodotto catalogo viene eseguita in modo tempestivo.

_ACP2E-3476 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/87d012e5)_

### Installazione e amministrazione

#### L&#39;aggiornamento di Magento non riesce con MariaDB 11.4 + 2.4.8-beta1

L’aggiornamento dovrebbe avvenire senza alcun errore.

_AC-13242 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7b336d0a)_

#### Nessun pulsante Esporta VCL per vernice 7 nel pannello di amministrazione

Il pulsante &quot;Esporta VCL per vernice 7&quot; è stato aggiunto al pannello di amministrazione.

_ACP2E-2102 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventario/MSI

#### L&#39;aggiornamento dell&#39;inventario del prodotto configurabile non riesce quando il database utilizza prefissi

Il sistema ora aggiorna correttamente l&#39;inventario dei prodotti configurabili quando il database utilizza prefissi, evitando messaggi di errore e assicurando il salvataggio della quantità corretta. In precedenza, se il database utilizzava i prefissi, si verificava un errore durante il tentativo di salvare la quantità di magazzino per i prodotti semplici all’interno di un prodotto configurabile.

_AC-10750 - [Problema GitHub](https://github.com/magento/magento2/issues/38045)_

#### La chiave API google di Google non funziona durante l’aggiunta della mappa con attributi

Il sistema ora supporta la versione più recente dell’API di Google Maps 3.56, che consente agli utenti di aggiungere allo stage un blocco di contenuto Mappa dal menu PageBuilder senza riscontrare errori. In precedenza, gli utenti non potevano aggiungere un blocco di contenuto Mappa a causa di problemi di compatibilità con la versione dell’API Google Maps, causando un messaggio di errore &quot;si è verificato un errore&quot;.

_AC-11593 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Impossibile creare la spedizione per l&#39;articolo dell&#39;ordine con più origini e SKU danneggiato

In precedenza, quando gli spazi venivano aggiunti erroneamente nello SKU tramite database, si verificava un errore nella pagina di spedizione, che ora è fissa, e il ritaglio automatico viene considerato un errore di facile utilizzo e non è stato trovato alcun impatto. La spedizione è stata quindi creata correttamente.

_AC-13922 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [Test] prodotti del bundle con 0 inventario visualizzati sul lato negozio

Il prodotto del bundle non viene visualizzato sui siti web aggiuntivi utilizzando scorte aggiuntive.

_ACP2E-1411_

#### [Cloud] problema critico con l&#39;elenco prodotti con spazi vuoti

Ora il sistema visualizza correttamente gli elenchi dei prodotti senza spazi vuoti quando i prodotti sono impostati su &quot;esaurito&quot;, garantendo una visualizzazione coerente e accurata dei prodotti disponibili. In precedenza, se si impostava un prodotto su &quot;Esaurito&quot;, nell’elenco dei prodotti veniva visualizzato uno spazio vuoto, che causava interruzioni del layout e poteva confondere i clienti.

_ACP2E-2794 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/b59e48ca)_

#### Impossibile spedire l&#39;ordine quando l&#39;archivio di ritiro MSI è abilitato

Miglioramento delle prestazioni di inventario per creare la spedizione in caso di molte origini con prelievo in-store

_ACP2E-3335 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### La reindicizzazione della corona non riesce ad aggiornare la disponibilità del prodotto sul front-end

In precedenza, i prodotti rimanevano esauriti sul front-end dopo l’aggiornamento dello stato dell’ordine arretrato tramite l’API REST. Ora, dopo aver aggiornato lo stato dell’ordine inevaso tramite l’API REST, i prodotti vengono visualizzati come in stock.

_ACP2E-3355 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### L’aggiunta di immagini a configurabile non funziona quando MSI è abilitato.

Il caricamento dell’immagine per il prodotto configurabile ora funziona come previsto quando si utilizza il modulo inventario. In precedenza, il caricamento dell’immagine non funzionava

_ACP2E-3357 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/fdf409aa)_

#### Problema con il prodotto in bundle + MSI in Clean M2.4.7-p3

In precedenza, per i prodotti bundle di inventario dopo la duplicazione con lo stesso prodotto semplice, il prodotto semplice non poteva essere salvato. Dopo l’applicazione di questa correzione, il prodotto semplice può essere salvato correttamente senza eccezioni.

_ACP2E-3470 - [Problema GitHub](https://github.com/magento/magento2/issues/39358) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/0208e433)_

### Magazzino/MSI, Ricerca

#### Tutti i prodotti sono indicizzati con [is_out_of_stock] = 1 quando lo SKU non è impostato come attributo ricercabile

Dopo la correzione, &quot;is_out_of_stock&quot; nell’indice di ricerca del catalogo è corretto, anche quando lo SKU non è ricercabile.

_ACP2E-3413 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

### Ordine

#### Schermata di panoramica ordine back-end: quantità in inevaso non visibile a livello di articolo ordine

Il sistema visualizza ora il numero di articoli in inevaso nella colonna quantità della schermata di panoramica dell’ordine backend. In questo modo gli utenti possono tenere traccia con precisione dello stato di tutti gli elementi di un ordine. In precedenza, la colonna Quantità mostrava solo il numero di articoli ordinati, fatturati e spediti, ma non il numero di articoli in inevaso.

_AC-10828 - [Problema GitHub](https://github.com/magento/magento2/issues/38252) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38320)_

#### [Problema] ID archivio errato utilizzato nel modulo di rendering degli indirizzi dell&#39;ordine

Il sistema ora utilizza correttamente l’ID store associato a un ordine durante il rendering dell’indirizzo dell’ordine, assicurandosi che gli indirizzi siano formattati correttamente in base al rispettivo ID store. In precedenza, il sistema utilizzava erroneamente l’ID store corrente, il che poteva causare una formattazione degli indirizzi errata nei casi in cui occorreva inviare più e-mail di ordine da diversi store.

_AC-10994 - [Problema GitHub](https://github.com/magento/magento2/issues/38412) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37932)_

#### Problema di caching JoinProcessor

Il sistema ora applica correttamente il JoinProcessor per ogni iterazione, anche con chiamate consecutive, garantendo un recupero accurato dei dati. In precedenza, JoinProcessor veniva erroneamente contrassegnato come già applicato in iterazioni consecutive, causando errori nel recupero dei dati.

_AC-11690 - [Problema GitHub](https://github.com/magento/magento2/issues/27504) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37550)_

#### [Problema] Prezzo di spedizione diverso nel PDF stampato

Il sistema visualizza correttamente i prezzi di spedizione nei PDF stampati in base alle impostazioni di configurazione delle imposte, garantendo la coerenza tra la pagina di visualizzazione della fattura dell&#39;ordine di vendita e la fattura stampata. In precedenza, il prezzo di spedizione visualizzato nel PDF stampato escludeva le imposte, indipendentemente dalle impostazioni di configurazione delle imposte.

_AC-11798 - [Problema GitHub](https://github.com/magento/magento2/issues/38608) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38595) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Riordina con un prodotto configurabile principale eliminato

Ora durante il riordino con il prodotto eliminato il sistema non mostra il pulsante di riordino da riordinare

_AC-13839 - [Problema GitHub](https://github.com/magento/magento2/issues/39568) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39601)_

#### [Problema] Correzione non valida \Magento\Sales\Model\Order\Email\Container\Template::$id property

Questo risolve il problema phpdoc per \Magento\Sales\Model\Order\Email\Container\Template::$id, in realtà $id è type int ma in realtà è string.

_AC-13924 - [Problema GitHub](https://github.com/magento/magento2/issues/39151) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39150)_

#### Impossibile salvare le modifiche al numero di telefono nei dettagli dell&#39;ordine esistente

Ora l&#39;utente può aggiungere il prefisso internazionale 00 nel campo telefono dell&#39;indirizzo ordine

_ACP2E-2622 - [Problema GitHub](https://github.com/magento/magento2/issues/38201) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### Invio delle e-mail non riuscito

Il sistema ora include un’opzione di configurazione async_sending_attempted per specificare il numero di tentativi di invio di un’e-mail prima dell’arresto, migliorando la gestione degli invii di e-mail non riusciti quando &quot;Invio asincrono&quot; è abilitato. In precedenza, se l’invio di un’e-mail non riusciva, il sistema tentava continuamente di inviarla nuovamente, generando un ciclo infinito di messaggi di errore nel registro del sistema.

_ACP2E-2734 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [Cloud] Lo stato dell&#39;ordine è stato modificato in completo quando si effettua il rimborso parziale di un ordine spedito parzialmente

Quando si emette una nota di accredito, lo stato dell&#39;ordine non viene più modificato in &quot;completato&quot; se sono presenti articoli non ancora spediti.

_ACP2E-2756 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD] Non è in grado di disabilitare l&#39;invio di e-mail dall&#39;interfaccia utente di amministrazione come mostrato nella documentazione per sviluppatori

Il sistema ora impedisce correttamente l’invio delle e-mail di vendita quando la comunicazione e-mail è disabilitata. Queste e-mail non verranno più inviate quando la comunicazione e-mail verrà riattivata. In precedenza, le e-mail di vendita avviate mentre la comunicazione e-mail era disabilitata venivano comunque inviate una volta riabilitata la comunicazione e-mail.

_ACP2E-3002 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Ordine chiuso senza rimborso completo

Il sistema ora gestisce correttamente lo stato dell&#39;ordine come &quot;Elaborazione&quot; e lo stato della fattura come &quot;In sospeso&quot; quando un ordine con un pagamento non acquisito presenta una spedizione creata. In questo modo gli ordini vengono contrassegnati come &#39;Chiusi&#39; solo dopo essere stati completamente rimborsati. In precedenza, la creazione di una spedizione per un ordine con una fattura in sospeso avrebbe erroneamente modificato lo stato dell’ordine in &quot;Chiuso&quot;.

_ACP2E-3045 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud] Non è possibile creare l&#39;ordine in Admin su un archivio se non è stato impostato solo l&#39;indirizzo di fatturazione predefinito

Ora il messaggio di errore rilevante &quot;Un cliente con lo stesso indirizzo e-mail esiste già in un sito web associato&quot;. viene visualizzato se un cliente non ha un indirizzo di fatturazione predefinito e tenta di creare un ordine in un altro negozio.

_ACP2E-3311 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Richieste di ordini di luoghi duplicati inviate dall&#39;amministratore

In precedenza, il pulsante &quot;Invia ordine&quot; nel pannello di amministrazione poteva essere fatto clic più volte o attivato premendo ripetutamente il tasto &quot;Invio&quot;, causando invii duplicati o ordini con errore. Ora, impedendo ulteriori azioni fino a quando l’ordine non è completamente elaborato, garantendo che venga inviato un solo ordine.

_ACP2E-3416 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### L’amministratore può comunque effettuare l’ordine anche senza il metodo di pagamento

Il metodo di pagamento selezionato in precedenza viene ora mantenuto quando il metodo di pagamento viene nuovamente visualizzato nell&#39;elenco dei pagamenti disponibili.

_ACP2E-3425 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Gli elementi vengono duplicati dopo aver creato un ordine da Admin on - Mozilla Firefox browser

I prodotti aggiunti utilizzando &quot;Aggiungi prodotti per SKU&quot; non vengono più duplicati in Firefox quando si crea un ordine in admin.

_ACP2E-3518_

### Ordine, Pagamenti

#### L’amministratore può comunque effettuare l’ordine anche senza il metodo di pagamento

In precedenza, il commerciante poteva effettuare ordini dal pannello di amministrazione senza selezionare un metodo di pagamento. Ora, il commerciante è richiesto un metodo di pagamento per procedere con l&#39;effettuazione di un ordine.

_ACP2E-3233 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

### Ordine, restituzioni

#### Il rimborso dell&#39;ordine risulta in una nota di accredito duplicata

L’emissione del rimborso tramite API REST quando due richieste identiche sono state eseguite contemporaneamente non creerà più note di credito duplicate.

_ACP2E-2982 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Ordine, imposta

#### [CLOUD] Base_row_total non corretta nell&#39;API dell&#39;ordine RESTFUL quando si abilitano transazioni transfrontaliere e si applicano sconti coupon

Ora base_row_total corretta viene restituita dall’API dell’ordine RESTFUL quando è abilitata la transazione transfrontaliera e viene applicato lo sconto coupon.

_ACP2E-3003 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

### Altro

#### [Braintree] rimborsa la transazione di archiviazione online come transazione id-rimborso

_BUNDLE-3394_

#### [Braintree] + [CLOUD] ordini Braintree (carta di credito) non in grado di dividere le spese

_BUNDLE-3421_

#### [Braintree] [Cloud]Il certificato SSL di Braintree scade il 30 giugno

_BUNDLE-3422_

#### cookie private_content_version restituito nelle query GQL

È stato risolto un problema a causa del quale il cookie private_content_version veniva restituito nelle query GraphQL, anche quando il cookie di sessione era disabilitato. Il cookie non viene più incluso nelle risposte di GraphQL quando la sessione è disabilitata, come previsto.

_LYNX-339_

#### Errore del server nelle proprietà e-mail nelle query fisiche sulle gift card

È stato risolto un problema che causava un errore del server nelle query per sender_email e recipient_email su gift card fisiche. Queste proprietà ora vengono restituite correttamente per le carte regalo virtuali e il comportamento di query è coerente.

_LYNX-366_

#### L’attributo is_available in CartItemInterface restituisce sempre false per i prodotti configurabili

È stato risolto un problema a causa del quale l’attributo is_available in CartItemInterface restituiva sempre false per i prodotti configurabili in magazzino. Ora riflette correttamente la disponibilità come true quando applicabile.

_LYNX-380_

#### L&#39;attributo is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto

È stato risolto il problema a causa del quale l’attributo is_available in CartItemInterface restituiva erroneamente true anche quando la quantità dell’articolo del carrello superava le scorte vendibili.

_LYNX-382_

#### L’attributo only_x_left_in_stock in ProductInterface non è accurato nei prodotti configurabili

È stato risolto un problema a causa del quale l’attributo only_x_left_in_stock in ProductInterface non rifletteva con precisione il materiale disponibile per le varianti di prodotto configurabili nel carrello. Ora, il valore only_x_left_in_stock corrisponde correttamente ai livelli di scorte varianti effettivi, garantendo che vengano restituiti dati di inventario accurati nella query GQL del carrello.

_LYNX-395_

#### La miniatura segnaposto viene restituita quando un prodotto semplice viene aggiunto al carrello all’interno di un prodotto raggruppato

È stato risolto un problema a causa del quale l’aggiunta di un prodotto semplice (parte di un prodotto raggruppato) al carrello restituiva un’immagine miniatura segnaposto, anche quando al prodotto era assegnata un’immagine.
Dettagli correzione:
- Ora la miniatura del prodotto mostra correttamente l’immagine assegnata, se disponibile.
- La selezione delle miniature rispetta la configurazione di amministrazione in:
Negozi > Configurazione > Vendite > Pagamento > Carrello acquisti > Immagine prodotto raggruppato.
In questo modo si garantisce un comportamento coerente delle miniature per i prodotti raggruppati in base alle impostazioni dello store.

_LYNX-399_

#### Gli attributi di opzione personalizzati del cliente non funzionano con valori interi

È stato risolto un problema che impediva il funzionamento degli attributi di opzione personalizzati del cliente quando il valore restituito era un numero intero. Le opzioni personalizzate ora gestiscono e restituiscono correttamente i valori interi come previsto.

_LYNX-400_

#### Errore interno del server durante il tentativo di ottenere il prezzoDettagli per i prodotti Bundle con prezzo dinamico

È stato risolto un problema che causava un errore interno del server a causa della query di price_details per i prodotti bundle con prezzo dinamico tramite GraphQL. Questo miglioramento garantisce la stabilità delle query sul carrello quando si lavora con prodotti bundle configurati con prezzi dinamici.

_LYNX-402_

#### only_x_left_in_stock restituisce sempre 0 per i prodotti configurabili

È stato risolto un problema a causa del quale l’attributo only_x_left_in_stock restituiva sempre 0 per i prodotti configurabili quando aggiunti utilizzando lo SKU padre con le opzioni.
Dettagli correzione:
- Il valore only_x_left_in_stock ora riflette con precisione il materiale grezzo della variante figlio selezionata invece dello SKU padre.
- In questo modo i livelli delle scorte vengono visualizzati correttamente per le varianti di prodotto configurabili nel carrello e nelle pagine dei prodotti.

_LYNX-403_

#### Errore GraphQL: tipo di file non supportato nella query delle opzioni personalizzabili

È stato risolto un problema a causa del quale GraphQL restituiva un errore per le opzioni personalizzabili di tipo &quot;file&quot; negli elementi del carrello. La query ora restituisce correttamente i dettagli per tutti i tipi di opzioni personalizzabili, comprese le opzioni basate su file, senza causare errori.

_LYNX-405_

#### La query GraphQL non restituisce il prezzo normale calcolato corretto per i prodotti personalizzabili

È stato risolto un problema a causa del quale GraphQL non restituiva il prezzo normale calcolato corretto per i prodotti personalizzabili. La query ora include correttamente il prezzo regolare calcolato con valori personalizzabili applicati (ad esempio, $ 125) nella proprietà price, che riflette sia il prezzo di base che eventuali costi di personalizzazione aggiuntivi.

_LYNX-411_

#### Le imposte applicate tramite Totali stimati persistono con mutazioni aggiornate

È stato risolto un problema relativo alla mutazione EstimatedTotals a causa del quale le imposte applicate persistevano su un carrello anche dopo l’aggiornamento del codice postale o dell’area geografica. La mutazione ora aggiorna correttamente le imposte applicate quando si cambia tra i valori di area e codice postale, garantendo che venga applicata solo la regola fiscale corretta in base ai dati del carrello correnti.

_LYNX-412_

#### L&#39;attributo is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto

È stato risolto un problema a causa del quale l’attributo is_available in CartItemInterface restituiva erroneamente true anche quando le scorte vendibili erano inferiori alla quantità di prodotto richiesta. Il campo is_available ora restituisce correttamente false quando la quantità del prodotto supera le scorte disponibili.

_LYNX-420_

#### Impossibile aggiungere il coupon al carrello per lo sconto solo spedizione

È stato risolto un problema che impediva l&#39;applicazione di un coupon al carrello per sconti solo per la spedizione. Il coupon viene ora applicato correttamente all’importo di spedizione quando si utilizza una regola di vendita senza condizioni di prodotto, garantendo l’applicazione dello sconto previsto alle spese di spedizione.

_LYNX-421_

#### Prezzo regolare del prodotto con 12 decimali e valore errato

È stato risolto un problema a causa del quale il valore regular_price nei percorsi GraphQL product.price_range.maximum_price e minimum_price non corrispondeva al prezzo del catalogo quando venivano applicate più aliquote fiscali. Il prezzo_regolare ora riflette in modo coerente il prezzo di catalogo in tutte le configurazioni di imposta, garantendo prezzi unitari accurati, calcoli del costo totale di riga e assegni di sconto nel Riepilogo carrello.

_LYNX-425_

#### Errore del server GraphQL sul carrello con prodotto incluso esaurito

È stato risolto un problema a causa del quale GraphQL restituiva un errore interno del server durante il recupero di un carrello contenente un prodotto in bundle con un articolo esaurito, in particolare quando la query includeva la proprietà itemsV2. GraphQL ora restituisce correttamente un elenco di elementi con messaggi di errore pertinenti associati alla voce dell’elemento del prodotto nel pacchetto, come previsto.

_LYNX-430_

#### Impossibile creare un indirizzo con attributi personalizzati

È stato risolto un problema relativo alla mutazione createCustomerAddress che impediva la creazione di indirizzi con gli attributi personalizzati richiesti. La mutazione ora gestisce correttamente gli attributi degli indirizzi personalizzati quando viene fornito il payload appropriato.

_LYNX-441_

#### Errore del server GraphQL nel carrello con only_x_left_in_stock nel prodotto in bundle

È stato risolto un problema a causa del quale il recupero di un carrello contenente un prodotto in bundle con il campo only_x_left_in_stock nella query GraphQL generava un errore interno del server. GraphQL ora restituisce correttamente un valore float o null per il campo only_x_left_in_stock senza errori.

_LYNX-447_

#### Errore GraphQL durante la rimozione di altri prodotti con prodotto configurabile insufficiente nel carrello

È stato risolto un problema a causa del quale il tentativo di rimuovere i prodotti di magazzino dal carrello causava un errore GraphQL di tipo &quot;La quantità richiesta non è disponibile&quot; se il carrello conteneva anche prodotti configurabili con scorte insufficienti. La rimozione ora funziona come previsto senza errori di attivazione.

_LYNX-464_

#### Impossibile aggiungere prodotti perché la mutazione SKU fa distinzione tra maiuscole e minuscole

È stato risolto un problema a causa del quale la mutazione addProductsToCart restituiva un errore &quot;PRODUCT_NOT_FOUND&quot; quando si utilizzavano SKU con maiuscole e minuscole diverse. La mutazione ora gestisce gli SKU senza distinzione tra maiuscole e minuscole, garantendo la coerenza con le query di Catalog Service e il comportamento PDP.

_LYNX-469_

#### Attributo prodotto > marchio di fabbrica formato breve &trade; viene restituito come &trade;

È stato risolto un problema di codifica dei caratteri con il nome del prodotto per l’API GraphQL.

_LYNX-603_

#### updateCustomerEmail problema di mutazione

È stato risolto un problema relativo alla mutazione updateCustomerEmail a causa del quale i clienti che non disponevano degli attributi personalizzati richiesti (aggiunti dopo la creazione dell’account) non potevano aggiornare l’e-mail.

_LYNX-619_

#### Il set di mutazioni ShippingAddressesOnCart genera un errore quando si utilizza pickup_location_code

È stato risolto un problema a causa del quale la mutazione setShippingAddressesOnCart restituiva un errore quando si utilizzava pickup_location_code senza specificare customer_address_id o address. La mutazione ora consente correttamente di impostare un indirizzo di spedizione con solo il codice pickup_location_code.

_LYNX-626_

#### L&#39;elenco CustomerOrder.items_idonea_for_return deve essere coerente con gli articoli dell&#39;ordine

Sono state risolte le incoerenze con l’idoneità alla restituzione negli ordini:
1. L&#39;elenco CustomerOrder.items_idonea_for_return è ora coerente con gli articoli dell&#39;ordine effettivi.
2. Il campo OrderItemInterface.idonea_per_return restituisce correttamente false quando è già stata restituita la quantità completa.
3. CustomerOrder.items_idonea_for_return ora include solo gli articoli che non sono già in fase di restituzione.

_LYNX-627_

#### Aggiungi campo quantity_return_requested

È stato aggiunto il campo quantity_return_requested a OrderItemInterface, che consente di identificare la quantità di articoli per i quali è stata sottomessa una restituzione. In questo modo viene migliorata la registrazione dei resi insieme al campo quantity_returned esistente.

_LYNX-628_

#### Le azioni disponibili per l&#39;ordine non devono contenere la funzione RESTITUISCI dopo le restituzioni create per tutti gli articoli nella quantità totale

È stato risolto un problema a causa del quale il campo available_actions nella query customer.orders di GraphQL includeva erroneamente RETURN dopo la creazione di una restituzione completa per tutti gli articoli. L’azione RETURN viene ora rimossa correttamente al termine del processo di restituzione.

_LYNX-634_

#### Compatibilità Storefront: aggiorna la logica per ottenere il nome della tabella con il prefisso e altri miglioramenti minori

È stata aggiornata la logica per recuperare il nome della tabella con il prefisso (relativo alle modifiche SCP).

_LYNX-637_

#### Il salvataggio nella rubrica non funziona quando si utilizza il campo same_as_shipping di setBillingAddressOnCart GQL

È stato risolto un problema a causa del quale l’indirizzo di spedizione non veniva salvato nella rubrica del cliente quando si utilizzava la mutazione GraphQL setBillingAddressOnCart con il campo same_as_shipping impostato su true. Ora l&#39;indirizzo di spedizione viene memorizzato correttamente come previsto.

_LYNX-643_

#### Standarizzare order_id nelle mutazioni

L’input order_id nelle mutazioni è stato standardizzato e il modello e-mail di conferma dell’annullamento dell’ordine è stato aggiornato in modo da esporre l’ID incremento invece dell’ID ordine.

_LYNX-650_

#### CustomerOrder non visualizza i commenti dell&#39;ordine

È stato risolto un problema relativo a CustomerOrder che consentiva di includere i commenti relativi agli ordini nelle query di GraphQL relative agli ordini dei clienti e dei clienti.

_LYNX-651_

#### original_item_price non deve includere alcuno sconto

È stata aggiornata la logica per original_item_price in GraphQL Cart Item price per escludere gli sconti.

_LYNX-652_

#### I prodotti del bundle mostrano ancora &quot;IN_STOCK&quot; quando uno dei loro prodotti in bundle è esaurito

È stato risolto un problema a causa del quale product.stock_status per i prodotti bundle mostrava ancora &quot;IN_STOCK&quot; anche quando uno degli articoli in bundle era esaurito.

_LYNX-681_

#### La query del cliente restituisce un errore server interno se per un cliente esiste un valore per l’attributo personalizzato eliminato

È stato risolto il problema a causa del quale la query del cliente restituiva un errore interno del server quando un attributo personalizzato eliminato aveva ancora un valore memorizzato. Ora, se viene richiesto un attributo non esistente, viene restituito un messaggio di errore corretto. La cache necessaria viene invalidata al momento dell’eliminazione dell’attributo personalizzato del cliente.

_LYNX-686_

#### Parametro azione per i collegamenti di conferma per restituzione e annullamento

È stato aggiunto un parametro di azione per i collegamenti correlati all’e-mail di conferma per restituzione e annullamento

_LYNX-687_

#### L’URL di conferma dell’utente ospite viene reindirizzato alla pagina di stato dell’ordine poiché manca orderRef (per GuestRMA)

È stato aggiunto il parametro orderRef al collegamento nell’e-mail di conferma RMA per il guest

_LYNX-688_

#### L’URL di conferma dell’utente ospite viene reindirizzato alla pagina di stato dell’ordine perché manca orderRef

È stato aggiunto il parametro orderRef al collegamento nell’e-mail di conferma per l’annullamento dell’ordine dei clienti

_LYNX-689_

#### Problemi relativi alla query del cliente quando RMA è disabilitato

È stata aggiornata la logica di GraphQL per garantire che le restituzioni create in precedenza rimangano accessibili anche quando RMA è disabilitato a livello globale. Il messaggio di errore è stato rimosso per migliorare l’interfaccia utente di storefront, consentendo ai clienti di visualizzare ancora i resi passati.

_LYNX-690_

#### GraphQL non restituisce i dati del carrello aggiornati quando vengono applicati coupon in conflitto

È stato risolto un problema a causa del quale l’applicazione di un coupon in conflitto con priorità maggiore generava un messaggio di errore senza restituire i dati del carrello aggiornati. Ora, quando un nuovo coupon invalida quello esistente, la mutazione restituisce correttamente il carrello con il coupon valido applicato.

_LYNX-696_

#### Impossibile restituire null per il campo &quot;TaxItem.title&quot; non nullable in placeOrder GQL

È stato risolto un problema che causava un errore interno del server a causa della mutazione placeOrder non riuscita a causa di un valore null per il campo TaxItem.title non nullable. Ora, il campo restituisce sempre un valore valido, garantendo il corretto inserimento dell’ordine.

_LYNX-699_

#### EstimateTotals: gli sconti sono nulli per i tipi di prodotto virtuali

È stato risolto il problema a causa del quale la mutazione estimateTotals restituiva un valore null per gli sconti quando un codice di sconto veniva applicato a un carrello contenente prodotti virtuali.

_LYNX-702_

#### Il prodotto del bundle non restituisce la percentuale e l&#39;importo di sconto corretti

Sono state introdotte nuove proprietà &quot;catalog_discount&quot; e &quot;row_catalog_discount&quot; per i prezzi degli articoli del catalogo, in modo da visualizzare gli importi e le percentuali di sconto corretti a livello di riga e di singolo articolo.

_LYNX-703_

#### Configurazione del messaggio regalo a livello di prodotto

È stato risolto un problema a causa del quale i messaggi regalo non venivano applicati a livello di prodotto quando era disabilitato a livello globale. Ora, se i messaggi regalo sono abilitati per un prodotto specifico, possono essere aggiunti correttamente utilizzando la mutazione updateCartItems e verranno salvati e riflessi correttamente.

_LYNX-714_

#### Problema relativo alla rimozione della confezione regalo dall&#39;elemento del carrello

È stato risolto il problema che impediva la rimozione della confezione regalo da un elemento del carrello utilizzando la mutazione updateCartItems. Ora, sia l&#39;applicazione che la rimozione di confezione regalo funzionano correttamente senza errori.

_LYNX-717_

#### La funzione del cliente registrato corrispondente non funziona in Boilerplate e la mutazione trackViewedProduct deve essere abilitata per gli ospiti.

È stata esposta la mutazione trackViewedProduct per tenere traccia dell’evento di visualizzazione del prodotto per clienti e ospiti

_LYNX-751_

#### la query cart.rules restituisce un errore invece di un array vuoto se non vengono applicate regole attive del carrello

È stata corretta la query cart.rules che restituiva un array vuoto anziché un errore quando non venivano applicate regole attive per il carrello.

_LYNX-757_

#### Problema durante il recupero delle confezioni regalo per gli articoli del carrello

È stata aggiornata la logica di recupero per restituire le opzioni di confezione regalo per gli articoli del carrello quando è disabilitata a livello globale ma abilitata a livello di prodotto

_LYNX-758_

#### Le chiamate GraphQL con il metodo OPTIONS restituiscono il codice di risposta 500 quando è installato il pacchetto di compatibilità adobe-commerce/storefront

È stato risolto un problema a causa del quale le chiamate di GraphQL eseguite con il metodo OPTIONS restituivano un errore interno del server 500 quando era installato il pacchetto di compatibilità adobe-commerce/storefront-compatibility. L’endpoint ora restituisce correttamente una risposta 200/204 come previsto.

_LYNX-778_

### Altri strumenti per sviluppatori

#### [Problema] È stato corretto un errore di sintassi HTML in visual.phtml

Il sistema ora chiude correttamente il tag di inizio nel file visual.phtml, garantendo la sintassi HTML corretta. In precedenza, il tag di inizio non veniva chiuso correttamente, causando un errore di sintassi HTML.

_AC-10658 - [Problema GitHub](https://github.com/magento/magento2/issues/38247) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37457)_

#### [Problema] cambiato &quot;attivo&quot; in &quot;abilitato&quot; nel comando bin/magento maintenance:status

Il sistema ora fornisce messaggi di stato più precisi per il comando della modalità di manutenzione, cambiando lo stato da &quot;attivo&quot; a &quot;abilitato&quot; e da &quot;non attivo&quot; a &quot;disabilitato&quot;. In precedenza, il messaggio di stato per il comando della modalità di manutenzione veniva visualizzato come &quot;attivo&quot; o &quot;non attivo&quot;, il che poteva creare confusione.

_AC-11474 - [Problema GitHub](https://github.com/magento/magento2/issues/38486) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38410)_

#### La navigazione nella struttura delle categorie causa errori in Redis: &quot;La sessione di Redis ha superato le connessioni simultanee&quot;

_AC-12571 - [Problema GitHub](https://github.com/magento/magento2/issues/38851) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0611e750)_

#### Problemi CSP combinati con dev/css/use_css_critical_path

Il sistema ora carica correttamente i file CSS in modo asincrono sulle pagine di pagamento, anche quando l’impostazione &quot;dev/css/use_css_critical_path&quot; è abilitata, garantendo che tali pagine vengano sottoposte a rendering con gli stili CSS appropriati. In precedenza, i criteri sulla sicurezza dei contenuti (CSP) con restrizioni impedivano l’esecuzione di JavaScript in linea, causando il mancato caricamento dei file CSS come previsto.

_AC-12731 - [Problema GitHub](https://github.com/magento/magento2/issues/39020) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39040)_

#### Utilizzo del tipo virtuale per configurare il plug-in. Impossibile generare correttamente il metodo intercettore nel comando `setup:di:compile`

Il sistema ora genera correttamente i metodi intercettore quando si utilizza un tipo virtuale per configurare un plug-in, garantendo risultati coerenti sia in modalità precompilata che in modalità runtime. In precedenza, il sistema generava risultati errati se precompilato rispetto alla compilazione in fase di esecuzione.

_AC-13398 - [Problema GitHub](https://github.com/magento/magento2/issues/33980) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38141)_

#### Test di unità Adobe Commerce 2.4.7-p3 non riusciti

Non sono richieste note sulla versione.

_ACP2E-3631 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Metodi di pagamento, ordine

#### Flusso di pagamento Papale I dettagli della carta di credito salvati per un uso successivo non vengono visualizzati nella pagina del metodo di pagamento memorizzato

Flusso di pagamento papale precedente I dettagli della carta di credito salvati per un uso successivo non venivano visualizzati nella pagina del metodo di pagamento memorizzato, che ora è fisso i dettagli della carta di credito vengono visualizzati nella pagina del metodo di pagamento memorizzato.

_AC-13699 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Pagamenti

#### Il pagamento con carta di credito (collegamento flusso di pagamento) non funziona

Precedente Ottenere errore (pagamento è stato rifiutato) durante il posizionamento dell&#39;ordine con carta di credito dopo la correzione Ordine effettuato correttamente.

_AC-13414 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a68324bc)_

#### Payflow crea una nuova transazione ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione

Il sistema ora recupera correttamente le informazioni sulle transazioni senza creare una nuova transazione di pagamento ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione. In precedenza, facendo clic sul pulsante Recupera, veniva erroneamente creata una nuova transazione di pagamento per un ordine già pagato.

_ACP2E-2841 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Il messaggio Paylater non viene visualizzato in PDP per l&#39;account commerciante paypal canadese

Il sistema ora visualizza correttamente il messaggio PayLater per i conti commerciali PayPal canadesi sulla pagina Dettagli prodotto (PDP) quando il paese dell&#39;acquirente può essere determinato dall&#39;indirizzo di fatturazione o dalla spedizione del conto. In precedenza, il messaggio PayLater non veniva visualizzato a causa di un parametro mancante, causando un errore nella console del browser.

_ACP2E-3028 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Il rimborso dell&#39;ordine PayPal si traduce in una nota di credito duplicata

È stata corretta l&#39;emissione di note di credito create tramite IPN per il servizio di pagamento PayPal.

_ACP2E-3143 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La regola del prezzo del carrello non funziona per Paypal

L&#39;importo corretto viene visualizzato sul lato PayPal quando lo sconto è applicato per metodo di pagamento

_ACP2E-3163 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud] utenti con un ruolo specifico non possono accedere

l&#39;utente amministratore con un ruolo che contiene solo l&#39;accesso alla sezione PayPal ora può accedere senza errori

_ACP2E-3208 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

### Prestazioni

#### Problema impostazioni attributi prodotto predefiniti

Il sistema ora consente agli utenti di deselezionare un’opzione predefinita per un attributo di prodotto, assicurandosi che l’attributo non abbia sempre un set predefinito. In precedenza, una volta impostato un valore predefinito per un attributo di prodotto, non era possibile deselezionarlo, in modo che l’attributo avesse sempre un valore predefinito.

_AC-11932 - [Problema GitHub](https://github.com/magento/magento2/issues/38703) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] Pulizia del codice, aggiunta di un nuovo blocco di testa critico e spostamento di un css critico prima delle risorse

Il sistema ora include un nuovo blocco di testa critico e sposta CSS critico prima delle risorse, consentendo una maggiore personalizzazione e ottimizzazione delle prestazioni nel front-end. In precedenza, il CSS critico non veniva posizionato prima delle risorse, limitando le opportunità di personalizzazione e ottimizzazione.

_AC-12000 - [Problema GitHub](https://github.com/magento/magento2/issues/38748) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35580)_

#### La compilazione del tema si interrompe quando l&#39;host Mysql contiene informazioni sulla porta

Il sistema ora gestisce correttamente la configurazione host MySQL che include le informazioni sulle porte, garantendo la corretta compilazione del tema. In precedenza, la compilazione del tema non riusciva se la configurazione host MySQL nella connessione al database includeva informazioni sulla porta.

_AC-12176 - [Problema GitHub](https://github.com/magento/magento2/issues/38799) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38842)_

#### Supporto per CommandLoaderInterface di Symfony in Magento CLI

Questa modifica riduce i tempi di inizializzazione dell&#39;app Magento CLI consentendo l&#39;inizializzazione differita dei comandi fino al momento in cui sono necessari.

_AC-13471 - [Problema GitHub](https://github.com/magento/magento2/issues/29266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29355)_

#### Problema di prestazioni durante il caricamento degli attributi del prodotto nelle regole del carrello

Sono state migliorate le prestazioni delle query per le regole di vendita, da circa 150 ms a una cifra ms.

_ACP2E-2494 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Prestazioni di indicizzazione parziale del prezzo

Le prestazioni di indicizzazione parziale del prezzo sono state migliorate ottimizzando alcune delle query di eliminazione utilizzate nel processo di indicizzazione.

_ACP2E-2673 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### L’ordine viene rifiutato in caso di configurazione multi-store quando si utilizza l’elaborazione asincrona degli ordini + Termini e condizioni

Gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati vengono ora elaborati.
Prima che venissero automaticamente rifiutati.

_ACP2E-2850 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### L’esecuzione della chiamata API per il resto dell’ordine richiede molto tempo

Il sistema ora esegue la chiamata API Order Rest in un lasso di tempo ragionevole, migliorando le prestazioni durante il recupero di un numero elevato di ordini. In precedenza, l’esecuzione della chiamata API per il resto dell’ordine impiegava molto tempo, causando ritardi durante il recupero di un numero elevato di ordini.

_ACP2E-2910 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188)_

### Prestazioni, Promozione

#### L&#39;esecuzione dell&#39;indicizzatore della regola di vendita è stata interrotta

Il sistema ora completa correttamente l’indicizzatore della regola di vendita anche con un numero elevato di gruppi di filtri combinati, garantendo che le condizioni della regola del carrello vengano applicate al carrello come previsto. In precedenza, l’indicizzatore della regola di vendita non veniva completato quando si registrava un numero elevato di gruppi di filtri combinati, generando un messaggio di errore e impedendo l’applicazione delle condizioni della regola del carrello.

_ACP2E-2617_

### Prezzi

#### Magento2.4.6-p4 Ordina API Articolo semplice senza prezzo

Il sistema ora visualizza correttamente il prezzo dei prodotti semplici quando viene eseguita una query tramite l’API dell’ordine, garantendo una rappresentazione accurata dei dati. In precedenza, il prezzo dei prodotti semplici veniva erroneamente visualizzato come zero nella risposta API.

_AC-11810 - [Problema GitHub](https://github.com/magento/magento2/issues/38603)_

#### Errore di arrotondamento in centesimi nella regola del catalogo

_AC-13855 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/276e0acd)_

### Prodotto

#### I caratteri speciali nel nome configurabile del prodotto associato vengono convertiti in entità HTML.

Il sistema ora mantiene correttamente i caratteri speciali nei nomi dei prodotti associati durante la modifica di un prodotto configurabile, impedendo che vengano convertiti in entità HTML. In precedenza, i caratteri speciali nei nomi dei prodotti associati venivano convertiti in entità HTML quando il prodotto configurabile veniva modificato.

_AC-10535 - [Problema GitHub](https://github.com/magento/magento2/issues/38146) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38447)_

#### La funzione ProductRepository GetById non crea la chiave cache corretta

Il sistema ora crea correttamente una chiave cache nella funzione GetById del ProductRepository, indipendentemente dal fatto che l’ID archivio venga passato come stringa o come numero intero. In questo modo il prodotto viene recuperato dalla memoria nelle chiamate successive, migliorando le prestazioni. In precedenza, il sistema recuperava il prodotto dal database ogni volta che la funzione veniva chiamata, anche con gli stessi parametri, a causa di una creazione errata della chiave della cache.

_AC-10947 - [Problema GitHub](https://github.com/magento/magento2/issues/38384) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38433)_

#### [Problema] [MFTF] Aggiunto AdminClickAddOptionForBundleItemsActionGroup

Il sistema ora include AdminClickAddOptionForBundleItemsActionGroup, che migliora le funzionalità del pannello di amministrazione. In precedenza, questo gruppo di azioni non era disponibile.

_AC-11992 - [Problema GitHub](https://github.com/magento/magento2/issues/30857) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30838)_

#### [Problema] È stato corretto l&#39;errore di battitura nel blocco PHPDoc

Il sistema ora rimuove correttamente una variabile di riferimento sconosciuta in PHPDoc per la dichiarazione della variabile $helper, migliorando la chiarezza e la precisione del codice. In precedenza, questa variabile di riferimento sconosciuta in PHPDoc causava confusione e potenziali imprecisioni nel codice.

_AC-13173 - [Problema GitHub](https://github.com/magento/magento2/issues/38961) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38940)_

#### [Problema] è stato corretto il bundle danneggiato e il layout delle pagine di prodotto scaricabili in Magento >= 2.4.7

Il layout per le pagine di prodotti bundle e scaricabili è stato corretto, garantendo una visualizzazione coerente e corretta su tutti i dispositivi. In precedenza, in queste pagine si verificavano problemi di layout a causa di una ridisposizione del blocco multimediale di informazioni sul prodotto.

_AC-13423 - [Problema GitHub](https://github.com/magento/magento2/issues/39403) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - Il #2 dell&#39;argomento ($storeId) deve essere di tipo int, stringa specificata

Il sistema ora attiva correttamente le e-mail di avviso sul prodotto verificando che l’identificatore dello store sia del tipo di dati corretto. In precedenza, le e-mail di avviso sul prodotto non venivano inviate a causa di una mancata corrispondenza del tipo nell’identificatore dello store.

_AC-5969 - [Problema GitHub](https://github.com/magento/magento2/issues/35602) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### La funzione addFilterToMap di [Cloud] non funziona per alcune colonne

Ora è possibile utilizzare il modulo personalizzato nella griglia dell’ordine. Errori precedenti durante l’utilizzo di un modulo personalizzato.

_ACP2E-2944 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### [Cloud] prodotti nella categoria - Aggiungi prodotti - Assegna - Seleziona tutto

Ora gli utenti possono selezionare o deselezionare i prodotti utilizzando l’interruttore.

_ACP2E-3471_

### Promozione

#### Attributo cliente non visibile durante la creazione dell’account da un invito

Gli attributi del cliente sono disponibili durante la creazione dell’account da un invito.

_ACP2E-2602 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Il codice coupon con limite Usi per coupon non viene rilasciato per il pagamento non riuscito a causa dell’annullamento dell’ordine

Il sistema ora aggiorna immediatamente gli utilizzi dei coupon quando un ordine viene creato o annullato e aggiunge gli utilizzi delle regole a una coda per evitare potenziali deadlock. In questo modo, viene rilasciato un codice coupon con un limite &quot;Usi per coupon&quot; che può essere riutilizzato in caso di annullamento di un ordine a causa di un pagamento non riuscito. In precedenza, il sistema non rilasciava il codice coupon per il riutilizzo in tali casi, causando un messaggio di errore che indicava che il codice coupon non era valido.

_ACP2E-2627 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud] Indicizzatore prodotto regola catalogo di reindicizzazione genera SQLSTATE[HY000]: errore generale: il server MySQL 2006 non è più disponibile.

Il sistema ora gestisce correttamente il valore &quot;batchCount&quot; personalizzato nel file di.xml per &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, impedendo errori SQL come &quot;Errore generale: il server MySQL 2006 non è più disponibile&quot; durante la reindicizzazione dell’indicizzatore del prodotto Catalog Rule a causa di dimensioni batch errate in cataloghi di grandi dimensioni

_ACP2E-2811 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [CLOUD]Regola di prezzo del carrello per il segmento di clienti Visitatori che non applica uno sconto sul carrello

Il sistema ora applica correttamente le regole di prezzo del carrello per i segmenti dei clienti visitatori, anche se la regola non utilizza un coupon, assicurandosi che al carrello vengano applicati gli sconti appropriati. In precedenza, gli sconti non venivano applicati al carrello per i segmenti dei clienti visitatore, a meno che la regola del prezzo del carrello non utilizzasse un coupon.

_ACP2E-2926_

#### Attributo &quot;Type&quot; mancante nella scheda &quot;Products to Match&quot; delle regole prodotto correlate

L’attributo &quot;Type&quot; è ora disponibile come opzione di filtro nella scheda &quot;Products to Match&quot; del modulo &quot;Related Product Rules&quot;, che consente una definizione più precisa della regola. In precedenza, questo attributo mancava dalla scheda &quot;Products to Match&quot; (Prodotti da abbinare), limitando la possibilità di creare criteri di corrispondenza accurati.

_ACP2E-3024_

#### La regola di vendita con l&#39;attributo Passo quantità sconto (Acquista X) causa la mancata applicazione di altre regole

La regola del prezzo del carrello non annulla le regole applicate in precedenza se la quantità del prodotto nel carrello non è sufficiente per applicare la regola.

_ACP2E-3139 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### Problema di prestazioni nella regola prezzo carrello - Modulo Regola vendite anticipate

Sono stati aggiunti indici DB mancanti per i filtri AdvancedSalesRule

_ACP2E-3331_

#### Emetti regole di vendita con sconto importo fisso e &quot;Sconto quantità massima applicato a&quot;

È stato risolto un problema relativo allo sconto sulle regole del carrello che si verifica quando lo sconto sull’importo fisso è configurato per essere applicato per una quantità limitata di prodotti e il carrello. In precedenza, il valore &quot;Sconto quantità massima viene applicato a&quot; veniva utilizzato per calcolare il prezzo dell’articolo corrente nel carrello, non solo per calcolare lo sconto della regola.

_ACP2E-3332 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### [L&#39;aggiornamento del Magento CLOUD] ha fatto sì che i coupon distinguessero tra maiuscole e minuscole

Prima della correzione era necessario digitare il codice del coupon esattamente come era stato configurato prendendo in considerazione maiuscole o minuscole. Ora il coupon viene convalidato nel backend indipendentemente dalla configurazione del codice in maiuscolo o in minuscolo.

_ACP2E-3342_

#### Regole del carrello &quot;Sconto importo fisso per intero carrello&quot;  L&#39;azione applica gli sconti in modo errato

I codici coupon verranno convalidati correttamente, indipendentemente dalla maiuscola o dalla minuscola, se utilizzati per la creazione degli ordini dall’area di amministrazione. In precedenza, il codice del coupon non veniva convalidato se non corrispondeva esattamente alla lettera maiuscola del codice della regola del carrello configurato.

_ACP2E-3349 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### In Backend, i valori store predefiniti per gli attributi del prodotto (anziché i valori admin previsti)

Ora nel back-end vengono utilizzati i valori amministratore invece dei valori di archivio predefiniti per gli attributi del prodotto.

_ACP2E-3374 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Regole del carrello L’azione &quot;Sconto di importo fisso per l’intero carrello&quot; applica gli sconti in modo errato quando si aggiungono prodotti bundle

Le regole del carrello a importo fisso non venivano applicate correttamente per i prodotti bundle. Ora, quando si calcola l&#39;importo dello sconto totale, vengono presi in considerazione i prodotti secondari del bundle, con conseguente calcolo dello sconto corretto.

_ACP2E-3377 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Regole prezzo carrello Calcola erroneamente lo sconto

Gli sconti sull&#39;importo fisso vengono ora calcolati correttamente. Prima della correzione, gli sconti sull&#39;importo fisso non venivano totalizzati correttamente per i prodotti bundle.

_ACP2E-3403 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0b488dd1)_

#### Le categorie nidificate nelle condizioni della regola non vengono visualizzate

È stato risolto un problema a causa del quale le categorie nidificate di livello 3 o categoria non venivano visualizzate nelle regole di marketing per la condizione categoria

_ACP2E-3406 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit e uses_per_customer non vengono aggiornati nella tabella salesrule_coupon

L’aggiornamento di Usi per coupon e Usi per cliente nella regola di prezzo del carrello ora influisce sui coupon generati automaticamente esistenti. In precedenza, i nuovi valori interessavano solo i nuovi coupon

_ACP2E-3432 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### La regola del prezzo del carrello non considera la categoria padre quando si utilizza la condizione &quot;è uguale o maggiore di&quot;.

Le regole di prezzo del carrello ora considerano correttamente la categoria padre quando viene utilizzata in condizioni avanzate

_ACP2E-3456 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93359343)_

#### Calcolo sconto non valido con priorità

Nel caso dell&#39;importo fisso applicato per l&#39;intero tipo di sconto del carrello, l&#39;importo non veniva calcolato correttamente per gli articoli del carrello già scontati da una promozione precedente. Ora, gli sconti sono correttamente sommati.

_ACP2E-3463 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [CLOUD] Il calcolo della spedizione non considera la regola del carrello acquisti

Prima della correzione, una regola del carrello con condizione region non veniva applicata in modo coerente. Dopo la correzione, le regole del carrello con condizioni di area vengono applicate correttamente.

_ACP2E-3472 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### La condizione di SKU della regola del carrello non riesce per la fattura.

Lo sconto sul prodotto del bundle con prezzo dinamico ora si riflette correttamente nella fattura. In precedenza, lo sconto non veniva riportato sulla fattura.

_ACP2E-3491 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Valore di sconto errato quando più regole del prezzo del carrello vengono applicate contemporaneamente ai prodotti scontati/a prezzi speciali

Prima della correzione, l’importo fisso per le regole dell’intero carrello non veniva applicato correttamente se ne veniva applicato più di uno. Ora, le regole del carrello sconti per importo fisso vengono applicate correttamente.

_ACP2E-3498 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Restituisce

#### [CLOUD] Gli utenti amministratori con restrizioni possono visualizzare il menu e i pulsanti restituiti

Gli utenti amministratori con restrizioni ora non hanno accesso ai controlli relativi a RMA (menu e pulsanti).
Gli utenti amministratori con restrizioni precedenti potevano visualizzare il menu e i pulsanti di ritorno.

_ACP2E-3330_

#### La schermata di ritorno è disattivata quando si aggiorna la schermata

L’utente può aggiornare la pagina senza che si verifichi alcuna distorsione dello schermo.

_ACP2E-3443_

### SEO

#### L’aggiunta di riscritture URL con un accento causa un caricamento infinito

Il sistema ora crea e funziona la riscrittura degli URL con accenti, impedendo il caricamento infinito durante il processo di salvataggio. In precedenza, l’aggiunta della riscrittura di un URL con un accento causava un problema di caricamento infinito.

_AC-11907 - [Problema GitHub](https://github.com/magento/magento2/issues/38692) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### Riscrittura URL di categoria errata in più store per la categoria di terzo livello

Genera riscritture URL corrette per gli elementi figlio con chiave URL con ambito personalizzato

_ACP2E-2641 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### I caratteri a doppio byte (caratteri speciali) nel campo Nome prodotto bloccano la creazione del prodotto nel back-end

È stata aggiunta una nuova impostazione che consente di applicare o meno la traslitterazione all’URL del prodotto. L’impostazione è disponibile qui: Negozi > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca: &quot;Applica traslitterazione per URL prodotto&quot;

_ACP2E-2770 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Creazione di voci url_rewrite non corretta con più store in un unico gruppo di store

Prima della correzione, era possibile generare riscritture URL solo a livello di sito web durante la modifica di un prodotto. Con la correzione, è stata introdotta una nuova impostazione (Stores > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca, &quot;URL prodotto - Ambito di riscrittura&quot; con opzioni &quot;Visualizzazione archivio&quot;, &quot;Sito web&quot;) che consente di generare riscritture URL a livello di visualizzazione archivio o sito web.

_ACP2E-3383 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2d627301)_

### Vendite

#### La seconda regola prezzo carrello non viene applicata se la regola Primo carrello è già applicata

_AC-13751_

### Ricerca

#### Ottenere &quot;Immettere un termine di ricerca e riprovare&quot;. errore nella pagina di ricerca avanzata in storefront nella versione 2.4.8-beta1

Il sistema ora visualizza correttamente i risultati della ricerca nella pagina Ricerca avanzata quando un attributo di prodotto è impostato su &quot;No&quot;. In precedenza, se si impostava un attributo di prodotto su &quot;No&quot; e si eseguiva una ricerca, veniva visualizzato un messaggio di errore di tipo &quot;Inserisci un termine di ricerca e riprova&quot;.

_AC-13053 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search dipende da un ramo opensearch-php inesistente

_AC-13721 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/05dc0bbf)_

#### la tabella search_query, se di dimensioni enormi, ha un impatto notevole sul front-end del tempo di caricamento

È stato migliorato il tempo di caricamento della pagina nell’elenco delle ricerche. Prima della correzione, la pagina dell’elenco di ricerca subiva un ritardo a causa di una query non ottimizzata.

_ACP2E-3362 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Sicurezza

#### [Problema] Popup Font CSP Paylater mancante

Il sistema ora consente il caricamento del font &quot;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;&quot; senza violare la direttiva Content Security Policy, garantendo la corretta visualizzazione del Popup Paylater. In precedenza, il caricamento del font veniva rifiutato a causa di una violazione della direttiva Content Security Policy, causando problemi di visualizzazione con il Popup Paylater.

_AC-11855 - [Problema GitHub](https://github.com/magento/magento2/issues/38624) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37401)_

#### [Problema] Aggiornamento del testo DOM js.js reinterpretato come HTML

L’utilizzo di innerText evita il rischio di iniezioni di HTML, in quanto queste proprietà sfuggono automaticamente a qualsiasi carattere speciale di HTML nel testo fornito. Questa correzione, aiuta a prevenire le vulnerabilità cross-site scripting (XSS) trattando l’input come testo normale anziché come HTML interpretato.

_AC-12035 - [Problema GitHub](https://github.com/magento/magento2/issues/38767)_

#### ReCaptcha V2 non viene visualizzato correttamente al momento del pagamento per la lingua tedesca

Precedentemente i recaptcha da sotto l&#39;indirizzo e-mail da checkout appaiono sformattati per le lingue con parole lunghe, come il tedesco. Dopo questo il recaptcha si presenta come tutti gli elementi recaptcha dal resto delle aree.

_ACP2E-3273 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Captcha all’accesso come amministratore non richiede interazione per alcuni utenti

ReCaptcha per l’accesso amministratore è convalidato come previsto

_ACP2E-3300 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/8f64ab3c)_

### Spedizione

#### [Problema] È stato corretto un errore di battitura in tracking.phtml. Le funzioni JS sono state rinominate &quot;currier&quot; in &quot;carrier&quot;

Il sistema ora utilizza correttamente il termine &quot;carrier&quot; invece del &quot;currier&quot; errato nelle funzioni del gestore JavaScript utilizzate nel modello di tracciamento degli ordini, garantendo una corretta denominazione delle funzioni e chiarezza del codice. In precedenza, veniva utilizzato il termine errato &quot;currier&quot;, che portava a una potenziale confusione e incoerenza nella base di codice.

_AC-10757 - [Problema GitHub](https://github.com/magento/magento2/issues/34523) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33414)_

#### UPS REST &quot;Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura&quot;

Assicurati che le tariffe UPS siano visibili nel carrello e nel pagamento.

_AC-11938 - [Problema GitHub](https://github.com/magento/magento2/issues/38618) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/493e01f5)_

#### UPS REST &quot;sandbox&quot; e &quot;prod&quot; aggiornamento delle istruzioni di installazione in devdoc

_AC-12938_

#### [Problema] Correggere l&#39;ortografia delle variabili per l&#39;indirizzo del cliente

Il sistema ora scrive correttamente le variabili per gli indirizzi dei clienti, garantendo una visualizzazione accurata nell’area conto del front-end. In precedenza, l’ortografia errata di queste variabili poteva causare errori durante le revisioni del codice locale.

_AC-13172 - [Problema GitHub](https://github.com/magento/magento2/issues/32817) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32815)_

#### Finestra di tracciamento che mostra una data di consegna prevista errata

Visualizza la data di consegna corretta per il gestore Fedex.

_ACP2E-2738 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### Le Tariffe Delle Tabelle Continuano A Essere Visualizzate Anche Se Viene Applicata La Spedizione Gratuita

Il metodo di spedizione Tariffa tabella ora viene visualizzato anche se la spedizione gratuita diventa disponibile dopo l&#39;applicazione del coupon

_ACP2E-2763 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Test MFTF AdminCreatingShippingLabelTest non riuscito a causa di credenziali non aggiunte nell&#39;ambiente Jenkins

correzione test mftf

_ACP2E-2765 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### L’API Track di FedEx non funziona con le credenziali REST

In precedenza, l’integrazione FedEx non richiedeva chiavi API aggiuntive per l’API di tracciamento. Ora è stata aggiunta una nuova configurazione per supportare le chiavi API di tracciamento.

_ACP2E-3340 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Tariffe negoziate FedEx di Cloud] non restituite su REST

Prima della correzione, i tassi specifici dell’account FedEx non venivano inviati nella risposta, anche attraverso la documentazione FedEx che avrebbe dovuto essere inviata. Dopo la correzione, i tassi specifici dell’account vengono inviati alla risposta modificando la richiesta dal nostro lato.

_ACP2E-3354 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Staging e anteprima

#### Le impostazioni dell’aggiornamento pianificato non vengono salvate se originariamente aggiunte eseguendo l’aggiornamento

Il sistema ora cancella correttamente i valori degli attributi del prodotto negli aggiornamenti pianificati successivi quando tali attributi vengono modificati nell&#39;aggiornamento attualmente in esecuzione. In precedenza, quando un attributo di prodotto veniva modificato da un aggiornamento pianificato in esecuzione, non era possibile cancellare tali valori durante la creazione di un nuovo aggiornamento pianificato, richiedendo all’utente di modificarli nuovamente dopo la creazione.

_ACP2E-2901_

#### La regola del prezzo del carrello dalla data e fino alla data non è sincronizzata con l&#39;aggiornamento della gestione temporanea

Le date vengono salvate in base agli aggiornamenti per Staging regole prezzo carrello.

_ACP2E-2999_

#### Errore JS nell’anteprima di staging

Ora il file form-mini-stub.js viene caricato correttamente senza errori di sintassi Js negli strumenti per sviluppatori.

_ACP2E-3104_

#### Impossibile aggiornare il contenuto di staging del prezzo speciale del prodotto

Il sistema ora consente di modificare la data di fine di una campagna di aggiornamento dei prezzi dopo il suo avvio, in modo che gli utenti possano apportare le modifiche necessarie alle campagne. In precedenza, veniva generato un errore durante il tentativo di aggiornare la data di fine di una campagna attiva, impedendo agli utenti di apportare modifiche.

_ACP2E-3162_

#### Impossibile aggiornare l’aggiornamento pianificato quando si utilizza un attributo di categoria personalizzato univoco

È stato risolto un problema che impediva l’aggiornamento pianificato di una categoria se questa aveva un attributo univoco

_ACP2E-3453 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Targeting

#### [Problema] Consente l&#39;utilizzo di intervalli CIDR nell&#39;elenco consentiti di manutenzione

Il sistema ora supporta l’utilizzo di intervalli CIDR nella modalità di manutenzione elenco Consenti IP, consentendo a un intervallo di indirizzi IP di ignorare la modalità di manutenzione. In precedenza, la modalità di manutenzione Consenti elenco IP consentiva solo a singoli indirizzi IP di ignorare la modalità di manutenzione.

_AC-9432 - [Problema GitHub](https://github.com/magento/magento2/issues/37943) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30699)_

### Imposta

#### [Problema] Promozione proprietà costruttore funzionalità/php8.1: SQL grafico

Sostituisci quasi tutte le proprietà con la promozione della proprietà del costruttore nel modulo wee graph ql:

_AC-13295 - [Problema GitHub](https://github.com/magento/magento2/issues/39309) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36975)_

#### L&#39;FPT (Fixed Product Tax) non funziona con i prodotti configurabili

FPT per varianti di prodotto configurabili che funzionano correttamente.

_ACP2E-3193 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Framework di test

#### Test di integrazione non riuscito testDbSchemaUpToDate a causa del tipo di colonna JSON

Il sistema ora riconosce correttamente i tipi di colonna JSON nello schema del database durante gli integration test, impedendo gli errori dei test a causa di una mancata corrispondenza tra lo schema del database e lo schema dichiarativo. In precedenza, il sistema identificava erroneamente i tipi di colonna JSON come LONGTEXT in MariaDB, causando l’errore dei test di integrazione.

_AC-11654 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [Problema] ortografia correzione PHPDoc

Il sistema ora riconosce correttamente i metodi obsoleti nelle IDE a causa di una correzione ortografica nel PHPDoc. In precedenza, un errore ortografico nel PHPDoc causava il mancato riconoscimento da parte degli IDE di alcuni metodi come obsoleti.

_AC-13362 - [Problema GitHub](https://github.com/magento/magento2/issues/31399) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118: Verifica del comportamento con il carrello acquisti persistente dopo la scadenza della sessione

_AC-13478 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### Test di integrazione non riusciti Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission

_AC-13716_

#### [Confronto database] Errore irreversibile se il database contiene record sulla regola di destinazione senza condizioni

In precedenza, se Database contiene record sulla regola di destinazione senza alcuna condizione, si verificavano errori irreversibili ma dopo che lo strumento Correggi confronto database è stato passato senza errori irreversibili.

_AC-13722_

#### Correggi i test statici per consentire l’utilizzo da parte di estensioni di terze parti

_AC-13848 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9e383b4d)_

#### [Errore interno] di applicazione della correzione non visualizzato durante l&#39;esecuzione o nei registri

&quot;-

_ACP2E-3334 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest

Mftf fissi

_ACP2E-3458 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Framework interfaccia utente

#### Correzione della vulnerabilità di sicurezza di Prototype.js CVE-2020-27511

Il sistema è stato aggiornato per risolvere la vulnerabilità di sicurezza CVE-2020-27511 in Prototype.js 1.7.3, migliorando la sicurezza complessiva del sistema. Prima di questo aggiornamento, il sistema era suscettibile a un’espressione regolare Denial of Service (ReDOS) attraverso la rimozione di tag HTML creati.

_AC-12128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less utilizza il prefisso pub/prefisso per sourcemaps

Il sistema ora genera meno mappe sorgente/css senza il prefisso /pub per i percorsi quando si utilizza grunt, eliminando la necessità di una soluzione alternativa nella configurazione del server web. In precedenza, l’utilizzo del prefisso /pub nei percorsi sourcemaps richiedeva una configurazione specifica nel server web per funzionare correttamente.

_AC-12189 - [Problema GitHub](https://github.com/magento/magento2/issues/38837) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38840)_

#### Campo File Componente Interfaccia Utente

Il sistema ora convalida correttamente il campo file in un modulo componente dell’interfaccia utente, consentendo l’invio del modulo senza errori quando viene selezionato un file. In precedenza, la convalida non riusciva anche quando veniva selezionato un file, impedendo l’invio del modulo.

_AC-12432 - [Problema GitHub](https://github.com/magento/magento2/issues/38908) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39004)_

#### [Problema] Formato data migliorato nella console js: passa da 12 a 24 ore dopo...

Formato data migliorato nella console js: passa da 12 ore a 24 ore

_AC-12645 - [Problema GitHub](https://github.com/magento/magento2/issues/38983) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38972)_

#### [Problema]: aggiunta della generazione sourceMap per un numero inferiore di file in modalità sviluppatore

Il sistema ora genera mappe sorgente per un numero minore di file in modalità sviluppatore, semplificando l&#39;identificazione dell&#39;origine di uno stile. In precedenza, identificare la sorgente di uno stile era difficile quando si eseguiva il sistema in modalità sviluppatore con compilazione senza lato server.

_AC-12650 - [Problema GitHub](https://github.com/magento/magento2/issues/38982) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38977)_

#### È in corso la distribuzione di contenuto statico per i moduli disabilitati

Il sistema ora esclude i CSS relativi ai moduli disabilitati dai file di output CSS finali, garantendo che non vengano caricati stili non necessari. In precedenza, i CSS relativi ai moduli disattivati venivano inclusi nei file di output CSS finali, determinando il caricamento di stili aggiuntivi e non necessari.

_AC-1306 - [Problema GitHub](https://github.com/magento/magento2/issues/24666) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32922)_

#### Comportamento incoerente nell’ordinamento &quot;esaurito&quot; con soglia minima di stock

Il sistema ora ordina correttamente i prodotti nel catalogo in base ai livelli di stock, rispettando la soglia di stock minima impostata e spostando in modo coerente gli articoli esauriti nella parte inferiore dell’elenco. In precedenza, il comportamento di ordinamento era incoerente: gli elementi non venivano sempre visualizzati nell’ordine corretto in base ai livelli di stock e le modifiche nell’ordinamento potevano verificarsi in modo imprevedibile dopo il salvataggio, l’aggiornamento o la modifica della gerarchia di categorie.

_AC-13459 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### Suggerimenti per migliorare la segnalazione degli errori per i problemi di caricamento di require.js

Questa PR migliora il messaggio di errore quando i requisiti non riescono a caricare un componente.

_AC-13472 - [Problema GitHub](https://github.com/magento/magento2/issues/36761) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38971)_

#### Errori di deprecazione di PHP 8.4 che causano errori di build in 2.4-development

_AC-14004 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [Problema] Non caricare il contesto del blocco di back-end sul front-end

Il sistema ora assicura che il contesto del blocco back-end non venga caricato sul front-end, impedendo la creazione di sessioni backend non necessarie e potenziali blocchi di sessione. In precedenza, il sistema caricava erroneamente il contesto del blocco back-end sul front-end, determinando la creazione di sessioni back-end e potenziali blocchi di sessione.

_AC-9007 - [Problema GitHub](https://github.com/magento/magento2/issues/37617) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36368)_

#### [Problema] Rimuovi riepilogo di revisione degli script non necessari

Il sistema ora ottimizza il tempo di caricamento delle pagine rimuovendo gli script JavaScript non necessari dalla sezione di valutazione, invece di utilizzare gli stili CSS in linea per un codice più efficiente e leggibile. In precedenza, l’utilizzo di script JavaScript per la sezione di valutazione poteva potenzialmente rallentare il tempo di caricamento delle pagine.

_AC-9168 - [Problema GitHub](https://github.com/magento/magento2/issues/37776) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/34643)_

#### Eccezione durante il controllo del saldo di una gift card quando Recaptcha è abilitato

Gli utenti potranno recuperare il saldo della gift card nella schermata Visualizza e modifica carrello. In precedenza, questi dettagli non venivano visualizzati quando reCAPTCHA era abilitato.

_ACP2E-2529 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [CHIARIMENTO] Richiesta di funzionalità Conformità ADA

Il sistema ora garantisce la conformità ADA rimuovendo le proprietà CSS non supportate e sostituendole con quelle supportate nel file print.css. In precedenza, l’utilizzo di proprietà CSS non supportate causava problemi di compatibilità con il browser.

_ACP2E-2729 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] Codice libreria di confusione in effect-drop.js di AC 2.4.4-p8

Il sistema ora implementa correttamente la libreria effect-drop.js, garantendo il corretto funzionamento degli effetti dell’interfaccia utente jQuery. In precedenza, la libreria effect-drop.js veniva erroneamente sovrascritta con la libreria effect-clip.js, causando potenziali problemi con gli effetti dell’interfaccia utente jQuery.

_ACP2E-3061 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Intestazione sito | Caratteri speciali che interrompono la sezione di benvenuto del cliente

Dopo la correzione, i caratteri speciali vengono visualizzati correttamente nella sezione di benvenuto del cliente.

_ACP2E-3367 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### L’edizione del segmento cliente non riesce con l’intervallo di dati

È possibile salvare il segmento del cliente con la condizione Intervallo date, quando è stata modificata solo una delle date.

_ACP2E-3561 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

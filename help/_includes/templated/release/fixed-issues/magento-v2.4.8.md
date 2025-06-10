---
source-git-commit: 21da8a0133c3c70c2c37851aca79e2d5d8f82905
workflow-type: tm+mt
source-wordcount: '25731'
ht-degree: 0%

---
# Note sulla versione di Magento Open Source (v2.4.8)

## In evidenza

Le 31 caratteristiche principali riportate di seguito si applicano alla versione 2.4.8 di Magento Open Source.

### Framework

* __Aggiornamento delle dipendenze di Compositore lega/flysystem alla versione più recente__
Aggiorna le dipendenze del Compositore leasing/flysystem 2.x alla versione più recente 3.x
  _AC-10721 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/91cb4d46>)_
* __Verifica le versioni più recenti di php-amqplib/php-amqplib__
È stata aggiornata la versione più recente php-amqplib/php-amqplib :^3.x
  _AC-11673 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_
* __jQuery/fileuploader: pulizia css dopo la migrazione alla libreria uppy__
È stata rimossa la libreria jQuery/fileUploader perché è stata migrata alla libreria Uppy
  _AC-11911 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/7cabfb46>)_
* __Aggiunta della compatibilità con MySQL 8.4 LTS per Magento CE__
  _AC-11995 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Pulizia cartella ExtJs dopo la migrazione alla libreria jsTree__
È stata rimossa la cartella extJs perché la relativa funzionalità è stata migrata a jsTree
  _AC-12015 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/7cabfb46>)_
* __Aggiorna la dipendenza del sistema monologo/monologo alla versione principale più recente__
Il sistema è stato aggiornato per utilizzare la versione principale più recente della libreria &quot;monologo/monologo:^3.x&quot;, garantendo compatibilità e prestazioni migliorate. In precedenza, il sistema utilizzava una versione obsoleta della libreria &quot;monologo/monologo&quot; che avrebbe potuto portare a potenziali problemi e limitazioni.
  _AC-12022 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_
* __Aggiorna la dipendenza wikimedia/less.php alla versione principale più recente__
Il sistema è stato aggiornato per utilizzare la versione principale 5.x più recente della libreria &quot;wikimedia/less.php&quot;, garantendo compatibilità e funzionalità aggiornate. In precedenza, il sistema utilizzava una versione obsoleta della libreria che poteva causare problemi di sicurezza.
  _AC-12023 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_
* __Aggiorna la dipendenza della libreria jquery/validate alla versione secondaria più recente__
Aggiorna la dipendenza della libreria jquery/validate alla versione secondaria più recente 1.20.0
  _AC-12024 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_
* __Aggiorna la dipendenza di sistema moment.js alla versione secondaria più recente__
Aggiorna la dipendenza del sistema moment.js alla versione secondaria più recente 2.30.1
  _AC-12025 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/de4dfb8e>)_
* __Aggiunta della compatibilità con MySQL 8.4 LTS per EE__
  _AC-12032 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Aggiungi compatibilità con MySQL 8.4 LTS per B2B__
  _AC-12034 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Aggiunta della compatibilità con MySQL 8.4 LTS per le estensioni del bundle__
  _AC-12074 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Aggiunta della compatibilità con MariaDB 11.4 LTS per CE__
Aggiunto supporto MariaDB 11.4 con Adobe Commerce ed estensioni
  _AC-12085 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_
* __Ottimizzazione sottoscrittori - PhpUnit10__
  _AC-12165 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/90e25b6b>)_
* __Nuovi tentativi di connessione di supporto per la sessione Redis e compatibili con colinmollenhour/php-redis-session-abstract v2.0.0__
È stata aggiornata la versione più recente di colinmollenhour/php-redis-session-abstract v2.0.0, compatibile con adobe commerce
  _AC-12267 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Esaminare gli errori dei test di automazione con MySQL 8.4 LTS__
  _AC-12576 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/672a2e61>)_
* __Aggiunta della compatibilità con MariaDB 11.4 LTS per EE__
Aggiunto supporto MariaDB 11.4 con Adobe Commerce ed estensioni
  _AC-12595 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_
* __Aggiornamento delle dipendenze del compositore laminas alla versione più recente__
Il sistema ora supporta le versioni più recenti delle dipendenze del compositore laminas:
laminas/laminas-servicemanager
server laminas/laminas
laminas/laminas-stdlib
laminas/laminas-validator
compatibilità e funzionalità aggiornate. In precedenza, l’aggiornamento alle versioni più recenti di queste dipendenze poteva causare problemi di incompatibilità con le versioni precedenti e errori di test.
  _AC-12715 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_
* __Esaminare l&#39;errore dello unit test dovuto all&#39;aggiornamento della patch phpunit durante l&#39;aggiornamento del componente__
  _AC-12823 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_
* __[Parte 1] - Aggiorna tutta la libreria js e la dipendenza npm con l&#39;ultima versione disponibile__
il supporto per la versione del compositore era disponibile solo nella versione 2.2.x del compositore. Ora il supporto è stato esteso anche alla versione 2.4.x.
  _AC-13076 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/19844aa0>)_

### Ordine

* __[Richiesta di funzionalità] Il cliente suggerisce che il pulsante Invia commento nella pagina Dettagli ordine sia confuso e debba essere cambiato__
Per ridurre al minimo la confusione, l’etichetta del pulsante &quot;Invia commento&quot; è stata modificata in &quot;Aggiorna&quot; nella pagina dei dettagli dell’ordine.
  _ACP2E-2709 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/488c1034>)_

### Altro

* __Gli indicizzatori impostati vengono visualizzati come predefiniti quando viene installata la nuova versione di Adobe Commerce__
Dopo l&#39;installazione di Magento, lo stato dell&#39;indicizzatore deve essere *Pronto* per impostazione predefinita.
  _AC-11420 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/71432aeb>)_
* __Nell&#39;installazione di Magento esistente quando si installa il modulo di indicizzazione di terze parti, impostare gli indicizzatori in Aggiorna per pianificazione per impostazione predefinita.__
Per impostazione predefinita, tutti i nuovi indicizzatori sono in modalità [Aggiorna in base alla pianificazione]. In precedenza, la modalità predefinita era [Aggiorna al salvataggio]. Lo stesso vale per gli indicizzatori personalizzati.
  _AC-11421 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/71432aeb>)_
* Le opzioni __Elasticsearch 7 e 8 devono essere impostate su Obsoleto in Admin config.__
L’opzione Elasticsearch 8 nell’Admin Config viene visualizzata con testo obsoleto per informare gli utenti che Elasticsearch 8 non è più un’opzione consigliata da utilizzare.
  _AC-12480 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/0611e750>)_
* __Aggiungi una nota di testo quando l&#39;opzione Elasticsearch è selezionata in Admin Configuration__
Viene aggiunta una nota di testo per informare gli utenti amministratori di Adobe Commerce che elasticsearch non è più supportato da Adobe ed è obsoleto.
  _AC-12481 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/0611e750>)_
* __Distribuisci la patch per il miglioramento delle prestazioni delle operazioni di livello-prezzo in 2.4.8__
Il sistema ora consente aggiornamenti in blocco più efficienti dei prezzi di livello senza causare problemi di prestazioni o mancata risposta del sito quando si utilizza l’endpoint REST API &quot;/V1/products/tier-price&quot;. In precedenza, l’aggiornamento di un numero elevato di prezzi utilizzando questo endpoint poteva causare problemi di prestazioni e la mancata risposta del sito.
  _AC-13448 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/082d981c>)_
* __Rimuovi tutti gli avvisi riservati sul copyright di Adobe dagli archivi di Magento Open Source__
Tutti gli avvisi riservati sul copyright di Adobe sono stati rimossi dagli archivi open source, in modo da garantire che venga utilizzata solo la forma ridotta del copyright di Adobe. In precedenza, alcuni file negli archivi pubblici contenevano avvisi riservati sul copyright di Adobe, che hanno portato a escalation dalla community.
  _AC-13550 - [Problema GitHub](https://github.com/magento/magento2/issues/39493) - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/4bca5dfe>)_

### Framework interfaccia utente

* Migrazione di __[2.4.8-beta1] TinyMCE 5 a TinyMCE 7__
La migrazione da TinyMCE 5 a TinyMCE 7.3.0 è stata supportata per Adobe Commerce; in precedenza era in uso la versione 5.10.2, che era obsoleta e segnalava vulnerabilità di sicurezza
  _AC-12726 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_
* __[2.4.8-beta1] Migrazione di TinyMCE 5 a TinyMCE 7 Page Builder__
La migrazione da TinyMCE 5 a TinyMCE 7.3.0 è stata supportata per Adobe Commerce; in precedenza era in uso la versione 5.10.2, che era obsoleta e segnalava vulnerabilità di sicurezza
  _AC-12825 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_
* __[2.4.8-beta1] Migrazione di TinyMCE 5 a TinyMCE 7 - Magento2-infra - parole vietate__
La migrazione da TinyMCE 5 a TinyMCE 7.3.0 è stata supportata per Adobe Commerce; in precedenza era in uso la versione 5.10.2, che era obsoleta e segnalava vulnerabilità di sicurezza
  _AC-12844 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/edcd0dcc>)_
* __Aggiornamento Require.js alla versione più recente 2.3.7 (vulnerabilità di sicurezza CVE-2024-38999)__
Il file require.js è stato aggiornato alla versione più recente 2.3.7. Nella versione precedente segnalava una vulnerabilità di sicurezza
  _AC-12901 - [Contributo codice GitHub](<https://github.com/magento/magento2/commit/b34c0a75>)_

## Problemi risolti nella versione v2.4.8

Sono stati risolti 497 problemi nel codice core di Magento Open Source 2.4.8. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

* L&#39;API REST di __/V1/transaction restituisce un errore quando parent_txn_id = txn_id__
Il sistema ora gestisce correttamente le transazioni dei concetti padre e figlio in cui l&#39;ID della transazione padre è uguale all&#39;ID della transazione, impedendo un ciclo infinito durante la query dell&#39;endpoint REST API /V1/transaction. In precedenza, questo scenario generava un errore irreversibile dovuto al superamento del tempo massimo di esecuzione.
  _AC-10042 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_
* __[Problema di tipo Graphql] in 2.4.7__
Il sistema ora gestisce correttamente i valori interi nella funzione GetCustomSelectedOptionAttributes durante l&#39;esecuzione di una query GraphQL, evitando errori relativi al tipo. In precedenza, l&#39;avvio di una query GraphQL che utilizzava GetCustomSelectedOptionAttributes con un argomento Integer generava un errore di tipo.
  _AC-11878 - [Problema GitHub](https://github.com/magento/magento2/issues/38662) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38663)_
* __Caratteri speciali nella categoria url_key (se creata tramite API REST)__
Precedente In category_url_key il carattere speciale non è presente dopo la correzione in cui viene visualizzato in category_url_key
  _AC-3223 - [Problema GitHub](https://github.com/magento/magento2/issues/35577) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c699c206)_
* __Problema con l&#39;API rest dopo l&#39;abilitazione di 2FA Duo__
L’opzione di sicurezza 2FA con Duo genera ora la firma corretta per l’API Rest
  _ACP2E-2755 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/412fa642)_
* __[REST API]: l&#39;utilizzo del valore predefinito nella visualizzazione archivio non rimane controllato dopo l&#39;aggiunta di configurazioni per un prodotto configurabile__
Il problema è stato risolto garantendo le voci di database corrette per le opzioni personalizzabili per un archivio non predefinito. La casella di controllo per l’archivio personalizzato nella sezione &quot;admin > Catalog > Product Edit > Customizable Options&quot; (Amministrazione > Catalogo > Modifica prodotto > Opzioni personalizzabili) era stata precedentemente deselezionata a causa di voci di database non accurate, anche se il titolo dell’opzione per l’archivio personalizzato rimaneva lo stesso dell’archivio predefinito.
  _ACP2E-2927 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_
* __API REST: impossibile effettuare richieste con barra (/) nello SKU quando si utilizza Oauth1__
Prima della correzione, non era possibile effettuare una chiamata API per un prodotto con &quot;/&quot; nello SKU. Ora è possibile inviare una richiesta API per ottenere i dettagli del prodotto, anche se lo SKU contiene una barra.
  _ACP2E-2969 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_
* __Impossibile aggiornare l&#39;indirizzo del cliente durante l&#39;aggiornamento tramite API REST se &quot;validateDefaultAddress&quot; abilitato__
L’endpoint API ora funziona come previsto dopo che il problema con la chiave ID mancante nel payload API è stato risolto.
  _ACP2E-3079 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_
* __[Cloud] Creazione del gruppo di clienti prezzi gruppo sito Web duplicato nell&#39;API prezzi livello.__
Ora l’API Rest prezzo di livello non consente di creare il gruppo di clienti prezzo di gruppo del sito web duplicato.
In precedenza era possibile creare il gruppo di clienti prezzo gruppo sito web duplicato nell’API prezzi livello che non avrebbe superato la convalida in Amministratore durante il salvataggio del prodotto.
  _ACP2E-3091 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_
* __Impossibile aggiungere il commento dell&#39;ordine con stato tramite API REST__
Il problema è stato risolto consentendo la modifica dello stato dell’ordine se proviene solo dallo stato corrente. In precedenza, non rispettava lo stato dell’ordine e impediva modifiche in qualsiasi stato dell’ordine, anche se proveniva dallo stesso stato.
  _ACP2E-3130 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_
* __L&#39;operazione asincrona ha esito negativo quando lo SKU non è presente nel payload__
Operazioni asincrone e di sincronizzazione non riuscite in precedenza a causa di errori di salvataggio del prodotto se lo SKU manca nel payload. Dopo la correzione, le operazioni dell’API rest di salvataggio del prodotto asincrono e sincrono non riescono e viene visualizzato il messaggio di eccezione pertinente.
  _ACP2E-3236 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_
* __[CLOUD] Impossibile aggiornare i prezzi base utilizzando l&#39;API REST (il valore di &#39;value_id&#39; in &#39;catalog_product_entity_decimal&#39; non viene incrementato correttamente).__
In precedenza a questa correzione, quando veniva chiamato rest api /rest/default/V1/products/base-price, l’ID incremento veniva aumentato erroneamente, lasciando un gap tra i valori. Dopo la correzione l’ID incremento viene aumentato come previsto, in modo incrementale. Anche l’intervallo del campo value_id è stato aumentato.
  _ACP2E-3376 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Gli elementi dell&#39;ordine non sono visibili nelle e-mail delle note di accredito per l&#39;API POST V1/order/:orderId/return__
In precedenza, prima di questa correzione, quando un cliente crea una nota di credito da una richiesta API di notifica send_email, non contiene la griglia dei dettagli del prodotto. Dopo questa correzione, il cliente invia una richiesta API per la nota di credito e troverà i dettagli dell’elemento del prodotto che compaiono nell’e-mail.
  _ACP2E-3460 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_
* __I valori predefiniti non sono impostati per gli attributi di data e ora con i prodotti RestAPI__
I valori predefiniti ora vengono impostati correttamente per gli attributi di data e data e ora tramite RestAPI
  _ACP2E-3486 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### API, carrello e pagamento

* __Errore critico 500: Magento\Framework\Webapi\Exception relativo all&#39;intestazione HTTP Accept__
Dopo la correzione, non si verifica alcun problema quando si specifica l’intestazione &quot;Accept&quot; (Accetta).
  _ACP2E-3343 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### Account

* __Il modulo Indirizzo cliente consente l&#39;utilizzo di codice casuale nei campi Nome__
Il sistema ora convalida l’input nei campi Nome e Cognome nel modulo dell’indirizzo del cliente, impedendo l’utilizzo di codice casuale. In precedenza, il sistema consentiva l’utilizzo di codice casuale in questi campi senza generare un errore.
  _AC-10782 - [Problema GitHub](https://github.com/magento/magento2/issues/38331) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38345)_
* __aggiornamento password amministratore.__
  _AC-10886 - [Problema GitHub](https://github.com/magento/magento2/issues/38352) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4bca5dfe)_
* __arresto anomalo del mio account durante il salvataggio__
Il sistema ora salva correttamente gli indirizzi dei clienti anche quando il campo dell&#39;area non viene visualizzato, evitando un arresto anomalo durante il processo di salvataggio. In precedenza, se si tentava di aggiungere o modificare un indirizzo senza un campo area visualizzato, si verificava un errore di eccezione.
  _AC-10990 - [Problema GitHub](https://github.com/magento/magento2/issues/38406) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38407)_
* __Ciclo di reindirizzamento se l&#39;URL è in lettere maiuscole__
Il sistema ora converte automaticamente i caratteri maiuscoli negli URL in minuscoli, impedendo un ciclo di reindirizzamento durante l’accesso alla pagina home. In precedenza, l’utilizzo di caratteri maiuscoli nell’URL della base sicura causava un ciclo di reindirizzamento continuo quando si tentava di accedere alla home page.
  _AC-11718 - [Problema GitHub](https://github.com/magento/magento2/issues/38538) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38539)_
* __middlename(s) non salvato(i) per gli account guest__
Il sistema ora salva correttamente il secondo nome per gli account guest durante il pagamento, rendendolo accessibile nel modello e-mail. In precedenza, il secondo nome non veniva salvato nella tabella dei preventivi e non era accessibile nel modello di e-mail per gli account guest.
  _AC-11755 - [Problema GitHub](https://github.com/magento/magento2/issues/38593) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39067)_
* __Amministratore: pulsanti Azioni pagina mobili a sinistra anziché a destra__
Il sistema ora allinea correttamente i pulsanti Azioni pagina al lato destro dell’intestazione fissa nel pannello di amministrazione, migliorando l’aspetto professionale. In precedenza, questi pulsanti si spostavano erroneamente sul lato sinistro dell’intestazione fissa.
  _AC-11919 - [Problema GitHub](https://github.com/magento/magento2/issues/38701) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_
* Errore __`dev:di:info`in magento 2.4.7__
Il sistema ora visualizza correttamente i parametri del costruttore durante l&#39;esecuzione del comando `dev:di:info`, evitando il verificarsi di errori. In precedenza, l’esecuzione di questo comando generava un errore a causa di una mancata corrispondenza del tipo nell’argomento.
  _AC-11999 - [Problema GitHub](https://github.com/magento/magento2/issues/38740) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Casella di controllo per l&#39;accesso come consenso del cliente non traducibile__
Il sistema ora consente di impostare i campi &quot;Login as Customer opt-in checkbox&quot; e &quot;Login as Customer checkbox tooltip&quot; nell&#39;ambito &quot;Visualizzazione store&quot;, consentendo la traduzione per diverse visualizzazioni dello store. In precedenza, questi campi venivano impostati solo nell’ambito &quot;Sito web&quot;, impedendo le traduzioni per le singole visualizzazioni dello store.
  _AC-13000 - [Problema GitHub](https://github.com/magento/magento2/issues/32329) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32359)_
* __Il cliente ha eseguito l&#39;accesso ma ha visualizzato l&#39;errore 404 in front-end.__
La pagina della dashboard del cliente storefront ora viene caricata come previsto quando un cliente effettua l’accesso. In precedenza, i clienti potevano accedere, ma questa pagina mostrava un errore 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
  _AC-6071 - [Problema GitHub](https://github.com/magento/magento2/issues/35838) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36263)_
* __Impossibile salvare le informazioni sugli attributi del cliente nella sezione del cliente Admin Edit;__
L’ID store del cliente ora è implementato correttamente per ambito del sito web per il modulo di modifica cliente amministratore.
  _ACP2E-2791 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/488c1034)_
* __Dopo l&#39;accesso, i prodotti aggiunti all&#39;elenco di confronto come utenti guest non sono visibili.__
I prodotti aggiunti all’elenco di confronto dei prodotti prima di effettuare l’accesso come cliente ora vengono mantenuti dopo l’accesso.
In precedenza, dopo l’accesso, i prodotti aggiunti all’elenco di confronto come utenti guest non erano visibili.
  _ACP2E-3329 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __La configurazione di Consenti paesi causa problemi nelle configurazioni degli indirizzi del cliente__
La selezione della configurazione Consenti paesi non influisce sui paesi mostrati per al di fuori dell’ambito specificato. Consenti in precedenza la configurazione di Paesi influenzata dall’attributo dell’indirizzo del cliente al di fuori dell’ambito specificato
  _ACP2E-3433 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __VAPT: errore della logica di business - data futura come data di nascita del cliente__
La data di nascita del cliente non può essere posticipata a oggi
  _ACP2E-3501 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Account, API, GraphQL

* __API Cliente - Il Numero Di Errori Di Accesso Non È Riuscito A Ripristinare 0 Dopo Il Corretto Accesso__
Ora il numero di errore viene reimpostato su zero nella tabella delle entità cliente dopo l’accesso del cliente tramite gli endpoint API.
  _ACP2E-3246 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Account, interfaccia utente amministratore, B2B

* __Gli utenti amministratori con restrizioni non possono sempre visualizzare i cataloghi condivisi personalizzati__
Gli utenti amministratori con restrizioni possono ora visualizzare e gestire in modo coerente i clienti e tutti i cataloghi condivisi a cui i prodotti sono assegnati, a condizione che abbiano accesso allo store specifico. In precedenza, un utente amministratore con accesso limitato a un particolare archivio non poteva sempre visualizzare tutti i cataloghi condivisi a cui erano assegnati i prodotti oppure poteva vedere clienti che non potevano salvare, con conseguenti incongruenze nel sistema.
  _ACP2E-3038 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_

### Account, carrello e pagamento

* L&#39;attributo dell&#39;indirizzo cliente personalizzato __&quot;select&quot; non viene riprodotto per il nuovo indirizzo cliente__
  _AC-2341 - [Problema GitHub](https://github.com/magento/magento2/issues/34950)_

### Interfaccia utente amministratore

* __[Problema]: pulsante &quot;Ricarica dati&quot; per il controllo delle autorizzazioni di aggiunta__
Il sistema ora include un controllo delle autorizzazioni per il pulsante &quot;Ricarica dati&quot;, che garantisce che venga visualizzato e accessibile solo agli utenti con le autorizzazioni appropriate. In precedenza, il pulsante &quot;Ricarica dati&quot; era visibile e cliccabile per tutti gli utenti, portando a una pagina &quot;non consentita&quot; quando gli utenti facevano clic senza le autorizzazioni necessarie.
  _AC-10705 - [Problema GitHub](https://github.com/magento/magento2/issues/38283) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38279)_
* __[Problema] Etichette non coerenti per gli attributi nelle regole di marketing__
Il sistema ora compila correttamente le etichette in modo coerente per le opzioni di categoria e attributo nella regola prezzo carrello
  _AC-11427 - [Problema GitHub](https://github.com/magento/magento2/issues/31232) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31231)_
* __Convalida dei dati completata. Pulsante Importa presente durante l&#39;importazione di prodotti con comportamento Sostituisci__
Il sistema ora convalida correttamente i dati e nasconde il pulsante &quot;Importa&quot; durante il processo di importazione del prodotto con il comportamento &quot;Sostituisci&quot;, impedendo qualsiasi sostituzione involontaria dei dati. In precedenza, il sistema convalidava i dati in modo errato e visualizzava il pulsante &quot;Importa&quot;, causando potenziali incongruenze nei dati.
  _AC-11588 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_
* __[Bug] Magento 2.4.7 non consente foto di prodotto con estensione maiuscola.__
Il sistema ora accetta caricamenti di immagini di prodotto con estensioni di file in formato maiuscolo, garantendo un processo di creazione del prodotto fluido. In precedenza, i caricamenti di immagini con estensioni di file in maiuscolo venivano rifiutati, costringendo gli utenti a cambiare l’estensione del file in minuscolo.
  _AC-12167 - [Problema GitHub](https://github.com/magento/magento2/issues/38831) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_
* __Elenco a discesa nascosto nelle griglie con azione di selezione (ad esempio Contenuto > Elementi > Pagine)__
Ora il sistema è stato corretto tutti i menu a discesa simili per tutte le griglie.
  _AC-12319 - [Problema GitHub](https://github.com/magento/magento2/issues/38891) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39371)_
* __[Problema] Correzione Avviso: chiave di matrice &quot;filters&quot;__ non definita
Il sistema ora gestisce gli scenari in cui un nuovo utente non ha ancora interagito con i segnalibri, impedendo la registrazione di un avviso di &quot;filtri&quot; della chiave di array non definita. In precedenza, questo avviso veniva registrato quando un nuovo utente non aveva interagito con i segnalibri.
  _AC-13131 - [Problema GitHub](https://github.com/magento/magento2/issues/39013) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38996)_
* __Il file CSV di importazione prodotti con caratteri speciali non riesce a causa di modifiche al codice nel file Validate.php__
Il sistema ora convalida e importa correttamente i file CSV dei prodotti contenenti caratteri speciali, consentendo il corretto trasferimento dei dati. In precedenza, se si tentava di importare un file CSV di un prodotto con caratteri speciali, si verificava un errore che impediva il processo di importazione.
  _AC-13529 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __Nessun asterisco rosso per il campo del numero di telefono obbligatorio__
In precedenza l&#39;asterisco rosso non veniva visualizzato per il numero di telefono, ma  numero di telefono obbligatorio. Che è ora un asterisco rosso fisso può essere visto sul numero di telefono come un campo obbligatorio.
  _AC-13850 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c699c206)_
* __[Problema] Imposta la modalità di indicizzazione predefinita su &#39;pianificazione&#39;__
Per impostazione predefinita, tutti i nuovi indicizzatori sono in modalità **[!UICONTROL Update by Schedule]**.  In precedenza, la modalità predefinita era **[!UICONTROL Update on Save]**. Gli indicizzatori esistenti non vengono interessati. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
  _AC-6975 - [Problema GitHub](https://github.com/magento/magento2/issues/36419) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0b410856)_
* __[Problema] Elimina le tabelle del registro modifiche dell&#39;indicizzatore in caso di annullamento dell&#39;abbonamento a mview__
Il sistema ora rimuove automaticamente le tabelle del registro delle modifiche inutilizzate quando un indice viene cambiato da &quot;aggiorna secondo pianificazione&quot; a &quot;aggiorna al salvataggio&quot;, contrassegnando l&#39;indice come non valido per assicurarsi che non vengano saltate voci. In precedenza, il passaggio di un indice a &quot;aggiorna al salvataggio&quot; lasciava le tabelle del registro modifiche inutilizzate nel sistema e contrassegnava tutti gli indici modificati come &quot;validi&quot;.
  _AC-7700 - [Problema GitHub](https://github.com/magento/magento2/issues/29789) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/25859)_
* __Nessun collegamento per la spedizione durante i pagamenti nell&#39;estrazione nella visualizzazione per telefono cellulare__
Il sistema ora assicura che i titoli/collegamenti di pagamento &quot;Shipping&quot; e &quot;Review &amp; Payments&quot; siano sempre visibili nella parte superiore della pagina nella vista mobile, consentendo agli utenti di spostarsi facilmente tra i vari passaggi e apportare le correzioni necessarie. In precedenza, questi titoli/collegamenti erano nascosti nella visualizzazione per dispositivi mobili, rendendo difficile per gli utenti conoscere il passaggio corrente o tornare ai passaggi precedenti.
  _AC-7962 - [Problema GitHub](https://github.com/magento/magento2/issues/36856) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36982)_
* __i commenti di spedizione per query ordini cliente created_at vengono restituiti in un fuso orario +0 non incluso nel fuso orario configurato__
Il sistema ora visualizza correttamente il campo &quot;created_at&quot; dai commenti sulla spedizione nel fuso orario configurato del cliente quando si utilizza la query Ordini cliente. In precedenza, il campo &quot;created_at&quot; veniva visualizzato nel fuso orario +0, indipendentemente dal fuso orario configurato del cliente.
  _AC-8109 - [Problema GitHub](https://github.com/magento/magento2/issues/36947) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37642)_
* __i18n:collect-phrase interrompe l&#39;integrità delle traduzioni__
Il comando `bin/magento i18n:collect-phrases -o` ora raccoglie e aggiunge correttamente nuove frasi dai file JavaScript e .phtml, garantendo che le traduzioni vengano riflesse correttamente nel file di traduzione. In precedenza, il sistema non era in grado di includere frasi di traduzione multilinea da file JavaScript e frasi da file .phtml nel file di traduzione, il che portava a traduzioni incomplete o errate.
  _AC-9843 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Il nome dell&#39;apostrofo nella visualizzazione archivio è stato sostituito da &amp;#039;__
I filtri di visualizzazione archivio della griglia ora visualizzano correttamente gli apostrofi
  _ACP2E-2787 - [Problema GitHub](https://github.com/magento/magento2/issues/38395) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __Il caricamento dei favicon non riesce a convalidare i file .ico__
L’errore di convalida del file è stato aggiornato a &quot;Convalida del file non riuscita. Verifica le impostazioni di elaborazione delle immagini nella configurazione dell&#39;archivio.&quot; In precedenza, si trattava semplicemente di &quot;Convalida file non riuscita&quot;.
  _ACP2E-2847 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __Nella raccolta di PageBuilder viene visualizzata la miniatura dell&#39;immagine precedente invece dell&#39;immagine appena caricata__
Rigenera le anteprime delle immagini per le immagini eliminate e ricaricate con lo stesso nome tramite la raccolta multimediale nel contenuto del Page Builder.
  _ACP2E-2957 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188)_
* __Il salvataggio di un prodotto da parte di un utente amministratore con un ambito di ruolo diverso sovrascrive/elimina le informazioni di prodotto correlate esistenti nel prodotto__
In precedenza, prima della correzione, i prodotti correlati venivano reimpostati e diventavano vuoti quando l’utente amministratore secondario faceva clic sul pulsante Salva senza modificare il prodotto correlato. Dopo questa correzione, l’utente amministratore secondario fa clic sul pulsante Salva e il prodotto non viene reimpostato e salvato correttamente.
  _ACP2E-2978 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_
* __Impossibile esportare più di 200 ordini__
I limiti del server per la dimensione della richiesta degli ID selezionati inviati in precedenza sono stati trascurati modificando la richiesta HTTP da GET a POST per risolvere il problema. In precedenza, a causa delle limitazioni del server per la dimensione della richiesta GET, si verificava il problema.
  _ACP2E-3033 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_
* __Messaggio di convalida pagina di estrazione non corretto.__
Se un campo obbligatorio viene lasciato vuoto, ad esempio &quot;address&quot;, la convalida lato server non visualizza il messaggio. La convalida lato client garantirà la visualizzazione della notifica di errore del campo obbligatorio, indicando &quot;Questo campo è obbligatorio&quot;. In precedenza, se un campo obbligatorio veniva lasciato vuoto, veniva visualizzato il messaggio &quot;address is required&quot; (indirizzo richiesto), in aggiunta al messaggio di convalida lato client.
  _ACP2E-3037 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_
* __Problema del modello di reimpostazione della password con l&#39;utente amministratore__
Il problema è stato risolto utilizzando la chiave corretta, che ora include il nome utente amministratore nel modello e-mail e completa correttamente l’oggetto. In precedenza, il problema derivava da una chiave obsoleta in uso.
  _ACP2E-3125 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_
* __Barre doppie nell&#39;URL del segmento cliente__
Le barre doppie non vengono visualizzate nell’URL quando si fa clic su &quot;Reimposta filtro&quot; nella griglia.
  _ACP2E-3149 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_
* __COD non è disponibile per paesi specifici consentiti__
Ora Cash on delivery è disponibile per i paesi specifici consentiti ogni volta che è richiesto e   AC-3216 funziona come previsto.
  _ACP2E-3171 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_
* __Impossibile aggiornare lo stato dell&#39;ordine personalizzato creato__
&quot;Ora è possibile aggiornare gli stati degli ordini creati su misura, mentre in precedenza era possibile modificare lo stato solo se lo stato corrente era &quot;elaborazione&quot; o &quot;frode&quot;.&quot;
  _ACP2E-3178 - [Problema GitHub](https://github.com/magento/magento2/issues/38659) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_
* __Lo stato dell&#39;indirizzo di spedizione non è aggiornato automaticamente__
Prima della correzione, l’area dell’indirizzo di spedizione (o l’ID di regione) non era sincronizzata con le informazioni di fatturazione dell’indirizzo. Ora, sia l&#39;area dell&#39;indirizzo di spedizione che l&#39;ID di regione vengono aggiornati correttamente quando vengono modificate le informazioni sull&#39;indirizzo di fatturazione.
  _ACP2E-3294 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __Il pulsante Reimposta non funziona su Aggiungi/Modifica utente amministratore__
In precedenza, il pulsante Reimposta non funzionava nella pagina Aggiungi/Modifica utente amministratore. Ora, nel pannello Amministratore in Sistema -> Autorizzazioni -> Tutti gli utenti, il pulsante Reimposta funziona correttamente nella pagina Aggiungi/Modifica utente amministratore.
  _ACP2E-3364 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __Rilevamento errato e errori CORS durante il routing degli URL dell&#39;amministratore Magento__
Dopo la correzione, se il dominio amministratore personalizzato è un sottodominio del dominio principale, l’amministratore è accessibile solo dal sottodominio configurato.
  _ACP2E-3373 - [Problema GitHub](https://github.com/magento/magento2/issues/37663) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_
* __Convalida interrotta per &#39;Quantità massima consentita nel carrello&#39;__
In precedenza, quando `Maximum Qty Allowed in Shopping Cart` veniva inserito vuoto, non veniva generata alcuna eccezione, anche se qui non veniva accettato un valore vuoto. In seguito all’applicazione di questa correzione, se si inserisce una stringa vuota verranno generate delle eccezioni e non sarà possibile salvare il prodotto.
  _ACP2E-3392 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Problema nell&#39;interfaccia utente di Anteprima Pagebuilder] I pulsanti nella colonna Page Builder non sono allineati correttamente__
I pulsanti nelle colonne di Page Builder ora sono allineati correttamente. In precedenza, non erano allineati nelle colonne di Page Builder.
  _ACP2E-3408 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_
* __Esportazione del report Prodotti ordinati non eseguita. Errore 404.__
L&#39;esportazione del rapporto Prodotti ordinati in formato CSV e XML ora funziona come previsto
  _ACP2E-3431 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_
* __Errore TinyMCE JS nella console dopo l&#39;abilitazione della minimizzazione Js con modalità di produzione__
In precedenza, l’abilitazione della minimizzazione di JavaScript in modalità di produzione all’interno del pannello di amministrazione causava la visualizzazione degli errori JavaScript relativi a TinyMCE 6 nella console del browser, influendo sulla funzionalità e sull’esperienza utente. Ora, questo problema è stato risolto, garantendo che TinyMCE 6 funzioni senza errori, anche quando la minimizzazione JS è abilitata.
  _ACP2E-3457 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/56463d5e)_
* __Richiesta di ulteriori modifiche per completare completamente la correzione ACP2E-3375__
&quot;-
  _ACP2E-3459 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Abilitazione automatica delle nuove autorizzazioni ACL__
Le nuove autorizzazioni aggiunte ai moduli personalizzati non concederanno più automaticamente l’accesso a tutti i ruoli utente esistenti, a meno che non siano configurate in modo esplicito.
  _ACP2E-3503 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_
* __Il report utente del log delle azioni amministratore non mostra i dettagli per adminhtml_user_delete__
Il file adminhtml_user_delete registra correttamente i dettagli importanti. In precedenza, i registri non venivano generati per le eliminazioni degli utenti.
  _ACP2E-3509 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4de008a9)_
* __Regola carrello con condizione di spedizione non applicabile quando si effettua l&#39;ordine dall&#39;amministratore__
In precedenza, se la regola del prezzo del carrello aveva uno sconto sul metodo di spedizione associato al coupon, non poteva essere applicata tramite l’interfaccia utente di amministrazione. Dopo l’applicazione di questa correzione, lo sconto della regola di prezzo del carrello con un coupon per un metodo di spedizione specifico verrà applicato correttamente dall’interfaccia utente di amministrazione.
  _ACP2E-3536 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/11ce816b)_
* Il codice HEX __[FRESH] non viene aggiornato correttamente nel campione__
Il codice HEX immesso manualmente dall’utente nel selettore colore Campione visivo non viene più modificato dal sistema. In precedenza, alcuni codici HEX subivano lievi regolazioni a causa di errori di conversione tra i modelli di colore.
  _ACP2E-3559 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1ef984c0)_

### Interfaccia utente amministratore, B2B

* __L&#39;account di accesso B2B come intestazione del cliente ha ancora il marchio Magento__
In precedenza, l’intestazione della vetrina mostra &quot;Ora sei connesso come &lt;nome cliente> a &lt;nome negozio>&quot; con il branding Magento. Che è ora fisso e l’intestazione viene visualizzata con il branding ADOBE.
  _AC-13628 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Interfaccia utente amministratore, metodi di pagamento/pagamento, ordine

* __Autorizzazione transazione non visualizzata nella scheda Transazione dopo l&#39;ordine dei pulsanti avanzati PayPal__
Il sistema ora visualizza correttamente l&#39;autorizzazione della transazione nella scheda Transazione dopo aver effettuato un ordine utilizzando lo Smart Button PayPal. In precedenza, la transazione di autorizzazione non veniva visualizzata nella scheda Transazione dopo aver fatto clic sul pulsante &quot;Autorizza&quot; e non veniva creata alcuna nuova transazione di tipo &quot;Autorizzazione&quot;.
  _AC-13520 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Interfaccia utente amministratore, Prestazioni

* __Dopo l&#39;aggiornamento a 2.4.5-p8 si verificano errori 500 durante la creazione dell&#39;ordine dall&#39;amministratore__
In precedenza, quando si abilitava la minimizzazione di HTML, non era possibile effettuare un ordine dall’amministratore. Ora, con la minimizzazione di HTML abilitata, l’ordine dall’amministratore può essere effettuato correttamente.
  _ACP2E-3169 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Interfaccia utente amministratore, Spedizione

* __Il conteggio dei codici coupon non viene aggiornato nel   &quot;Tempo utilizzato&quot; nella scheda Gestisci codici coupon se un ordine viene effettuato con la spedizione multipla.__
In precedenza, quando un ordine veniva effettuato con la spedizione multipla, il conteggio del codice coupon non veniva aggiornato nella colonna &quot;Tempo utilizzato&quot; della scheda Gestisci codici coupon. Ora, il conteggio corretto viene visualizzato in entrambi i &quot;Tempo utilizzato&quot; che riflettono i valori desiderati con la spedizione multipla.
  _ACP2E-2519 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4745100c)_

### Interfaccia utente amministratore, staging e anteprima

* __[Cloud] La rimozione del modello con immagini mancanti determina l&#39;eliminazione di pub/supporti__
Precedentemente a questa correzione, se per un modello di pagebuilder mancava il nome dell’immagine di anteprima, la cartella pub/media veniva eliminata. Dopo la correzione, verranno eliminati solo il modello e l’immagine di anteprima, se trovata.
  _ACP2E-3424 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/Generazione rapporti

* __Errore Google Analytics CSP https://region1.analytics.google.com__
Il sistema ora consente correttamente le connessioni a &quot;https://region1.analytics.google.com&#39; quando Google Analytics è abilitato, evitando errori Content Security Policy (CSP). In precedenza, l’abilitazione di Google Analytics e la visualizzazione del sito web dall’UE generavano errori nella console CSP a causa del rifiuto di connettersi a &quot;https://region1.analytics.google.com&#39;&quot;.
  _AC-9922 - [Problema GitHub](https://github.com/magento/magento2/issues/37750) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38991)_
* __Il report Avanzamento non funziona__
Il sistema ora supporta la generazione di file di dati di reporting avanzato per set di dati di dimensioni eccessive caricando e scrivendo rapporti in batch di 10.000. In precedenza, il modulo di reporting avanzato non era in grado di generare file di dati per set di dati di dimensioni eccessive, causando errori di tipo &quot;MySQL Server has gone away&quot; durante l’esecuzione del processo analytics_collect_data cron.
  _ACP2E-2570 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_
* __Problema di visibilità dell&#39;intervallo di date del rapporto Prodotti ordinati dall&#39;amministratore.__
L’utente potrà selezionare una data qualsiasi dal rapporto prodotti ordinati. In precedenza, dopo l’aggiornamento di una tabella, selezionando la data &quot;DA&quot; si reimpostava la data &quot;A&quot;.
  _ACP2E-3080 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_
* __Intestazioni curl non corrette che impediscono il funzionamento di `newrelic:create:deploy-marker`__
Il sistema ora formatta correttamente le intestazioni curl, consentendo al comando `newrelic:create:deploy-marker` di creare correttamente un marcatore di distribuzione in New Relic. In precedenza, intestazioni curl errate impedivano la creazione di un marcatore di distribuzione in New Relic.
  _ACP2E-3096 - [Problema GitHub](https://github.com/magento/magento2/issues/37641) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* __Lo script inlineJS per il monitoraggio del browser NewRelic causa errori CSP__
Gli script di monitoraggio di NewRelic Browser ora vengono inseriti dall’applicazione al posto dell’agente APM per la conformità con CSP (Content Security Policy, criteri per la sicurezza dei contenuti). In precedenza, gli script di monitoraggio del browser NewRelic inseriti dall’agente APM non erano conformi a CSP e causavano la mancata esecuzione degli script.
  _ACP2E-3183 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_
* __Le query INSERT nella tabella sales_bestsellers_aggregated_daily diventano lente in un progetto con un volume di ordini di vendita elevato__
In precedenza, la generazione del rapporto giornaliero aggregato dei bestseller richiedeva molto tempo per un grande volume di ordini effettuati. Ora il rapporto viene generato in modo tempestivo.
  _ACP2E-3189 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_
* __Report ordini con simbolo di valuta errato__
Il simbolo di valuta per gli importi degli ordini nel rapporto Ordine è stato erroneamente ricavato da valuta/opzioni/base. Ora è stato corretto per utilizzare valuta/opzioni/valore predefinito per una generazione rapporti accurata.
  _ACP2E-3276 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Calcoli non corretti nel report sull&#39;utilizzo del coupon__
Il totale delle vendite nella griglia del rapporto coupon viene ora calcolato in modo accurato incorporando sia &quot;Importo compensazione imposta sconto&quot; che &quot;Importo compensazione imposta sconto spedizione&quot;. In precedenza, tali importi mancavano dal calcolo, causando discrepanze tra il totale delle vendite e i dati degli ordini di vendita.
  _ACP2E-3302 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_
* __Problemi con &quot;&lt;project_id>/var/tmp&quot; condiviso__
I file temporanei Analytics DataExport utilizzeranno la directory sys tmp, più adatta per l’accesso frequente e le modifiche. Per evitare conflitti nel caso in cui più istanze siano in esecuzione sullo stesso server, il percorso tmp è stato aggiornato per utilizzare l’ID univoco di un’istanza
  _ACP2E-3339 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/Reporting, B2B

* __B2B - la mappa del sito include prodotti/categorie non assegnati al catalogo condiviso__
Limita le categorie e i prodotti generati da sitemap alle categorie e ai prodotti assegnati solo al catalogo condiviso pubblico e/o all’impostazione delle autorizzazioni per la categoria del catalogo.
  _ACP2E-2300 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics / Reporting, cloud

* __Magento elimina la maggior parte delle transazioni New Relic cron #34108__
AC sta segnalando correttamente le transazioni relative al processo cron a NewRelic. In precedenza, alcune transazioni relative a lavori cron venivano indicate come &quot;OtherTransaction/Action/unknown&quot; in NR
  _ACP2E-3067 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_
* __La metrica in NR potrebbe essere fuorviante per le transazioni in background- Seguito di ACP2E-3067__
Le transazioni in background (cron) utilizzeranno il nome dell’app New Relic definito nelle impostazioni di configurazione
  _ACP2E-3187 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

* __I prodotti assegnati al catalogo condiviso non si riflettono sul front-end quando viene eseguito l&#39;indice parziale__
I prodotti assegnati al catalogo condiviso tramite API REST ora sono immediatamente visibili sulla vetrina dopo il completamento dell’indicizzazione parziale. In precedenza, i prodotti erano visibili solo dopo una reindicizzazione completa.
  _ACP2E-2139 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_
* __Bordi non necessari nella sezione Ordini personali__
In precedenza veniva creato un contenitore aggiuntivo (riferimenti ordine) che applicava classi CSS aggiuntive, causando la visualizzazione di linee di bordo non necessarie sotto il numero ordine all’interno della sezione Ordini personali, che ora non è visibile.
  _ACP2E-3044 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_
* __sales_clean_quotes cron elimina i preventivi dagli ordini di acquisto ancora approvati__
I preventivi utilizzati ora negli ordini fornitore non verranno eliminati dal processo cron sales_clean_quotes
  _ACP2E-3247 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

### B2B, Framework

* __Il Filtro Della Griglia Aziendale E Il Tentativo Di Esportazione CSV Della Griglia Non Riusciranno E Genereranno Un&#39;Eccezione__
Il sistema ora consente l’esportazione CSV dei dati della griglia Aziende nel pannello di amministrazione, anche quando vengono applicati filtri come &quot;Saldo in sospeso&quot; e &quot;Tipo di azienda&quot;. In precedenza, l’applicazione di determinati filtri e il tentativo di esportare i dati della griglia generavano un errore e un’eccezione.
  _AC-9607 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

### Bundle

* __Il conteggio dei messaggi di errore di convalida del bundle Storefront supera 1__
Il sistema visualizza ora un solo messaggio di errore di convalida quando si fa clic sul pulsante &quot;Aggiungi al carrello&quot; senza selezionare alcuna opzione di casella di controllo per un prodotto incluso. In precedenza, il sistema visualizzava più messaggi di errore di convalida per ogni casella di controllo non selezionata.
  _AC-10826 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_

### Carrello e pagamento

* __L&#39;eccezione non viene gestita correttamente durante l&#39;aggiunta di un prodotto al carrello nella pagina confronto prodotti__
Il sistema ora gestisce correttamente le eccezioni quando si aggiunge un prodotto al carrello dalla pagina di confronto dei prodotti, visualizzando un messaggio di gestione dei messaggi nel controller. In precedenza, un’eccezione generava la restituzione di una pagina con codifica JSON invece di essere rilevata e gestita correttamente.
  _AC-10660 - [Problema GitHub](https://github.com/magento/magento2/issues/38200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38257) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __GTag non invia i prezzi e i totali delle transazioni.__
Il sistema ora invia correttamente i prezzi delle transazioni e i totali a Google Tag quando viene abilitato GTag, garantendo un tracciamento accurato dei dati di e-commerce. In precedenza, la valuta veniva erroneamente inviata come parte degli ordini &quot;all&quot;, piuttosto che essere associata al singolo ordine.
  _AC-10698 - [Problema GitHub](https://github.com/magento/magento2/issues/37348) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37504) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37349)_
* __[Problema] [Estrazione] Direttive dipendenti aggiornate nel modello e-mail di pagamento non riuscito__
Il sistema ora omette correttamente l&#39;indirizzo di spedizione e il metodo di spedizione dal modello e-mail di pagamento non riuscito per i prodotti virtuali, assicurandosi che nell&#39;e-mail vengano incluse solo le informazioni pertinenti. In precedenza, l’e-mail di pagamento non riuscito per i prodotti virtuali includeva erroneamente l’indirizzo di spedizione e il metodo di spedizione.
  _AC-11641 - [Problema GitHub](https://github.com/magento/magento2/issues/32781) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32511)_
* __Accesso a Magento 2 durante l&#39;estrazione con il cliente esistente: errore di invio della console nel browser Firefox__
Il sistema ora consente agli utenti di accedere durante il processo di pagamento senza incontrare errori della console nel browser Firefox. In precedenza, se si tentava di accedere come cliente esistente durante il check-out, si verificava un errore della console in Firefox.
  _AC-11717 - [Problema GitHub](https://github.com/magento/magento2/issues/38557) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39509)_
* __[Problema] Regressione delle regole di vendita in 2.4.7__
Il sistema ora convalida correttamente le regole di vendita, impedendo l’applicazione di un codice coupon a un carrello quando la condizione del prodotto non corrisponde a nessun nome di prodotto. In precedenza, era possibile applicare una regola di vendita e applicare uno sconto sull’importo della spedizione anche quando la condizione del prodotto non corrispondeva a nessun nome di prodotto.
  _AC-11876 - [Problema GitHub](https://github.com/magento/magento2/issues/38671) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_
* __[Problema] Calcolo CartFixed della regola di vendita: importo sconto non corretto__
Il sistema ora calcola correttamente l&#39;importo dello sconto per le regole di vendita con importi fissi del carrello, assicurando l&#39;applicazione di sconti precisi indipendentemente dalle modifiche negli articoli del carrello. In precedenza, l’importo dello sconto poteva variare in modo errato quando gli articoli del carrello cambiavano, risultando a volte in sconti notevolmente più grandi del previsto.
  _AC-11914 - [Problema GitHub](https://github.com/magento/magento2/issues/38694) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __[Problema] Il caricatore blocca i metodi di spedizione dopo la modifica del codice postale, le regole di convalida delle tariffe di spedizione__
Il sistema ora gestisce correttamente i metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione, assicurandosi che il caricatore non blocchi i metodi di spedizione dopo la modifica del codice postale nell&#39;indirizzo di spedizione durante il pagamento. In precedenza, la modifica del codice postale nell’indirizzo di spedizione durante il pagamento causava il blocco dei metodi di spedizione da parte del caricatore, che non scompariva quando venivano utilizzati metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione.
  _AC-11993 - [Problema GitHub](https://github.com/magento/magento2/issues/38742) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_
* __La funzionalità Codice coupon non funziona correttamente nella pagina di pagamento di Magento 2.4.7__
Il sistema ora abilita il campo di input del codice sconto/coupon nella pagina di pagamento per i prodotti virtuali e scaricabili, consentendo agli utenti di applicare i codici sconto come previsto. In precedenza, l’input del codice sconto/coupon veniva disattivato e il testo del titolo del pulsante visualizzato come &quot;Annulla coupon&quot;, impedendo agli utenti di applicare codici sconto.
  _AC-12170 - [Problema GitHub](https://github.com/magento/magento2/issues/38826) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_
* __La casella di controllo dei termini e delle condizioni non consente l&#39;utilizzo di HTML in vetrina__
Il sistema ora supporta la formattazione HTML nel testo della casella di controllo &quot;Termini e condizioni&quot; nella vetrina, consentendo una personalizzazione e una leggibilità migliorate. In precedenza, il testo della casella di controllo veniva visualizzato in formato testo normale, ignorando eventuali tag di HTML utilizzati.
  _AC-12479 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __La regola del prezzo del carrello creata per l&#39;utente connesso viene erroneamente applicata per l&#39;utente non connesso__
Il sistema ora rimuove correttamente la regola del prezzo del carrello per gli utenti connessi quando vengono disconnessi automaticamente a causa della scadenza dei cookie, garantendo che lo sconto non venga applicato agli utenti non connessi. In precedenza, la regola del prezzo del carrello veniva ancora applicata anche quando l’utente veniva disconnesso, causando l’applicazione di uno sconto errato agli utenti non connessi.
  _AC-12541 - [Problema GitHub](https://github.com/magento/magento2/issues/38944) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Problema] [FUNZIONALITÀ] Ottimizzazione delle prestazioni dei grandi carrelli acquisti impedendo...__
Il sistema ora ottimizza le prestazioni per i carrelli acquisti di grandi dimensioni impedendo chiamate getActions duplicate, migliorando la velocità e l’efficienza delle operazioni del carrello. In precedenza, per un carrello con più elementi, la funzione getActions veniva chiamata più volte, rallentando le prestazioni del sistema.
  _AC-13302 - [Problema GitHub](https://github.com/magento/magento2/issues/39292) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39290)_
* __IVA di traduzione nel modulo di rendering indirizzi__
Il sistema ora consente la traduzione del testo &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; nei renderer degli indirizzi, consentendo agli utenti di tradurre questi termini nella lingua specifica del negozio. In precedenza, questi termini non erano traducibili, costringendo gli utenti a utilizzare una soluzione alternativa.
  _AC-8103 - [Problema GitHub](https://github.com/magento/magento2/issues/36942) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36943)_
* __Ordini duplicati con lo stesso ID preventivo contemporaneamente con poche differenze di tempo__
È stato risolto il problema che si verificava quando i clienti di Adobe Commerce riscontravano ordini duplicati con lo stesso QuoteID.
  _ACP2E-2055 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __Carrello acquisti permanente cancellato durante il passaggio di pagamento__
Dopo la correzione, la selezione del metodo di pagamento durante l’estrazione senza accesso non interrompe la sessione persistente.
  _ACP2E-2470 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __Riordina aggiunge al carrello un prodotto non assegnato__
In precedenza, per i diversi punti vendita, i prodotti potevano essere riordinati dall&#39;altro. Dopo aver applicato questa correzione solo allo stesso archivio, è possibile riordinare lo stesso prodotto di ambito quando è abilitata la condivisione dei conti cliente
  _ACP2E-2518 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __In admin, il &quot;carrello&quot; a sinistra non viene aggiornato quando si selezionano gli elementi e il &quot;carrello&quot; a destra__
Il &quot;Carrello acquisti&quot; a sinistra viene aggiornato quando si selezionano gli articoli e &quot;Sposta nel carrello&quot; a destra nel lato amministratore. In precedenza questa funzionalità non funzionava perché gli elementi del carrello trasformati non venivano vuoti dalla sessione.
  _ACP2E-2620 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __[Regola di vendita per cloud] non applicata al primo ordine di spedizione multipla__
Dopo la correzione, lo sconto viene visualizzato correttamente per ogni ordine dello stesso preventivo di spedizione multipla.
  _ACP2E-2646 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __[Cloud] Richieste Parallele Di Produzione Per Aggiungere Lo Stesso Prodotto Al Carrello Risultano In Due Elementi Separati Nell&#39;API REST Carrello__
Il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello tramite l’API REST generava più elementi di riga per lo stesso SKU.
  _ACP2E-2664 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __Impossibile inviare il cookie. Dimensione di &#39;mage-messages&#39; durante il tentativo di riordinare__
Il processo di riordinamento non genera ora i propri errori. Si baserà sull&#39;elenco del carrello assegni articoli incorporati.
  _ACP2E-2704 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __L&#39;indirizzo di spedizione predefinito non è selezionato al momento dell&#39;estrazione__
L’evento di selezione dell’indirizzo di spedizione predefinito viene ora eseguito nel contesto della ricerca degli indirizzi abilitata.
  _ACP2E-2798 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_
* __[Problema API addProductsToCart graphql] di CLOUD con opzione personalizzata__
GraphQL aggiunge correttamente al carrello lo stesso prodotto con diverse opzioni personalizzate
  _ACP2E-2897 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_
* __Più indirizzi aggiunti all&#39;account al momento dell&#39;estrazione come nuovo cliente__
Il sistema ora salva un nuovo indirizzo cliente una sola volta se l&#39;ordine non è stato creato, impedendo la creazione di più indirizzi identici in caso di errori di inserimento dell&#39;ordine. In precedenza, il sistema salvava un nuovo indirizzo ogni volta che veniva effettuato un tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine fosse stato creato correttamente o meno.
  _ACP2E-2923 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/2ebcef39)_
* __Il riordinamento dell&#39;ordine cliente tramite il modulo d&#39;ordine ospite genera un carrello vuoto__
In precedenza, quando si effettuava un nuovo ordine attraverso la pagina Ordini e restituzioni, il cliente veniva reindirizzato alla pagina di accesso. Dopo l’applicazione di questa correzione, il cliente registrato viene reindirizzato correttamente alla pagina Visualizza carrello al momento del riordino. Il flusso funziona come i clienti guest.
  _ACP2E-3004 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* __L&#39;utente amministratore con risorse ruolo limitate non è in grado di visualizzare i carrelli acquisti__
In precedenza, l’amministratore con restrizioni non poteva visualizzare il carrello abbandonato dal pannello di amministrazione per un sito web associato. Dopo aver applicato questa correzione, l’amministratore con restrizioni può visualizzare il carrello abbandonato dal pannello di amministrazione.
  _ACP2E-3025 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_
* __[Cloud] ordina rapidamente grandi quantità di prestazioni SKU__
Le prestazioni di checkout sono state migliorate quando gli attributi utilizzati nelle regole di prezzo del carrello non sono presenti per tutti i prodotti e quando la funzione MAP (Prezzo minimo annunciato) è abilitata.
  _ACP2E-3176 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_
* __Elementi duplicati nel carrello__
Il sistema ora elabora correttamente più richieste parallele per aggiungere lo stesso prodotto al carrello in un singolo elemento di riga, impedendo la creazione di elementi di riga separati per lo stesso SKU. In precedenza, effettuare richieste parallele per aggiungere lo stesso prodotto al carrello in Storefront generava più righe per lo stesso SKU.
  _ACP2E-3211 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_
* __L&#39;e-mail di conferma dell&#39;ordine di estrazione viene inviata alle e-mail immesse in Nome/Cognome__
La conferma e-mail dell’ordine di pagamento, precedentemente inviata quando nei campi Nome e Cognome veniva inserito un pattern simile a un’e-mail, non viene più inviata.
  _ACP2E-3296 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __Estrai il modulo dell&#39;indirizzo di spedizione e ottieni l&#39;aggiornamento con indirizzo errato__
shippingAddressFromData viene ora salvato nell&#39;archivio locale per sito Web. In precedenza, un indirizzo del sito Web errato poteva essere inserito automaticamente nel modulo dell’indirizzo di spedizione durante il pagamento se nell’URL veniva utilizzato un codice store e il pagamento veniva avviato da più siti Web durante la stessa sessione guest.
  _ACP2E-3402 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __Prodotto gift card | Unione carrello: unione delle gift card__ in corso
I prodotti Giftcard ora vengono uniti correttamente nel carrello
  _ACP2E-3407 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_
* __La persistenza del carrello non viene rispettata alla disconnessione__
È stata aggiunta la funzionalità Memorizza utente dall’accesso del cliente alla finestra a comparsa per l’autenticazione e gli accessi di pagamento.
  _ACP2E-3415 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_
* __I dati delle virgolette esistenti non sono aggiornati/non visibili. Creare un nuovo record delle virgolette quando trigger_recollect = 1__
Gli articoli del carrello del cliente non scompaiono più a seguito dell’eliminazione di un prodotto dopo che è stato aggiunto al carrello.
  _ACP2E-3488 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_
* __[CLOUD] Riordina funzionalità pulsante__
Riordinare un ordine dall&#39;area di amministrazione ora aggiungerà prodotti con scorte al preventivo anche se nell&#39;ordine originale sono presenti alcuni prodotti che non dispongono più di scorte. Prima della correzione non veniva aggiunto alcun prodotto al nuovo preventivo se il prodotto senza scorte era nell’ordine originale.
  _ACP2E-3618 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_
* __Gli archivi di ricerca non funzionano per codice postale__
La ricerca delle posizioni di prelievo per codice postale non funzionava correttamente per le localizzazioni olandesi. Dopo la correzione, la ricerca della posizione di prelievo fornirà risultati in base al codice postale.
  _ACP2E-3622 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Carrello e pagamento, Pagamento/ Pagamento di una pagina

* __[BUG casuale] Il campo E-mail non viene visualizzato o richiede molto tempo nella pagina Pagamento o spedizione pagamento__
Commerce ora esegue il rendering del campo **[!UICONTROL Email]** nelle pagine di pagamento e spedizione di pagamento di pagamento come previsto. In precedenza, questo campo era assente o visualizzato lentamente.
  _AC-9386 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e1babcfd)_

### Carrello e pagamento, ordine

* __Datepicker per il prodotto con più opzioni personalizzabili con campi data non funzionanti quando si effettua l&#39;ordine dall&#39;amministratore__
Il sistema ora visualizza correttamente il selettore data per tutti i campi della data durante la configurazione di un prodotto con più opzioni di data personalizzabili nel processo di creazione degli ordini di amministrazione. In precedenza, il selettore data veniva visualizzato solo per il primo campo data, lasciando i campi rimanenti senza un selettore data.
  _ACP2E-3097 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Carrello e pagamento, spedizione

* __Acquisto immediato &quot;spedizione più economica&quot; interrotto per prodotti configurabili__
La funzione Acquisto istantaneo ha selezionato erroneamente l&#39;opzione di consegna in-store più costosa per i prodotti configurabili invece del metodo più economico. Questa correzione assicura che venga scelto il metodo di spedizione corretto in base al prezzo effettivo.&quot;
  _AC-12119 - [Problema GitHub](https://github.com/magento/magento2/issues/38811) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38819) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29fe9097)_

### Catalogo

* __La pulizia della tabella del database cron_schedule non esegue la pulizia dei processi non esistenti__
Il sistema ora ripulisce automaticamente la tabella di database cron_schedule, rimuovendo le voci per i processi che non esistono più nel sistema. In questo modo è possibile garantire prestazioni ottimali mantenendo un numero minimo di righe nella tabella. In precedenza, le voci per i processi da moduli inattivi o rimossi non venivano pulite, generando un’inutile accumulazione di dati nella tabella cron_schedule.
  _AC-10910 - [Problema GitHub](https://github.com/magento/magento2/issues/38217) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38693)_
* __Il prezzo di livello non verrà eliminato dal prodotto configurabile__
Il sistema ora rimuove correttamente il prezzo di livello di un prodotto quando viene convertito da prodotto semplice a prodotto configurabile, garantendo una visualizzazione precisa del prezzo sul front-end. In precedenza, il prezzo di livello di un prodotto configurabile non veniva eliminato quando un prodotto veniva convertito da prodotto semplice a prodotto configurabile, determinando una mancata corrispondenza nel prezzo visualizzato.
  _AC-10953 - [Problema GitHub](https://github.com/magento/magento2/issues/38390) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38427)_
* __La descrizione della categoria WYSIWYG è vuota nella visualizzazione archivio non predefinita__
Il sistema ora salva e visualizza correttamente la descrizione della categoria nell&#39;editor di WYSIWYG quando si modifica una categoria a livello di visualizzazione store. In precedenza, l’editor WYSIWYG risultava vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione store.
  _AC-11804 - [Problema GitHub](https://github.com/magento/magento2/issues/38622) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38623)_
* __Impossibile riordinare i prodotti configurabili con una casella di controllo selezionata per l&#39;opzione personalizzata__
Il sistema ora elabora correttamente il riordino dei prodotti configurabili con una singola opzione personalizzata di casella di controllo selezionata, consentendo la corretta creazione del carrello. In precedenza, il tentativo di riordinare tali prodotti causava un errore e impediva l’aggiunta degli articoli al carrello.
  _AC-11970 - [Problema GitHub](https://github.com/magento/magento2/issues/38736) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1d144bce)_
* __[Problema] È stata corretta la formulazione dell&#39;elemento filtro nella navigazione a livelli__
Il sistema ora utilizza correttamente le parole &quot;item&quot; (elemento) e &quot;items&quot; (elementi) nell&#39;elemento del filtro di navigazione a livelli, migliorando la chiarezza e la precisione delle descrizioni del filtro. In precedenza, queste parole venivano utilizzate in modo errato, generando potenziale confusione per gli utenti che navigavano nelle opzioni del filtro.
  _AC-12076 - [Problema GitHub](https://github.com/magento/magento2/issues/38789) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37852)_
* __Il formato data e ora per l&#39;opzione personalizzata non funziona__
Il sistema ora applica correttamente il formato data configurato alle opzioni personalizzate del prodotto di tipo Data, garantendo che il formato data venga visualizzato correttamente sul front-end. In precedenza, le modifiche alla configurazione del formato della data non venivano applicate al front-end per le opzioni personalizzate del prodotto di tipo Data.
  _AC-12164 - [Problema GitHub](https://github.com/magento/magento2/issues/32990) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38925)_
* __Opzioni a discesa mancanti__
Ora il sistema visualizza correttamente tutti i valori nel menu a discesa quando crea un nuovo attributo con più di 20 valori. In precedenza venivano visualizzati solo i primi 20 valori o un altro valore di pagina selezionato, causando la mancanza dei valori rimanenti.
  _AC-13068 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problema] Utilizza l&#39;ID archivio corrente per la cache runtime delle categorie__
Il sistema ora utilizza correttamente l’ID archivio corrente per la cache runtime delle categorie, impedendo la sostituzione dei dati quando viene utilizzata l’emulazione o quando il codice personalizzato salva la categoria in archivi diversi. In precedenza, l’oggetto archiviato in fase di esecuzione poteva provenire da un archivio errato, con conseguente sostituzione dei dati.
  _AC-13296 - [Problema GitHub](https://github.com/magento/magento2/issues/39310) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36394)_
* __bin/magento sampledata:deploy —no-update genera un&#39;eccezione__
Il sistema ora accetta correttamente un valore booleano quando si utilizza l&#39;opzione —no-update nel comando sampledata:deploy, evitando errori durante la distribuzione dei dati di esempio. In precedenza, veniva generato un errore durante l’utilizzo di questo comando, poiché il sistema prevedeva erroneamente un valore intero.
  _AC-13324 - [Problema GitHub](https://github.com/magento/magento2/issues/39344) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39345)_
* __[Problema] è stato corretto l&#39;utilizzo del tipo di cache EAV__
Il sistema ora utilizza correttamente il tipo di cache EAV in tutte le posizioni rilevanti, garantendo un caching dei dati coerente ed efficiente. In precedenza, il tipo di cache EAV non veniva utilizzato in modo coerente, con potenziali inefficienze e incoerenze nella memorizzazione dei dati nella cache.
  _AC-13355 - [Problema GitHub](https://github.com/magento/magento2/issues/32322) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31264)_
* __La ricerca avanzata del catalogo con dati vuoti consente di accedere alla pagina dei risultati della ricerca[2.4.dev branch]__
Il sistema ora mantiene correttamente gli utenti nella pagina Ricerca avanzata e visualizza un messaggio di errore quando tentano di eseguire una ricerca senza immettere alcun dato. In precedenza, l’esecuzione di una ricerca vuota reindirizzava gli utenti alla pagina Ricerca avanzata catalogo con un messaggio che chiedeva di modificare la ricerca.
  _AC-13596 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __[Problema] Layout del prodotto basato su attribute_set__
Il sistema ora consente di regolare il layout del prodotto in base al set di attributi, fornendo un modo più pratico ed efficiente per gestire la visualizzazione del prodotto nel negozio front-end. In precedenza, il layout poteva essere regolato solo per SKU o per tipi di prodotto, il che non era sempre pratico per molti prodotti o articoli specifici.
  _AC-13622 - [Problema GitHub](https://github.com/magento/magento2/issues/38790) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36244)_
* __Chiave univoca mancante nella tabella eav_attribute_option_value__
Il sistema ora include una chiave univoca nelle colonne &#39;option_id&#39; e &#39;store_id&#39; nella tabella &#39;eav_attribute_option_value&#39;, impedendo la possibilità che un&#39;opzione contenga più valori per la stessa vista store. In precedenza, un codice errato poteva causare la presenza di più valori per la stessa visualizzazione archivio, causando problemi durante la modifica di prodotti o attributi.
  _AC-6738 - [Problema GitHub](https://github.com/magento/magento2/issues/24718) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/28796)_
* __[Problema] Utilizza la classe di visibilità per l&#39;indicizzatore di prodotti di categoria, anziché valori hardcoded__
Il sistema ora utilizza la classe di visibilità per l’indicizzatore di prodotto della categoria invece dei valori hardcoded, migliorando la modularità. In precedenza, venivano utilizzati valori hardcoded nell’indicizzatore dei prodotti per categoria, limitando la flessibilità e l’adattabilità.
  _AC-8297 - [Problema GitHub](https://github.com/magento/magento2/issues/37200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37199)_
* __Il codice valuta non viene modificato nel widget Nuovo prodotto__
Il sistema ora aggiorna correttamente il codice della valuta nel widget Nuovo prodotto quando la valuta viene modificata nel front-end, garantendo la coerenza nella visualizzazione della valuta in tutto il sito. In precedenza, la modifica della valuta nel front-end non influenzava il codice di valuta visualizzato nel widget Nuovo prodotto.
  _AC-9375 - [Problema GitHub](https://github.com/magento/magento2/issues/37898) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37899)_
* __Il prezzo normale non viene visualizzato nel PLP per il prodotto configurabile__
Ora sulle pagine degli elenchi dei prodotti viene visualizzato il prezzo normale per i prodotti configurabili con prodotti secondari a prezzo speciale.
  _ACP2E-2224 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __Informazioni sul titolo non visualizzate correttamente nella griglia di Visual Merchandising__
Il materiale viene ora visualizzato in base al negozio selezionato.
  _ACP2E-2478 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_
* __Il contenuto del widget non viene aggiornato nella pagina CMS__
Ora il sistema aggiorna il contenuto del widget su una pagina CMS quando un prodotto viene impostato come nuovo e salvato, assicurandosi che nella pagina venga visualizzata la raccolta di prodotti aggiornata. In precedenza, la pagina non veniva aggiornata per mostrare il nuovo prodotto a causa di identità di cache non corrette utilizzate per il widget nella cache.
  _ACP2E-2621 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __Problemi durante il salvataggio dei prezzi avanzati per i prodotti bundle__
Miglioramento delle prestazioni con risparmio sui prodotti.
  _ACP2E-2630 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __[Processo di reindicizzazione locale] inefficiente durante la creazione delle regole di prezzo catalogo__
Il salvataggio della regola del prezzo di catalogo non invalida gli indicizzatori, ma solo i prodotti interessati
  _ACP2E-2652 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_
* __Aggiornamento degli attributi di prodotto di tipo Data e Ora tramite l&#39;importazione CSV__
Ora gli attributi datetime avranno una parte temporale nei dati esportati. Sarà inoltre possibile aggiornare l’ora per tali attributi utilizzando l’importazione. Inoltre, se è abilitata l&#39;opzione &quot;Raccoglimento campi&quot;, i valori degli attributi nella colonna &quot;additional_attributes&quot; saranno racchiusi tra virgolette doppie.
  _ACP2E-2679 - [Problema GitHub](https://github.com/magento/magento2/issues/38306) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Nessun messaggio di errore appropriato quando l&#39;ID del sito Web non è corretto nella richiesta__
Ora è stato aggiunto il messaggio di errore appropriato da visualizzare quando l’ID del sito web nella richiesta non è corretto. In precedenza non vi era alcuna convalida quando l’ID del sito web nella richiesta era errato.
  _ACP2E-2689 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __L&#39;immagine del prodotto viene persa dopo l&#39;eliminazione di un aggiornamento pianificato esistente che non influisce sull&#39;immagine__
Le immagini del prodotto non vengono rimosse durante l’eliminazione dell’aggiornamento di staging.
  _ACP2E-2785 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_
* __[Cloud] Prezzo del prodotto del bundle errato se utilizzato con prezzi di livello__
Precedentemente, quando si calcolavano determinati sconti percentuali arrotondati a 2 punti decimali, si generavano prezzi finali diversi per il carrello e la pagina di elenco dei prodotti/i dettagli del prodotto. Dopo l’applicazione di questa correzione, il prezzo finale per il prodotto bundle è lo stesso della pagina dei dettagli del prodotto, della pagina di elenco dei prodotti e della pagina del mini carrello.
  _ACP2E-2799 - [Problema GitHub](https://github.com/magento/magento2/issues/38091) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __La regola delle promozioni del catalogo non funziona con l&#39;attributo quantity_and_stock_status__
L’attributo quantity_and_stock_status verrà ora preso in considerazione dalla regola di promozione del catalogo, che non era stata precedentemente presa in considerazione durante la generazione di un nuovo prodotto dal lato amministratore.
  _ACP2E-2805 - [Problema GitHub](https://github.com/magento/magento2/issues/35627) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/cf34971d)_
* __I valori della colonna update_at dell&#39;entità prodotto non vengono aggiornati durante l&#39;aggiornamento del prezzo tramite API REST__
La colonna &quot;Data ultimo aggiornamento&quot; del prodotto da parte dell’amministratore viene aggiornata alla data e all’ora corrette durante l’aggiornamento dei prodotti esistenti tramite l’API REST. In precedenza, la colonna &quot;Ultimo aggiornamento alle&quot; non veniva aggiornata correttamente.
  _ACP2E-2837 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __È possibile impostare valori non univoci tramite l&#39;importazione del prodotto__
Il sistema ora applica correttamente il vincolo del valore univoco per gli attributi di prodotto univoci durante l’importazione del prodotto, impedendo la presenza di valori duplicati per tale attributo. In precedenza, era possibile impostare valori non univoci per gli attributi del prodotto configurati per avere valori univoci tramite l’importazione del prodotto.
  _ACP2E-2840 - [Problema GitHub](https://github.com/magento/magento2/issues/38445) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_
* __I prodotti nel front-end utilizzano dati specifici dell&#39;archivio quando è abilitata la modalità Archivio singolo__
In precedenza, quando si abilitava la modalità archivio singolo per la visualizzazione archivio predefinita, le modifiche non venivano migrate nell’ambito a livello di sito web. Dopo l’applicazione di questa correzione, quando abilitiamo la modalità archivio singolo, i dati predefiniti della visualizzazione archivio verranno sincronizzati con i dati specifici a livello di sito web e risolveranno i possibili conflitti per prodotti e categorie.
  _ACP2E-2843 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_
* __Impossibile impostare &quot;Ordinamento predefinito per&quot; in una categoria utilizzando l&#39;API rest__
Aggiornare correttamente default_sort_by in una categoria tramite una richiesta REST/SOAP APi
  _ACP2E-2857 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Il commerciante sta riscontrando problemi con il numero di lista dei desideri__
L’aggiunta di un prodotto alla lista dei desideri in un negozio non aumenta più il numero di elenchi dei desideri in altri negozi aperti nello stesso browser. In precedenza, se entrambi gli store fossero caricati nello stesso browser, il numero di lista dei desideri aumenterebbe anche nell’altro store.
  _ACP2E-2871 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_
* __La pagina Categoria in front-end mostra gli slot vuoti quando si utilizza il prodotto bundle__
I prodotti bundle non vendibili nel contesto del negozio corrente non vengono più indicizzati.
  _ACP2E-2874 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bc37ec76)_
* __[Cloud] problema di offerta nell&#39;architettura di più siti Web__
In precedenza, l’architettura multisito con valute e gruppi di clienti diversi non poteva applicare correttamente gli sconti al negozio. Dopo l’implementazione di questa correzione, l’architettura multi-sito con diversi sconti sui prezzi del gruppo di clienti verrà applicata con successo ai diversi store.
  _ACP2E-2905 - [Problema GitHub](https://github.com/magento/magento2/issues/38506) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __dynamic-rows.js:658 TypeError non rilevato: dataRecord.slice durante la modifica di prodotti bundle__
Nella console del browser non è presente alcun errore JavaScript durante l’eliminazione dell’opzione dal prodotto bundle.
  _ACP2E-2909 - [Problema GitHub](https://github.com/magento/magento2/issues/38505) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_
* __[Cloud] Bundle Prezzi errati del prodotto nella conferma dell&#39;ordine__
L&#39;importo corretto viene visualizzato per le opzioni del bundle in ordine su Storefront quando è stata utilizzata una valuta diversa da quella di base.
  _ACP2E-2950 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __Bug aggiunta video YouTube__
Le immagini e i video dei prodotti sono configurati in ambito globale. Poiché non è possibile avere un video di prodotto in un ambito e non in un altro, l’impostazione della chiave API di Youtube è stata impostata su ambito globale.
  _ACP2E-2956 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __[Aggiornamento URL cloud] solo per store_id=0__
Il &quot;Percorso URL&quot; viene ora memorizzato con l’ID archivio corretto. In precedenza, l’ID archivio era errato e durante lo spostamento delle categorie continuavano a rimanere nel database percorsi URL errati.
  _ACP2E-2964 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_
* __async.operations.all eseguito e creato un errore.__
I dati di collegamento del prodotto errati nelle chiamate API REST non causano più errori critici.
  _ACP2E-3009 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_
* __[Problema cloud] solo per dispositivi mobili che non è in grado di pizzicare l&#39;immagine PDP__
Il sistema ora supporta la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili su Chrome, migliorando l’esperienza di utilizzo mobile. In precedenza, il doppio tocco sull’immagine nella visualizzazione per dispositivi mobili su Chrome non consentiva di ingrandire l’immagine come previsto.
  _ACP2E-3029 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_
* __Etichetta mancante in LayeredNavigation con nome opzione 0__
Il problema è stato risolto saltando una verifica del valore vuoto per il valore di attributo 0. In precedenza, veniva considerata vuota e causava il problema.
  _ACP2E-3058 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_
* __I clienti visualizzano i prezzi di altri gruppi di clienti__
È stato risolto un problema a causa del quale le informazioni relative al gruppo di clienti venivano salvate in un segmento errato a causa del vecchio valore di X-Magento-Vary nella richiesta.
  _ACP2E-3069 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_
* __Errore durante l&#39;eliminazione delle opzioni del bundle__
Il sistema ora elimina correttamente le opzioni del bundle senza attivare un errore o impedire la risposta della pagina. In precedenza, se si tentava di eliminare le opzioni del bundle, si verificava un errore &quot;Page Unresponsive&quot; (Non risponde pagina) e si impediva il salvataggio del prodotto.
  _ACP2E-3076 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* Il file di immagine __[Cloud] non esiste nel registro errori di New Relic__
Il sistema ora sincronizza le immagini segnaposto personalizzate con l’archiviazione locale, garantendo che vengano riprodotte correttamente quando si utilizza l’archiviazione remota, ad esempio AWS S3. In precedenza, il rendering delle immagini segnaposto personalizzate non riusciva quando si utilizzava l’archiviazione remota, causando una visualizzazione delle immagini interrotta e registri di errori.
  _ACP2E-3100 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_
* __Il feed RSS dei nuovi prodotti non è aggiornato con i nuovi prodotti a causa della cache__
Il feed Rss per i nuovi prodotti viene ora aggiornato quando un prodotto viene impostato come nuovo e salvato
  _ACP2E-3103 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_
* La risposta GQL di __[Cloud] Product Media Gallery non è ordinata in base alla posizione dell&#39;immagine__
Il sistema ora ordina correttamente gli elementi nella raccolta multimediale in base alla posizione nella risposta del GraphQL, garantendo un ordine di visualizzazione accurato. In precedenza, gli elementi nella raccolta multimediale non venivano ordinati in base alla posizione, causando un ordine di visualizzazione errato.
  _ACP2E-3126 - [Problema GitHub](https://github.com/magento/magento2/issues/37671) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91)_
* __[Gli elementi della sottocategoria cloud] non vengono visualizzati nella modifica dei widget nel backend di amministrazione__
La struttura delle categorie nella nuova pagina widget non dovrebbe più presentare problemi nel caricamento delle categorie di livello 5+. In precedenza, mancavano alcune categorie durante il caricamento della struttura oltre le categorie di livello 5.
  _ACP2E-3136 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_
* __[cloud] problema di zoom e spostamento a due dita sul dispositivo mobile reale__
Il sistema ora garantisce una funzionalità di zoom coerente delle immagini sui dispositivi mobili, fornendo un&#39;esperienza utente fluida e prevedibile. In precedenza, la funzione di zoom dell’immagine era incoerente e improvvisamente si riduceva dopo un certo punto quando veniva visualizzata su un dispositivo mobile.
  _ACP2E-3198 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_
* __Quando si rimuovono le assegnazioni di prodotti dal catalogo condiviso, i prodotti della lista dei desideri non vengono cancellati__
Ora, se un prodotto non è disponibile nel catalogo condiviso, non sarà visibile alcun elemento nella lista dei desideri. In precedenza, la pagina della lista dei desideri mostrava erroneamente un conteggio di &quot;1 elemento&quot; anche quando nessun elemento era effettivamente disponibile nella lista dei desideri.
  _ACP2E-3282 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __Prodotti correlati Seleziona tutto/Deseleziona tutto__
In precedenza, i pulsanti &quot;Seleziona tutto&quot;/&quot;Deseleziona tutto&quot; per i prodotti correlati non funzionavano correttamente se un prodotto veniva selezionato manualmente. Dopo la correzione, questi pulsanti ora funzionano in modo coerente, anche dopo la selezione manuale, garantendo che tutti i prodotti siano selezionati correttamente o deselezionati.
  _ACP2E-3286 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Cloud] Traduzione e-mail avviso Stock nella lingua errata__
Quando si inviano avvisi su azioni/prezzi per un sito web con più visualizzazioni del negozio utilizzando lingue diverse, nell’e-mail verrà utilizzata la lingua per la visualizzazione del negozio in cui è stato creato l’avviso.
  _ACP2E-3336 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_
* __I nomi delle categorie disabilitate non sono più disattivati nell&#39;albero delle categorie__
In precedenza, le categorie disabilitate non erano disattivate nella struttura delle categorie. Ora vengono visualizzate con un effetto di grigio.
  _ACP2E-3350 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_
* __Il caricamento del modulo di modifica del prodotto configurabile causa timeout e esaurimento della memoria__
Prima della correzione, le varianti di prodotto configurabili erano costruite in base a tutte le possibili combinazioni di opzioni di attributo. Nei casi in cui gli attributi disponevano di numerose opzioni, l’operazione risultava lunga e dispendiosa in termini di risorse. Ora le varianti di prodotto configurabili sono costruite in base agli attributi di prodotto secondari esistenti. Ciò comporta un numero molto inferiore di calcoli, quindi un migliore utilizzo delle risorse.
  _ACP2E-3410 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __Fotorama non carica correttamente il video quando si utilizzano i campioni e l&#39;opzione è preselezionata tramite URL__
Ora i video dei prodotti vengono riprodotti correttamente nella pagina dei dettagli dei prodotti configurabile, se l’URL contiene opzioni selezionate.
  _ACP2E-3454 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __Il widget Carosello PageBuilder mostra prodotti che non soddisfano le condizioni__
L’elenco dei prodotti utilizzati nei widget ora rispetta la condizione della categoria
  _ACP2E-3461 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __Errore Di Convalida Attivato Per Tutti I Prodotti Del Gruppo Se Uno Dei Prodotti Presenta Una Quantità Non Valida__
Ora, l’errore di convalida viene attivato correttamente per tutti i prodotti del gruppo quando un prodotto ha una quantità non valida, il che non si verificava in precedenza.
  _ACP2E-3469 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/56463d5e)_
* __[CLOUD] Prezzo speciale non visualizzato nel prodotto configurabile__
Dopo la correzione, la modifica del valore &quot;Usato nell’elenco dei prodotti&quot; per l’attributo di prezzo speciale non influirà sulla visualizzazione del prezzo speciale per i prodotti configurabili.
  _ACP2E-3513 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_
* __Le tabelle temporanee degli indicizzatori non vengono pulite se il processo viene terminato__
Le tabelle temporanee dell&#39;indicizzatore CatalogRule vengono ora pulite se il processo di indicizzazione viene terminato
  _ACP2E-3516 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_
* __[QUANS] errori di unit test di base in 2.4.7-p3__
Le note sulla versione di questo test non sono necessarie in quanto si tratta di un miglioramento di unit test.
  _ACP2E-3520 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_
* __Problema di prestazioni nel recupero della quantità di magazzino per prodotti raggruppati con più origini__
La pagina di modifica di prodotto raggruppato e bundle è ora ottimizzata quando i prodotti assegnati hanno un numero elevato di sorgenti di inventario.
  _ACP2E-3533 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/0208e433)_
* __Correzione ACP2E-3389__
Sono state migliorate le prestazioni della pagina categoria amministratore in caso di numero elevato di categorie di ancoraggio
  _ACP2E-3641 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogo, contenuto

* La cache __[Cloud] non viene invalidata.__
In precedenza, quando si salvava una pagina CMS con un layout di progettazione aggiornato, questa non veniva riflessa in modo appropriato nel front-end. Una volta applicata questa correzione, il layout di progettazione appropriato sarà visibile nel front-end quando si modifica il layout di progettazione e si salva la pagina CMS.
  _ACP2E-3063 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_
* __[Categorie di ancoraggio/non di ancoraggio di Cloud] invertite nel widget del contenuto__
In precedenza, quando si selezionava Visualizza su -> Categorie di ancoraggio, venivano visualizzate tutte le categorie che non riflettevano la relazione padre-figlio tra l&#39;ancoraggio e il non ancoraggio. Dopo l&#39;applicazione di questa correzione, Visualizza attivato -> Categorie di ancoraggio visualizza solo le Categorie di ancoraggio (selezionabile), mentre Visualizza attivato -> Categorie non di ancoraggio visualizza le Categorie non di ancoraggio (selezionabile)
  _ACP2E-3131 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_
* __Categorie non funzionanti con widget__
In precedenza, se salvavamo il blocco CMS per diverse categorie di ancoraggio/non di ancoraggio, non funzionava per le categorie figlio quando veniva visualizzato sul front-end. Dopo l’applicazione di questa correzione, il blocco viene visualizzato nel front-end per diverse categorie.
  _ACP2E-3152 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

### Catalogo, Framework

* __Raccolta ordini get(Spedizioni|Creditmemos|Fattura)Raccolta - Impossibile caricare la raccolta__
Il sistema ora assicura che le raccolte per le spedizioni e le note di credito non vengano precaricate quando vengono recuperate da un ordine, consentendo l&#39;applicazione di filtri o ordini aggiuntivi a tali raccolte. In precedenza, queste raccolte venivano caricate automaticamente, impedendo ulteriori modifiche.
  _AC-9111 - [Problema GitHub](https://github.com/magento/magento2/issues/37561) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37562)_
* __[Cloud]Follow-up: mancata corrispondenza nel confronto dei dati durante la verifica se i dati hanno subito modifiche__
In precedenza, l’oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica di dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Inoltre, non controlla i numeri mobili incapsulati da stringa. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa
  _ACP2E-2949 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_

### Catalogo, GraphQL

* __Gestione dei filtri delle categorie in GraphQL: includeDirectChildrenOnly e category_uid__
Durante il filtraggio per category_uid vengono recuperate solo le categorie figlio dirette.
  _ACP2E-3090 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93d50f8d)_
* __[L&#39;ordinamento del prodotto Graphql per Cloud] non funziona__
L’ordinamento dei prodotti GraphQl per più campi quando i campi vengono passati nelle variabili ora funziona come previsto.
  _ACP2E-3166 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_
* __I prezzi di livello restituiscono un valore errato nei prodotti GraphQL (rispetto a Storefront)__
Dopo la correzione, i prezzi del livello del prodotto restituiti per le richieste graphql hanno prezzo per un articolo.
  _ACP2E-3312 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### Catalogo, prezzi, staging e anteprima

* __[Cloud] L&#39;endpoint API a prezzo speciale restituisce un errore quando si aggiornano contemporaneamente numerosi prodotti__
Ora l’API per l’aggiornamento in blocco dei prezzi speciali creerà una singola campagna per ogni intervallo di date invece di più aggiornamenti pianificati per ogni prodotto e intervallo di date. Inoltre, supporterà le richieste API simultanee per un’elaborazione più rapida di un gran numero di SKU.
  _ACP2E-2672 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f89a447e)_

### Catalogo, prodotto

* __La struttura di selezione delle categorie nella modifica del prodotto non è nello stesso ordine impostato in Catalogo->Categorie__
Il sistema ora visualizza correttamente la struttura di selezione delle categorie nella sezione di modifica del prodotto nello stesso ordine impostato in Catalogo->Categorie, semplificando l’amministrazione dei prodotti nei cataloghi di grandi dimensioni. In precedenza, la struttura ad albero delle categorie nella sezione di modifica del prodotto veniva visualizzata in ordine di creazione delle categorie, indipendentemente dall’ordine di visualizzazione impostato in Catalogo->Categorie.
  _AC-7050 - [Problema GitHub](https://github.com/magento/magento2/issues/36101) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36104)_

### Catalogo, SEO

* __URL canonico errato per la categoria quando la pagina è > 1__
In precedenza, l’URL canonico per il contenuto multipagina non funzionava correttamente, visualizzando in modo coerente l’URL di base. Tuttavia, dopo l’implementazione della correzione, l’URL canonico per i contenuti con più pagine ora visualizza correttamente l’URL con l’ID pagina.
  _ACP2E-3653 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogo, Ricerca

* __I prodotti non vengono visualizzati nella categoria e nella ricerca, ma i collegamenti diretti funzionano__
In precedenza, l’attributo personalizzato Sì/No con price_* attribute_code non funzionava con l’indicizzazione. Dopo questa correzione, l’attributo personalizzato Sì/No funziona come previsto.
  _ACP2E-2757 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __[Cloud] Errore di ricerca elastica in alcune pagine categoria__
In precedenza, con il ticket di configurazione menzionato, quando si inseriva il prezzo 0 per più prodotti, veniva generata un’eccezione nella pagina della categoria front-end. Dopo che questa correzione è stata applicata quando più prezzi del prodotto 0 e la pagina della categoria viene caricata in front-end, non viene generata alcuna eccezione e la pagina della categoria viene caricata correttamente.
  _ACP2E-3053 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_
* __Errore di tipo durante la creazione dell&#39;oggetto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception__
Dopo la correzione, è possibile creare un&#39;istanza della classe Magento\CatalogSearch\Model\Indexer\Fulltext senza specificare $data.
  _ACP2E-3345 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_
* __[Il problema di CLOUD] con i prodotti non è visibile in FrontEnd dopo il salvataggio in Magento Admin__
Dopo la correzione i prodotti configurabili che hanno prodotti secondari con nomi lunghi non verranno persi nella vetrina.
  _ACP2E-3521 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Cloud

* __[Cloud] PHPSESSID sta modificando ogni richiesta POST__
PHPSESSID non viene più rigenerato nelle richieste POST sull&#39;area front-end per un cliente connesso se la cache L2 Redis è abilitata e il cliente è stato aggiornato dal back-end
  _ACP2E-3010 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* __Avvisi di generazione mappa del sito__
Dopo la correzione, la mappa del sito viene generata nella directory tmp del sistema e copiata nella destinazione finale.
  _ACP2E-3532 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Contenuto

* __[Problema] relativo alla visualizzazione del prezzo nel widget Visualizzato di recente__
Il sistema ora visualizza correttamente il prezzo dei prodotti semplici esauriti nel widget &quot;Prodotto visualizzato di recente&quot;, garantendo la coerenza tra tutti i widget e le pagine dell’elenco dei prodotti. In precedenza, il prezzo dei prodotti semplici esauriti non veniva visualizzato nel widget &quot;Prodotto visualizzato di recente&quot; a causa di una condizione nei modelli di caricamento del prezzo.
  _AC-10539 - [Problema GitHub](https://github.com/magento/magento2/issues/38167) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38159)_
* __[Problema] Digitare e grammatica corretti nel file acl.xsd__
Il sistema ora corregge un errore di battitura e grammatica nel file acl.xsd, migliorando la chiarezza e l’accuratezza della documentazione. In precedenza, il file acl.xsd conteneva un errore ortografico e grammaticale non corretto che poteva causare confusione.
  _AC-10596 - [Problema GitHub](https://github.com/magento/magento2/issues/38061) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38046)_
* __Immagine del banner di Pagebuilder non visibile nella raccolta__
Il sistema ora visualizza correttamente le immagini del banner caricate nelle cartelle appena create nella raccolta Pagebuilder, eliminando gli errori precedenti della console. Prima di questa correzione, le immagini del banner non erano visibili nella raccolta se venivano caricate in una nuova cartella, causando un errore nella console.
  _AC-10845 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_
* __&quot;Codice di zona non impostato&quot; dopo l&#39;aggiornamento a 2.4.5-p8__
Il sistema ora completa correttamente il processo di distribuzione del contenuto statico quando il modulo Magento_CSP è abilitato e &quot;dev/js/translate_strategy&quot; è impostato su &quot;embedded&quot;, senza attivare l’errore &quot;indicativo di località non impostato&quot;. In precedenza, in queste condizioni, il processo di distribuzione del contenuto statico non riusciva e veniva visualizzato un errore di tipo &quot;Codice di area non impostato&quot;.
  _AC-12283 - [Problema GitHub](https://github.com/magento/magento2/issues/38845) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38922)_
* __Il rendering della struttura di categorie del widget non è corretto__
  _AC-12692 - [Problema GitHub](https://github.com/magento/magento2/issues/39008) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/58e40ceb)_
* __Impossibile visualizzare il messaggio &quot;Utilizzo del valore predefinito&quot; durante la modifica del tema nella pagina di configurazione della progettazione__
Il sistema ora include una colonna separata per visualizzare il messaggio &quot;Using Default value&quot; (Uso del valore predefinito) a seconda del tema selezionato nella pagina di configurazione della progettazione. Questo garantisce chiarezza e visibilità dello stato del valore predefinito. In precedenza, il messaggio &quot;Using Default value&quot; (Utilizzo del valore predefinito) non veniva visualizzato, generando confusione sullo stato del tema selezionato.
  _AC-13054 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problema] Ripristina nuovamente la compatibilità con i plug-in TinyMCE (dopo...__
Il sistema ora ripristina la compatibilità con le versioni precedenti dei plug-in TinyMCE, consentendo di chiamare le funzioni definite all&#39;interno del plug-in quando si utilizza il widget da un&#39;altra posizione. In precedenza, a causa di una modifica nella versione TinyMCE, i plug-in non restituivano i widget come oggetto, causando un errore quando si tentava di chiamare alcune funzioni sull’istanza del widget.
  _AC-13569 - [Problema GitHub](https://github.com/magento/magento2/issues/39262) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39258)_
* __[Problema] problema di caricamento file nell&#39;editor di WYSIWYG nella pagina del prodotto__
Il sistema ora visualizza correttamente la struttura ad albero delle cartelle e consente il caricamento di immagini nell’editor WYSIWYG sulla pagina del prodotto, anche dopo aver espanso prima la scheda &quot;Immagine e video&quot;. In precedenza, l’espansione della scheda &quot;Immagini e video&quot; causava prima la mancata visualizzazione della struttura delle cartelle e un messaggio di errore durante il caricamento di un’immagine nell’editor di WYSIWYG.
  _AC-9638 - [Problema GitHub](https://github.com/magento/magento2/issues/38026) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38025)_
* __[On-PREM] problema blocco dinamico__
Il rendering dei widget ora viene eseguito correttamente all’interno dei blocchi dinamici.
  _ACP2E-2392 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_
* __[Cloud] Frontend non si carica a causa di un problema nel modello di newsletter__
L’aggiunta di blocchi tramite la sezione del contenuto di una pagina CMS non causa più un’eccezione
  _ACP2E-2693 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_
* __ACP2E-2836: [Cloud] Rilevata eccezione di analisi nel registro: InvalidArgumentException: la classe non esiste in vendor/magento/module-rule/Model/ConditionFactory.php__
La rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder non causa più la registrazione di un&#39;eccezione nei file di registro. In precedenza, la rimozione di una condizione nelle impostazioni del contenuto dei prodotti PageBuilder causava la registrazione di un’eccezione critica nei registri, nonostante non causasse problemi sul front-end.
  _ACP2E-2836 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_
* __Passaggio alla modalità archivio singolo - il contenuto globale non viene più visualizzato__
Ora il sistema sincronizza le configurazioni di progettazione della vista archivio con le configurazioni di progettazione del sito web quando si abilita la modalità di archiviazione singola, garantendo che gli aggiornamenti del contenuto siano visibili sul front-end. In precedenza, il passaggio alla modalità single store impediva che gli aggiornamenti dei contenuti venissero rispecchiati nella vetrina.
  _ACP2E-2842 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_
* __Page Builder sostituisce l&#39;immagine quando si tenta di aggiungere un collegamento e altri errori di usabilità.__
Facendo clic su un&#39;immagine, i collegamenti nell&#39;editor wysiwyg nell&#39;elemento di testo Page Builder verranno caricati i dati corretti nella finestra di dialogo immagine, configurazione collegamento. Anche l’aggiunta di un collegamento a un’immagine nell’editor ora funziona correttamente. In precedenza, l’immagine veniva sostituita da un collegamento.
  _ACP2E-2903 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __La raccolta multimediale precedente non riesce a eseguire il rendering delle immagini quando si inserisce un&#39;immagine a 0 byte nella directory__
Il sistema ora gestisce le immagini a 0 byte nella raccolta multimediale senza interrompere la funzionalità, consentendo la visualizzazione e la selezione di altre immagini nella directory come previsto. In precedenza, la presenza di un&#39;immagine a 0 byte nella raccolta multimediale impediva la visualizzazione o la selezione di tutte le immagini nella directory.
  _ACP2E-2970 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_
* __Errore di Page Builder durante la modifica del blocco CMS__
Il sistema ora salva correttamente le modifiche apportate nell’area di amministrazione utilizzando Page Builder, senza generare l’errore &quot;Page Builder ha eseguito il rendering per 5 secondi senza rilasciare blocchi&quot;. nella console del browser. In precedenza, questo errore si verificava quando si tentava di salvare le modifiche, impedendo il corretto aggiornamento del contenuto.
  _ACP2E-3064 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __[CLOUD] Nessun pulsante di estrazione o modifica del carrello nella sezione carrello__
Il prodotto bundle ora viene aggiunto al carrello tramite widget senza errori.
  _ACP2E-3092 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b21e5d91) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_
* __[CLOUD] Il pulsante Carica immagine non funziona__
Prima il pulsante Carica immagine per il banner e il cursore da PageBuilder non funzionava come previsto e ora quando si preme si apre il file manager locale per selezionare l&#39;immagine da caricare.
  _ACP2E-3122 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_
* __imagecreatetruecolor(): il #2 dell&#39;argomento ($height) deve essere maggiore di 0. Impossibile caricare un&#39;immagine specifica__
È stato risolto il problema che causava errori nell’amministratore durante il caricamento di immagini con altezza pari a 0 tramite la raccolta multimediale ed è stata eseguita con successo la sincronizzazione delle risorse tramite il comando sync. In precedenza non era possibile caricare l’immagine tramite la raccolta multimediale e il comando di sincronizzazione ha esito negativo anche quando un’immagine specifica si trova nella raccolta.
  _ACP2E-3127 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_
* __Array Prototype.js.from in conflitto con l&#39;API Google Maps__
Google Maps ora viene eseguito correttamente nell’editor di PageBuilder. In precedenza, un errore JavaScript impediva il corretto rendering di Google Maps.
  _ACP2E-3154 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_
* __[Cloud] - Il cursore di CMS non riflette le ultime modifiche__
Il problema è stato risolto assicurandosi che l’elenco di dispositivi di scorrimento venga aggiornato mentre l’evento di salvataggio viene attivato nella schermata di modifica della diapositiva. In precedenza, si attivava e causava il problema.
  _ACP2E-3275 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __Si è verificato un errore nella pagina CSM quando i blocchi di CMS vengono inseriti utilizzando il generatore di pagine in un determinato ordine__
In precedenza, su alcune versioni di PHP e OS (Linux), il rendering dei blocchi che facevano riferimento ad altri blocchi CMS attraverso PageBuilder non sarebbe riuscito con un &quot;Si è verificato un errore sconosciuto. Riprova.&quot;. Ora il contenuto dei blocchi cms viene riprodotto correttamente all’interno di un contenuto controllato da PageBuilder.
  _ACP2E-3326 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __Errore di anteprima del modello di Pagebuilder per contenuti di grandi dimensioni__
Contenuto di grandi dimensioni causava l’overflow dell’elemento canvas nei limiti del browser e la restituzione di un valore errato, con conseguente interruzione del codice di back-end (impossibile decodificare correttamente l’immagine). È stato corretto limitando le dimensioni dell’area di lavoro al limite del browser universale.
  _ACP2E-3428 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/adfb1747)_
* __Ultimi aggiornamenti di sicurezza con dimensione font mancante in TinyMCE 7__
I selettori delle dimensioni e della famiglia di caratteri sono ora disponibili in WYSIWYG Editor. Prima di questa correzione, con TinyMCE 7 queste non erano disponibili nell’interfaccia dell’editor.
  _ACP2E-3430 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_
* __Le dimensioni del font dell&#39;editor TinyMCE 7 nell&#39;amministratore in PT e non in PX sono corrette__
Prima della correzione non era possibile specificare la dimensione del font in pixel nelle aree WYSIWYG. Ora è possibile impostare la dimensione del carattere in px anziché in pt.
  _ACP2E-3483 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __Il tipo di contenuto del prodotto in Page Builder viene compresso senza messaggi corretti__
Prima della correzione, l’html di anteprima non veniva generato correttamente se il widget non conteneva prodotti. Ora la risposta vuota viene generata correttamente e il widget prodotti viene visualizzato correttamente nell’anteprima.
  _ACP2E-3490 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __[Page Builder]Aggiunta dell&#39;elenco dei prodotti per bloccare i risultati in errori__
L’aggiunta dell’elenco dei prodotti del bundle al blocco tramite Page Builder non genera errori
  _ACP2E-3534 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Cliente/clienti

* __Front-end - Convalida della data di nascita non riuscita nella pagina di creazione del cliente__
Assicurati che tutta la convalida funzioni dopo la dipendenza del sistema moment.js dall’aggiornamento alla versione secondaria più recente
  _AC-12162 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Il campo di testo dell&#39;area non viene reimpostato quando il menu a discesa del paese viene modificato__
Il sistema ora reimposta il campo di testo dell&#39;area geografica quando il paese viene modificato nel menu a discesa, assicurandosi che i valori precedenti non persistano. In precedenza, la modifica del paese dall’elenco a discesa non reimpostava il campo area e veniva mantenuto l’ultimo valore salvato.
  _AC-8499 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_
* __L&#39;eliminazione del cliente non comporta la pulizia di tutti i dati della sessione del browser su Storefront per il cliente connesso ed eliminato__
L’eliminazione di un cliente ora pulisce tutti i dati della sessione del browser dalla vetrina per i clienti che hanno effettuato l’accesso e per quelli eliminati, come previsto. L’acquirente può continuare a fare acquisti e il browser tratta la sua sessione come una sessione ospite. In precedenza, quando l’account del cliente per un acquirente connesso veniva eliminato dall’amministratore, il browser dell’acquirente generava errori JavaScript.
  _AC-9240 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

### Framework

* __[Domanda]Configurazione tipo inutilizzato in`app/code/Magento/Translation/etc/di.xml`__
Il sistema ora rimuove le dipendenze inutilizzate nella configurazione, migliorando la pulizia e l’efficienza complessiva del codice. In precedenza, nella configurazione vi erano dipendenze non utilizzate che non contribuivano ad alcuna funzionalità.
  _AC-10037 - [Problema GitHub](https://github.com/magento/magento2/issues/38030) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38064)_
* __V1/customers/password endpoint question/issue__
Il sistema ora rispetta i vincoli impostati all&#39;interno dell&#39;interfaccia grafica di gestione quando elabora le richieste di modifica della password tramite l&#39;API, impedendo il potenziale abuso della funzione di reimpostazione della password. In precedenza, l’API poteva elaborare richieste di modifica della password al di fuori delle regole definite nell’interfaccia grafica di gestione, consentendo potenzialmente un flusso costante di e-mail di reimpostazione se erano note e-mail valide.
  _AC-10654 - [Problema GitHub](https://github.com/magento/magento2/issues/38238) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __La configurazione di vernice non esclude tutti i parametri di marketing__
Il sistema ora esclude correttamente tutti i parametri di marketing comuni nella configurazione di Vernice, garantendo un tracciamento e un’analisi accurati. In precedenza, alcuni parametri di marketing, come gad_source, srsltid e msclkid, non venivano esclusi, generando potenziali imprecisioni nella raccolta dei dati.
  _AC-10738 - [Problema GitHub](https://github.com/magento/magento2/issues/38298) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39188)_
* __Processo di indicizzazione errori processo indice di ricerca catalogo__
Il sistema ora completa correttamente il comando di reindicizzazione senza incontrare errori, indipendentemente dalla versione libxml compilata con PHP. In precedenza, l’esecuzione del comando di reindicizzazione causava un errore di &quot;Errore di processo dell’indice di ricerca del catalogo durante il processo di indicizzazione&quot; quando PHP veniva compilato con determinate versioni di libxml.
  _AC-10838 - [Problema GitHub](https://github.com/magento/magento2/issues/38254) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38553) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_
* __Sono stati aggiunti i filtri created_at, status e grand_total alla query Ordini cliente e sono stati corretti più filtri non riusciti__
Il sistema ora supporta l’utilizzo di filtri created_at, status e grand_total nelle query Ordini cliente e ha risolto un problema che impediva la corretta applicazione di più filtri. In precedenza, il sistema non supportava questi filtri e non applicava tutti i filtri quando in una query ne veniva utilizzato più di uno.
  _AC-10941 - [Problema GitHub](https://github.com/magento/magento2/issues/38392) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36949)_
* __Inondazione casuale di query da blocchi correlati / upselling / crossselling e indicizzazione dei prezzi__
Il sistema ora ottimizza le query da blocchi correlati, di upselling e di cross-selling, migliorando le prestazioni ed evitando che il sito si abbassi a causa di query eccessive. In precedenza, il sistema poteva essere sovraccarico di query provenienti da questi blocchi, causando rallentamenti significativi e potenzialmente riducendo il sito.
  _AC-10991 - [Problema GitHub](https://github.com/magento/magento2/issues/36667) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38050)_
* __Eccezione: avviso: tentativo di accedere all&#39;offset dell&#39;array in... -> Calendar.php dall&#39;aggiornamento a ICU 74.1 (PHP Intl)__
Commerce non registra più la seguente eccezione in exception.log ogni volta che un acquirente o un commerciante visita la vetrina o l&#39;amministratore: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
  _AC-11423 - [Problema GitHub](https://github.com/magento/magento2/issues/38214) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38364)_
* __[Problema] Correggi i problemi relativi ai dati dei clienti quando il modulo contiene un elemento con nome`method`__
Il sistema ora identifica correttamente l’attributo &quot;method&quot; nell’invio del modulo, anche quando nel modulo è presente un elemento denominato &quot;method&quot;. In questo modo i dati dei clienti vengono elaborati con precisione. In precedenza, se un elemento modulo fosse denominato &quot;metodo&quot;, interferirebbe con l’identificazione dell’attributo &quot;metodo&quot; nell’invio dei moduli, causando potenziali problemi con la gestione dei dati dei clienti.
  _AC-11476 - [Problema GitHub](https://github.com/magento/magento2/issues/38484) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38449)_
* __[Problema] Correzione di PHPDocs per \Magento\Framework\Data\Collection::getItemById__
I PHPDocs per il metodo \Magento\Framework\Data\Collection::getItemById sono stati aggiornati per includere null come possibile tipo restituito, risolvendo i problemi con gli strumenti di analisi statica. In precedenza, i PHPDocs del metodo non specificavano null come possibile tipo restituito, generando avvisi o errori nell&#39;analisi statica quando il metodo veniva utilizzato nelle istruzioni condizionali.
  _AC-11489 - [Problema GitHub](https://github.com/magento/magento2/issues/38485) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38439)_
* __[Problema] Consenti solo preferenze valide durante`setup:di:compile`__
Il sistema ora genera un errore durante il comando `setup:di:compile` se viene creata una preferenza per una classe che non esiste o che è specificamente esclusa, assicurandosi che siano consentite solo le preferenze valide. In precedenza, questi scenari avrebbero avuto esito negativo in silenzio, rendendo potenzialmente inutili i plug-in associati alle classi originali.
  _AC-11592 - [Problema GitHub](https://github.com/magento/magento2/issues/38517) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33161)_
* __Magento sta tentando di modificare la proprietà di sola lettura nel metodo di riattivazione __di LoggerProxy__
Il sistema ora consente di modificare le proprietà di sola lettura precedenti nel metodo di riattivazione __LoggerProxy, garantendo un funzionamento senza forzare gli utenti a utilizzare una soluzione alternativa. In precedenza, si verificavano problemi se si tentava di riassegnare il valore di una proprietà di sola lettura nel metodo di riattivazione __LoggerProxy.
  _AC-11651 - [Problema GitHub](https://github.com/magento/magento2/issues/38526) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_
* __[Problema] AC-2039 AC-1667 aggiornamento riferimenti TinyMCE__
Versione aggiornata più recente di tinymce in compositore.json
  _AC-11681 - [Problema GitHub](https://github.com/magento/magento2/issues/38533) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36543) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b34c0a75)_
* __ChangelogBatchWalker non funziona in più thread__
Il sistema ora supporta il fork di processo per l&#39;indicizzazione MView, evitando errori durante l&#39;esecuzione dell&#39;indicizzatore quando si opera su più thread. In precedenza, l’esecuzione di ChangelogBatchWalker su più thread determinava l’eliminazione delle tabelle utilizzate da altri thread, causando un errore durante l’esecuzione dell’indicizzatore.
  _AC-11696 - [Problema GitHub](https://github.com/magento/magento2/issues/38246) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38248)_
* __[Problema] Rinominare la variabile con nome errato__
Il sistema ora assegna correttamente i nomi alla variabile che contiene la quantità di denaro che può ancora essere rimborsata, evitando confusione durante il debug. In precedenza, questa variabile veniva erroneamente denominata totalRefund, il che poteva generare malintesi per gli sviluppatori.
  _AC-11781 - [Problema GitHub](https://github.com/magento/magento2/issues/38609) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36205)_
* __[Problema] Trasmettere gli attributi personalizzati al collegamento corrente tramite XML__
Il sistema ora consente di passare gli attributi personalizzati al collegamento corrente tramite XML, garantendo che vengano visualizzati correttamente anche quando il collegamento è nella pagina corrente. In precedenza, gli attributi personalizzati non venivano visualizzati per il collegamento della pagina corrente perché il metodo getAttributesHtml() non veniva utilizzato per il collegamento corrente.
  _AC-11809 - [Problema GitHub](https://github.com/magento/magento2/issues/38500) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30070)_
* __La cache FPC integrata è interrotta nella versione 2.4.7 per alcune configurazioni__
Ora il sistema memorizza correttamente nella cache le pagine quando è impostato il parametro MAGE_RUN_CODE, garantendo prestazioni ottimali. In precedenza, le pagine non venivano memorizzate nella cache in queste condizioni, causando potenziali problemi di prestazioni.
  _AC-11819 - [Problema GitHub](https://github.com/magento/magento2/issues/38626) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38646) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __[Problema] è stata corretta l&#39;incoerenza nella gestione delle eccezioni tra le modalità di sviluppo e di produzione__
Il sistema ora gestisce in modo coerente le eccezioni tra le modalità di sviluppo e di produzione, evitando il reindirizzamento imprevisto alla pagina di accesso quando viene generata un’eccezione. In precedenza, un’incoerenza nella gestione delle eccezioni poteva causare un reindirizzamento alla pagina di accesso in modalità di produzione invece di visualizzare il messaggio di eccezione.
  _AC-11829 - [Problema GitHub](https://github.com/magento/magento2/issues/38639) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37712)_
* __Sostituisci la traduzione &#39;Conto PayPal&#39; in token_list.phtml__
Il sistema ora etichetta la sezione per i metodi di pagamento con conto &quot;tokenizable&quot; come &quot;Account&quot; invece di &quot;Conto PayPal&quot; nella pagina Metodi di pagamento memorizzati, rendendola più rappresentativa della sua funzione. In precedenza, questa sezione era specificamente etichettata come &quot;Conto PayPal&quot;, che era fuorviante quando sono stati aggiunti altri metodi di pagamento per account tokenizable.
  _AC-11852 - [Problema GitHub](https://github.com/magento/magento2/issues/35622) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37959)_
* __Compatibilità con le versioni precedenti persa nella classe Magento\Catalog\Model\ProductRepository__
La classe ProductRepository ora mantiene la compatibilità con le versioni precedenti ripristinando la classe Initialization Helper come secondo parametro, garantendo che i moduli che si estendono da questa classe funzionino come previsto. In precedenza, la rimozione di Initialization Helper dal costruttore nella classe ProductRepository comportava una perdita di compatibilità con le versioni precedenti, costringendo gli utenti a utilizzare una soluzione alternativa.
  _AC-11874 - [Problema GitHub](https://github.com/magento/magento2/issues/38669)_
* __[Problema] Distribuzione di contenuto statico - Errore di tipo__
Il sistema ora gestisce correttamente i file LESS vuoti durante la distribuzione del contenuto statico, visualizzando un messaggio di errore &quot;LESS file is empty&quot;. In precedenza, veniva generato un errore di tipo errato quando si incontrava un file LESS vuoto durante la distribuzione.
  _AC-11905 - [Problema GitHub](https://github.com/magento/magento2/issues/38682) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38683)_
* __[Problema] [Visualizzazione] Spazio aggiuntivo rimosso nel tag collegamento e script__
Il sistema ora assicura che non vi siano spazi aggiuntivi nei tag di collegamento e script, fornendo un codice più pulito ed efficiente. In precedenza, si trovavano doppi spazi tra gli attributi nei tag link e script.
  _AC-12002 - [Problema GitHub](https://github.com/magento/magento2/issues/32920) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32919)_
* __[Problema]: evitare un loop infinito di configurazione errata__
Il sistema ora evita un ciclo infinito impedendo la mappatura autoreferenziale nelle configurazioni di tipo virtuale. In questo modo l’applicazione non si blocca in un ciclo infinito quando si tenta di dereferenziare un nodo autoreferenziale. In precedenza, se una configurazione di tipo virtuale fosse autoreferenziale, l’applicazione girerebbe indefinitamente.
  _AC-12127 - [Problema GitHub](https://github.com/magento/magento2/issues/38822) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38794)_
* __Gestione oggetti non utilizzato per Magento\Csp\Model\Mode\Data\ModeConfigured__
Il sistema ora utilizza correttamente Object Manager durante la creazione dell&#39;oggetto ModeConfigured, consentendo l&#39;utilizzo di plug-in su questo oggetto. In precedenza, Object Manager non veniva utilizzato, impedendo l’applicazione dei plug-in all’oggetto ModeConfigured.
  _AC-12299 - [Problema GitHub](https://github.com/magento/magento2/issues/38875) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38886)_
* __Commento impreciso del blocco di documenti in Avvisi su azioni e prezzi di prodotto__
Il commento del blocco del documento per il metodo deleteCustomer negli avvisi di prezzo e scorte prodotto è stato corretto per riflettere con precisione il fatto che il metodo elimina tutti gli avvisi di prezzo o prodotto di magazzino associati a un determinato cliente e sito Web, non il cliente dal sito Web. In precedenza, il commento affermava erroneamente che il metodo era quello di eliminare un cliente dal sito web.
  _AC-12540 - [Problema GitHub](https://github.com/magento/magento2/issues/38939) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39001)_
* __[Problema] Utilizza la configurazione compilata per i dati generati invece della configurazione generale__
Il sistema ora utilizza la configurazione compilata per i dati generati invece della configurazione generale, riducendo il trasferimento di rete e il sovraccarico dei dati che dipende da una determinata versione del codice. Questa modifica impedisce l’override della cache nelle istanze condivise durante lo scambio dei contenitori, migliorando la stabilità e riducendo i tempi di inattività. In precedenza, alcune classi principali utilizzavano il tipo di configurazione condiviso, che poteva causare l’override della cache o tempi di inattività dell’applicazione a causa delle differenze nelle versioni del codice tra più server.
  _AC-12594 - [Problema GitHub](https://github.com/magento/magento2/issues/38785) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29954)_
* __[Problema] Rimuovere i riferimenti ai file da extjs che sono stati rimossi in e1ccdb...__
Il sistema ora rimuove i riferimenti ai file da extjs che erano stati precedentemente rimossi, eliminando gli errori nella console del browser e nel file di registro del sistema. In precedenza, questi riferimenti causavano errori a causa dell’assenza dei file di riferimento.
  _AC-12597 - [Problema GitHub](https://github.com/magento/magento2/issues/38960) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38951)_
* __[Problema] Pulizia secondaria: è stato corretto l&#39;utilizzo errato di sprintf. Sono necessari solo due segnaposto qui e w...__
Il sistema ora utilizza correttamente la funzione sprintf con il numero appropriato di segnaposto, migliorando la pulizia e la coerenza del codice. In precedenza, la funzione sprintf veniva erroneamente utilizzata con un argomento aggiuntivo, che non causava problemi importanti ma non era l’utilizzo corretto.
  _AC-12778 - [Problema GitHub](https://github.com/magento/magento2/issues/39062) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38628)_
* __PHP 8.2.15 ha rimosso l&#39;estensione FTP__
Il sistema ora include l’estensione FTP come dipendenza nel file compositore.json, garantendo la corretta configurazione delle importazioni CSV tramite FTP. In precedenza, veniva generato un errore durante il tentativo di configurare le importazioni CSV tramite FTP a causa dell’assenza dell’estensione FTP nel pacchetto PHP.
  _AC-12857 - [Problema GitHub](https://github.com/magento/magento2/issues/39083) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_
* __[Problema] Corregge le classi errate a cui si fa riferimento nei moduli Magento.__
Il sistema ora fa correttamente riferimento alle classi nei moduli, garantendo un funzionamento più fluido ed evitando arresti anomali dovuti a classi non esistenti. Ciò include un bug nei moduli Indexer e Creditmemo e l&#39;implementazione di HttpGetActionInterface nella classe PrintAction. In precedenza, i riferimenti di classe errati causavano errori e potenziali arresti anomali del sistema, e alcune funzionalità, come il nome del file creditmemo PDF e la reindicizzazione delle scorte, non funzionavano come previsto.
  _AC-12869 - [Problema GitHub](https://github.com/magento/magento2/issues/39126) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37784)_
* __Possibilità di definire l&#39;area per il comando CLI `dev:di:info`__
Il sistema ora consente agli sviluppatori di definire un&#39;area per il comando CLI `dev:di:info`, migliorando il processo di sviluppo e debug. In precedenza, questo comando consentiva di visualizzare solo le informazioni relative all&#39;area GLOBAL.
  _AC-12964 - [Problema GitHub](https://github.com/magento/magento2/issues/38758) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38759)_
* __[Problema] aggiungere la proprietà isMultipleFiles al modello di elemento del modulo dell&#39;immagine__
Questa correzione evita che il pulsante &quot;Sfoglia per trovare o trascinare l’immagine qui&quot; scompaia quando un’immagine viene aggiunta in un elemento modulo immagine con più file.
  _AC-13149 - [Problema GitHub](https://github.com/magento/magento2/issues/39219) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36325)_
* __[Problema] Rimuovi tutti i parametri di marketing get per ridurre la cache__
Il sistema ora rimuove tutti i parametri di marketing get per ottimizzare l’utilizzo della cache, rispecchiando la logica utilizzata quando è in uso vernice. In precedenza, questi parametri potevano causare il gonfiore della cache e ridurre le prestazioni.
  _AC-13279 - [Problema GitHub](https://github.com/magento/magento2/issues/39266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39099)_
* __[Problema] [PHPDOC] Correzione phpdoc non valido Magento\Directory\Model\AllowedCountries::getAllowedCountries()__
Il metodo PHPDoc per AllowedCountries::getAllowedCountries() è stato corretto per fornire informazioni accurate, migliorando la chiarezza e l’utilità della documentazione. Precedentemente, il PHPDoc per questo metodo conteneva informazioni errate, che potevano portare a confusione o uso improprio del metodo.
  _AC-13345 - [Problema GitHub](https://github.com/magento/magento2/issues/39246) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39241)_
* __[Problema] Rimuove parte del codice per le versioni PHP non più supportate.__
Rimozione del codice per le versioni PHP non più supportate in Magento
  _AC-13348 - [Problema GitHub](https://github.com/magento/magento2/issues/39361) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39202)_
* __[Problema] Rendere l&#39;adattatore ImageMagick compatibile con php8 (conversione implicita da float a int)__
Il sistema ora garantisce la compatibilità con PHP8 gestendo correttamente i numeri in virgola mobile durante il calcolo delle dimensioni dell&#39;immagine, evitando errori dovuti alla conversione implicita da virgola mobile a int. In precedenza, il calcolo delle dimensioni dell’immagine poteva causare numeri in virgola mobile che, se arrotondati in modo implicito, generavano un errore.
  _AC-13417 - [Problema GitHub](https://github.com/magento/magento2/issues/39402) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37362)_
* __[Problema] [PHPDOC] Correzione phpdoc non valido Magento\Framework\App\Config\ScopeConfigInterface__
Questo aggiornamento corregge le annotazioni PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface per riflettere con precisione il tipo di argomento $scopeCode per i metodi getValue e isSetFlag.
  _AC-13537 - [Problema GitHub](https://github.com/magento/magento2/issues/39492) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39199)_
* __Magento\Framework\Filesystem\Driver\Http dipende dalla frase del motivo OK__
È stato rimosso il controllo della frase &quot;OK&quot; da Magento\Framework\Filesystem\Driver\Http::isExists
  _AC-13725 - [Problema GitHub](https://github.com/magento/magento2/issues/39546) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39558)_
* __L&#39;indicizzatore Griglia cliente non funziona correttamente in modalità Aggiornamento pianificato__
La griglia del cliente precedente è stata aggiornata istantaneamente ma dopo la correzione la griglia del cliente viene aggiornata dopo l’esecuzione della cron ma non viene visualizzata immediatamente.
  _AC-13810 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_
* __errore di battitura in un file js.__
Il sistema ora utilizza correttamente il termine &quot;abbonati&quot; nel file JavaScript, garantendo la corretta funzionalità delle relative funzioni. In precedenza, un errore tipografico nel file JavaScript causava l’uso errato del termine &quot;abbonati&quot;.
  _AC-6754 - [Problema GitHub](https://github.com/magento/magento2/issues/36163) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36171)_
* __[Problema] Rimuovi il tag `@author` non consentito__
Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` proibito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.
  _AC-8353 - [Problema GitHub](https://github.com/magento/magento2/issues/37253) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37003)_
* __[Problema] Rimuovi il tag `@author` non consentito da `Magento_Customer` (parte 2)__
Il sistema ora rispetta lo standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, il tag `@author` era presente in alcuni moduli, in contrasto con gli standard di codifica stabiliti.
  _AC-8356 - [Problema GitHub](https://github.com/magento/magento2/issues/37250) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37000)_
* __Lo spazio nella sintassi editorconfig interrompe la regola per [{compositore,auth}.json]__
Il sistema ora applica correttamente un rientro a 4 spazi ai file compositore e auth.json, in seguito a una correzione di un errore di sintassi nell&#39;editor config. In precedenza, a causa di uno spazio nella sintassi editorconfig, questi file non venivano formattati correttamente con un rientro a 2 spazi.
  _AC-8659 - [Problema GitHub](https://github.com/magento/magento2/issues/37394) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37395)_
* __[Problema] Migliorare la registrazione degli errori cron__
Il sistema ora acquisisce e registra sia STDERR che STDOUT per i processi cron, fornendo informazioni diagnostiche preziose in scenari in cui i processi cron falliscono. In precedenza, eventuali messaggi di errore all’interno dei processi cron non venivano registrati e STDERR e STDOUT per i gruppi cron in esecuzione in processi separati andavano persi.
  _AC-8662 - [Problema GitHub](https://github.com/magento/magento2/issues/37453) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32690)_
* __[Problema] Aggiunge altri colori all&#39;output di alcuni comandi cli di installazione__
Il sistema ora aggiunge più colori all&#39;output di alcuni comandi CLI (Command Line Interface) di installazione, migliorando la leggibilità e l&#39;esperienza utente. In precedenza, l&#39;output di questi comandi era più difficile da leggere a causa della mancanza di differenziazione dei colori.
  _AC-8984 - [Problema GitHub](https://github.com/magento/magento2/issues/29335) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29298)_
* __L&#39;aggiornamento di Magento reimposta General/region/state_required quando viene aggiunto un nuovo paese con lo stato o l&#39;area geografica richiesti.__
Il sistema ora aggiunge il paese modificato alla configurazione &quot;general/region/state_required&quot; solo quando viene aggiunto un nuovo paese con stati required, evitando interruzioni del codice personalizzato che presuppongono la disabilitazione della regione. In precedenza, l’aggiunta di un nuovo paese con stati obbligatori reimpostava la configurazione &quot;general/region/state_required&quot; sui paesi predefiniti con uno stato obbligatorio, potenzialmente interrompendo il negozio.
  _AC-9630 - [Problema GitHub](https://github.com/magento/magento2/issues/37796) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38076)_
* __Differenza nella compilazione minore tra la libreria php e nodejs (grunt) con `calc` espressioni complicate__
Correggi la differenza in meno compilazione tra libreria php e nodejs (grunt) dopo aggiornamento wikimedia/less.php:^5.x
  _AC-9712 - [Problema GitHub](https://github.com/magento/magento2/issues/37841) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b34c0a75)_
* __Errore &quot;Impossibile trovare la tabella o la vista di base&quot; quando viene eseguita l&#39;indicizzazione parziale__
La reindicizzazione parziale ora funziona correttamente con il changelog grande in caso di connessione db secondaria
  _ACP2E-2692 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __Problemi dopo l&#39;aggiornamento di MariaDB a 10.5.1 o versione successiva__
È stato risolto il problema che si verificava quando i valori datetime in un database venivano convertiti in 0000-00-00 00:00:00 dopo l&#39;aggiornamento di Mysql.
  _ACP2E-2844 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a12063bd)_
* __Tipo non corrispondente nel confronto dei dati durante la verifica della presenza di modifiche nei dati__
In precedenza, l’oggetto di salvataggio veniva chiamato ogni volta senza alcuna modifica di dati (per qualsiasi campo dati numerico, ad esempio int/float/double). Attiva il flag _hasDataChanges su true e chiama la funzione di salvataggio. Dopo l’applicazione di questa correzione, la funzione di salvataggio chiamerà solo se i dati vengono modificati. Il valore di dati per int/float/double-check con il valore passato alla funzione e esegue una corrispondenza di tipo rigorosa.
  _ACP2E-2855 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_
* Impossibile utilizzare l&#39;importazione __[Cloud] con la directory var__
Il prodotto può essere importato correttamente indipendentemente dal nome file.
  _ACP2E-2959 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_
* __In ipad mini il menu e l&#39;intestazione vengono caricati come dispositivi mobili, ma come desktop.__
Il sistema ora tratta i dispositivi con una larghezza di 768 px come desktop, garantendo che il menu e l&#39;intestazione vengano caricati correttamente. In precedenza, i dispositivi con una larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile.
  _ACP2E-2966 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __La modifica della lunghezza della colonna tramite db_schema.xml non funziona in caso di chiavi esterne__
La modifica della colonna con chiave esterna tramite lo schema dichiarativo ora non genera errori con MariaDB
  _ACP2E-3230 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __Alcuni dei record delle relazioni vengono salvati nel database quando il record dell&#39;ordine viene salvato__
Prima della correzione venivano attivate query UPDATE non necessarie che potevano avere un impatto sulle prestazioni. Dopo la correzione, le query UPDATE non necessarie sono state eliminate.
  _ACP2E-3361 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD] Nella console sono presenti molti errori JavaScript__
In precedenza, nel pannello di amministrazione erano presenti molti errori JavaScript nella console. Ora, nel pannello di amministrazione, non ci saranno errori JavaScript nella console e tutte le funzioni predefinite di JavaScript verranno eseguite correttamente senza alcun problema.
  _ACP2E-3375 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_
* __[Cloud] Magento: il messaggio della coda è stato eliminato__
I messaggi della coda ora vengono cancellati correttamente. Prima della correzione, dato che il sistema della coda SQL era in uso, i nuovi messaggi potevano essere eliminati se il messaggio della coda di pulizia era in esecuzione allo stesso tempo.
  _ACP2E-3387 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Le voci della chiave della cache corrispondenti non sono disponibili nei tag della cache, pertanto la pulizia della cache non funziona correttamente__
La modalità LUA è ora abilitata per impostazione predefinita per il Garbage Collector della cache Redis per evitare race condition
  _ACP2E-3537 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_
* Il valore __MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK viene ignorato__
Dopo la correzione, una variabile ENV impostata su &quot;false&quot; verrà trattata come bool false, non come stringa &#39;false&#39;.
  _ACP2E-3681 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

* __[Problema] È stato introdotto il supporto di tipi scalari personalizzati per lo schema GraphQL__
Il sistema ora supporta i tipi scalari personalizzati per lo schema di GraphQL, consentendo agli sviluppatori di definire tipi e implementazioni scalari personalizzati. Questa funzione può essere particolarmente utile per esprimere valori che possono richiedere la convalida, come HTML, e-mail, URL, date e così via, e per casi più avanzati come gli attributi EAV. In precedenza, il sistema non supportava l’elaborazione di tipi scalari personalizzati in GraphQL.
  _AC-7976 - [Problema GitHub](https://github.com/magento/magento2/issues/36877) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/34651) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### Framework, Framework interfaccia utente

* __Possibilità di sovrascrivere il valore di configurazione anche se è bloccato__
Prima di questa correzione, non era possibile impostare la configurazione di progettazione tramite il comando bin/magento config:set e i valori bloccati potevano essere modificati manipolando il modulo che li visualizzava. Dopo la correzione i valori bloccati impostati da cli con —lock-env o —lock-conf non possono più essere aggiornati.
  _ACP2E-3324 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

* __Magento_GraphQl esegue l&#39;elaborazione delle intestazioni anche se il valore dell&#39;intestazione non supera la convalida__
Il sistema ora garantisce che l’elaborazione dell’intestazione venga eseguita una sola volta e solo se il valore dell’intestazione supera la convalida, migliorando la sicurezza e impedendo potenziali vulnerabilità. In precedenza, l’elaborazione dell’intestazione veniva eseguita anche se il valore dell’intestazione non superava la convalida, generando potenziali vulnerabilità e comportamenti imprevisti dovuti alla doppia elaborazione dei valori dell’intestazione.
  _AC-11729 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8f87c25)_
* __L&#39;ordinamento delle opzioni Giftcard fisiche non è corretto__
Il sistema ora ordina correttamente le opzioni dei prodotti gift card fisici quando viene richiesto tramite GraphQL, garantendo un rendering coerente con il tema Luma. In precedenza, l’ordinamento era errato in base al tema luma, causando una visualizzazione e un ordinamento errati delle opzioni, ad esempio nome del mittente, nome del destinatario e importo.
  _AC-8951 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_
* __[GraphQL] Resolver Cache invalidata durante la creazione, la modifica, lo spostamento o l&#39;eliminazione di un aggiornamento di gestione temporanea__
Il sistema ora assicura che la cache del risolutore non venga invalidata durante la creazione, la modifica, lo spostamento o l’eliminazione di un aggiornamento di staging, ma solo quando l’aggiornamento di staging viene applicato all’entità. In precedenza, la cache del risolutore veniva invalidata prematuramente, anche prima dell’applicazione dell’aggiornamento di staging, il che portava a inutili invalidamenti della cache.
  _AC-9157 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Cache rapida non cancellata per l&#39;aggiornamento dell&#39;area di gestione temporanea del contenuto__
Ora GraphQL con cache di risposta dei contenuti di PageBuilder viene invalidato quando le entità correlate al contenuto di PageBuilder vengono aggiornate.
  _ACP2E-2642 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __Disabilitazione della navigazione a livelli - Non rimuove l&#39;aggregazione da Graphql__
Il problema è stato risolto dopo l’applicazione del controllo durante la richiesta di una ricerca di prodotto con aggregazioni di categorie tramite una query GraphQL quando l’impostazione di configurazione dell’amministratore è &quot;Catalogo > Navigazione a livelli > Visualizza filtro categorie&quot;.
  _ACP2E-2653 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/12e071c3)_
* __La chiamata ai prodotti GraphQL contenente il filtro prezzi {from:&quot;0&quot;} non restituisce alcun risultato__
In precedenza, la ricerca di prodotti graphql con filtro per prezzi zero non restituiva alcun risultato a causa di un’eccezione generata. Ora la ricerca restituisce i risultati come previsto.
  _ACP2E-2928 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_
* __Traduzioni per gli attributi restituiti dal cliente non incluse nell&#39;API GraphQL per il rispettivo StoreView__
Le traduzioni per gli attributi di restituzione del cliente si riflettono nell&#39;API di GraphQL per il rispettivo StoreView.
In precedenza, gli attributi di restituzione dei clienti per i rispettivi StoreView non venivano riportati nell’API di GraphQL.
  _ACP2E-2974 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] chiamata GraphQL interrotta per getPurchaseOrder con preventivo del nodo__
La chiamata GraphQL dell’ordine di acquisto sarà in grado di eseguire l’attività senza incontrare errori interni al server.
  _ACP2E-3128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6f4805f8)_
* __[Cloud] Prodotti configurabili non visualizzati nel sito di produzione se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;__
Il sistema ora visualizza correttamente i prodotti configurabili nel sito anche se il prodotto non è abilitato in &quot;Tutte le visualizzazioni dello store&quot;, ma è abilitato in ambiti specifici di visualizzazione dello store.
In precedenza, se un prodotto veniva disabilitato in &quot;Tutte le visualizzazioni store&quot; e abilitato solo in ambiti di visualizzazione specifici, gli attributi del prodotto non venivano visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.
  _ACP2E-3184 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/3f300077)_
* __[Graphql di prodotti Cloud] con errore quando lo stesso prodotto semplice è stato assegnato a più prodotti configurabili__
In precedenza, con prodotti configurabili separati con lo stesso prodotto semplice, grapQL restituiva un errore. Dopo l’applicazione di questa correzione, diversi prodotti configurabili con lo stesso prodotto semplice, grapQL restituisce il risultato senza errori.
  _ACP2E-3190 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/148c3ead)_
* __[Problema cloud] con l&#39;autenticazione utente e l&#39;accesso ai token intersito nella configurazione multisito__
Le query relative a informazioni sul cliente e sul carrello GraphQl in Configurazione multisito controllano se il cliente è presente sul sito web non predefinito.
La query precedente funzionava senza assicurarsi che il cliente esistesse su un sito Web non predefinito in Configurazione multisito.
  _ACP2E-3215 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __La paginazione di GraphQL cart itemsV2 non funziona correttamente__
Il problema è stato risolto passando il valore corretto per l&#39;argomento pagina corrente nella query di raccolta. In precedenza, veniva trasmesso un valore errato per impostare la pagina corrente, causando il problema.
  _ACP2E-3253 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_
* È necessario specificare il valore del modello __[GRAPHQL] per ottenere customerCart__
La query &quot;customerCart&quot; di GraphQL ora può creare un carrello vuoto anche quando il preventivo non è disponibile nel database. In precedenza, questa operazione non riusciva a causa di problemi di convalida del paese durante la creazione del carrello vuoto.
  _ACP2E-3255 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[Gli elementi dell&#39;elenco dei desideri GraphQl] sono visibili tramite GraphQl ma non nella vetrina__
Prodotti della lista dei desideri che non sono stati correttamente elencati quando richiesto tramite GraphQL. Adesso, i prodotti della lista dei desideri vengono filtrati in base al contesto del negozio fornito.
  _ACP2E-3380 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_
* __[GraphQL] Reimposta incoerenza e-mail password tra contenuto e oggetto/collegamento__
Il problema è stato risolto simulando il negozio corretto in cui è registrato l’account del cliente al momento dell’invio della richiesta di reimpostazione della password, indipendentemente dallo store del sito web.
  _ACP2E-3404 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __[Prodotti cloud] La query GraphQL restituisce prodotti correlati non assegnati al sito Web corrente__
In precedenza, per la query graphQL, i prodotti correlati a più store non venivano visualizzati correttamente per la query del prodotto. Dopo l’applicazione di questa correzione, per i prodotti, graphQL esegue una query sui prodotti correlati a più store visualizzati di conseguenza.
  _ACP2E-3419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __L&#39;utilizzo di un ID archivio errato nell&#39;intestazione di GraphQL causa un errore irreversibile di memoria__
L’invio di codice archivio errato nella richiesta GraphQL non comporta più un consumo eccessivo di memoria.
  _ACP2E-3447 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Risposta cloud] 500 a una risposta Graphql vuota nella versione 2.4.7__
Dopo la correzione, le richieste graphql non valide non verranno registrate nel file exception.log.
  _ACP2E-3467 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_
* __[Problemi con l&#39;API Graphql]__
Prima della correzione tramite il server applicazioni Graphql, la richiesta dell&#39;indirizzo del cliente non restituiva i dati più recenti.
  _ACP2E-3492 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_
* __Il prodotto disabilitato viene ancora visualizzato negli elementi correlati, di upselling e di cross-selling nella query grpahQL__
Graphql fornisce ora una risposta corretta per i prodotti relared, upselling e cross-selling disabilitati
  _ACP2E-3505 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_
* __[CLOUD]: errore GraphQl Errore interno del server. Mutazione placeOrder__
La mutazione &quot;placeOrder&quot; con le informazioni sul codice coupon nella richiesta non genera più un’eccezione di errore interna, l’ordine è stato effettuato correttamente. In precedenza, non riusciva con &quot;Errore interno del server&quot;.
  _ACP2E-3647 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_
* __La percentuale di sconto non è calcolata per i prodotti bundle con prezzo dinamico__
Correzione aggiunta per sconto_percentuale di product.price_details che non mostra il valore corretto per i prodotti bundle con prezzo dinamico abilitato e coupon di sconto applicato.
  _LYNX-426_
* __Il bundle dei prodotti mostra ancora &quot;IN_STOCK&quot; quando uno dei suoi prodotti in bundle è esaurito__
Risoluzione del problema per cui i prodotti bundle mostravano ancora &quot;IN_STOCK&quot; anche quando uno dei loro prodotti bundle era esaurito.
  _LYNX-485_
* __not_available_message e only_x_left_in_stock non mostra le stesse scorte disponibili__
È stato risolto il problema che causava la visualizzazione incoerente della disponibilità delle scorte in not_available_message e only_x_left_in_stock
  _LYNX-486_
* Il campo __original_row_total restituisce un valore errato__
È stato risolto il problema relativo al campo original_row_total, che restituiva valori errati quando venivano selezionate opzioni personalizzate.
  _LYNX-488_
* __La miniatura di prodotto raggruppata deve essere visualizzata in base alla configurazione     .__
È stato risolto il problema per garantire che la miniatura del prodotto raggruppato venga visualizzata in base alle impostazioni di configurazione
  _LYNX-503_
* __original_item_price non include sconti__
Original_item_price è stato aggiornato per includere gli sconti.
  _LYNX-512_
* __Il messaggio non disponibile non mostra la quantità di magazzino disponibile__
È stato risolto il messaggio di errore e il codice di errore per la mutazione AddProductsToCart in modo da allinearlo alla configurazione del messaggio &quot;not available&quot; (non disponibile)
  _LYNX-530_
* Lo stato __&quot;OUT_OF_STOCK&quot; viene restituito su Semplice con opzioni personalizzate e prodotti con opzioni a selezione multipla__
È stato aggiornato il risolutore StockStatusProvider nel pacchetto di inventario per correggere stock_status per i prodotti semplici con opzioni personalizzate.
  _LYNX-532_
* __Errore (GQL): cart.itemsV2.items.product.custom_attributesV2 restituisce un errore del server__
È stato risolto l’errore del server che si verificava quando una query sul carrello includeva gli attributi personalizzati di un prodotto aggiungendo un prodotto senza attributi personalizzati.
  _LYNX-533_
* __orders/date_of_first_order restituisce sempre null__
È stato risolto il problema per cui orders > date_of_first_order restituiva sempre null.
  _LYNX-536_
* __Il cliente non può annullare un ordine parzialmente spedito__
È stata aggiunta la convalida per impedire ai clienti di annullare un ordine spedito parzialmente.
  _LYNX-544_
* __Codici di errore per l&#39;annullamento dell&#39;ordine in base al messaggio di errore__
I codici di errore per l’annullamento dell’ordine ora si basano sul messaggio di errore specifico.
  _LYNX-548_
* __Ripristina le proprietà relative ai cookie da private a protected__
Ripristina la visibilità delle proprietà del costruttore di classe Magento\Framework\App\PageCache\Version da private a protected
  _LYNX-581_
* __Aumenta la complessità delle query GraphQL predefinite a 1000__
La complessità massima predefinita delle query GraphQL è stata aumentata da 300 a 1000.
  _LYNX-600_
* __GQL - itemsV2 > Riga totale originale, i prezzi della fascia di prezzo vengono restituiti come $0,00 per il prodotto scaricabile con opzioni di file che ha prezzi separati.__
È stato risolto un problema a causa del quale i prodotti scaricabili con opzioni di acquisto di collegamento separate abilitate restituivano $ 0 per gli articoliV2 > Totale riga originale e l’intervallo di prezzo restituiva $ 0,00 per i prodotti con opzioni di file con prezzi separati.
  _LYNX-620_
* __Compatibilità GraphQl per PHP-8.4 versione__
Sono stati risolti i problemi di compatibilità di GraphQL con PHP 8.4 su più resolver, garantendo funzionalità senza problemi. Sono stati aggiornati i file interessati nei moduli CatalogRule, Customer, GiftMessage, GiftCard e GiftWrapping.
  _LYNX-772_

### GraphQL, Inventory/MSI

* __La mutazione MergeCart genera un&#39;eccezione quando i carrelli di origine e di destinazione hanno gli stessi elementi bundle__
&quot;-
  _ACP2E-2607 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, inventario/MSI, prestazioni

* __Sito inattivo dopo aggiornamento__
Sono state migliorate le prestazioni di recupero dei prodotti bundle tramite GraphQl.
  _ACP2E-1716 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Prestazioni

* __[GraphQL Resolver] I dati del resolver del cliente non sono invalidati dall&#39;importazione__
La cache del resolver clienti GraphQL ora viene invalidata come previsto quando un cliente viene modificato o eliminato tramite importazioni. In precedenza, la cache non veniva invalidata e i dati dei clienti potevano essere modificati o eliminati durante l’importazione.
  _AC-9569 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Cerca

* __L&#39;ordinamento dell&#39;elenco di prodotti GraphQL in base a più parametri non funziona__
L’ordinamento dei prodotti per più campi in GraphQl ora funziona come descritto nella documentazione
  _ACP2E-2809 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_
* __Query GraphQL dell&#39;elenco prodotti limitata a un totale di 10.000 prodotti__
Dopo la correzione, il risultato della ricerca non è limitato ai prodotti 10000, ma diventa possibile ottenere tutti i prodotti che corrispondono ai criteri di ricerca anche se il conteggio è superiore a 10000.
  _ACP2E-948 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, framework di prova

* __Magento\GraphQl\App\GraphQlCustomerMutationsTest.php errore test integrazione__
&quot;-
  _ACP2E-3363 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importa/esporta

* __Problema durante l&#39;importazione del prodotto se fornito con il tipo di opzione personalizzato: file (il prodotto creato non contiene il prezzo per l&#39;opzione personalizzata e mostra solo la prima estensione del tipo di file fornita)__
Il sistema ora importa correttamente i dati del prodotto con opzioni personalizzate di tipo &quot;file&quot;, assicurandosi che vengano visualizzate tutte le estensioni di file fornite e che venga incluso il prezzo per l’opzione personalizzata. In precedenza, durante l’importazione del prodotto, se un’opzione personalizzata di tipo &quot;file&quot; veniva fornita con più di un’estensione di file, veniva visualizzata solo la prima estensione e mancava il prezzo per l’opzione personalizzata.
  _AC-12172 - [Problema GitHub](https://github.com/magento/magento2/issues/38805) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38926)_
* __Tempo di esecuzione errato per l&#39;operazione di importazione nella griglia della cronologia di importazione__
Il tempo di esecuzione dell’importazione del rapporto viene visualizzato correttamente, indipendentemente dalle impostazioni locali dell’amministratore.
  _ACP2E-2710 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Clienti duplicati creati con lo stesso indirizzo e-mail mediante l&#39;importazione__
Viene aggiornata l&#39;importazione del cliente mentre Condivisione account è impostato su Globale, cliente importato che esiste nel sistema.
Il cliente importato in precedenza è stato duplicato.
  _ACP2E-2737 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_
* __Aggiungi/aggiorna importazione su prodotti che duplicano opzioni personalizzabili__
Il problema è stato risolto assegnando l’archivio corretto alle opzioni del prodotto durante le importazioni CSV delle opzioni del prodotto.
In precedenza, venivano assegnati all’archivio di amministrazione invece che al rispettivo archivio.
  _ACP2E-2902 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Data &quot;created_at&quot; cliente non convertita in fuso orario di archiviazione al momento dell&#39;esportazione__
Un valore di data colonna &quot;created_at&quot; viene convertito nel formato di data corretto in base al fuso orario dell’archivio nella sezione CSV di esportazione del cliente.
  _ACP2E-2990 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3056e9cb)_
* __[Cloud] Ricezione di un errore durante la verifica dei dati nei dati di importazione tramite CSV__
Non viene generato alcun errore durante il controllo dei dati durante l’importazione CSV. In precedenza, il messaggio di errore visualizzato era: &quot;Impossibile trovare un cliente che corrisponda a questo indirizzo e-mail e al codice del sito web nelle righe: 1&quot; quando si controllano i dati nella sezione di importazione utilizzando il file CSV dell’amministratore.
  _ACP2E-3165 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8459b17d)_
* __Pulsante Importa mancante__
Per risolvere il problema di mancanza del pulsante Importa, segui una verifica dei dati con record corretti e non corretti nel file CSV. In precedenza, il pulsante di importazione non veniva visualizzato dopo il controllo dei dati con record corretti e non corretti nel file CSV.
  _ACP2E-3172 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1819fe73)_
* __Impossibile importare l&#39;indirizzo del cliente esportato__
L’importazione dell’indirizzo del cliente procederà come previsto. In precedenza, un file di importazione dell’indirizzo di un cliente non superava la convalida se Condividi account del cliente = Globale ed esistono due siti web in cui il sito web predefinito ha un elenco di paesi limitato e l’indirizzo che viene importato è per un altro sito web in cui i paesi consentiti sono diversi
  _ACP2E-3382 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud] La quantità errata nel file CSV non ha restituito alcun errore__
Ora l’importazione delle origini delle scorte genera un errore di convalida per i valori non numerici nella colonna Quantità. In precedenza, l&#39;importazione di origini di scorte con valore non numerico nella colonna Quantità comportava l&#39;impostazione della quantità su 0.
  _ACP2E-3448 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5b21b7af)_
* __Il messaggio di errore relativo alla chiave URL duplicata generato durante l&#39;importazione di un prodotto non è corretto se la chiave URL appartiene già a una categoria__
Visualizzazione del messaggio di errore corretto durante il controllo dell’importazione del prodotto, quando il cliente ha tentato di importare un prodotto quando il codice URL del prodotto appartiene già a una categoria.
  _ACP2E-3455 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_
* __L&#39;esportazione del prodotto causa OOM anche con limite di memoria 4G__
Prima di questa correzione, l’esportazione del prodotto non riusciva se gli attributi del prodotto avevano migliaia di valori di opzione anche con la memoria disponibile 4G. Dopo questa correzione, l’esportazione del prodotto dovrebbe terminare l’esportazione del file CSV.
  _ACP2E-3475 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_
* __[Processi di importazione cloud] che interferiscono tra loro__
I messaggi corretti vengono visualizzati se lo stesso utente amministratore esegue due o più operazioni di importazione utilizzando la stessa sessione utente.
  _ACP2E-3527 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Importazione/esportazione, prestazioni

* __[Cloud] Il tempo di importazione del prodotto è notevolmente aumentato__
Prima della correzione, l’importazione di prodotti catalogo con più di 10.000 voci presentava una notevole riduzione del tempo. Dopo la correzione, l’importazione del prodotto catalogo viene eseguita in modo tempestivo.
  _ACP2E-3476 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/87d012e5)_

### Installazione e amministrazione

* __L&#39;aggiornamento di Magento non riesce in MariaDB 11.4 + 2.4.8-beta1__
L’aggiornamento dovrebbe avvenire senza alcun errore.
  _AC-13242 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7b336d0a)_
* __Nessun VCL di esportazione per il pulsante Vernice 7 nel pannello di amministrazione__
Il pulsante &quot;Esporta VCL per vernice 7&quot; è stato aggiunto al pannello di amministrazione.
  _ACP2E-2102 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventario/MSI

* __L&#39;aggiornamento dell&#39;inventario del prodotto configurabile non riesce quando il database utilizza prefissi__
Il sistema ora aggiorna correttamente l&#39;inventario dei prodotti configurabili quando il database utilizza prefissi, evitando messaggi di errore e assicurando il salvataggio della quantità corretta. In precedenza, se il database utilizzava i prefissi, si verificava un errore durante il tentativo di salvare la quantità di magazzino per i prodotti semplici all’interno di un prodotto configurabile.
  _AC-10750 - [Problema GitHub](https://github.com/magento/magento2/issues/38045)_
* __La chiave Google google API non funziona durante l&#39;aggiunta della mappa con attributi__
Il sistema ora supporta la versione più recente dell’API di Google Maps 3.56, che consente agli utenti di aggiungere allo stage un blocco di contenuto Mappa dal menu PageBuilder senza riscontrare errori. In precedenza, gli utenti non potevano aggiungere un blocco di contenuto Mappa a causa di problemi di compatibilità con la versione dell’API Google Maps, causando un messaggio di errore &quot;si è verificato un errore&quot;.
  _AC-11593 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_
* __Impossibile creare la spedizione per l&#39;articolo dell&#39;ordine con più origini e SKU danneggiato__
In precedenza, quando gli spazi venivano aggiunti erroneamente nello SKU tramite database, si verificava un errore nella pagina di spedizione, che ora è fissa, e il ritaglio automatico viene considerato un errore di facile utilizzo e non è stato trovato alcun impatto. La spedizione è stata quindi creata correttamente.
  _AC-13922 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/c18eb5fa)_
* __[Test] prodotti del bundle con 0 inventario visualizzati nella vetrina__
Il prodotto del bundle non viene visualizzato sui siti web aggiuntivi utilizzando scorte aggiuntive.
  _ACP2E-1411_
* __[Cloud] problema critico con l&#39;elenco prodotti con spazi vuoti__
Ora il sistema visualizza correttamente gli elenchi dei prodotti senza spazi vuoti quando i prodotti sono impostati su &quot;esaurito&quot;, garantendo una visualizzazione coerente e accurata dei prodotti disponibili. In precedenza, se si impostava un prodotto su &quot;Esaurito&quot;, nell’elenco dei prodotti veniva visualizzato uno spazio vuoto, che causava interruzioni del layout e poteva confondere i clienti.
  _ACP2E-2794 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/b59e48ca)_
* __Impossibile spedire l&#39;ordine quando l&#39;archivio di ritiro MSI è abilitato__
Miglioramento delle prestazioni di inventario per creare la spedizione in caso di molte origini con prelievo in-store
  _ACP2E-3335 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_
* __La reindicizzazione Cron non riesce ad aggiornare la disponibilità del prodotto sul front-end__
In precedenza, i prodotti rimanevano esauriti sul front-end dopo l’aggiornamento dello stato dell’ordine arretrato tramite l’API REST. Ora, dopo aver aggiornato lo stato dell’ordine inevaso tramite l’API REST, i prodotti vengono visualizzati come in stock.
  _ACP2E-3355 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/e6fe0aa7)_
* __L&#39;aggiunta di immagini a configurabile non funziona quando MSI è abilitato.__
Il caricamento dell’immagine per il prodotto configurabile ora funziona come previsto quando si utilizza il modulo inventario. In precedenza, il caricamento dell’immagine non funzionava
  _ACP2E-3357 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/fdf409aa)_
* __Problema con il prodotto del bundle + MSI in Clean M2.4.7-p3__
In precedenza, per i prodotti bundle di inventario dopo la duplicazione con lo stesso prodotto semplice, il prodotto semplice non poteva essere salvato. Dopo l’applicazione di questa correzione, il prodotto semplice può essere salvato correttamente senza eccezioni.
  _ACP2E-3470 - [Problema GitHub](https://github.com/magento/magento2/issues/39358) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/0208e433)_

### Magazzino/MSI, Ricerca

* __Tutti i prodotti sono indicizzati con [is_out_of_stock] = 1 quando lo SKU non è impostato come attributo ricercabile__
Dopo la correzione, &quot;is_out_of_stock&quot; nell’indice di ricerca del catalogo è corretto, anche quando lo SKU non è ricercabile.
  _ACP2E-3413 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

### Ordine

* __Schermata di panoramica ordine back-end: quantità in inevaso non visibile a livello di articolo ordine__
Il sistema visualizza ora il numero di articoli in inevaso nella colonna quantità della schermata di panoramica dell’ordine backend. In questo modo gli utenti possono tenere traccia con precisione dello stato di tutti gli elementi di un ordine. In precedenza, la colonna Quantità mostrava solo il numero di articoli ordinati, fatturati e spediti, ma non il numero di articoli in inevaso.
  _AC-10828 - [Problema GitHub](https://github.com/magento/magento2/issues/38252) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38320)_
* __[Problema] ID archivio errato utilizzato nel modulo di rendering degli indirizzi dell&#39;ordine__
Il sistema ora utilizza correttamente l’ID store associato a un ordine durante il rendering dell’indirizzo dell’ordine, assicurandosi che gli indirizzi siano formattati correttamente in base al rispettivo ID store. In precedenza, il sistema utilizzava erroneamente l’ID store corrente, il che poteva causare una formattazione degli indirizzi errata nei casi in cui occorreva inviare più e-mail di ordine da diversi store.
  _AC-10994 - [Problema GitHub](https://github.com/magento/magento2/issues/38412) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37932)_
* __Problema di caching JoinProcessor__
Il sistema ora applica correttamente il JoinProcessor per ogni iterazione, anche con chiamate consecutive, garantendo un recupero accurato dei dati. In precedenza, JoinProcessor veniva erroneamente contrassegnato come già applicato in iterazioni consecutive, causando errori nel recupero dei dati.
  _AC-11690 - [Problema GitHub](https://github.com/magento/magento2/issues/27504) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37550)_
* __[Problema] Prezzo di spedizione diverso nel pdf stampato__
Il sistema visualizza correttamente i prezzi di spedizione nei PDF stampati in base alle impostazioni di configurazione delle imposte, garantendo la coerenza tra la pagina di visualizzazione della fattura dell&#39;ordine di vendita e la fattura stampata. In precedenza, il prezzo di spedizione visualizzato nel PDF stampato escludeva le imposte, indipendentemente dalle impostazioni di configurazione delle imposte.
  _AC-11798 - [Problema GitHub](https://github.com/magento/magento2/issues/38608) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38595) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bafc571)_
* __Riordina con un prodotto configurabile padre eliminato__
Ora durante il riordino con il prodotto eliminato il sistema non mostra il pulsante di riordino da riordinare
  _AC-13839 - [Problema GitHub](https://github.com/magento/magento2/issues/39568) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39601)_
* __[Problema] Correzione non valida \Magento\Sales\Model\Order\Email\Container\Template::$id, proprietà__
Questo risolve il problema phpdoc per \Magento\Sales\Model\Order\Email\Container\Template::$id, in realtà $id è type int ma in realtà è string.
  _AC-13924 - [Problema GitHub](https://github.com/magento/magento2/issues/39151) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39150)_
* __Impossibile salvare le modifiche al numero di telefono nei dettagli ordine esistenti__
Ora l&#39;utente può aggiungere il prefisso internazionale 00 nel campo telefono dell&#39;indirizzo ordine
  _ACP2E-2622 - [Problema GitHub](https://github.com/magento/magento2/issues/38201) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/12e071c3)_
* __Impossibile inviare le e-mail__
Il sistema ora include un’opzione di configurazione async_sending_attempted per specificare il numero di tentativi di invio di un’e-mail prima dell’arresto, migliorando la gestione degli invii di e-mail non riusciti quando &quot;Invio asincrono&quot; è abilitato. In precedenza, se l’invio di un’e-mail non riusciva, il sistema tentava continuamente di inviarla nuovamente, generando un ciclo infinito di messaggi di errore nel registro del sistema.
  _ACP2E-2734 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __[Cloud] Lo stato dell&#39;ordine è stato modificato in completo quando si effettua il rimborso parziale di un ordine spedito parzialmente__
Quando si emette una nota di accredito, lo stato dell&#39;ordine non viene più modificato in &quot;completato&quot; se sono presenti articoli non ancora spediti.
  _ACP2E-2756 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD] Non è in grado di disabilitare l&#39;invio di e-mail dall&#39;interfaccia utente di amministrazione come mostrato nei documenti di sviluppo__
Il sistema ora impedisce correttamente l’invio delle e-mail di vendita quando la comunicazione e-mail è disabilitata. Queste e-mail non verranno più inviate quando la comunicazione e-mail verrà riattivata. In precedenza, le e-mail di vendita avviate mentre la comunicazione e-mail era disabilitata venivano comunque inviate una volta riabilitata la comunicazione e-mail.
  _ACP2E-3002 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8931218)_
* __Ordine chiuso senza rimborso completo__
Il sistema ora gestisce correttamente lo stato dell&#39;ordine come &quot;Elaborazione&quot; e lo stato della fattura come &quot;In sospeso&quot; quando un ordine con un pagamento non acquisito presenta una spedizione creata. In questo modo gli ordini vengono contrassegnati come &#39;Chiusi&#39; solo dopo essere stati completamente rimborsati. In precedenza, la creazione di una spedizione per un ordine con una fattura in sospeso avrebbe erroneamente modificato lo stato dell’ordine in &quot;Chiuso&quot;.
  _ACP2E-3045 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* __[Cloud] Non è possibile creare l&#39;ordine nell&#39;amministratore in un archivio se non è stato impostato solo l&#39;indirizzo di fatturazione predefinito__
Ora il messaggio di errore rilevante &quot;Un cliente con lo stesso indirizzo e-mail esiste già in un sito web associato&quot;. viene visualizzato se un cliente non ha un indirizzo di fatturazione predefinito e tenta di creare un ordine in un altro negozio.
  _ACP2E-3311 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d75cff27)_
* __Inviate richieste di ordini di luogo duplicate dall&#39;amministratore__
In precedenza, il pulsante &quot;Invia ordine&quot; nel pannello di amministrazione poteva essere fatto clic più volte o attivato premendo ripetutamente il tasto &quot;Invio&quot;, causando invii duplicati o ordini con errore. Ora, impedendo ulteriori azioni fino a quando l’ordine non è completamente elaborato, garantendo che venga inviato un solo ordine.
  _ACP2E-3416 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __L&#39;amministratore può comunque ordinare anche senza metodo di pagamento__
Il metodo di pagamento selezionato in precedenza viene ora mantenuto quando il metodo di pagamento viene nuovamente visualizzato nell&#39;elenco dei pagamenti disponibili.
  _ACP2E-3425 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

### Ordine, Pagamenti

* __L&#39;amministratore può comunque ordinare anche senza metodo di pagamento__
In precedenza, il commerciante poteva effettuare ordini dal pannello di amministrazione senza selezionare un metodo di pagamento. Ora, il commerciante è richiesto un metodo di pagamento per procedere con l&#39;effettuazione di un ordine.
  _ACP2E-3233 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

### Ordine, restituzioni

* __Il rimborso dell&#39;ordine risulta in una nota di credito duplicata__
L’emissione del rimborso tramite API REST quando due richieste identiche sono state eseguite contemporaneamente non creerà più note di credito duplicate.
  _ACP2E-2982 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Ordine, imposta

* __[CLOUD] Base_row_total non corretta nell&#39;API dell&#39;ordine RESTFUL quando si abilitano transazioni transfrontaliere e si applicano sconti coupon__
Ora base_row_total corretta viene restituita dall’API dell’ordine RESTFUL quando è abilitata la transazione transfrontaliera e viene applicato lo sconto coupon.
  _ACP2E-3003 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9af794a4)_

### Altro

* Cookie __private_content_version restituito nelle query GQL__
È stato risolto un problema a causa del quale il cookie private_content_version veniva restituito nelle query GraphQL, anche quando il cookie di sessione era disabilitato. Il cookie non viene più incluso nelle risposte di GraphQL quando la sessione è disabilitata, come previsto.
  _LYNX-339_
* L&#39;attributo __is_available in CartItemInterface restituisce sempre false per i prodotti configurabili__
È stato risolto un problema a causa del quale l’attributo is_available in CartItemInterface restituiva sempre false per i prodotti configurabili in magazzino. Ora riflette correttamente la disponibilità come true quando applicabile.
  _LYNX-380_
* L&#39;attributo __is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto__
È stato risolto il problema a causa del quale l’attributo is_available in CartItemInterface restituiva erroneamente true anche quando la quantità dell’articolo del carrello superava le scorte vendibili.
  _LYNX-382_
* __Viene restituita la miniatura segnaposto quando un prodotto semplice viene aggiunto al carrello all&#39;interno di un prodotto raggruppato__
È stato risolto un problema a causa del quale l’aggiunta di un prodotto semplice (parte di un prodotto raggruppato) al carrello restituiva un’immagine miniatura segnaposto, anche quando al prodotto era assegnata un’immagine.
Dettagli correzione:
* Ora la miniatura del prodotto mostra correttamente l’immagine assegnata, se disponibile.
* La selezione delle miniature rispetta la configurazione di amministrazione in:
Negozi > Configurazione > Vendite > Pagamento > Carrello acquisti > Immagine prodotto raggruppato.
In questo modo si garantisce un comportamento coerente delle miniature per i prodotti raggruppati in base alle impostazioni dello store.
  _LYNX-399_
* __Gli attributi di opzione personalizzati del cliente non funzionano con valori interi__
È stato risolto un problema che impediva il funzionamento degli attributi di opzione personalizzati del cliente quando il valore restituito era un numero intero. Le opzioni personalizzate ora gestiscono e restituiscono correttamente i valori interi come previsto.
  _LYNX-400_
* __Errore interno del server durante il tentativo di ottenere priceDetails per i prodotti Bundle con prezzo dinamico__
È stato risolto un problema che causava un errore interno del server a causa della query di price_details per i prodotti bundle con prezzo dinamico tramite GraphQL. Questo miglioramento garantisce la stabilità delle query sul carrello quando si lavora con prodotti bundle configurati con prezzi dinamici.
  _LYNX-402_
* __only_x_left_in_stock restituisce sempre 0 per i prodotti configurabili__
È stato risolto un problema a causa del quale l’attributo only_x_left_in_stock restituiva sempre 0 per i prodotti configurabili quando aggiunti utilizzando lo SKU padre con le opzioni.
Dettagli correzione:
* Il valore only_x_left_in_stock ora riflette con precisione il materiale grezzo della variante figlio selezionata invece dello SKU padre.
* In questo modo i livelli delle scorte vengono visualizzati correttamente per le varianti di prodotto configurabili nel carrello e nelle pagine dei prodotti.
  _LYNX-403_
* __La query GraphQL non restituisce il prezzo normale calcolato corretto per i prodotti personalizzabili__
È stato risolto un problema a causa del quale GraphQL non restituiva il prezzo normale calcolato corretto per i prodotti personalizzabili. La query ora include correttamente il prezzo regolare calcolato con valori personalizzabili applicati (ad esempio, $ 125) nella proprietà price, che riflette sia il prezzo di base che eventuali costi di personalizzazione aggiuntivi.
  _LYNX-411_
* __Le imposte applicate tramite EstimatedTotals persistono con mutazioni aggiornate__
È stato risolto un problema relativo alla mutazione EstimatedTotals a causa del quale le imposte applicate persistevano su un carrello anche dopo l’aggiornamento del codice postale o dell’area geografica. La mutazione ora aggiorna correttamente le imposte applicate quando si cambia tra i valori di area e codice postale, garantendo che venga applicata solo la regola fiscale corretta in base ai dati del carrello correnti.
  _LYNX-412_
* L&#39;attributo __is_available in CartItemInterface restituisce true anche quando le scorte vendibili sono inferiori alla quantità del prodotto__
È stato risolto un problema a causa del quale l’attributo is_available in CartItemInterface restituiva erroneamente true anche quando le scorte vendibili erano inferiori alla quantità di prodotto richiesta. Il campo is_available ora restituisce correttamente false quando la quantità del prodotto supera le scorte disponibili.
  _LYNX-420_
* __Prezzo normale del prodotto con 12 decimali e valore errato__
È stato risolto un problema a causa del quale il valore regular_price nei percorsi GraphQL product.price_range.maximum_price e minimum_price non corrispondeva al prezzo del catalogo quando venivano applicate più aliquote fiscali. Il prezzo_regolare ora riflette in modo coerente il prezzo di catalogo in tutte le configurazioni di imposta, garantendo prezzi unitari accurati, calcoli del costo totale di riga e assegni di sconto nel Riepilogo carrello.
  _LYNX-425_
* __Errore del server GraphQL nel carrello con prodotto incluso esaurito__
È stato risolto un problema a causa del quale GraphQL restituiva un errore interno del server durante il recupero di un carrello contenente un prodotto in bundle con un articolo esaurito, in particolare quando la query includeva la proprietà itemsV2. GraphQL ora restituisce correttamente un elenco di elementi con messaggi di errore pertinenti associati alla voce dell’elemento del prodotto nel pacchetto, come previsto.
  _LYNX-430_
* __Impossibile creare un indirizzo con attributi personalizzati__
È stato risolto un problema relativo alla mutazione createCustomerAddress che impediva la creazione di indirizzi con gli attributi personalizzati richiesti. La mutazione ora gestisce correttamente gli attributi degli indirizzi personalizzati quando viene fornito il payload appropriato.
  _LYNX-441_
* __Errore del server GraphQL nel carrello con only_x_left_in_stock nel prodotto incluso__
È stato risolto un problema a causa del quale il recupero di un carrello contenente un prodotto in bundle con il campo only_x_left_in_stock nella query GraphQL generava un errore interno del server. GraphQL ora restituisce correttamente un valore float o null per il campo only_x_left_in_stock senza errori.
  _LYNX-447_
* __Errore GraphQL durante la rimozione di altri prodotti con prodotto configurabile insufficiente nel carrello__
È stato risolto un problema a causa del quale il tentativo di rimuovere i prodotti di magazzino dal carrello causava un errore GraphQL di tipo &quot;La quantità richiesta non è disponibile&quot; se il carrello conteneva anche prodotti configurabili con scorte insufficienti. La rimozione ora funziona come previsto senza errori di attivazione.
  _LYNX-464_
* __Impossibile aggiungere prodotti perché la mutazione SKU nella mutazione fa distinzione tra maiuscole e minuscole__
È stato risolto un problema a causa del quale la mutazione addProductsToCart restituiva un errore &quot;PRODUCT_NOT_FOUND&quot; quando si utilizzavano SKU con maiuscole e minuscole diverse. La mutazione ora gestisce gli SKU senza distinzione tra maiuscole e minuscole, garantendo la coerenza con le query di Catalog Service e il comportamento PDP.
  _LYNX-469_
* __Attributo prodotto > marchio di fabbrica formato breve &amp;trade; viene restituito come &amp;trade;__
È stato risolto un problema di codifica dei caratteri con il nome del prodotto per l’API GraphQL.
  _LYNX-603_
* __problema di mutazione di customerEmail__
È stato risolto un problema relativo alla mutazione updateCustomerEmail a causa del quale i clienti che non disponevano degli attributi personalizzati richiesti (aggiunti dopo la creazione dell’account) non potevano aggiornare l’e-mail.
  _LYNX-619_
* __Il set di mutazioni ShippingAddressesOnCart genera un errore quando si utilizza pickup_location_code__
È stato risolto un problema a causa del quale la mutazione setShippingAddressesOnCart restituiva un errore quando si utilizzava pickup_location_code senza specificare customer_address_id o address. La mutazione ora consente correttamente di impostare un indirizzo di spedizione con solo il codice pickup_location_code.
  _LYNX-626_
* __Compatibilità Storefront: aggiorna la logica per ottenere il nome della tabella con il prefisso e altri miglioramenti minori__
È stata aggiornata la logica per recuperare il nome della tabella con il prefisso (relativo alle modifiche SCP).
  _LYNX-637_
* __il salvataggio nella rubrica non funziona quando si utilizza il campo same_as_shipping di setBillingAddressOnCart GQL__
È stato risolto un problema a causa del quale l’indirizzo di spedizione non veniva salvato nella rubrica del cliente quando si utilizzava la mutazione GraphQL setBillingAddressOnCart con il campo same_as_shipping impostato su true. Ora l&#39;indirizzo di spedizione viene memorizzato correttamente come previsto.
  _LYNX-643_
* __Standarizzare order_id in mutazioni__
L’input order_id nelle mutazioni è stato standardizzato e il modello e-mail di conferma dell’annullamento dell’ordine è stato aggiornato in modo da esporre l’ID incremento invece dell’ID ordine.
  _LYNX-650_
* __CustomerOrder non visualizza i commenti dell&#39;ordine__
È stato risolto un problema relativo a CustomerOrder che consentiva di includere i commenti relativi agli ordini nelle query di GraphQL relative agli ordini dei clienti e dei clienti.
  _LYNX-651_
* __original_item_price non deve includere alcuno sconto__
È stata aggiornata la logica per original_item_price in GraphQL Cart Item price per escludere gli sconti.
  _LYNX-652_
* __Il bundle dei prodotti mostra ancora &quot;IN_STOCK&quot; quando uno dei suoi prodotti in bundle è esaurito__
È stato risolto un problema a causa del quale product.stock_status per i prodotti bundle mostrava ancora &quot;IN_STOCK&quot; anche quando uno degli articoli in bundle era esaurito.
  _LYNX-681_
* __la query del cliente restituisce un errore interno del server se per un cliente esiste un valore per l&#39;attributo personalizzato eliminato__
È stato risolto il problema a causa del quale la query del cliente restituiva un errore interno del server quando un attributo personalizzato eliminato aveva ancora un valore memorizzato. Ora, se viene richiesto un attributo non esistente, viene restituito un messaggio di errore corretto. La cache necessaria viene invalidata al momento dell’eliminazione dell’attributo personalizzato del cliente.
  _LYNX-686_
* __Parametro azione per i collegamenti di conferma di restituzione e annullamento__
È stato aggiunto un parametro di azione per i collegamenti correlati all’e-mail di conferma per restituzione e annullamento
  _LYNX-687_
* __L&#39;URL di conferma utente ospite viene reindirizzato alla pagina di stato dell&#39;ordine perché manca orderRef__
È stato aggiunto il parametro orderRef al collegamento nell’e-mail di conferma per l’annullamento dell’ordine dei clienti
  _LYNX-689_
* __Impossibile restituire null per il campo &quot;TaxItem.title&quot; non nullable in placeOrder GQL__
È stato risolto un problema che causava un errore interno del server a causa della mutazione placeOrder non riuscita a causa di un valore null per il campo TaxItem.title non nullable. Ora, il campo restituisce sempre un valore valido, garantendo il corretto inserimento dell’ordine.
  _LYNX-699_
* __EstimateTotals: sconti nulli per i tipi di prodotto virtuali__
È stato risolto il problema a causa del quale la mutazione estimateTotals restituiva un valore null per gli sconti quando un codice di sconto veniva applicato a un carrello contenente prodotti virtuali.
  _LYNX-702_
* __Il prodotto del bundle non restituisce la percentuale e l&#39;importo di sconto corretti__
Sono state introdotte nuove proprietà &quot;catalog_discount&quot; e &quot;row_catalog_discount&quot; per i prezzi degli articoli del catalogo, in modo da visualizzare gli importi e le percentuali di sconto corretti a livello di riga e di singolo articolo.
  _LYNX-703_
* __Configurazione del messaggio regalo a livello di prodotto__
È stato risolto un problema a causa del quale i messaggi regalo non venivano applicati a livello di prodotto quando era disabilitato a livello globale. Ora, se i messaggi regalo sono abilitati per un prodotto specifico, possono essere aggiunti correttamente utilizzando la mutazione updateCartItems e verranno salvati e riflessi correttamente.
  _LYNX-714_
* __la query cart.rules ha restituito un errore invece di un array vuoto se non sono applicate regole attive__
È stata corretta la query cart.rules che restituiva un array vuoto anziché un errore quando non venivano applicate regole attive per il carrello.
  _LYNX-757_
* __Le chiamate di GraphQL con il metodo OPTIONS restituiscono il codice di risposta 500 quando è installato il pacchetto di compatibilità adobe-commerce/storefront-compatibility__
È stato risolto un problema a causa del quale le chiamate di GraphQL eseguite con il metodo OPTIONS restituivano un errore interno del server 500 quando era installato il pacchetto di compatibilità adobe-commerce/storefront-compatibility. L’endpoint ora restituisce correttamente una risposta 200/204 come previsto.
  _LYNX-778_

### Altri strumenti per sviluppatori

* __[Problema] È stato corretto un errore di sintassi HTML in visual.phtml__
Il sistema ora chiude correttamente il tag di inizio nel file visual.phtml, garantendo la sintassi HTML corretta. In precedenza, il tag di inizio non veniva chiuso correttamente, causando un errore di sintassi HTML.
  _AC-10658 - [Problema GitHub](https://github.com/magento/magento2/issues/38247) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37457)_
* __[Problema] cambiato &quot;attivo&quot; in &quot;abilitato&quot; nel comando bin/magento maintenance:status__
Il sistema ora fornisce messaggi di stato più precisi per il comando della modalità di manutenzione, cambiando lo stato da &quot;attivo&quot; a &quot;abilitato&quot; e da &quot;non attivo&quot; a &quot;disabilitato&quot;. In precedenza, il messaggio di stato per il comando della modalità di manutenzione veniva visualizzato come &quot;attivo&quot; o &quot;non attivo&quot;, il che poteva creare confusione.
  _AC-11474 - [Problema GitHub](https://github.com/magento/magento2/issues/38486) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38410)_
* __La navigazione nella struttura delle categorie genera errori in Redis: &quot;La sessione di Redis ha superato le connessioni simultanee&quot;__
  _AC-12571 - [Problema GitHub](https://github.com/magento/magento2/issues/38851) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0611e750)_
* __Problemi CSP combinati con dev/css/use_css_critical_path__
Il sistema ora carica correttamente i file CSS in modo asincrono sulle pagine di pagamento, anche quando l’impostazione &quot;dev/css/use_css_critical_path&quot; è abilitata, garantendo che tali pagine vengano sottoposte a rendering con gli stili CSS appropriati. In precedenza, i criteri sulla sicurezza dei contenuti (CSP) con restrizioni impedivano l’esecuzione di JavaScript in linea, causando il mancato caricamento dei file CSS come previsto.
  _AC-12731 - [Problema GitHub](https://github.com/magento/magento2/issues/39020) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39040)_
* __Utilizzo del tipo virtuale per configurare il plug-in, impossibile generare correttamente il metodo intercettore nel comando `setup:di:compile`__
Il sistema ora genera correttamente i metodi intercettore quando si utilizza un tipo virtuale per configurare un plug-in, garantendo risultati coerenti sia in modalità precompilata che in modalità runtime. In precedenza, il sistema generava risultati errati se precompilato rispetto alla compilazione in fase di esecuzione.
  _AC-13398 - [Problema GitHub](https://github.com/magento/magento2/issues/33980) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38141)_
* __Impossibile eseguire gli unit test di Adobe Commerce 2.4.7-p3__
Non sono richieste note sulla versione.
  _ACP2E-3631 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Metodi di pagamento, ordine

* __Flusso di pagamento papale I dettagli della carta di credito salvati per un uso successivo non vengono visualizzati nella pagina del metodo di pagamento memorizzata__
Flusso di pagamento papale precedente I dettagli della carta di credito salvati per un uso successivo non venivano visualizzati nella pagina del metodo di pagamento memorizzato, che ora è fisso i dettagli della carta di credito vengono visualizzati nella pagina del metodo di pagamento memorizzato.
  _AC-13699 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Pagamenti

* __Il pagamento tramite carta di credito (Payflow Link) non funziona__
Precedente Ottenere errore (pagamento è stato rifiutato) durante il posizionamento dell&#39;ordine con carta di credito dopo la correzione Ordine effettuato correttamente.
  _AC-13414 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a68324bc)_
* __Payflow crea una nuova transazione ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione__
Il sistema ora recupera correttamente le informazioni sulle transazioni senza creare una nuova transazione di pagamento ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione. In precedenza, facendo clic sul pulsante Recupera, veniva erroneamente creata una nuova transazione di pagamento per un ordine già pagato.
  _ACP2E-2841 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __Il messaggio Paylater non viene visualizzato in PDP per l&#39;account esercente canadese Paypal__
Il sistema ora visualizza correttamente il messaggio PayLater per i conti commerciali PayPal canadesi sulla pagina Dettagli prodotto (PDP) quando il paese dell&#39;acquirente può essere determinato dall&#39;indirizzo di fatturazione o dalla spedizione del conto. In precedenza, il messaggio PayLater non veniva visualizzato a causa di un parametro mancante, causando un errore nella console del browser.
  _ACP2E-3028 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6a185204)_
* __Il rimborso dell&#39;ordine PayPal risulta in una nota di credito duplicata__
È stata corretta l&#39;emissione di note di credito create tramite IPN per il servizio di pagamento PayPal.
  _ACP2E-3143 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_
* __La regola del prezzo del carrello non funziona per Paypal__
L&#39;importo corretto viene visualizzato sul lato PayPal quando lo sconto è applicato per metodo di pagamento
  _ACP2E-3163 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_
* __[Cloud] Utenti con un ruolo specifico non possono accedere__
l&#39;utente amministratore con un ruolo che contiene solo l&#39;accesso alla sezione PayPal ora può accedere senza errori
  _ACP2E-3208 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/66dea0de)_

### Prestazioni

* __Problema impostazioni attributi prodotto predefiniti__
Il sistema ora consente agli utenti di deselezionare un’opzione predefinita per un attributo di prodotto, assicurandosi che l’attributo non abbia sempre un set predefinito. In precedenza, una volta impostato un valore predefinito per un attributo di prodotto, non era possibile deselezionarlo, in modo che l’attributo avesse sempre un valore predefinito.
  _AC-11932 - [Problema GitHub](https://github.com/magento/magento2/issues/38703) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_
* __[Problema] Pulizia del codice, aggiunta di un nuovo blocco di intestazione critico e spostamento di CSS critici prima delle risorse__
Il sistema ora include un nuovo blocco di testa critico e sposta CSS critico prima delle risorse, consentendo una maggiore personalizzazione e ottimizzazione delle prestazioni nel front-end. In precedenza, il CSS critico non veniva posizionato prima delle risorse, limitando le opportunità di personalizzazione e ottimizzazione.
  _AC-12000 - [Problema GitHub](https://github.com/magento/magento2/issues/38748) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35580)_
* __Interruzione della compilazione del tema quando l&#39;host Mysql contiene informazioni sulla porta__
Il sistema ora gestisce correttamente la configurazione host MySQL che include le informazioni sulle porte, garantendo la corretta compilazione del tema. In precedenza, la compilazione del tema non riusciva se la configurazione host MySQL nella connessione al database includeva informazioni sulla porta.
  _AC-12176 - [Problema GitHub](https://github.com/magento/magento2/issues/38799) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38842)_
* __Supporto per CommandLoaderInterface di Symfony in Magento CLI__
Questa modifica riduce i tempi di inizializzazione dell&#39;app Magento CLI consentendo l&#39;inizializzazione differita dei comandi fino al momento in cui sono necessari.
  _AC-13471 - [Problema GitHub](https://github.com/magento/magento2/issues/29266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29355)_
* __Problema di prestazioni durante il caricamento degli attributi del prodotto nelle regole del carrello__
Sono state migliorate le prestazioni delle query per le regole di vendita, da circa 150 ms a una cifra ms.
  _ACP2E-2494 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __Prestazioni indicizzazione parziale prezzo__
Le prestazioni di indicizzazione parziale del prezzo sono state migliorate ottimizzando alcune delle query di eliminazione utilizzate nel processo di indicizzazione.
  _ACP2E-2673 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ba25af8a)_
* __L&#39;ordine viene rifiutato durante la configurazione di più store quando si utilizza l&#39;elaborazione dell&#39;ordine asincrono + Termini e condizioni__
Gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati vengono ora elaborati.
Prima che venissero automaticamente rifiutati.
  _ACP2E-2850 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_
* __L&#39;esecuzione della chiamata API per il resto dell&#39;ordine richiede molto tempo__
Il sistema ora esegue la chiamata API Order Rest in un lasso di tempo ragionevole, migliorando le prestazioni durante il recupero di un numero elevato di ordini. In precedenza, l’esecuzione della chiamata API per il resto dell’ordine impiegava molto tempo, causando ritardi durante il recupero di un numero elevato di ordini.
  _ACP2E-2910 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/001e5188)_

### Prezzi

* __Magento2.4.6-p4 Ordine API semplice articolo mancante prezzo__
Il sistema ora visualizza correttamente il prezzo dei prodotti semplici quando viene eseguita una query tramite l’API dell’ordine, garantendo una rappresentazione accurata dei dati. In precedenza, il prezzo dei prodotti semplici veniva erroneamente visualizzato come zero nella risposta API.
  _AC-11810 - [Problema GitHub](https://github.com/magento/magento2/issues/38603)_
* __Errore di arrotondamento in centesimi nella regola del catalogo__
  _AC-13855 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/276e0acd)_

### Prodotto

* __I caratteri speciali nel nome configurabile del prodotto associato vengono convertiti in entità HTML.__
Il sistema ora mantiene correttamente i caratteri speciali nei nomi dei prodotti associati durante la modifica di un prodotto configurabile, impedendo che vengano convertiti in entità HTML. In precedenza, i caratteri speciali nei nomi dei prodotti associati venivano convertiti in entità HTML quando il prodotto configurabile veniva modificato.
  _AC-10535 - [Problema GitHub](https://github.com/magento/magento2/issues/38146) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38447)_
* __La funzione GetById di ProductRepository non crea la chiave cache corretta__
Il sistema ora crea correttamente una chiave cache nella funzione GetById del ProductRepository, indipendentemente dal fatto che l’ID archivio venga passato come stringa o come numero intero. In questo modo il prodotto viene recuperato dalla memoria nelle chiamate successive, migliorando le prestazioni. In precedenza, il sistema recuperava il prodotto dal database ogni volta che la funzione veniva chiamata, anche con gli stessi parametri, a causa di una creazione errata della chiave della cache.
  _AC-10947 - [Problema GitHub](https://github.com/magento/magento2/issues/38384) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38433)_
* __[Problema] [MFTF] Aggiunto AdminClickAddOptionForBundleItemsActionGroup__
Il sistema ora include AdminClickAddOptionForBundleItemsActionGroup, che migliora le funzionalità del pannello di amministrazione. In precedenza, questo gruppo di azioni non era disponibile.
  _AC-11992 - [Problema GitHub](https://github.com/magento/magento2/issues/30857) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30838)_
* __[Problema] È stato corretto l&#39;errore di battitura nel blocco PHPDoc__
Il sistema ora rimuove correttamente una variabile di riferimento sconosciuta in PHPDoc per la dichiarazione della variabile $helper, migliorando la chiarezza e la precisione del codice. In precedenza, questa variabile di riferimento sconosciuta in PHPDoc causava confusione e potenziali imprecisioni nel codice.
  _AC-13173 - [Problema GitHub](https://github.com/magento/magento2/issues/38961) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38940)_
* __[Problema]: è stato corretto il bundle interrotto e il layout delle pagine di prodotto scaricabili in Magento >= 2.4.7__
Il layout per le pagine di prodotti bundle e scaricabili è stato corretto, garantendo una visualizzazione coerente e corretta su tutti i dispositivi. In precedenza, in queste pagine si verificavano problemi di layout a causa di una ridisposizione del blocco multimediale di informazioni sul prodotto.
  _AC-13423 - [Problema GitHub](https://github.com/magento/magento2/issues/39403) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __AlertProcessor - Il #2 dell&#39;argomento ($storeId) deve essere di tipo int, stringa specificata__
Il sistema ora attiva correttamente le e-mail di avviso sul prodotto verificando che l’identificatore dello store sia del tipo di dati corretto. In precedenza, le e-mail di avviso sul prodotto non venivano inviate a causa di una mancata corrispondenza del tipo nell’identificatore dello store.
  _AC-5969 - [Problema GitHub](https://github.com/magento/magento2/issues/35602) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0574ac23)_
* La funzione addFilterToMap di __[Cloud] non funziona per alcune colonne__
Ora è possibile utilizzare il modulo personalizzato nella griglia dell’ordine. Errori precedenti durante l’utilizzo di un modulo personalizzato.
  _ACP2E-2944 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

### Promozione

* __Attributo cliente non visibile durante la creazione dell&#39;account dall&#39;invito__
Gli attributi del cliente sono disponibili durante la creazione dell’account da un invito.
  _ACP2E-2602 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/39d54c2d)_
* __Il codice coupon con limite Usi per coupon non viene rilasciato per il pagamento non riuscito. Annullamento ordine__
Il sistema ora aggiorna immediatamente gli utilizzi dei coupon quando un ordine viene creato o annullato e aggiunge gli utilizzi delle regole a una coda per evitare potenziali deadlock. In questo modo, viene rilasciato un codice coupon con un limite &quot;Usi per coupon&quot; che può essere riutilizzato in caso di annullamento di un ordine a causa di un pagamento non riuscito. In precedenza, il sistema non rilasciava il codice coupon per il riutilizzo in tali casi, causando un messaggio di errore che indicava che il codice coupon non era valido.
  _ACP2E-2627 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c971859e)_
* __[Cloud] Indicizzatore prodotto regola catalogo di reindicizzazione genera SQLSTATE[HY000]: errore generale: il server MySQL 2006 non è più disponibile.__
Il sistema ora gestisce correttamente il valore &quot;batchCount&quot; personalizzato nel file di.xml per &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, impedendo errori SQL come &quot;Errore generale: il server MySQL 2006 non è più disponibile&quot; durante la reindicizzazione dell’indicizzatore del prodotto Catalog Rule a causa di dimensioni batch errate in cataloghi di grandi dimensioni
  _ACP2E-2811 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __La regola di vendita con l&#39;attributo Passo Qtà sconto (X acquisto) causa l&#39;applicazione di altre regole__
La regola del prezzo del carrello non annulla le regole applicate in precedenza se la quantità del prodotto nel carrello non è sufficiente per applicare la regola.
  _ACP2E-3139 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d01ee51e)_
* __Emettere le regole di vendita con sconto importo fisso e &quot;Sconto quantità massima applicato a&quot;__
È stato risolto un problema relativo allo sconto sulle regole del carrello che si verifica quando lo sconto sull’importo fisso è configurato per essere applicato per una quantità limitata di prodotti e il carrello. In precedenza, il valore &quot;Sconto quantità massima viene applicato a&quot; veniva utilizzato per calcolare il prezzo dell’articolo corrente nel carrello, non solo per calcolare lo sconto della regola.
  _ACP2E-3332 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __Regole carrello &quot;Sconto importo fisso per intero carrello&quot;  L&#39;azione applica gli sconti in modo errato__
I codici coupon verranno convalidati correttamente, indipendentemente dalla maiuscola o dalla minuscola, se utilizzati per la creazione degli ordini dall’area di amministrazione. In precedenza, il codice del coupon non veniva convalidato se non corrispondeva esattamente alla lettera maiuscola del codice della regola del carrello configurato.
  _ACP2E-3349 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/581b7ef1)_
* __Nel back-end, i valori di archivio predefiniti per gli attributi di prodotto (anziché i valori di amministrazione previsti)__
Ora nel back-end vengono utilizzati i valori amministratore invece dei valori di archivio predefiniti per gli attributi del prodotto.
  _ACP2E-3374 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5184c067)_
* __Regole del carrello &quot;Sconto importo fisso per l&#39;intero carrello&quot; applica gli sconti in modo errato quando si aggiungono prodotti bundle__
Le regole del carrello a importo fisso non venivano applicate correttamente per i prodotti bundle. Ora, quando si calcola l&#39;importo dello sconto totale, vengono presi in considerazione i prodotti secondari del bundle, con conseguente calcolo dello sconto corretto.
  _ACP2E-3377 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_
* __Le Regole Di Prezzo Del Carrello Calcolano Erroneamente Lo Sconto__
Gli sconti sull&#39;importo fisso vengono ora calcolati correttamente. Prima della correzione, gli sconti sull&#39;importo fisso non venivano totalizzati correttamente per i prodotti bundle.
  _ACP2E-3403 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0b488dd1)_
* __Le categorie nidificate nelle condizioni della regola non vengono visualizzate__
È stato risolto un problema a causa del quale le categorie nidificate di livello 3 o categoria non venivano visualizzate nelle regole di marketing per la condizione categoria
  _ACP2E-3406 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_
* __usage_limit e uses_per_customer non vengono aggiornati nella tabella salesrule_coupon__
L’aggiornamento di Usi per coupon e Usi per cliente nella regola di prezzo del carrello ora influisce sui coupon generati automaticamente esistenti. In precedenza, i nuovi valori interessavano solo i nuovi coupon
  _ACP2E-3432 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/88660e79)_
* __La regola del prezzo del carrello non considera la categoria padre quando si utilizza la condizione &quot;è uguale o maggiore di&quot;.__
Le regole di prezzo del carrello ora considerano correttamente la categoria padre quando viene utilizzata in condizioni avanzate
  _ACP2E-3456 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/93359343)_
* __Calcolo sconto non valido con priorità__
Nel caso dell&#39;importo fisso applicato per l&#39;intero tipo di sconto del carrello, l&#39;importo non veniva calcolato correttamente per gli articoli del carrello già scontati da una promozione precedente. Ora, gli sconti sono correttamente sommati.
  _ACP2E-3463 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD] Il calcolo della spedizione non considera la regola del carrello acquisti__
Prima della correzione, una regola del carrello con condizione region non veniva applicata in modo coerente. Dopo la correzione, le regole del carrello con condizioni di area vengono applicate correttamente.
  _ACP2E-3472 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_
* __La condizione di SKU della regola del carrello non riesce per la fattura.__
Lo sconto sul prodotto del bundle con prezzo dinamico ora si riflette correttamente nella fattura. In precedenza, lo sconto non veniva riportato sulla fattura.
  _ACP2E-3491 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3f12d152)_
* __Valore di sconto errato quando più regole del prezzo del carrello vengono applicate contemporaneamente a prodotti scontati/a prezzi speciali__
Prima della correzione, l’importo fisso per le regole dell’intero carrello non veniva applicato correttamente se ne veniva applicato più di uno. Ora, le regole del carrello sconti per importo fisso vengono applicate correttamente.
  _ACP2E-3498 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### SEO

* __L&#39;aggiunta di riscritture URL con un accento causa un caricamento infinito__
Il sistema ora crea e funziona la riscrittura degli URL con accenti, impedendo il caricamento infinito durante il processo di salvataggio. In precedenza, l’aggiunta della riscrittura di un URL con un accento causava un problema di caricamento infinito.
  _AC-11907 - [Problema GitHub](https://github.com/magento/magento2/issues/38692) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44cef3a9)_
* __Riscrittura URL categoria errata in più store per categoria di terzo livello__
Genera riscritture URL corrette per gli elementi figlio con chiave URL con ambito personalizzato
  _ACP2E-2641 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_
* __I caratteri a byte doppio (caratteri speciali) nel campo Nome prodotto bloccano la creazione del prodotto nel back-end__
È stata aggiunta una nuova impostazione che consente di applicare o meno la traslitterazione all’URL del prodotto. L’impostazione è disponibile qui: Negozi > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca: &quot;Applica traslitterazione per URL prodotto&quot;
  _ACP2E-2770 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __Creazione di voci url_rewrite non corretta con più archivi in un gruppo di archivi__
Prima della correzione, era possibile generare riscritture URL solo a livello di sito web durante la modifica di un prodotto. Con la correzione, è stata introdotta una nuova impostazione (Stores > Configurazione > Catalogo > Catalogo > Ottimizzazione motore di ricerca, &quot;URL prodotto - Ambito di riscrittura&quot; con opzioni &quot;Visualizzazione archivio&quot;, &quot;Sito web&quot;) che consente di generare riscritture URL a livello di visualizzazione archivio o sito web.
  _ACP2E-3383 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2d627301)_

### Ricerca

* __Ricezione di &quot;Immetti un termine di ricerca e riprova&quot;. errore nella pagina di ricerca avanzata in storefront in 2.4.8-beta1__
Il sistema ora visualizza correttamente i risultati della ricerca nella pagina Ricerca avanzata quando un attributo di prodotto è impostato su &quot;No&quot;. In precedenza, se si impostava un attributo di prodotto su &quot;No&quot; e si eseguiva una ricerca, veniva visualizzato un messaggio di errore di tipo &quot;Inserisci un termine di ricerca e riprova&quot;.
  _AC-13053 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ea26621)_
* __magento/module-open-search dipende da branch opensearch-php inesistente__
  _AC-13721 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/05dc0bbf)_
* __tabella search_query di grandi dimensioni, con un impatto notevole sul front-end del tempo di caricamento__
È stato migliorato il tempo di caricamento della pagina nell’elenco delle ricerche. Prima della correzione, la pagina dell’elenco di ricerca subiva un ritardo a causa di una query non ottimizzata.
  _ACP2E-3362 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Sicurezza

* __[Problema] Carattere mancante CSP Paylater Popup__
Il sistema ora consente il caricamento del font &quot;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;&quot; senza violare la direttiva Content Security Policy, garantendo la corretta visualizzazione del Popup Paylater. In precedenza, il caricamento del font veniva rifiutato a causa di una violazione della direttiva Content Security Policy, causando problemi di visualizzazione con il Popup Paylater.
  _AC-11855 - [Problema GitHub](https://github.com/magento/magento2/issues/38624) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37401)_
* __[Problema] Aggiornamento del testo DOM js.js reinterpretato come HTML__
L’utilizzo di innerText evita il rischio di iniezioni di HTML, in quanto queste proprietà sfuggono automaticamente a qualsiasi carattere speciale di HTML nel testo fornito. Questa correzione, aiuta a prevenire le vulnerabilità cross-site scripting (XSS) trattando l’input come testo normale anziché come HTML interpretato.
  _AC-12035 - [Problema GitHub](https://github.com/magento/magento2/issues/38767)_
* __ReCaptcha V2 non viene visualizzato correttamente al momento dell&#39;estrazione per la lingua tedesca__
Precedentemente i recaptcha da sotto l&#39;indirizzo e-mail da checkout appaiono sformattati per le lingue con parole lunghe, come il tedesco. Dopo questo il recaptcha si presenta come tutti gli elementi recaptcha dal resto delle aree.
  _ACP2E-3273 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7377de59)_
* __Captcha all&#39;accesso come amministratore non richiede interazione per alcuni utenti__
ReCaptcha per l’accesso amministratore è convalidato come previsto
  _ACP2E-3300 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/8f64ab3c)_

### Spedizione

* __[Problema] È stato corretto un errore di battitura in tracking.phtml. Le funzioni JS sono state rinominate &quot;currier&quot; in &quot;carrier&quot;__
Il sistema ora utilizza correttamente il termine &quot;carrier&quot; invece del &quot;currier&quot; errato nelle funzioni del gestore JavaScript utilizzate nel modello di tracciamento degli ordini, garantendo una corretta denominazione delle funzioni e chiarezza del codice. In precedenza, veniva utilizzato il termine errato &quot;currier&quot;, che portava a una potenziale confusione e incoerenza nella base di codice.
  _AC-10757 - [Problema GitHub](https://github.com/magento/magento2/issues/34523) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33414)_
* __UPS REST &quot;Una spedizione non può avere come unità di misura KGS/IN, LBS/CM o OZS/CM&quot;__
Assicurati che le tariffe UPS siano visibili nel carrello e nel pagamento.
  _AC-11938 - [Problema GitHub](https://github.com/magento/magento2/issues/38618) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/493e01f5)_
* __[Problema] Correggere l&#39;ortografia delle variabili per l&#39;indirizzo del cliente__
Il sistema ora scrive correttamente le variabili per gli indirizzi dei clienti, garantendo una visualizzazione accurata nell’area conto del front-end. In precedenza, l’ortografia errata di queste variabili poteva causare errori durante le revisioni del codice locale.
  _AC-13172 - [Problema GitHub](https://github.com/magento/magento2/issues/32817) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32815)_
* __Finestra di tracciamento che mostra una data di consegna prevista errata__
Visualizza la data di consegna corretta per il gestore Fedex.
  _ACP2E-2738 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_
* __Le Tariffe Delle Tabelle Sono Ancora Visibili Anche Se È Applicata La Spedizione Gratuita__
Il metodo di spedizione Tariffa tabella ora viene visualizzato anche se la spedizione gratuita diventa disponibile dopo l&#39;applicazione del coupon
  _ACP2E-2763 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b2286ecf)_
* __Test MFTF AdminCreatingShippingLabelTest non riuscito a causa di credenziali non aggiunte nell&#39;ambiente Jenkins__
correzione test mftf
  _ACP2E-2765 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_
* __L&#39;API Track FedEx non funziona con le credenziali REST__
In precedenza, l’integrazione FedEx non richiedeva chiavi API aggiuntive per l’API di tracciamento. Ora è stata aggiunta una nuova configurazione per supportare le chiavi API di tracciamento.
  _ACP2E-3340 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Tariffe negoziate FedEx di Cloud] non restituite su REST__
Prima della correzione, i tassi specifici dell’account FedEx non venivano inviati nella risposta, anche attraverso la documentazione FedEx che avrebbe dovuto essere inviata. Dopo la correzione, i tassi specifici dell’account vengono inviati alla risposta modificando la richiesta dal nostro lato.
  _ACP2E-3354 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Staging e anteprima

* __Impossibile aggiornare l&#39;aggiornamento pianificato quando si utilizza un attributo di categoria personalizzato univoco__
È stato risolto un problema che impediva l’aggiornamento pianificato di una categoria se questa aveva un attributo univoco
  _ACP2E-3453 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Targeting

* __[Problema] Consenti l&#39;utilizzo di intervalli CIDR nell&#39;elenco consentiti di manutenzione__
Il sistema ora supporta l’utilizzo di intervalli CIDR nella modalità di manutenzione elenco Consenti IP, consentendo a un intervallo di indirizzi IP di ignorare la modalità di manutenzione. In precedenza, la modalità di manutenzione Consenti elenco IP consentiva solo a singoli indirizzi IP di ignorare la modalità di manutenzione.
  _AC-9432 - [Problema GitHub](https://github.com/magento/magento2/issues/37943) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30699)_

### Imposta

* __[Problema] Promozione della proprietà del costruttore di funzionalità/php8.1 con grafico SQL__
Sostituisci quasi tutte le proprietà con la promozione della proprietà del costruttore nel modulo wee graph ql:
  _AC-13295 - [Problema GitHub](https://github.com/magento/magento2/issues/39309) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36975)_
* __FPT (Fixed Product Tax) non funziona con prodotti configurabili__
FPT per varianti di prodotto configurabili che funzionano correttamente.
  _ACP2E-3193 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Framework di test

* __Test di integrazione non riuscito per testDbSchemaUpToDate a causa del tipo di colonna JSON__
Il sistema ora riconosce correttamente i tipi di colonna JSON nello schema del database durante gli integration test, impedendo gli errori dei test a causa di una mancata corrispondenza tra lo schema del database e lo schema dichiarativo. In precedenza, il sistema identificava erroneamente i tipi di colonna JSON come LONGTEXT in MariaDB, causando l’errore dei test di integrazione.
  _AC-11654 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef81f5a2)_
* __[Problema] ortografia correzione PHPDoc__
Il sistema ora riconosce correttamente i metodi obsoleti nelle IDE a causa di una correzione ortografica nel PHPDoc. In precedenza, un errore ortografico nel PHPDoc causava il mancato riconoscimento da parte degli IDE di alcuni metodi come obsoleti.
  _AC-13362 - [Problema GitHub](https://github.com/magento/magento2/issues/31399) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31398)_
* __MAGETWO-95118: controllo del comportamento con il carrello permanente dopo la scadenza della sessione__
  _AC-13478 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7d5e3906)_
* __Correggi i test statici per abilitare l&#39;utilizzo da parte di estensioni di terze parti__
  _AC-13848 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9e383b4d)_
* __[Errore interno] di applicazione della correzione non visualizzato durante l&#39;esecuzione o nei registri__
&quot;-
  _ACP2E-3334 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d4de4726)_
* __[MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPriceTest__
Mftf fissi
  _ACP2E-3458 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Framework interfaccia utente

* __Correzione di vulnerabilità di sicurezza di Prototype.js CVE-2020-27511__
Il sistema è stato aggiornato per risolvere la vulnerabilità di sicurezza CVE-2020-27511 in Prototype.js 1.7.3, migliorando la sicurezza complessiva del sistema. Prima di questo aggiornamento, il sistema era suscettibile a un’espressione regolare Denial of Service (ReDOS) attraverso la rimozione di tag HTML creati.
  _AC-12128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Grunt Less utilizza il prefisso pub/ per sourcemaps__
Il sistema ora genera meno mappe sorgente/css senza il prefisso /pub per i percorsi quando si utilizza grunt, eliminando la necessità di una soluzione alternativa nella configurazione del server web. In precedenza, l’utilizzo del prefisso /pub nei percorsi sourcemaps richiedeva una configurazione specifica nel server web per funzionare correttamente.
  _AC-12189 - [Problema GitHub](https://github.com/magento/magento2/issues/38837) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38840)_
* __Campo File Componente Interfaccia Utente__
Il sistema ora convalida correttamente il campo file in un modulo componente dell’interfaccia utente, consentendo l’invio del modulo senza errori quando viene selezionato un file. In precedenza, la convalida non riusciva anche quando veniva selezionato un file, impedendo l’invio del modulo.
  _AC-12432 - [Problema GitHub](https://github.com/magento/magento2/issues/38908) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39004)_
* __[Problema] Formato data migliorato nella console js: passa da 12 ore a 24 ore dopo...__
Formato data migliorato nella console js: passa da 12 ore a 24 ore
  _AC-12645 - [Problema GitHub](https://github.com/magento/magento2/issues/38983) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38972)_
* __[Problema]: aggiunta della generazione sourceMap per un numero inferiore di file in modalità sviluppatore__
Il sistema ora genera mappe sorgente per un numero minore di file in modalità sviluppatore, semplificando l&#39;identificazione dell&#39;origine di uno stile. In precedenza, identificare la sorgente di uno stile era difficile quando si eseguiva il sistema in modalità sviluppatore con compilazione senza lato server.
  _AC-12650 - [Problema GitHub](https://github.com/magento/magento2/issues/38982) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38977)_
* __È in corso la distribuzione del contenuto statico per i moduli disabilitati__
Il sistema ora esclude i CSS relativi ai moduli disabilitati dai file di output CSS finali, garantendo che non vengano caricati stili non necessari. In precedenza, i CSS relativi ai moduli disattivati venivano inclusi nei file di output CSS finali, determinando il caricamento di stili aggiuntivi e non necessari.
  _AC-1306 - [Problema GitHub](https://github.com/magento/magento2/issues/24666) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32922)_
* __Comportamento incoerente nell&#39;ordinamento &quot;esaurito&quot; con soglia minima di scorte__
Il sistema ora ordina correttamente i prodotti nel catalogo in base ai livelli di stock, rispettando la soglia di stock minima impostata e spostando in modo coerente gli articoli esauriti nella parte inferiore dell’elenco. In precedenza, il comportamento di ordinamento era incoerente: gli elementi non venivano sempre visualizzati nell’ordine corretto in base ai livelli di stock e le modifiche nell’ordinamento potevano verificarsi in modo imprevedibile dopo il salvataggio, l’aggiornamento o la modifica della gerarchia di categorie.
  _AC-13459 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47b448e2)_
* __Suggerimenti per migliorare la segnalazione degli errori per i problemi di caricamento di require.js__
Questa PR migliora il messaggio di errore quando i requisiti non riescono a caricare un componente.
  _AC-13472 - [Problema GitHub](https://github.com/magento/magento2/issues/36761) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38971)_
* __Errori di deprecazione di PHP 8.4 che causano errori di compilazione in 2.4-development__
  _AC-14004 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_
* __[Problema] Non caricare il contesto del blocco di back-end in front-end__
Il sistema ora assicura che il contesto del blocco back-end non venga caricato sul front-end, impedendo la creazione di sessioni backend non necessarie e potenziali blocchi di sessione. In precedenza, il sistema caricava erroneamente il contesto del blocco back-end sul front-end, determinando la creazione di sessioni back-end e potenziali blocchi di sessione.
  _AC-9007 - [Problema GitHub](https://github.com/magento/magento2/issues/37617) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36368)_
* __[Problema] Rimuovi riepilogo di revisione degli script non necessari__
Il sistema ora ottimizza il tempo di caricamento delle pagine rimuovendo gli script JavaScript non necessari dalla sezione di valutazione, invece di utilizzare gli stili CSS in linea per un codice più efficiente e leggibile. In precedenza, l’utilizzo di script JavaScript per la sezione di valutazione poteva potenzialmente rallentare il tempo di caricamento delle pagine.
  _AC-9168 - [Problema GitHub](https://github.com/magento/magento2/issues/37776) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/34643)_
* __Eccezione durante la verifica del saldo di una gift card quando Recaptcha è abilitato__
Gli utenti potranno recuperare il saldo della gift card nella schermata Visualizza e modifica carrello. In precedenza, questi dettagli non venivano visualizzati quando reCAPTCHA era abilitato.
  _ACP2E-2529 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_
* __[CHIARIMENTO] Richiesta di funzionalità Conformità ADA__
Il sistema ora garantisce la conformità ADA rimuovendo le proprietà CSS non supportate e sostituendole con quelle supportate nel file print.css. In precedenza, l’utilizzo di proprietà CSS non supportate causava problemi di compatibilità con il browser.
  _ACP2E-2729 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/57a32313)_
* __[Cloud] Codice libreria di confusione in effect-drop.js di AC 2.4.4-p8__
Il sistema ora implementa correttamente la libreria effect-drop.js, garantendo il corretto funzionamento degli effetti dell’interfaccia utente jQuery. In precedenza, la libreria effect-drop.js veniva erroneamente sovrascritta con la libreria effect-clip.js, causando potenziali problemi con gli effetti dell’interfaccia utente jQuery.
  _ACP2E-3061 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/35b1b1da)_
* __Intestazione sito | Caratteri speciali che interrompono la sezione di benvenuto del cliente__
Dopo la correzione, i caratteri speciali vengono visualizzati correttamente nella sezione di benvenuto del cliente.
  _ACP2E-3367 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1366ae5e)_
* __L&#39;edizione del segmento cliente ha esito negativo con l&#39;intervallo di dati__
È possibile salvare il segmento del cliente con la condizione Intervallo date, quando è stata modificata solo una delle date.
  _ACP2E-3561 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

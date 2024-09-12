---
source-git-commit: cd4655cf45df5293ef82a9fa2f411e8630524603
workflow-type: tm+mt
source-wordcount: '13175'
ht-degree: 0%

---
# Problemi risolti dal Magento Open Source (v2.4.8-beta1)

## Problemi risolti

Sono stati risolti 253 problemi nel codice core del Magento Open Source 2.4.8. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

* _AC-10042_: /V1/transaction L&#39;API REST restituisce un errore quando parent_txn_id = txn_id
   * _Correzione nota_: il sistema ora gestisce correttamente le transazioni di concetto padre e figlio in cui l&#39;ID della transazione padre è uguale all&#39;ID della transazione, impedendo un ciclo infinito durante la query dell&#39;endpoint REST API /V1/transaction. In precedenza, questo scenario generava un errore irreversibile dovuto al superamento del tempo massimo di esecuzione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] problema di tipo in 2.4.7
   * _Correzione nota_: il sistema ora gestisce correttamente i valori interi nella funzione GetCustomSelectedOptionAttributes durante l&#39;esecuzione di una query GraphQL, evitando errori relativi al tipo. In precedenza, l&#39;avvio di una query GraphQL che utilizzava GetCustomSelectedOptionAttributes con un argomento Integer generava un errore di tipo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38663>
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

### Account

* _AC-10782_: il modulo Indirizzo cliente consente l&#39;utilizzo di codice casuale nei campi del nome
   * _Correzione nota_: il sistema ora convalida l&#39;input nei campi Nome e Cognome nel modulo dell&#39;indirizzo del cliente, impedendo l&#39;utilizzo di codice casuale. In precedenza, il sistema consentiva l’utilizzo di codice casuale in questi campi senza generare un errore.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: arresto anomalo del mio account durante il salvataggio
   * _Correzione nota_: il sistema ora salva correttamente gli indirizzi dei clienti anche quando il campo dell&#39;area non è visualizzato, impedendo un arresto anomalo durante il processo di salvataggio. In precedenza, se si tentava di aggiungere o modificare un indirizzo senza un campo area visualizzato, si verificava un errore di eccezione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38406>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Amministratore: pulsanti Azioni pagina mobili a sinistra anziché a destra
   * _Correzione nota_: il sistema ora allinea correttamente i pulsanti Azioni pagina al lato destro dell&#39;intestazione fissa nel pannello di amministrazione, migliorando l&#39;aspetto professionale. In precedenza, questi pulsanti si spostavano erroneamente sul lato sinistro dell’intestazione fissa.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: errore dev:di:info in magento 2.4.7
   * _Correzione nota_: i parametri del costruttore vengono ora visualizzati correttamente durante l&#39;esecuzione del comando dev:di:info, evitando il verificarsi di errori. In precedenza, l’esecuzione di questo comando generava un errore a causa di una mancata corrispondenza del tipo nell’argomento.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: il cliente ha eseguito l&#39;accesso ma visualizza l&#39;errore 404 in front-end.
   * _Correzione nota_: la pagina della dashboard del cliente storefront ora viene caricata come previsto quando un cliente effettua l&#39;accesso. In precedenza, i clienti potevano accedere, ma questa pagina mostrava un errore 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: impossibile salvare le informazioni sugli attributi del cliente nella sezione del cliente Admin Edit;
   * _Correzione nota_: l&#39;ID archivio del cliente è ora implementato correttamente per ambito sito Web per il modulo di modifica clienti amministratore.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### Interfaccia utente amministratore

* _AC-11588_: la convalida dei dati ha esito positivo e il pulsante Importa è presente durante l&#39;importazione di prodotti con il comportamento Sostituisci
   * _Correzione nota_: il sistema ora convalida correttamente i dati e nasconde il pulsante &quot;Importa&quot; durante il processo di importazione del prodotto con il comportamento &quot;Sostituisci&quot;, impedendo qualsiasi sostituzione involontaria dei dati. In precedenza, il sistema convalidava i dati in modo errato e visualizzava il pulsante &quot;Importa&quot;, causando potenziali incongruenze nei dati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Il Magento 2.4.7 non consente foto del prodotto con estensione maiuscola.
   * _Nota corretta_: il sistema ora accetta caricamenti di immagini di prodotto con estensioni di file in maiuscolo, garantendo un processo di creazione del prodotto fluido. In precedenza, i caricamenti di immagini con estensioni di file in maiuscolo venivano rifiutati, costringendo gli utenti a cambiare l’estensione del file in minuscolo.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38831>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-7700_: [Problema] Eliminare le tabelle del registro modifiche dell&#39;indicizzatore all&#39;annullamento dell&#39;abbonamento a mview
   * _Correzione nota_: il sistema rimuove automaticamente le tabelle del registro modifiche non utilizzate quando un indice viene cambiato da &quot;aggiorna secondo pianificazione&quot; a &quot;aggiorna al salvataggio&quot;, contrassegnando l&#39;indice come non valido per garantire che non vengano perse voci. In precedenza, il passaggio di un indice a &quot;aggiorna al salvataggio&quot; lasciava le tabelle del registro modifiche inutilizzate nel sistema e contrassegnava tutti gli indici modificati come &quot;validi&quot;.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29789>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-phrase interrompe l&#39;integrità delle traduzioni
   * _Correggi nota_: il comando `bin/magento i18n:collect-phrases -o` raccoglie e aggiunge correttamente nuove frasi dai file JavaScript e .phtml, garantendo che le traduzioni vengano riflesse correttamente nel file di traduzione. In precedenza, il sistema non era in grado di includere frasi di traduzione multilinea da file JavaScript e frasi da file .phtml nel file di traduzione, il che portava a traduzioni incomplete o errate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: il nome dell&#39;apostrofo nella visualizzazione punto vendita è sostituito da &#39;
   * _Correzione nota_: i filtri di visualizzazione archivio della griglia ora visualizzano correttamente gli apostrofi
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38395>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: il caricamento Favicon non riesce a convalidare i file .ico
   * _Correzione nota_: l&#39;errore di convalida del file è stato aggiornato a &quot;Convalida del file non riuscita. Verifica le impostazioni di elaborazione delle immagini nella configurazione dell&#39;archivio.&quot; In precedenza, si trattava semplicemente di &quot;Convalida file non riuscita&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: nella raccolta di PageBuilder viene visualizzata la miniatura dell&#39;immagine precedente invece dell&#39;immagine appena caricata
   * _Correzione nota_: rigenera anteprime immagini per le immagini eliminate e ricaricate con lo stesso nome tramite la raccolta multimediale nel contenuto del Page Builder.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: il salvataggio di un prodotto da parte di un utente amministratore con ambito ruolo diverso sovrascrive/elimina le informazioni di prodotto correlate esistenti nel prodotto
   * _Nota sulla correzione_: in precedenza, prima della correzione, i prodotti correlati venivano reimpostati e diventavano vuoti quando l&#39;utente amministratore secondario faceva clic sul pulsante Salva senza modificare il prodotto correlato. Dopo questa correzione, l’utente amministratore secondario fa clic sul pulsante Salva e il prodotto non viene reimpostato e salvato correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: impossibile esportare più di 200 ordini
   * _Correzione nota_: i limiti del server per la dimensione della richiesta degli ID selezionati inviati in precedenza sono stati ignorati modificando la richiesta HTTP da GET a POST per risolvere il problema. In precedenza, a causa delle limitazioni del server per la dimensione della richiesta di GET, si verificava il problema.
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

### Interfaccia utente amministratore, Prestazioni

* _ACP2E-3169_: dopo l&#39;aggiornamento a 2.4.5-p8 si verificano 500 errori durante la creazione dell&#39;ordine dall&#39;amministratore
   * _Correzione nota_: in precedenza, quando si abilitava la minimizzazione di HTML, non era possibile effettuare un ordine dall&#39;amministratore. Ora, con la minimizzazione di HTML abilitata, l’ordine dall’amministratore può essere effettuato correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Interfaccia utente amministratore, Spedizione

* _ACP2E-2519_: il conteggio dei codici coupon non viene aggiornato in   &quot;Tempo utilizzato&quot; nella scheda Gestisci codici coupon se un ordine viene effettuato con la spedizione multipla.
   * _Correzione nota_: in precedenza, quando un ordine era stato effettuato con spedizione multipla, il conteggio del codice coupon non veniva aggiornato nella colonna &quot;Tempo utilizzato&quot; della scheda Gestisci codici coupon. Ora, il conteggio corretto viene visualizzato in entrambi i &quot;Tempo utilizzato&quot; che riflettono i valori desiderati con la spedizione multipla.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### Analytics/Generazione rapporti

* _ACP2E-2570_: il report preliminare non funziona
   * _Correzione nota_: il sistema ora supporta la generazione di file di dati di Advanced Reporting per set di dati di dimensioni eccessive caricando e scrivendo report in batch di 10.000. In precedenza, il modulo di reporting avanzato non era in grado di generare file di dati per set di dati di dimensioni eccessive, causando errori di tipo &quot;MySQL Server has gone away&quot; durante l’esecuzione del processo analytics_collect_data cron.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: problema di visibilità dell&#39;intervallo di date del rapporto Prodotti ordinati dall&#39;amministratore.
   * _Correzione nota_: l&#39;utente potrà selezionare una data qualsiasi dal report prodotti ordinati. In precedenza, dopo l’aggiornamento di una tabella, selezionando la data &quot;DA&quot; si reimpostava la data &quot;A&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: intestazioni curl non corrette che impediscono il funzionamento di newrelic:create:deploy-marker
   * _Correzione nota_: il sistema ora formatta correttamente le intestazioni curl, consentendo al comando newrelic:create:deploy-marker di creare correttamente un marcatore di distribuzione in New Relic. In precedenza, intestazioni curl errate impedivano la creazione di un marcatore di distribuzione in New Relic.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37641>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Analytics/Reporting, B2B

* _ACP2E-2300_: B2B - la mappa del sito include prodotti/categorie non assegnati al catalogo condiviso
   * _Correzione nota_: limita le categorie e i prodotti generati da sitemap alle categorie e ai prodotti assegnati solo al catalogo condiviso pubblico e/o all&#39;impostazione delle autorizzazioni per le categorie di catalogo.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Reporting, cloud

* _ACP2E-3067_: il Magento elimina la maggior parte delle transazioni New Relic cron #34108
   * _Nota corretta_: AC sta segnalando correttamente le transazioni relative al processo cron a NewRelic. In precedenza, alcune transazioni relative a lavori cron venivano indicate come &quot;OtherTransaction/Action/unknown&quot; in NR
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_: bordi non necessari nella sezione Ordini personali
   * _Correzione nota_: in precedenza era stato creato un contenitore aggiuntivo (riferimenti ordine) che applicava classi CSS aggiuntive, causando la visualizzazione di linee di bordo non necessarie sotto il numero ordine nella sezione Ordini personali, che ora non è visibile.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Framework

* _AC-9607_: Il Filtro Della Griglia Aziendale E Il Tentativo Di Esportazione CSV Della Griglia Non Riusciranno E Genereranno Un&#39;Eccezione
   * _Correzione nota_: il sistema ora consente l&#39;esportazione CSV dei dati della griglia Aziende nel pannello di amministrazione, anche quando vengono applicati filtri come &quot;Saldo in sospeso&quot; e &quot;Tipo di società&quot;. In precedenza, l’applicazione di determinati filtri e il tentativo di esportare i dati della griglia generavano un errore e un’eccezione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_: pagamento tramite LPM
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_: configurabile con prodotto virtuale come secondario
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: errore di verifica CVV non riuscita
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_: archiviazione tramite l&#39;area dell&#39;account problemi 247
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_: invia a un indirizzo di un altro paese
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_: carta di credito - funzione Teardown
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_: richiamata di spedizione per PayPal Express
   * _Contributo codice GitHub_: <https://github.com/magento/ext-braintree/pull/204>

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
* _AC-11876_: [Problema] Regressione delle regole di vendita nella versione 2.4.7
   * _Correzione nota_: il sistema ora convalida correttamente le regole di vendita, impedendo l&#39;applicazione di un codice coupon a un carrello quando la condizione del prodotto non corrisponde ad alcun nome di prodotto. In precedenza, era possibile applicare una regola di vendita e applicare uno sconto sull’importo della spedizione anche quando la condizione del prodotto non corrispondeva a nessun nome di prodotto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38671>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_: [Problema] Il caricatore blocca i metodi di spedizione dopo la modifica del codice postale e le regole di convalida delle tariffe di spedizione
   * _Correzione nota_: il sistema ora gestisce correttamente i metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione, assicurandosi che il caricatore non blocchi i metodi di spedizione dopo la modifica del codice postale nell&#39;indirizzo di spedizione durante l&#39;estrazione. In precedenza, la modifica del codice postale nell’indirizzo di spedizione durante il pagamento causava il blocco dei metodi di spedizione da parte del caricatore, che non scompariva quando venivano utilizzati metodi di spedizione personalizzati senza regole di convalida delle tariffe di spedizione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38742>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: la funzionalità del codice coupon non funziona correttamente nella pagina di pagamento del Magento 2.4.7
   * _Correzione nota_: il sistema ora abilita il campo di input del codice sconto/coupon nella pagina di pagamento per i prodotti virtuali e scaricabili, consentendo agli utenti di applicare i codici sconto come previsto. In precedenza, l’input del codice sconto/coupon veniva disattivato e il testo del titolo del pulsante visualizzato come &quot;Annulla coupon&quot;, impedendo agli utenti di applicare codici sconto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38826>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
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
* _ACP2E-2704_: impossibile inviare il cookie. Dimensione dei &#39;messaggi-immagine&#39; durante il tentativo di riordinare
   * _Correzione nota_: il processo di riordinamento non genererà più i propri errori. Si baserà sull&#39;elenco del carrello assegni articoli incorporati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: l&#39;indirizzo di spedizione predefinito non è selezionato al momento dell&#39;estrazione
   * _Correzione nota_: l&#39;evento di selezione dell&#39;indirizzo di spedizione predefinito è in corso nel contesto della ricerca degli indirizzi abilitata.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [Problema API addProductsToCart graphql di CLOUD] con opzione personalizzata
   * _Correzione nota_: GraphQL aggiunge correttamente al carrello lo stesso prodotto con opzioni personalizzate diverse
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: più indirizzi aggiunti all&#39;account al momento dell&#39;estrazione come nuovo cliente
   * _Correzione nota_: il sistema ora salva un nuovo indirizzo del cliente una sola volta se l&#39;ordine non è stato creato, impedendo la creazione di più indirizzi identici in caso di errori di inserimento dell&#39;ordine. In precedenza, il sistema salvava un nuovo indirizzo ogni volta che veniva effettuato un tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine fosse stato creato correttamente o meno.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: il riordinamento dell&#39;ordine cliente tramite il modulo d&#39;ordine ospite genera un carrello vuoto
   * _Correzione nota_: in precedenza, quando si effettuava un riordino tramite la pagina Ordini e restituzioni, il cliente veniva reindirizzato alla pagina di accesso. Dopo l’applicazione di questa correzione, il cliente registrato viene reindirizzato correttamente alla pagina Visualizza carrello al momento del riordino. Il flusso funziona come i clienti guest.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: l&#39;utente amministratore con risorse ruolo limitate non è in grado di visualizzare i carrelli acquisti
   * _Correzione nota_: in precedenza, l&#39;amministratore con restrizioni non poteva visualizzare il carrello abbandonato dal pannello di amministrazione per un sito Web associato. Dopo aver applicato questa correzione, l’amministratore con restrizioni può visualizzare il carrello abbandonato dal pannello di amministrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>

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
* _AC-12076_: [Problema] Correzione del testo dell&#39;elemento filtro nella navigazione a livelli
   * _Correzione nota_: il sistema ora utilizza correttamente le parole &quot;item&quot; e &quot;items&quot; nell&#39;elemento del filtro di navigazione con livelli, migliorando la chiarezza e la precisione delle descrizioni del filtro. In precedenza, queste parole venivano utilizzate in modo errato, generando potenziale confusione per gli utenti che navigavano nelle opzioni del filtro.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: il formato di data e ora per l&#39;opzione personalizzata non funziona
   * _Correzione nota_: il sistema ora applica correttamente il formato data configurato alle opzioni personalizzate del prodotto di tipo Data, garantendo che il formato data venga visualizzato correttamente nel front-end. In precedenza, le modifiche alla configurazione del formato della data non venivano applicate al front-end per le opzioni personalizzate del prodotto di tipo Data.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38925>
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
* _ACP2E-3100_: [Il file di immagine Cloud] non esiste nel registro errori di New Relic
   * _Correzione nota_: il sistema ora sincronizza le immagini segnaposto personalizzate con l&#39;archiviazione locale, assicurandosi che vengano riprodotte correttamente quando si utilizza l&#39;archiviazione remota, ad esempio AWS S3. In precedenza, il rendering delle immagini segnaposto personalizzate non riusciva quando si utilizzava l’archiviazione remota, causando una visualizzazione delle immagini interrotta e registri di errori.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: [Cloud] La risposta GQL di Product Media Gallery non è ordinata in base alla posizione dell&#39;immagine
   * _Correzione nota_: il sistema ora ordina correttamente gli elementi nella raccolta multimediale in base alla posizione nella risposta di GraphQL, garantendo un ordine di visualizzazione accurato. In precedenza, gli elementi nella raccolta multimediale non venivano ordinati in base alla posizione, causando un ordine di visualizzazione errato.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Gli elementi della sottocategoria Cloud] non vengono visualizzati nella modifica dei widget sul backend di amministrazione
   * _Correzione nota_: la struttura delle categorie nella nuova pagina widget non deve più presentare problemi durante il caricamento delle categorie di livello 5+. In precedenza, mancavano alcune categorie durante il caricamento della struttura oltre le categorie di livello 5.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Catalogo, Framework

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

### Catalogo, prezzi, staging e anteprima

* _ACP2E-2672_: [Cloud] L&#39;endpoint API a prezzo speciale restituisce un errore quando si aggiornano contemporaneamente numerosi prodotti
   * _Correzione nota_: ora l&#39;API di aggiornamento in blocco del prezzo speciale creerà una singola campagna per ogni intervallo di date invece di più aggiornamenti pianificati per ogni prodotto e intervallo di date. Inoltre, supporterà le richieste API simultanee per un’elaborazione più rapida di un gran numero di SKU.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/f89a447e>

### Catalogo, prodotto

* _AC-7050_: la struttura di selezione delle categorie in Modifica prodotto non è nello stesso ordine impostato in Catalogo->Categorie
   * _Correzione nota_: il sistema ora visualizza correttamente la struttura di selezione delle categorie nella sezione di modifica dei prodotti nello stesso ordine impostato in Catalogo->Categorie, semplificando l&#39;amministrazione dei prodotti nei cataloghi di grandi dimensioni. In precedenza, la struttura ad albero delle categorie nella sezione di modifica del prodotto veniva visualizzata in ordine di creazione delle categorie, indipendentemente dall’ordine di visualizzazione impostato in Catalogo->Categorie.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catalogo, Ricerca

* _ACP2E-2757_: i prodotti non vengono visualizzati nella categoria e nella ricerca, ma i collegamenti diretti funzionano
   * _Correzione nota_: in precedenza, l&#39;attributo personalizzato Sì/No con price_* attribute_code non funzionava con l&#39;indicizzazione. Dopo questa correzione, l’attributo personalizzato Sì/No funziona come previsto.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Errore di ricerca elastica in alcune pagine categoria
   * _Correzione nota_: in precedenza, con il ticket di configurazione indicato, quando si inseriva il prezzo 0 per più prodotti, veniva generata un&#39;eccezione nella pagina della categoria front-end. Dopo che questa correzione è stata applicata quando più prezzi del prodotto 0 e la pagina della categoria viene caricata in front-end, non viene generata alcuna eccezione e la pagina della categoria viene caricata correttamente.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-3010_: [Cloud] PHPSESSID sta modificando ogni richiesta POST
   * _Correzione nota_: PHPSESSID non viene più rigenerato nelle richieste POST nell&#39;area front-end per un cliente connesso se la cache L2 Redis è abilitata e il cliente è stato aggiornato dal back-end
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>

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
* _AC-9638_: [Problema] relativo al caricamento di file nell&#39;editor di WYSIWYG nella pagina del prodotto
   * _Correzione nota_: la struttura delle cartelle viene ora visualizzata correttamente e nell&#39;editor di WYSIWYG è possibile caricare le immagini nella pagina del prodotto, anche dopo l&#39;espansione della scheda &#39;Immagini e video&#39;. In precedenza, l’espansione della scheda &quot;Immagini e video&quot; causava prima la mancata visualizzazione della struttura delle cartelle e un messaggio di errore durante il caricamento di un’immagine nell’editor di WYSIWYG.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] problema blocco dinamico
   * _Correzione nota_: il rendering dei widget è ora eseguito correttamente all&#39;interno di blocchi dinamici.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
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
* _ACP2E-3127_: imagecreatetruecolor(): il #2 dell&#39;argomento ($height) deve essere maggiore di 0. Impossibile caricare un’immagine specifica
   * _Correzione nota_: il problema è stato risolto causando errori nell&#39;amministratore durante il caricamento di immagini con altezza 0 tramite la raccolta multimediale ed è stata eseguita correttamente la sincronizzazione delle risorse tramite il comando sync. In precedenza non era possibile caricare l’immagine tramite la raccolta multimediale e il comando di sincronizzazione ha esito negativo anche quando un’immagine specifica si trova nella raccolta.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from in conflitto con l&#39;API di Google Maps
   * _Correzione di nota_: le mappe di Google ora vengono riprodotte correttamente nell&#39;editor di PageBuilder. In precedenza, un errore JavaScript impediva il corretto rendering di Google Maps.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Cliente/clienti

* _AC-12162_: front-end - convalida della data di nascita non riuscita nella pagina di creazione del cliente
   * _Correzione nota_: assicurati che tutta la convalida funzioni dopo la dipendenza di sistema di moment.js dall&#39;aggiornamento alla versione secondaria più recente
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Framework

* _AC-10654_: V1/customers/password endpoint question/issue
   * _Correzione nota_: il sistema ora rispetta i vincoli impostati nell&#39;interfaccia grafica di gestione durante l&#39;elaborazione delle richieste di modifica della password tramite l&#39;API, impedendo il potenziale abuso della funzione di reimpostazione della password. In precedenza, l’API poteva elaborare richieste di modifica della password al di fuori delle regole definite nell’interfaccia grafica di gestione, consentendo potenzialmente un flusso costante di e-mail di reimpostazione se erano note e-mail valide.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Correzione nota_: aggiornamento delle dipendenze di League/Flysystem Composer aggiornamento alla versione più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _Contributo del codice GitHub_: aggiorna le dipendenze del Compositore di League/flysystem 2.x alla versione più recente 3.x
* _AC-10838_: processo di indicizzazione errori processo indice di ricerca catalogo
   * _Correzione nota_: il sistema ora completa il comando di reindicizzazione senza errori, indipendentemente dalla versione libxml compilata con PHP. In precedenza, l’esecuzione del comando di reindicizzazione causava un errore di &quot;Errore di processo dell’indice di ricerca del catalogo durante il processo di indicizzazione&quot; quando PHP veniva compilato con determinate versioni di libxml.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: sono stati aggiunti i filtri created_at, status e grand_total alla query Ordini cliente e sono stati corretti più errori di filtro
   * _Correzione nota_: il sistema ora supporta l&#39;utilizzo dei filtri created_at, status e grand_total nelle query Ordini cliente e ha risolto un problema che impediva la corretta applicazione di più filtri. In precedenza, il sistema non supportava questi filtri e non applicava tutti i filtri quando in una query ne veniva utilizzato più di uno.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Correzione nota_: PHP 8.2/8.3, solo una dipendenza non riesce al momento dal puntatore php: league/flysystem
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contributo codice GitHub_: il sistema ora supporta PHP 8.2/8.3 aggiornando il pacchetto league/flysystem alla versione 3.0.20, garantendo che non si verifichino errori di linting PHP. Precedentemente, l&#39;esecuzione di file PHP attraverso l&#39;indicatore PHP con PHP 8.3 causava errori di linting nel pacchetto league/flysystem.
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
* _AC-11651_: il Magento sta tentando di modificare la proprietà di sola lettura nel metodo __wakeup di LoggerProxy
   * _Correzione nota_: il sistema ora consente la modifica delle proprietà di sola lettura precedenti nel metodo di riattivazione __LoggerProxy, garantendo un funzionamento senza problemi senza costringere gli utenti a utilizzare una soluzione alternativa. In precedenza, si verificavano problemi se si tentava di riassegnare il valore di una proprietà di sola lettura nel metodo di riattivazione __LoggerProxy.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38526>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Correzione nota_: esamina le versioni più recenti di php-amqplib/php-amqplib
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contributo codice GitHub_: aggiornata la versione più recente php-amqplib/php-amqplib :^3.x
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
* _AC-11808_:
   * _Correggi nota_: esamina e aggiorna l&#39;elenco delle dipendenze di base di Adobe Commerce
   * _Contributo del codice GitHub_: è necessario aggiornare l&#39;elenco delle dipendenze di base di Adobe Commerce 
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
* _AC-11905_: [Problema] Distribuzione contenuto statico - Errore di tipo
   * _Correzione nota_: il sistema ora gestisce correttamente i file LESS vuoti durante la distribuzione del contenuto statico, visualizzando il messaggio di errore &quot;LESS file is empty&quot;. In precedenza, veniva generato un errore di tipo errato quando si incontrava un file LESS vuoto durante la distribuzione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Correzione nota_: pulizia css jQuery/fileuploader dopo la migrazione alla libreria uppy
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contributo codice GitHub_: la libreria jQuery/fileUploader è stata rimossa perché è stata migrata alla libreria Uppy
* _AC-12002_: [Problema] [Visualizzazione] Spazio aggiuntivo rimosso nel tag link e script
   * _Correzione nota_: il sistema ora garantisce che non vi siano spazi aggiuntivi nei tag di collegamento e script, fornendo un codice più pulito ed efficiente. In precedenza, si trovavano doppi spazi tra gli attributi nei tag link e script.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Correzione nota_: pulizia della cartella ExtJs dopo la migrazione alla libreria jsTree
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contributo del codice GitHub_: la cartella extJs è stata rimossa perché la funzionalità correlata è stata migrata in jsTree
* _AC-12022_:
   * _Correzione nota_: aggiorna la dipendenza del sistema monologo/monologo alla versione principale più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contributo codice GitHub_: il sistema è stato aggiornato per utilizzare la versione principale più recente della libreria &quot;monolog/monolog:^3.x&quot;, garantendo compatibilità e prestazioni migliorate. In precedenza, il sistema utilizzava una versione obsoleta della libreria &quot;monologo/monologo&quot; che avrebbe potuto portare a potenziali problemi e limitazioni.
* _AC-12023_:
   * _Correzione nota_: aggiorna la dipendenza wikimedia/less.php alla versione principale più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contributo del codice GitHub_: il sistema è stato aggiornato in modo da utilizzare la versione principale 5.x più recente della libreria &quot;wikimedia/less.php&quot;, garantendo compatibilità e funzionalità aggiornate. In precedenza, il sistema utilizzava una versione obsoleta della libreria che poteva causare problemi di sicurezza.
* _AC-12024_:
   * _Correzione nota_: aggiorna la dipendenza jquery/validate library alla versione secondaria più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contributo del codice GitHub_: aggiorna la dipendenza della libreria jquery/validate alla versione secondaria più recente 1.20.0
* _AC-12025_:
   * _Correzione nota_: aggiorna la dipendenza di sistema moment.js alla versione secondaria più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contributo del codice GitHub_: aggiorna la dipendenza del sistema moment.js alla versione secondaria più recente 2.30.1
* _AC-12267_:
   * _Correzione nota_: supporto dei nuovi tentativi di connessione per la sessione Redis e compatibilità con colinmollenhour/php-redis-session-abstract v2.0.0
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contributo del codice GitHub_: è stata aggiornata la versione più recente di colinmollenhour/php-redis-session-abstract v2.0.0, compatibile con adobe commerce
* _AC-12268_:
   * _Correzione nota_: aggiorna le dipendenze del Compositore di League/Flysystem alla versione più recente
   * _Contributo del codice GitHub_: aggiorna le dipendenze del Compositore di League/flysystem 2.x alla versione più recente 3.x
* _AC-12594_: [Problema] Utilizza la configurazione compilata per i dati generati invece della configurazione generale
   * _Correzione nota_: il sistema ora utilizza la configurazione compilata per i dati generati anziché la configurazione generale, riducendo il trasferimento di rete e il sovraccarico dei dati che dipendono da una determinata versione del codice. Questa modifica impedisce l’override della cache nelle istanze condivise durante lo scambio dei contenitori, migliorando la stabilità e riducendo i tempi di inattività. In precedenza, alcune classi principali utilizzavano il tipo di configurazione condiviso, che poteva causare l’override della cache o tempi di inattività dell’applicazione a causa delle differenze nelle versioni del codice tra più server.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Rimuovere i riferimenti ai file da extjs rimossi in e1ccdb...
   * _Correzione nota_: il sistema ora rimuove i riferimenti ai file da extjs che erano stati precedentemente rimossi, eliminando gli errori nella console del browser e nel file di registro del sistema. In precedenza, questi riferimenti causavano errori a causa dell’assenza dei file di riferimento.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Correzione nota_: aggiornamento dipendenze compositore laminas aggiornamento alla versione più recente
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contributo codice GitHub_: il sistema ora supporta le versioni più recenti delle dipendenze del compositore laminas:
laminas/laminas-servicemanager
server laminas/laminas
laminas/laminas-stdlib
laminas/laminas-validator
compatibilità e funzionalità aggiornate. In precedenza, l’aggiornamento alle versioni più recenti di queste dipendenze poteva causare problemi di incompatibilità con le versioni precedenti e errori di test.
* _AC-12778_: [Problema] Pulizia minore: è stato corretto l&#39;utilizzo errato di sprintf. Sono necessari solo 2 segnaposto qui e...
   * _Correzione nota_: il sistema ora utilizza correttamente la funzione sprintf con il numero appropriato di segnaposto, migliorando la pulizia e la coerenza del codice. In precedenza, la funzione sprintf veniva erroneamente utilizzata con un argomento aggiuntivo, che non causava problemi importanti ma non era l’utilizzo corretto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _Correzione nota_: rimozione deprecazioni- Test di integrazione PhpUnit10
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contributo del codice GitHub_: risolvi le deprecazioni di PHPUnit
* _AC-12868_:
   * _Correzione nota_: rimozione degli elementi obsoleti- Test WebApi PhpUnit10
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contributo del codice GitHub_: risolvi le deprecazioni di PHPUnit
* _AC-12869_: [Problema] Corregge le classi errate a cui si fa riferimento nei moduli di Magento.
   * _Correzione nota_: il sistema ora fa correttamente riferimento alle classi nei moduli, garantendo un funzionamento più fluido e impedendo arresti anomali dovuti a classi non esistenti. Ciò include un bug nei moduli Indexer e Creditmemo e l&#39;implementazione di HttpGetActionInterface nella classe PrintAction. In precedenza, i riferimenti di classe errati causavano errori e potenziali arresti anomali del sistema e alcune funzionalità, come il nome del file di creditmemo PDF e la reindicizzazione delle scorte, non funzionavano come previsto.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37784>
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
* _AC-8984_: [Problema] Aggiunge altri colori all&#39;output di alcuni comandi cli di installazione
   * _Correzione nota_: il sistema ora aggiunge più colori all&#39;output di alcuni comandi CLI (Command Line Interface) di installazione, migliorando la leggibilità e l&#39;esperienza utente. In precedenza, l&#39;output di questi comandi era più difficile da leggere a causa della mancanza di differenziazione dei colori.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: l&#39;aggiornamento del Magento reimposta General/region/state_required quando viene aggiunto un nuovo paese con lo stato o l&#39;area geografica richiesti.
   * _Correzione nota_: il sistema ora aggiunge il paese modificato alla configurazione &#39;general/region/state_required&#39; solo quando viene aggiunto un nuovo paese con stati required, evitando interruzioni del codice personalizzato che presuppongono la disabilitazione dell&#39;area. In precedenza, l’aggiunta di un nuovo paese con stati obbligatori reimpostava la configurazione &quot;general/region/state_required&quot; sui paesi predefiniti con uno stato obbligatorio, potenzialmente interrompendo il negozio.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37796>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: https://github.com/magento/magento2/issues/37841
   * _Correzione nota_: differenza nella compilazione inferiore tra la libreria php e nodejs (grunt) con espressioni `calc` complicate
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contributo codice GitHub_: correggi la differenza in termini di minore compilazione tra la libreria php e nodejs (grunt) dopo l&#39;aggiornamento wikimedia/less.php:^5.x
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

### Framework, GraphQL

* _AC-7976_: [Problema] È stato introdotto il supporto di tipi scalari personalizzati per lo schema GraphQL
   * _Correzione nota_: il sistema ora supporta i tipi scalari personalizzati per lo schema di GraphQL, consentendo agli sviluppatori di definire tipi e implementazioni scalari personalizzati. Questa funzione può essere particolarmente utile per esprimere valori che possono richiedere la convalida, come HTML, e-mail, URL, date e così via, e per casi più avanzati come gli attributi EAV. In precedenza, il sistema non supportava l’elaborazione di tipi scalari personalizzati in GraphQL.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/36877>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

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
* _ACP2E-3253_: la paginazione di GraphQL cart itemsV2 non funziona correttamente
   * _Correzione nota_: il problema è stato risolto passando il valore corretto per l&#39;argomento della pagina corrente nella query di raccolta. In precedenza, veniva trasmesso un valore errato per impostare la pagina corrente, causando il problema.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

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

### Installazione e amministrazione

* _ACP2E-2102_: nessun pulsante Esporta VCL per vernice 7 nel pannello di amministrazione
   * _Correzione nota_: il pulsante &quot;Esporta VCL per vernice 7&quot; è stato aggiunto al pannello di amministrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventario/MSI

* _AC-11593_: la chiave API Google google non funziona durante l&#39;aggiunta della mappa con attributi
   * _Correzione nota_: il sistema ora supporta la versione più recente dell&#39;API di Google Maps 3.56, consentendo agli utenti di aggiungere correttamente un blocco di contenuto Map dal menu PageBuilder all&#39;area di visualizzazione senza riscontrare errori. In precedenza, gli utenti non potevano aggiungere un blocco di contenuto Mappa a causa di problemi di compatibilità con la versione dell’API Google Maps, causando un messaggio di errore &quot;si è verificato un errore&quot;.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_: [Cloud] problema critico con l&#39;elenco dei prodotti con spazi vuoti
   * _Correzione nota_: il sistema visualizza correttamente gli elenchi di prodotti senza spazi vuoti quando i prodotti sono impostati su &quot;esaurito&quot;, garantendo una visualizzazione coerente e accurata dei prodotti disponibili. In precedenza, se si impostava un prodotto su &quot;Esaurito&quot;, nell’elenco dei prodotti veniva visualizzato uno spazio vuoto, che causava interruzioni del layout e poteva confondere i clienti.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Ordine

* _AC-10828_: schermata di panoramica ordine back-end: quantità in inevaso non visibile a livello di articolo ordine
   * _Correzione nota_: il sistema visualizza ora il numero di articoli in inevaso nella colonna Quantità della schermata di panoramica ordine inevaso. In questo modo gli utenti possono tenere traccia con precisione dello stato di tutti gli elementi di un ordine. In precedenza, la colonna Quantità mostrava solo il numero di articoli ordinati, fatturati e spediti, ma non il numero di articoli in inevaso.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] ID archivio errato utilizzato nel modulo di rendering degli indirizzi dell&#39;ordine
   * _Correzione nota_: il sistema ora utilizza correttamente l&#39;ID store associato a un ordine durante il rendering dell&#39;indirizzo dell&#39;ordine, assicurandosi che gli indirizzi siano formattati correttamente in base al rispettivo ID store. In precedenza, il sistema utilizzava erroneamente l’ID store corrente, il che poteva causare una formattazione degli indirizzi errata nei casi in cui occorreva inviare più e-mail di ordine da diversi store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38412>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [Numero] Prezzo di spedizione diverso nel PDF stampato
   * _Nota sulla correzione_: i prezzi di spedizione vengono ora visualizzati correttamente nei PDF stampati in base alle impostazioni di configurazione dell&#39;imposta, garantendo la coerenza tra la pagina di visualizzazione della fattura dell&#39;ordine di vendita e la fattura stampata. In precedenza, il prezzo di spedizione visualizzato nel PDF stampato escludeva le imposte, indipendentemente dalle impostazioni di configurazione delle imposte.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
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

### Ordine, restituzioni

* _ACP2E-2982_: il rimborso dell&#39;ordine risulta in una nota di credito duplicata
   * _Correzione nota_: l&#39;emissione del rimborso tramite l&#39;API REST quando due richieste identiche sono state eseguite contemporaneamente non creerà più note di credito duplicate.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Ordine, imposta

* _ACP2E-3003_: [CLOUD] Base_row_total non corretta nell&#39;API dell&#39;ordine RESTFUL quando si abilitano transazioni transfrontaliere e si applicano sconti coupon
   * _Correzione nota_: ora viene restituito il valore base_row_total corretto dall&#39;API dell&#39;ordine RESTFUL quando è abilitata la transazione transfrontaliera e viene applicato lo sconto coupon.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Altri strumenti per sviluppatori

* _AC-10658_: [Problema] Correggere l&#39;errore di sintassi di HTML in visual.phtml
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

### Pagamenti

* _ACP2E-2841_: il flusso di pagamento crea una nuova transazione ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione
   * _Correzione nota_: il sistema ora recupera correttamente le informazioni sulla transazione senza creare una nuova transazione di pagamento ogni volta che si fa clic sul pulsante Recupera nella schermata Visualizza transazione. In precedenza, facendo clic sul pulsante Recupera, veniva erroneamente creata una nuova transazione di pagamento per un ordine già pagato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: il messaggio Paylater non viene visualizzato in PDP per l&#39;account commerciante paypal canadese
   * _Nota sulla correzione_: il sistema ora visualizza correttamente il messaggio PayLater per gli account esercente PayPal canadesi nella pagina Dettagli prodotto (PDP) quando il paese dell&#39;acquirente può essere determinato dall&#39;indirizzo di fatturazione o dalla spedizione del conto. In precedenza, il messaggio PayLater non veniva visualizzato a causa di un parametro mancante, causando un errore nella console del browser.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Prestazioni

* _AC-12000_: [Problema] Pulizia del codice, aggiunta di un nuovo blocco di intestazione critico e spostamento di CSS critico prima delle risorse
   * _Correzione nota_: il sistema ora include un nuovo blocco di intestazione critico e sposta CSS critico prima delle risorse, consentendo una maggiore personalizzazione e ottimizzazione delle prestazioni nel front-end. In precedenza, il CSS critico non veniva posizionato prima delle risorse, limitando le opportunità di personalizzazione e ottimizzazione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: la compilazione del tema si interrompe quando l&#39;host Mysql contiene informazioni sulla porta
   * _Correzione nota_: il sistema ora gestisce correttamente la configurazione host MySQL che include le informazioni sulla porta, garantendo la corretta compilazione del tema. In precedenza, la compilazione del tema non riusciva se la configurazione host MySQL nella connessione al database includeva informazioni sulla porta.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38799>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38842>
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

### Prodotto

* _AC-10535_: i caratteri speciali nel nome configurabile del prodotto associato vengono convertiti in entità HTML.
   * _Correzione nota_: il sistema ora mantiene correttamente i caratteri speciali nei nomi dei prodotti associati durante la modifica di un prodotto configurabile, impedendo che vengano convertiti in entità HTML. In precedenza, i caratteri speciali nei nomi dei prodotti associati venivano convertiti in entità HTML al momento della modifica del prodotto configurabile.
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
* _AC-5969_: AlertProcessor - Il #2 dell&#39;argomento ($storeId) deve essere di tipo int, stringa specificata
   * _Correzione nota_: il sistema ora attiva correttamente le e-mail di avviso sul prodotto verificando che l&#39;identificatore dell&#39;archivio sia del tipo di dati corretto. In precedenza, le e-mail di avviso sul prodotto non venivano inviate a causa di una mancata corrispondenza del tipo nell’identificatore dello store.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/35602>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [La funzione addFilterToMap del cloud] non funziona per alcune colonne
   * _Correzione nota_: ora è possibile utilizzare il modulo personalizzato nella griglia dell&#39;ordine. Errori precedenti durante l’utilizzo di un modulo personalizzato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>

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

### Sicurezza

* _AC-11762_:
   * _Correzione nota_: dopo la modifica BiC, aggiorna il campo finestra 2FA OTP con la descrizione e il valore predefiniti corretti
   * _Contributo del codice GitHub_: comando aggiornato per la modalità di immissione del periodo otp_window da ora bin/magento config:set twofactorauth/google/otp_window VALUE
to bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-11855_: [Problema] Popup Font CSP Paylater mancante
   * _Correzione nota_: il sistema ora consente il caricamento del tipo di carattere &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; senza violare la direttiva Content Security Policy, garantendo la corretta visualizzazione del popup Paylater. In precedenza, il caricamento del font veniva rifiutato a causa di una violazione della direttiva Content Security Policy, causando problemi di visualizzazione con il Popup Paylater.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Correzione nota_: dopo la modifica BiC, aggiorna il campo finestra 2FA OTP con la descrizione e il valore predefiniti corretti
   * _Contributo del codice GitHub_: comando aggiornato per la modalità di immissione del periodo otp_window da ora bin/magento config:set twofactorauth/google/otp_window VALUE
to bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-12309_:
   * _Correzione nota_: aggiorna la documentazione utente per l&#39;autenticazione a due fattori (2FA) per modificare il comando otp_window
   * _Contributo codice GitHub_: aggiorna la documentazione utente per l&#39;autenticazione a due fattori (2FA) per modificare il comando delle impostazioni OTP_WINDOW come da: https://jira.corp.adobe.com/browse/AC-11762

### Spedizione

* _AC-10757_: [Problema] È stato corretto un errore di battitura in tracking.phtml - le funzioni JS sono state rinominate &quot;currier&quot; in &quot;carrier&quot;
   * _Correzione nota_: il sistema ora utilizza correttamente il termine &quot;carrier&quot; invece del &quot;currier&quot; errato nelle funzioni del gestore JavaScript utilizzate nel modello di tracciamento degli ordini, garantendo la corretta denominazione delle funzioni e la chiarezza del codice. In precedenza, veniva utilizzato il termine errato &quot;currier&quot;, che portava a una potenziale confusione e incoerenza nella base di codice.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Correzione nota_: UPS REST &quot;Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura&quot;
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _Contributo codice GitHub_: le tariffe UPS sono visibili nel carrello e nell&#39;estrazione.
* _AC-11916_:
   * _Correzione nota_: [QPT] UPS REST &quot;Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura&quot;
   * _Contributo codice GitHub_: le tariffe UPS sono visibili nel carrello e nell&#39;estrazione.
* _AC-11938_: UPS REST &quot;Una spedizione non può avere come unità di misura KGS/IN, LBS/CM o OZS/CM&quot;
   * _Correzione nota_: assicurarsi che le tariffe UPS siano visibili nel carrello e nell&#39;estrazione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38618>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Correzione nota_: [QPT] UPS REST &quot;Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura&quot;
   * _Contributo codice GitHub_: le tariffe UPS sono visibili nel carrello e nell&#39;estrazione.
* _AC-11984_:
   * _Correzione nota_: [QPT] UPS REST &quot;Una spedizione non può avere un KGS/IN o LBS/CM o OZS/CM come unità di misura&quot;
   * _Contributo codice GitHub_: le tariffe UPS sono visibili nel carrello e nell&#39;estrazione.
* _ACP2E-2738_: la finestra di tracciamento mostra una data di consegna prevista errata
   * _Correzione nota_: visualizza la data di consegna corretta per il gestore Fedex.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Le Tariffe Della Tabella Continuano A Essere Visualizzate Anche Se È Applicata La Spedizione Gratuita
   * _Correzione nota_: il metodo di spedizione delle tariffe della tabella viene visualizzato anche se la spedizione gratuita diventa disponibile dopo l&#39;applicazione del coupon
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: test MFTF AdminCreatingShippingLabelTest non riuscito a causa di credenziali non aggiunte nell&#39;ambiente Jenkins
   * _Correzione nota_: correzione test mftf
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Targeting

* _AC-9432_: [Problema] Consente l&#39;utilizzo di intervalli CIDR nell&#39;elenco consentiti di manutenzione
   * _Correzione nota_: il sistema ora supporta l&#39;utilizzo di intervalli CIDR nell&#39;elenco Consenti elenco indirizzi IP in modalità di manutenzione, consentendo a un intervallo di indirizzi IP di ignorare la modalità di manutenzione. In precedenza, la modalità di manutenzione Consenti elenco IP consentiva solo a singoli indirizzi IP di ignorare la modalità di manutenzione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37943>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/30699>

### Framework di test

* _AC-11491_:
   * _Correzione nota_: [Ignora] È necessario annullare nuovamente il salto del test di integrazione
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _Contributo del codice GitHub_: annulla il salto di tutti i test di integrazione ignorati in questa PR - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_: test di integrazione non riuscito in testDbSchemaUpToDate a causa del tipo di colonna JSON
   * _Correzione nota_: il sistema ora riconosce correttamente i tipi di colonna JSON nello schema del database durante gli integration test, evitando errori di test a causa di una mancata corrispondenza tra lo schema del database e lo schema dichiarativo. In precedenza, il sistema identificava erroneamente i tipi di colonna JSON come LONGTEXT in MariaDB, causando l’errore dei test di integrazione.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/ef81f5a2>

### Framework interfaccia utente

* _AC-12128_: correzione della vulnerabilità di sicurezza di Prototype.js CVE-2020-27511
   * _Correzione nota_: il sistema è stato aggiornato per risolvere la vulnerabilità di sicurezza CVE-2020-27511 in Prototype.js 1.7.3, migliorando la sicurezza complessiva del sistema. Prima di questo aggiornamento, il sistema era suscettibile a un’espressione regolare Denial of Service (ReDOS) attraverso la rimozione di tag HTML creati.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12128_:
   * _Correzione nota_: Correzione di una vulnerabilità di sicurezza di Prototype.js CVE-2020-27511
   * _Problema GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contributo del codice GitHub_: il sistema è stato aggiornato per risolvere la vulnerabilità di sicurezza CVE-2020-27511 in Prototype.js 1.7.3, migliorando la sicurezza complessiva del sistema. Prima di questo aggiornamento, il sistema era suscettibile a un’espressione regolare Denial of Service (ReDOS) attraverso la rimozione di tag HTML creati.
* _AC-12189_: Grunt Less utilizza il prefisso pub/ per sourcemaps
   * _Correzione nota_: il sistema ora genera meno sourcemap/css senza il prefisso /pub per i percorsi quando si utilizza grunt, eliminando la necessità di una soluzione alternativa nella configurazione del server Web. In precedenza, l’utilizzo del prefisso /pub nei percorsi sourcemaps richiedeva una configurazione specifica nel server web per funzionare correttamente.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/38837>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: il contenuto statico è in distribuzione per i moduli disabilitati
   * _Correzione nota_: il sistema ora esclude i CSS relativi ai moduli disabilitati dai file di output CSS finali, garantendo che non vengano caricati stili non necessari. In precedenza, i CSS relativi ai moduli disattivati venivano inclusi nei file di output CSS finali, determinando il caricamento di stili aggiuntivi e non necessari.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/24666>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Problema] Non caricare il contesto del blocco di back-end sul front-end
   * _Correzione nota_: il sistema ora garantisce che il contesto del blocco back-end non venga caricato sul front-end, impedendo la creazione di sessioni backend non necessarie e potenziali blocchi di sessione. In precedenza, il sistema caricava erroneamente il contesto del blocco back-end sul front-end, determinando la creazione di sessioni back-end e potenziali blocchi di sessione.
   * _Problema GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: eccezione durante la verifica del saldo di una gift card quando Recaptcha è abilitato
   * _Correzione nota_: gli utenti potranno recuperare il saldo della gift card nella schermata Visualizza e modifica carrello. In precedenza, questi dettagli non venivano visualizzati quando reCAPTCHA era abilitato.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [CHIARIMENTO] Richiesta di funzionalità Conformità ADA
   * _Correzione nota_: il sistema ora garantisce la conformità ADA rimuovendo le proprietà CSS non supportate e sostituendole con quelle supportate nel file print.css. In precedenza, l’utilizzo di proprietà CSS non supportate causava problemi di compatibilità con il browser.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Codice libreria di confusione in effect-drop.js di AC 2.4.4-p8
   * _Correzione nota_: il sistema ora implementa correttamente la libreria effect-drop.js, garantendo il corretto funzionamento degli effetti dell&#39;interfaccia utente jQuery. In precedenza, la libreria effect-drop.js veniva erroneamente sovrascritta con la libreria effect-clip.js, causando potenziali problemi con gli effetti dell’interfaccia utente jQuery.
   * _Contributo codice GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>

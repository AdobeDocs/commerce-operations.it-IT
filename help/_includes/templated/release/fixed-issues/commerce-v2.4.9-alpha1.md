---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Problemi risolti in Adobe Commerce (v2.4.9-alpha1)

## Sono stati risolti dei problemi in v2.4.9-alpha1

Sono stati risolti 84 problemi nel codice core Adobe Commerce 2.4.9-alpha1. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### L’operazione di massa asincrona rimane in stato aperto per async.magento.configurableproduct.api.optionrepositoryinterface.save.post

Gli endpoint API in blocco ora generano un errore se il corpo della richiesta non è un array, richiedendo pertanto che le chiavi degli elementi in blocco siano numeri consecutivi a partire da 0. In precedenza, lo stato dell’elemento in blocco non veniva aggiornato a causa della chiave dell’elemento arbitraria inviata nella richiesta in blocco.

_ACP2E-3544 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### [Errore REST API CLOUD] nel valore is_subscscriptions che non considera dall&#39;archivio corrente utilizzando searchCriteria

API REST La query del cliente recupera il valore &quot;is_subscscriptions&quot; corretto dall’archivio corretto utilizzando searchCriteria
In precedenza, la query API REST del cliente non considerava l’archiviazione quando si recuperava il valore is_subscscriptions&quot;.

_ACP2E-3621 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all può creare più voci per 1 SKU

Le richieste simultanee di salvataggio e aggiornamento dello stesso prodotto vengono ora serializzate per evitare race condition che potrebbero causare incongruenze nei dati o duplicazione dei prodotti

_ACP2E-3744 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Account

#### [L&#39;operazione di eliminazione del cloud] non è consentita per l&#39;errore dell&#39;area corrente durante la creazione dell&#39;account del cliente

Dopo la correzione, il salvataggio di un cliente con un indirizzo non valido restituisce un messaggio che descrive il motivo dell’invalidità invece di irrilevante &quot;Operazione di eliminazione non consentita per l’area corrente&quot;.

_ACP2E-3791 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Interfaccia utente amministratore

#### [Problema] Migliorare l&#39;esperienza utente con la struttura dei ruoli

Questa richiesta di pull aggiunge pulsanti per comprimere tutto, espandere tutto ed espandere i rami con gli elementi selezionati. Questa funzionalità è simile a quella fornita nella struttura delle categorie (Catalogo -> Inventario -> Categorie)

_AC-14020 - [Problema GitHub](https://github.com/magento/magento2/issues/39654) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: l’intestazione &quot;Sender&quot; deve essere un’istanza di &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (ottenuto &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

_AC-14520 - [Problema GitHub](https://github.com/magento/magento2/issues/39823) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1e14bd72)_

#### Fornire una funzione per eliminare di massa le aliquote utilizzando la griglia

Gli utenti amministratori ora possono eliminare simultaneamente più aliquote dalla griglia Aliquote amministrative.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problema GitHub](https://github.com/magento/magento2/issues/33399) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33484) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### La regola del prezzo del carrello con condizione SKU non tiene conto degli &quot;zeri iniziali&quot; nello SKU (sku: 01234 è uguale a 1234)

Il sistema ora gestisce correttamente la regola di prezzo del carrello con SKU condizione tenendo conto degli &quot;zeri iniziali&quot; nello SKU

_AC-9428 - [Problema GitHub](https://github.com/magento/magento2/issues/37919) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problema con il comportamento del valore dell’opzione attributo predefinito per la selezione multipla

Prima della correzione, i valori predefiniti per l’attributo di più opzioni non venivano salvati correttamente. Ora, dopo la correzione, i valori vengono memorizzati correttamente nel database.

_ACP2E-3523 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### I sottotitoli del menu di amministrazione del back-end non vengono visualizzati

Tutti i titoli dei gruppi del menu principale verranno ora visualizzati correttamente. In precedenza, se la seconda o la terza colonna del menu principale conteneva un solo gruppo di collegamenti, il titolo del gruppo non veniva visualizzato.

_ACP2E-3540_

#### Problema durante lo spostamento della quantità di prodotto dal carrello all’amministratore

Quando crei un ordine dall’amministratore, i prodotti nel carrello dei clienti sulla barra laterale non scompaiono se aggiunti all’ordine.

_ACP2E-3563 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Interfaccia utente amministratore, B2B

#### L’accesso B2B come intestazione del cliente presenta ancora il marchio Magento

In precedenza, l’intestazione della vetrina mostra &quot;Ora sei connesso come &lt;nome cliente> a &lt;nome negozio>&quot; con il branding Magento. Che è ora fisso e l’intestazione viene visualizzata con il branding ADOBE.

_AC-14361 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interfaccia utente amministratore, contenuto

#### Eccezione &quot;Impossibile creare una rappresentazione per i percorsi delle risorse multimediali&quot; durante l’inserimento dell’immagine

Dopo aver rimosso i valori di Larghezza massima e Altezza massima della configurazione di Ottimizzazione immagine di Media Gallery, l’errore non si verifica più durante il processo di ottimizzazione dell’immagine.

_ACP2E-3781 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interfaccia di amministrazione, protezione

#### Gestione password deboli

Non è possibile salvare l&#39;utente amministratore con la stessa password. In precedenza, era stato salvato senza una convalida corretta.

_ACP2E-3657 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Interfaccia utente amministratore, Sicurezza, Staging e Anteprima

#### Registri delle azioni per staging dei contenuti

I registri azioni ora visualizzano le attività Staging Update. In precedenza, il registro Staging Update (Aggiornamento gestione temporanea) non veniva registrato nei registri delle azioni di amministrazione.

_ACP2E-3679_

### B2B

#### L&#39;ordine non funziona su Procedi al pagamento tramite Offerta negoziabile con metodo di pagamento con carta di credito PayFlow Pro

_AC-11973_

#### Il messaggio di successo dopo la ridenominazione del preventivo scompare in modo intermittente

_AC-13447_

#### Il calcolo del totale complessivo non include l&#39;importo dell&#39;imposta

L&#39;ordine contiene i totali corretti quando i luoghi dell&#39;ordine di acquisto esistente sono abilitati per il commercio transfrontaliero.

_ACP2E-3727_

#### La rimozione dell’assegnazione delle categorie in un catalogo condiviso B2B tramite l’API REST è lenta

Ora le prestazioni sono notevolmente migliorate quando si annullano le assegnazioni di categorie in B2B. In precedenza, la rimozione dell’assegnazione di categorie nel catalogo condiviso B2B richiedeva molto tempo.

_ACP2E-3796_

#### Problema di prestazioni con la nuova patch di installazione in B2B

È stato risolto il problema di prestazioni a causa del quale l’aggiornamento del modulo Magento_Company dopo l’aggiornamento a B2B 1.5.2 impiegava un tempo eccessivamente lungo durante l’elaborazione di un numero elevato di record (~100.000+) nella tabella company_structure.

_ACP2E-3850_

### Carrello e pagamento

#### Aggiornamento Magento 2.4.7 (mini)cart senza quantità decimale consentita

Ora Magento gestisce correttamente quando si aggiorna la quantità con i decimali dal mini carrello quando la lingua era NL (olandese)

_AC-13238 - [Problema GitHub](https://github.com/magento/magento2/issues/39236) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problema] Aggiornamento subtotale.phtml

Il sistema aggiorna subtotal.phtml con la spaziatura corretta

_AC-13907 - [Problema GitHub](https://github.com/magento/magento2/issues/39619) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39612)_

#### Impossibile effettuare l&#39;ordine con l&#39;ospite

_AC-14241 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### I preventivi persistenti scaduti non vengono eliminati da un processo cron sales_clean_quote

Le virgolette persistenti scadute vengono ora cancellate quando viene eseguito il processo cron &#39;persistent_clear_expiry&#39;. In precedenza, le virgolette persistenti scadute non venivano cancellate da nessun altro processo cron.

_ACP2E-3493 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Errore &quot;Si è verificato un errore&quot; durante il pagamento per l’azienda inattiva

Prima della correzione, se la società utente connessa non era più abilitata, l’azione di disconnessione non veniva completata correttamente nella pagina del carrello. Ora, se la società non è più disponibile, la disconnessione viene eseguita correttamente.

_ACP2E-3541 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La selezione degli indirizzi non viene salvata quando si esegue il Check-Out con più indirizzi

Prima della correzione durante l’annullamento dell’opzione di multishipping, l’indirizzo non veniva preselezionato quando si tornava al multiservizio. Ora l&#39;indirizzo predefinito viene sostituito da una delle selezioni effettuate nella schermata di configurazione multipla.

_ACP2E-3646 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6ea61121)_

### Carrello e pagamento, SEO

#### URL codice gift card errato nell’e-mail quando acquistato da dal sito web secondario

In precedenza, la configurazione di più store e la gift card per i negozi non predefiniti reindirizzavano sempre la richiesta di gift card al sito Web predefinito. Dopo l&#39;applicazione di questa correzione, l&#39;e-mail reindirizzerà il collegamento della richiesta di rimborso della gift card all&#39;ambito o al sito Web corretto.

_ACP2E-3699_

### Carrello e pagamento, spedizione

#### La regola del prezzo del carrello [Mainline] non rispetta la multiproprietà

Prima dell’implementazione di questa correzione, la regola del prezzo del carrello per i prodotti di spedizione multipla non veniva applicata correttamente quando venivano applicate le condizioni di selezione secondaria ed era abilitata la spedizione gratuita. Tuttavia, poiché la correzione è stata applicata, la regola del prezzo del carrello per i carrelli con spedizione multipla ora funziona come previsto.

_ACP2E-3666 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogo

#### Fpc cache duplicata per la stessa pagina con la stessa query

Il sistema ora identifica e utilizza correttamente la stessa cache full page (FPC) per le pagine con gli stessi parametri di query, indipendentemente dall’ordine o dai caratteri finali. In questo modo si evita un aumento superfluo delle dimensioni della cartella della cache delle pagine. In precedenza, il sistema creava un identificatore FPC diverso per la stessa pagina se l’ordine dei parametri di query era diverso o se c’erano caratteri finali, portando a un aumento della dimensione della cartella della cache delle pagine.

_AC-10722 - [Problema GitHub](https://github.com/magento/magento2/issues/38269) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38270)_

#### Indicizzazione mancante delle colonne richieste nella tabella catalog_product_entity_int

Aggiunta dell&#39;indicizzazione mancante delle colonne richieste nella tabella catalog_product_entity_int

_AC-10844 - [Problema GitHub](https://github.com/magento/magento2/issues/38315) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38316)_

#### La pagina di prodotto contiene un errore a causa di riscritture URL

Ora la pagina di prodotto viene caricata correttamente quando l’URL viene riscritto

_AC-2950 - [Problema GitHub](https://github.com/magento/magento2/issues/35371) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39670)_

#### [Cloud] bug durante l&#39;aggiunta di prodotti alla categoria

L’etichetta di impaginazione e conteggio dei record ora funziona correttamente quando si aggiungono prodotti a una categoria tramite la griglia a comparsa. In precedenza, il caricamento di una sola pagina con elementi uguali alle dimensioni della pagina causava problemi con il menu a discesa per la selezione degli elementi.

_ACP2E-3526_

#### errore cron indexer_update_all_views con MAGE_INDEXER_THREADS_COUNT

È stato risolto un problema per MAGE_INDEXER_THREADS_COUNT > 2 con l’indicizzatore del segmento cliente

_ACP2E-3538 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Eccezione durante l’aggiunta della &quot;combinazione di condizioni&quot; nella condizione del widget Prodotti Page Builder

Il problema è stato risolto aggiungendo un segno di spunta per saltare le condizioni mancanti o incomplete. In precedenza, ciò causava la generazione di registri di errore a causa della gestione di condizioni incomplete nel sistema.

_ACP2E-3545 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Arresto anomalo del browser durante il caricamento del set di attributi

Il browser non si blocca più nella pagina di modifica del set di attributi se sono presenti più di attributi di prodotto 4k

_ACP2E-3633 - [Problema GitHub](https://github.com/magento/magento2/issues/38810) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [L&#39;URL del prodotto ] di CLOUD riscrive non è stato creato per il nuovo store: Go Live Blocker

Creazione della riscrittura dell&#39;URL del prodotto per il nuovo archivio completata.
Operazione precedente terminata con perdita di memoria o timeout.

_ACP2E-3669 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Il valore predefinito dell&#39;attributo per le opzioni non funziona

In precedenza, quando si modificava il valore predefinito di un attributo di selezione del prodotto, questo veniva visualizzato come un elemento array con i valori precedenti. Dopo l’applicazione di questa correzione, quando si aggiorna un valore di attributo del prodotto, questo viene salvato come singolo elemento nella tabella eav_attribute.

_ACP2E-3688 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La convalida della gift card non riesce quando si modifica a causa del separatore delle migliaia

È stato risolto un problema relativo al risparmio del tipo di prodotto gift card quando l&#39;importo della gift card è 1000 e superiore.

_ACP2E-3704_

### Catalogo, GraphQL, Ricerca

#### La graphql dei prodotti restituiva categorie disabilitate nelle aggregazioni di categorie

Dopo la correzione, le categorie disabilitate non vengono restituite per la richiesta GraphQl dei prodotti.

_ACP2E-2885 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogo, prodotto

#### [Errore casuale] libreria Fotorama non caricata

Il sistema ora assicura che la libreria Fotorama sia caricata correttamente, consentendo la visualizzazione di tutte le immagini allegate nella galleria immagini come previsto. In precedenza, solo la prima immagine era visibile a causa di un problema con la libreria Fotorama che non veniva caricata correttamente.

_AC-12124 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/27217d0e)_

### Contenuto

#### L’inserimento di csp_whitelist.xml nel tema non funziona e crea un problema intermittente

È stato implementato il caching della whitelist CSP per area del sito web.

_AC-13069 - [Problema GitHub](https://github.com/magento/magento2/issues/38933) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39672)_

#### Errore: errore di script per &quot;Magento_Catalog/js/validate-product&quot; per admin content pagebuilder with products load

Questa PR corregge l’errore Script per catalogAddToCart quando si modifica il generatore di pagine con la condizione &quot;products&quot;

_AC-13891 - [Problema GitHub](https://github.com/magento/magento2/issues/39604) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39677)_

#### Blocca la selezione in widget che hanno lo stesso identificatore

Il sistema ora gestisce correttamente la selezione del blocco durante la creazione di widget quando sono presenti gli stessi blocchi di identificatore

_AC-14132 - [Problema GitHub](https://github.com/magento/magento2/issues/39692) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39722)_

#### Prefisso tabella non preso in considerazione

_AC-14556 - [Problema GitHub](https://github.com/magento/magento2/issues/39847) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Impossibile caricare l’immagine con larghezza relativamente piccola

Il sistema non è più in grado di ridimensionare l&#39;immagine con una larghezza relativamente ridotta rispetto all&#39;altezza.

_ACP2E-3558 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Percorso di configurazione errato per la configurazione dello stile del percorso di archiviazione remota

Dopo la correzione, l’impostazione della configurazione dello stile del percorso di archiviazione remota influirà sulla configurazione effettiva dello stile del percorso AWS S3.

_ACP2E-3734 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Framework

#### Compilazione del codice del modulo disabilitato.

Questa richiesta pull evita i moduli disabilitati prima della compilazione del codice.

_AC-10933 - [Problema GitHub](https://github.com/magento/magento2/issues/38241) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39723)_

#### Modello titolo_tema Magento.phtml non valido per PHP 8.2

Questa richiesta di pull risolve un problema quando una pagina CMS creata con l’intestazione null come nel Php 8.x passando null a trim() genera un’eccezione: Funzionalità obsolete: trim(): passaggio null al parametro #1 ($string) di tipo stringa

_AC-12856 - [Problema GitHub](https://github.com/magento/magento2/issues/39092) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39398)_

#### Quando si utilizza lo storage dei file per il provider di blocchi, viene creata una directory di file in continua crescita senza alcuna pulizia

Questa richiesta di pull introduce un nuovo processo cron che viene eseguito una volta al giorno e cerca i file di blocco che non sono stati modificati nelle ultime 24 ore e che possono quindi essere rimossi in modo sicuro. In questo modo il contenuto della directory dei file di blocco sarà controllato.
Questo processo cron eseguirà un elemento solo quando il provider di blocchi è configurato per l’utilizzo di file, non quando viene utilizzato uno degli altri (database: impostazione predefinita, zookeeper o cache)

_AC-13367 - [Problema GitHub](https://github.com/magento/magento2/issues/39369) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Problema] Pulizia: non utilizzare un valore restituito void dalle chiamate di metodo.

Questa PR esegue una pulizia di minore entità. A volte chiamavamo metodi che non restituivano nulla (void) e utilizzavano quel valore di risultato. Che in realtà non è necessario.

_AC-13664 - [Problema GitHub](https://github.com/magento/magento2/issues/39524) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39516)_

#### [Problema] [PHPDOC] Correzione di phpdoc non valido per Magento\Framework\Message\ManagerInterface

Questa PR corregge il phpdoc errato per \Magento\Framework\Message\ManagerInterface e rimuove tutti i phpdoc duplicati in \Magento\Framework\Message\Manager (utilizza la sintassi inheritdoc).

_AC-14312 - [Problema GitHub](https://github.com/magento/magento2/issues/39593) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39153)_

#### È stata rimossa la stabilità minima beta da compositore.json

È stata rimossa la stabilità minima beta da compositore.json

_AC-14450 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallel_generation deve essere impostato tramite la variabile di ambiente

Dopo la correzione, è possibile utilizzare la variabile di ambiente &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; per impostare la configurazione &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] La modifica del tipo di colonna della tabella da Int a Decimal tramite il file db_schema.xml In Magento 2 genera errori

La modifica del tipo di dati della colonna non funziona correttamente. In precedenza, generava un errore: l’attributo &quot;identity&quot; non era consentito.

_ACP2E-3709 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Supporto per la nuova valuta (XCG) in Adobe

Il Fiorino dei Caraibi (XCG) è aggiunto all&#39;elenco delle valute.

_ACP2E-3790 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### Il posizionamento di Risposta GraphQL per ordine non include il messaggio di eccezione

È stata ripristinata la modifica precedente che restituiva errori in un formato diverso. Ora i potenziali errori vengono restituiti in modo coerente, senza interrompere lo schema di GraphQL. È opportuno aggiungere questo codice come BIC noto, approvato dal PM nel documento ACP2E-3399

_ACP2E-3399 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Il posizionamento di GraphQL Response for Order è parzialmente localizzato

Gli errori restituiti dalla mutazione GraphQl placeOrder non erano completamente localizzati. Ora, in un contesto multilingue, gli errori vengono tradotti correttamente.

_ACP2E-3506 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Chiamate simultanee per riordinare l’API di GraphQL - Stessi prodotti aggiunti a righe diverse

È stato risolto il problema che causava l’aggiunta degli stessi prodotti come righe diverse da parte di chiamate simultanee all’API Reorder GraphQL, con conseguenti incongruenze nei dati.

_ACP2E-3774 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL mutation(Change email Address) non attiva la notifica e-mail

In precedenza, l’e-mail non veniva inviata ai clienti dopo il corretto aggiornamento dei loro indirizzi e-mail sui loro account. Dopo l’applicazione della correzione, i clienti ora ricevono le notifiche e-mail dopo aver aggiornato correttamente i loro indirizzi e-mail.

_ACP2E-3785 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Attributo dinamico non aggiornato nel registro dei regali tramite updateGiftRegistry Mutation

In precedenza, prima di questa correzione tramite la mutazione updateGiftRegistry, l’attributo personalizzato del registro dei doni non veniva modificato o aggiornato tramite mutazioni GraphQL. Dopo l’applicazione di questa correzione, l’attributo dinamico del registro degli omaggi può essere aggiornato correttamente tramite la mutazione updateGiftRegistry.

_ACP2E-3805 - [Problema GitHub](https://mcstaging.briscoes.co.nz/)_

### Importa/esporta

#### [Problema] Copyedit: cambia &quot;copia&quot; in &quot;copia&quot;

PR corregge il problema di modifica secondaria per correggere l&#39;ortografia di &quot;copia&quot;

_AC-13300 - [Problema GitHub](https://github.com/magento/magento2/issues/39311) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39307)_

#### Endpoint REST &quot;Product Import Json&quot; non convalida i campi obbligatori

Il campo Nome è ora necessario quando si creano nuovi prodotti tramite il processo di importazione (amministratore o API). Prima della correzione, potevi creare nuovi prodotti senza nome, l’interfaccia di amministrazione veniva interrotta e venivano creati prodotti non validi.

_ACP2E-3660 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Opzione filtro sito Web mancante nel processo di esportazione

È ora possibile filtrare i prodotti per siti web durante la creazione dell’esportazione di prodotti.

_ACP2E-3720 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicato di AC-13913 - Pulizia degli attributi statici in modo asincrono.

Dopo la correzione, non viene visualizzato alcun errore di tipo &quot;apply_to&quot;, chiave di array non definita, quando vengono create numerose istanze di \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType.

_ACP2E-3752 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Inventario/MSI

#### Il ritiro dello store non rispetta il raggio di ricerca massimo quando l’indirizzo viene modificato al momento del pagamento

Ora lo store preselezionato in &quot;Pick in Store&quot; verrà aggiornato se l&#39;indirizzo di spedizione cambia. In precedenza, una volta preselezionato un negozio, non veniva modificato anche se il nuovo indirizzo di spedizione non si trovava nel raggio dello store selezionato

_ACP2E-3728 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/07620383)_

### Ordine

#### Impossibile restituire null per il campo non nullable \&amp;quot;AppliedCoupon.code\&amp;quot; problema imprevisto

_AC-14484 - [Problema GitHub](https://github.com/magento/magento2/issues/39841) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### [Cloud] Alcuni JavaScript in linea non funzionano dopo l&#39;aggiornamento a Magento 2.4.6-p7

Facendo clic sul pulsante &quot;Elimina&quot; in &quot;Aggiungi per ordine da SKU&quot; in admin verrà ora rimosso lo SKU. In precedenza, facendo clic sul pulsante &quot;elimina&quot; in &quot;Aggiungi per ordine da SKU&quot; non veniva rimosso lo SKU.

_ACP2E-3515_

#### i dati serializzati gift_cards non sono coerenti nella tabella sales_order

i dati gift_cards nella tabella sales_order ora sono serializzati correttamente. In precedenza, veniva serializzato ogni volta che l’ordine veniva aggiornato.

_ACP2E-3662_

### Ordine, determinazione prezzi

#### L’Amministratore visualizza un simbolo di valuta errato quando crea un reso

In una configurazione multisito con valute diverse (EUR/USD/GBP), nella pagina di selezione del prodotto di ritorno in amministrazione viene ora visualizzato il simbolo di valuta corretto. In precedenza veniva visualizzato il simbolo di valuta predefinito.

_ACP2E-3658 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Altri strumenti per sviluppatori

#### Errore di accessibilità del faro

Il sistema ora passa con un punteggio di accessibilità pari a 100

_AC-12783 - [Problema GitHub](https://github.com/magento/magento2/issues/39054) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39164)_

#### Disabilita la configurazione della vetrina captcha comunque carica i file captcha js

Il sistema ora non carica i file captcha js quando captcha è stato disabilitato per storefront

_AC-14267 - [Problema GitHub](https://github.com/magento/magento2/issues/32987) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39154)_

### Imballaggio

#### [Creazione pacchetti] Correzione della dipendenza standard di magento/magento-coding+ Page-Builder

_ACPLTSRV-6383_

### Pagamenti

#### [Problema] Correggere l&#39;acquisizione delle fatture offline (404)

Corregge l’errore di pagina 404 durante l’acquisizione di fatture per metodi di pagamento offline dall’amministratore di Magento

_AC-13336 - [Problema GitHub](https://github.com/magento/magento2/issues/39298) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39297)_

### Prestazioni

#### Il modulo delle autorizzazioni per categoria potrebbe impedire il caching

Controller di terze parti ora memorizzati correttamente nella cache con i segmenti dei clienti

_ACP2E-3721_

### Prodotto

#### Raccolta prodotti: chiamate addMediaGalleryData getSize quando la raccolta può essere o sarà caricata (può utilizzare il conteggio per evitare una query DB aggiuntiva)

Questa PR riduce la chiamata di query aggiuntiva utilizzando count() se la raccolta di prodotti è già caricata durante la chiamata di Product Graphql con il campo media_gallery incluso.

_AC-13055 - [Problema GitHub](https://github.com/magento/magento2/issues/39111) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39681)_

#### [2.4.8] Nessun callback trovato per il processo cron catalog_product_alert

_AC-14494 - [Problema GitHub](https://github.com/magento/magento2/issues/39800) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### La query lenta viene eseguita quando il widget del prodotto è incluso tramite pagebuilder

La query per la creazione di widget di prodotto, inclusi SKU di prodotto, è ottimizzata.

_ACP2E-3449 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Immagini del prodotto non ridimensionate quando aggiunte come prodotto configurabile

In precedenza, le immagini aggiunte tramite le configurazioni nel pannello di amministrazione non rispettavano il limite di dimensione massima per il caricamento, il che poteva causare incoerenze e problemi di gestione. Ora è stata implementata una correzione per garantire che le immagini vengano ridimensionate automaticamente durante il caricamento in modo da rispettare il limite di dimensione massimo, semplificando il processo e mantenendo gli standard di sistema.

_ACP2E-3504 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Spedizione

#### Il documento deve essere aggiornato per % di implementazione non corretta nel documento ufficiale

È stato aggiornato il devdoc per il supporto dell&#39;API REST DHL

_AC-14507_

#### [DHL]-Gestisce le dimensioni facoltative nelle impostazioni delle dimensioni regolari e la varianza di prezzo tra le integrazioni REST e API XML

_AC-14601 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Eccezione durante la creazione dell&#39;etichetta di spedizione UPS

Avviso corretto: conversione da array a stringa durante la creazione di etichette di spedizione UPS

_ACP2E-3676 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Staging e anteprima

#### L&#39;anteprima di un aggiornamento pianificato consente di aprire la prima visualizzazione dello store in ordine alfabetico anziché la visualizzazione dello store di interesse

Prima della correzione, l’anteprima di un aggiornamento pianificato veniva aperta nella prima visualizzazione store in ordine alfabetico anziché nella visualizzazione store assegnata.
Dopo la correzione, l’anteprima ora si apre correttamente nella vista archivio assegnata all’aggiornamento di staging del blocco CMS.

_ACP2E-3671 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Problema di comportamento Cron Staging_apply_version - special_price ignorato

Dopo la correzione, i totali dei preventivi verranno ricalcolati dopo la modifica del prezzo speciale mediante l&#39;aggiornamento programmato del prodotto.

_ACP2E-3674_

### Imposta

#### L&#39;importo dell&#39;imposta non viene aggiornato quando la confezione regalo viene rimossa dal carrello

_AC-14637_

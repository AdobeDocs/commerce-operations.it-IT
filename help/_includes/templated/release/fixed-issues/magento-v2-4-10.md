---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '9924'
ht-degree: 0%
---
# Problemi risolti di Magento Open Source (v2.4.10-alpha1)

## Sono stati risolti dei problemi in v2.4.10-alpha1

Sono stati risolti 152 problemi nel codice core Magento Open Source 2.4.10-alpha1. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### [Problema] Errore di tipo in Creditmemo\Validation\QuantityValidator causato da min() con quantità stringa

Per stabilizzare le pipeline di registrazione finanziaria e prevenire errori di richiesta API durante i rimborsi automatizzati degli ordini in blocco, sono stati aggiunti guardrail di colata del tipo di dati alla fabbrica delle note di credito di vendita interne e ai livelli di convalida.

_AC-16056 - [Problema GitHub](https://github.com/magento/magento2/issues/40302) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40429) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40303)_

#### L’aggiornamento dell’attributo REST API non riesce senza attribute_id

È stato risolto un problema che impediva l’aggiornamento di un attributo di prodotto esistente tramite l’API REST se l’attributo attribute_id non veniva fornito. L’API ora identifica correttamente l’attributo utilizzando attribute_code dall’URL e lo aggiorna correttamente.

_AC-16424 - [Problema GitHub](https://github.com/magento/magento2/issues/40458) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Il campione visivo viene eliminato quando si aggiorna l’opzione tramite API REST

Per proteggere l&#39;integrità dei dati del catalogo e semplificare le integrazioni automatizzate, è stato risolto un bug nel livello di gestione dei campioni EAV in cui i valori dei campioni visivi o testuali esistenti venivano involontariamente cancellati durante gli aggiornamenti delle opzioni standard.

_AC-9199 - [Problema GitHub](https://github.com/magento/magento2/issues/37794) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40872)_

#### L’API di prezzo per livello bulk non riesce in un batch completo quando manca uno SKU

In precedenza, l’API per l’aggiornamento del prezzo per il livello bulk (POST /V1/products/tier-price) non riusciva a soddisfare l’intera richiesta quando non esistevano SKU nel payload, lasciando senza aggiornamenti gli SKU validi. Ora, gli SKU validi vengono elaborati correttamente mentre gli SKU mancanti vengono segnalati come errori per articolo, pertanto una singola voce non valida non interrompe più l’intero batch.

_ACP2E-4998 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### L’aggiornamento dell’attributo non riesce e l’etichetta Value corrisponde all’ID del valore di opzione esistente

È stato risolto il problema che impediva la creazione di una nuova opzione attributo prodotto a discesa/a selezione multipla tramite l’API REST se l’etichetta corrispondeva all’ID di un’opzione esistente. In precedenza, l’API restituiva un errore &quot;esiste già&quot; (e poteva restituire l’ID opzione errato) anche se la stessa opzione poteva essere creata correttamente tramite l’interfaccia utente di amministrazione.

_ACP2E-5107 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### API, importazione ed esportazione

#### REST API consente prezzi del prodotto negativi mentre l’interfaccia utente amministratore li blocca

L’importazione del prodotto tramite l’endpoint REST API ora rifiuta i valori negativi per gli attributi del tipo di prezzo (prezzo, prezzo_speciale, costo e campi MSRP correlati), in linea con il comportamento dell’importazione nell’interfaccia di amministrazione. In precedenza, l’API accettava i prezzi negativi in silenzio e li manteneva.

_ACP2E-4941 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### API, ordine

#### Funzione Limite frequenza ordini non compatibile con il back-end della cache di Valkey

In precedenza, il limite della frequenza di correzione veniva ignorato automaticamente e ogni richiesta veniva consentita fino a indipendentemente dal limite configurato. Dopo la correzione, le richieste che superano il limite configurato vengono rifiutate correttamente con HTTP 429.

_ACP2E-4899 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Account

#### [Problema] risolto: etichetta password errata per il modulo di accesso

È stato risolto un problema a causa del quale il campo Password nella pagina di accesso del cliente presentava un’associazione di etichetta errata. L’etichetta della password ora esegue correttamente il targeting del campo Password, consentendone la corretta identificazione tramite strumenti di test automatizzati.

_AC-16193 - [Problema GitHub](https://github.com/magento/magento2/issues/40353) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### [Problema] Convalida il tipo di input front-end per i caricamenti di file

I caricamenti del file dell’indirizzo del cliente ora verificano che il tipo di input dell’attributo di destinazione sia file o immagine prima dell’elaborazione, pertanto non è possibile abusare del testo e di altri attributi non relativi al file come destinazioni di caricamento. I tentativi di caricamento non validi restituiscono un errore di convalida chiaro anziché generare errori imprevedibili o accettare tipi di file non consentiti.

_AC-17076 - [Problema GitHub](https://github.com/magento/magento2/issues/40795) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40583)_

#### Il token cliente generato sul sito Web A può essere utilizzato sul sito Web B in una configurazione cliente con ambito sito Web

Per applicare un rigido isolamento dei dati dei clienti su istanze multi-sito, è stato risolto un gap di sicurezza nel livello di autenticazione di GraphQL in cui i token venivano convalidati in modo errato attraverso confini separati.

_AC-17299 - [Problema GitHub](https://github.com/magento/magento2/issues/40847) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40858)_

#### [Problema] Correzione deprecazione PHP 8.5: utilizzo di null come parametro chiave per array_key_exists()

È stato risolto un problema in PHP 8.5 a causa del quale l’accesso del cliente durante il check-out guest non riusciva a causa di una chiamata array_key_exists() obsoleta con una chiave null. L’accesso del cliente ora funziona correttamente senza generare l’errore di obsolescenza.

_AC-17395 - [Problema GitHub](https://github.com/magento/magento2/issues/40875) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] magento/magento2: aggiungi le traduzioni i18 a requestPasswordResetEmail e resetPassword GraphQL mutations

Per garantire un’esperienza di vetrina headless completamente localizzata, sono state aggiunte funzionalità di traduzione (i18n) agli endpoint API di recupero account cliente

_AC-9356 - [Problema GitHub](https://github.com/magento/magento2/issues/29658) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/28950)_

### Interfaccia utente amministratore

#### Il dashboard deve visualizzare gli ultimi 7 giorni per impostazione predefinita quando vengono utilizzati i dati aggregati

È stato risolto un problema a causa del quale il dashboard veniva visualizzato Oggi per impostazione predefinita quando erano abilitati i dati di vendita aggregati. Per impostazione predefinita, la dashboard ora mostra Ultimi 7 giorni quando si utilizzano dati aggregati.

_AC-13799 - [Problema GitHub](https://github.com/magento/magento2/issues/28152) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Il valore FPT nella pagina del carrello e nella pagina del prodotto sono diversi per le stesse configurazioni di un prodotto semplice

È stato risolto un problema a causa del quale i valori FPT (Fixed Product Tax) venivano visualizzati in modo diverso sulle pagine del prodotto e del carrello per la stessa configurazione dell&#39;imposta. I valori FPT vengono ora visualizzati in modo coerente nelle pagine di prodotto, catalogo, mini carrello e carrello acquisti.

_AC-17007 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Implementazione di configurazione differita

Ottimizzazione delle prestazioni che migliora le prestazioni di caricamento della configurazione risolvendo in modo differito i dati di configurazione del sistema con ambito, mantenendo al contempo il comportamento di configurazione esistente.

_ACP2E-4751 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/65f660bd)_

#### L’editor HugeRTE blocca le emoji - convalida JavaScript non riuscita

È stato risolto il problema che impediva a HugeRTE di salvare il contenuto contenente emoticon utf8mb4 (ad esempio 🔵⚪🔴) durante la modifica all&#39;interno dei modali di tipo contenuto di PageBuilder (Testo, Banner, Diapositiva). Precedentemente, la configurazione di convalida wysiwyg per questi moduli modali ha risolto `allowUtf8mb4` in `false`, causando il rifiuto da parte dell&#39;editor di caratteri UTF-8 a 4 byte anche nelle installazioni in cui il database supporta completamente utf8mb4.

_ACP2E-4822 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### L’amministratore viene disconnesso quando si visualizzano clienti con rubriche di grandi dimensioni nella pagina di modifica del cliente in Admin Panel (Pannello di amministrazione)

È stato risolto un problema che si verificava alla disconnessione dell’amministratore durante la visualizzazione di clienti con rubriche di grandi dimensioni nella pagina di modifica del cliente nel pannello di amministrazione

_ACP2E-4875 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Gli ordini non vengono visualizzati nella griglia vendite

È stato risolto un problema a causa del quale i nuovi ordini venivano ritardati nella visualizzazione nelle griglie di vendita quando era abilitata l’indicizzazione asincrona della griglia, a causa della reimpostazione del cursore di riconciliazione una volta recuperata l’entità più recente. Le nuove voci vengono ora visualizzate nella griglia alla successiva esecuzione del cron.

_ACP2E-4893 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Interfaccia utente amministratore, Ordine

#### Viene visualizzato un prezzo errato per il prodotto raggruppato nell’ordine di creazione amministratore quando due prodotti raggruppati condividono lo stesso prodotto semplice

È stato risolto un problema a causa del quale il prezzo di un prodotto raggruppato nell’ordine di creazione amministratore non veniva calcolato correttamente quando due prodotti raggruppati che condividevano lo stesso prodotto semplice venivano entrambi configurati senza essere aggiunti al carrello.

_ACP2E-4965 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Interfaccia utente amministratore, Framework interfaccia utente

#### Magento2 viene reindirizzato alla home page invece di mostrare un errore con una dichiarazione di menu errata

Per ottimizzare il flusso di lavoro di sviluppo delle estensioni e garantire un caricamento stabile del back-end, è stato risolto un difetto strutturale di indirizzamento a causa del quale le dichiarazioni del menu di amministrazione non valide attivavano errori di loop silenziosi del browser invece di visualizzare messaggi diagnostici actionable.

_AC-7543 - [Problema GitHub](https://github.com/magento/magento2/issues/36632) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40881)_

### Analytics/Generazione rapporti

#### [QUANS] È possibile visualizzare l&#39;ID e il nome dell&#39;e-mail del cliente nella tabella KPI cliente in Reporting avanzato

Adobe Commerce ora include il nome, il centro e il cognome del cliente nei dati esportati in Advanced Reporting, consentendo alla tabella KPI cliente di visualizzare il nome del cliente. In precedenza, veniva esportato solo un identificatore cliente codificato, pertanto gli esercenti non potevano identificare i clienti per nome nella funzione di reporting avanzato.

_ACP2E-3928 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### Inserimento pesante su sales_bestsellers_aggregated_month

Sono state migliorate le prestazioni per il cron aggregate_sales_report_bestsellers_data.

_ACP2E-4559 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Il payload dell’evento Add to Cart è nel formato e-commerce avanzato legacy di Universal Analytics anziché nel formato e-commerce GA4.

Prima della correzione, gli eventi di e-commerce inviati a Google Analytics 4 tramite Google Tag Manager utilizzavano il formato legacy Universal Analytics e mancavano diversi eventi di pagamento. Dopo la correzione, tutti gli eventi di e-commerce utilizzano il formato GA4 corretto e viene tracciato il funnel di pagamento completo.

_ACP2E-5176 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### B2B, Ordine

#### Guida sulla pulizia delle tabelle di preventivo di 59M+ (sales_clean_quotes non è in grado di eseguire)

È stato risolto il problema relativo al timeout del processo cron `sales_clean_quotes` nelle istanze con tabelle di virgolette grandi. In precedenza, la query di pulizia selezionava inutilmente tutte le colonne dalla tabella `negotiable_quote`, facendo in modo che MySQL eseguisse un file completo su milioni di righe; ogni preventivo veniva eliminato singolarmente tramite il livello del modello PHP, aggiungendo il costo delle prestazioni.

_ACP2E-4891 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Carrello e pagamento

#### Notifica Aggiungi al carrello per prodotti correlati

È stato risolto un problema a causa del quale la notifica Aggiungi al carrello non includeva il prodotto correlato durante l’aggiunta di un prodotto e del relativo prodotto correlato.
La notifica visualizza ora i nomi di entrambi i prodotti aggiunti al carrello.

_AC-11976 - [Problema GitHub](https://github.com/magento/magento2/issues/27164) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] Aggiornamento di CartRepositoryInterface.php

Il file CartRepositoryInterface.php è stato aggiornato per dichiarare le eccezioni che possono essere generate durante il salvataggio di un carrello. In questo modo l’interfaccia rimane coerente con l’implementazione del carrello sottostante.

_AC-13323 - [Problema GitHub](https://github.com/magento/magento2/issues/39328) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### [Bug] Il campo Società nell&#39;indirizzo di spedizione è impostato su null in una configurazione multi-store quando si aggiunge un nuovo indirizzo durante la fase di spedizione dell&#39;estrazione

È stato risolto un problema a causa del quale il campo Società non veniva salvato quando i clienti aggiungevano un nuovo indirizzo di spedizione durante il pagamento in una configurazione multi-store. Il valore Società viene ora salvato correttamente nel preventivo, nell&#39;ordine effettuato e nella rubrica del cliente.

_AC-13456 - [Problema GitHub](https://github.com/magento/magento2/issues/39424) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal > Mancata corrispondenza dati cliente (prefisso, nome, cognome)

È stato risolto un problema a causa del quale i dettagli dei nomi dei clienti venivano mappati in modo errato durante il flusso di pagamento SEPA PayPal. Prefisso, Nome e Cognome ora vengono compilati correttamente nell’ordine senza alcuna mancata corrispondenza.

_AC-15366 - [Problema GitHub](https://github.com/magento/magento2/issues/39061) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Flag free_shipping non corretto per i prodotti virtuali

È stato risolto un problema a causa del quale il flag free_shipping veniva impostato in modo errato per i prodotti virtuali quando al carrello venivano aggiunti più articoli. Il flag è ora impostato correttamente per tutti gli articoli quando viene applicata la regola di spedizione gratuita applicabile.

_AC-15648 - [Problema GitHub](https://github.com/magento/magento2/issues/40184) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Componente aggiuntivo al carrello per gli ospiti: sezione &quot;carrello&quot; mini-carrello/dati cliente che riporta il carrello come vuoto nonostante la persistenza corretta dell’articolo

È stato risolto un problema a causa del quale il mini-carrello guest non rifletteva gli articoli subito dopo l’aggiunta di un prodotto al carrello. Il contatore del mini-carrello e il menu a discesa ora vengono aggiornati correttamente e i prodotti aggiunti vengono visualizzati nel carrello come previsto.

_AC-17973 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### messaggi di errore in linea del componente aggiuntivo al carrello di AJAX semanticamente role=&quot;alert&quot; perso

È stato risolto un problema a causa del quale i messaggi di errore del componente aggiuntivo al carrello di AJAX erano visibili nella vetrina ma non venivano annunciati dagli assistenti vocali. Gli errori di aggiunta al carrello vengono ora visualizzati in un&#39;area accessibile role=&quot;alert&quot; per il supporto dell&#39;accessibilità corretto.

_AC-18036 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Ignora le regole successive per l&#39;importo di spedizione

Per garantire prezzi promozionali accurati e una rigorosa conformità con le regole di sconto configurate, è stato risolto un errore nel calcolatore delle regole del carrello dove gli sconti di spedizione a priorità inferiore venivano applicati in modo errato

_AC-9612 - [Problema GitHub](https://github.com/magento/magento2/issues/37985) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40869)_

#### Ordini duplicati creati anche se l’errore viene attivato

È stato risolto un problema a causa del quale era ancora possibile effettuare gli ordini con un indirizzo cliente non valido.

_ACP2E-4774 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Impatto delle prestazioni del prodotto configurabile sul pagamento (totali-informazioni, stime-moduli di spedizione)

Prima della correzione, le richieste di pagamento, come le informazioni totali e i metodi di spedizione delle stime, potevano diventare notevolmente più lente per i prodotti configurabili con molti prodotti secondari quando il primo figlio vendibile appariva in ritardo nell’elenco dei prodotti secondari. Dopo la correzione, questa riduzione delle prestazioni non si verifica più e i tempi di risposta rimangono costanti indipendentemente dalla posizione del primo bambino vendibile.

_ACP2E-4805 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Totali del carrello ricalcolati in ogni visualizzazione della pagina del carrello

Totali richieste carrello ottimizzati nella pagina del carrello. I totali del carrello vengono ricalcolati due volte in ogni visualizzazione della pagina del carrello.

_ACP2E-4817 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Le regole di convalida della città e della via dell&#39;attributo dell&#39;indirizzo del cliente (EAV) sono in conflitto con le regole di convalida codificate.

È stato risolto un problema a causa del quale la convalida della città rifiutava erroneamente i nomi di città validi più lunghi di 100 caratteri (il limite del database è di 255) e gli indirizzi stradali più lunghi di 255 caratteri potevano essere troncati automaticamente nel database senza\
errore di convalida restituito. Entrambe le convalide ora applicano limiti allineati con il vincolo di colonna più stretto del database in tutte le tabelle degli indirizzi.

_ACP2E-4861 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Storefront] Messaggio aggiuntivo al carrello &quot;qtà richiesta non disponibile&quot; non renderizzato in modo intermittente nel PDP

È stato risolto il problema relativo al messaggio di indisponibilità delle scorte (&quot;La quantità richiesta non è disponibile. Ridurre la quantità.&quot;) non veniva visualizzato in modo intermittente nella pagina dei dettagli del prodotto dopo un tentativo non riuscito di aggiunta al carrello. In precedenza, la pagina poteva essere aggiornata in modo silenzioso senza alcun feedback di errore quando un acquirente faceva ripetutamente clic su Aggiungi al carrello per un prodotto le cui scorte disponibili erano già completamente riservate nel carrello.

_ACP2E-5071 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### Carrello acquisti persistente cancellato alla scadenza della sessione naturale quando Cancella persistenza alla disconnessione = Sì

È stato risolto il problema per cui il carrello acquisti persistente veniva cancellato alla scadenza della sessione del browser. In precedenza, quando era abilitata l’opzione Clear Persistence on Log Out (Cancella persistenza alla disconnessione), una sessione scaduta svuotava il carrello e rimuoveva il cookie persistente anche se l’acquirente non si era disconnesso.

_ACP2E-5088 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Offerta ospite customer_email non risincronizzata dall&#39;indirizzo di fatturazione dopo restoreQuote() durante un nuovo tentativo di pagamento

È stato risolto un problema a causa del quale, se si riprovava a eseguire un check-out guest non riuscito, veniva inviato l’ordine con l’e-mail precedentemente immessa invece di quella aggiornata.

_ACP2E-5188 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Carrello e pagamento, GraphQL

#### L’API GraphQL per le offerte può assegnare ai campi delle offerte oggetti valuta invece dei codici valuta ISO

È stata aggiornata l&#39;API GraphQL preventivo per assegnare codici valuta ISO ai campi della valuta del preventivo e del relativo archivio anziché assegnare oggetti valuta.

_ACP2E-5229 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catalogo

#### [Problema] miglioramenti al file module.xml per i moduli Magento_ConfigurableProductGraphQl, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting e Magento_Swatches.

È stata ottimizzata l’architettura di dichiarazione dei moduli rimuovendo le dipendenze ridondanti di Magento_Catalog da quattro sottomoduli core. Questa pulizia risolve inutili duplicazioni nella struttura delle dipendenze, semplifica i calcoli degli ordini di caricamento dei moduli e migliora la gestibilità del framework a lungo termine senza introdurre modifiche che causano interruzioni.

_AC-10762 - [Problema GitHub](https://github.com/magento/magento2/issues/30675) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30638)_

#### Possibile perdita di memoria nella funzione getUsedProducts per gli elementi configurabili

È stato risolto un problema che causava un aumento nel tempo dei tempi di esecuzione e dell’utilizzo della memoria dovuto all’elaborazione di più prodotti configurabili.
I prodotti configurabili possono ora essere elaborati senza il progressivo rallentamento e l&#39;aumento della memoria.

_AC-10942 - [Problema GitHub](https://github.com/magento/magento2/issues/37639) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/8c058c2e)_

#### Filtro Acquista per categoria visibile per categorie non di ancoraggio

È stato risolto un problema che causava la visualizzazione del filtro Shop By Category (Acquista per categoria) su categorie non di ancoraggio anche quando il filtro delle categorie era disabilitato in Admin (Amministrazione).
Il filtro è ora nascosto nella vetrina in base all’impostazione configurata.

_AC-10945 - [Problema GitHub](https://github.com/magento/magento2/issues/38379) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### Il tipo di dati di apply_rule_ids in Quote e Quote Item è diverso

Per garantire la coerenza assoluta dello schema del database ed evitare incongruenze nei dati critici del carrello negli archivi promozionali di volumi elevati, le definizioni promo attive di tracciamento delle colonne di dati sono state espanse tra le strutture di checkout principali.

_AC-14518 - [Problema GitHub](https://github.com/magento/magento2/issues/39838) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40540)_

#### Impossibile ottenere l&#39;attributo `decimal` con ambito di raccolta prodotti se il prezzo è con ambito globale

Per garantire una precisa determinazione dei prezzi della vetrina e il rendering degli attributi nelle impostazioni internazionali, è stato risolto un bug della raccolta dati di base a causa del quale i valori decimali specifici del punto vendita venivano erroneamente sostituiti da valori globali predefiniti.

_AC-15806 - [Problema GitHub](https://github.com/magento/magento2/issues/40218) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40419)_

#### Gestione errata dei parametri GET

Per migliorare la stabilità della piattaforma e salvaguardare il funnel di pagamento, è stato aggiunto un livello di convalida dell’input a livello di blocco per impedire che le query URL non corrette si interrompano nelle pagine dei prodotti della vetrina.

_AC-16262 - [Problema GitHub](https://github.com/magento/magento2/issues/40405) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes viene attivato su tutte le query del carrello

Per ridurre i vincoli di esecuzione del database ed eliminare gli hit del database non ottimizzati durante i checkout del cliente, il plug-in di configurazione del prodotto per le regole di vendita è stato ottimizzato per l’esecuzione condizionale e l’utilizzo delle strutture di caching.

_AC-16559 - [Problema GitHub](https://github.com/magento/magento2/issues/40226) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40251)_

#### [Problema] [PHPDOC] Correggi il parametro orderComment delle funzioni in Magento\Sales\Model\Order

Per eliminare le restrizioni di digitazione, migliorare l&#39;accuratezza dell&#39;analisi statica e migliorare l&#39;esperienza degli sviluppatori con rigorosi motori di linting come PHPStan (livello 5 o superiore), i blocchi di documentazione strutturale in linea sono stati standardizzati all&#39;interno dei sottosistemi core degli ordini di vendita.

_AC-16759 - [Problema GitHub](https://github.com/magento/magento2/issues/39575) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39572)_

#### [Problema] [Bug] GraphQL SearchCriteriaValidator non caricato — rimosso dalla sostituzione dell&#39;array di modulo-graph-ql di.xml

Per mantenere una valida convalida delle query e applicare i guardrail della piattaforma, è stato risolto un difetto di configurazione dell’iniezione di dipendenza (DI) in cui il livello SearchCriteriaValidator veniva inavvertitamente disabilitato.

_AC-16959 - [Problema GitHub](https://github.com/magento/magento2/issues/40762) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40742)_

#### strpos() prevede che il parametro 1 sia una stringa, matrice specificata | magento/modulo-eav

Per proteggere la stabilità della vetrina e fornire un&#39;esperienza di individuazione dei clienti ininterrotta, è stato risolto un difetto critico di mancata corrispondenza dei tipi all&#39;interno dei motori di elaborazione della ricerca avanzata del catalogo.

_AC-1706 - [Problema GitHub](https://github.com/magento/magento2/issues/33588) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40422)_

#### Quando il cliente visita una pagina, vengono creati record di offerta vuoti

Se si visita la pagina di prodotto nella vetrina, in alcune situazioni non vengono creati record di preventivo vuoti.
Precedentemente venivano creati record di offerta vuoti quando il cliente visita una pagina di prodotto nella vetrina

_ACP2E-4682 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Nella pagina dei dettagli del prodotto, l’attributo &quot;Weight&quot; (Peso) non mostra il suffisso dell’unità nella sezione &quot;Additional Information&quot; (Informazioni aggiuntive)

È stato risolto il problema che causava la visualizzazione dell&#39;attributo Weight nella pagina del prodotto Storefront solo di un valore numerico non elaborato nella sezione &quot;Ulteriori informazioni&quot; o &quot;Ulteriori informazioni&quot; senza l&#39;unità di misura configurata (kg o kg).

_ACP2E-4808 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud] l&#39;attivazione della regola del prezzo del catalogo non si riflette in Live Search fino alla prossima risincronizzazione forzata — ritardo sincronizzazione feed prezzi

È stato risolto un problema a causa del quale l&#39;attivazione di una regola del prezzo di catalogo non aggiornava i prezzi in Live Search fino a una successiva forzatura della risincronizzazione. L’indicizzatore del feed dei prezzi poteva essere eseguito prima che l’indicizzatore della regola del catalogo da cui dipende fosse terminato, e quindi esportava prezzi non aggiornati. Gli indicizzatori con dipendenze non completate vengono ora rinviati alla successiva esecuzione cron, pertanto il feed di prezzo viene sempre eseguito in base a prezzi aggiornati.

_ACP2E-5029 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Il testo alternativo (etichetta) non viene salvato per una nuova immagine prodotto aggiunta

È stato risolto un problema a causa del quale il testo alt (etichetta) di un’immagine di prodotto appena caricata non veniva salvato quando il file caricato veniva rinominato al momento del salvataggio a causa di una collisione del nome file nella galleria multimediale. In precedenza, gli attributi del ruolo dell’immagine (immagine, immagine_piccola, miniatura) venivano memorizzati correttamente, ma gli attributi *_etichetta corrispondenti venivano rilasciati automaticamente, lasciando vuoto il testo alt nelle pagine di ricerca e elenco in vetrina. Il gestore di creazione della raccolta ora risolve il file rinominato nella voce dell&#39;immagine di origine, in modo che l&#39;etichetta venga mantenuta per tutti i ruoli immagine assegnati. Di conseguenza, il testo alternativo immesso durante la creazione del prodotto viene salvato e renderizzato in modo affidabile nella vetrina.

_ACP2E-5216 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

#### Errore di deprecazione di PHP 8.5 &quot;null come offset array&quot; apertura della pagina Aggiungi prodotto in amministrazione quando l’utente non dispone della risorsa Modifica stato prodotto

In precedenza, gli utenti amministratori che non disponevano dell’autorizzazione &quot;Modifica stato prodotto&quot; potevano rilevare un errore di deprecazione &quot;null come offset array&quot; all’apertura della pagina Aggiungi prodotto. Questo problema è stato risolto per consentire il caricamento corretto della pagina indipendentemente dalle autorizzazioni di stato del prodotto dell’utente.

_ACP2E-5248 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catalogo, GraphQL

#### [GraphQl] prodotti eseguono query sui problemi del filtro prezzi con prezzi netti immessi in adminhtml

È stato risolto un problema a causa del quale la query dei prodotti GraphQL non considerava le imposte quando si applicava un filtro prezzi.
Il filtro prezzi ora utilizza il prezzo comprensivo di imposta visualizzato, in modo da restituire solo i prodotti all’interno dell’intervallo di prezzo specificato.

_AC-6883 - [Problema GitHub](https://github.com/magento/magento2/issues/36337) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

### Catalogo, SEO

#### La categoria url_path non viene sincronizzata in seguito alla modifica di url_key per tutte le visualizzazioni del punto vendita

In precedenza, la modifica della chiave URL di una categoria nell’ambito &quot;Tutte le visualizzazioni archivio&quot; poteva lasciare le categorie discendenti con ambito archivio con un percorso_URL non aggiornato o con prefisso errato, mentre la modifica di una categoria con la sostituzione url_path specifica per il negozio poteva scegliere la chiave URL pre-modifica invece di quella appena immessa. Questo problema è ora risolto: le modifiche della chiave URL vengono applicate correttamente a catena a tutti i discendenti con ambito store nell&#39;ordine gerarchico corretto con il percorso padre corretto e la sostituzione del percorso url_path con ambito store di una categoria viene ricalcolata utilizzando la chiave URL appena modificata, in modo che gli URL con ambito store rimangano accurati subito dopo il salvataggio.

_ACP2E-5113 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Cloud, Framework

#### Regressione delle prestazioni e archiviazione della cache non corretta con SymfonyL2 abilitato

È stato risolto un problema che causava il reindirizzamento silenzioso del percorso di archiviazione della cache L1 come percorso assoluto (ad esempio, /dev/shm) alla directory var/ e un problema di prestazioni separato in cui l’invalidazione dei tag della cache su cataloghi di grandi dimensioni poteva causare ritardi significativi dei tempi di risposta a causa di un’operazione Redis di blocco.

_ACP2E-4989 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Contenuto

#### La richiesta di anteprima AJAX di Page Builder restituisce un errore 500 con la cache di traduzione disabilitata

Ora l’anteprima di PageBuilder viene riprodotta correttamente indipendentemente dal fatto che la cache delle traduzioni sia abilitata o disabilitata. In precedenza, il rendering dell’anteprima di PageBuilder non riusciva quando la cache delle traduzioni era disabilitata.

_ACP2E-5118 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### I caricamenti GIF animati vengono convertiti in PNG quando l’opzione Abilita raccolta file multimediali vecchi è abilitata

È stato risolto un problema a causa del quale le immagini GIF animate caricate tramite la galleria di file multimediali venivano convertite in PNG quando la galleria di file multimediali legacy era abilitata. In precedenza, quando era attivata l’opzione Abilita ridimensionamento front-end, le GIF animate caricate tramite la Raccolta vecchi file multimediali perdevano l’animazione e venivano salvate come file PNG statici. Le GIF animate vengono ora caricate e memorizzate nel loro formato originale.

_ACP2E-5232 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Contenuto/CMS

#### [Problema] Correggi la scheda della galleria di prodotti quando un&#39;etichetta di attributo dell&#39;immagine contiene una virgoletta singola

Per garantire un’esperienza di gestione del catalogo affidabile e ininterrotta nel pannello di amministrazione, è stato risolto un difetto di formattazione di JavaScript che ha completamente interrotto l’interfaccia back-end dell’area di lavoro del prodotto

_AC-16474 - [Problema GitHub](https://github.com/magento/magento2/issues/40519) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40870)_

#### [Problema] Migliora le prestazioni quando si accede all&#39;URL dell&#39;immagine ridimensionata ma non esiste ancora.

Per massimizzare i tempi di risposta della distribuzione delle risorse, ridurre in modo significativo l’I/O del disco del server ed evitare picchi severi del processore del server, il sottosistema di generazione delle immagini del catalogo è stato ottimizzato per gestire gli URL dei contenuti multimediali mancanti esclusivamente su richiesta.

_AC-16547 - [Problema GitHub](https://github.com/magento/magento2/issues/40399) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40388)_

#### Regressione: il componente URI non codificato UTF-8 genera ancora il messaggio &quot;Impossibile serializzare il valore&quot; in CatalogWidget il 2.4.7-p5

Per eliminare gli errori critici di rendering causati da un traffico web di produzione errato, il blocco del widget catalogo è stato rinforzato per gestire con facilità le sequenze di dati non UTF-8 all’interno degli URL richiesti.

_AC-17264 - [Problema GitHub](https://github.com/magento/magento2/issues/40824) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40825)_

#### `Using null as an array offset is deprecated, use an empty string instead` durante la modifica dell&#39;ambito di configurazione della progettazione globale

È stato risolto un problema a causa del quale la modifica dell’ambito Globale in Contenuto > Progettazione > Configurazione restituiva un errore HTTP 500 su PHP 8.5 a causa di un offset di array null obsoleto. La configurazione di progettazione globale ora si apre correttamente senza l’errore.

_AC-17456 - [Problema GitHub](https://github.com/magento/magento2/issues/40886) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Framework

#### SELEZIONARE da media_storage_file_storage quando l&#39;archiviazione del database dei supporti non è in uso o è disabilitata

Per ridurre il sovraccarico delle query sul database ed eliminare le eccezioni di sistema rumorose, il livello di sincronizzazione dei file multimediali è stato ottimizzato in modo da ignorare i controlli di archiviazione del database quando il sistema è configurato in modo esplicito per utilizzare il file system locale

_AC-10586 - [Problema GitHub](https://github.com/magento/magento2/issues/38116) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40480)_

#### Errore irreversibile generato nel costruttore di eccezioni quando l’archivio dei cookie è un array

È stato risolto un problema che causava un errore irreversibile PHP a causa di un valore di cookie di archivio non valido.
Magento ora genera correttamente un’eccezione &quot;Parametro di archivio non valido&quot; quando il cookie di archivio contiene un valore non valido.

_AC-10888 - [Problema GitHub](https://github.com/magento/magento2/issues/38365) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [Problema] Utilizza la costante statica in Magento\Customer\Model\Address\Config

È stato risolto un problema a causa del quale le classi di configurazione degli indirizzi personalizzati dovevano duplicare getFormats() per utilizzare un percorso del modello di indirizzo personalizzato. Le configurazioni di indirizzi personalizzate possono ora definire il proprio percorso di modello utilizzando una costante statica senza duplicare il metodo.

_AC-12906 - [Problema GitHub](https://github.com/magento/magento2/issues/39135) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Impossibile utilizzare processFilter sulla raccolta di prodotti

È stato risolto un problema che causava un errore PHP in seguito all’applicazione di più filtri a una raccolta di prodotti utilizzando FilterProcessor. Le raccolte di prodotti ora possono essere filtrate correttamente utilizzando più condizioni di filtro.

_AC-15018 - [Problema GitHub](https://github.com/magento/magento2/issues/40014) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### Potenziale problema di prestazioni dell’indicizzatore per cataloghi di grandi dimensioni: inserimento in blocco e blocco dell’intera tabella CL per identificare la versione più recente

Per salvaguardare le prestazioni del database su cataloghi di grandi dimensioni aziendali, la pipeline dell’indicizzatore del database di sistema è stata rinforzata per analizzare le modifiche dei dati pianificate in batch limitati, eliminando i blocchi del database ad alta pressione.

_AC-16238 - [Problema GitHub](https://github.com/magento/magento2/issues/40331) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40546)_

#### [Problema] Miglioramento delle prestazioni

Per eliminare l&#39;allocazione di memoria non necessaria e ridurre il sovraccarico di elaborazione in fase di runtime, sono state reimpostate diverse routine di manipolazione delle stringhe di base per utilizzare il comportamento nativo ottimizzato di PHP.

_AC-16565 - [Problema GitHub](https://github.com/magento/magento2/issues/40383) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40375)_

#### [Problema] Risoluzione del supporto per GLOB_BRACE su sistemi Linux non GNU

Per garantire una funzionalità di distribuzione fluida in ambienti di virtualizzazione leggeri, è stato corretto un bug critico di individuazione del percorso per ripristinare completamente il supporto dell&#39;esecuzione per i sistemi che utilizzano librerie non GNU, come le immagini Docker Alpine Linux.

_AC-16568 - [Problema GitHub](https://github.com/magento/magento2/issues/40552) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40538)_

#### Parametri di marketing aggiunti nuovamente alla query utilizzata per la creazione di identificatori FPC incorporati

Per migliorare le percentuali di hit della cache ed eliminare le regressioni delle prestazioni del server, è stato risolto un problema strutturale nel sistema nativo integrato Full Page Cache (FPC) in cui i parametri di query di marketing e tracciamento venivano accidentalmente reintrodotti nelle firme degli identificatori della cache.

_AC-16583 - [Problema GitHub](https://github.com/magento/magento2/issues/40350) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40349)_

#### Aggiunta del supporto per oggetti semplici con proprietà alzate di livello nella comunicazione della coda di messaggi

Per supportare le pratiche di sviluppo PHP moderne e semplificare i flussi di lavoro dell’architettura asincrona, il motore di riflessione del framework è stato migliorato per elaborare in modo nativo gli oggetti di trasferimento dati (DTO, Data Transfer Objects) utilizzando proprietà di costruzione pubbliche, promosse e di sola lettura.

_AC-16672 - [Problema GitHub](https://github.com/magento/magento2/issues/36660) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40457)_

#### [Problema] Correzione: il tipo di colonna reale introspezione ignora i processori non firmati/nullable e utilizza i valori predefiniti

Per garantire un tracciamento accurato della configurazione del sistema, è stato risolto un difetto di astrazione del database per cui i comandi di verifica dello schema dichiarativo segnalavano in modo permanente le modifiche in sospeso per le colonne DOUBLE UNSIGNED prive di attributi di precisione o scala espliciti.

_AC-16758 - [Problema GitHub](https://github.com/magento/magento2/issues/40646) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40582)_

#### [Funzionalità] supporta lo stato &quot;disabilitato&quot; per le singole opzioni selezionate nella configurazione amministratore

Per migliorare la flessibilità del modulo back-end e fornire agli sviluppatori un controllo granulare del layout, è stato introdotto il supporto a livello di framework per contrassegnare i singoli tag di opzione come non selezionabili all’interno degli elementi del modulo.

_AC-16761 - [Problema GitHub](https://github.com/magento/magento2/issues/40564) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40565)_

#### Prestazioni ⚡: memoria mancante in StoreManager e sovraccarico del plug-in nel modulo Store

Per ridurre drasticamente l&#39;esecuzione di CPU e ridurre al minimo l&#39;abbandono della memoria dell&#39;applicazione, è stata implementata una routine di caching dei valori di configurazione critici per intercettare i processi di controllo degli archivi ridondanti.

_AC-16838 - [Problema GitHub](https://github.com/magento/magento2/issues/40706) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40732)_

#### [Problema] correzione: rimuovere il percorso del codice openssl_free_key() inattivo in JwkFactory

Per ripulire il debito tecnologico strutturale e allineare gli strumenti di crittografia con profili di esecuzione moderni, sono stati eliminati dal back-end dell’utility JSON Web Key gli hook legacy che liberano risorse.

_AC-16958 - [Problema GitHub](https://github.com/magento/magento2/issues/40761) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40688)_

#### [Problema] ortografia correzione PHPDoc

Per mantenere standard di qualità del codice elevati e migliorare la precisione dei suggerimenti di codice dell’ambiente di sviluppo integrato (IDE), sono state applicate pulizia strutturale ai livelli della documentazione del codice in linea nei moduli framework di base.

_AC-16960 - [Problema GitHub](https://github.com/magento/magento2/issues/40763) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40745)_

#### [Problema] perf(di:compile): memorizzare nella cache le istanze ReflectionClass in Type, Config/Reader e ClassReader

Per accelerare in modo significativo i tempi di compilazione e massimizzare il throughput di distribuzione di Continuous Integration (CI), il backend del compilatore di iniezione di dipendenza interna (`setup:di:compile`) è stato ottimizzato per eliminare i cicli di riflessione PHP ridondanti.

_AC-17077 - [Problema GitHub](https://github.com/magento/magento2/issues/40796) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40615)_

#### [Problema] Aggiorna Filter.php per consentire `{{block template="Magento_Module::path/to/template.phtml"}}` e imposta \Magento\Framework\View\Element\Template come classe predefinita

Per semplificare la creazione di contenuti e allineare le direttive CMS agli standard di layout dei modelli, è stato migliorato il sistema core di elaborazione dei tag di markup, in modo da supportare le dichiarazioni a blocchi senza una definizione esplicita della classe.

_AC-17078 - [Problema GitHub](https://github.com/magento/magento2/issues/38477) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38469)_

#### [Problema] perf(di:compile): durante la compilazione viene letto l&#39;ambito di configurazione dell&#39;intercettazione della memoria

Per accelerare notevolmente le distribuzioni dei siti e la compilazione di back-end automatizzata, il compilatore di iniezione delle dipendenze (`setup:di:compile`) è stato ottimizzato per eliminare le operazioni di analisi XML ridondanti.

_AC-17313 - [Problema GitHub](https://github.com/magento/magento2/issues/40852) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40614)_

#### Aggiorna underscore.js a 1.13.8 per evitare la vulnerabilità della sicurezza

La libreria Underscore.js inclusa nel pacchetto (lib/web/underscore.js) è stata aggiornata dalla versione 1.13.7 alla versione 1.13.8. Non sono richieste modifiche di configurazione.

_AC-17349 - [Problema GitHub](https://github.com/magento/magento2/issues/40857) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/12d0be1e)_

#### magento-compositore-installer lascia silenziosamente setup/ (e altre directory mappate) non popolato quando una destinazione di distribuzione è un symlink

È stato risolto un problema che impediva silenziosamente al compositore-compositore-installer di popolare setup/ e altre directory mappate da Compositore quando la destinazione di distribuzione era configurata come collegamento simbolico. Questo potrebbe causare la perdita di file e una distribuzione Commerce incompleta.

_AC-17360 - [Problema GitHub](https://github.com/magento/magento2/issues/40864)_

#### Le chiavi di precaricamento della cache non hanno più bisogno del prefisso ID quando si utilizza l’adattatore Symfony Cache

È ora possibile configurare le chiavi di precaricamento (preload_keys) per l’adattatore Symfony Cache senza l’id_prefix della cache. In precedenza, in seguito alla configurazione documentata e all’inclusione del prefisso su ciascuna chiave (ad esempio, 061_SYSTEM_DEFAULT), le chiavi non venivano precaricate. È ora possibile specificare le chiavi esattamente come l’applicazione le richiede (ad esempio, SYSTEM_DEFAULT) e Adobe Commerce applica automaticamente id_prefix.

_AC-17407 - [Problema GitHub](https://github.com/magento/magento2/issues/40877) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3a6b9667)_

#### [Problema] Correggi la deprecazione di PHP 8.5 quando l&#39;attributo di categoria ha &#39;frontend_input&#39; ...

Correzione di un problema per cui l&#39;apertura di una categoria nel pannello di amministrazione causava un errore in PHP 8.5 quando un attributo di categoria aveva frontend_input impostato su null. Le pagine delle categorie ora si aprono e possono essere modificate senza l’errore di obsolescenza.

_AC-17499 - [Problema GitHub](https://github.com/magento/magento2/issues/40908) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [Problema] Sostituisci asserzioni PHPUnit obsolete e configurazione test-stub

È stata aggiornata la suite di test delle unità principali di Magento 2 per i futuri aggiornamenti PHPUnit, sostituendo sette utilizzi PHPUnit obsoleti. Le modifiche riguardano le asserzioni `isType()` e la configurazione `with*()` negli stub di test, modelli che attivano gli avvisi di obsolescenza nelle versioni PHPUnit correnti e sono destinati alla rimozione in PHPUnit 13 o versioni successive.

_AC-17750 - [Problema GitHub](https://github.com/magento/magento2/issues/41040) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/41033)_

#### Le marche temporali order_date e comment di GraphQL restituiscono una data di calendario errata in lingue non en_US (analisi errata IntlDateFormatter) — Correzione AC-14431 incompleta

È stato risolto un problema a causa del quale le date dell’ordine di GraphQL potevano mostrare una data di calendario non corretta per le lingue francese e tedesca.
Le date dell’ordine e le marche temporali dei commenti correlate ora restituiscono la data e l’ora corrette.
È stata migliorata la formattazione della data in modo che i valori delle date di GraphQL possano essere analizzati in modo affidabile dalle applicazioni.
Il comportamento esistente per la lingua en_US rimane invariato.

_AC-18084 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d10ab92b)_

#### [Problema] Rimuovi tag @author non consentito

Per garantire un rigoroso allineamento con le linee guida tecniche di base, è stata completata una sweep incrementale di manutenzione del codice per pulire i blocchi di documentazione delle risorse in linea in più moduli di sistema.

_AC-8366 - [Problema GitHub](https://github.com/magento/magento2/issues/37248) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36993)_

#### [Problema] Rimuovi il tag `@author` non consentito da `Magento_Catalog` (parte 2)

Per garantire il pieno allineamento con le linee guida di distribuzione del codice unificato di Magento, è stato eseguito un passaggio di pulizia incrementale per eliminare sistematicamente i commenti di file non conformi tra i modelli di risorse della vetrina principale.

_AC-8370 - [Problema GitHub](https://github.com/magento/magento2/issues/37247) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36988)_

#### Livello Prezzo Interfaccia di immagazzinaggio Elimina Il bug non elimina tutti i prezzi di livello

È stato risolto un problema in TierPriceStorage a causa del quale l’eliminazione dei prezzi del livello prodotto in più siti web non riusciva a eliminare tutti i prezzi aggiornando la logica di corrispondenza dell’ID prezzo in modo che tenesse conto dell’ID sito web assegnato.

_AC-9738 - [Problema GitHub](https://github.com/magento/magento2/issues/37949) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40557)_

#### [B2B] Gli ordini fornitore non vengono convertiti automaticamente in ordini cliente con ActiveMQ

È stato risolto un problema a causa del quale i consumatori avviati da cron non elaboravano i messaggi quando ActiveMQ veniva utilizzato con il protocollo STOMP. Di conseguenza, gli ordini di acquisto approvati automaticamente non sono stati convertiti in ordini di vendita. L’elaborazione dei messaggi per le code STOMP è ora più affidabile e coerente con le implementazioni delle code DB e AMQP.

_ACP2E-4349 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/08b91f1a) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/239464da)_

#### Esporta errori con lo storage AWS S3 configurato

L’esportazione del prodotto ora funziona correttamente quando è configurato lo storage remoto AWS S3. In precedenza, non era possibile scrivere i file esportati in S3 a causa di una risoluzione del percorso non valida nel driver di archiviazione.

_ACP2E-4786 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Indicizzatori bloccati nel ciclo self-lock con provider &#39;use_application_lock&#39; e &#39;file&#39;

È stato risolto un problema a causa del quale gli indicizzatori si bloccavano indefinitamente durante la reindicizzazione quando l’impostazione use_application_lock dell’indicizzatore era abilitata insieme al provider del blocco file. Le operazioni di reindicizzazione ora vengono completate come previsto.

_ACP2E-5027 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Prestazioni lente con le variabili MAGENTO_DC impostate nell’interfaccia utente cloud

Dopo la correzione, la configurazione di distribuzione non viene ricaricata ogni volta che la chiave richiesta non è presente e vengono definite alcune variabili env.

_ACP2E-5094 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD] Il percorso URL non valido restituisce HTTP 500 invece di 404 nel router di riscrittura URL

È stato risolto il problema a causa del quale un URL della vetrina non valido restituiva una pagina di errore HTTP 500 invece di una pagina standard 404 Non trovato. In precedenza, alcuni percorsi di richiesta non validi causavano un errore non rilevato durante la risoluzione della riscrittura URL.

_ACP2E-5154 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### [Compatibilità PHP 8.5 di CLOUD] — ComponentRegistrar::getPath() con array null: offset arresta l&#39;installazione:static-content:deploy (compact strategy) in 2.4.9

È stato risolto un problema a causa del quale `setup:static-content:deploy` non riusciva in PHP 8.5 con un errore &quot;Using null as an array offset&quot; (Utilizzo di null come offset di array) durante la compilazione dei file LESS del modulo che utilizzano la direttiva //@magento_import. L’implementazione di contenuti statici ora viene completata correttamente su PHP 8.5.

_ACP2E-5183 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] Falso positivo &quot;Contenuto HTML non valido fornito&quot; durante il salvataggio del blocco CMS con un href di ancoraggio seguito da un altro attributo

Il contenuto CMS contenente un collegamento di ancoraggio standard (ad esempio `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`) non attiva più un avviso di convalida &quot;Contenuto HTML non valido fornito&quot; falso o un errore di salvataggio quando è abilitato cms/wysiwyg/force_valid.

_ACP2E-5203 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Framework, GraphQL

#### L’elemento dell’array di.xml viene sostituito se la configurazione successiva utilizza una chiave numerica

Per proteggere l&#39;integrità dei dati dell&#39;architettura e migliorare l&#39;estensibilità modulare, è stato risolto un bug principale all&#39;interno del motore di analisi XML di Dependency Injection (DI), in cui le configurazioni dell&#39;array che utilizzano il tasto numerico &quot;0&quot; venivano automaticamente sovrascritte o eliminate durante la compilazione del modulo.

_AC-8102 - [Problema GitHub](https://github.com/magento/magento2/issues/36861) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart genera errori su custom_attributesV2 se il codice attributo è model

È stato risolto un problema a causa del quale addProductsToCart restituiva un errore interno del server quando un prodotto aveva un attributo personalizzato con il modello di codice. L’attributo personalizzato può ora essere recuperato correttamente tramite custom_attributesV2.

_AC-16987 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/809ba93c)_

#### Quantità GQL nulla mentre stock_status è IN_STOCK

Il campo della quantità nella query GraphQL dei prodotti ha restituito erroneamente null per i prodotti in magazzino in un magazzino MSI personalizzato. Il risolutore stava valutando la risposta sul valore di configurazione cataloginventory/options/not_available_message prima di recuperare la quantità di scorte effettiva e il valore XML predefinito di questa configurazione (2 — &quot;Articoli non sufficienti per la vendita&quot;) ha causato la restituzione di valori Null su qualsiasi nuovo archivio senza un&#39;esplicita sostituzione da parte dell&#39;amministratore.
Il controllo viene ora valutato dopo la risoluzione della quantità vendibile. null viene restituito solo quando il prodotto non dispone di scorte (saleableQty &lt;= 0) e il punto vendita è configurato in modo esplicito con &quot;articoli insufficienti per la vendita&quot;. I prodotti in magazzino restituiscono sempre la quantità effettiva vendibile, indipendentemente da questa impostazione di configurazione. La configurazione letta viene corretta anche per utilizzare l’ambito di archiviazione in modo da rispettare le sostituzioni a livello di archivio.

_ACP2E-4840 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price ignora i prezzi con ambito sito Web quando Catalog Price Scope = Sito Web

Correzione dei prezzi delle opzioni del bundle con ambito sito Web in GraphQL: è stato risolto un problema a causa del quale l&#39;esecuzione di query sulle opzioni dei prodotti del bundle tramite GraphQL restituiva prezzi globali per &quot;Tutte le visualizzazioni del negozio&quot; invece di prezzi con ambito sito Web quando l&#39;ambito del prezzo del catalogo era impostato su Sito Web. Il resolver Magento\BundleGraphQl\Model\Resolver\Links\Collection ora controlla correttamente l’ambito del prezzo e unisce i prezzi di selezione specifici per il sito web in base all’ambito del negozio richiesto.

_ACP2E-5057 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Carrello attivo duplicato creato per il cliente a causa di richieste simultanee customerCart GraphQL race condition

Il sistema ora assicura che venga creato un solo carrello attivo per cliente, indipendentemente dalla concorrenza tra richieste. In precedenza, due query simultanee di customerCart GraphQL o richieste POST /V1/carts/mine REST per lo stesso cliente autenticato senza carrello attivo potevano causare la duplicazione dei record attivi del carrello nel database.

_ACP2E-5077 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud] ha gestito GraphQlNoThatEntityException da QuoteGraphQl registrato in exception.log, causando una crescita smisurata del log

È stato risolto un problema che causava la scrittura su var/log/exception.log di errori GraphQlNoThatEntityException previsti, come quelli restituiti per un ID carrello scaduto o non valido. Questi errori gestiti vengono comunque restituiti al client come normali risposte di errore di GraphQL, ma non riempiono più il registro eccezioni.

_ACP2E-5122 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, Inventory/MSI

#### GraphQL: l’ID store passato come ID sito web in ProductStock::isProductAvailable causa l’errore &quot;sito web ... non è stato trovato&quot;

In precedenza, alcuni vetrine potevano rilevare un errore &quot;non trovato sul sito&quot; durante la verifica della disponibilità delle scorte dei prodotti durante l’aggiunta di articoli al carrello, a causa dell’ID negozio utilizzato quando era richiesto un ID sito web. Questo problema è stato risolto in modo che i controlli della disponibilità delle scorte utilizzino il contesto del sito Web corretto, evitando l&#39;errore.

_ACP2E-5242 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, Ordine

#### [Richiesta di funzionalità] Cancella i dati ridondanti di prelievo dall&#39;archivio durante la modifica del vettore di spedizione

Quando si passa dal prelievo in negozio al metodo di consegna a domicilio, l’ubicazione del prelievo e l’indirizzo del negozio associato vengono rimossi dal carrello. È necessario fornire un indirizzo di spedizione valido prima di effettuare l&#39;ordine.

_ACP2E-4973 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, prodotto

#### Chiave mancante \&quot;model\&quot; nei dati del valore della lista dei desideri

È stato risolto un problema a causa del quale la query dei dettagli della lista dei desideri tramite GraphQL restituiva un errore interno del server.
La query della lista dei desideri ora viene restituita senza l’errore &quot;Modello chiave mancante nei dati del valore della lista dei desideri&quot;.

_AC-8062 - [Problema GitHub](https://github.com/magento/magento2/issues/36909) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Importare ed esportare

#### [Problema] Correzione della visibilità iframe per l&#39;importazione

Per garantire un’interfaccia utente pulita e raffinata all’interno del pannello di amministrazione di Magento, è stato risolto un difetto di layout del modello a causa del quale un iframe di esecuzione in background interno diventava visibile ai responsabili degli archivi durante le convalide dei dati

_AC-13250 - [Problema GitHub](https://github.com/magento/magento2/issues/39267) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39265)_

#### [Problema] risolto: algoritmo hash xxh128 hardcode nell&#39;importazione del prodotto

Per ripulire i sottosistemi interni e sfruttare le linee di base di ottimizzazione dei sistemi moderne, il componente di importazione del prodotto è stato razionalizzato per utilizzare un singolo algoritmo hash permanente.

_AC-16967 - [Problema GitHub](https://github.com/magento/magento2/issues/40770) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40687)_

#### Il pulsante Importa rimane disponibile dopo gli errori di convalida quando la strategia di convalida è impostata su &quot;Interrompi in caso di errore&quot;

È stato risolto il problema a causa del quale il pulsante Importa veniva ancora visualizzato nei risultati di convalida dopo una convalida dei dati non riuscita quando la strategia di convalida era impostata su &quot;Interrompi in caso di errore&quot;. In precedenza, il pulsante veniva visualizzato e poteva essere cliccato anche se la convalida di tutti i record non era riuscita, pertanto il tentativo di importazione veniva immediatamente terminato.

_ACP2E-5124 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Installazione e amministrazione

#### [Cloud] Correzione dei codici di suddivisione ISO esistenti obsoleti

Sono stati aggiornati i codici regionali per 13 paesi, in conformità allo standard ISO 3166-2. In precedenza, alcuni codici di area non corrispondevano allo standard, il che poteva causare problemi con le integrazioni di terze parti e la conformità internazionale. Sono state aggiunte nuove regioni per Belgio, Colombia, Spagna, Francia, Italia e Lettonia. Codici di regione aggiornati per Austria, Colombia, Costa Rica, Germania, Estonia, Spagna, Finlandia, Francia, India, Islanda e Lettonia.

_ACP2E-4495 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Inventario/MSI

#### [CLOUD] gift card e relativo WF-1688 non vendibile

Il prodotto non scompare quando vengono utilizzate scorte/fonti non predefinite e viene salvato il prodotto correlato (relativo o in upselling o cross-selling).

_ACP2E-4741 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Bundle Incoerenza dello stato delle scorte di prodotto

In precedenza, quando un amministratore negozio aggiornava manualmente lo stato delle scorte di un prodotto bundle dal pannello Amministratore, la modifica non veniva applicata alla vetrina per i negozi configurati con più origini di inventario. I clienti continueranno a vedere lo stato delle scorte obsoleto nonostante le modifiche dell’amministratore.

Questo problema è stato risolto. Le modifiche dello stato delle scorte dei prodotti del bundle apportate nel pannello di amministrazione ora vengono propagate correttamente in tutte le origini di inventario e le ubicazioni di scorte configurate, garantendo ai clienti una disponibilità accurata delle scorte nella vetrina.

_ACP2E-4866 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/db712a46)_

#### &quot;Impossibile trovare l’archivio richiesto&quot; di NoThatEntityException generato da GetStockIdForCurrentWebsite.php

È stato risolto il problema che causava la registrazione di NoThatEntityException a livello CRITICO a ogni richiesta di questo tipo quando la visita a una pagina di vetrina con un parametro di query ?store= non valido. In precedenza, il plug-in MSI stock data passava il codice dell’archivio non elaborato direttamente a StoreManager::getStore() senza gestire il caso in cui l’archivio non esisteva, generando un disordine nel registro delle eccezioni.

_ACP2E-5003 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1bf25e46)_

### Ordine

#### Cancel Order Observer non eseguito quando l’ambito è front-end o webapi_rest

È stato risolto un problema a causa del quale l’annullamento di un ordine dalla vetrina o tramite l’ambito webapi_rest non eseguiva correttamente l’osservatore di annullamento. Gli importi delle carte regalo vengono ora ripristinati al credito del negozio del cliente quando l&#39;ordine viene annullato.

_AC-16353 - [Problema GitHub](https://github.com/magento/magento2/issues/40414) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### La regola prezzo carrello con utilizzo limitato non viene applicata quando si modifica un ordine esistente in Admin (ad esempio, &quot;Usi per cliente = 1&quot;)

È stato risolto un problema a causa del quale gli sconti della Regola prezzo carrello con limiti di utilizzo venivano rimossi durante la modifica di un ordine esistente in Admin. Lo sconto originale viene ora mantenuto quando l’ordine viene modificato, anche dopo il raggiungimento del limite di utilizzo.

_AC-16671 - [Problema GitHub](https://github.com/magento/magento2/issues/40624) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Errore di convalida della quantità minima nel pannello di amministrazione per i prodotti bundle

Per migliorare l’esperienza di ordinamento back-end e rimuovere i blocchi funzionali durante la generazione dei preventivi manuali, è stato risolto un errore di convalida a causa del quale i parametri degli elementi figlio non venivano valutati correttamente durante la creazione degli ordini di amministrazione.

_AC-17193 - [Problema GitHub](https://github.com/magento/magento2/issues/40812) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40863)_

#### Incoerenza della quantità di articoli figlio del bundle nella vista ordine front-end

Ora nella pagina dei dettagli dell&#39;ordine di vetrina viene visualizzata la quantità totale ordinata per ogni opzione di prodotto del bundle. In precedenza, nella colonna Quantità per ogni opzione figlio veniva visualizzata la quantità ordinata del bundle padre anziché la quantità totale ordinata per opzione.

_ACP2E-4820 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() mancante DeadlockException nuovo tentativo causa errore permanente ShipOrder/InvoiceOrder-

Le operazioni ShipOrder e InvoiceOrder ora vengono risolte correttamente in caso di blocco.
Le precedenti operazioni di spedizione ordine e ordine di fatturazione non riescono in modo permanente a causa del blocco

_ACP2E-4913 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Calcolo errato a livello di riga FPT/WEEE per gli articoli configurabili padre durante la generazione della fattura

I totali complessivi delle fatture e delle note di accredito per i prodotti configurabili ora includono correttamente l&#39;importo dell&#39;imposta sul prodotto fisso. In precedenza, gli importi a livello di riga FPT non venivano propagati all&#39;articolo dell&#39;ordine configurabile padre, causando la riduzione dei totali delle fatture e delle note di accredito rispetto al totale complessivo dell&#39;ordine dell&#39;importo FPT.

_ACP2E-4977 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Quantità di prodotti modificate all&#39;aggiornamento della pagina durante la creazione dell&#39;ordine dall&#39;amministratore

È stato risolto un problema a causa del quale l’aggiornamento della pagina poteva causare l’aggiunta ripetuta dello stesso SKU.

_ACP2E-5046 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### I processi di lavoro cron per e-mail asincrone simultanei inviano e-mail di conferma dell’ordine duplicate per lo stesso ordine

È stato risolto un problema a causa del quale i processi di lavoro e-mail simultanei potevano inviare e-mail di conferma dell’ordine duplicate per lo stesso ordine.

_ACP2E-5059 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### Memoria insufficiente per il processo cron [CLOUD] sales_clean_quotes

È stato risolto il problema che causava la mancanza di memoria del processo cron sales_clean_quotes durante la pulizia di un numero elevato di virgolette scadute. In precedenza, il processo manteneva tutte le virgolette elaborate in memoria e terminava con un errore irreversibile di esaurimento della memoria prima che tutte le virgolette scadute venissero rimosse.

_ACP2E-5137 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### Ordine, promozione

#### La regola del prezzo del carrello per la categoria a importo fisso sconta l&#39;elemento secondario del bundle dinamico non corrispondente quando la regola corrisponde all&#39;elemento padre del bundle

È stato risolto il problema a causa del quale una regola del prezzo del carrello a importo fisso con una condizione di categoria applicava erroneamente uno sconto a tutti i figli di un bundle a prezzo dinamico quando la regola corrispondeva solo al padre del bundle. In precedenza, i figli del bundle che non appartenevano alla categoria di destinazione ricevevano una quota proporzionale dello sconto invece di zero.

_ACP2E-5075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Pagamenti

#### Il comando config:show non funziona con percorsi parziali nelle versioni più recenti

Il comando `config:show` ora accetta percorsi di configurazione parziali, ad esempio pagamento, e visualizza i valori di configurazione in tale percorso. In precedenza, l&#39;esecuzione del pagamento di `php bin/magento config:show` restituiva un errore: `The "payment" path doesn't exist. Verify and try again.` invece di mostrare i valori corretti.

_AC-13908 - [Problema GitHub](https://github.com/magento/magento2/issues/39610) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40432)_

### Prestazioni

#### setup:upgrade sta modificando la modalità indicizzatore in `save` da `schedule` rallentandola enormemente

È stato risolto un problema di lunga data a causa del quale l&#39;esecuzione della configurazione bin/magento:upgrade avrebbe inavvertitamente modificato le modalità di indicizzazione da &quot;Salva secondo pianificazione&quot; a &quot;Salva al salvataggio&quot; e avrebbe eliminato e ricreato inutilmente i trigger del database, riducendo drasticamente i tempi di inattività e impedendo i colli di bottiglia delle prestazioni durante le distribuzioni in cataloghi di grandi dimensioni.

_AC-2423 - [Problema GitHub](https://github.com/magento/magento2/issues/33386) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40643)_

#### Le chiavi della cache di layout Valkey occupano molto spazio per un grande catalogo di prodotti

Precedentemente, ogni prodotto generava una propria voce di cache LAYOUT per ogni vista dello store, causando un eccessivo consumo di memoria in Redis/Valkey su cataloghi di grandi dimensioni. Ora le voci della cache di layout sono condivise tra i prodotti con lo stesso tipo, set di attributi e vista store, limitando la crescita della cache indipendentemente dalla dimensione del catalogo.

_ACP2E-4908 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### Errore di deadlock nella query del prodotto

È stato risolto un deadlock InnoDB nelle pagine con un elenco di prodotti CatalogWidget filtrato per categoria, che si verificava quando l’indicizzatore dei prezzi in modalità di pianificazione veniva eseguito contemporaneamente.

_ACP2E-5052 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] peggioramento delle prestazioni delle query di risoluzione URL Adobe Commerce

È stato risolto il problema a causa del quale la query di indirizzamento di GraphQL eseguiva sempre il rendering del contenuto completo della pagina CMS, inclusi l’esecuzione del widget Page Builder e il caricamento della raccolta di prodotti, anche quando venivano richiesti solo i metadati di indirizzamento URL (relative_url, redirect_code, type). In precedenza, ciò causava un rendering inutile di widget/prodotti e un aumento significativo delle query sul database per richiesta per le pagine CMS contenenti widget di Page Builder.

_ACP2E-5143 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Admin Customer Edit Performance tank (Amministrazione clienti) quando Customer Account Sharing è impostato su Global (Globale)

È stato risolto un problema di prestazioni nella pagina Modifica clienti amministratore a causa del quale il tempo di caricamento e la dimensione di risposta HTTP aumentavano quadraticamente quando Condividi account cliente era impostato su Globale.

_ACP2E-5164 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Prodotto

#### Il pulsante Aggiungi al carrello nella finestra a comparsa &quot;Clic per prezzo&quot; non funziona.

È stato risolto un problema che impediva al pulsante Aggiungi al carrello nella finestra a comparsa &quot;Fai clic per visualizzare il prezzo&quot; nella pagina di elenco dei prodotti di aggiungere il prodotto al carrello.
I prodotti possono ora essere aggiunti al carrello correttamente dalla finestra a comparsa.

_AC-11896 - [Problema GitHub](https://github.com/magento/magento2/issues/30356) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### I risolutori BundleGraphQL creano istanze di prodotto differite separate, superando il batch di query (N+1)

Per accelerare drasticamente il throughput di risposta API e ridurre al minimo il sovraccarico del server, il livello di risoluzione GraphQL è stato ottimizzato per applicare il batch di query vero e proprio per i prodotti bundle, eliminando perdite di database N+1 che riducono le prestazioni.

_AC-16647 - [Problema GitHub](https://github.com/magento/magento2/issues/40595) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40867)_

#### La convalida dell&#39;attributo Select e Multiselect di EAV rifiuta erroneamente le etichette di opzione con il valore &quot;0&quot;

Per migliorare l&#39;integrità dei dati ed eliminare gli errori di invio imprevisti nei moduli dei clienti e dei cataloghi, è stato risolto un errore di convalida a causa del quale le etichette delle opzioni contenenti il valore esatto della stringa &quot;0&quot; venivano erroneamente rifiutate dal framework di base EAV

_AC-16986 - [Problema GitHub](https://github.com/magento/magento2/issues/40634) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40827)_

#### Le etichette di opzione personalizzabili e i titoli di opzione personalizzabili non possono essere salvati quando il ruolo di un utente è limitato a un determinato ambito

È stato risolto un problema che causava il ripristino di etichette e titoli di opzione personalizzabili quando venivano modificati da un utente amministratore con accesso limitato a un ambito di archivio specifico.
Le etichette e i titoli aggiornati vengono ora salvati correttamente per l’ambito selezionato.

_AC-2684 - [Problema GitHub](https://github.com/magento/magento2/issues/35210)_

#### Avviso prodotto Il consumatore ignora il sistema con ambito di archiviazione/stmp/disable

Il consumer di avvisi sui prodotti ora tiene conto dell’impostazione store scoped system/stmp/disable.

_ACP2E-4870 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Pagina di confronto front-end in cui sono visualizzate traduzioni errate dell&#39;etichetta Descrizione breve

In precedenza, nella pagina Confronta prodotti, le etichette di attributi comparabili, ad esempio Descrizione breve, potevano mostrare una traduzione da una visualizzazione diversa invece di quella per lo store corrente. Ora vengono visualizzate le traduzioni corrette specifiche per lo store.

_ACP2E-4929 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

#### Il carosello del prodotto di Page Builder ignora l’ordinamento della posizione della categoria e visualizza i prodotti in ordine DESC entity_id

È stato risolto un problema a causa del quale i prodotti visualizzati in un carosello di Page Builder impostato per l&#39;ordinamento in base alla posizione della categoria apparivano in ordine errato nella vetrina. I prodotti vengono ora visualizzati nell’ordine configurato nella scheda Admin → Catalog → Categories (Categorie → prodotti).

_ACP2E-4980 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Regole di promozione

#### Calcolo dello sconto errato quando una delle regole del prezzo del carrello applicato ha il valore del passo Qtà sconto

È stato risolto un problema a causa del quale lo sconto veniva calcolato in modo errato quando venivano applicate più regole di prezzo del carrello e una regola aveva un valore di Incremento quantità sconto (Acquista X).
Gli sconti vengono ora calcolati correttamente per tutte le quantità idonee.

_AC-12307 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c10554e1)_

### Restituisce

#### RMA - API per aggiungere commenti di ritorno - Le e-mail vengono attivate al mittente (rappresentante commerciale) ma non al cliente

È stato risolto un problema a causa del quale le e-mail di commento sulla restituzione inviate tramite l’API delle restituzioni venivano inviate al rappresentante commerciale ma non al cliente.
Ora i clienti ricevono una notifica e-mail quando viene aggiunto un commento di ritorno tramite l’API con la notifica al cliente abilitata.

_AC-1138 - [Problema GitHub](https://github.com/magento/magento2/issues/33985)_

### Vendite

#### Nella colonna product_options di `[Order][REST]` sales_order_items mancano i dati quando l&#39;ordine viene effettuato dall&#39;api rest V1/orders o V1/orders/create endpoints

È stato risolto un problema a causa del quale gli elementi dell’ordine creati tramite l’API REST non includevano dati product_options completi. Le etichette di opzione personalizzate e i relativi dettagli ora vengono salvati correttamente per gli ordini creati tramite l’API REST.

_AC-15187 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### Griglia ordine cliente bloccata in modo permanente nello stato non aggiornato quando l&#39;indicizzazione della griglia asincrona è abilitata a causa di marche temporali update_at collegate

È stato risolto un problema a causa del quale la griglia ordini di vendita poteva rimanere bloccata con uno stato di ordine non aggiornato quando era abilitata l’indicizzazione asincrona della griglia. Lo stato della griglia dell’ordine ora viene aggiornato correttamente in modo da corrispondere allo stato dell’ordine corrente, compresi i casi in cui si verificano più aggiornamenti dell’ordine nello stesso secondo.

_AC-17118 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/478f8e7c)_

### Sicurezza

#### [Problema] Aggiornamento del testo DOM js.phtml reinterpretato come HTML

Per rafforzare la linea di base di sicurezza della piattaforma e ridurre al minimo il rischio di esecuzione di input dannosi, è stato eseguito il refactoring del modello di script in linea principale che gestisce gli aggiornamenti DOM dinamici per eliminare i vettori di iniezione cross-site scripting (XSS).

_AC-12118 - [Problema GitHub](https://github.com/magento/magento2/issues/38821) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38804)_

### Spedizione

#### Problema con l’API REST USPS: tassi non corretti per il peso massimo del pacchetto

Sono state corrette le stime di spedizione errate quando un ordine viene suddiviso in più pacchetti (ad esempio, sopra &quot;Peso massimo del pacchetto&quot;). Il gestore ora richiede una tariffa per ciascun pacchetto e ne totalizza gli importi, in linea con il flusso degli strumenti web legacy.

_ACP2E-4813 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6c67a9b5)_

### Imposta

#### base_wee_tax_apply_amount non è impostato per il prodotto padre

il valore base_weee_tax_apply_amount viene ora popolato per il prodotto configurabile nelle tabelle di database come sales_order_item, sales_invoitem, sales_creditmemo_item, non solo per il relativo elemento figlio

_ACP2E-4922 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Framework di test

#### [Problema] Aggiorna GraphQL test Client.php per il confronto delle sottostringhe senza distinzione tra maiuscole e minuscole

È stato risolto un problema a causa del quale i test API di GraphQL non riconoscevano le intestazioni Set-Cookie quando l’intestazione utilizzava maiuscole e minuscole diverse. I test ora gestiscono correttamente le intestazioni Set-Cookie, set-cookie e SET-COOKIE.

_AC-15337 - [Problema GitHub](https://github.com/magento/magento2/issues/39713) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Test funzionali WebAPI GraphQL estremamente lenti

Per ottimizzare le impostazioni di consegna della build e accelerare gli ambienti CI (Continuous Integration), è stato risolto un collo di bottiglia dell’infrastruttura di test trasferendo i comportamenti di cancellazione della cache dalle chiamate dei comandi di sistema esterno alla gestione nativa della memoria in-process.

_AC-15395 - [Problema GitHub](https://github.com/magento/magento2/issues/39725) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40804)_

### Framework interfaccia utente

#### Il miniart non può essere usato due volte nella stessa pagina

Per fornire agli sviluppatori front-end una maggiore flessibilità di layout, è stata risolta una limitazione di lunga data dell’interfaccia utente core, che consente l’esistenza e l’aggiornamento indipendente di più blocchi minicart (ad esempio, uno nell’intestazione e un altro nel piè di pagina) su un layout di pagina singolo.

_AC-12579 - [Problema GitHub](https://github.com/magento/magento2/issues/38958) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [Problema] fix(pagecache): riconoscere PATCH come metodo HTTP valido in VCL vernice

Il file VCL vernice predefinito di Magento ora riconosce PATCH come metodo HTTP valido, pertanto le richieste di aggiornamento parziale dell’API REST (ad esempio PATCH /rest/V1/products/:sku) vengono passate al backend invece di essere reindirizzate. In questo modo vengono corretti gli errori o il comportamento errato delle chiamate di PATCH quando la cache di pagina intera è impostata su Varish.

_AC-16954 - [Problema GitHub](https://github.com/magento/magento2/issues/40757) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40657)_

#### [Problema] Sostituisci tutti i parametri gad_* in VCL

Per eliminare le regressioni delle prestazioni causate dalle campagne pubblicitarie dinamiche, i livelli di caching dell’applicazione sono stati aggiornati per ignorare in modo proattivo tutte le stringhe di query gad_* di Google Ads. Questo impedisce ai collegamenti alle campagne esterne di annullare la validità delle cache delle pagine e rallentare le pagine di destinazione

_AC-16980 - [Problema GitHub](https://github.com/magento/magento2/issues/40781) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40780)_

#### [Problema] corretto: aggiornare il check-in della versione PHP minima a 8.3

Per evitare errori di runtime confusi e migliorare la risoluzione dei problemi di installazione per gli sviluppatori, la convalida nativa dell&#39;ambiente PHP all&#39;interno del framework di avvio del sistema è stata portata in linea con i requisiti di base effettivi dell&#39;applicazione.

_AC-17312 - [Problema GitHub](https://github.com/magento/magento2/issues/40851) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php` restituisce 500 quando `igbinary` è installato e viene utilizzata la cache di file predefinita (Vernice 503)

È stato risolto un problema a causa del quale health_check.php restituiva HTTP 500 quando igbinary veniva installato con il backend della cache dei file predefinito. Il controllo di integrità ora accetta configurazioni di cache valide senza una chiave di back-end esplicita, impedendo a Vernice di contrassegnare il back-end come non integro e di restituire HTTP 503.

_AC-17400 - [Problema GitHub](https://github.com/magento/magento2/issues/40876) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [Problema] risolto: aggiorna i tipi gzip e rimuovi la soluzione alternativa IE6 nella configurazione nginx

Per migliorare le velocità di caricamento delle pagine e ottimizzare la distribuzione delle risorse di rete, la configurazione del server di fallback è stata modernizzata per supportare meglio i componenti moderni della vetrina e rimuovere il sovraccarico tecnologico legacy

_AC-17498 - [Problema GitHub](https://github.com/magento/magento2/issues/40774) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40681)_

#### [Problema] Tentativo di correzione di graphql non attendibile OrderStatusChangeDateTest.

Per migliorare l’affidabilità dell’integrazione continua (CI) e ridurre gli errori di build falsi positivi, è stata risolta una race condition nella suite di test funzionali WebAPI. Nel test di convalida dello stato dell&#39;ordine di GraphQL (OrderStatusChangeDateTest) si sono verificati in precedenza errori intermittenti a causa di lievi disparità di tempistica tra la memoria PHP e le marche temporali MySQL

_AC-17959 - [Problema GitHub](https://github.com/magento/magento2/issues/41126) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40618)_

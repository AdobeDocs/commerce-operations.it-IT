---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Problemi risolti in Adobe Commerce (v2.4.9-alpha2)

## Problemi risolti in v2.4.9-alpha2

Sono stati risolti 118 problemi nel codice core Adobe Commerce 2.4.9-alpha2. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### Il campo Prezzo speciale fino a data non viene convalidato correttamente in applySpecialPrice

Il sistema funziona correttamente per quanto riguarda il prezzo speciale e il prezzo speciale del prodotto scadrà alla data impostata dall’amministratore o dal sistema di terze parti dall’API REST

_AC-13130 - [Problema GitHub](https://github.com/magento/magento2/issues/39169) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39690)_

#### Il corpo o i parametri della richiesta non validi causano un errore interno del server

_AC-746 - [Problema GitHub](https://github.com/magento/magento2/issues/32784) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Order &quot;base_row_total&quot; e &quot;row_total&quot; mostrano il prezzo di un singolo articolo nella risposta API REST

La risposta dell’API REST per i dettagli dell’ordine ora contiene valori corretti per gli attributi &quot;base_row_total&quot; e &quot;row_total&quot; nel caso in cui siano stati ordinati più elementi uguali

_ACP2E-3874 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### API, ordine

#### [CLOUD] problema di informazioni ordine con aspetto totale riga per 000075568 ordine

Corregge il problema per cui il valore row_total_incl_tax nella risposta API dell’ordine veniva restituito come valore residuo vicino a zero invece di 0,00 quando un articolo veniva completamente scontato.

_ACP2E-3950 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Account

#### Problema durante l’aggiornamento dell’e-mail del cliente in Admin Panel con dominio ö e .swiss

_AC-13409 - [Problema GitHub](https://github.com/magento/magento2/issues/39394) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### Lo switch abilitato per l’abbonamento alla newsletter non funziona per sito web/store

Il sistema gestisce correttamente l’abbonamento con la newsletter quando sono presenti più siti web/visualizzazioni di store quando è stata disabilitata a livello globale

_AC-14283 - [Problema GitHub](https://github.com/magento/magento2/issues/39751) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39752)_

#### Dichiarare obsoleta la condizione di &quot;Prodotto visualizzato&quot; per il segmento di clienti

_AC-14542_

#### [Problema] Rimozione della divulgazione e-mail completata

Ora il sistema visualizza un messaggio di errore che indica un messaggio e-mail errato se l’e-mail inserita non è necessaria per confermare l’account, indipendentemente dal fatto che il cliente esista o meno.

_AC-14561 - [Problema GitHub](https://github.com/magento/magento2/issues/39574) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39570)_

### Interfaccia utente amministratore

#### Il valore FPT nella pagina del carrello e nella pagina del prodotto sono diversi per le stesse configurazioni per il prodotto semplice

_AC-13066 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Non è possibile salvare le opzioni per l&#39;attributo di selezione multipla/selezione quando i moduli Campioni sono disabilitati

_AC-13071 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Il valore FPT nella pagina del carrello e nella pagina del prodotto sono diversi per le stesse configurazioni di un prodotto dinamico

_AC-13075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Colore al passaggio del mouse non applicato alle griglie statiche in amministrazione

I colori al passaggio del mouse vengono ora applicati come previsto sulle righe delle griglie statiche di amministrazione.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema GitHub](https://github.com/magento/magento2/issues/35358) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35384)_

#### Gli utenti amministratori con restrizioni non possono aggiornare in massa lo stato del prodotto

L’amministratore personalizzato può aggiornare in massa lo stato del prodotto in quanto si tratta di una proprietà a livello di sito web. Lo stato viene aggiornato solo sui siti web a cui ha accesso l’amministratore con restrizioni.

_ACP2E-3772_

#### [Gestione temporanea2] Le schede archiviate non sono visibili nel pannello di amministrazione

Corregge il problema per cui l’opzione di pagamento &quot;Stored Card&quot; non veniva più visualizzata nel modulo di inserimento dell’ordine back-end dopo un aggiornamento.

_ACP2E-3830 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### convalida del campo aziendale non riuscita per l&#39;estrazione guest

_AC-14987 - [Problema GitHub](https://github.com/magento/magento2/issues/40011) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

### Bundle

#### Escludi i file JS dell’editor avanzato dall’output in bundle tra i temi

_AC-15128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/43648891) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2bc584af)_

### Carrello e pagamento

#### Convalide quantità front-end prodotto raggruppato mancanti

Il sistema ora funziona correttamente e viene visualizzato un errore di convalida quando si tenta di aggiungere una quantità negativa e una quantità massima

_AC-13524 - [Problema GitHub](https://github.com/magento/magento2/issues/39479) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39480)_

#### Prefisso ospite non salvato nell&#39;indirizzo preventivo 2.4.8

_AC-14705 - [Problema GitHub](https://github.com/magento/magento2/issues/39915) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Problema] Imposta il prezzo sull&#39;articolo del preventivo anziché base_price

Il sistema gestisce correttamente il set di prezzi dell&#39;articolo del preventivo in base al prezzo base anziché al prezzo se in un sito Web sul front-end sono presenti più valute

_AC-9985 - [Problema GitHub](https://github.com/magento/magento2/issues/38094) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36878)_

#### [Cloud] Gli ordini recenti non vengono visualizzati in un&#39;altra visualizzazione archivio se gli ordini vengono creati in una visualizzazione archivio

È stato risolto un problema che impediva alla pagina &quot;Il mio account&quot; di visualizzare gli ordini recenti provenienti da altre visualizzazioni dello store. La logica di recupero degli ordini è stata aggiornata per garantire una visibilità coerente degli ordini in tutte le visualizzazioni dello store, in linea con il comportamento della pagina &quot;I miei ordini&quot;.

_ACP2E-3807 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qtà visualizzata come  0 nella sezione admin customer shopping cart (Carrello acquisti cliente amministratore) durante l’aggiunta di prodotti BUNDLE  

Nella sezione Carrello acquisti in Attività cliente è ora visualizzata la quantità corretta. In precedenza, la quantità veniva visualizzata come 0.

_ACP2E-3872 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carrello e pagamento, GraphQL

#### Errore durante la mappatura del messaggio al codice di errore durante l’ordine tramite GraphQL

Le chiamate di GraphQL per effettuare un ordine per un carrello inesistente o inattivo ora restituiscono correttamente i codici di errore CART_NOT_ACTIVE o CART_NOT_FOUND in tutte le visualizzazioni archivio, risolvendo un problema a causa del quale i messaggi di errore tradotti in precedenza generavano un codice NON DEFINITO.

_ACP2E-3942 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Carrello e pagamento, GraphQL, Inventario/MSI

#### L&#39;attributo is_available in CartItemInterface restituisce false anche quando le scorte vendibili sono elevate

L&#39;attributo is_available restituisce true quando le scorte vendibili sono elevate. In precedenza, restituiva sempre false.

_ACP2E-3885 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Catalogo

#### Errore di ambito nella risorsa URL del catalogo (_getCategories)

Questa PR aggiunge un fallback all’ambito predefinito se non è definito alcun valore nell’ambito di archiviazione nella risorsa URL della categoria.

_AC-11011 - [Problema GitHub](https://github.com/magento/magento2/issues/38393) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Verifica se OpenGraph può mostrare il prezzo

Il sistema funziona correttamente quando usiamo il plugin che nasconde il prezzo e con questo cambiamento di prezzo non è visibile nel tag OG.

_AC-11635 - [Problema GitHub](https://github.com/magento/magento2/issues/38512) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38510)_

#### [Bug] REST API: l&#39;aggiornamento dei prezzi speciali non imposta i valori per tutte le visualizzazioni dello store

_AC-13671 - [Problema GitHub](https://github.com/magento/magento2/issues/39521) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] errore PHP non rilevato

Questa PR Modifica il nome di una variabile di loop per aggiungere correttamente i dati &quot;_cache_instance_product_ids&quot; sul prodotto specificato da utilizzare nelle chiamate successive.

_AC-14159 - [Problema GitHub](https://github.com/magento/magento2/issues/39641) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD] Il ridimensionamento delle immagini richiede oltre 400 GB di spazio su disco

Dopo la correzione, il comando `catalog:images:resize` utilizzato con il flag —skip_hidden_images non genererà cache di immagini per i siti Web in cui le immagini non sono presenti.

_ACP2E-3869 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Il CountryID fornito non esiste - Irlanda (IE)

Dopo la correzione, i codici postali irlandesi sono disponibili per cercare le località di prelievo.

_ACP2E-3932 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Catalogo, Prestazioni

#### Le categorie in amministrazione si caricano molto lentamente

Le prestazioni di caricamento delle categorie sono notevolmente migliorate. In precedenza, il caricamento della categoria che causava un problema di timeout richiedeva così tanto tempo.

_ACP2E-3891 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogo, prezzi

#### Sconto regola prezzo catalogo non valido applicato al prodotto figlio

Risolve il problema per cui la regola del prezzo di catalogo per la variante viene sostituita dal prodotto configurabile principale, nel caso in cui entrambe le regole abbiano la stessa priorità.

_ACP2E-3693 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

### Catalogo, Ricerca

#### La richiesta RestApi &#39;/rest/default/V1/Categories?searchCriteria%5Bpage_size%5D=1&#39; non riesce e viene restituito un errore di timeout

_AC-13358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenuto

#### Dopo l&#39;aggiornamento a Magento 2.4.7 p2 non può vedere i file appena caricati galleria multimediale

_AC-13262 - [Problema GitHub](https://github.com/magento/magento2/issues/39275)_

#### Se si rimuove completamente un&#39;immagine della galleria da be, vengono impostati i ruoli/tipi dell&#39;ambito (base/piccola/miniatura) e dopo la nuova aggiunta vengono visualizzati i ruoli/tipi &quot;vecchi&quot;

Il sistema funziona come previsto negli ambiti di archiviazione. Le immagini ereditano i ruoli o i tipi della nuova immagine aggiunta in base all’ambito predefinito

_AC-13556 - [Problema GitHub](https://github.com/magento/magento2/issues/39481) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Piccolo bug] Il filtro del pannello di amministrazione `listing component` non può essere attivato se il valore del campo contiene `\`

Il sistema funziona correttamente quando si filtra il titolo della pagina con una barra (esempio: Magento\Store)

_AC-13661 - [Problema GitHub](https://github.com/magento/magento2/issues/39513) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39535)_

#### &quot;La pagina CMS con ID &quot;0&quot; non esiste&quot; flusso di registro

Il sistema funziona come previsto dopo la creazione dell’utente amministratore e quando si crea una nuova pagina system.log non contiene messaggi di errore

_AC-14254 - [Problema GitHub](https://github.com/magento/magento2/issues/39743) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39746)_

#### I widget per collegamenti catalogo utilizzano un URL errato

Il sistema ora gestisce correttamente i widget dopo l’aggiunta del collegamento di prodotto catalogo e del collegamento di categoria catalogo e mostra anche gli URL corretti nell’origine HTML

_AC-14437 - [Problema GitHub](https://github.com/magento/magento2/issues/39464) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39710)_

#### Il componente Prodotto di Page Builder non funziona se l’utente non dispone dell’autorizzazione Widget

Prima della correzione, quando si accedeva a un widget senza autorizzazioni, la pagina generava un errore generico e mostrava un GIF di &quot;caricamento&quot;. Ora, dopo la correzione, viene visualizzata una finestra modale con &quot;Spiacenti, sono necessarie le autorizzazioni per visualizzare questo contenuto&quot;. messaggio.

_ACP2E-3664 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### L’ordine del widget di prodotto di Page Builder non viene applicato in GraphQL

È stato risolto il problema che impediva alla risposta della query &quot;route&quot; di GraphQL di restituire i prodotti nell&#39;ordinamento corretto all&#39;interno di un tipo di contenuto Prodotti Page Builder.

_ACP2E-3898 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema di visualizzazione dei prezzi su vetrine non inglesi a causa della versione della libreria ICU

Dopo la correzione, il prezzo del prodotto viene visualizzato correttamente nella lingua ebraica (Israele).

_ACP2E-3938 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Aggiornamento della configurazione della progettazione annullata del codice dell&#39;archivio

È stato risolto il problema che causava la cancellazione delle impostazioni di Configurazione della progettazione da parte dell&#39;aggiornamento del codice della vista archivio a causa di un aggiornamento non corretto della cache di configurazione.

_ACP2E-3941 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Framework

#### Errore durante l&#39;esecuzione del comando setup:upgrade con il trigger del database personalizzato

_AC-11487 - [Problema GitHub](https://github.com/magento/magento2/issues/38481)_

#### Il modulo di entità sito web/gruppo/archivio non può essere esteso con più elementi di modulo valore per gli attributi di estensione

Questa PR consente agli elementi modulo multivalore di inviare dati a un modulo sito Web/gruppo/archivio.

_AC-11657 - [Problema GitHub](https://github.com/magento/magento2/issues/24070) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema] Rimuovi utilizzo del risolutore ambito

Questa PR risolve le impostazioni URL amministratore a livello globale invece che nell’archivio corrente

_AC-11736 - [Problema GitHub](https://github.com/magento/magento2/issues/38566) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38554)_

#### Esposizione della versione di Magento tramite route di installazione con configurazione Nginx predefinita

Il sistema ora funziona come previsto e non espone la versione esatta di Magento in esecuzione sul sito

_AC-13205 - [Problema GitHub](https://github.com/magento/magento2/issues/39227) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] refactoring dell&#39;indirizzo dell&#39;offerta per convalidare il metodo

Questa PR include miglioramenti di leggibilità al metodo doValidate.

_AC-13214 - [Problema GitHub](https://github.com/magento/magento2/issues/38230) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38219)_

#### opzione Magento: magento-init-params non viene mai utilizzato quando si esegue cli?

_AC-13231 - [Problema GitHub](https://github.com/magento/magento2/issues/39248) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### dichiarazione di tipo getItemsByColumnValue errata

Il sistema ora definisce correttamente il parametro di input $value come tipo primitivo, non come array, nella funzione getItemsByColumnValue, assicurandosi che la funzione restituisca l&#39;insieme previsto. In precedenza, se come parametro di input veniva utilizzato un array con un singolo valore, la funzione restituiva null e gli IDE la contrassegnavano come errore.

_AC-13240 - [Problema GitHub](https://github.com/magento/magento2/issues/33070) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33120)_

#### Cache Keys associata a FPC nelle implementazioni multi-store di Magento 2.4.7

_AC-13719 - [Problema GitHub](https://github.com/magento/magento2/issues/39456) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### API Rest di Magento che espone PII

_AC-13904 - [Problema GitHub](https://github.com/magento/magento2/issues/39336)_

#### L’indicizzazione parziale smette di funzionare per i clienti con un numero enorme di aggiornamenti

_AC-14424 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Esaminare &quot;use strict&quot; non è necessario all’interno dei moduli

_AC-14517 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Dopo aver scaricato l&#39;etichetta di spedizione possiamo vedere alcuni importo di spedizione che non corrispondeva con il prezzo di spedizione e di imballaggio.

_AC-14560_

#### Il meccanismo MView ignora automaticamente gli errori durante l’esecuzione del trigger

_AC-14567 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] Evita molte eccezioni non necessarie durante il caricamento dell&#39;unione XML del layout

Questa PR introduce una nuova funzione (per la compatibilità B/C non sovrascriviamo la stringa _loadXmlString protetta) da caricare e non genera un’eccezione

_AC-14580 - [Problema GitHub](https://github.com/magento/magento2/issues/39877) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37570)_

#### [Problema] Utilizza la promozione della proprietà del costruttore nel grafo di Vault del modulo Ql

Questa PR sostituisce le proprietà del costruttore con la promozione di proprietà nel modulo VaultGraphQl

_AC-14616 - [Problema GitHub](https://github.com/magento/magento2/issues/39900) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36996)_

#### [Problema] È stata rimossa la ridondanza del codice per i layout front-end del modulo.

Questa PR rimuove la ridondanza del codice nei layout dei temi per i moduli front-end Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter e Magento_Sitemap.

_AC-14625 - [Problema GitHub](https://github.com/magento/magento2/issues/30673) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30644)_

#### [Problema] Rimuovi il codice relativo a Microsoft IIS

Questa PR consente di eliminare il codice relativo a Microsoft IIS in base alla documentazione sui requisiti di sistema di Magento, in cui si specifica che il sistema operativo Microsoft Windows non è supportato

_AC-14702 - [Problema GitHub](https://github.com/magento/magento2/issues/39910) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39894)_

#### Errore di sintassi Magnifier.js

La funzionalità Lente di ingrandimento del sistema deve continuare a funzionare nel modo in cui funzionava in precedenza e le opzioni Lente di ingrandimento non devono essere disponibili in ambito globale

_AC-14722 - [Problema GitHub](https://github.com/magento/magento2/issues/36200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modalità dettagliata backport nel comando CLI `setup:db:status`

_AC-14807 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Invio di posta SMTP con tls e 2.4.8

_AC-14883 - [Problema GitHub](https://github.com/magento/magento2/issues/39947) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema] è stato risolto un problema di concorrenza nella distribuzione di contenuto statico

Questa PR risolve un bug in cui più processi simultanei si attivano per gestire lo stesso pacchetto di temi, a seconda di come i temi vengono definiti con i loro genitori.

_AC-14944 - [Problema GitHub](https://github.com/magento/magento2/issues/39990) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Rimuovere il codice di compatibilità legacy per le versioni PHP &lt; 8.1

Questa richiesta di pull rimuove il codice progettato per essere eseguito su PHP &lt;8.1.
Inoltre, i controlli rimossi per la disponibilità del contatto PHP_VERSION_ID, poiché è disponibile in tutte le versioni PHP

_AC-14971 - [Problema GitHub](https://github.com/magento/magento2/issues/39891) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC non funziona all&#39;accesso

_AC-14999 - [Problema GitHub](https://github.com/magento/magento2/issues/40007) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/)_

#### [Problema] migliorare la gestione degli errori SchemaBuilder

Questa PR migliora la gestione dei messaggi di errore dello schema del database. Ci aiuta a identificare il problema senza dover eseguire pesanti operazioni di debug.

_AC-15020 - [Problema GitHub](https://github.com/magento/magento2/issues/39816) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39799)_

#### Errore del test di integrazione su SYNC PR per lo sviluppo 2.4.9-alpha2 dovuto alla modifica di CliStateTest

_AC-15136 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2d0f8066)_

#### Bugfix di tipo PHP8.1

I prodotti associati vengono ora inizializzati in un array vuoto anziché false quando la modalità di elaborazione rigorosa non è attiva o quando sono disponibili informazioni sul prodotto. Questa modifica garantisce che la gestione logica successiva dei prodotti associati si comporti in modo coerente, migliorando la stabilità e la prevedibilità nel processo di preparazione del prodotto.

_AC-6017 - [Problema GitHub](https://github.com/magento/magento2/issues/35808) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35842)_

#### [Problema] Rimuovere il tag `@author` non consentito dal framework (parte 3)

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8343 - [Problema GitHub](https://github.com/magento/magento2/issues/37270) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema] Utilizza la promozione della proprietà del costruttore nel modulo invia messaggio grafo SQL

Il sistema ora utilizza la promozione della proprietà del costruttore nel modulo GraphQL &quot;send friend&quot;, migliorando la leggibilità del codice e riducendo la complessità. In precedenza, il modulo utilizzava proprietà che occupavano numerose righe, rendendo il codice più complesso e meno leggibile.

_AC-8346 - [Problema GitHub](https://github.com/magento/magento2/issues/37235) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Downloadable`

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8355 - [Problema GitHub](https://github.com/magento/magento2/issues/37251) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità e la coerenza del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8358 - [Problema GitHub](https://github.com/magento/magento2/issues/37264) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8360 - [Problema GitHub](https://github.com/magento/magento2/issues/37261) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8361 - [Problema GitHub](https://github.com/magento/magento2/issues/37260) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8363 - [Problema GitHub](https://github.com/magento/magento2/issues/37258) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8375 - [Problema GitHub](https://github.com/magento/magento2/issues/37257) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37007)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8376 - [Problema GitHub](https://github.com/magento/magento2/issues/37256) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37006)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8400 - [Problema GitHub](https://github.com/magento/magento2/issues/37254) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37004)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8401 - [Problema GitHub](https://github.com/magento/magento2/issues/37255) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37005)_

#### [Problema] Migliorare l&#39;estensibilità della generazione degli URL del servizio

Il sistema ora consente di personalizzare la funzione di Generazione URL di servizio tramite plug-in, promuovendo un approccio più manutenibile alle modifiche. In precedenza, la personalizzazione di questa funzione veniva ottenuta tramite preferenze che potevano non essere altrettanto efficienti o manutenibili.

_AC-8813 - [Problema GitHub](https://github.com/magento/magento2/issues/37404) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37403)_

#### Problema con l’aggiornamento 2.4.7-p5 a causa di una nuova convalida

È stato risolto un problema nella classe SchemaBuilder a causa del quale una &quot;colonna&quot; di chiave di array non definita causava un arresto anomalo durante la creazione o gli aggiornamenti dello schema. Ciò si verificava durante l’elaborazione dei dati della tabella che non includevano una chiave &quot;column&quot; (colonna).

_ACP2E-3871 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Errore di deprecazione di PHP8.4: E_USER_ERROR dopo l’aggiornamento ad Adobe Commerce 2.4.8

Gli scenari rivolti al cliente non sono interessati dalla correzione.

_ACP2E-3963 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, Ricerca

#### Opensearch 2.19.1 legal_topic_exception su categorie a un prezzo

Opensearch non genera più un’eccezione legal_topic_exception sulle categorie contenenti tutti i prodotti con lo stesso prezzo. Precedentemente, l&#39;eccezione &quot;[dal parametro] non può essere negativa&quot;.

_ACP2E-3896 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### graphql customerOrders restituisce un errore quando il prodotto è stato eliminato

La richiesta graphql customerOrders non genera più un errore anche se il prodotto nell’ordine è stato eliminato. In precedenza, veniva generato un errore &quot;Errore interno del server&quot;.

_ACP2E-3936_

#### Gli elementi della lista dei desideri non sono condivisi tra store e visualizzazioni all&#39;interno di un sito Web nella richiesta GraphQL

Prima della correzione, gli elementi della lista dei desideri venivano filtrati per ID archivio. Ora, dopo la correzione, gli elementi della lista dei desideri vengono filtrati per sito web.

_ACP2E-3987 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, prodotto

#### MediaGalleryInterface non contiene il parametro media_type nel grafico del prodotto

La richiesta GraphQL di MediaGallery ora include il campo &quot;tipi&quot; per i tipi di immagini di prodotto. In precedenza, questo campo &quot;types&quot; non esisteva nella richiesta GraphQL di MediaGallery.

_ACP2E-3880 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventario/MSI

#### Nessun negozio disponibile dopo il reindirizzamento alla home page e l&#39;estrazione

Lo store selezionato in precedenza ora sarà preselezionato nella spedizione &quot;Pick in Store&quot; se il cliente passa alla pagina di pagamento, poi ritorna alla home page e infine ritorna alla pagina di pagamento. In precedenza, dopo essere tornato ripetutamente alla pagina di pagamento, lo store selezionato nel &quot;Pick in Store&quot; veniva cancellato.

_ACP2E-3793 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

### Ordine

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) interrompe customAttributes

_AC-10568 - [Problema GitHub](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Riordino Magento -1 numeri di ordine

Il sistema funziona come previsto e dopo il riordino dal backend il numero dell&#39;ordine sarà univoco di 8 cifre

_AC-12854 - [Problema GitHub](https://github.com/magento/magento2/issues/39089) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perdita del caricamento del file di opzione personalizzato del prodotto durante il check-out con il metodo di pagamento con carta di credito di Adobe

_AC-14306 - [Problema GitHub](https://github.com/magento/magento2/issues/39647)_

#### Stato ordine bloccato durante l’elaborazione

Prima della correzione, quando si ordina un prodotto in bundle con l’opzione &quot;Spedisci insieme&quot; abilitata, lo stato dell’ordine non passava automaticamente a &quot;completo&quot; dopo la fattura e la spedizione. Ora, dopo la correzione, lo stato dell’ordine passa automaticamente a &quot;completo&quot; dopo che l’ordine è stato fatturato e spedito.

_ACP2E-3947 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Codice Magento OOTB - Problema di configurazione del modello e-mail

Prima della correzione, quando si utilizzava l’invio asincrono di e-mail per la spedizione, queste risultavano incoerenti con l’ordine dello store. Ora, dopo la correzione, viene consegnato l’ordine e-mail di spedizione del negozio corretto.

_ACP2E-3998 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Altri strumenti per sviluppatori

#### [Problema] Suggerimento di tipo errato per il membro protetto $_urlHelper

Il sistema ora corregge l&#39;hint di tipo errato con quello corretto, utilizzato anche nel costruttore

_AC-10716 - [Problema GitHub](https://github.com/magento/magento2/issues/32503) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32496)_

### Prestazioni

#### [Problema] - Archivio aggiornamenti.php

Questa PR migliora le prestazioni saltando la risoluzione dell’archivio corrente.

_AC-14791 - [Problema GitHub](https://github.com/magento/magento2/issues/39949) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38717)_

### Prezzi

#### Il prezzo è sempre 0 per gli articoli di prodotti bundle senza prezzo dinamico in order rest API

_AC-11925 - [Problema GitHub](https://github.com/magento/magento2/issues/38687) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7da46f52)_

### Prodotto

#### Sconto percentuale sul prezzo di livello e regola del prezzo di catalogo calcolata sul prezzo originale senza opzioni selezionate.

_AC-12004 - [Problema GitHub](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minQtà ordine prodotto mancante consentita

Il sistema funziona correttamente e la sorgente della pagina mostra correttamente la quantità minima del prodotto

_AC-12909 - [Problema GitHub](https://github.com/magento/magento2/issues/39142) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39480)_

#### Eccezione Magento durante l&#39;esecuzione del test di Magento Payflow Pro

_AC-13681_

#### Problema con la griglia Opzioni personalizzabili nella pagina del prodotto nel pannello di amministrazione

Il sistema funziona come previsto durante la creazione di opzioni personalizzabili con il menu a discesa del tipo

_AC-14003 - [Problema GitHub](https://github.com/magento/magento2/issues/39640) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39694)_

#### L&#39;Opzione Di Stampa Della Pagina Dell&#39;Elenco Richieste Non Funziona

_AC-14711_

#### Tutti gli elementi degli elenchi di confronto di altri clienti vengono assegnati al cliente dopo l’accesso tramite l’amministratore

In precedenza, quando un amministratore utilizzava la funzione &quot;Accedi come cliente&quot; nel back-end, i prodotti dell’elenco di confronto di un cliente precedentemente connesso venivano erroneamente assegnati al cliente attualmente rappresentato.  Dopo la correzione, l’elenco di confronto viene caricato correttamente per il cliente connesso corretto.

_ACP2E-3818 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### L’aggiornamento di product url_key tramite API REST non genera un URL 301 Rewrite

Quando si aggiorna la chiave URL del prodotto tramite l’API REST, con l’impostazione &quot;Create Permanent Redirect for URLs if URL Key Changed&quot; (Crea reindirizzamento permanente per gli URL se la chiave URL è stata modificata) impostata su Sì, l’URL del prodotto riscritto viene creato per creare un reindirizzamento dal vecchio URL a uno nuovo.

_ACP2E-3900 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Vendite

#### Lo stato dell’ordine viene scomparso durante la selezione del valore nel menu a discesa Stato ordine

_AC-15010_

### Sicurezza

#### JS in bundle/uniti non fa parte degli hash SRI

Prima della correzione, il bundle generato o i file uniti non venivano aggiunti all’elenco di hash SRI. Ora i file vengono aggiunti correttamente agli hash dell’SRI.

_ACP2E-3854 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Spedizione

#### [QUANS] - Il modulo di base Magento_Fedex verifica la presenza di un token attivo valido prima di inviare una richiesta per ottenerne uno nuovo?

Adobe Commerce non effettua molte richieste al servizio API FedEx per il token di accesso. In precedenza, anche se il token di accesso è ancora valido, Adobe Commerce effettuava sempre nuove richieste all’API FedEx, causando un problema di limitazione della frequenza.

_ACP2E-3930 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Staging e anteprima

#### Impossibile visualizzare in anteprima l&#39;aggiornamento programmato del prodotto con le autorizzazioni per la categoria abilitate

Prima della correzione, un prodotto futuro da abilitare non veniva visualizzato in modalità anteprima. Ora viene visualizzato anche se lo stato corrente è disabilitato.

_ACP2E-3786 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### L&#39;ambito mostra una visualizzazione diversa dello store durante l&#39;anteprima

Prima della correzione, in un archivio diverso potrebbe essere stata aperta un’anteprima dell’aggiornamento di staging del blocco cms e del contenuto della pagina cms rispetto all’archivio assegnato al blocco cms o alla pagina quando si accede dal dashboard di staging del contenuto. Dopo la correzione, se al blocco cms o alla pagina è assegnato solo un archivio specifico nell’aggiornamento di staging, l’anteprima dal dashboard di staging del contenuto si aprirà con l’archivio corretto selezionato.

_ACP2E-3815_

#### Convalida mancante per il campo Importo sconto regola prezzo catalogo

In precedenza, il campo discount_amount nell’aggiornamento della pianificazione di staging non veniva convalidato correttamente con le regole di convalida correnti. Tuttavia, dopo aver applicato la correzione, il campo sconto_importo verrà convalidato in modo appropriato.

_ACP2E-3867 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Imposta

#### Totale ordine errato. L&#39;arrotondamento non viene applicato al calcolo del prezzo.

Il sistema è ora in grado di gestire correttamente il calcolo dell&#39;importo price_after_discount, discount_amount e tax.
il totale effettivo dell&#39;ordine

_AC-11389 - [Problema GitHub](https://github.com/magento/magento2/issues/38455) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39687)_

### Framework di test

#### [Problema] Ignora lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

Il sistema ora ignora il file &quot;env.php&quot; generato durante l’esecuzione degli unit test, garantendo che lo stato Git rimanga pulito dopo l’esecuzione dei test. In precedenza, l’esecuzione degli unit test generava un nuovo file &quot;env.php&quot;, causando la visualizzazione di un nuovo file trovato e rendendolo più sporco.

_AC-13293 - [Problema GitHub](https://github.com/magento/magento2/issues/39304) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema] è stato corretto un problema di test dell&#39;integrazione con l&#39;intercettore

Il sistema ora identifica e gestisce correttamente \Magento\TestFramework\App\Config\Interceptor nel test di integrazione, garantendo che il test possa accedere ai dati necessari anche quando esiste un plug-in nella classe. In precedenza, il sistema non riusciva a tenere conto della possibilità che \Magento\TestFramework\App\Config fosse un \Magento\TestFramework\App\Config\Interceptor, causando un errore durante il tentativo di accedere alla proprietà $data.

_AC-13305 - [Problema GitHub](https://github.com/magento/magento2/issues/39324) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: invio di e-mail a un modulo per amici con captcha abilitato

Il caso di test riguarda la funzionalità del modulo &quot;E-mail all’amico&quot; quando CAPTCHA è abilitato, garantendo che il processo di invio del modulo funzioni correttamente con valori CAPTCHA sia errati che corretti.

_AC-13492 - [Problema GitHub](https://github.com/magento/magento2/issues/39462) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] utilizzi di TestCase::getTestResultObject non validi da phpunit v10

_AC-13502 - [Problema GitHub](https://github.com/magento/magento2/issues/39463)_

#### Guasti degli unit test specifici dell’ambiente in AC 2.4.7-p3

Questo problema risolve gli errori degli unit test che non vengono riprodotti su tutte le versioni e gli ambienti. In precedenza, per correggere alcuni unit test non riusciti a causa di diverse versioni della libreria o a causa di funzionalità mancanti aggiunte in una versione successiva.

_ACP2E-3712 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Strumenti/Strumento di migrazione dati

#### [ATLH] Errore irreversibile in assenza di differenze

L’errore irreversibile non viene più visualizzato quando non è presente alcuna differenza da visualizzare

_ACP2E-3901_

### Framework interfaccia utente

#### WYSIWYG è vuoto nelle righe dinamiche

_AC-12336 - [Problema GitHub](https://github.com/magento/magento2/issues/38893) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] Correzione dell&#39;errore di tipo MIME

Il sistema gestisce e corregge correttamente il tipo mime e l’errore di battitura per l’immagine gif

_AC-8001 - [Problema GitHub](https://github.com/magento/magento2/issues/36899) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Evita l&#39;accesso diretto all&#39;elenco delle recensioni Ajax

Il sistema gestisce correttamente ed evita l&#39;accesso diretto all&#39;elenco recensioni Ajax

_AC-9381 - [Problema GitHub](https://github.com/magento/magento2/issues/37920) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33876)_

### Aggiornamenti - Upgrade Compatibility Tool

#### Funzionalità obsoleta: creazione della proprietà dinamica Magento\Framework\Acl::$_roleRegistry

_AC-12343 - [Problema GitHub](https://github.com/magento/magento2/issues/37469)_

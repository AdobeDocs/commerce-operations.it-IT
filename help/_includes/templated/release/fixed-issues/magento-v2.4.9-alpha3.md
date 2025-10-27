---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Note sulla versione di Magento Open Source (v2.4.9-alpha3)

## Problemi risolti in v2.4.9-alpha3

Sono stati risolti 129 problemi nel codice core Magento Open Source 2.4.9-alpha3. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### Errore indirizzo fatturazione mancante nel dashboard di amministrazione durante la creazione di un ordine tramite API REST con solo le informazioni di pagamento

È stato risolto un problema che consentiva la creazione degli ordini tramite API senza un indirizzo di fatturazione, causando arresti anomali del dashboard di amministrazione.
Ora gli ordini senza indirizzo di fatturazione sono soggetti a restrizioni e non vengono più creati.

_AC-14049 - [Problema GitHub](https://github.com/magento/magento2/issues/39651) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problema relativo all’aggiunta del prodotto al carrello nell’API REST

È stato risolto un problema a causa del quale era ancora possibile aggiungere al carrello e acquistare prodotti non assegnati a un sito Web specifico.
Ora viene visualizzato un messaggio di errore: &quot;Il prodotto che stai tentando di aggiungere non è disponibile&quot;.

_AC-15054 - [Problema GitHub](https://github.com/magento/magento2/issues/40029) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f5cc09fc)_

#### L’Etichetta Dell’Opzione Dell’Attributo Viene Sovrascritta Quando Si Aggiornano Le Etichette Dell’Archivio

È stato risolto un problema a causa del quale l’aggiornamento di un attributo di prodotto a selezione multipla tramite API REST sovrascriveva tutte le etichette store_labels, rimuovendo le etichette specifiche dello store esistenti.
Ora, quando si aggiorna l’etichetta predefinita per la vista archivio, Magento unisce le etichette fornite con quelle esistenti invece di sovrascriverle completamente.
In questo modo, dopo gli aggiornamenti, le etichette specifiche per le altre visualizzazioni dello store rimarranno intatte.

_AC-15208 - [Problema GitHub](https://github.com/magento/magento2/issues/40093) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### L’endpoint REST API export-stock-salable-qty restituisce un valore item total_count errato

È stato risolto un problema di paginazione nell’API della quantità vendibile delle scorte di esportazione in magazzino in cui total_count era limitato in modo errato alla dimensione della pagina. In precedenza, quando si utilizzava l’endpoint /rest/all/V1/inventory/export-stock-salable-qty/website/base con parametri di impaginazione come page_size=5, il campo total_count nella risposta restituiva 5 invece del numero totale effettivo di prodotti che corrispondono ai criteri di ricerca. Dopo questa correzione, il campo total_count ora riflette correttamente il numero totale di prodotti disponibili indipendentemente dal parametro page_size, garantendo un comportamento di impaginazione coerente in tutti gli endpoint API REST di Magento.

_ACP2E-4086 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Problema di convalida con gli ID opzione personalizzati nell’elemento del carrello API REST

API REST V1/guest-carts/&lt;cartId>/items/ e V1/carts/mine/items/ ora convalidano &quot;product_options.extension_attributes.custom_options.*.option_id&quot; per garantire che faccia riferimento a un option_id valido per lo SKU dell’articolo del carrello. In precedenza, questo parametro veniva elaborato e salvato nel database senza convalida.

_ACP2E-4138 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Account

#### [Problema] È stata rimossa la spaziatura superflua nella griglia di back-end

Il sistema ora rimuove la spaziatura superflua nella griglia backend quando sono presenti elementi selezionati

_AC-11579 - [Problema GitHub](https://github.com/magento/magento2/issues/38502) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32622)_

#### Impossibile cancellare il commento dell&#39;elemento della lista dei desideri tramite `updateProductsInWishlist` mutazione GraphQL

È stato risolto un problema a causa del quale i commenti della lista dei desideri non venivano aggiornati tramite mutazioni GraphQL.
Ora i commenti vengono aggiornati correttamente e si riflettono sia nella risposta API che nella vetrina.

_AC-14682 - [Problema GitHub](https://github.com/magento/magento2/issues/39911) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Impostazione Mostra prefisso/suffisso ignorata se impostata su No

È stato risolto un problema a causa del quale il prefisso/suffisso del nome del cliente continuava a essere visualizzato negli ordini anche se disabilitato nella configurazione.
Ora i valori prefisso/suffisso vengono rimossi dai dettagli dell’ordine in base all’impostazione di configurazione.

_AC-15074 - [Problema GitHub](https://github.com/magento/magento2/issues/40036) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Registro account cliente Storefront: il formato dell’indirizzo e-mail viene convertito con un formato di dominio diverso

Questo bug ha risolto un problema a causa del quale le e-mail del cliente con caratteri speciali nel dominio (ad esempio, tec55241@adòbe.com) venivano automaticamente convertite in formato punycode (tec55241@xn--adbe-mqa.com).
In Magento 2.4.9-alpha3, la correzione assicura che tali ID e-mail rimangano invariati e validi, evitando errori di consegna.

_AC-15177 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Messaggi di convalida mancanti (errore immagine) nel modulo del registro

È stato risolto un problema a causa del quale i campi obbligatori nella pagina di creazione dell’account del cliente non mostravano messaggi di convalida se lasciati vuoti.
Ora vengono visualizzati messaggi di errore corretti per tutti i campi vuoti o errati.

_AC-15185 - [Problema GitHub](https://github.com/magento/magento2/issues/40076) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problema dopo l’accesso a magento 2.4.8-p1

È stato risolto un problema su Magento 2.4.8-p1 a causa del quale il collegamento &quot;Crea un account&quot; era ancora visibile sulla home page dopo l’accesso.
Ora, il collegamento viene nascosto correttamente dopo l’accesso, in modo coerente con le altre pagine.

_AC-15292 - [Problema GitHub](https://github.com/magento/magento2/issues/40120)_

### Interfaccia utente amministratore

#### [Problema] sostituisce l&#39;escape obsoleto

Questa PR rimuove getEscaper() obsoleto e lo aggiunge tramite l’iniezione del costruttore

_AC-15132 - [Problema GitHub](https://github.com/magento/magento2/issues/40062) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38135)_

#### Messaggio di benvenuto che si sovrappone alla categoria di prodotto nella vista per dispositivi mobili.

È stato risolto un problema dell’interfaccia utente a causa del quale il nome del benvenuto si sovrapponeva alle categorie di prodotto nella visualizzazione per dispositivi mobili, bloccando i clic.
Ora le categorie sono completamente visibili e cliccabili senza problemi di sovrapposizione.

_AC-15166 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### &quot;Impossibile risolvere le voci del parametro reCAPTCHA&quot; in exception.log per Google reCAPTCHA Admin Panel

Un errore reCaptcha nel file `var/log/exception.log` per l&#39;accesso amministratore reCAPTCHA di Google V3 è stato risolto e non vengono registrati messaggi di errore. In precedenza, il seguente errore veniva generato ogni pochi secondi quando un utente amministratore configurava le impostazioni del **Configurazione** > **Sicurezza** > **Pannello di amministrazione Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema GitHub](https://github.com/magento/magento2/issues/34975) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contributo codice GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### L’utente amministratore con restrizioni può salvare/aggiornare le configurazioni predefinite nonostante le autorizzazioni specifiche per lo store

È stato risolto il problema che impediva agli utenti amministratori con restrizioni di visualizzare e tentare di aggiornare l’ambito &quot;Configurazione predefinita&quot; nonostante fossero assegnati solo a specifici ambiti del sito web, il che poteva causare confusione.

_ACP2E-4011 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Il prezzo del prodotto configurabile è stato salvato in DB per qualsiasi ambito di visualizzazione dello store, causando problemi nella funzione di ordinamento Prodotti in Categoria in cui il prezzo salvato non ha rilevanza nel front-end

È stata rimossa la casella di controllo &quot;Usa valore predefinito&quot; per un prodotto configurabile quando il prezzo è configurato per sito Web e nella pagina di modifica del prodotto configurabile dall’interfaccia di amministrazione è selezionata una visualizzazione Store.

_ACP2E-4036 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]I criteri per la password amministratore non soddisfano la conformità PCI DSS 4.0 (minimo 12 caratteri)

Gli amministratori possono ora configurare il requisito della lunghezza minima della password per gli utenti amministratori tramite Archivi > Configurazione > Avanzate > Amministratore > Sicurezza. Questo miglioramento offre maggiore flessibilità di sicurezza mantenendo al contempo i criteri password esistenti. La convalida viene applicata sia durante la creazione/modifica degli utenti amministratore che durante i salvataggi della configurazione, con una convalida front-end in tempo reale per migliorare l’esperienza utente.

_ACP2E-4044 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Problema relativo al filtro data quando la lingua dell’interfaccia di amministrazione è giapponese

Il filtro e la colonna Compleanno utilizzeranno il formato unificato M/d/y, lo stesso del filtro/colonna &quot;Cliente dal&quot;

_ACP2E-4052 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Interfaccia utente amministratore, Imposta

#### Errore nell’interfaccia utente di amministrazione dell’aliquota

Questo ticket ha risolto un problema relativo all’interfaccia utente di amministrazione dell’aliquota, a causa del quale il passaggio da un paese all’altro (ad esempio, da Stati Uniti → Regno Unito) mostrava ancora lo stato statunitense precedentemente selezionato, ingannando gli utenti.
In 2.4.9-alpha3, il campo stato ora viene reimpostato su * quando il paese selezionato non ha stati.

_AC-8440 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Prodotti API REST-render-info restituiscono il prezzo finale errato per il cliente connesso

Il ticket ha una correzione per Rest API products-render-info restituisce il prezzo finale errato per il cliente connesso

_AC-5979 - [Problema GitHub](https://github.com/magento/magento2/issues/35757) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/)_

#### Il pulsante Aggiungi a elenco richieste di acquisto scompare quando si tenta di aggiungerlo dalla pagina della categoria

Il pulsante Precedente Aggiungi a elenco richieste di acquisto scompare quando si tenta di aggiungerlo dalla pagina della categoria che è ora fissa e viene visualizzato il pulsante della richiesta nella pagina della categoria

_AC-8575_

### B2B, carrello e pagamento

#### Nessuna entità di questo tipo con ID carrello = X errore viene visualizzata su Storefront quando si accede all’utente dell’azienda B2B dalla funzione di amministrazione &quot;Accedi come cliente&quot;

Ora l’errore &quot;Nessuna entità di questo tipo con ID carrello = X&quot; non è più visibile dopo il corretto accesso dal backend di amministrazione quando si utilizza la funzione &quot;Accedi come cliente&quot;.

_ACP2E-3994 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

### Carrello e pagamento

#### [Problema] Aggiungere EventPrefix ed EventObject per estrarre il modello di contratto

Il sistema ora include EventPrefix ed EventObject per il modello di contratto di pagamento, consentendo l&#39;attivazione degli eventi con un prefisso di evento. Questo miglioramento offre maggiore flessibilità agli sviluppatori quando lavorano con eventi di contratto di pagamento. In precedenza, il modello di contratto di pagamento non supportava EventPrefix e EventObject, limitando la possibilità di personalizzare la gestione degli eventi.

_AC-13252 - [Problema GitHub](https://github.com/magento/magento2/issues/32510) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Graphql] Non può restituire null per il campo &quot;SelectedCustomizableOption.label&quot; che non ammette valori Null

Il sistema ora non genera un errore interno del server con un messaggio quando l’opzione selezionata non esiste più

_AC-14256 - [Problema GitHub](https://github.com/magento/magento2/issues/39729) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] Non è possibile inserire ordini contenenti cifre da 0 a 9, e commerciale, punto e virgola o parentesi nel nome della città

È stato corretto un problema a causa del quale l’estrazione non riusciva per i nomi delle città contenenti caratteri speciali come . , &amp; o parentesi.
Ora, gli ordini con tali nomi di città vengono inseriti correttamente senza errori di convalida.

_AC-14495 - [Problema GitHub](https://github.com/magento/magento2/issues/39854) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Sottoselezione regola di vendita con condizione Quantità non applicata

È stato risolto un problema a causa del quale le regole del prezzo del carrello con condizioni di sottoselezione del prodotto non venivano applicate al momento del pagamento.
Ora, gli sconti vengono applicati correttamente in base alle regole configurate.

_AC-14884 - [Problema GitHub](https://github.com/magento/magento2/issues/39965) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql - Il carrello unione non funziona correttamente quando è abilitato l&#39;ordine arretrato

È stato risolto un problema che impediva l’unione degli articoli del carrello ospiti con il carrello clienti durante l’unione dei carrelli tramite GraphQL.
Ora, il carrello clienti riflette correttamente la quantità combinata dai carrelli ospiti e clienti.

_AC-15148 - [Problema GitHub](https://github.com/magento/magento2/issues/40064) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integrazione] [Estrazione] Direttive dipendenti aggiornate nel modello e-mail di pagamento non riuscito

Modello e-mail di pagamento non riuscito aggiornato per gestire correttamente le direttive dipendenti.
La correzione garantisce che l&#39;indirizzo di spedizione e il metodo di spedizione vengano visualizzati correttamente quando applicabile.
In precedenza, questi campi mancavano nelle e-mail di pagamento non riuscite.

_AC-15363 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Cloud] Lo sconto sulla spedizione gratuita non viene rimosso correttamente se il carrello non soddisfa più i requisiti

Il Subtotale (Escl. Imposta) nella regola del prezzo del carrello ora incorporerà gli sconti delle regole precedenti.

_ACP2E-3973 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Ordine duplicato trovato per lo stesso cliente in Multishipping

Le richieste simultanee di inserire un ordine con più indirizzi di spedizione non generano più ordini duplicati per lo stesso cliente

_ACP2E-4117 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Carrello e pagamento, ordine, prodotto

#### L&#39;e-mail della gift card viene inviata anche se la fattura dell&#39;ordine non riesce

Prima dell’implementazione di questa correzione, le e-mail delle gift card venivano inviate dopo la creazione della fattura. Tuttavia, dopo l’applicazione della correzione, le e-mail delle gift card vengono ora inviate dopo che le fatture sono state salvate e salvate correttamente.

_ACP2E-3905_

### Carrello e pagamento, sicurezza

#### [CLOUD] Recupero del file 404 per JS alla pagina di estrazione al primo tentativo dopo l&#39;implementazione della patch SRI

Prima di correggere i mixin, non venivano caricati nel carrello e prelevati quando erano abilitati i comandi di minimizzazione e raggruppamento. Dopo la correzione, tutti i mixin devono essere caricati come previsto.

_ACP2E-4128 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogo

#### Problemi relativi all&#39;ambito dei prezzi e config.php

In Magento 2.4.2, la modifica dell’ambito del prezzo tramite config.php non aggiorna correttamente il valore is_global in catalog_eav_attribute per l’attributo del prezzo.
Di conseguenza, i prezzi dei prodotti rimangono globali e non possono essere salvati per sito web, anche quando la definizione del prezzo è impostata su sito web.
La soluzione alternativa richiede l’aggiornamento manuale della colonna is_global nel database, che non è ideale per gli ambienti di produzione.
Questo comportamento è coerente con la progettazione predefinita di Magento, in cui l’ambito del prezzo è Globale o Sito web, ma non per visualizzazione negozio.

_AC-13857 - [Problema GitHub](https://github.com/magento/magento2/issues/33559)_

#### La pagina After Store Switch proviene dalla cache (il commutatore store non funziona) nella versione 2.4.8

È stato risolto un problema a causa del quale il passaggio delle viste archivio dall’intestazione della vetrina non funzionava fino a quando la cache non veniva cancellata manualmente.
Ora, il passaggio dalla visualizzazione archivio funziona correttamente senza la necessità di pulire la cache.

_AC-14426 - [Problema GitHub](https://github.com/magento/magento2/issues/39806)_

#### Stili .less ignorati con larghezza minima: (@screen__l)

È stato risolto un problema a causa del quale venivano visualizzati solo tre prodotti per riga nelle pagine delle categorie.
Ora vengono visualizzati quattro prodotti per riga, come previsto.

_AC-14463 - [Problema GitHub](https://github.com/magento/magento2/issues/39817) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Numero di elenchi di desideri non visualizzato nella pagina home o in altre pagine, ad eccezione della pagina elenco di desideri nel menu del cliente

È stato risolto un problema a causa del quale il conteggio della lista dei desideri veniva visualizzato come parentesi vuote nelle pagine non incluse nella lista dei desideri.
Ora, il numero corretto di voci della lista dei desideri viene visualizzato accanto a &quot;Elenco dei desideri&quot; in tutte le pagine.

_AC-14607 - [Problema GitHub](https://github.com/magento/magento2/issues/39892) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before l’osservatore genera un errore relativo alla data quando utilizza l’API REST senza valori a livello di store (problema getFinalPrice())

Questa PR regola l’elaborazione di SpecialFromDate per garantire la formattazione corretta quando la data viene fornita come istanza DateTimeInterface. In questo modo si evitano errori durante l’esecuzione di getFinalPrice() in determinati scenari.

_AC-14847 - [Problema GitHub](https://github.com/magento/magento2/issues/39959) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40003)_

#### URGENTE: impossibile aggiungere un prodotto al bundle se il prodotto da aggiungere dispone di opzioni personalizzabili

È stato risolto un problema che impediva l’aggiunta di prodotti con opzioni personalizzabili ai prodotti bundle.
In precedenza, tali prodotti venivano esclusi dall’elenco &quot;Aggiungi prodotti all’opzione&quot; nella creazione del bundle.
Ora, i prodotti con opzioni personalizzabili possono essere aggiunti ai bundle senza includere le loro opzioni personalizzate, consentendo una corretta gestione delle scorte.
Ciò consente la creazione di bundle senza duplicare i prodotti o influenzare i livelli di inventario.

_AC-14958 - [Problema GitHub](https://github.com/magento/magento2/issues/39993)_

#### L’etichetta di prezzo &quot;As low as&quot; (Fino a) viene visualizzata per i prodotti configurabili con una singola opzione

È stato risolto un problema a causa del quale i prodotti configurabili visualizzavano il prezzo con un&#39;etichetta &quot;As low as&quot; errata su PDP/PLP.
Ora, il prodotto mostra il prezzo corretto ($500) senza alcuna etichetta fuorviante.

_AC-15237 - [Problema GitHub](https://github.com/magento/magento2/issues/40104) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Metodo errato chiamato per il pulsante Aggiungi a confronto

È stato corretto il metodo utilizzato in \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
In precedenza, getAddToCartButton() veniva chiamato in modo errato invece di getAddToCompareButton().
Questa modifica garantisce il comportamento corretto per il rendering del pulsante &quot;Aggiungi per confrontare&quot; negli elenchi dei prodotti.
Non vengono introdotte modifiche funzionali del comportamento; l’aggiornamento migliora l’esperienza degli sviluppatori e la correttezza del codice.

_AC-15323 - [Problema GitHub](https://github.com/magento/magento2/issues/39754) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### La generazione dinamica di immagini genera un numero elevato di immagini

Dopo la correzione, le immagini vengono generate solo per i siti web a cui è assegnato il prodotto.

_ACP2E-3927 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### L’errore 500 si verifica sul front-end, a causa di una struttura di layout errata memorizzata nella cache

È stato risolto un problema a causa del quale una pagina restituiva un codice di errore 500 a causa di una struttura di layout errata memorizzata nella cache nel layout

_ACP2E-4040 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Errore di convalida per il campo importo sconto regola prezzo catalogo in Aggiornamento pianificato

In precedenza, prima di risolvere questo problema, per l’aggiornamento della pianificazione per la regola del prezzo di catalogo, se l’importo dello sconto è by_fixed allora non è stato convalidato correttamente a causa della regola di convalida dell’intervallo di numeri. Dopo l&#39;applicazione di questa correzione, la convalida funziona correttamente per la regola del prezzo di catalogo a prezzo fisso.

_ACP2E-4054 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### I prodotti vengono visualizzati come esauriti dopo la disattivazione

Dopo la correzione, i prodotti disabilitati non sono presenti nel widget prodotti.

_ACP2E-4136 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] errori con voci duplicate (temp_category_descendants_%)

È stato risolto un problema relativo a voci duplicate durante la creazione di aggiornamenti pianificati per gli ambienti con un numero elevato di categorie nidificate

_ACP2E-4159 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catalogo, GraphQL

#### Calcolo sconto GraphQl non valido

GraphQL ora visualizza correttamente le percentuali di sconto e i prezzi base quando i prezzi del catalogo sono configurati per includere le imposte. In precedenza si verificavano errori di arrotondamento, ad esempio la visualizzazione del 19,99% invece del 20%.

_ACP2E-3993 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogo, prodotto

#### I prodotti correlati tramite la regola prodotto correlata non vengono visualizzati in PDP tramite GraphQL

In precedenza, prima dell’applicazione di questa correzione, la regola di prodotto relativa restituiva vuoto/null per un prodotto che corrispondeva alla regola. Dopo l’applicazione di questa correzione, la regola relativa al prodotto viene restituita correttamente per i prodotti corrispondenti.

_ACP2E-3949_

### Contenuto

#### graphql (magento 2.4.6-p4 ): errore durante il tentativo di ottenere la pagina cms con stato non attivo

È stato risolto un problema a causa del quale la query GraphQL per una pagina CMS disabilitata restituiva un errore interno del server.
Ora la query recupera una risposta corretta senza errori.

_AC-12302 - [Problema GitHub](https://github.com/magento/magento2/issues/38877) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] Ciclo infinito query route

Questo ticket ha risolto il problema che causava un loop infinito e alla fine un timeout in seguito a una query di instradamento di GraphQL con percorso di richiesta e percorso di destinazione identici.
In 2.4.9-alpha3, la query ora restituisce la risposta di errore corretta invece di eseguire un ciclo.

_AC-14269 - [Problema GitHub](https://github.com/magento/magento2/issues/39707) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Cambia la costante IMAGE_FILE_NAME_PATTERN in public visible, per una maggiore flessibilità

La costante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php è stata resa pubblica per consentire agli sviluppatori una maggiore flessibilità quando si lavora con rappresentazioni di immagini. La correzione è inclusa in Magento 2.4.9-alpha3 con copertura completa per unit test e integration test.

_AC-15338 - [Problema GitHub](https://github.com/magento/magento2/issues/39733) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### L’anteprima di staging del contenuto non funziona con i risultati della ricerca

La funzione Ricerca nell&#39;anteprima di staging ora restituisce i prodotti in base all&#39;ambito selezionato. In precedenza, la ricerca restituiva risultati nell’ambito predefinito, ignorando l’archivio selezionato.

_ACP2E-4095_

#### Page Builder - Problema di logica della condizione di prodotto (la logica OR si comporta in modo errato nel mostrare meno prodotti)

Il widget Prodotti Page Builder ora restituisce il risultato corretto quando si utilizza un attributo con ambito globale nella condizione &quot;Corrispondenza con qualsiasi&quot;

_ACP2E-4096 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Cliente/clienti

#### La convalida del valore minimo e massimo non funziona per l&#39;attributo DOB in Storefront

Questo bug ha risolto il problema che impediva il funzionamento della convalida della data minima e massima per l’attributo Data di nascita (DOB) nella vetrina (anche se funzionava in Admin).
In 2.4.9-alpha3, la convalida ora blocca correttamente il salvataggio dei clienti con DOB al di fuori dell’intervallo consentito, mostrando un messaggio di errore.

_AC-13535 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Errore di Ajax 401 caricato nella schermata di avviso nel pannello di amministrazione durante la revoca dell’autorizzazione di accesso come cliente

Questo bug ha risolto un problema che causava la visualizzazione di un errore Ajax 401 con HTML non elaborato nel popup di avviso in seguito alla revoca dell’autorizzazione Accesso come cliente.
Dopo la correzione, il sistema ora visualizza correttamente un normale messaggio di avviso invece di un HTML non elaborato.
La soluzione è stata fornita in Magento 2.4.9-alpha3

_AC-15336 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

### Framework

#### [Problema] Rendere la firma del metodo coerente con l&#39;interfaccia

La firma del metodo per getAttributes è ora coerente con la relativa interfaccia, evitando errori durante la sovrascrittura del metodo. In precedenza, le incoerenze nella firma del metodo causavano errori quando si tentava di sovrascrivere il metodo getAttributes.

_AC-11578 - [Problema GitHub](https://github.com/magento/magento2/issues/38501) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31955)_

#### [Problema]: è stata corretta la regola di convalida delle e-mail per il componente dell&#39;interfaccia utente

Il sistema ora convalida correttamente più indirizzi e-mail immessi nei componenti dell’interfaccia utente, garantendo che ogni e-mail sia tagliata e convalidata correttamente. In precedenza, il sistema utilizzava un metodo errato per tagliare gli indirizzi e-mail, il che poteva causare errori di convalida.

_AC-11719 - [Problema GitHub](https://github.com/magento/magento2/issues/38528) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema] Rimuovere i metodi ridondanti

Qualità del codice: sono stati rimossi i metodi ridondanti nei componenti AsynchronousOperations e Sales che chiamavano solo i metodi padre senza aggiungere funzionalità, migliorando la manutenibilità del codice.

_AC-11915 - [Problema GitHub](https://github.com/magento/magento2/issues/29748) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29147)_

#### la convalida xsd non riesce nei file etc/adminhtml/system.xml che contengono commenti sotto gli elementi dei campi.

Questa PR corregge le definizioni dello schema XML in phpstorm per il nodo dei commenti

_AC-12945 - [Problema GitHub](https://github.com/magento/magento2/issues/39148) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 utilizza pacchetti di sviluppo che non seguono il controllo delle versioni semantiche

Magento 2.4.8 richiede versioni di sviluppo di pdependent/pdependent e phpmd/phpmd (3.x-dev) per la compatibilità con PHP 8.4.
Queste versioni di sviluppo sono in conflitto con gli strumenti di terze parti che si aspettano pacchetti compatibili con SemVer, impedendo alcuni aggiornamenti.
Una soluzione alternativa temporanea consiste nell’assegnare un alias alle versioni di sviluppo in compositore.json (ad esempio, &quot;3.x-dev as 3.99.0&quot;), consentendo la compatibilità e soddisfacendo al contempo il controllo delle versioni semantiche.
Questo assicura il supporto di PHP 8.4 ed evita conflitti fino a quando non saranno disponibili versioni stabili.

_AC-14519 - [Problema GitHub](https://github.com/magento/magento2/issues/39796)_

#### API REST: chiamata a una funzione membro getVideoProvider() su null

È stato risolto un problema a causa del quale la chiamata all’API figlio del prodotto configurabile restituiva un errore interno del server 500 se un prodotto figlio aveva solo un video YouTube e nessun’altra immagine.
L&#39;errore è stato causato da un riferimento null in ExternalVideoEntryConverter.
Ora, l’API restituisce correttamente i prodotti secondari con voci della galleria di contenuti multimediali, inclusi i dati video esterni, senza generare errori.
Questo garantisce il corretto recupero di tutti i tipi di file multimediali per i prodotti secondari tramite API REST.

_AC-15046 - [Problema GitHub](https://github.com/magento/magento2/issues/40021)_

#### [Problema] Correzione di alcuni errori di battitura nei commenti PHPDoc

Questa PR risolve alcuni errori di battitura presenti nel documento

_AC-15075 - [Problema GitHub](https://github.com/magento/magento2/issues/40042) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38809)_

#### [Problema] Rimuovere l&#39;utilizzo di sprintf nelle chiamate di frase

Questa PR rimuove l’utilizzo di sprintf nella chiamata della funzione phrase nel core di Magento.

_AC-15183 - [Problema GitHub](https://github.com/magento/magento2/issues/40050) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40033)_

#### Impossibile reindicizzare tutti gli indicizzatori non validi su più thread con blocco applicazione attivo

Questo problema ha risolto un errore dell’indicizzatore multi-thread quando use_application_lock era abilitato.
In precedenza, i blocchi del database venivano persi durante l’elaborazione parallela, causando il mantenimento degli indicizzatori nello stato &quot;funzionante&quot; e la generazione di errori SQL (tabella non trovata).
In Magento 2.4.9-alpha3, la correzione assicura che gli indicizzatori vengano reindicizzati correttamente con il blocco dell’applicazione abilitato.

_AC-15270 - [Problema GitHub](https://github.com/magento/magento2/issues/40102) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Aggiornare i collegamenti ai documenti e risolverli

_AC-15340 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Problema] registra il plug-in non dichiarato solo se non è disabilitato

Questa PR corregge e registra il plug-in che non è dichiarato e non è utilizzato (istanza abilitata e mancante).

_AC-15386 - [Problema GitHub](https://github.com/magento/magento2/issues/40086) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework versione 103.0.8-p2: classe EmailMessage che chiama un metodo inesistente

_AC-15446 - [Problema GitHub](https://github.com/magento/magento2/issues/40170) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [I Data/Schema Patches getAliases() di Magento 2.3.x] causano errori durante `setup:upgrade`

getAliases() causa errori durante l&#39;installazione:upgrade. Questa PR corregge lo stesso

_AC-15559 - [Problema GitHub](https://github.com/magento/magento2/issues/31396) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38239)_

#### Previsto tipo &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Trovato &#39;Magento\Customer\Model\Group&#39;.

È stato risolto un problema che causava un errore di tipo durante il salvataggio di un gruppo di clienti tramite GroupRepositoryInterface tramite GroupFactory.
In precedenza, l’archivio prevedeva GroupInterface, ma sono state passate le istanze del modello Group, causando un errore irreversibile.
Ora, i gruppi di clienti possono essere salvati correttamente tramite l’archivio garantendo la corretta implementazione dell’interfaccia.
In questo modo vengono risolti gli avvisi IDE e gli errori di runtime durante la creazione o l’aggiornamento programmatico dei gruppi di clienti.

_AC-6909 - [Problema GitHub](https://github.com/magento/magento2/issues/36269)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8349 - [Problema GitHub](https://github.com/magento/magento2/issues/37266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8350 - [Problema GitHub](https://github.com/magento/magento2/issues/37265) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8359 - [Problema GitHub](https://github.com/magento/magento2/issues/37262) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8362 - [Problema GitHub](https://github.com/magento/magento2/issues/37259) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Backup` e `Magento_Bundle`

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8367 - [Problema GitHub](https://github.com/magento/magento2/issues/37244) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problema] Correzione del nome della variabile in catalogsearch

Il sistema ora assegna correttamente i nomi alle variabili nel modulo del motore di ricerca, migliorando la chiarezza del codice e la manutenibilità. In precedenza, veniva utilizzato un nome di variabile irrilevante, $defaultCountry, nel modulo del motore di ricerca, causando confusione.

_AC-9215 - [Problema GitHub](https://github.com/magento/magento2/issues/37810) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Problema del server potenzialmente causato da una chiave di accesso S3 non valida

Credenziali AWS S3 errate non causano più il caricamento infinito delle pagine sulla vetrina.

_ACP2E-3890 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js non funziona

Quando la minimizzazione JS è abilitata, ora i seguenti file JS sono minimizzati completamente e correttamente: mage/backend/tabs.min.j, jquery/jquery.validate.min.js e Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Di conseguenza, la convalida del campo della classe CSS di Page Builder funziona come previsto.

_ACP2E-3925 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Il processo Cron non cancella la tabella del database, causando interruzioni dovute all’arresto anomalo di Galera

La pulizia delle tabelle del registro modifiche è ora in esecuzione in batch per evitare operazioni di eliminazione complesse.

_ACP2E-3995 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Il file JS non minimizzato a volte viene caricato ignorando &quot;abilita minimizzazioni js&quot;

Prima della correzione, anche se era stata abilitata la minimizzazione, alcuni dei file JS venivano richiesti senza il prefisso &quot;min&quot;, dando luogo al codice di stato 404. Dopo la correzione, quando la minimizzazione è abilitata non sono richieste risorse JS non minimizzate.

_ACP2E-4058 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Attributo data nel gruppo di attributi personalizzato: impossibile visualizzare Datepicker in Admin

È stato risolto un problema a causa del quale la finestra a comparsa del calendario per gli attributi di data veniva visualizzata fuori schermo quando veniva assegnata a gruppi di attributi personalizzati.

_ACP2E-4060 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### GraphQL ordine cliente: il recupero delle categorie di prodotto per il prodotto associato &quot;non è visibile singolarmente

Prima della correzione, se l’ordine conteneva un prodotto nascosto, le sue categorie visualizzavano un array vuoto nella risposta Customer Order GraphQl.
Ora, dopo la correzione, le categorie di prodotti vengono incluse nella risposta di una richiesta GraphQl dell’ordine del cliente anche se il prodotto è nascosto.

_ACP2E-3945 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [Cloud] getRemoteAddress restituito 127.0.0.1 in produzione

Prima di questa correzione, l&#39;indirizzo remoto non veniva determinato correttamente quando si utilizzava il server applicazioni. Dopo la correzione, l’indirizzo remoto viene determinato correttamente insieme alla corretta configurazione dell’intestazione nelle configurazioni di indice e intestazione.

_ACP2E-3991 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] Conferma la reversione del comportamento di gestione delle eccezioni di posizionamento dell&#39;ordine GQL

È stata risolta una modifica non compatibile con le versioni precedenti per la mutazione placeOrder.

_ACP2E-4031 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Mappatura del problema del messaggio tradotto in codice di errore durante l’ordine tramite GraphQL

È stato risolto un problema che si verificava durante l’utilizzo del messaggio di eccezione tradotto per mappare il codice di errore per le richieste GraphQL, causando codici di errore sconosciuti per gli errori noti.

_ACP2E-4033 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD] Il filtro Ordine cliente non funziona per le Date

Dopo la correzione, il recupero degli ordini tramite GraphQL utilizzando un filtro per intervalli di date restituisce il risultato corretto.

_ACP2E-4090 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Affrontare le questioni sollevate in ACP2E-4031

Prima della correzione la posizione del nodo di errore non forniva compatibilità diretta con le versioni 2.4.7 e 2.4.9. Ora, dopo la correzione, il nodo di errore viene posizionato correttamente per adattarsi a entrambe le versioni.

_ACP2E-4115 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Raggruppamento padre che mostra esaurito anche il figlio ha una scorta nella chiamata Graphql

Dopo la correzione, la richiesta di un elenco di prodotti tramite GraphQL restituisce lo stato corretto delle scorte per i prodotti bundle.

_ACP2E-4168 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Inventory/MSI

#### Discrepanze nelle mutazioni GraphQL mergeCart

Dopo la correzione, la richiesta di unione carrelli GraphQL controlla correttamente la quantità di prodotto, tenendo conto della configurazione delle scorte.

_ACP2E-4184 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, sicurezza

#### La reimpostazione della password del cliente tramite GraphQL non rispetta le restrizioni

È stato risolto un problema a causa del quale le richieste di reimpostazione della password del cliente effettuate tramite le mutazioni di GraphQL non rispettavano le restrizioni di reimpostazione della password configurate in Store > Configurazione > Clienti > Configurazione cliente > Opzioni password. Queste impostazioni vengono ora applicate correttamente.

_ACP2E-3992 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importa/esporta

#### Importazione prodotto CSV: impossibile annullare l&#39;impostazione di un&#39;immagine campione

Prima della correzione non era possibile aggiornare l’immagine campione di un prodotto tramite l’importazione del prodotto. Ora, dopo la correzione, se contrassegni la colonna dell’immagine del campione di prodotto con l’indicatore vuoto configurato, l’immagine verrà impostata su nascosta.

_ACP2E-3972 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Il programma di importazione prodotti genera URL vuoti per l’ambito del Negozio

La chiave dell’URL del prodotto nella vista Store ora eredita il valore impostato nell’ambito predefinito se url_key ha un valore vuoto nell’origine dati di importazione. Se in precedenza si impostava url_key su un valore vuoto nell’origine dati di importazione per un record della vista archivio, il valore url_key veniva sovrascritto con un valore vuoto in tale ambito.

_ACP2E-4038 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Il processo di importazione del prodotto rileva un errore se è configurato un attributo a selezione multipla come richiesto

È stato risolto un problema che causava un errore nelle importazioni del prodotto se era incluso un attributo obbligatorio di tipo a selezione multipla. La convalida dei dati ora viene passata correttamente, consentendo il completamento corretto del processo di importazione del prodotto.

_ACP2E-4057 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] prodotti senza ordini arretrati selezionati per gestire le scorte, consentendo ai clienti di ordinare le scorte superiori al livello corrente al momento dell&#39;importazione

Dopo la correzione, non è più possibile importare un valore non accettabile per l’attributo &quot;allow_backorders&quot; del prodotto.

_ACP2E-4116 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Importazione del prodotto non riuscita a causa di una lunghezza della descrizione superiore a 65.536 caratteri Convalida

Dopo la correzione, è possibile importare attributi di prodotto con testo di tipo i cui valori superano i 65.536 caratteri.

_ACP2E-4119 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Inventario/MSI

#### Operazione di eliminazione del magazzino non completata

Dopo la correzione, l’eliminazione di un elemento sorgente non comporta una reindicizzazione completa e aggiorna solo i prodotti interessati, aumentando le prestazioni.

_ACP2E-3917 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI] Nessuna indicazione nell&#39;amministratore se il cliente è stato avvisato in modo asincrono che l&#39;ordine è pronto per il ritiro

Aggiunta alla notifica della cronologia degli ordini relativa alla notifica asincrona al cliente relativa all&#39;ordine pronto per il ritiro

_ACP2E-3968 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Query duplicate sullo stato delle scorte al caricamento del preventivo

È stata corretta l’esecuzione duplicata della query cataloginventory_stock_status durante il caricamento di un preventivo nella vetrina, causando chiamate ridondanti al database.

_ACP2E-4102 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/fc15a9ae)_

#### ACP2E-4118 dopo la patch: la modifica della soglia di magazzino in Amministrazione causa una mancata corrispondenza tra le quantità di vendita negative e lo stato del magazzino

Lo stato delle scorte viene ora regolato automaticamente quando le configurazioni di scorte globali Quantità, ordini inevasi e soglia scorte esaurite vengono aggiornate tramite l&#39;importazione.

_ACP2E-4142 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### Ordine

#### Magento 2.4.8 GraphQL - Formattazione errata di order_date per gli articoli dell’ordine

È stato risolto un problema a causa del quale il campo order_date nella risposta di GraphQL restituiva in formato aaaa-mm-gg.
Ora, order_date viene visualizzato correttamente nel formato gg-mm-aaaa.

_AC-14431 - [Problema GitHub](https://github.com/magento/magento2/issues/39805) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### E-mail di spedizione non inviata quando inviata dalla vista Ordine amministratore nonostante sia abilitata nella configurazione archivio

Il sistema ora invia un&#39;e-mail di conferma della spedizione poiché è abilitata nella configurazione del negozio in cui è stato effettuato l&#39;ordine.

_AC-14563 - [Problema GitHub](https://github.com/magento/magento2/issues/39861) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39897)_

#### Il filtro in base alla data non funziona a causa di nomi di campo ambigui

In Magento 2.4.7-p6, è stato segnalato un errore dovuto ai join con i moduli Braintree quando si filtra la griglia dell’ordine per data.
Il problema riguardava l’unione di query braintree_transaction_details e sales_order durante l’applicazione di filtri per data.
Adobe Commerce Engineering ha esaminato il caso, ma non è stato in grado di riprodurre l’errore nell’ambiente.
Il comportamento previsto prevede che il filtro per data restituisca gli ordini che corrispondono al filtro senza errori.

_AC-15037 - [Problema GitHub](https://github.com/magento/magento2/issues/40024)_

#### Magento2: impossibile creare la regola di promozione

Questa PR risolve,
modello \Magento\Catalog\Model\ResourceModel\Eav\Attribute invece di \Magento\Catalog\Model\ResourceModel\Eav\Attribute nel metodo \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema GitHub](https://github.com/magento/magento2/issues/12176) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30479)_

#### Annulla reindirizzamento fattura a 404

L&#39;annullamento della fattura eseguita con il tipo Non acquisire non porta più alla pagina 404.

_ACP2E-4001 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### I processi Cron dell&#39;archivio vendite causano problemi di blocco del database

Prima della correzione, le query DELETE non associate che si trovavano nell’archivio cron causavano problemi con Galera. Ora, dopo l’aggiornamento, le query di eliminazione vengono eseguite con limiti.

_ACP2E-4010_

#### Problema con gli ordini aggiornati con opzioni configurabili utilizzando l’API REST

Mantenere le opzioni prodotto esistenti sugli articoli dell&#39;ordine di vendita durante l&#39;aggiornamento di un ordine tramite endpoint API rest.

_ACP2E-4061 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Altri strumenti per sviluppatori

#### [Problema] Pulizia del codice non utilizzato.

Il sistema ora rimuove il codice non utilizzato relativo alle importazioni non utilizzate.

_AC-10980 - [Problema GitHub](https://github.com/magento/magento2/issues/38424) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33499)_

#### [Problema] accessibilità: i ruoli WAI-ARIA nidificati nel menu non sono corretti

Il sistema ora genera l’accessibilità del faro senza che i ruoli WAI-ARIA nidificino in modo errato nell’errore di menu e il report dovrebbe essere verde

_AC-15082 - [Problema GitHub](https://github.com/magento/magento2/issues/40045) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38617)_

#### Errore della console nell’anteprima e-mail in Magento admin

Il sistema non genererà alcun errore della console durante l’anteprima del modello e-mail

_AC-9245 - [Problema GitHub](https://github.com/magento/magento2/issues/37820) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37933)_

### Pagamenti

#### Gli IPN sconosciuti di PayPal abusano del processore IPN dell&#39;applicazione

Il gestore IPN ora ignora i tipi IPN non supportati o sconosciuti. Invece di restituire un errore 500, registra il problema e continua l’elaborazione senza interruzioni.

_ACP2E-4049 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Token carta salvata PayflowPro non riuscito al pagamento

Gli ID transazione PayFlow Pro (PNREF) di PayPal sono ora validi per l&#39;utilizzo nelle transazioni di riferimento per un periodo fisso di 12 mesi. Una volta scaduta, la scheda salvata non viene più visualizzata e deve essere aggiunta di nuovo. In precedenza, la validità era determinata dalla data di scadenza della carta di pagamento utilizzata nella transazione originale.

_ACP2E-4064 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Prestazioni

#### [Problema] L&#39;aggiornamento non può essere modificato dal controllo della cache di utilizzo per il sito statico

Questa PR migliora le prestazioni poiché non convalida il contenuto statico a ogni caricamento di pagina fino a quando &amp; non ne cambia la versione.

_AC-15171 - [Problema GitHub](https://github.com/magento/magento2/issues/39486) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39484)_

#### [CLOUD] Impossibile aggiungere prodotti alle categorie

Sono state migliorate le prestazioni durante l’aggiunta di prodotti alla categoria tramite Visual Merchandiser.

_ACP2E-3946 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate su 10.000 registri

In precedenza, la cache veniva cancellata a ogni visita del PLP o del carrello, causando un sovraccarico di prestazioni non necessario. La cache delle regole di destinazione non viene più invalidata su queste pagine, migliorando l’efficienza della navigazione.

_ACP2E-4059_

### Prezzi

#### Il prodotto viene salvato anche quando la data di inizio del prezzo speciale è successiva alla data di fine utilizzando l&#39;azione di massa

È stato risolto un problema che consentiva di salvare i prodotti con un intervallo di date di prezzo speciale non valido senza convalida.
Ora viene visualizzato un messaggio di errore: &quot;Assicurarsi che la data di fine sia successiva o uguale alla data di inizio.&quot;

_AC-15252 - [Problema GitHub](https://github.com/magento/magento2/issues/40113) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Mancata corrispondenza dei dettagli di spedizione dopo aver completato l&#39;estrazione di paypal express per un preventivo negoziabile.

Questo problema ha risolto una mancata corrispondenza delle spese di spedizione durante il completamento di un Checkout PayPal Express per un preventivo negoziabile approvato.
Prima della correzione, la spedizione veniva erroneamente raddoppiata (mostrando $10 invece di $5) portando a totali gonfiati.
La correzione in Magento 2.4.9-alpha3 garantisce l&#39;applicazione delle spese di spedizione corrette

_AC-15280_

#### Il prezzo speciale non entra in vigore con i siti web creati con fusi orari diversi

Prima della correzione, la validità della data del prezzo speciale veniva creata nell’ambito della marca temporale del negozio corrente. Ora, dopo la correzione, viene preso in considerazione il fuso orario predefinito dell’archivio.

_ACP2E-4002_

#### Il prezzo regolare non è visibile, anche se viene applicato un prezzo speciale.

È stato risolto un problema che impediva la visualizzazione del prezzo regolare quando veniva applicato un prezzo speciale. Il prezzo normale ora appare correttamente insieme al prezzo speciale previsto.

_ACP2E-4100 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Prodotto

#### Per un prodotto configurabile per il test case AC-6158 viene ancora visualizzata l&#39;etichetta &quot;As low as&quot; (Come basso come)

Prodotti configurabili implementati e verificati (P1-P7) con relative assegnazioni di varianti e categorie. Garantire la corretta visualizzazione del prezzo di vendita e il comportamento dell&#39;etichetta &quot;As low as&quot; per i prodotti della categoria C.

_AC-10847 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Registrazione Aggiuntiva Quando La Richiesta Di Un Prodotto Tramite Archivio Non Riesce

Messaggi di errore migliorati per ProductRepository::get e getById quando non viene trovato uno SKU o un ID.
In precedenza, le eccezioni non fornivano alcun contesto in merito allo SKU o all’ID che causava l’errore.
Ora, il messaggio di eccezione include lo SKU o l’ID mancante, facilitando il debug e migliorando l’esperienza di sviluppo.
Questa modifica non influisce su alcun comportamento funzionale dell’API.

_AC-15199 - [Problema GitHub](https://github.com/magento/magento2/issues/40090) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Prodotti semplici non assegnati quando il prodotto configurabile è stato modificato da un ruolo limitato

Prima di questa correzione, se un utente amministratore con restrizioni salvava un prodotto configurabile che conteneva prodotti semplici a cui l’utente amministratore non aveva accesso, veniva rimosso dal prodotto configurabile al momento del salvataggio. Dopo la correzione, il prodotto configurabile viene mantenuto come salvato da un amministratore a pieno diritto.

_ACP2E-4081_

#### Le prestazioni di generazione di [Cloud] Sitemap sono significativamente ridotte

La generazione di sitemap per i prodotti con immagini non subisce più un rallentamento esponenziale. In precedenza, la generazione di sitemap per i negozi in cui era abilitata l’inclusione delle immagini comportava tempi di elaborazione lunghi.

_ACP2E-4153 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Promozione

#### Errore nell’ottenere gli sconti sull’articolo ordine apply_to per l’ordine del cliente tramite la richiesta del cliente GraphQl

In precedenza, quando si osservava l’errore del server interno nella richiesta del cliente GraphQl con sconti apply_to per l’ordine del cliente, ora è fisso e vengono recuperati i dati corretti dell’ordine del cliente con sconti applicati

_AC-14888 - [Problema GitHub](https://github.com/magento/magento2/issues/39963) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Errore nell’ottenere il codice del coupon dell’articolo dell’ordine tramite la richiesta del cliente GraphQl

È stato risolto un problema a causa del quale il recupero degli ordini con i dettagli del coupon tramite GraphQL restituiva un errore interno del server.
Ora la query viene eseguita correttamente e restituisce le informazioni corrette del coupon nella risposta.

_AC-14889 - [Problema GitHub](https://github.com/magento/magento2/issues/39962) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Chiave array non definita in ProductRepository getById

Il problema si verificava quando ProductRepository::getById() veniva chiamato con un ID non valido come 123abc, causando un errore di tipo &quot;Chiave array non definita&quot;.
Dopo la correzione in Magento 2.4.9-alpha3, tali richieste ora restituiscono correttamente una pagina 404 invece di generare un’eccezione.
Il controllo qualità è stato confermato con ID validi e non validi e non sono stati osservati ulteriori problemi.

_AC-15345 - [Problema GitHub](https://github.com/magento/magento2/issues/40146) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### [Cloud] La generazione di sitemap non termina mai

Prima della correzione, la generazione della sitemap non poteva terminare correttamente se il catalogo conteneva più di un milione di prodotti. Dopo la correzione, la generazione della sitemap terminerà con un’allocazione di memoria inferiore e un massimo di un milione di prodotti per store.

_ACP2E-3902 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### [Il commutatore di store cloud] non funziona da EN a FR per la pagina delle domande frequenti

È stato risolto un problema a causa del quale, passando da una visualizzazione store a un’altra, gli utenti venivano reindirizzati alla home page e non alla corrispondente pagina CMS tradotta. Il commutatore del negozio ora verifica la riscrittura degli URL nel negozio di destinazione per garantire il corretto reindirizzamento (ad esempio, pagina FAQ in inglese → pagina FAQ in francese).

_ACP2E-4112_

### Staging e anteprima

#### Interruzioni dell’anteprima dell’aggiornamento di staging al momento dell’estrazione quando si utilizza un altro dominio amministratore

Un cliente può effettuare l’accesso e visualizzare il carrello in modalità anteprima punto vendita quando l’URL della base del negozio è diverso dall’URL dell’amministratore.

_ACP2E-3906_

#### Dashboard gestione temporanea del contenuto Visualizzazione dell’ora non corretta

Ora i filtri di data &quot;Ora di inizio&quot; e &quot;Ora di fine&quot; in &quot;Dashboard di staging del contenuto&quot; mostrano la data e l’ora corrette. In precedenza, dopo aver selezionato la data e l’ora nel datepicker venivano visualizzate data e ora errate

_ACP2E-3969_

#### L’ambito mostra una visualizzazione diversa dello store durante l’anteprima per i prodotti e la categoria con aggiornamento pianificato

Precedentemente a questa correzione, il collegamento di anteprima per categorie e prodotti non veniva generato per l’archivio corretto. Dopo questa correzione, il collegamento di anteprima selezionerà automaticamente l’archivio in cui è stata creata l’anteprima.

_ACP2E-4053_

### Framework interfaccia utente

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Backend`

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8814 - [Problema GitHub](https://github.com/magento/magento2/issues/37522) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36976)_

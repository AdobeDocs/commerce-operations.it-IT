---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '24355'
ht-degree: 0%

---
# Problemi risolti in Magento Open Source (v2.4.9-beta1)

## Sono stati risolti i problemi in v2.4.9-beta1

Sono stati risolti 501 problemi nel codice core Magento Open Source 2.4.9-beta1. Di seguito è descritto un sottoinsieme dei problemi risolti inclusi in questa versione.

### API

#### Il campo Prezzo speciale fino a data non viene convalidato correttamente in applySpecialPrice

Il sistema funziona correttamente per quanto riguarda il prezzo speciale e il prezzo speciale del prodotto scadrà alla data impostata dall’amministratore o dal sistema di terze parti dall’API REST

_AC-13130 - [Problema GitHub](https://github.com/magento/magento2/issues/39169) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39690)_

#### [WebAPI] conferma e-mail cliente tramite paradosso WebAPI

È stato risolto un problema che impediva ai clienti di attivare i propri account tramite WebAPI a causa di un paradosso di autorizzazione che richiedeva un token prima della conferma. L’aggiornamento consente ai clienti non confermati di attivare correttamente i propri account tramite l’API, garantendo un flusso di conferma coerente e funzionale.

_AC-13281 - [Problema GitHub](https://github.com/magento/magento2/issues/39255) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

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

#### [Problema] L&#39;opzione di attributo chiarito esiste già nella risposta

Il sistema ora ha sostituito la frase scomoda &quot;Ottieni nuovo nome file se lo stesso esiste già&quot; con una versione più chiara e grammaticalmente corretta: &quot;Ottieni un nuovo nome file se ne esiste già uno&quot;. Ciò migliora la leggibilità e la comprensione da parte dell’utente.
Lo stesso per la risposta dell’opzione dell’attributo.

_AC-15473 - [Problema GitHub](https://github.com/magento/magento2/issues/39943) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39941)_

#### Errore interno del server nell’endpoint API /V1/products/special-price

È stato risolto un problema a causa del quale le richieste non valide inviate a /V1/products/special-price e alle relative API di determinazione prezzi restituivano un errore interno del server 500 a causa di un TypeError nullo.
Ora le API convalidano correttamente l’input e restituiscono un errore 400 per payload non validi, migliorando la gestione degli errori e l’affidabilità dell’API.

_AC-6419 - [Problema GitHub](https://github.com/magento/magento2/issues/35934) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Errore interno del server nell&#39;endpoint API `/V1/order/&lbrace;orderId&rbrace;/ship`

Il sistema ora corregge l&#39;errore del server interno nell&#39;endpoint API `/V1/order/{orderId}/ship` e restituisce un errore 400 poiché la richiesta non è valida.

_AC-6420 - [Problema GitHub](https://github.com/magento/magento2/issues/35931) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38282)_

#### Errore interno del server nell’endpoint API /V1/creditmemo

È stato risolto un problema a causa del quale le richieste non valide inviate all&#39;API /V1/creditmemo restituivano un errore interno del server 500.
Ora l’API convalida correttamente la richiesta e restituisce un errore 400 per payload non validi, migliorando la gestione e la stabilità degli errori.

_AC-6422 - [Problema GitHub](https://github.com/magento/magento2/issues/35924) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### L’API REST e il backend Magento utilizzano metodi di convalida diversi per attribute_code durante la creazione di nuovi attributi

È stata risolta un’incoerenza che consentiva l’utilizzo di lettere maiuscole in attribute_code da parte dell’amministratore di Magento, ma che veniva rifiutata dall’API REST durante la creazione dell’attributo del prodotto.
Ora, sia l’API Admin che REST seguono la stessa convalida, consentendo la corretta creazione di attributi con lettere maiuscole.

_AC-6660 - [Problema GitHub](https://github.com/magento/magento2/issues/33138) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Convalida diversa tra la creazione e l’aggiornamento degli attributi tramite API REST

È stato risolto un problema a causa del quale una convalida incoerente durante la creazione dell’attributo tramite l’API REST causava l’assegnazione di backend_type errato.
Ora, il sistema imposta il tipo di backend corretto quando è valido, genera un’eccezione per valori non validi o effettua il fallback in modo appropriato se non fornito, garantendo un comportamento dell’attributo coerente.

_AC-6885 - [Problema GitHub](https://github.com/magento/magento2/issues/36327) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Il corpo o i parametri della richiesta non validi causano un errore interno del server

I parametri o i corpi di richiesta in formato non valido ora restituiscono una risposta &quot;400 Richiesta non valida&quot;.
In precedenza, l’invio di corpi di richiesta o parametri non validi a vari endpoint API REST (ad esempio /V1/carts/search, /V1/orders, /V1/products, ecc.) causava un &quot;Errore interno del server&quot; generico (500), rendendo difficile la diagnosi dei problemi di input.
Ora Adobe Commerce restituisce una risposta &quot;400 Bad Request&quot;, che fornisce un feedback più chiaro quando le richieste non sono valide.

_AC-746 - [Problema GitHub](https://github.com/magento/magento2/issues/32784) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Nell&#39;endpoint `/orders` (o `/orders/:id`) mancano i campi &quot;state&quot; e &quot;status&quot;

È stato risolto un problema a causa del quale le risposte API `/orders` e `/orders/{id}` omettevano i campi di stato e stato quando i valori del database erano nulli.
Ora, entrambi i campi vengono restituiti in modo coerente nella risposta, garantendo la conformità con la documentazione API e migliorando l’affidabilità dei dati.

_AC-9244 - [Problema GitHub](https://github.com/magento/magento2/issues/37807) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

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

#### Order &quot;base_row_total&quot; e &quot;row_total&quot; mostrano il prezzo di un singolo articolo nella risposta API REST

La risposta dell’API REST per i dettagli dell’ordine ora contiene valori corretti per gli attributi &quot;base_row_total&quot; e &quot;row_total&quot; nel caso in cui siano stati ordinati più elementi uguali

_ACP2E-3874 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### L’endpoint REST API export-stock-salable-qty restituisce un valore item total_count errato

È stato risolto un problema di paginazione nell’API della quantità vendibile delle scorte di esportazione in magazzino in cui total_count era limitato in modo errato alla dimensione della pagina. In precedenza, quando si utilizzava l’endpoint /rest/all/V1/inventory/export-stock-salable-qty/website/base con parametri di impaginazione come page_size=5, il campo total_count nella risposta restituiva 5 invece del numero totale effettivo di prodotti che corrispondono ai criteri di ricerca. Dopo questa correzione, il campo total_count ora riflette correttamente il numero totale di prodotti disponibili indipendentemente dal parametro page_size, garantendo un comportamento di impaginazione coerente in tutti gli endpoint API REST di Magento.

_ACP2E-4086 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Problema di convalida con gli ID di opzioni personalizzati nell’elemento del carrello API REST.

API REST V1/guest-carts/&lt;cartId>/items/ e V1/carts/mine/items/ ora convalidano &quot;product_options.extension_attributes.custom_options.*.option_id&quot; per garantire che faccia riferimento a un option_id valido per lo SKU dell’articolo del carrello. In precedenza, questo parametro veniva elaborato e salvato nel database senza convalida.

_ACP2E-4138 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Durante il recupero del prodotto dal carrello e la modifica della lingua dell’intestazione del negozio non cambia

La query customerCart di GraphQL ora restituisce i valori dell’attributo del prodotto in base al valore dell’intestazione del negozio. In precedenza, la modifica della lingua dell’intestazione del negozio durante il recupero di un prodotto dal carrello tramite GraphQL non rispecchiava la lingua aggiornata, causando una localizzazione incoerente.

_ACP2E-4227 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### L’endpoint REST API/media non riesce per i prodotti Gift Card - restituisce &quot;Impossibile salvare il prodotto&quot;

Prima della correzione era possibile creare prodotti gift card che non includevano un importo nell’ambito globale. Con la correzione, è stata aggiunta una convalida che verifica la presenza di importi nell’ambito globale.

_ACP2E-4395 - [Problema GitHub](https://mcstaging.panini.it/shp_ita_it/)_

### API, carrello e pagamento

#### Per le informazioni sulla spedizione, la convalida lato server non funziona utilizzando l’API REST

È stato risolto un problema nell’API REST a causa del quale la convalida delle informazioni sull’indirizzo di spedizione non aderiva alla configurazione dell’attributo definita nel backend di amministrazione. La convalida ora segue correttamente le impostazioni configurate.

_ACP2E-4156 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### API, catalogo

#### Elimina endpoint API prezzi livello soglia interruzioni sito Web/negozio predefinito

In precedenza, l’eliminazione del sito web di base predefinito e l’utilizzo del sito web secondario come sito web predefinito causavano un errore durante il tentativo di aggiornare il prezzo del livello per il sito web secondario. Tuttavia, dopo l’applicazione di questa correzione, il prezzo del livello può essere aggiornato correttamente anche se il sito web di base viene eliminato o disattivato.

_ACP2E-4334 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### API, Framework

#### Eccezione RedisRequestLogger\RedisClient (limitatore di velocità) su Application Server

Dopo la correzione, la funzione di limitazione della frequenza può essere utilizzata insieme al server applicazioni GraphQL nei casi in cui è installata l&#39;estensione PHP redis.

_ACP2E-4237 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

### API, importazione/esportazione

#### L&#39;API di rimborso fatture asincrone crea rimborsi offline anziché online

Sono state corrette le operazioni di rimborso asincrone in cui le richieste di rimborso con il parametro `is_online` non venivano elaborate correttamente.

_ACP2E-4394 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

### API, ordine

#### [CLOUD] problema di informazioni ordine con aspetto totale riga per 000075568 ordine

Corregge il problema per cui il valore row_total_incl_tax nella risposta API dell’ordine veniva restituito come valore residuo vicino a zero invece di 0,00 quando un articolo veniva completamente scontato.

_ACP2E-3950 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Account

#### [Problema] Correzione degli errori di battitura nelle opzioni del modello del widget catalogo

Il sistema ora corregge gli errori di battitura nelle opzioni del modello Widget catalogo.

_AC-11576 - [Problema GitHub](https://github.com/magento/magento2/issues/38185) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38178)_

#### [Problema] È stata rimossa la spaziatura superflua nella griglia di back-end

Il sistema ora rimuove la spaziatura superflua nella griglia backend quando sono presenti elementi selezionati

_AC-11579 - [Problema GitHub](https://github.com/magento/magento2/issues/38502) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32622)_

#### Il codice del gruppo di clienti salvato non corrisponde all&#39;input quando si utilizzano caratteri multibyte

È stato risolto un problema a causa del quale i codici dei gruppi di clienti che utilizzavano caratteri multibyte venivano troncati e non corrispondevano al valore inserito. L’aggiornamento garantisce che l’input completo venga salvato correttamente, consentendo la creazione accurata di gruppi di clienti con nomi multibyte.

_AC-13335 - [Problema GitHub](https://github.com/magento/magento2/issues/39342) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problema durante l’aggiornamento dell’e-mail del cliente in Admin Panel con dominio ö e .swiss

Il pannello di amministrazione ora accetta le e-mail dei clienti con caratteri speciali e domini .swiss.
In precedenza, l’aggiornamento di un’e-mail del cliente a un indirizzo come max@möstermann.swiss non riusciva e conteneva errori relativi a nomi host e TLD non validi.
AC-13409

_AC-13409 - [Problema GitHub](https://github.com/magento/magento2/issues/39394) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### Lo switch abilitato per l’abbonamento alla newsletter non funziona per sito web/store

Il sistema gestisce correttamente l’abbonamento con la newsletter quando sono presenti più siti web/visualizzazioni di store quando è stata disabilitata a livello globale

_AC-14283 - [Problema GitHub](https://github.com/magento/magento2/issues/39751) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39752)_

#### [Problema] Rimozione della divulgazione e-mail completata

Ora il sistema visualizza un messaggio di errore che indica un messaggio e-mail errato se l’e-mail inserita non è necessaria per confermare l’account, indipendentemente dal fatto che il cliente esista o meno.

_AC-14561 - [Problema GitHub](https://github.com/magento/magento2/issues/39574) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39570)_

#### Impossibile cancellare il commento dell&#39;elemento della lista dei desideri tramite `updateProductsInWishlist` mutazione GraphQL

È stato risolto un problema a causa del quale i commenti della lista dei desideri non venivano aggiornati tramite mutazioni GraphQL.
Ora i commenti vengono aggiornati correttamente e si riflettono sia nella risposta API che nella vetrina.

_AC-14682 - [Problema GitHub](https://github.com/magento/magento2/issues/39911) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Il prodotto rimosso su dispositivi mobili viene comunque visualizzato nella sezione di confronto minima del Web fino al nuovo accesso

Il sistema ora rimuove il prodotto immediatamente scompare da tutte le visualizzazioni di confronto sia su dispositivi mobili che sul web, inclusa la sezione mini confronto.

_AC-14703 - [Problema GitHub](https://github.com/magento/magento2/issues/39905) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40023)_

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

#### Traduzione mancante titolo modale annullamento ordine

Il sistema ora risolve una traduzione mancante nella finestra modale di annullamento dell’ordine sulla vetrina. Quando un cliente fa clic sul pulsante &quot;Annulla&quot; nella pagina Il mio account > I miei ordini, viene visualizzata una finestra modale in cui viene richiesto un motivo di annullamento. Tuttavia, il titolo modale era precedentemente codificato e non traducibile. Questa modifica garantisce che il titolo modale utilizzi un metodo di traduzione corretto.

_AC-15260 - [Problema GitHub](https://github.com/magento/magento2/issues/40098) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40100)_

#### Problema dopo l’accesso a magento 2.4.8-p1

È stato risolto un problema su Magento 2.4.8-p1 a causa del quale il collegamento &quot;Crea un account&quot; era ancora visibile sulla home page dopo l’accesso.
Ora, il collegamento viene nascosto correttamente dopo l’accesso, in modo coerente con le altre pagine.

_AC-15292 - [Problema GitHub](https://github.com/magento/magento2/issues/40120)_

#### [Problema] Impostare isSecureArea prima di eliminare il cliente

Il sistema ora funziona correttamente e questa PR imposta isSecureArea per il processo di eliminazione e il cliente può registrarsi di nuovo correttamente.

_AC-15723 - [Problema GitHub](https://github.com/magento/magento2/issues/40211) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38462)_

#### [L&#39;operazione di eliminazione del cloud] non è consentita per l&#39;errore dell&#39;area corrente durante la creazione dell&#39;account del cliente

Dopo la correzione, il salvataggio di un cliente con un indirizzo non valido restituisce un messaggio che descrive il motivo dell’invalidità invece di irrilevante &quot;Operazione di eliminazione non consentita per l’area corrente&quot;.

_ACP2E-3791 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [B2B] le richieste Webapi vanno a ciclo infinito per i clienti connessi quando la cache &quot;eav&quot; è disabilitata

Dopo la correzione, la disattivazione della cache eav non comporta un loop infinito durante alcune richieste REST.

_ACP2E-4191 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Errore durante il caricamento di alcune impostazioni locali

È stato risolto un problema che impediva la creazione di un account cliente quando si utilizzavano le impostazioni internazionali in arabo e l’attributo Data di nascita era impostato per essere visualizzato nella vetrina. L’account può ora essere creato correttamente in questa configurazione.

_ACP2E-4311 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Errore Data non valida durante l&#39;aggiornamento delle informazioni sull&#39;account

I clienti ora possono aggiornare correttamente il proprio account quando utilizzano le impostazioni locali arabe. In precedenza, tentava di salvare le informazioni sull’account, ma la data di nascita non riusciva a causa di un errore di data non valida.

_ACP2E-4344 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Account, interfaccia utente amministratore

#### [Cloud] Nessuna entità di questo tipo con cartId

È stato risolto un problema a causa del quale l’utilizzo di Accedi come cliente con due account amministratore della società nella stessa sessione causava un errore &quot;Nessuna entità di questo tipo con ID carrello&quot;.

_ACP2E-4137 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### I messaggi di errore del modulo di creazione del cliente non vengono tradotti

È stato risolto un problema che impediva la corretta traduzione e formattazione dei messaggi di errore di convalida del cliente in diverse interfacce. Gli errori di convalida ora visualizzano correttamente i messaggi tradotti in tutte le aree dell&#39;applicazione: storefront, adminhtml, rest api e graphql.

_ACP2E-4354 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Interfaccia utente amministratore

#### Griglia prodotti categoria > Le colonne Stato e visibilità sono vuote quando si ordina per nome

È stato risolto un problema che causava la visualizzazione di colonne Stato e Visibilità vuote nella griglia Prodotti categoria durante l’ordinamento in base al nome del prodotto.
La griglia ora visualizza correttamente tutti i dati delle colonne dopo l’ordinamento, garantendo informazioni accurate sui prodotti nel pannello di amministrazione.

_AC-10659 - [Problema GitHub](https://github.com/magento/magento2/issues/38233) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### Modello e-mail store-switcher

È stato risolto un problema a causa del quale il commutatore store nell’anteprima del modello e-mail della newsletter non si apriva quando si faceva clic su a causa di un codice jQuery obsoleto. L’aggiornamento dell’evento di caricamento ha ripristinato la funzionalità corretta, consentendo agli utenti di accedere al commutatore dell’archivio come previsto.

_AC-12334 - [Problema GitHub](https://github.com/magento/magento2/issues/38892) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Il valore FPT nella pagina del carrello e nella pagina del prodotto sono diversi per le stesse configurazioni per il prodotto semplice

I valori FPT ora sono coerenti tra le pagine del carrello e quelle dei prodotti per i prodotti semplici.
In precedenza, i valori FPT (Fixed Product Tax) potevano differire nelle posizioni decimali tra le pagine del carrello e quelle dei prodotti, anche quando venivano applicate le stesse configurazioni.
AC-13066

_AC-13066 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Non è possibile salvare le opzioni per l&#39;attributo di selezione multipla/selezione quando i moduli Campioni sono disabilitati

È ora possibile salvare le opzioni per l&#39;attributo a selezione multipla/selezione quando i moduli Campioni sono disattivati.
In precedenza, la disattivazione dei moduli Campioni causava eccezioni durante la creazione di nuove opzioni per attributi a selezione multipla/selezione.
AC-13071

_AC-13071 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Il valore FPT nella pagina del carrello e nella pagina del prodotto sono diversi per le stesse configurazioni di un prodotto dinamico

I valori FPT ora sono coerenti tra le pagine del carrello e quelle dei prodotti per i prodotti dinamici.
In precedenza, i valori FPT (Fixed Product Tax) potevano differire nelle posizioni decimali tra le pagine del carrello e quelle dei prodotti per le stesse configurazioni.
AC-13075

_AC-13075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Formato data non rispettato nel componente interfaccia utente data

È stato risolto un problema a causa del quale il componente dell’interfaccia utente Data ignorava il formato configurato e visualizzava valori errati. La correzione assicura che il campo data ora rispetti il formato specificato (ad esempio, Y-m-d) sia per la visualizzazione che per l’input.

_AC-13174 - [Problema GitHub](https://github.com/magento/magento2/issues/39218) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Nessuna opzione disponibile per eliminare le origini

È stata aggiunta un’opzione di eliminazione per le origini inventario nell’interfaccia utente di amministrazione, che consente agli amministratori di rimuovere le origini aggiuntive invece di attivarle o disabilitarle. Questo miglioramento migliora la gestione dell’inventario fornendo un migliore controllo sulle sorgenti inutilizzate.

_AC-13354 - [Problema GitHub](https://github.com/magento/magento2/issues/32362) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### La struttura delle categorie in amministrazione non viene espansa per mostrare tutte le categorie nidificate selezionate dal livello 3

È stato risolto un problema che impediva l&#39;espansione della struttura ad albero delle categorie di amministrazione per visualizzare le categorie nidificate selezionate oltre il livello 3. Dopo la correzione, tutte le categorie selezionate vengono espanse automaticamente, migliorando la visibilità e l’usabilità nelle condizioni relative alle categorie.

_AC-13363 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema] Migliorare l&#39;esperienza utente con la struttura dei ruoli

Questa richiesta di pull aggiunge pulsanti per comprimere tutto, espandere tutto ed espandere i rami con gli elementi selezionati. Questa funzionalità è simile a quella fornita nella struttura delle categorie (Catalogo -> Inventario -> Categorie)

_AC-14020 - [Problema GitHub](https://github.com/magento/magento2/issues/39654) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36511)_

#### I registri delle azioni di importazione/esportazione non vengono creati in Sistema > Registri azioni > Griglia report

È stata implementata la registrazione per le azioni di amministrazione di importazione/esportazione in modo che vengano visualizzate in Sistema > Log azioni > Report. In questo modo viene garantito un migliore tracciamento dei controlli registrando le attività di importazione precedentemente mancanti.

_AC-14266 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: l’intestazione &quot;Sender&quot; deve essere un’istanza di &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (ottenuto &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

Adobe Commerce ora invia correttamente le e-mail di registrazione quando viene configurato un indirizzo del percorso restituito personalizzato per SMTP. In precedenza, su vanilla Adobe Commerce 2.4.8 con system/smtp/set_return_path impostato su 2 e system/smtp/return_path_email impostato su un indirizzo personalizzato, la registrazione del cliente veniva completata ma l’e-mail di registrazione non veniva inviata e Adobe Commerce registrava questo errore: Symfony\Component\Mime\Exception\LogicException: l’intestazione &quot;Sender&quot; doveva essere un’istanza di &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (ottenuto &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [Problema GitHub](https://github.com/magento/magento2/issues/39823) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1e14bd72) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1514117f)_

#### L&#39;ordine di aggiornamento non riceve i dati degli attributi personalizzati più recenti

È stato risolto un problema a causa del quale l’aggiornamento della pagina dell’ordine non visualizzava i dati degli attributi personalizzati più recenti del cliente. Dopo la correzione, i valori degli attributi aggiornati ora vengono rispecchiati senza dover annullare e ricreare l’ordine.

_AC-14690 - [Problema GitHub](https://github.com/magento/magento2/issues/30301)_

#### [Problema] sostituisce l&#39;escape obsoleto

È stato rimosso getEscaper() obsoleto e aggiunto tramite iniezione del costruttore.

_AC-15132 - [Problema GitHub](https://github.com/magento/magento2/issues/40062) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38135)_

#### Messaggio di benvenuto sovrapposto a una categoria di prodotto nella vista per dispositivi mobili

È stato risolto un problema dell’interfaccia utente a causa del quale il nome del benvenuto si sovrapponeva alle categorie di prodotto nella visualizzazione per dispositivi mobili, bloccando i clic.
Ora le categorie sono completamente visibili e cliccabili senza problemi di sovrapposizione.

_AC-15166 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Il pulsante Ripristina modulo interfaccia utente non funziona come previsto

Il sistema ora funziona correttamente quando si fa clic sul pulsante di ripristino senza ricaricare l’intera pagina, i dati del modulo verranno reimpostati.

_AC-15204 - [Problema GitHub](https://github.com/magento/magento2/issues/40092) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40094)_

#### [Problema] PageCache/AccessList: aggiunta del supporto CIDR

Il sistema ora accetta le richieste di eliminazione all&#39;interno di una rete, ed è più semplice fornire un intervallo CIDR.

_AC-15804 - [Problema GitHub](https://github.com/magento/magento2/issues/39953) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37809)_

#### [Problema] Aggiungi titoli esplicativi ai pulsanti di gestione della cache

Il sistema ora aggiunge titoli esplicativi ai pulsanti di gestione della cache quando si sposta il cursore

_AC-16212 - [Problema GitHub](https://github.com/magento/magento2/issues/38607) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38598)_

#### Fornire una funzione per eliminare di massa le aliquote utilizzando la griglia

Gli utenti amministratori ora possono eliminare simultaneamente più aliquote dalla griglia Aliquote amministrative.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problema GitHub](https://github.com/magento/magento2/issues/33399) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33484) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Colore al passaggio del mouse non applicato alle griglie statiche in amministrazione

I colori al passaggio del mouse vengono ora applicati come previsto sulle righe delle griglie statiche di amministrazione.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema GitHub](https://github.com/magento/magento2/issues/35358) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35384)_

#### &quot;Impossibile risolvere le voci del parametro reCAPTCHA&quot; in exception.log per Google reCAPTCHA Admin Panel

Un errore reCaptcha nel file `var/log/exception.log` per l&#39;accesso amministratore reCAPTCHA di Google V3 è stato risolto e non vengono registrati messaggi di errore. In precedenza, il seguente errore veniva generato ogni pochi secondi quando un utente amministratore configurava le impostazioni del **Configurazione** > **Sicurezza** > **Pannello di amministrazione Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema GitHub](https://github.com/magento/magento2/issues/34975) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contributo codice GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### La regola del prezzo del carrello con SKU condizione non tiene conto degli &quot;zeri iniziali&quot; nello SKU (sku: 01234 è uguale a 1234)

Il sistema ora gestisce correttamente la regola di prezzo del carrello con SKU condizione tenendo conto degli &quot;zeri iniziali&quot; nello SKU

_AC-9428 - [Problema GitHub](https://github.com/magento/magento2/issues/37919) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problema con il comportamento del valore dell’opzione attributo predefinito per la selezione multipla

Prima della correzione, i valori predefiniti per l’attributo di più opzioni non venivano salvati correttamente. Ora, dopo la correzione, i valori vengono memorizzati correttamente nel database.

_ACP2E-3523 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Problema durante lo spostamento della quantità di prodotto dal carrello all’amministratore

Quando crei un ordine dall’amministratore, i prodotti nel carrello dei clienti sulla barra laterale non scompaiono se aggiunti all’ordine.

_ACP2E-3563 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [Gestione temporanea2] Le schede archiviate non sono visibili nel pannello di amministrazione

Corregge il problema per cui l’opzione di pagamento &quot;Stored Card&quot; non veniva più visualizzata nel modulo di inserimento dell’ordine back-end dopo un aggiornamento.

_ACP2E-3830 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

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

_ACP2E-4052 - [Problema GitHub](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Blocchi bianchi visualizzati su entrambi i lati dell’intestazione della griglia di amministrazione

È stato risolto un problema di allineamento visivo nelle griglie di amministrazione. In precedenza, quando si scorreva orizzontalmente tra le griglie dei prodotti nel pannello di amministrazione, i blocchi bianchi risultavano non allineati sui lati sinistro e destro dell’intestazione della griglia. Gli elementi dell’intestazione della griglia ora mantengono un corretto allineamento verticale durante lo scorrimento, fornendo un’esperienza visiva più pulita per gli amministratori che gestiscono cataloghi di prodotti di grandi dimensioni.

_ACP2E-4104 - [Problema GitHub](https://mcprod.pap-store.acer.com/index.html)_

#### FileUploader del componente dell’interfaccia utente non funziona correttamente su 2.4.8-p1/ 2.4-development

È stato migliorato il caricamento dei file per il componente dell’interfaccia utente personalizzato con selezione multipla per consentire il caricamento al clic sull’area di caricamento.

_ACP2E-4162 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [In locale] Nuovi ordini, società o clienti creati automaticamente inclusi nell&#39;ambito &quot;Seleziona tutto&quot; durante il processo di selezione

È stato risolto il problema che causava l&#39;eliminazione involontaria di tutti i record da parte della selezione manuale di tutti i record in una pagina non aggiornata della griglia di amministrazione durante l&#39;esecuzione di azioni di massa. In precedenza, la griglia passava automaticamente alla modalità &quot;seleziona tutto&quot; internamente quando il numero di elementi selezionati corrispondeva al conteggio totale, causando azioni di massa per influenzare tutti i record invece di solo quelli selezionati in modo esplicito.

_ACP2E-4202 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### La soluzione di ACP2E-3362 funziona lentamente su MariaDB 10.6

Sono state migliorate le prestazioni della pagina di ricerca front-end in caso di un numero elevato di richieste di ricerca storiche.

_ACP2E-4225 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Il filtro data non funziona in base al fuso orario del negozio sulla griglia delle note di credito

Prima della correzione degli elenchi in base agli attributi di data causava elementi mancanti a causa di differenze di fuso orario tra la data selezionata e le date memorizzate Ora, dopo la corretta applicazione dei filtri di correzione data.

_ACP2E-4239 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### La finestra di dialogo Caricamento file si apre due volte quando è installato pagebuilder

Prima che il pulsante Correggi caricamento componente personalizzato si attivasse due volte. Dopo la correzione, il pulsante Carica funziona come previsto.

_ACP2E-4241 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Errori di convalida sugli attributi del cliente eliminati durante la modifica dei dati del cliente.

Prima della correzione, il salvataggio del cliente e dell’indirizzo del cliente non riusciva se includeva più opzioni di attributo eliminate. Dopo la correzione, entrambi possono essere salvati correttamente anche quando sono ancora presenti più opzioni di attributo.

_ACP2E-4281 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Avviso JS nel dashboard di amministrazione: &quot;Previsto avvio del loader ma non ne ho trovato uno nel DOM&quot;

È stato corretto l’avviso JavaScript visualizzato nella console del browser quando i grafici erano abilitati per il dashboard di amministrazione. In precedenza, quando si accedeva al dashboard di amministrazione con i grafici abilitati, un controllo di debug obsoleto segnalava erroneamente &quot;Previsto per avviare il caricatore ma non ne ha trovato uno nel dom&quot; anche se la funzionalità funzionava correttamente.

_ACP2E-4336 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Configurazione [CLOUD] Con Configurazione Dipendenza Modificabile Quando Si Utilizza La Configurazione Archivio Predefinito Archiviato

È stato risolto il problema che si verificava quando i campi Configurazione di sistema potevano essere abilitati dopo il caricamento della pagina, nonostante fosse selezionata l’opzione &quot;Usa predefinito/sito Web&quot;.

_ACP2E-4337 - [Problema GitHub](https://mcstaging.pap-store.acer.com) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Il grafico degli ordini del dashboard di amministrazione viene animato nelle dimensioni finali

Il grafico dell’ordine del dashboard di amministrazione ora viene visualizzato immediatamente senza la necessità di un’animazione di ridimensionamento non necessaria.

_ACP2E-4398 - [Problema GitHub](https://github.com/magento/magento2/issues/38860) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder non riesce a salvare il contenuto nella vista mobile a causa di un errore JS (TypeError: impossibile leggere le proprietà di non definito)

È stato risolto un problema che impediva il salvataggio delle pagine in Page Builder durante l’aggiunta di banner nella visualizzazione per dispositivi mobili.

_ACP2E-4399 - [Problema GitHub](https://github.com/magento/magento2/issues/38565) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Interfaccia utente amministratore, B2B

#### L’accesso B2B come intestazione del cliente presenta ancora il marchio Magento

In precedenza, l’intestazione della vetrina mostra &quot;Ora sei connesso come &lt;nome cliente> a &lt;nome negozio>&quot; con il branding Magento. Che è ora fisso e l’intestazione viene visualizzata con il branding ADOBE.

_AC-14361 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### Interfaccia utente amministratore, Catalogo

#### Il salvataggio del prodotto non riesce quando la regola del catalogo è attiva e la modalità tempo reale è abilitata

È stato risolto un problema che causava un errore di indicizzazione della regola catalogo con un errore di transazione DDL durante le operazioni di salvataggio del prodotto, separando l’indicizzazione della regola catalogo dalla transazione del prodotto.

_ACP2E-4378 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Interfaccia utente amministratore, contenuto

#### Eccezione &quot;Impossibile creare una rappresentazione per i percorsi delle risorse multimediali&quot; durante l’inserimento dell’immagine

Dopo aver rimosso i valori di Larghezza massima e Altezza massima della configurazione di Ottimizzazione immagine di Media Gallery, l’errore non si verifica più durante il processo di ottimizzazione dell’immagine.

_ACP2E-3781 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Interfaccia utente amministratore, Ordine

#### Creazione ordine amministratore: overflow delle dimensioni della sessione durante l’aggiunta di più di 20 prodotti (dimensione della sessione supera il limite di 256 KB)

È stato risolto un overflow della dimensione della sessione durante la creazione dell’ordine di amministrazione impedendo l’archiviazione nella sessione di risposte HTML di grandi dimensioni per le richieste JSON, garantendo il corretto funzionamento delle aggiunte in blocco di prodotti senza disconnettersi dall’amministratore.

_AC-15893_

### Interfaccia di amministrazione, protezione

#### Gestione password deboli

Non è possibile salvare l&#39;utente amministratore con la stessa password. In precedenza, era stato salvato senza una convalida corretta.

_ACP2E-3657 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Interfaccia utente amministratore, Imposta

#### Errore nell’interfaccia utente di amministrazione dell’aliquota

Questo ticket ha risolto un problema relativo all’interfaccia utente di amministrazione dell’aliquota, a causa del quale il passaggio da un paese all’altro (ad esempio, da Stati Uniti → Regno Unito) mostrava ancora lo stato statunitense precedentemente selezionato, ingannando gli utenti.
In 2.4.9-alpha3, il campo stato ora viene reimpostato su * quando il paese selezionato non ha stati.

_AC-8440 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/Generazione rapporti

#### [Problema] Aggiunto il inserisco nell&#39;elenco Consentiti di scp per Analytics se utilizzi solo Google Analytics

Questa PR aggiunge una whitelist CSP al modulo Google Analytics, consentendogli di funzionare in modo indipendente senza una dipendenza da Google Adwords. Google Analytics ora funziona correttamente anche quando il modulo Google Adwords è disabilitato.

_AC-16311 - [Problema GitHub](https://github.com/magento/magento2/issues/40051) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40032)_

#### Le intestazioni di file duplicate nei file CSV dei rapporti avanzati causano rapporti vuoti

Dopo la correzione, i rapporti generati per la funzione di reporting avanzato non contengono più righe di intestazione duplicate nei casi in cui il conteggio delle righe superi la dimensione batch.

_ACP2E-4187 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Il report del carrello abbandonato contiene caratteri non validi

Il rapporto Carrello abbandonato esportato come file CSV ora contiene caratteri riprodotti correttamente per simboli di valuta come rupia indiana quando viene aperto in MS Excel.

_ACP2E-4288 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Aggiornamento per MDVA-19640 per la compatibilità con la versione 2.4.8

La correzione sposta le attività del processo cron di Analytics dal gruppo predefinito al gruppo Analytics

_ACP2E-4309 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### I ricavi non vengono visualizzati nei report Ordini/Fatture nel sito Web/valuta di Amministrazione per Canada

Alcuni rapporti relativi agli ordini non applicavano i tassi della valuta dello store. Dopo la correzione, i rapporti applicano correttamente le percentuali di archiviazione configurate.

_ACP2E-4361 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### convalida del campo aziendale non riuscita per l&#39;estrazione guest

Il checkout ospite ora convalida correttamente il campo aziendale.
In precedenza, quando l’attributo company era obbligatorio, il checkout del guest non riusciva e veniva visualizzato l’errore: &quot;Company is a required value&quot; (La società è un valore obbligatorio), anche quando il campo era compilato.
AC-14987

_AC-14987 - [Problema GitHub](https://github.com/magento/magento2/issues/40011) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Prodotti API REST-render-info restituiscono il prezzo finale errato per il cliente connesso

Il ticket ha una correzione per Rest API products-render-info restituisce il prezzo finale errato per il cliente connesso

_AC-5979 - [Problema GitHub](https://github.com/magento/magento2/issues/35757)_

### B2B, carrello e pagamento

#### Nessuna entità di questo tipo con ID carrello = X errore viene visualizzata su Storefront quando si accede all’utente dell’azienda B2B dalla funzione di amministrazione &quot;Accedi come cliente&quot;

Ora l’errore &quot;Nessuna entità di questo tipo con ID carrello = X&quot; non è più visibile dopo il corretto accesso dal backend di amministrazione quando si utilizza la funzione &quot;Accedi come cliente&quot;.

_ACP2E-3994 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### L&#39;indirizzo di fatturazione mancante impedisce il posizionamento dell&#39;ordine con il metodo di spedizione &quot;In store Delivery&quot;

È stato risolto un problema a causa del quale l’indirizzo di fatturazione non veniva popolato automaticamente durante il pagamento, quando come metodo di consegna era selezionato Prelievo in-store. Senza un indirizzo di fatturazione, l&#39;estrazione non poteva essere completata.

_ACP2E-4030 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/42d23211)_

### Carrello e pagamento

#### Aggiornamento Magento 2.4.7 (mini)cart senza quantità decimale consentita

Ora Magento gestisce correttamente quando si aggiorna la quantità con i decimali dal mini carrello quando la lingua era NL (olandese)

_AC-13238 - [Problema GitHub](https://github.com/magento/magento2/issues/39236) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problema] Aggiungere EventPrefix ed EventObject per estrarre il modello di contratto

Il sistema ora include EventPrefix ed EventObject per il modello di contratto di pagamento, consentendo l&#39;attivazione degli eventi con un prefisso di evento. Questo miglioramento offre maggiore flessibilità agli sviluppatori quando lavorano con eventi di contratto di pagamento. In precedenza, il modello di contratto di pagamento non supportava EventPrefix e EventObject, limitando la possibilità di personalizzare la gestione degli eventi.

_AC-13252 - [Problema GitHub](https://github.com/magento/magento2/issues/32510) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Problema] Esperienza sviluppatore: stile codice AbstractItem offerta (SOP-348 di SwiftOtter)

Questa richiesta di pull corregge le dichiarazioni di metodo fuorvianti per i metodi Abstract Item.

_AC-13334 - [Problema GitHub](https://github.com/magento/magento2/issues/39340)_

#### Convalide quantità front-end prodotto raggruppato mancanti

Il sistema ora funziona correttamente e viene visualizzato un errore di convalida quando si tenta di aggiungere una quantità negativa e una quantità massima

_AC-13524 - [Problema GitHub](https://github.com/magento/magento2/issues/39479) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39480)_

#### [Problema] Aggiornamento subtotale.phtml

Il sistema aggiorna subtotal.phtml con la spaziatura corretta

_AC-13907 - [Problema GitHub](https://github.com/magento/magento2/issues/39619) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39612)_

#### Impossibile effettuare l&#39;ordine con l&#39;ospite

Adobe Commerce ora consente agli acquirenti ospiti di effettuare con successo gli ordini quando il campo del secondo nome è configurato come richiesto in Amministratore. In precedenza, in Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4), la configurazione del secondo nome come obbligatorio e il check-out come ospite impedivano il posizionamento dell’ordine anche quando veniva fornito un secondo nome, bloccando il completamento del checkout. AC-14241

_AC-14241 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql] Non può restituire null per il campo &quot;SelectedCustomizableOption.label&quot; che non ammette valori Null

Il sistema ora non genera un errore interno del server con un messaggio quando l’opzione selezionata non esiste più

_AC-14256 - [Problema GitHub](https://github.com/magento/magento2/issues/39729) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart non riesce ad aggiornare la quantità per gli articoli del carrello esistenti quando un articolo della lista dei desideri non è valido (Magento 2.4.7-p3)

È stato risolto un problema a causa del quale la mutazione addWishlistItemsToCart di GraphQL interrompeva l’elaborazione quando veniva rilevato un prodotto configurabile non valido. Dopo la correzione, gli elementi validi della lista dei desideri vengono aggiunti al carrello e le quantità vengono aggiornate, mentre gli elementi non validi vengono ignorati e vengono restituiti gli errori appropriati.

_AC-14464 - [Problema GitHub](https://github.com/magento/magento2/issues/39820) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] Non è possibile inserire ordini contenenti cifre da 0 a 9, e commerciale, punto e virgola o parentesi nel nome della città

È stato risolto un problema che impediva l’estrazione dei nomi delle città contenenti caratteri speciali come . , &amp; o parentesi.
Ora, gli ordini con tali nomi di città vengono inseriti correttamente senza errori di convalida.

_AC-14495 - [Problema GitHub](https://github.com/magento/magento2/issues/39854) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Prefisso ospite non salvato nell&#39;indirizzo preventivo 2.4.8

Il prefisso del cliente ospite (Sig/Sig.ra) viene ora salvato durante il pagamento.
In precedenza, i saluti selezionati dai clienti ospiti andavano persi prima di raggiungere l’ordine finale, mentre tutti gli altri campi dell’indirizzo venivano trasferiti correttamente.
AC-14705

_AC-14705 - [Problema GitHub](https://github.com/magento/magento2/issues/39915) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Sottoselezione regola di vendita con condizione Quantità non applicata

È stato risolto un problema a causa del quale le regole del prezzo del carrello con condizioni di sottoselezione del prodotto non venivano applicate al momento del pagamento.
Ora, gli sconti vengono applicati correttamente in base alle regole configurate.

_AC-14884 - [Problema GitHub](https://github.com/magento/magento2/issues/39965) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problema] Rimuovere lo spazio nell&#39;attributo di classe

Il sistema ora rimuove uno spazio aggiuntivo nell’attributo della classe

_AC-14939 - [Problema GitHub](https://github.com/magento/magento2/issues/39977) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39970)_

#### Graphql - Il carrello unione non funziona correttamente quando è abilitato l&#39;ordine arretrato

È stato risolto un problema che impediva l’unione degli articoli del carrello ospiti con il carrello clienti durante l’unione dei carrelli tramite GraphQL.
Ora, il carrello clienti riflette correttamente la quantità combinata dai carrelli ospiti e clienti.

_AC-15148 - [Problema GitHub](https://github.com/magento/magento2/issues/40064) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integrazione] [Estrazione] Direttive dipendenti aggiornate nel modello e-mail di pagamento non riuscito

Modello e-mail di pagamento non riuscito aggiornato per gestire correttamente le direttive dipendenti.
La correzione garantisce che l&#39;indirizzo di spedizione e il metodo di spedizione vengano visualizzati correttamente quando applicabile.
In precedenza, questi campi mancavano nelle e-mail di pagamento non riuscite.

_AC-15363 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Carrello] La pagina del carrello non viene caricata quando è abilitata l&#39;imposta fissa sui prodotti

È stato risolto un problema a causa del quale la pagina del carrello inseriva un caricamento infinito quando l’opzione FPT (Fixed Product Tax) era abilitata. Il problema è stato causato da calcoli del subtotale errati a causa dell&#39;inclusione dell&#39;imposta nello stesso elemento HTML del prezzo dell&#39;articolo, causando una mancata corrispondenza tra subtotali centrali e di riepilogo. Dopo la correzione, il carrello viene caricato correttamente e visualizza i totali corretti.

_AC-16096 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Regola prezzo carrello Condizione Azione &quot;Prezzo nel carrello&quot;, applicabile quando non dovrebbe

È stato risolto un problema a causa del quale le regole del prezzo del carrello con la condizione &quot;Prezzo nel carrello inferiore a&quot; venivano applicate in modo errato ai prodotti non ammissibili.
Ora, i coupon vengono convalidati e rifiutati correttamente quando i prezzi degli articoli nel carrello non soddisfano le condizioni della regola configurate.

_AC-6997 - [Problema GitHub](https://github.com/magento/magento2/issues/36433) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Problema] Imposta il prezzo sull&#39;articolo del preventivo anziché base_price

Il sistema gestisce correttamente il set di prezzi dell&#39;articolo del preventivo in base al prezzo base anziché al prezzo se in un sito Web sul front-end sono presenti più valute

_AC-9985 - [Problema GitHub](https://github.com/magento/magento2/issues/38094) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36878)_

#### I preventivi persistenti scaduti non vengono eliminati da un processo cron sales_clean_quote

Le virgolette persistenti scadute vengono ora cancellate quando viene eseguito il processo cron &#39;persistent_clear_expiry&#39;. In precedenza, le virgolette persistenti scadute non venivano cancellate da nessun altro processo cron.

_ACP2E-3493 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Errore &quot;Si è verificato un errore&quot; durante il pagamento per l’azienda inattiva

Prima della correzione, l’azione di logout non veniva completata correttamente nella pagina del carrello, se l’opzione longged in user company (azienda utente con longevo ritardi) non era più abilitata. Ora, se la società non è più disponibile, la disconnessione viene eseguita correttamente.

_ACP2E-3541 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La selezione degli indirizzi non viene salvata quando si esegue il Check-Out con più indirizzi

Prima della correzione durante l’annullamento dell’opzione di multishipping, l’indirizzo non veniva preselezionato quando si tornava al multiservizio. Ora l&#39;indirizzo predefinito viene sostituito da una delle selezioni effettuate nella schermata di configurazione multipla.

_ACP2E-3646 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [Cloud] Gli ordini recenti non vengono visualizzati in un&#39;altra visualizzazione archivio se gli ordini vengono creati in una visualizzazione archivio

È stato risolto un problema che impediva alla pagina &quot;Il mio account&quot; di visualizzare gli ordini recenti provenienti da altre visualizzazioni dello store. La logica di recupero degli ordini è stata aggiornata per garantire una visibilità coerente degli ordini in tutte le visualizzazioni dello store, in linea con il comportamento della pagina &quot;I miei ordini&quot;.

_ACP2E-3807 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### qtà visualizzata come  0 nella sezione admin customer shopping cart (Carrello acquisti cliente amministratore) durante l’aggiunta di prodotti BUNDLE  

Nella sezione Carrello acquisti in Attività cliente è ora visualizzata la quantità corretta. In precedenza, la quantità veniva visualizzata come 0.

_ACP2E-3872 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [Cloud] Lo sconto sulla spedizione gratuita non viene rimosso correttamente se il carrello non soddisfa più i requisiti

Il Subtotale (Escl. Imposta) nella regola del prezzo del carrello ora incorporerà gli sconti delle regole precedenti.

_ACP2E-3973 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Ordine duplicato trovato per lo stesso cliente in Multishipping

Le richieste simultanee di inserire un ordine con più indirizzi di spedizione non generano più ordini duplicati per lo stesso cliente

_ACP2E-4117 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] il messaggio di notifica del limite di azioni superato viene visualizzato due volte quando viene raggiunta la soglia di scorte esaurite

È stato risolto il problema che causava la visualizzazione di banner di errore duplicati negli aggiornamenti del carrello. In precedenza, dopo un errore di convalida di AJAX, il backend aggiungeva nuovamente lo stesso messaggio durante l’invio del modulo, così gli acquirenti visualizzavano due avvisi identici. Ora saltiamo l’aggiunta del messaggio di backend aggiuntivo, mantenendo la pagina del carrello su un singolo banner di errore chiaro.

_ACP2E-4192 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Per le informazioni di fatturazione la convalida lato server non funziona utilizzando l’API REST per le informazioni di spedizione

La convalida dei dati dell’indirizzo del cliente è stata migliorata per garantire una maggiore coerenza tra REST e GraphQl per l’estrazione.

_ACP2E-4223 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] problema prezzo prodotto bundle sulla pagina del carrello

È stato risolto il problema di prezzo del prodotto Bundle sulla pagina del carrello per i negozi a più valute

_ACP2E-4245 - [Problema GitHub](https://www.techbuyer.com/) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Gestisci problemi ambito negozio carrello acquisti

Ora, gli errori del carrello vengono visualizzati all’utente amministratore durante la gestione del carrello per un cliente assegnato a un sito web non predefinito. In precedenza, gli errori non venivano visualizzati.

_ACP2E-4348 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Tempi coupon_utilizzati ripristina dopo annullamento parziale della fattura

Il conteggio del coupon times_used ora viene aggiornato correttamente quando un ordine viene parzialmente annullato.

_ACP2E-4365 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Carrello e pagamento, GraphQL

#### Errore durante la mappatura del messaggio al codice di errore durante l’ordine tramite GraphQL

Le chiamate di GraphQL per effettuare un ordine per un carrello inesistente o inattivo ora restituiscono correttamente i codici di errore CART_NOT_ACTIVE o CART_NOT_FOUND in tutte le visualizzazioni archivio, risolvendo un problema a causa del quale i messaggi di errore tradotti in precedenza generavano un codice NON DEFINITO.

_ACP2E-3942 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] problema di sconto elemento carrello query carrello su preventivi virtuali

È stato risolto un problema a causa del quale la query del carrello di GraphQL restituiva un importo di sconto errato per i preventivi virtuali. In precedenza, gli sconti venivano erroneamente applicati a determinati prodotti virtuali non idonei.

_ACP2E-4248 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 crea un altro problema

Quando è stata effettuata una richiesta graphQL per un articolo con quantità insufficiente, è stato restituito un messaggio di errore corretto con un codice di errore e, se la quantità richiesta è disponibile, l’aggiornamento del carrello è riuscito.

_ACP2E-4404 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Carrello e pagamento, GraphQL, Inventario/MSI

#### L&#39;attributo is_available in CartItemInterface restituisce false anche quando le scorte vendibili sono elevate

L&#39;attributo is_available restituisce true quando le scorte vendibili sono elevate. In precedenza, restituiva sempre false.

_ACP2E-3885 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carrello e pagamento, Magazzino/MSI

#### 414 Errore nell’endpoint &quot;Ricerca posizione di prelievo&quot; con dimensioni del carrello elevate

La selezione di un negozio durante il pagamento con l’opzione &quot;Pick in Store&quot; non ha più esito negativo a causa della lunghezza degli URL quando molti prodotti sono nel carrello.
In precedenza, questo causava un errore 414 causato da URL eccessivamente lunghi generati durante la selezione dell’archivio, impedendo ai clienti di completare il pagamento.

_ACP2E-4266 - [Problema GitHub](https://mcstaging.casamyers.com.mx/) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/ae1f272f)_

### Carrello e pagamento, promozione

#### Il saldo visualizzato sulla gift card non è limitato dall’ambito del sito web

Il controllo del saldo della gift card è limitato all’ambito del sito web assegnato.

_ACP2E-4379 - [Problema GitHub](https://www.panini.it)_

### Carrello e pagamento, sicurezza

#### [CLOUD] Recupero del file 404 per JS alla pagina di estrazione al primo tentativo dopo l&#39;implementazione della patch SRI

Prima di correggere i mixin, non venivano caricati nel carrello e prelevati quando erano abilitati i comandi di minimizzazione e raggruppamento. Dopo la correzione, tutti i mixin devono essere caricati come previsto.

_ACP2E-4128 - [Problema GitHub](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

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

#### Errore di ambito nella risorsa URL del catalogo (_getCategories)

Questa PR aggiunge un fallback all’ambito predefinito se non è definito alcun valore nell’ambito di archiviazione nella risorsa URL della categoria.

_AC-11011 - [Problema GitHub](https://github.com/magento/magento2/issues/38393) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Verifica se OpenGraph può mostrare il prezzo

Il sistema funziona correttamente quando usiamo il plugin che nasconde il prezzo e con questo cambiamento di prezzo non è visibile nel tag OG.

_AC-11635 - [Problema GitHub](https://github.com/magento/magento2/issues/38512) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38510)_

#### Problema di arrotondamento dei prezzi quando si aggiungono imposte per visualizzare i prezzi

Il sistema ora risolve il problema dell&#39;arrotondamento dei prezzi quando si aggiungono imposte per visualizzare i prezzi

_AC-11725 - [Problema GitHub](https://github.com/magento/magento2/issues/18025) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35730)_

#### [Problema] Consenti condizioni regola catalogo personalizzate

È stato risolto un problema che impediva l’utilizzo delle condizioni delle regole di catalogo personalizzate a causa di un controllo rigoroso dei tipi. La correzione sostituisce la verifica dell’uguaglianza delle classi con l’istanza di, consentendo il corretto funzionamento delle classi di condizioni personalizzate e la corretta convalida e indicizzazione delle regole.

_AC-13338 - [Problema GitHub](https://github.com/magento/magento2/issues/39339) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Opzioni di perdita del prodotto configurabili quando aggiunti alla lista dei desideri

È stato risolto un problema che causava la perdita delle opzioni di prodotto configurabili dopo l’aggiunta del prodotto alla lista dei desideri. Ora, le opzioni selezionate vengono mantenute, consentendo l’aggiunta del prodotto al carrello senza richiedere agli utenti di riselezionare le opzioni.

_AC-13373 - [Problema GitHub](https://github.com/magento/magento2/issues/39363) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Il prezzo speciale non viene visualizzato correttamente per il prodotto secondario del prodotto configurabile (prodotto semplice)

È stato risolto un problema che impediva la corretta visualizzazione del prezzo speciale per il prodotto secondario (semplice) di un prodotto configurabile nella pagina di elenco dei prodotti quando &quot;Utilizzato nell’elenco dei prodotti&quot; era impostato su No. Ora il prezzo speciale viene visualizzato correttamente insieme al prezzo regolare, garantendo prezzi coerenti tra i diversi tipi di prodotto.

_AC-13594 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [Bug] REST API: l&#39;aggiornamento dei prezzi speciali non imposta i valori per tutte le visualizzazioni dello store

REST API ora aggiorna i prezzi speciali per tutte le visualizzazioni del negozio in un sito web.
In precedenza, l’aggiornamento dei prezzi speciali tramite API REST interessava solo la visualizzazione dello store specificata, non tutte le visualizzazioni dello store nel sito web.
AC-13671

_AC-13671 - [Problema GitHub](https://github.com/magento/magento2/issues/39521) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problemi relativi all&#39;ambito dei prezzi e config.php

In Magento 2.4.2, la modifica dell’ambito del prezzo tramite config.php non aggiorna correttamente il valore is_global in catalog_eav_attribute per l’attributo del prezzo.
Di conseguenza, i prezzi dei prodotti rimangono globali e non possono essere salvati per sito web, anche quando la definizione del prezzo è impostata su sito web.
La soluzione alternativa richiede l’aggiornamento manuale della colonna is_global nel database, che non è ideale per gli ambienti di produzione.
Questo comportamento è coerente con la progettazione predefinita di Magento, in cui l’ambito del prezzo è Globale o Sito Web, ma non per visualizzazione negozio.

_AC-13857 - [Problema GitHub](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] errore PHP non rilevato

È stato modificato il nome di una variabile di loop per aggiungere correttamente i dati &quot;_cache_instance_product_ids&quot; sul prodotto specificato da utilizzare nelle chiamate successive.

_AC-14159 - [Problema GitHub](https://github.com/magento/magento2/issues/39641) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39642)_

#### La ricerca elastica interferisce con l’ordinamento predefinito dei prodotti (passando dal primo più recente al primo più vecchio)

Il sistema ora ordina I prodotti più recenti nel database (quello con entity_id più alto) vengono visualizzati per primi

_AC-14411 - [Problema GitHub](https://github.com/magento/magento2/issues/31043) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36900)_

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

#### La stringa di query `?p=` negativa causa l&#39;eccezione Elasticsearch

Il sistema ora gestisce il valore negativo ?p= nell’impaginazione Categoria, che attualmente genera un’eccezione ed è considerata una richiesta valida

_AC-15191 - [Problema GitHub](https://github.com/magento/magento2/issues/40079) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40080)_

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

#### Il prezzo del prodotto sbagliato viene visualizzato sul carrello con valute diverse in diverse visualizzazioni del negozio

È stato risolto un problema che causava la visualizzazione di prezzi del prodotto errati nel carrello quando si utilizzavano valute diverse nelle visualizzazioni dei negozi. Dopo la correzione, il carrello ora mostra il prezzo convertito corretto in base alla valuta configurata, garantendo la coerenza tra la pagina del prodotto e il carrello.

_AC-15385 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Visualizzazione del prezzo &quot;As low as&quot; errata per i prodotti configurabili quando FPT è abilitato

Confermato che il prezzo &quot;As low as&quot; errato per i prodotti configurabili quando FPT era abilitato era causato dall&#39;applicazione dell&#39;imposta due volte; la correzione assicura che il calcolo del prezzo finale rispetti la configurazione dell&#39;imposta e ora visualizza il prezzo corretto.

_AC-15718 - [Problema GitHub](https://github.com/magento/magento2/issues/40171) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### La complessità temporale di _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection aumenta con il numero di prodotti nel carrello e gli attributi

Questo PR ottimizzava _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection sostituendo i loop nidificati con un&#39;unione di array (+) e riducendo le chiamate a _setItemAttributeValue, migliorando le prestazioni per i carrelli di prodotti di grandi dimensioni.

_AC-15833 - [Problema GitHub](https://github.com/magento/magento2/issues/40216) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40217)_

#### Interazione bloccata tra la cache della raccolta e la raccolta prodotti configurabili

È stato risolto un problema di caching con le raccolte di prodotti configurabili aggiungendo un controllo di tipo difensivo per garantire che media_gallery_images venga sempre trattato come una raccolta, evitando errori irreversibili causati da dati cache danneggiati.

_AC-16066 - [Problema GitHub](https://github.com/magento/magento2/issues/33965) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La pagina di prodotto contiene un errore a causa di riscritture URL

Ora la pagina di prodotto viene caricata correttamente quando l’URL viene riscritto

_AC-2950 - [Problema GitHub](https://github.com/magento/magento2/issues/35371) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39670)_

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

#### [Mainline] [CLOUD] Il ridimensionamento delle immagini richiede oltre 400 GB di spazio su disco

Dopo la correzione, il comando `catalog:images:resize` utilizzato con il flag `--skip_hidden_images` non genererà cache immagini per i siti Web in cui le immagini non sono presenti.

_ACP2E-3869 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### La generazione dinamica di immagini genera un numero elevato di immagini

Dopo la correzione, le immagini vengono generate solo per i siti web a cui è assegnato il prodotto.

_ACP2E-3927 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### Il CountryID fornito non esiste - Irlanda (IE)

Dopo la correzione, i codici postali irlandesi sono disponibili per cercare le località di prelievo.

_ACP2E-3932 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### L’errore 500 si verifica sul front-end, a causa di una struttura di layout errata memorizzata nella cache

È stato risolto un problema a causa del quale una pagina restituiva un codice di errore 500 a causa di una struttura di layout errata memorizzata nella cache nel layout

_ACP2E-4040 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Rapporto Visualizzazioni prodotto errato: conteggio inferiore rispetto a GA

È stato corretto un bug a causa del quale la tabella report_viewed_product_index non mostrava il numero corretto di visualizzazioni della pagina di prodotto.

_ACP2E-4045 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Errore di convalida per il campo importo sconto regola prezzo catalogo in Aggiornamento pianificato

In precedenza, prima di risolvere questo problema, per l’aggiornamento della pianificazione per la regola del prezzo di catalogo, se l’importo dello sconto è by_fixed allora non è stato convalidato correttamente a causa della regola di convalida dell’intervallo di numeri. Dopo l&#39;applicazione di questa correzione, la convalida funziona correttamente per la regola del prezzo di catalogo a prezzo fisso.

_ACP2E-4054 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### La convalida dell’IVA non riesce a causa del limitatore di aliquota API IVA - attiva una modifica falsa positiva del gruppo di clienti

Ottimizzazione delle richieste allo strumento di convalida IVA Europa, che si traduce in meno errori di &quot;limitatore di velocità&quot;

_ACP2E-4072 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Eliminazione in blocco nell’indicizzatore core che attiva l’errore di dimensione massima del set di scrittura in produzione

Ottimizza la pulizia dell’indice del prodotto della regola del catalogo implementando due strategie di eliminazione in base al volume dei dati.

_ACP2E-4085 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### I prodotti vengono visualizzati come esauriti dopo la disattivazione

Dopo la correzione, i prodotti disabilitati non sono presenti nel widget prodotti.

_ACP2E-4136 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Cloud] errori con voci duplicate (temp_category_descendants_%)

È stato risolto un problema relativo a voci duplicate durante la creazione di aggiornamenti pianificati per gli ambienti con un numero elevato di categorie nidificate

_ACP2E-4159 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Confronta i problemi di mancata corrispondenza del conteggio dei prodotti per diversi store

Il confronto dell&#39;elenco dei prodotti ora funziona correttamente dopo il passaggio a un&#39;altra visualizzazione dello store

_ACP2E-4249 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Nessuna opzione per &quot;usare il valore predefinito&quot; su &quot;Immagini e video&quot; per l’assegnazione del ruolo immagine

Le opzioni &quot;Usa valore predefinito&quot; sono state aggiunte alla sezione delle immagini e dei video del prodotto, consentendo l’ereditarietà delle impostazioni dall’ambito predefinito.

_ACP2E-4280 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Prodotti per categorie con restrizioni ancora conteggiati nella lista dei desideri dopo l’aggiornamento del gruppo di clienti

Prima della correzione, le autorizzazioni per la categoria non venivano applicate correttamente agli elementi della lista dei desideri del cliente. Ora, dopo la correzione, gli elementi della lista dei desideri vengono visualizzati e impaginati correttamente sia nel web che in GraphQL.

_ACP2E-4294 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [Cloud] problema di prezzo del bundle su PDP e PLP

Il prezzo del prodotto in bundle con prezzo regolare viene visualizzato correttamente su PDP/PLP per la valuta non predefinita

_ACP2E-4298 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### Il cliente può ordinare un prodotto inaccessibile dopo la modifica del gruppo di clienti

In precedenza, quando si modificava il gruppo di clienti da amministratore, il catalogo front-end e il carrello non rispecchiavano le modifiche nelle autorizzazioni del catalogo. Tuttavia, dopo aver applicato questa correzione, le virgolette front-end ora cambiano in base alle autorizzazioni del catalogo aggiornate quando il gruppo di clienti viene modificato da admin.

_ACP2E-4300 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Reindicizzazione bloccata a causa di un utilizzo elevato della memoria

È stato risolto il problema che impediva il completamento dell’indicizzatore della regola del catalogo a causa di memoria eccessiva e problemi di instabilità e memoria insufficiente.

_ACP2E-4303 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS] collegamento di anteprima aggiornamento pianificato reindirizza alla pagina Manutenzione

Nell’anteprima degli aggiornamenti pianificati del collegamento alla pagina iniziale con prodotti configurabili viene visualizzato correttamente l’elenco dei prodotti. Precedentemente reindirizzava gli utenti alla pagina Manutenzione

_ACP2E-4401 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Catalogo, GraphQL

#### Calcolo sconto GraphQl non valido

GraphQL ora visualizza correttamente le percentuali di sconto e i prezzi base quando i prezzi del catalogo sono configurati per includere le imposte. In precedenza si verificavano errori di arrotondamento, ad esempio la visualizzazione del 19,99% invece del 20%.

_ACP2E-3993 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Il campo GetCart GraphQL Media Gallery restituisce dati vuoti dopo lo svuotamento della cache

Dopo la correzione, la media_gallery del prodotto viene restituita come previsto nella risposta di GraphQL per la richiesta del carrello.

_ACP2E-4185 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Catalogo, GraphQL, Ricerca

#### La graphql dei prodotti restituiva categorie disabilitate nelle aggregazioni di categorie

Dopo la correzione, le categorie disabilitate non vengono restituite per la richiesta GraphQl dei prodotti.

_ACP2E-2885 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogo, Prestazioni

#### Le categorie in amministrazione si caricano molto lentamente

Le prestazioni di caricamento delle categorie sono notevolmente migliorate. In precedenza, il caricamento della categoria che causava un problema di timeout richiedeva così tanto tempo.

_ACP2E-3891 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogo, prezzi

#### Sconto regola prezzo catalogo non valido applicato al prodotto figlio

Risolve il problema per cui la regola del prezzo di catalogo per la variante viene sostituita dal prodotto configurabile principale, nel caso in cui entrambe le regole abbiano la stessa priorità.

_ACP2E-3693 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Problema di prezzo del prodotto del bundle Cloud]

Il prezzo del prodotto in bundle con prezzo speciale viene visualizzato correttamente su PDP/PLP per la valuta non predefinita

_ACP2E-4110 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6e134409)_

### Catalogo, prodotto

#### [Errore casuale] libreria Fotorama non caricata

Il sistema ora assicura che la libreria Fotorama sia caricata correttamente, consentendo la visualizzazione di tutte le immagini allegate nella galleria immagini come previsto. In precedenza, solo la prima immagine era visibile a causa di un problema con la libreria Fotorama che non veniva caricata correttamente.

_AC-12124 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### Il collegamento &quot;Aggiungi prodotti manualmente&quot; deve essere sempre visibile

È stato risolto un problema che impediva la visualizzazione del collegamento &quot;Aggiungi prodotti manualmente&quot; durante la creazione di un prodotto configurabile senza configurazioni esistenti. Il collegamento ora viene sempre visualizzato, consentendo agli amministratori di associare facilmente prodotti semplici senza creare configurazioni fittizie.

_AC-13866 - [Problema GitHub](https://github.com/magento/magento2/issues/39595) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Modifica di un prodotto nel backend Rimuove cifre decimali aggiuntive dal prezzo delle opzioni di prodotto

È stato risolto un problema che causava il troncamento del prezzo delle opzioni di prodotto con due cifre decimali in seguito alla modifica di un prodotto nell’amministratore. Il sistema mantiene ora i prezzi con una precisione decimale più elevata, assicurando la conservazione dei valori accurati dopo il salvataggio.

_AC-14050 - [Problema GitHub](https://github.com/magento/magento2/issues/39655) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

### Catalogo, Ricerca

#### La richiesta RestApi &#39;/rest/default/V1/Categories?searchCriteria%5Bpage_size%5D=1&#39; non riesce e viene restituito un errore di timeout

Le richieste API REST di categoria non hanno più esito negativo con errori di timeout.
In precedenza, le richieste a /rest/default/V1/Categories?searchCriteria[page_size]=1 potevano non riuscire e dopo alcune modifiche al codice si verificava un timeout.
AC-13358

_AC-13358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenuto

#### graphql (magento 2.4.6-p4 ): errore durante il tentativo di ottenere la pagina cms con stato non attivo

È stato risolto un problema a causa del quale la query GraphQL per una pagina CMS disabilitata restituiva un errore interno del server.
Ora la query recupera una risposta corretta senza errori.

_AC-12302 - [Problema GitHub](https://github.com/magento/magento2/issues/38877) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Il modulo di condivisione della lista dei desideri consente il codice casuale nei campi del nome

È stata risolta una vulnerabilità critica SSTI (Server-Side Template Injection) nel modulo di condivisione della lista dei desideri, a causa della quale poteva essere inserito del codice dannoso nel campo del messaggio e inviato tramite e-mail. L’aggiornamento aggiunge la convalida dell’input alle direttive dei modelli di blocco e ai modelli non sicuri, mostrando ora un messaggio di errore quando viene rilevato contenuto non valido.

_AC-12730 - [Problema GitHub](https://github.com/magento/magento2/issues/39024) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### L’inserimento di csp_whitelist.xml nel tema non funziona e crea un problema intermittente

È stato implementato il caching della whitelist CSP per area del sito web.

_AC-13069 - [Problema GitHub](https://github.com/magento/magento2/issues/38933) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39672)_

#### Dopo l&#39;aggiornamento a Magento 2.4.7 p2 non può vedere i file appena caricati galleria multimediale

I nuovi file caricati vengono ora visualizzati in Media Gallery dopo l’aggiornamento.
In precedenza, dopo l’aggiornamento a Magento 2.4.7 p2, le immagini appena caricate non venivano visualizzate in Media Gallery fino a quando non veniva eseguita una sincronizzazione manuale.
AC-13262

_AC-13262 - [Problema GitHub](https://github.com/magento/magento2/issues/39275)_

#### In Media Gallery vengono visualizzate immagini non corrette provenienti da directory con nomi identici ma con maiuscole e minuscole diverse

Il sistema ora risolve un problema in cui i file caricati in una directory specifica in Media Gallery sono visibili anche in directory con nomi simili ma con maiuscole e minuscole diverse.

_AC-13489 - [Problema GitHub](https://github.com/magento/magento2/issues/39382) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39502)_

#### Se si rimuove completamente un&#39;immagine della galleria da be, vengono impostati i ruoli/tipi dell&#39;ambito (base/piccola/miniatura) e dopo la nuova aggiunta vengono visualizzati i ruoli/tipi &quot;vecchi&quot;

Il sistema funziona come previsto negli ambiti di archiviazione. Le immagini ereditano i ruoli o i tipi della nuova immagine aggiunta in base all’ambito predefinito

_AC-13556 - [Problema GitHub](https://github.com/magento/magento2/issues/39481) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Piccolo bug] Il filtro del pannello di amministrazione `listing component` non può essere attivato se il valore del campo contiene `\`

Il sistema funziona correttamente quando si filtra il titolo della pagina con una barra (esempio: Magento\Store)

_AC-13661 - [Problema GitHub](https://github.com/magento/magento2/issues/39513) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39535)_

#### Errore: errore di script per &quot;Magento_Catalog/js/validate-product&quot; per admin content pagebuilder with products load

Questa PR corregge l’errore Script per catalogAddToCart quando si modifica il generatore di pagine con la condizione &quot;products&quot;

_AC-13891 - [Problema GitHub](https://github.com/magento/magento2/issues/39604) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39677)_

#### Errore catalogAddToCart Script durante la configurazione del widget prodotto.

È stato corretto un errore di script che si verificava durante la configurazione del widget Prodotti con &quot;Combinazione condizioni&quot; in Page Builder. Il problema è stato causato dalla mancanza di file JS front-end, con conseguenti errori della console. Dopo la correzione, il widget viene caricato correttamente senza errori della console.

_AC-13892 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Blocca la selezione in widget che hanno lo stesso identificatore

Il sistema ora gestisce correttamente la selezione del blocco durante la creazione di widget quando sono presenti gli stessi blocchi di identificatore

_AC-14132 - [Problema GitHub](https://github.com/magento/magento2/issues/39692) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39722)_

#### &quot;La pagina CMS con ID &quot;0&quot; non esiste&quot; flusso di registro

Il sistema funziona come previsto dopo la creazione dell’utente amministratore e quando si crea una nuova pagina system.log non contiene messaggi di errore

_AC-14254 - [Problema GitHub](https://github.com/magento/magento2/issues/39743) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] Ciclo infinito query route

Questo ticket ha risolto il problema che causava un loop infinito e alla fine un timeout in seguito a una query di instradamento di GraphQL con percorso di richiesta e percorso di destinazione identici.
In 2.4.9-alpha3, la query ora restituisce la risposta di errore corretta invece di eseguire un ciclo.

_AC-14269 - [Problema GitHub](https://github.com/magento/magento2/issues/39707) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### La mappa del sito inesistente risponde con l’immagine del prodotto

Il sistema ora corregge quando si accede a sitemap inesistente risponde con l&#39;immagine del prodotto con la risposta: 404 NOT FOUND

_AC-14295 - [Problema GitHub](https://github.com/magento/magento2/issues/39756) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40135)_

#### I widget per collegamenti catalogo utilizzano un URL errato

Il sistema ora gestisce correttamente i widget dopo l’aggiunta del collegamento di prodotto catalogo e del collegamento di categoria catalogo e mostra anche gli URL corretti nell’origine HTML

_AC-14437 - [Problema GitHub](https://github.com/magento/magento2/issues/39464) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39710)_

#### Prefisso tabella non preso in considerazione

Adobe Commerce ora rispetta correttamente i prefissi della tabella del database durante il caricamento della griglia del tema Struttura > Configurazione in Admin. In precedenza, in Adobe Commerce 2.4.8 con un prefisso di tabella configurato in app/etc/env.php, lo spostamento a Contenuto > Progettazione > Configurazione causava un errore perché il prefisso della tabella non veniva preso in considerazione e la griglia di temi non veniva riprodotta.

_AC-14556 - [Problema GitHub](https://github.com/magento/magento2/issues/39847) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Cambia la costante IMAGE_FILE_NAME_PATTERN in public visible, per una maggiore flessibilità

La costante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php è stata resa pubblica per consentire agli sviluppatori una maggiore flessibilità quando si lavora con le rappresentazioni delle immagini. La correzione è inclusa in Magento 2.4.9-alpha3 con copertura completa di unit test e integration test.

_AC-15338 - [Problema GitHub](https://github.com/magento/magento2/issues/39733) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Il metodo di spedizione non corretto viene visualizzato nella pagina dell&#39;ordine di revisione per spedizioni multiple

È stato risolto un problema relativo al pagamento di più spedizioni a causa del quale nella pagina dell&#39;ordine di revisione venivano visualizzate spese di spedizione non corrette (5 INR invece di 10 INR). L&#39;aggiornamento garantisce che per ogni indirizzo venga visualizzato l&#39;importo di spedizione corretto.

_AC-15664 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### la configurazione bin/magento :show(o set) design/theme/theme_id non riesce

È stato risolto un problema che causava l&#39;errore dei comandi CLI bin/magento config:show e config:set per il percorso design/theme/theme_id nonostante la configurazione fosse presente.
Ora, i comandi vengono eseguiti correttamente e consentono la visualizzazione e l’impostazione dell’ID tema senza errori.

_AC-5915 - [Problema GitHub](https://github.com/magento/magento2/issues/35751) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Impossibile caricare l’immagine con larghezza relativamente piccola

Il sistema non è più in grado di ridimensionare l&#39;immagine con una larghezza relativamente ridotta rispetto all&#39;altezza.

_ACP2E-3558 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Il componente Prodotto di Page Builder non funziona se l’utente non dispone dell’autorizzazione Widget

Prima della correzione, quando si accedeva a un widget senza autorizzazioni, la pagina generava un errore generico e mostrava un GIF di &quot;caricamento&quot;. Ora, dopo la correzione, viene visualizzata una finestra modale con &quot;Spiacenti, sono necessarie le autorizzazioni per visualizzare questo contenuto&quot;. messaggio.

_ACP2E-3664 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Percorso di configurazione errato per la configurazione dello stile del percorso di archiviazione remota

Dopo la correzione, l’impostazione della configurazione dello stile del percorso di archiviazione remota influirà sulla configurazione effettiva dello stile del percorso AWS S3.

_ACP2E-3734 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### L’ordine del widget di prodotto di Page Builder non viene applicato in GraphQL

È stato risolto il problema che impediva alla risposta della query &quot;route&quot; di GraphQL di restituire i prodotti nell&#39;ordinamento corretto all&#39;interno di un tipo di contenuto Prodotti Page Builder.

_ACP2E-3898 - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema di visualizzazione dei prezzi su vetrine non inglesi a causa della versione della libreria ICU

Dopo la correzione, il prezzo del prodotto viene visualizzato correttamente nella lingua ebraica (Israele).

_ACP2E-3938 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Aggiornamento della configurazione della progettazione annullata del codice dell&#39;archivio

È stato risolto il problema che causava la cancellazione delle impostazioni di Configurazione della progettazione da parte dell&#39;aggiornamento del codice della vista archivio a causa di un aggiornamento non corretto della cache di configurazione.

_ACP2E-3941 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Problema di logica della condizione di prodotto (la logica OR si comporta in modo errato nel mostrare meno prodotti)

Il widget Prodotti Page Builder ora restituisce il risultato corretto quando si utilizza un attributo con ambito globale nella condizione &quot;Corrispondenza con qualsiasi&quot;

_ACP2E-4096 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Il carosello di prodotti aggiunge prodotti non corretti a Page Builder

Prima della correzione, un prodotto configurabile sarebbe stato incluso automaticamente negli elenchi a carosello dei prodotti PageBuilder se uno qualsiasi dei suoi figli avesse soddisfatto le condizioni di filtro. Ora, dopo la correzione, il prodotto principale verrà incluso solo se il prodotto secondario non è visibile da solo.

_ACP2E-4341 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Il widget Elenco prodotti restituisce un risultato errato se più categorie sono elencate nella condizione della categoria

Il widget &quot;Elenco prodotti catalogo&quot; ora visualizza risultati precisi quando più categorie elencate nella condizione &quot;La categoria è una di&quot;. In precedenza, veniva elaborata solo la prima categoria dell’elenco.

_ACP2E-4353 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032) - [Contributo codice GitHub](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### La creazione della cartella di [Cloud] Media Gallery richiede l&#39;autorizzazione delete_folder in New Media Gallery. I ruoli con solo create_folder non possono creare cartelle

In precedenza, prima dell’implementazione di questa correzione, un utente amministratore con l’autorizzazione per la creazione di una cartella solo per il contenuto non poteva creare una cartella nella raccolta multimediale di CMS. Tuttavia, dopo la correzione, i creatori di contenuto nella raccolta multimediale ora possono creare cartelle solo con l’autorizzazione di creazione cartella.

_ACP2E-4376 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] Duplicazione di una pagina CMS

Prima di questa correzione, la duplicazione di una pagina cms con aggiornamento del layout personalizzato non sarebbe riuscita. Ora le pagine CMS con aggiornamenti di layout personalizzati possono essere duplicate senza errori.

_ACP2E-4449 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Cliente/clienti

#### Eccezione in Storefront quando l’amministratore aggiunge il blocco CustomerCustomAttribute tramite CMS Page Content

È stato risolto un problema a causa del quale l’aggiunta del blocco CustomerCustomAttribute tramite il contenuto della pagina CMS causava un’eccezione storefront e impediva il caricamento della pagina.
Storefront ora viene visualizzato normalmente e mostra un messaggio significativo quando non è possibile eseguire il rendering del contenuto, evitando errori critici.

_AC-11004_

#### La Griglia Di Amministrazione Dei Clienti Ora Online Mostra Righe Duplicate Ogni Volta Che Un Utente Accede, Esci E Poi Entra

È stato risolto un problema che causava la visualizzazione di righe duplicate da parte della griglia di amministrazione Clienti online alla disconnessione e all&#39;accesso di un cliente.
La griglia ora aggiorna il record esistente con l’attività più recente invece di creare voci duplicate, garantendo un tracciamento accurato delle sessioni dei clienti.

_AC-11511 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/528af81a)_

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

#### Completamento del codice del modulo disabilitato.

Questo escape di richiesta pull ha disabilitato i moduli prima della compilazione del codice.

_AC-10933 - [Problema GitHub](https://github.com/magento/magento2/issues/38241) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39723)_

#### Errore durante l&#39;esecuzione del comando setup:upgrade con il trigger del database personalizzato

I trigger di database personalizzati non causano più errori durante l&#39;installazione:upgrade.
In precedenza, l&#39;esecuzione dell&#39;installazione di bin/magento:upgrade con un trigger di database personalizzato (ad esempio, AFTER INSERT nella tabella dell&#39;archivio) poteva causare l&#39;errore:
&quot;Avvertenza: tentativo di accedere all’offset dell’array sul valore di tipo null in vendor/magento/framework/Mview/View/Subscription.php alla riga 357&quot;
AC-11487

_AC-11487 - [Problema GitHub](https://github.com/magento/magento2/issues/38481)_

#### [Problema] Rendere la firma del metodo coerente con l&#39;interfaccia

La firma del metodo per getAttributes è ora coerente con la relativa interfaccia, evitando errori durante la sovrascrittura del metodo. In precedenza, le incoerenze nella firma del metodo causavano errori quando si tentava di sovrascrivere il metodo getAttributes.

_AC-11578 - [Problema GitHub](https://github.com/magento/magento2/issues/38501) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31955)_

#### Il modulo di entità sito web/gruppo/archivio non può essere esteso con più elementi di modulo valore per gli attributi di estensione

Questa PR consente agli elementi modulo multivalore di inviare dati a un modulo sito Web/gruppo/archivio.

_AC-11657 - [Problema GitHub](https://github.com/magento/magento2/issues/24070) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema]: è stata corretta la regola di convalida delle e-mail per il componente dell&#39;interfaccia utente

Il sistema ora convalida correttamente più indirizzi e-mail immessi nei componenti dell’interfaccia utente, garantendo che ogni e-mail sia tagliata e convalidata correttamente. In precedenza, il sistema utilizzava un metodo errato per tagliare gli indirizzi e-mail, il che poteva causare errori di convalida.

_AC-11719 - [Problema GitHub](https://github.com/magento/magento2/issues/38528) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema] Rimuovi utilizzo del risolutore ambito

Questa PR risolve le impostazioni URL amministratore a livello globale invece che nell’archivio corrente

_AC-11736 - [Problema GitHub](https://github.com/magento/magento2/issues/38566) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38554)_

#### [Problema] Rimuovere i metodi ridondanti

Qualità del codice: sono stati rimossi i metodi ridondanti nei componenti AsynchronousOperations e Sales che chiamavano solo i metodi padre senza aggiungere funzionalità, migliorando la manutenibilità del codice.

_AC-11915 - [Problema GitHub](https://github.com/magento/magento2/issues/29748) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/29147)_

#### Modello titolo_tema Magento.phtml non valido per PHP 8.2

Questa richiesta di pull risolve un problema quando una pagina CMS creata con l’intestazione null come nel Php 8.x passando null a trim() genera un’eccezione: Funzionalità obsolete: trim(): passaggio null al parametro #1 ($string) di tipo stringa

_AC-12856 - [Problema GitHub](https://github.com/magento/magento2/issues/39092) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39398)_

#### la convalida xsd non riesce nei file etc/adminhtml/system.xml che contengono commenti sotto gli elementi dei campi.

Questa PR corregge le definizioni dello schema XML in phpstorm per il nodo dei commenti

_AC-12945 - [Problema GitHub](https://github.com/magento/magento2/issues/39148) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39867)_

#### Esposizione della versione di Magento tramite route di installazione con configurazione Nginx predefinita

Il sistema ora funziona come previsto e non espone la versione esatta di Magento in esecuzione sul sito

_AC-13205 - [Problema GitHub](https://github.com/magento/magento2/issues/39227) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] decomprimi gli argomenti dell&#39;oggetto come parametri denominati

Il sistema ora utilizza la funzione PHP 8.1 di decompressione dell&#39;array con parametri denominati, che elimina la necessità di chiamate array_values e potenzialmente migliora le prestazioni complessive. In precedenza, il sistema richiedeva array_values per decomprimere gli argomenti dell&#39;oggetto.

_AC-13210 - [Problema GitHub](https://github.com/magento/magento2/issues/39233) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37411)_

#### [Problema] refactoring dell&#39;indirizzo dell&#39;offerta per convalidare il metodo

Questa PR include miglioramenti di leggibilità al metodo doValidate.

_AC-13214 - [Problema GitHub](https://github.com/magento/magento2/issues/38230) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38219)_

#### opzione Magento: magento-init-params non viene mai utilizzato quando si esegue cli?

L&#39;opzione —magento-init-params viene ora utilizzata quando si eseguono comandi CLI.
In precedenza, il passaggio di —magento-init-params ai comandi CLI non aveva alcun effetto su parametri come MAGE_MODE.
AC-13231

_AC-13231 - [Problema GitHub](https://github.com/magento/magento2/issues/39248) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### dichiarazione di tipo getItemsByColumnValue errata

Il sistema ora definisce correttamente il parametro di input $value come tipo primitivo, non come array, nella funzione getItemsByColumnValue, assicurandosi che la funzione restituisca l&#39;insieme previsto. In precedenza, se come parametro di input veniva utilizzato un array con un singolo valore, la funzione restituiva null e gli IDE la contrassegnavano come errore.

_AC-13240 - [Problema GitHub](https://github.com/magento/magento2/issues/33070) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33120)_

#### Quando si utilizza lo storage dei file per il provider di blocchi, viene creata una directory di file in continua crescita senza alcuna pulizia

Questa richiesta di pull introduce un nuovo cronjob che viene eseguito una volta al giorno e cerca i file di blocco che non sono stati modificati nelle ultime 24 ore e che possono quindi essere rimossi in modo sicuro. In questo modo il contenuto della directory dei file di blocco sarà controllato.
Questo processo cronologico eseguirà un elemento solo quando il provider di blocchi è configurato per l’utilizzo di file, non quando viene utilizzato uno degli altri (database: impostazione predefinita, zookeeper o cache)

_AC-13367 - [Problema GitHub](https://github.com/magento/magento2/issues/39369) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39372)_

#### [Problema] Pulizia: non utilizzare un valore restituito void dalle chiamate di metodo.

Questa PR esegue una pulizia di minore entità. A volte chiamavamo metodi che non restituivano nulla (void) e utilizzavano quel valore di risultato. Che in realtà non è necessario.

_AC-13664 - [Problema GitHub](https://github.com/magento/magento2/issues/39524) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39516)_

#### Cache Keys associata a FPC nelle implementazioni multi-store di Magento 2.4.7

È stato risolto un problema a causa del quale le chiavi della cache FPC (Full Page Cache) nelle impostazioni multi-store non includevano MAGE_RUN_CODE e MAGE_RUN_TYPE, causando un comportamento incoerente delle chiavi della cache rispetto alle versioni precedenti. Le chiavi della cache ora includono correttamente il contesto dell’archivio, garantendo il corretto isolamento della cache tra gli archivi.

_AC-13719 - [Problema GitHub](https://github.com/magento/magento2/issues/39456) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] [PHPDOC] Correzione di phpdoc non valido per Magento\Framework\Message\ManagerInterface

Questa PR corregge il phpdoc danneggiato per \Magento\Framework\Message\ManagerInterface e rimuove tutti i phpdoc duplicati in \Magento\Framework\Message\Manager (utilizzare la sintassi inheritdoc).

_AC-14312 - [Problema GitHub](https://github.com/magento/magento2/issues/39593) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39153)_

#### L’indicizzazione parziale smette di funzionare per i clienti con un numero enorme di aggiornamenti

L’indicizzazione parziale ora funziona per i clienti con un numero elevato di aggiornamenti.
In precedenza, il raggiungimento del valore massimo per la colonna version_id nella tabella del registro delle modifiche causava l&#39;arresto degli aggiornamenti dell&#39;indice.
AC-14424

_AC-14424 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 utilizza pacchetti di sviluppo che non seguono il controllo delle versioni semantiche

Magento 2.4.8 richiede versioni di sviluppo di pdependent/pdependent e phpmd/phpmd (3.x-dev) per la compatibilità con PHP 8.4.
Queste versioni di sviluppo sono in conflitto con gli strumenti di terze parti che si aspettano pacchetti compatibili con SemVer, impedendo alcuni aggiornamenti.
Una soluzione alternativa temporanea consiste nell’assegnare un alias alle versioni di sviluppo in compositore.json (ad esempio, &quot;3.x-dev as 3.99.0&quot;), consentendo la compatibilità e soddisfacendo al contempo il controllo delle versioni semantiche.
Questo assicura il supporto di PHP 8.4 ed evita conflitti fino a quando non saranno disponibili versioni stabili.

_AC-14519 - [Problema GitHub](https://github.com/magento/magento2/issues/39796)_

#### Il meccanismo MView ignora automaticamente gli errori durante l’esecuzione del trigger

Il meccanismo MView ora segnala correttamente gli errori durante l’esecuzione del trigger.
In precedenza, gli errori durante l’esecuzione del trigger venivano ignorati automaticamente, il che poteva causare aggiornamenti dell’indice mancanti senza alcuna notifica.
AC-14567

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

#### [Problema] Includi il costruttore come parte dell&#39;API `CommandListInterface`, estendi la documentazione in linea

Questo aggiornamento PR contrassegna Magento\Framework\Console\CommandList come API e introduce il costruttore a CommandListInterface per una migliore estensibilità. Inoltre, migliora la documentazione in linea per migliorare la chiarezza e la gestibilità per gli sviluppatori che estendono i comandi della console.

_AC-14680 - [Problema GitHub](https://github.com/magento/magento2/issues/31102) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37901)_

#### [Problema] Rimuovi il codice relativo a Microsoft IIS

Questa PR consente di eliminare il codice relativo a Microsoft IIS in base alla documentazione sui requisiti di sistema di Magento, in cui si specifica che il sistema operativo Microsoft Windows non è supportato

_AC-14702 - [Problema GitHub](https://github.com/magento/magento2/issues/39910) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39894)_

#### Errore di sintassi Magnifier.js

La funzionalità Lente di ingrandimento del sistema deve continuare a funzionare nel modo in cui funzionava in precedenza e le opzioni Lente di ingrandimento non devono essere disponibili in ambito globale

_AC-14722 - [Problema GitHub](https://github.com/magento/magento2/issues/36200) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modalità dettagliata backport nel comando CLI `setup:db:status`

Il comando CLI `setup:db:status` ora supporta la modalità dettagliata.
In precedenza, era difficile comprendere le modifiche al database richieste per gli aggiornamenti. L&#39;esecuzione di `bin/magento setup:db:status -v` fornisce informazioni dettagliate sulle differenze di schema e dati.
AC-14807

_AC-14807 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Invio di posta SMTP con tls e 2.4.8

L’invio di e-mail SMTP con TLS ora funziona come previsto.
In precedenza, l&#39;invio di e-mail tramite SMTP con TLS causava l&#39;errore: errore:1408F10B:Routine SSL:ssl3_get_record:numero di versione errato.
AC-14883

_AC-14883 - [Problema GitHub](https://github.com/magento/magento2/issues/39947) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema] è stato risolto un problema di concorrenza nella distribuzione di contenuto statico

Questa PR risolve un bug in cui più processi simultanei si attivano per gestire lo stesso pacchetto di temi, a seconda di come i temi vengono definiti con i loro genitori.

_AC-14944 - [Problema GitHub](https://github.com/magento/magento2/issues/39990) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Rimuovere il codice di compatibilità legacy per le versioni PHP &lt; 8.1

Questa richiesta di pull rimuove il codice progettato per essere eseguito su PHP &lt;8.1.
Inoltre, i controlli rimossi per la disponibilità del contatto PHP_VERSION_ID, poiché è disponibile in tutte le versioni PHP

_AC-14971 - [Problema GitHub](https://github.com/magento/magento2/issues/39891) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC non funziona all&#39;accesso

La cache a pagina intera (FPC) ora funziona correttamente per i clienti connessi.
In precedenza, dopo l’accesso, la home page non veniva caricata dalla cache e l’intestazione x-magento-cache-debug mostrava MISS invece di HIT.
AC-14999

_AC-14999 - [Problema GitHub](https://github.com/magento/magento2/issues/40007)_

#### Aggiungere tipi generici in alcune classi php per migliorare il supporto dell&#39;analisi statica

Il sistema ora utilizza una definizione di tipo generica per migliorare questo aspetto in modo significativo, facendola interpretare come la classe esatta restituita dalla chiamata di un metodo

_AC-15013 - [Problema GitHub](https://github.com/magento/magento2/issues/40017) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40119)_

#### [Problema] migliorare la gestione degli errori SchemaBuilder

Questa PR migliora la gestione dei messaggi di errore dello schema del database. Ci aiuta a identificare il problema senza dover eseguire pesanti operazioni di debug.

_AC-15020 - [Problema GitHub](https://github.com/magento/magento2/issues/39816) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39799)_

#### API REST: chiamata a una funzione membro getVideoProvider() su null

È stato risolto un problema a causa del quale la chiamata all’API figlio del prodotto configurabile restituiva un errore interno del server 500 se un prodotto figlio aveva solo un video YouTube e nessun’altra immagine.
L&#39;errore è stato causato da un riferimento null in ExternalVideoEntryConverter.
Ora, l’API restituisce correttamente i prodotti secondari con voci della galleria di contenuti multimediali, inclusi i dati video esterni, senza generare errori.
Questo garantisce il corretto recupero di tutti i tipi di file multimediali per i prodotti secondari tramite API REST.

_AC-15046 - [Problema GitHub](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Rimuovi testo/javascript dalla dichiarazione tag dello script del cookie

Questa PR rimuoveva l’attributo non necessario type=&quot;text/javascript&quot; dal tag script del cookie per conformità a HTML5.

_AC-15061 - [Problema GitHub](https://github.com/magento/magento2/issues/39982) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39983)_

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

#### Tipi restituiti non chiari/non validi in Magento\Framework\Escaper

Il sistema accetta i tipi per i metodi di escape Quando si esegue l&#39;analisi statica utilizzando phpstan al livello 5

_AC-15272 - [Problema GitHub](https://github.com/magento/magento2/issues/40012) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40114)_

#### [Problema] Consenti alla configurazione specifica della coda di superare il valore massimo predefinito per i messaggi

Il sistema ora consente alla configurazione specifica della coda di superare il valore massimo predefinito per i messaggi

_AC-15284 - [Problema GitHub](https://github.com/magento/magento2/issues/40121) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40110)_

#### [Problema] Copia cache fpc duplicata per la stessa pagina con la stessa query quando si utilizza la vernice

Questa PR corregge le voci duplicate della cache a pagina intera quando si utilizza Varish normalizzando l’ordine dei parametri di query, garantendo chiavi di cache coerenti per richieste identiche.
Migliora il rapporto di hit della cache e le prestazioni per gli URL con gli stessi parametri in sequenze diverse.

_AC-15325 - [Problema GitHub](https://github.com/magento/magento2/issues/39706) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39704)_

#### I temi community contengono risorse per i moduli dell’edizione di Commerce

Sono state rimosse le risorse di stile solo per Commerce dai temi della community spostandole nelle rispettive directory dei moduli. In questo modo si evita che i file CSS non utilizzati vengano inclusi in Community Edition, riducendo il payload non necessario ed eliminando le regole di stile obsolete e garantendo al contempo uno stile corretto quando i moduli Commerce sono abilitati.

_AC-15347 - [Problema GitHub](https://github.com/magento/magento2/issues/21446) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Problema] L&#39;aggiunta di codice archivio agli URL deve essere globale

Questa PR risolve il problema assicurandosi che l’impostazione &quot;Aggiungi codice store agli URL&quot; sia recuperata utilizzando l’ambito globale nel codice core

_AC-15365 - [Problema GitHub](https://github.com/magento/magento2/issues/40069) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40065)_

#### [Problema] registra il plug-in non dichiarato solo se non è disabilitato

Questa PR corregge e registra il plug-in che non è dichiarato e non è utilizzato (istanza abilitata e mancante).

_AC-15386 - [Problema GitHub](https://github.com/magento/magento2/issues/40086) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40081)_

#### [Problema] Pulizia ridotta, chiavi duplicate rimosse dall&#39;array

Il sistema ora ha eseguito una piccola pulizia e non è stato trovato alcun errore relativo all&#39;array con 2 chiavi duplicate con il valore &quot;Peso (e superiore)&quot;

_AC-15414 - [Problema GitHub](https://github.com/magento/magento2/issues/39851) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework versione 103.0.8-p2: classe EmailMessage che chiama un metodo inesistente

La classe EmailMessage ora gestisce correttamente il recupero del corpo dell&#39;e-mail.
In precedenza, in Magento 2.4.8-p2 con magento/framework versione 103.0.8-p2, la classe Magento\Framework\Mail\EmailMessage tentava di chiamare un metodo inesistente (getTextBody) sull’oggetto messaggio di posta Symfony. Ciò causava errori quando moduli o personalizzazioni di terze parti utilizzavano questo metodo per l’elaborazione delle e-mail.
Ora la classe EmailMessage non chiama più metodi non definiti, impedendo questi errori. AC-15446

_AC-15446 - [Problema GitHub](https://github.com/magento/magento2/issues/40170) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [I Data/Schema Patches getAliases() di Magento 2.3.x] causano errori durante `setup:upgrade`

getAliases() causa errori durante l&#39;installazione:upgrade. Questa PR corregge lo stesso

_AC-15559 - [Problema GitHub](https://github.com/magento/magento2/issues/31396) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38239)_

#### Combinazione di regole di confronto non valida per l&#39;operazione

_AC-15614 - [Problema GitHub](https://github.com/magento/magento2/issues/40138) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### [Problema] [PHPDOC] Correzione di phpdoc non valido Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Questa PR aggiorna il PHPDoc per \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() per riflettere correttamente che il parametro $alias può essere null oltre alla stringa. Questo risolve i problemi di PHPStan al livello 5+ e migliora la compatibilità degli strumenti di qualità del codice.

_AC-15626 - [Problema GitHub](https://github.com/magento/magento2/issues/39598) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39581)_

#### Combinazione non valida di regole di confronto nel modulo urlrewrite

_AC-15647 - [Problema GitHub](https://github.com/magento/magento2/issues/40189) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### Condizione non soddisfatta in `\Magento\Framework\Escaper::escapeScriptIdentifiers`

È stata corretta una condizione non raggiungibile in \Magento\Framework\Escaper::escapeScriptIdentifiers sostituendo il controllo false con null, allineandolo ai valori restituiti preg_replace e migliorando la precisione del codice senza influire sulla funzionalità.

_AC-15667 - [Problema GitHub](https://github.com/magento/magento2/issues/40195) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Vernice 7.3 (versione più recente) - I collegamenti/le opzioni delle sottocategorie della categoria predefinita non vengono visualizzati nella home page del Negozio

Confermato che i collegamenti di sottocategoria mancanti sulla home page della vetrina quando si utilizza Varnish 7.3 erano dovuti alla gestione delle richieste ESI e alla configurazione del server, piuttosto che a un difetto del codice Magento; il problema viene risolto tramite le correzioni di configurazione di Varnish consigliate, senza la necessità di modifiche al codice di base.

_AC-15674 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3cf1a106) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problema] Aggiungi dati di debug aggiuntivi al registro `cache_invalidate`

Questa PR ha migliorato il registro cache_invalidate per includere il contesto della richiesta e la traccia dello stack per le eliminazioni complete della cache, migliorando il debug e la visibilità.
Questo consente di identificare l’origine di invalidamenti imprevisti della cache completa senza modificare le funzionalità esistenti.

_AC-15719 - [Problema GitHub](https://github.com/magento/magento2/issues/40204) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40196)_

#### [Problema] L&#39;elenco di esclusione del caricatore automatico del compositore è stato migliorato un po&#39;.

Questa PR perfeziona le esclusioni del caricatore automatico del Compositore per saltare le classi di test, riducendo le voci di classmap non necessarie e impedendo gli avvisi PSR-4.

_AC-15743 - [Problema GitHub](https://github.com/magento/magento2/issues/40109) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40107)_

#### [Problema] Impedisce a `db_schema.xml` dichiarazioni con `comment=""` di interrompere zero distribuzioni di downtime

Il sistema ora impedisce che le dichiarazioni db_schema.xml con comment=&quot;&quot; interrompano zero implementazioni di downtime

_AC-15980 - [Problema GitHub](https://github.com/magento/magento2/issues/40254) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40242)_

#### Impossibile cancellare la cache di `\Magento\Framework\Filesystem\Glob::glob(...)`

Questo aggiornamento PR introduce un modo per cancellare la cache statica interna utilizzata da \Magento\Framework\Filesystem\Glob, garantendo risultati freschi e precisi quando le strutture dei file cambiano. Migliora l’affidabilità e l’esperienza degli sviluppatori, in particolare negli scenari di test e nei processi a lunga esecuzione in cui i risultati glob devono rimanere aggiornati.

_AC-15989 - [Problema GitHub](https://github.com/magento/magento2/issues/35741) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35742)_

#### L’URL del collegamento ReadME Leaders ha un reindirizzamento permanente

È stato aggiornato il collegamento README Leaders (Leader README) sostituendo l’URL permanente reindirizzato e scaduto con collegamenti di lavoro corretti, per garantire che le pagine dei collaboratori e dei maintainer si aprano correttamente.

_AC-16046 - [Problema GitHub](https://github.com/magento/magento2/issues/40292) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema] [PHPDOC] Correzione di phpdoc non valido Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Sono state corrette le annotazioni PHPDoc per joinLeft() nella raccolta di attributi per consentire definizioni di array corrette, migliorando la correttezza del codice e la compatibilità con strumenti come PHPStan.

_AC-16187 - [Problema GitHub](https://github.com/magento/magento2/issues/40354) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39155)_

#### Verificare che un singolo errore di comando registri l&#39;errore (file o stderr) senza interrompere l&#39;esecuzione dei comandi CLI successivi.

Il sistema ora assicura che un singolo errore di comando registri l&#39;errore (file o stderr) senza interrompere l&#39;esecuzione dei comandi CLI successivi

_AC-16244 - [Problema GitHub](https://github.com/magento/magento2/issues/40006) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40063)_

#### [Problema] Aggiungi il tipo int a $maxAge nel kernel PageCache

Questa PR assicura che il parametro $maxAge nel kernel PageCache sia rigorosamente digitato come numero intero per migliorare la sicurezza dei tipi e prevenire errori di analisi PHPStan/statica nella gestione della cache.

_AC-16313 - [Problema GitHub](https://github.com/magento/magento2/issues/40438) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36600)_

#### Evento Aggiungi al carrello: prezzi vuoti

È stato risolto un problema a causa del quale i prezzi dei prodotti venivano restituiti come nulli nel checkout_cart_product_add_after event observer durante il processo di aggiunta al carrello.
Ora, il prezzo di base e i relativi valori di prezzo vengono recuperati correttamente, garantendo la disponibilità di dati accurati per gli osservatori e le implementazioni personalizzate.

_AC-5966 - [Problema GitHub](https://github.com/magento/magento2/issues/35638) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Bugfix di tipo PHP8.1

I prodotti associati vengono ora inizializzati in un array vuoto anziché false quando la modalità di elaborazione rigorosa non è attiva o quando sono disponibili informazioni sul prodotto. Questa modifica garantisce che la gestione logica successiva dei prodotti associati si comporti in modo coerente, migliorando la stabilità e la prevedibilità nel processo di preparazione del prodotto.

_AC-6017 - [Problema GitHub](https://github.com/magento/magento2/issues/35808) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/35842)_

#### Previsto tipo &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Trovato &#39;Magento\Customer\Model\Group&#39;.

È stato risolto un problema che causava un errore di tipo durante il salvataggio di un gruppo di clienti tramite GroupRepositoryInterface tramite GroupFactory.
In precedenza, l’archivio prevedeva GroupInterface, ma sono state passate le istanze del modello Group, causando un errore irreversibile.
Ora, i gruppi di clienti possono essere salvati correttamente tramite l’archivio garantendo la corretta implementazione dell’interfaccia.
In questo modo vengono risolti gli avvisi IDE e gli errori di runtime durante la creazione o l’aggiornamento programmatico dei gruppi di clienti.

_AC-6909 - [Problema GitHub](https://github.com/magento/magento2/issues/36269)_

#### Campi di convalida nelle note di accredito

È stato risolto un problema che impediva l’invio della convalida del campo nella pagina della nota di credito anche dopo il riempimento dei campi personalizzati richiesti.
Ora la convalida funziona correttamente e il pulsante Invia viene attivato una volta completati tutti i campi obbligatori.

_AC-8308 - [Problema GitHub](https://github.com/magento/magento2/issues/37182) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problema] Rimuovere il tag `@author` non consentito dal framework (parte 3)

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8343 - [Problema GitHub](https://github.com/magento/magento2/issues/37270) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema] Utilizza la promozione della proprietà del costruttore nel modulo invia messaggio grafo SQL

Il sistema ora utilizza la promozione della proprietà del costruttore nel modulo GraphQL &quot;send friend&quot;, migliorando la leggibilità del codice e riducendo la complessità. In precedenza, il modulo utilizzava proprietà che occupavano numerose righe, rendendo il codice più complesso e meno leggibile.

_AC-8346 - [Problema GitHub](https://github.com/magento/magento2/issues/37235) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8349 - [Problema GitHub](https://github.com/magento/magento2/issues/37266) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8350 - [Problema GitHub](https://github.com/magento/magento2/issues/37265) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Downloadable`

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8355 - [Problema GitHub](https://github.com/magento/magento2/issues/37251) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità e la coerenza del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8358 - [Problema GitHub](https://github.com/magento/magento2/issues/37264) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8359 - [Problema GitHub](https://github.com/magento/magento2/issues/37262) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8360 - [Problema GitHub](https://github.com/magento/magento2/issues/37261) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, garantendo un codice più pulito e standardizzato. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8361 - [Problema GitHub](https://github.com/magento/magento2/issues/37260) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Rimuovi il tag `@author` non consentito

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8362 - [Problema GitHub](https://github.com/magento/magento2/issues/37259) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Rimuovi il tag `@author` non consentito

Il sistema ora rispetta gli standard di codifica rimuovendo il tag `@author` non consentito da alcuni moduli, migliorando la qualità complessiva del codice. In precedenza, la presenza di questo tag in alcuni moduli violava gli standard di codifica stabiliti.

_AC-8363 - [Problema GitHub](https://github.com/magento/magento2/issues/37258) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Backup` e `Magento_Bundle`

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8367 - [Problema GitHub](https://github.com/magento/magento2/issues/37244) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36979)_

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

#### [Problema] Correzione del nome della variabile in catalogsearch

Il sistema ora assegna correttamente i nomi alle variabili nel modulo del motore di ricerca, migliorando la chiarezza del codice e la manutenibilità. In precedenza, veniva utilizzato un nome di variabile irrilevante, $defaultCountry, nel modulo del motore di ricerca, causando confusione.

_AC-9215 - [Problema GitHub](https://github.com/magento/magento2/issues/37810) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation deve essere impostato tramite la variabile di ambiente

Dopo la correzione, è possibile utilizzare la variabile di ambiente &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; per impostare la configurazione &quot;allow_parallel_generation&quot;.

_ACP2E-3673 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud] La modifica del tipo di colonna della tabella da Int a Decimal tramite il file db_schema.xml In Magento 2 genera errori

La modifica del tipo di dati della colonna non funziona correttamente. In precedenza, generava un errore: l’attributo &quot;identity&quot; non era consentito.

_ACP2E-3709 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Supporto per la nuova valuta (XCG) in Adobe

Il Fiorino dei Caraibi (XCG) è aggiunto all&#39;elenco delle valute.

_ACP2E-3790 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Problema con l’aggiornamento 2.4.7-p5 a causa di una nuova convalida

È stato risolto un problema nella classe SchemaBuilder a causa del quale una &quot;colonna&quot; di chiave di array non definita causava un arresto anomalo durante la creazione o gli aggiornamenti dello schema. Ciò si verificava durante l’elaborazione dei dati della tabella che non includevano una chiave &quot;column&quot; (colonna).

_ACP2E-3871 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Problema del server potenzialmente causato da una chiave di accesso S3 non valida

Credenziali AWS S3 errate non causano più il caricamento infinito delle pagine sulla vetrina.

_ACP2E-3890 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js non funziona

Quando la minimizzazione JS è abilitata, ora i seguenti file JS sono minimizzati completamente e correttamente: mage/backend/tabs.min.j, jquery/jquery.validate.min.js e Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Di conseguenza, la convalida del campo della classe CSS di Page Builder funziona come previsto.

_ACP2E-3925 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Errore di deprecazione di PHP8.4: E_USER_ERROR dopo l’aggiornamento ad Adobe Commerce 2.4.8

*NON SONO RICHIESTE NOTE SULLA VERSIONE*
Gli scenari rivolti al cliente non sono interessati dalla correzione.

_ACP2E-3963 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Il processo Cron non cancella la tabella del database, causando interruzioni dovute all’arresto anomalo di Galera

La pulizia delle tabelle del registro modifiche è ora in esecuzione in batch per evitare operazioni di eliminazione complesse.

_ACP2E-3995 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Il file JS non minimizzato a volte viene caricato ignorando &quot;abilita minimizzazioni js&quot;

Prima della correzione, anche se era stata abilitata la minimizzazione, alcuni dei file JS venivano richiesti senza il prefisso &quot;min&quot;, dando luogo al codice di stato 404. Dopo la correzione, quando la minimizzazione è abilitata non sono richieste risorse JS non minimizzate.

_ACP2E-4058 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Attributo data nel gruppo di attributi personalizzato: impossibile visualizzare Datepicker in Admin

È stato risolto un problema a causa del quale la finestra a comparsa del calendario per gli attributi di data veniva visualizzata fuori schermo quando veniva assegnata a gruppi di attributi personalizzati.

_ACP2E-4060 - [Problema GitHub](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Il controllo delle autorizzazioni ACL di produzione ha causato il deterioramento delle prestazioni. Il metodo populateAcl è il collo di bottiglia

Elaborazione delle regole ACL ottimizzate

_ACP2E-4114 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Checkout non caricato nella versione più recente con AC-15867 + ACP2E-4296 e SCD compact

Prima della correzione, il caricamento di javascript personalizzati nella sezione head poteva causare problemi. Dopo l’introduzione della nuova impostazione, tali script possono essere differiti automaticamente, garantendo una maggiore compatibilità con il framework Magento 2.

_ACP2E-4319 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1c547060)_

#### Avviso di deprecazione: utilizzare moment.updateLocale(localeName, config) per modificare una lingua esistente. moment.defineLocale(localeName, config)

Prima della correzione veniva visualizzato un avviso obsoleto nella console del browser. Ora, dopo la correzione, non viene più visualizzato alcun avviso di questo tipo.

_ACP2E-4338 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Incompatibilità con MariaDB 10.11

In precedenza, l’installazione dell’ultima versione di Magento 2 non riusciva quando si utilizzava MariaDB 10.11, impedendo il completamento del processo di installazione. Questo problema è stato risolto aggiornando la gestione della compatibilità del database per supportare MariaDB 10.11.x durante l’installazione.

_ACP2E-4367 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, Ricerca

#### Opensearch 2.19.1 legal_topic_exception su categorie a un prezzo

Opensearch non genera più un’eccezione legal_topic_exception sulle categorie contenenti tutti i prodotti con lo stesso prezzo. Precedentemente, l&#39;eccezione &quot;[dal parametro] non può essere negativa&quot;.

_ACP2E-3896 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### L&#39;invio di un ordine in GraphQL ha esito positivo con un metodo di spedizione non valido

È stato risolto un problema a causa del quale era possibile effettuare gli ordini tramite GraphQL utilizzando un metodo di spedizione disabilitato o non valido.
Ora il sistema convalida il metodo di spedizione selezionato e restituisce un errore se non è disponibile, impedendo la creazione dell&#39;ordine.

_AC-10472 - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38268) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Eccezione durante l’esecuzione di una query GraphQl

È stato risolto un problema a causa del quale una query GraphQL generava un’eccezione a causa di un parametro di ordinamento non valido. Dopo la correzione, la query viene eseguita correttamente senza generare errori o registri di eccezioni.

_AC-14835 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Errore interno del server durante l’aggiunta del prodotto gift card al carrello tramite la mutazione AddProductsToCart che include custom_attributesV2

È stato risolto un errore interno del server attivato quando si aggiungono prodotti gift card (e simili con opzione personalizzata) al carrello tramite GraphQL con custom_attributesV2. La correzione gestisce correttamente valori di attributi complessi, consentendo l&#39;aggiunta di prodotti senza errori.

_AC-15856 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7fa400a7)_

#### Campi nulli nella query `Country`

È stato risolto un problema a causa del quale gli ordini contenenti articoli virtuali, rimborsati e spediti rimanevano in elaborazione garantendo che gli articoli virtuali fossero inclusi nei calcoli della quantità spedita, consentendo la corretta transizione dello stato dell&#39;ordine al completamento.

_AC-7731 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La query GraphQL &quot;customerOrders&quot; con attributo &quot;number&quot; causa un errore interno del server

È stato risolto un problema a causa del quale la query customerOrders di GraphQL restituiva un errore interno del server durante la richiesta del campo numero.
Ora il risolutore restituisce correttamente l’ID dell’incremento dell’ordine, consentendo alla query di essere eseguita correttamente e di recuperare il numero dell’ordine.

_AC-8949 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Il posizionamento di Risposta GraphQL per ordine non include il messaggio di eccezione

È stata ripristinata la modifica precedente che restituiva errori in un formato diverso. Ora i potenziali errori vengono restituiti in modo coerente, senza interrompere lo schema di GraphQL. Questo codice deve essere aggiunto come BIC noto, approvato da PM qui: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

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

#### GraphQL ordine cliente: il recupero delle categorie di prodotto per il prodotto associato &quot;non è visibile singolarmente

Prima della correzione, se l’ordine conteneva un prodotto nascosto, le sue categorie visualizzavano un array vuoto nella risposta Customer Order GraphQl.
Ora, dopo la correzione, le categorie di prodotti vengono incluse nella risposta di una richiesta GraphQl dell’ordine del cliente anche se il prodotto è nascosto.

_ACP2E-3945 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Gli elementi della lista dei desideri non sono condivisi tra store e visualizzazioni all&#39;interno di un sito Web nella richiesta GraphQL

Prima della correzione, gli elementi della lista dei desideri venivano filtrati per ID archivio. Ora, dopo la correzione, gli elementi della lista dei desideri vengono filtrati per sito web.

_ACP2E-3987 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

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

#### Eccezione GraphQL in SWAT

Dopo la correzione, le risposte per le richieste GraphQL vengono allineate con le specifiche GraphQL su HTTP. Viene restituito un codice di risposta 4XX quando è impossibile analizzare la richiesta, la richiesta non è autorizzata o si è verificato un altro problema generale con la richiesta. Se la richiesta viene analizzata e può essere elaborata, verrà restituito un codice di risposta 200.

_ACP2E-4194 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Il prodotto non viene rimosso dall’elenco di confronto dopo che l’elenco è stato assegnato al cliente

Dopo aver assegnato l&#39;elenco di confronto di un utente ospite a un account cliente, i prodotti aggiunti come ospite possono ora essere rimossi dal cliente.
In precedenza, le operazioni di rimozione non erano riuscite perché gli elementi aggiunti dai guest non erano collegati correttamente all&#39;account del cliente dopo l&#39;assegnazione.

_ACP2E-4244 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### risposta di errore errata di updateCartItems GraphQL

In precedenza, quando veniva effettuata una richiesta graphQL per un articolo con quantità insufficiente, veniva restituito un messaggio di errore corretto con un codice di errore, insieme al calcolo della quantità e del prezzo richiesto, anche se l’articolo non era disponibile. Dopo l&#39;applicazione di questa correzione, viene restituito un messaggio di errore corretto con un codice di errore e la quantità dell&#39;articolo viene impostata sul valore precedente, se non è disponibile nella risposta.

_ACP2E-4283 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Bug di assegnazione ordine per ospite in più siti Web nel plug-in MergeGuestOrder

Prima della correzione, un&#39;assegnazione di un cliente di un ordine ospite non prendeva in considerazione le opzioni di condivisione dell&#39;account. Ora, dopo la correzione, un ordine viene assegnato a un cliente se il cliente e l&#39;archivio ordini corrispondono (dato che l&#39;opzione di condivisione del conto cliente è impostata su &quot;Per sito Web&quot;.

_ACP2E-4312 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventory/MSI

#### Problema con only_x_left_in_stock in Magento 2 GraphQL - Calcolo errato quando si utilizzano le soglie

È stato risolto un problema a causa del quale il campo di GraphQL only_x_left_in_stock restituiva null a causa di una doppia deduzione errata di MinQty. Il calcolo è stato corretto in modo da restituire il valore esatto delle scorte in base alle soglie.

_AC-15832 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/35458c7f)_

#### Discrepanze nelle mutazioni GraphQL mergeCart

Dopo la correzione, la richiesta di unione carrelli GraphQL controlla correttamente la quantità di prodotto, tenendo conto della configurazione delle scorte.

_ACP2E-4184 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, prodotto

#### MediaGalleryInterface non contiene il parametro media_type nel grafico del prodotto

La richiesta GraphQL di MediaGallery ora include il campo &quot;tipi&quot; per i tipi di immagini di prodotto. In precedenza, questo campo &quot;types&quot; non esisteva nella richiesta GraphQL di MediaGallery.

_ACP2E-3880 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, sicurezza

#### La reimpostazione della password del cliente tramite GraphQL non rispetta le restrizioni

È stato risolto un problema a causa del quale le richieste di reimpostazione della password del cliente effettuate tramite le mutazioni di GraphQL non rispettavano le restrizioni di reimpostazione della password configurate in Store > Configurazione > Clienti > Configurazione cliente > Opzioni password. Queste impostazioni vengono ora applicate correttamente.

_ACP2E-3992 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importa/esporta

#### [Problema] Correggi il tipo di parametro

È stato risolto un problema di mancata corrispondenza del tipo di parametro nel modulo Import/Export a causa del quale un valore precedentemente definito come stringa ora veniva impostato correttamente come array. Ciò si allinea all’input previsto dal controller di esportazione e impedisce gli avvisi di analisi statica.

_AC-11665 - [Problema GitHub](https://github.com/magento/magento2/issues/38529) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64823f95)_

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

#### Filtri di esportazione per prodotto Sì-No Attributi non funzionano come previsto

Dopo la correzione, i prodotti esportati filtrati da un attributo Sì/No contengono i prodotti previsti che rispettano i filtri applicati.

_ACP2E-4160 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problema relativo al prezzo dell’opzione Aggiorna bundle per sito web tramite Importazione

È ora possibile esportare e importare i prezzi di selezione delle opzioni bundle per sito web

_ACP2E-4243 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Impossibile importare un cliente con un indirizzo e-mail in maiuscolo

È stato corretto un errore di chiave array non definita che si verificava durante l’importazione di clienti con e-mail in maiuscolo quando l’opzione Condivisione account era impostata su Globale. La normalizzazione delle e-mail è ora coerente in tutto il processo di importazione, garantendo ai clienti la possibilità di importare indipendentemente dal caso e-mail. Il comportamento di condivisione degli account a livello di sito web rimane invariato.

_ACP2E-4373 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Importa/esporta, Cliente/Clienti

#### L’amministratore può importare un cliente con data di nascita successiva alla data corrente

È stato risolto un problema a causa del quale gli amministratori potevano importare i clienti con una data di nascita impostata in futuro. Il sistema ora convalida il DOB durante l’importazione, mostra un errore per i record non validi e impedisce l’importazione di clienti con date di nascita future, garantendo così la precisione dei dati dei clienti.

_AC-13641 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventario/MSI

#### Il ritiro dello store non rispetta il raggio di ricerca massimo quando l’indirizzo viene modificato al momento del pagamento

Ora lo store preselezionato in &quot;Pick in Store&quot; verrà aggiornato se l&#39;indirizzo di spedizione cambia. In precedenza, una volta preselezionato un negozio, non veniva modificato anche se il nuovo indirizzo di spedizione non si trovava nel raggio dello store selezionato

_ACP2E-3728 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/07620383)_

#### Nessun negozio disponibile dopo il reindirizzamento alla home page e l&#39;estrazione

Lo store selezionato in precedenza ora sarà preselezionato nella spedizione &quot;Pick in Store&quot; se il cliente passa alla pagina di pagamento, poi ritorna alla home page e infine ritorna alla pagina di pagamento. In precedenza, dopo essere tornato ripetutamente alla pagina di pagamento, lo store selezionato nel &quot;Pick in Store&quot; veniva cancellato.

_ACP2E-3793 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

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

#### Il report dell&#39;amministratore [CLOUD] non mostra i dettagli quando l&#39;inventario viene aggiornato

Le modifiche all’origine dell’inventario dei prodotti vengono ora registrate dal modulo di registrazione. Prima della correzione, durante il salvataggio di un prodotto e l’esecuzione di modifiche relative alle scorte, i dettagli non venivano registrati.

_ACP2E-4167 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Il prodotto del bundle non è in grado di essere aggiunto al carrello mentre è contrassegnato come in magazzino

Lo stato delle scorte dei prodotti del bundle ora riflette correttamente le prenotazioni dei prodotti figlio e le soglie di scorte esaurite.
In precedenza, i prodotti in bundle erano contrassegnati come &quot;in stock&quot; anche quando uno o più prodotti secondari mancavano di quantità sufficiente da vendere. Questo causava errori di tipo &quot;Articoli insufficienti per la vendita&quot; durante l’aggiunta del bundle al carrello.

_ACP2E-4220 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Il prodotto raggruppato viene erroneamente visualizzato come esaurito nel PDP dopo l’importazione dal CSV quando l’elemento secondario viene assegnato all’origine/scorta personalizzata (fisso dopo la reindicizzazione manuale)

Dopo la correzione, la creazione di un prodotto composito tramite l’importazione esegue automaticamente la reindicizzazione delle scorte, rendendo il prodotto disponibile senza la necessità di una reindicizzazione manuale.

_ACP2E-4233 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98f028ab) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] test MFTF non riusciti relativi alle ultime modifiche della linea principale.

Prima della correzione, i clienti ospiti che scelgono il ritiro in-store senza un indirizzo di spedizione avevano il loro indirizzo di fatturazione automatico con l&#39;indirizzo del negozio, che non poteva essere modificato, portando a dettagli di fattura errati. In questo scenario, dopo la correzione dell’indirizzo di fatturazione è ora possibile modificarlo, consentendo agli ospiti di inserire i propri dettagli. Gli utenti registrati vedranno il loro indirizzo di fatturazione salvato invece di quello dello store.

_ACP2E-4260 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ab891304) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/13e432a6)_

#### Prenotazione inventario non corretta creata per le gift card virtuali

Prima dell&#39;implementazione di questa correzione, la quantità di una gift card virtuale contenente più articoli non veniva riflessa in modo accurato nella prenotazione del magazzino. Tuttavia, dopo l’applicazione della correzione, la quantità della prenotazione di magazzino e delle scorte è stata sincronizzata.

_ACP2E-4267 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### Comando Compensazione impegni di magazzino non riuscito con riferimenti di prodotto nulli e non esistenti

È stato risolto un problema che si verificava quando la CLI di compensazione delle prenotazioni di magazzino generava un&#39;eccezione se la combinazione elaborata aveva un ID ordine mancante

_ACP2E-4301 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### Il prodotto è esaurito dopo la modifica del case SKU

La modifica del case SKU non causa più l&#39;esaurimento delle scorte del prodotto sul vetrina.

_ACP2E-4375 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/0836c2ed)_

#### Ordina per facet prezzo/prezzo con dati non validi

Prima della correzione, i prezzi dei bundle non venivano indicizzati correttamente quando i prodotti secondari disponevano di scorte in origini personalizzate. Ora, dopo la correzione, i prezzi dei bundle vengono indicizzati correttamente a prescindere dall’assegnazione delle scorte dei prodotti secondari.

_ACP2E-4380 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1c547060) - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1f83ed24)_

### Ordine

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) interrompe customAttributes

Gli attributi personalizzati sugli indirizzi ora vengono gestiti correttamente durante le operazioni di pagamento e API.
In precedenza, l’utilizzo di $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) poteva interrompere la gestione degli attributi personalizzati, causando una struttura errata dei valori degli attributi.
AC-10568

_AC-10568 - [Problema GitHub](https://github.com/magento/magento2/issues/31644)_

#### Quando il cliente è impostato per l&#39;ordine di preventivo è ancora un ordine ospite

_AC-11689 - [Problema GitHub](https://github.com/magento/magento2/issues/38540)_

#### L&#39;ordine non è completo quando si mescolano articoli virtuali, rimborsati e spediti

È stato risolto un problema a causa del quale gli ordini contenenti articoli virtuali, rimborsati e spediti rimanevano in elaborazione garantendo che gli articoli virtuali fossero inclusi nei calcoli della quantità spedita, consentendo la corretta transizione dello stato dell&#39;ordine al completamento.

_AC-11691 - [Problema GitHub](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Riordino Magento -1 numeri di ordine

Il sistema funziona come previsto e dopo il riordino dal backend il numero dell&#39;ordine sarà univoco di 8 cifre

_AC-12854 - [Problema GitHub](https://github.com/magento/magento2/issues/39089) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39399)_

#### Perdita del caricamento del file di opzione personalizzato del prodotto durante il check-out con il metodo di pagamento con carta di credito di Adobe

I caricamenti dei file di opzioni personalizzati del prodotto vengono ora mantenuti durante il check-out con la carta di credito di Adobe.
In precedenza, i caricamenti di file andavano persi quando si utilizzava questo metodo di pagamento, ma funzionavano con altri.
AC-14306

_AC-14306 - [Problema GitHub](https://github.com/magento/magento2/issues/39647)_

#### Ordini amministratore - impossibile cercare Will

È stato risolto un problema a causa del quale la ricerca di ordini per nome del cliente (ad esempio, &quot;Will&quot;) nella griglia degli ordini di amministrazione non restituiva alcun risultato. Dopo la correzione, gli ordini rilevanti vengono visualizzati correttamente se filtrati per nome del cliente.

_AC-14360 - [Problema GitHub](https://github.com/magento/magento2/issues/36596) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Formattazione errata di order_date per gli articoli dell’ordine

È stato risolto un problema a causa del quale il campo order_date nella risposta di GraphQL restituiva in formato aaaa-mm-gg.
Ora, order_date viene visualizzato correttamente nel formato gg-mm-aaaa.

_AC-14431 - [Problema GitHub](https://github.com/magento/magento2/issues/39805) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Impossibile restituire null per il campo non nullable \&quot;AppliedCoupon.code\&quot;, problema imprevisto

Adobe Commerce ora restituisce correttamente i codici coupon applicati tramite GraphQL quando esegue una query sugli ordini dei clienti. In precedenza, in Adobe Commerce 2.4.8, il recupero di un ordine con il campo apply_coupons.code (ad esempio tramite la query customer.orders) poteva non riuscire e causava un errore interno del server e il messaggio Impossibile restituire null per il campo non nullable &quot;AppliedCoupon.code&quot;, e apply_coupons veniva restituito come [null] invece di un elenco contenente il codice coupon. AC-14484

_AC-14484 - [Problema GitHub](https://github.com/magento/magento2/issues/39841) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### E-mail di spedizione non inviata quando inviata dalla vista Ordine amministratore nonostante sia abilitata nella configurazione archivio

Il sistema ora invia un&#39;e-mail di conferma della spedizione poiché è abilitata nella configurazione del negozio in cui è stato effettuato l&#39;ordine.

_AC-14563 - [Problema GitHub](https://github.com/magento/magento2/issues/39861) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39897)_

#### Il filtro in base alla data non funziona a causa di nomi di campo ambigui

In Magento 2.4.7-p6, è stato segnalato un errore dovuto ai join con i moduli Braintree quando si filtra la griglia dell’ordine per data.
Il problema riguardava l’unione di query braintree_transaction_details e sales_order durante l’applicazione di filtri per data.
Adobe Commerce Engineering ha esaminato il caso, ma non è stato in grado di riprodurre l’errore nell’ambiente.
Il comportamento previsto prevede che il filtro per data restituisca gli ordini che corrispondono al filtro senza errori.

_AC-15037 - [Problema GitHub](https://github.com/magento/magento2/issues/40024)_

#### La creazione dell’ordine in backoffice con più prodotti, almeno uno dei quali contiene opzioni personalizzate, comporta l’aggiunta di prodotti aggiuntivi indesiderati all’ordine

È stato risolto un problema che causava errori durante la creazione di un ordine nel backoffice con più prodotti, tra cui uno con opzioni personalizzate, l’aggiunta involontaria di prodotti aggiuntivi e la generazione di errori. Il sistema ora aggiunge solo i prodotti selezionati, consentendo la creazione di ordini senza elementi imprevisti.

_AC-15286 - [Problema GitHub](https://github.com/magento/magento2/issues/40122) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: impossibile creare la regola di promozione

Questa PR risolve,
modello \Magento\Catalog\Model\ResourceModel\Eav\Attribute invece di \Magento\Catalog\Model\ResourceModel\Eav\Attribute nel metodo \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema GitHub](https://github.com/magento/magento2/issues/12176) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/30479)_

#### Magento ha modificato il tipo di entità di $order dopo le chiamate di $invoc = $this->_invocService->preparationInvoice($order);

È stato risolto un problema a causa del quale la modifica di un aggiornamento pianificato esistente per una sottocategoria aumentava erroneamente il valore child_count per le categorie padre nel database. Il problema ha causato dati errati nella gerarchia di categorie dopo il salvataggio degli aggiornamenti. Dopo la correzione, il conteggio dei figli rimane corretto e non viene più incrementato in modo imprevisto.

_AC-15401 - [Problema GitHub](https://github.com/magento/magento2/issues/40154)_

#### L&#39;ordine rimane nello stato &#39;elaborazione&#39; dopo la spedizione, se gli articoli vengono parzialmente rimborsati

È stato risolto un problema a causa del quale gli ordini rimanevano nello stato Elaborazione dopo il rimborso parziale degli articoli e la spedizione del resto. Lo stato dell&#39;ordine ora viene aggiornato correttamente a Completo quando le quantità totali spedite e rimborsate corrispondono alla quantità fatturata, garantendo una gestione accurata del ciclo di vita dell&#39;ordine.

_AC-15419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### L’invio di un’e-mail di vendita dal backend dà sempre esito positivo, anche quando è disabilitato

È stata corretta la notifica e-mail di vendita back-end per visualizzare messaggi precisi convalidando il risultato del servizio e-mail, garantendo che gli utenti venissero informati quando le e-mail di ordini o fatture vengono disabilitate e non inviate.

_AC-16059 - [Problema GitHub](https://github.com/magento/magento2/issues/40309) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Il prezzo personalizzato pari a 0 viene reimpostato sul prezzo originale al momento del riordino.

È stato risolto un problema che causava il ripristino del prezzo originale dei prodotti con prezzo personalizzato pari a 0.
Ora, il prezzo personalizzato viene mantenuto correttamente, garantendo prezzi accurati quando si riordinano gli articoli.

_AC-8147 - [Problema GitHub](https://github.com/magento/magento2/issues/36970) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Inserisci ordine con metodo di pagamento disabilitato funzionante

È stato risolto un problema che consentiva di effettuare gli ordini utilizzando un metodo di pagamento disattivato tramite GraphQL.
Ora viene restituito un errore quando si tenta di impostare o utilizzare un metodo di pagamento non disponibile, impedendo la creazione dell&#39;ordine.

_AC-9605 - [Problema GitHub](https://github.com/magento/magento2/issues/37983) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Stato ordine bloccato durante l’elaborazione

Prima della correzione, quando si ordina un prodotto in bundle con l’opzione &quot;Spedisci insieme&quot; abilitata, lo stato dell’ordine non passava automaticamente a &quot;completo&quot; dopo la fattura e la spedizione. Ora, dopo la correzione, lo stato dell’ordine passa automaticamente a &quot;completo&quot; dopo che l’ordine è stato fatturato e spedito.

_ACP2E-3947 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Codice Magento OOTB - Problema di configurazione del modello e-mail

Prima della correzione, quando si utilizzava l’invio asincrono di e-mail per la spedizione, queste risultavano incoerenti con l’ordine dello store. Ora, dopo la correzione, viene consegnato l’ordine e-mail di spedizione del negozio corretto.

_ACP2E-3998 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Annulla reindirizzamento fattura a 404

L&#39;annullamento della fattura eseguita con il tipo Non acquisire non porta più alla pagina 404.

_ACP2E-4001 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Problema con gli ordini aggiornati con opzioni configurabili utilizzando l’API REST

Mantenere le opzioni prodotto esistenti sugli articoli dell&#39;ordine di vendita durante l&#39;aggiornamento di un ordine tramite endpoint API rest.

_ACP2E-4061 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Inserimento vendite asincrone per ID limitato a 100 voci per esecuzione cron

È stata migliorata l&#39;elaborazione dell&#39;inserimento asincrono della griglia di vendita. Un&#39;esecuzione cron ora inserisce tutte le righe in sospeso in batch, invece di un rigido 100 per esecuzione.

_ACP2E-4360 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Messaggio di errore &quot;Il prodotto con ID &quot;1&quot; non esiste.&quot; viene registrato ripetutamente in exception.log

Prima della correzione, nella sezione Ultimi elementi ordinati venivano registrati errori critici in seguito al rilevamento di prodotti eliminati. Dopo la correzione, i commercianti possono configurare se registrare o saltare i prodotti eliminati tramite il parametro `skipDeletedProductLogging` in di.xml. Per impostazione predefinita, il comportamento rimane invariato per motivi di compatibilità con le versioni precedenti, ma i commercianti possono impostare il parametro su `true` per ignorare in modo invisibile all&#39;utente i prodotti eliminati ed evitare disturbi nel registro.

_ACP2E-4366 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Doppia imposta sul secondo rimborso nota di accredito

È stato corretto il calcolo dell&#39;imposta errato nelle note di accredito durante la creazione di un rimborso parziale da una fattura dopo la creazione di una nota di accredito precedente dalla pagina di visualizzazione ordine.

_ACP2E-4384 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Ordine, determinazione prezzi

#### L’Amministratore visualizza un simbolo di valuta errato quando crea un reso

In una configurazione multisito con valute diverse (EUR/USD/GBP), nella pagina di selezione del prodotto di ritorno in amministrazione viene ora visualizzato il simbolo di valuta corretto. In precedenza veniva visualizzato il simbolo di valuta predefinito.

_ACP2E-3658 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Ordine, restituzioni

#### Errore durante la creazione della nota di credito per il rimborso offline

È stato risolto un problema che impediva la creazione di una nota di credito per i prodotti bundle con l&#39;impostazione Prezzo dinamico = No. È ora possibile creare le note di credito senza errori.

_ACP2E-4157 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Altri strumenti per sviluppatori

#### [Problema] Suggerimento di tipo errato per il membro protetto $_urlHelper

Il sistema ora corregge l&#39;hint di tipo errato con quello corretto, utilizzato anche nel costruttore

_AC-10716 - [Problema GitHub](https://github.com/magento/magento2/issues/32503) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32496)_

#### [Problema] Pulizia del codice non utilizzato.

Il sistema ora rimuove il codice non utilizzato relativo alle importazioni non utilizzate.

_AC-10980 - [Problema GitHub](https://github.com/magento/magento2/issues/38424) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33499)_

#### Errore di accessibilità del faro

Il sistema ora passa con un punteggio di accessibilità pari a 100

_AC-12783 - [Problema GitHub](https://github.com/magento/magento2/issues/39054) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39164)_

#### Disabilita la configurazione di captcha storefont continua a caricare i file captcha js

Il sistema ora non carica i file captcha js quando è stato disabilitato captcha
per storefont

_AC-14267 - [Problema GitHub](https://github.com/magento/magento2/issues/32987) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39154)_

#### [Problema] accessibilità: i ruoli WAI-ARIA nidificati nel menu non sono corretti

Il sistema ora genera l’accessibilità del faro senza che i ruoli WAI-ARIA nidificino in modo errato nell’errore di menu e il report dovrebbe essere verde

_AC-15082 - [Problema GitHub](https://github.com/magento/magento2/issues/40045) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38617)_

#### Errore della console nell’anteprima e-mail in Magento admin

Il sistema non genererà alcun errore della console durante l’anteprima del modello e-mail

_AC-9245 - [Problema GitHub](https://github.com/magento/magento2/issues/37820) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37933)_

### Metodi di pagamento

#### Il messaggio Paylater non viene visualizzato nella vetrina durante la configurazione nel back-end

È stato risolto un problema che impediva la visualizzazione del messaggio PayPal Pay Later (Paga in seguito PayPal) nelle pagine Home e Carrello nonostante fosse configurato nel backend. Impossibile eseguire il rendering del banner quando il paese dell&#39;acquirente è nullo per gli ospiti o i clienti senza un indirizzo predefinito. Dopo la correzione, il messaggio Paga più tardi viene visualizzato correttamente nella vetrina.

_AC-12335 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/528af81a)_

### Pagamenti

#### [Problema] Correggere l&#39;acquisizione delle fatture offline (404)

Corregge l’errore di pagina 404 durante l’acquisizione di fatture per metodi di pagamento offline dall’amministratore di Magento

_AC-13336 - [Problema GitHub](https://github.com/magento/magento2/issues/39298) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39297)_

#### Gli IPN sconosciuti di PayPal abusano del processore IPN dell&#39;applicazione

Il gestore IPN ora ignora i tipi IPN non supportati o sconosciuti. Invece di restituire un errore 500, registra il problema e continua l’elaborazione senza interruzioni.

_ACP2E-4049 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Token carta salvata PayflowPro non riuscito al pagamento

Gli ID transazione PayFlow Pro (PNREF) di PayPal sono ora validi per l&#39;utilizzo nelle transazioni di riferimento per un periodo fisso di 12 mesi. Una volta scaduta, la scheda salvata non viene più visualizzata e deve essere aggiunta di nuovo. In precedenza, la validità era determinata dalla data di scadenza della carta di pagamento utilizzata nella transazione originale.

_ACP2E-4064 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Problema con scheda archiviata durante l’ordine in Admin

L&#39;inserimento di un ordine con carta di credito memorizzata in un sito Web con una configurazione di azione di pagamento diversa non comporta più un errore o un tipo di transazione errato

_ACP2E-4270 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Le ultime 4 cifre della carta salvata PayflowPro di Cloud] (Vault) non vengono visualizzate nell&#39;ordine

Le informazioni sulla carta ora vengono rese persistenti e visualizzate correttamente quando si utilizzano carte salvate con l&#39;azione di pagamento Vendite, in modo da corrispondere al comportamento quando si utilizza l&#39;azione di pagamento Autorizzazione per PayflowPro.

_ACP2E-4346 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Prestazioni

#### [Problema] - Archivio aggiornamenti.php

Questa PR migliora le prestazioni saltando la risoluzione dell’archivio corrente.

_AC-14791 - [Problema GitHub](https://github.com/magento/magento2/issues/39949) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/38717)_

#### [Problema] L&#39;aggiornamento non può essere modificato dal controllo della cache di utilizzo per il sito statico

Questa PR migliora le prestazioni poiché non convalida il contenuto statico a ogni caricamento di pagina fino a quando &amp; non ne cambia la versione.

_AC-15171 - [Problema GitHub](https://github.com/magento/magento2/issues/39486) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39484)_

#### [Problema] Memorizza nella cache i risultati delle chiamate isCacheable per migliorare le prestazioni

Questa PR aggiunge la memorizzazione in cache per il metodo isCacheable() e determina il processo di rendering del layout, riducendo i controlli ridondanti e migliorando le prestazioni complessive di rendering della pagina.

_AC-16054 - [Problema GitHub](https://github.com/magento/magento2/issues/40156) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40112)_

#### [Problema] miglioramento minore delle prestazioni dell&#39;elaborazione asincrona della griglia ordini

Questa PR introduce un’ottimizzazione delle prestazioni per l’elaborazione asincrona della griglia degli ordini di Magento, sostituendo la ricerca last_updated_at basata su cache transitoria con un flag persistente basato su DB memorizzato nella tabella dei flag. In questo modo il sistema mantiene in modo coerente l’ultima marca temporale elaborata anche dopo gli scaricamenti o le distribuzioni della cache, evitando inutili scansioni di tabelle complete su set di dati sales_order di grandi dimensioni. Di conseguenza, gli aggiornamenti della griglia asincrona diventano più efficienti e prevedibili, in particolare sugli store di grandi volumi con frequenti attività di ordine.

_AC-16109 - [Problema GitHub](https://github.com/magento/magento2/issues/40282) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40271)_

#### [CLOUD] Impossibile aggiungere prodotti alle categorie

Sono state migliorate le prestazioni durante l’aggiunta di prodotti alla categoria tramite Visual Merchandiser.

_ACP2E-3946 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Problema di prestazioni di pulizia Changelog dopo ACP2E-3995

Dopo la correzione, il processo cron indexer_clean_all_changelogs pulisce completamente i registri delle modifiche, mantenendo la suddivisione in batch.

_ACP2E-4211 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD] La cache Fastly non funziona dopo l&#39;aggiornamento alla versione 2.4.8

È stato risolto un problema a causa del quale le pagine memorizzabili in cache non venivano memorizzate o servite correttamente dalla cache Fastly, causando un comportamento di caching incoerente e prestazioni ridotte.

_ACP2E-4324 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Ricercare i motivi per l’aumento delle chiavi redis e della creazione di chiavi cache

Prima della correzione, le chiavi della cache utilizzate per i metadati dell’archiviazione remota non erano in scadenza. Ora, dopo la correzione, puoi impostare un TTL per tali chiavi della cache tramite l’iniezione di dipendenza.

_ACP2E-4345 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Prezzi

#### Il prezzo è sempre 0 per gli articoli di prodotti bundle senza prezzo dinamico in order rest API

L’API REST dell’ordine ora restituisce i prezzi corretti per gli articoli dei prodotti bundle senza prezzo dinamico.
In precedenza, quando si esportavano gli ordini tramite API REST, il prezzo per gli articoli del prodotto bundle senza prezzo dinamico veniva sempre restituito come 0, invece del prezzo effettivo visualizzato nella pagina del bundle.
AC-11925

_AC-11925 - [Problema GitHub](https://github.com/magento/magento2/issues/38687) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7da46f52)_

#### Ambito errato assegnato agli attributi del prezzo al momento della creazione

È stato risolto un problema a causa del quale agli attributi di prezzo appena creati veniva erroneamente assegnato l’ambito Visualizzazione store indipendentemente dalla configurazione. Dopo la correzione, l’ambito dell’attributo ora è allineato per impostazione predefinita all’impostazione Ambito prezzo catalogo (Globale o Sito Web).

_AC-14945 - [Problema GitHub](https://github.com/magento/magento2/issues/39986) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Il prodotto viene salvato anche quando la data di inizio del prezzo speciale è successiva alla data di fine utilizzando l&#39;azione di massa

È stato risolto un problema che consentiva di salvare i prodotti con un intervallo di date di prezzo speciale non valido senza convalida.
Ora viene visualizzato un messaggio di errore: &quot;Assicurarsi che la data di fine sia successiva o uguale alla data di inizio.&quot;

_AC-15252 - [Problema GitHub](https://github.com/magento/magento2/issues/40113) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Il prezzo regolare non è visibile, anche se viene applicato un prezzo speciale.

È stato risolto un problema che impediva la visualizzazione del prezzo regolare quando veniva applicato un prezzo speciale. Il prezzo normale ora appare correttamente insieme al prezzo speciale previsto.

_ACP2E-4100 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Prodotto

#### Prodotto configurabile con comportamento non corretto nel front-end

È stato risolto un problema a causa del quale i prodotti configurabili mostravano un comportamento front-end errato quando veniva incluso un attributo di campione di colore, causando una visualizzazione errata di prezzi, layout a discesa e indicatori di campo obbligatori.
Ora i prodotti configurabili vengono riprodotti correttamente con prezzi appropriati, menu a discesa allineati e comportamento previsto dell’interfaccia utente.

_AC-1014 - [Problema GitHub](https://github.com/magento/magento2/issues/14296) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Stringa di asserzione del prezzo non corrispondente quando il prodotto configurabile è assegnato al sito Web Stock di prova e di prova e l’opzione di visualizzazione dei prodotti esauriti è abilitata

È stato aggiornato il test non riuscito per allinearlo al comportamento effettivo dei prezzi per i prodotti configurabili quando tutti i prodotti secondari hanno lo stesso prezzo.
L’asserzione ora convalida correttamente il prezzo visualizzato, evitando falsi errori di test senza influire sulla funzionalità.

_AC-10843 - [Contributo codice GitHub](https://github.com/magento/inventory/commit/1ccc786b)_

#### Per un prodotto configurabile per il test case AC-6158 viene ancora visualizzata l&#39;etichetta &quot;As low as&quot; (Come basso come)

Prodotti configurabili implementati e verificati (P1-P7) con relative assegnazioni di varianti e categorie. Garantire la corretta visualizzazione del prezzo di vendita e il comportamento dell&#39;etichetta &quot;As low as&quot; per i prodotti della categoria C.

_AC-10847 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Sconto percentuale sul prezzo di livello e regola del prezzo di catalogo calcolata sul prezzo originale senza opzioni selezionate.

Gli sconti percentuali sulle regole del prezzo di livello e del prezzo di catalogo ora includono le opzioni personalizzate selezionate.
In precedenza, gli sconti in percentuale venivano calcolati sul prezzo del prodotto originale senza considerare le opzioni personalizzate selezionate, con conseguente prezzo finale errato.
AC-12004

_AC-12004 - [Problema GitHub](https://github.com/magento/magento2/issues/38750)_

#### [Problema] convalida-valutazione non funzionante, il selettore della valutazione di revisione è stato modificato

È stato risolto un problema a causa del quale la convalida della valutazione di revisione non veniva attivata a causa di un selettore modificato. In precedenza, era possibile salvare le recensioni senza selezionare una valutazione. Dopo la correzione, la convalida funziona correttamente e impedisce il salvataggio di una revisione, a meno che non venga selezionata una valutazione.

_AC-12686 - [Problema GitHub](https://github.com/magento/magento2/issues/33424) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minQtà ordine prodotto mancante consentita

Il sistema funziona correttamente e la sorgente della pagina mostra correttamente la quantità minima del prodotto

_AC-12909 - [Problema GitHub](https://github.com/magento/magento2/issues/39142) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39480)_

#### Raccolta prodotti: chiamate addMediaGalleryData getSize quando la raccolta può essere o sarà caricata (può utilizzare il conteggio per evitare una query DB aggiuntiva)

Questa PR riduce la chiamata di query aggiuntiva utilizzando count() se la raccolta di prodotti è già caricata durante la chiamata di Product Graphql con il campo media_gallery incluso.

_AC-13055 - [Problema GitHub](https://github.com/magento/magento2/issues/39111) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39681)_

#### Gestione SKU non valida per i prodotti collegati in Magento

È stato risolto un problema che impediva il collegamento dei prodotti con SKU &quot;0&quot; come articoli correlati, di upselling o di cross-selling a causa di una convalida SKU non valida. L’aggiornamento garantisce che tali prodotti possano essere collegati correttamente, consentendo al prodotto di salvare senza errori.

_AC-13311 - [Problema GitHub](https://github.com/magento/magento2/issues/39329) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problema con la griglia Opzioni personalizzabili nella pagina del prodotto nel pannello di amministrazione

Il sistema funziona come previsto durante la creazione di opzioni personalizzabili con il menu a discesa del tipo

_AC-14003 - [Problema GitHub](https://github.com/magento/magento2/issues/39640) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39694)_

#### Errore nella pagina di prodotto Amministrazione quando tutti gli attributi di prodotto sono impostati su ambito globale

È stato risolto un problema che causava la visualizzazione di un errore nella pagina di modifica del prodotto da parte dell’amministratore quando tutti gli attributi del prodotto erano impostati su ambito globale. L’errore è stato causato da una query del database vuota che ha reso la pagina inutilizzabile. Dopo la correzione, la pagina di prodotto viene riprodotta correttamente e i prodotti possono essere creati senza problemi.

_AC-14011 - [Problema GitHub](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] Nessun callback trovato per il processo cron catalog_product_alert

Adobe Commerce ora impedisce correttamente la pianificazione di processi cron catalog_product_alert errati dopo che il processo cron dell’avviso relativo al prodotto è stato rinominato in product_alert. In precedenza, in Adobe Commerce 2.4.8, la configurazione di Archivi > Configurazione > Catalogo > Catalogo > Impostazioni di esecuzione avvisi prodotto causava la creazione di una voce cron catalog_product_alert in core_config_data e, quando cron veniva eseguito, registrava l’errore Magento_Cron.CRITICAL: Eccezione: nessun callback trovato per il processo cron catalog_product_alert anche se i processi product_alert validi venivano eseguiti correttamente.

_AC-14494 - [Problema GitHub](https://github.com/magento/magento2/issues/39800) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [L&#39;elenco di confronto dei prodotti] non sarà utilizzabile

È stato risolto un problema a causa del quale l’elenco di confronto diventava inutilizzabile quando lo stesso prodotto veniva aggiunto da diverse visualizzazioni dello store. Dopo la correzione, l’elenco di confronto veniva caricato correttamente e visualizzava gli elementi in base allo specifico store.

_AC-14885 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Registrazione Aggiuntiva Quando La Richiesta Di Un Prodotto Tramite Archivio Non Riesce

Messaggi di errore migliorati per ProductRepository::get e getById quando non viene trovato uno SKU o un ID.
In precedenza, le eccezioni non fornivano alcun contesto in merito allo SKU o all’ID che causava l’errore.
Ora, il messaggio di eccezione include lo SKU o l’ID mancante, facilitando il debug e migliorando l’esperienza di sviluppo.
Questa modifica non influisce su alcun comportamento funzionale dell’API.

_AC-15199 - [Problema GitHub](https://github.com/magento/magento2/issues/40090) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### L’errore Set di attributi non esiste interrompe la pagina

È stato risolto un problema che causava un errore irreversibile quando si immetteva nell’URL un ID set di attributi non valido. Ora il sistema visualizza un messaggio di errore corretto in cui si informa che il set di attributi non esiste invece di interrompere la pagina.

_AC-15753 - [Problema GitHub](https://github.com/magento/magento2/issues/40213) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Rimborso con sconto di rimborso quantità sempre negativo

È stato risolto un problema a causa del quale la creazione di una nota di accredito con una quantità negativa rimborsava erroneamente l&#39;importo dello sconto.
Ora gli sconti non vengono rimborsati per quantità negative e la quantità di rimborso viene impostata correttamente su zero.

_AC-9424 - [Problema GitHub](https://github.com/magento/magento2/issues/37917) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La query lenta viene eseguita quando il widget del prodotto è incluso tramite pagebuilder

La query per la creazione di widget di prodotto, inclusi SKU di prodotto, è ottimizzata.

_ACP2E-3449 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Immagini del prodotto non ridimensionate quando aggiunte come prodotto configurabile

In precedenza, le immagini aggiunte tramite le configurazioni nel pannello di amministrazione non rispettavano il limite di dimensione massima per il caricamento, il che poteva causare incoerenze e problemi di gestione. Ora è stata implementata una correzione per garantire che le immagini vengano ridimensionate automaticamente durante il caricamento in modo da rispettare il limite di dimensione massimo, semplificando il processo e mantenendo gli standard di sistema.

_ACP2E-3504 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Tutti gli elementi degli elenchi di confronto di altri clienti vengono assegnati al cliente dopo l’accesso tramite l’amministratore

In precedenza, quando un amministratore utilizzava la funzione &quot;Accedi come cliente&quot; nel back-end, i prodotti dell’elenco di confronto di un cliente precedentemente connesso venivano erroneamente assegnati al cliente attualmente rappresentato.  Dopo la correzione, l’elenco di confronto viene caricato correttamente per il cliente connesso corretto.

_ACP2E-3818 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### [B2B] Il salvataggio del catalogo condiviso restituisce un errore di funzionalità obsoleto

L’amministratore può annullare l’assegnazione dei prodotti dal catalogo condiviso.
La precedente annullamento dell’assegnazione di prodotti con un numero elevato di SKU di prodotti lunghi da Shared Catalog generava un errore

_ACP2E-4097 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Le prestazioni di generazione di [Cloud] Sitemap sono significativamente ridotte

La generazione di sitemap per i prodotti con immagini non subisce più un rallentamento esponenziale. In precedenza, la generazione di sitemap per i negozi in cui era abilitata l’inclusione delle immagini comportava tempi di elaborazione lunghi.

_ACP2E-4153 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Prodotto, Imposta

#### L&#39;FPT (Fixed Product Tax) non viene visualizzato separatamente con i prodotti configurabili

È stato risolto un problema che impediva la visualizzazione separata di FPT (Fixed Product Tax) per i prodotti configurabili dopo aver selezionato un’opzione. Ora, la suddivisione FPT viene visualizzata correttamente sulle pagine di elenco dei prodotti e di dettaglio, in base al formato di visualizzazione dei prodotti semplici.

_AC-13171 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

### Promozione

#### Acquista X Ottieni la regola di prezzo del carrello aggiunge lo sconto errato quando un&#39;altra regola è già stata applicata

È stato risolto un problema a causa del quale la regola Compra X Ottieni Y carrello applicava sconti calcolati utilizzando il prezzo del prodotto originale anche dopo che un&#39;altra regola lo aveva già ridotto. L’aggiornamento assicura che la seconda regola applichi ora lo sconto al prezzo adeguato, ottenendo sconti totali accurati quando sono attive più promozioni.

_AC-12325 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Errore nell’ottenere gli sconti sull’articolo ordine apply_to per l’ordine del cliente tramite la richiesta del cliente GraphQl

In precedenza, quando si osservava l’errore del server interno nella richiesta del cliente GraphQl con sconti apply_to per l’ordine del cliente, ora è fisso e vengono recuperati i dati corretti dell’ordine del cliente con sconti applicati

_AC-14888 - [Problema GitHub](https://github.com/magento/magento2/issues/39963) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Errore nell’ottenere il codice del coupon dell’articolo dell’ordine tramite la richiesta del cliente GraphQl

È stato risolto un problema a causa del quale il recupero degli ordini con i dettagli del coupon tramite GraphQL restituiva un errore interno del server.
Ora la query viene eseguita correttamente e restituisce le informazioni corrette del coupon nella risposta.

_AC-14889 - [Problema GitHub](https://github.com/magento/magento2/issues/39962) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Regola prezzo catalogo `[Cloud][experienceleague]` non applicata

Prima di correggere le regole del prezzo del catalogo non erano applicabili quando `special_price` era impostato solo a livello di sito Web (non in &quot;Tutte le visualizzazioni dello store&quot;). Dopo la correzione, le regole del prezzo del catalogo ora vengono applicate correttamente quando `special_price` viene impostato a livello di sito Web controllando prima lo store predefinito del sito Web.

_ACP2E-4372 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() non dispone del filtro entity_type, pertanto le pagine CMS devono essere trattate come prodotti negli URL delle categorie

È stato risolto un problema che impediva a DynamicStorage di filtrare per entity_type, causando il trattamento errato delle pagine CMS come prodotti negli URL delle categorie. Gli URL non validi ora restituiscono correttamente un valore 404 invece di fornire contenuto CMS.

_AC-14991 - [Problema GitHub](https://github.com/magento/magento2/issues/39996) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### L’abilitazione del percorso di categoria negli URL del prodotto interrompe lo switcher del negozio in più modi

È stato risolto un problema che causava un errore nel commutatore store quando si abilitavano i percorsi delle categorie negli URL dei prodotti; ora il passaggio da un archivio all’altro risolve correttamente gli URL dei prodotti tra le visualizzazioni del negozio senza reindirizzare alla home page o restituire errori.

_AC-15110 - [Problema GitHub](https://github.com/magento/magento2/issues/40037) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Chiave array non definita in ProductRepository getById

Il problema si verificava quando ProductRepository::getById() veniva chiamato con un ID non valido come 123abc, causando un errore di tipo &quot;Chiave array non definita&quot;.
Dopo la correzione in Magento 2.4.9-alpha3, tali richieste ora restituiscono correttamente una pagina 404 invece di generare un’eccezione.
Il controllo qualità è stato confermato con ID validi e non validi e non sono stati osservati ulteriori problemi.

_AC-15345 - [Problema GitHub](https://github.com/magento/magento2/issues/40146) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Errore SEO di Google generato dal prodotto di confronto Storefront. Impossibile eseguire la ricerca per indicizzazione dei collegamenti

È stato risolto un problema SEO (Search Engine Optimization) a causa del quale il collegamento &quot;Compare Products&quot; nella vetrina non era eseguibile dalla ricerca per indicizzazione a causa di un attributo href mancante o associato in modo errato. L’aggiornamento garantisce che il collegamento contenga ora un URL valido e sottoponibile a ricerca per indicizzazione, migliorando la reperibilità del sito e aiutando a superare i controlli SEO (Search Engine Optimization) di Google.

_AC-15547 - [Problema GitHub](https://github.com/magento/magento2/issues/40185) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### L’aggiornamento di product url_key tramite API REST non genera un URL 301 Rewrite

Quando si aggiorna la chiave URL del prodotto tramite l’API REST, con l’impostazione &quot;Create Permanent Redirect for URLs if URL Key Changed&quot; (Crea reindirizzamento permanente per gli URL se la chiave URL è stata modificata) impostata su Sì, l’URL del prodotto riscritto viene creato per creare un reindirizzamento dal vecchio URL a uno nuovo.

_ACP2E-3900 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### [Cloud] La generazione di sitemap non termina mai

Prima della correzione, la generazione della sitemap non poteva terminare correttamente se il catalogo conteneva più di un milione di prodotti. Dopo la correzione, la generazione della sitemap terminerà con un’allocazione di memoria inferiore e un massimo di un milione di prodotti per store.

_ACP2E-3902 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### [Il commutatore di store cloud] non funziona da EN a FR per la pagina delle domande frequenti

È stato risolto un problema a causa del quale, passando da una visualizzazione store a un’altra, gli utenti venivano reindirizzati alla home page e non alla corrispondente pagina CMS tradotta. Il commutatore del negozio ora verifica la riscrittura degli URL nel negozio di destinazione per garantire il corretto reindirizzamento (ad esempio, pagina FAQ in inglese → pagina FAQ in francese).

_ACP2E-4112 - [Problema GitHub](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Cloud] Disattiva la generazione precedente di sitemap

È ora disponibile una nuova opzione di configurazione per passare dal processo standard di generazione della sitemap a una nuova modalità batch implementata. Questo miglioramento offre maggiore flessibilità e scalabilità nei flussi di lavoro per la creazione di sitemap.

_ACP2E-4132 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Le richieste sospette generano eccezioni in exception.log

È stato risolto un problema che causava errori di regole di confronto del database e la compilazione dei registri di eccezioni a causa di richieste URL dannose o non valide.
In precedenza, quando venivano ricevute richieste sospette contenenti codifiche di caratteri non valide o caratteri non supportati, il sistema tentava di decodificarli ed elaborarli, causando conflitti di regole di confronto MySQL.

_ACP2E-4328 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2687b487)_

### Vendite

#### Se il messaggio Regalo è abilitato a livello di Ordine ma l’utente non immette dati e non inserisce alcun ordine, in Amministratore vengono comunque visualizzati i campi Da nome e A nome del cliente.

È stato risolto un problema a causa del quale i campi Mittente e Destinatario del messaggio regalo venivano compilati automaticamente con i nomi dei clienti anche quando non veniva immesso alcun messaggio regalo. I campi ora rimangono vuoti a meno che l’utente non fornisca i dettagli.

_AC-15140 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

### Ricerca

#### &quot;Conferma reinvio modulo&quot; nella ricerca nel catalogo con &quot;Ricorda paginazione categoria&quot;

Quando si torna dalla pagina di un prodotto alla pagina dei risultati della ricerca nel catalogo dopo aver modificato le impostazioni della barra degli strumenti, non viene più attivata la finestra di dialogo &quot;Conferma invio modulo&quot; quando è abilitata l’opzione &quot;Ricorda paginazione categorie&quot;.
In precedenza, gli utenti riscontravano un errore del browser o un avviso relativo al reinvio dei moduli quando tornavano alla pagina dei risultati della ricerca dopo aver modificato i parametri della barra degli strumenti, ad esempio il criterio di ordinamento.

_ACP2E-4208 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Il campo di ricerca aggregato &quot;_search&quot; non viene più utilizzato nella query di ricerca

Ora, la ricerca full-text restituisce i prodotti corrispondenti se la condizione di corrispondenza minima viene soddisfatta collettivamente in tutti i campi ricercabili, anziché richiedere che la condizione venga soddisfatta da un singolo campo.

_ACP2E-4285 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cbca0396)_

### Sicurezza

#### Errore interno del server

Magento ora aggiunge correttamente i prodotti al carrello di un cliente quando si utilizza l’endpoint REST asincrono POST /rest/default/async/V1/carts/mine/items. In precedenza, questa richiesta asincrona &quot;aggiungi al carrello&quot; causava un errore interno del server e Magento registrava il seguente errore: Errore: Chiamata a un set di funzioni membro FinalPrice() su null in app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### JS in bundle/uniti non fa parte degli hash SRI

Prima della correzione, il bundle generato o i file uniti non venivano aggiunti all’elenco di hash SRI. Ora i file vengono aggiunti correttamente agli hash dell’SRI.

_ACP2E-3854 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] ha ottenuto il problema di autorizzazione scrivibile in newrelic

Prima della correzione, i registri venivano riempiti con eccezioni. Dopo aver applicato la correzione, i registri ora sono puliti e privi di eccezioni.

_ACP2E-4296 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Spedizione

#### Qtà da spedire errata dopo poche note di credito

È stato risolto un problema a causa del quale il valore Qtà da spedire veniva calcolato in modo errato dopo più note di credito, consentendo la spedizione di articoli rimborsati.
Ora il sistema aggiorna accuratamente la quantità rimanente spedibile in base agli articoli spediti e rimborsati, impedendo spedizioni non valide.

_AC-1479 - [Problema GitHub](https://github.com/magento/magento2/issues/34289) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Potenziale problema di prestazioni sul caricamento dei metodi di spedizione

È stato ottimizzato il processo di caricamento dei metodi di spedizione garantendo che vengano caricati solo i vettori attivi quando richiesto. In precedenza, venivano inizializzate le fabbriche per tutti i metodi di spedizione, causando un sovraccarico di prestazioni non necessario. La correzione migliora l’efficienza caricando in modo condizionale solo i vettori di spedizione attivi, riducendo il tempo di caricamento e l’utilizzo delle risorse.

_AC-15415 - [Problema GitHub](https://github.com/magento/magento2/issues/40153) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Problema] La destinazione commerciale non deve essere considerata residenziale

È stato risolto un problema nell’integrazione di spedizione REST UPS a causa del quale le destinazioni commerciali venivano erroneamente trattate come residenziali. Il ResidentialAddressIndicator è ora incluso nella richiesta di tariffa UPS solo per gli indirizzi residenziali, prevenendo sovrapposizioni residenziali non intenzionali e garantendo tariffe di spedizione commerciali accurate.

_AC-16285 - [Problema GitHub](https://github.com/magento/magento2/issues/40314) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/40307)_

#### Eccezione durante la creazione dell&#39;etichetta di spedizione UPS

Avviso corretto: conversione da array a stringa durante la creazione di etichette di spedizione UPS

_ACP2E-3676 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Il modulo di base Magento_Fedex verifica la presenza di un token attivo valido prima di inviare una richiesta per ottenerne uno nuovo?

Adobe Commerce non effettua molte richieste al servizio API FedEx per il token di accesso. In precedenza, anche se il token di accesso è ancora valido, Adobe Commerce effettuava sempre nuove richieste all’API FedEx, causando un problema di limitazione della frequenza.

_ACP2E-3930 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Staging e anteprima

#### Il prezzo del prodotto nel carrello interessato dalla regola del prezzo di catalogo non cambia quando la regola viene adeguata dall’aggiornamento della gestione temporanea

È stato risolto un problema a causa del quale i prezzi dei prodotti nel carrello non venivano aggiornati completamente dopo la modifica di una regola del prezzo di catalogo tramite un aggiornamento di staging. In precedenza, il prezzo aggiornato appariva solo nella sezione di riepilogo, mentre il blocco del carrello centrale mostrava il valore precedente. Ora, la regola rivista aggiorna correttamente il prezzo del prodotto in tutto il carrello.

_AC-15304 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Quando si elimina l&#39;aggiornamento pianificato per la categoria, la quantità di elementi figlio non viene diminuita per la categoria padre

È stato risolto un problema a causa del quale l’eliminazione di un aggiornamento pianificato per una categoria non riduceva il conteggio dei figli della categoria principale, garantendo la corretta esecuzione del conteggio quando vengono rimossi gli aggiornamenti o le sottocategorie pianificati.

_AC-15670 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Durante la modifica dell&#39;aggiornamento pianificato per le categorie, l&#39;importo dei figli viene aggiunto alla categoria padre

È stato risolto un problema a causa del quale la modifica di un aggiornamento pianificato esistente per una sottocategoria aumentava erroneamente il valore child_count per le categorie padre nel database. Il problema ha causato dati errati nella gerarchia di categorie dopo il salvataggio degli aggiornamenti. Dopo la correzione, il conteggio dei figli rimane corretto e non viene più incrementato in modo imprevisto.

_AC-16239 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### L&#39;anteprima di un aggiornamento pianificato consente di aprire la prima visualizzazione dello store in ordine alfabetico anziché la visualizzazione dello store di interesse

Prima della correzione, l’anteprima di un aggiornamento pianificato veniva aperta nella prima visualizzazione store in ordine alfabetico anziché nella visualizzazione store assegnata.
Dopo la correzione, l’anteprima ora si apre correttamente nella vista archivio assegnata all’aggiornamento di staging del blocco CMS.

_ACP2E-3671 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Impossibile visualizzare in anteprima l&#39;aggiornamento programmato del prodotto con le autorizzazioni per la categoria abilitate

Prima della correzione, un prodotto futuro da abilitare non veniva visualizzato in modalità anteprima. Ora viene visualizzato anche se lo stato corrente è disabilitato.

_ACP2E-3786 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Convalida mancante per il campo Importo sconto regola prezzo catalogo

In precedenza, il campo discount_amount nell’aggiornamento della pianificazione di staging non veniva convalidato correttamente con le regole di convalida correnti. Tuttavia, dopo aver applicato la correzione, il campo sconto_importo verrà convalidato in modo appropriato.

_ACP2E-3867 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Il bundle prodotto con aggiornamenti pianificati rimuove l’opzione elementi bundle durante l’azione di salvataggio del prodotto

La rimozione delle opzioni di prodotto del bundle o dei prodotti associati nell’aggiornamento pianificato non influisce più sulle opzioni di bundle originali e sui prodotti associati e viceversa. Anche la rimozione delle opzioni di produzione del bundle nel prodotto originale e la sostituzione con altre opzioni dopo la pianificazione di un aggiornamento non si traduce più nella rimozione delle nuove opzioni aggiunte

_ACP2E-4212 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Impossibile spostarsi tra siti Web nell&#39;anteprima di aggiornamento pianificazione

Prima di questa correzione, l’anteprima dell’aggiornamento pianificato si interromperebbe quando si tenta di visualizzare in anteprima il contenuto per gli archivi con domini personalizzati. Dopo questa correzione, i domini store personalizzati possono essere visualizzati in anteprima così come sono e spostati all’interno dell’iframe di anteprima. La correzione riguarda prodotti, categorie, pagine CMS e blocchi CMS e supporta i collegamenti di navigazione tramite `{{store url}}` tag di markup, come documentato in [Variabili Adobe Commerce e tag di markup](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/variables/markup-tags).

_ACP2E-4308 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Imposta

#### Totale ordine errato. L&#39;arrotondamento non viene applicato al calcolo del prezzo.

Il sistema è ora in grado di gestire correttamente il calcolo dell&#39;importo price_after_discount, discount_amount e tax.
il totale effettivo dell&#39;ordine

_AC-11389 - [Problema GitHub](https://github.com/magento/magento2/issues/38455) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/39687)_

#### [Problema] Correzione: Il valore base_weee_tax_apply_row_amnt degli elementi della nota di credito non è corretto

È stato corretto il calcolo della nota di accredito utilizzando il setter appropriato per base_weee_tax_apply_row_amnt, in modo che il valore dell&#39;imposta rifletta solo la quantità rimborsata. In precedenza, l&#39;importo della riga utilizzava erroneamente il valore completo dell&#39;ordine invece dell&#39;importo parziale della nota di accredito.

_AC-12049 - [Problema GitHub](https://github.com/magento/magento2/issues/38765) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Gli articoli nel mini-carrello visualizzano i prezzi in valuta estera senza conversione

Il mini-carrello ora converte correttamente la valuta e visualizza l’importo preciso in base ai tassi di conversione configurati.

_ACP2E-4364 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Framework di test

#### [Problema] Rimuovere un tag &lt;severity> duplicato dal test MFTF AdminSetUpWatermarkForSwatchImageTest

Il sistema ora include un solo tag di gravità in AdminSetUpWatermarkForSwatchImageTest, migliorando la chiarezza e la coerenza del codice. In precedenza, questo test conteneva due tag di gravità identici, il che era superfluo e poteva portare a confusione.

_AC-11873 - [Problema GitHub](https://github.com/magento/magento2/issues/38504) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31862)_

#### [Problema] Ignora lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

Il sistema ora ignora il file &quot;env.php&quot; generato durante l’esecuzione degli unit test, garantendo che lo stato Git rimanga pulito dopo l’esecuzione dei test. In precedenza, l’esecuzione degli unit test generava un nuovo file &quot;env.php&quot;, causando la visualizzazione di un nuovo file trovato e rendendolo più sporco.

_AC-13293 - [Problema GitHub](https://github.com/magento/magento2/issues/39304) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema] è stato corretto un problema di test dell&#39;integrazione con l&#39;intercettore

Il sistema ora identifica e gestisce correttamente \Magento\TestFramework\App\Config\Interceptor nel test di integrazione, garantendo che il test possa accedere ai dati necessari anche quando esiste un plug-in nella classe. In precedenza, il sistema non riusciva a tenere conto della possibilità che \Magento\TestFramework\App\Config fosse un \Magento\TestFramework\App\Config\Interceptor, causando un errore durante il tentativo di accedere alla proprietà $data.

_AC-13305 - [Problema GitHub](https://github.com/magento/magento2/issues/39324) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: invio di e-mail a un modulo per amici con captcha abilitato

Il caso di test riguarda la funzionalità del modulo &quot;E-mail all’amico&quot; quando CAPTCHA è abilitato, garantendo che il processo di invio del modulo funzioni correttamente con valori CAPTCHA sia errati che corretti.

_AC-13492 - [Problema GitHub](https://github.com/magento/magento2/issues/39462) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/32830)_

#### I percorsi di staffaggio hardcoded non riescono nelle build del compositore

_AC-16488_

#### [Problema] magento/magento2#: mutazione GraphQl. Copertura di test aggiuntiva per le impostazioni storeConfig del cliente.

Il sistema ora aggiunge la copertura di test aggiuntiva per le opzioni storeConfig del cliente successivo:
required_character_classes_number
minimum_password_length

_AC-9370 - [Problema GitHub](https://github.com/magento/magento2/issues/37915) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/28761)_

#### Guasti degli unit test specifici dell’ambiente in AC 2.4.7-p3

Questo problema risolve gli errori degli unit test che non vengono riprodotti su tutte le versioni e gli ambienti. In precedenza, per correggere alcuni unit test non riusciti a causa di diverse versioni della libreria o a causa di funzionalità mancanti aggiunte in una versione successiva.

_ACP2E-3712 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Framework interfaccia utente

#### [Problema] Rimuovi le variabili duplicate da uno o più file

Il sistema ora rimuove le variabili duplicate da meno file, garantendo un codice più pulito ed efficiente. In precedenza, queste variabili duplicate erano presenti nei file meno, con conseguente ridondanza non necessaria nel codice.

_AC-11743 - [Problema GitHub](https://github.com/magento/magento2/issues/31154) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG è vuoto nelle righe dinamiche

I campi WYSIWYG nelle righe dinamiche ora sono inizializzati e compilati correttamente.
In precedenza, i campi WYSIWYG nelle righe dinamiche (ad esempio nei moduli di configurazione della progettazione) potevano apparire vuoti o perdere il loro contenuto dopo determinate azioni, rendendo necessario l’intervento manuale per ripristinare i dati.
AC-12336

_AC-12336 - [Problema GitHub](https://github.com/magento/magento2/issues/38893) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] Correzione dell&#39;errore di tipo MIME

Il sistema gestisce e corregge correttamente il tipo mime e l’errore di battitura per l’immagine gif

_AC-8001 - [Problema GitHub](https://github.com/magento/magento2/issues/36899) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Rimuovere il tag `@author` non consentito da `Magento_Backend`

Questa PR rimuove il tag `@author` dalla base di codice

_AC-8814 - [Problema GitHub](https://github.com/magento/magento2/issues/37522) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/36976)_

#### [Problema] Evita l&#39;accesso diretto all&#39;elenco delle recensioni Ajax

Il sistema gestisce correttamente ed evita l&#39;accesso diretto all&#39;elenco recensioni Ajax

_AC-9381 - [Problema GitHub](https://github.com/magento/magento2/issues/37920) - [Contributo codice GitHub](https://github.com/magento/magento2/pull/33876)_

#### Intestazione Login/Logout Not Updating in Multi-Store Setup with Shared Cookies (Accesso/disconnessione non aggiornamento in configurazione di più store con cookie condivisi)

L’intestazione di accesso viene aggiornata correttamente al momento della disconnessione in base alle impostazioni di configurazione. Il file customer-data.js utilizzerà un cookie per memorizzare il valore &quot;mage-customer-login&quot; se gli account cliente sono condivisi a livello globale. In caso contrario, verrà utilizzata l’archiviazione locale.

_ACP2E-4149 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama può aprire Mini Cart su Image Viewer azione di chiusura

È stato risolto il problema relativo a Fotorama. In precedenza, per l&#39;azione di chiusura del Visualizzatore immagini veniva aperto un Mini carrello

_ACP2E-4231 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### I file js uniti non vengono generati correttamente in progetti con molti archivi.

L’unione di file JavaScript ora funziona correttamente quando sono configurati più archivi.
In precedenza, a volte i file non venivano uniti correttamente nelle impostazioni multi-store, generando risultati incompleti o incoerenti.

_ACP2E-4246 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/ab891304)_

### Aggiornamenti - Upgrade Compatibility Tool

#### Funzionalità obsoleta: creazione della proprietà dinamica Magento\Framework\Acl::$_roleRegistry

Gli errori di funzionalità obsoleti non impediscono più l’accesso al pannello di amministrazione dopo l’aggiornamento.
In precedenza, dopo l’aggiornamento a Magento 2.4.6, il tentativo di accedere al pannello di amministrazione poteva causare l’errore:
&quot;Funzionalità obsoleta: la creazione della proprietà dinamica Magento\Framework\Acl::$_roleRegistry è obsoleta in vendor/magento/framework/Session/SessionManager.php alla riga 186&quot;
Questo impediva agli amministratori di effettuare l’accesso.
AC-12343

_AC-12343 - [Problema GitHub](https://github.com/magento/magento2/issues/37469)_

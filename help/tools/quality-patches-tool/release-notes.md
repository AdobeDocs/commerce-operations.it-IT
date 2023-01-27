---
title: Note sulla versione
description: Scopri le patch disponibili per Adobe Commerce e i problemi che risolvono.
source-git-commit: 230e457a783707c2447fab046a6d139ac97a20c5
workflow-type: tm+mt
source-wordcount: '10584'
ht-degree: 0%

---

# Note sulla versione

La [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) offre patch individuali sviluppate dall&#39;Adobe e la comunità del Magento Open Source. Consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce o Magento Open Source. È possibile applicare patch ai progetti Adobe Commerce e Magenti Open Source indipendentemente da chi ha sviluppato la patch. Ad esempio, puoi applicare una patch sviluppata dalla community ai progetti Adobe Commerce.

>[!INFO]
>
>Vedi [Applica patch](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) per istruzioni su come applicare patch ai progetti Adobe Commerce o Magenti Open Source. Vedi [Patch disponibili](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella Guida all’aggiornamento del software per esaminare un elenco completo delle patch rilasciate.

>[!INFO]
>
>Per informazioni su [!DNL quality patches] creato dalla Comunità per Magento Open Source, vedi [note sulla versione](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (per Adobe Commerce e Magenti Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Risolve il problema per cui le notifiche di calo dei prezzi non vengono sempre inviate a causa della memorizzazione in cache a livello di applicazione.
* **ACSD-48661** (per Adobe Commerce e Magenti Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema per cui se il limite di credito della società è superiore a 999, il separatore virgola impedisce il salvataggio della società a causa di un errore di convalida.
* **ACSD-48773** (per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema in cui il modello e-mail dei punti di ricompensa viene preso dal negozio sbagliato.
* **ACSD-48587** (per Adobe Commerce e Magenti Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema in cui i caratteri speciali di HTML nelle regole di corrispondenza dei widget dei prodotti impedivano loro di visualizzare i prodotti corrispondenti.
* **ACSD-48212** (per Adobe Commerce e Magenti Open Source >=2.3.7 &lt;2.4.6) - Risolve il problema per cui l’importazione di prodotti assegna il prodotto all’origine errata.
* **ACSD-47988** (per Adobe Commerce e Magenti Open Source >=2.3.7 &lt;2.4.6) - Risolve il problema per cui l’esportazione del prodotto taglia i tag HTML dalla descrizione del prodotto page builder.
* **ACSD-48366** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Risolve il problema per cui l’immagine del prodotto non viene visualizzata sul modello e-mail Indietro su Stock.
* **ACSD-48417** (per Adobe Commerce e Magenti Open Source >=2.4.5 &lt;2.4.7) - Risolve il problema in cui viene visualizzato un errore SQL dopo la creazione di una modifica della pianificazione per un prodotto e il salvataggio di un altro prodotto.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Risolve il problema di mancato funzionamento del reindice del prezzo del prodotto se il prodotto bundle non è assegnato ad alcun sito web.
* **ACSD-48262** (per Adobe Commerce e Magenti Open Source >=2.4.5 &lt;2.4.6) - Risolve il problema a causa del quale i prodotti non sono visibili sul fronte quando l’impostazione &quot;Consenti tutti i prodotti per pagina&quot; è impostata su Sì.
* **ACSD-48293** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corregge il problema per cui i prodotti compositi esauriscono le scorte quando i prodotti secondari venduti vengono restituiti alle scorte.
* **ACSD-47520** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui i clienti perdono punti di premio quando viene creata una nota di credito.
* **ACSD-48044** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.4) - Risolve il problema che si verificava quando l’applicazione di più carte regalo a un singolo ordine con spedizione multipla impediva l’esecuzione di ordini.
* **ACSD-48300** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui non è possibile creare un ritorno se il prodotto configurabile viene rimosso.
* **ACSD-47910** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema degli ordini mancanti, delle fatture, delle spedizioni e delle note di credito nelle rispettive griglie di entità.
* **ACSD-47292** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Risolve il problema per cui i prodotti bundle esauriti non sono disponibili nella risposta di GraphQL se l&#39;opzione &quot;show out-of-stock products&quot; è impostata su Sì.
* **ACSD-48234** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema in cui il risultato della ricerca nel catalogo mostra un conteggio errato degli articoli della categoria quando l&#39;opzione &quot;mostra esaurito&quot; è abilitata.
* **ACSD-48313** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.5) - Risolve il problema in cui la colonna &quot;configurable_variation&quot; non viene analizzata se il valore dell&#39;attributo contiene una virgola. Lo stesso algoritmo di analisi viene utilizzato per &quot;add_attributes&quot;.
* **ACSD-48627** (per Adobe Commerce e Magenti Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui il prodotto configurabile esaurito causa un errore durante l’invio di una richiesta GraphQL per ottenere i dettagli del carrello.
* Patch aggiornata: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Risolve il problema per cui gli URL SEO-friendly non vengono generati per i prodotti che hanno *url_key* attributi ignorati a livello di visualizzazione archivio.
* **ACSD-46865** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui la griglia Spedizione e Nota di credito non viene compilata quando l&#39;indicizzazione asincrona è abilitata.
* **ACSD-47004** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema in cui l&#39;IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.
* **ACSD-47803** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema per cui i campioni di prodotto configurabili esauriti vengono visualizzati come disponibili.
* **ACSD-47137** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Migliora la velocità di caricamento della raccolta immagini quando la cartella pub/media è molto grande.
* **ACSD-46770** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui le e-mail dell’ordine di amministrazione vengono inviate anche quando il *Conferma ordine e-mail* è deselezionato.
* **ACSD-47955** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui GraphQL non visualizza correttamente lo sconto del carrello.
* **ACSD-46617** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema in cui la variabile *Procedi al pagamento* il pulsante è disabilitato anche se il subtotale è maggiore del *Importo minimo ordine*.
* **ACSD-47079** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Risolve il problema per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei sottoprodotti cambia tramite REST API POST /rest/V1/inventory/source-items.
* **ACSD-47336** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Correzioni *Qualcosa è andato storto.* errore durante l’eliminazione delle notifiche nell’amministrazione Commerce.
* **ACSD-47559** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema a causa del quale l’area Anteprima modello e-mail non è completamente visibile.
* **ACSD-47920** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui gli ordini possono essere inseriti tramite l’API Rest come utente ospite anche quando il *Consenti estrazione guest* è disattivato.
* Patch sostituite: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema che impediva ad un amministratore con accesso limitato a un ambito specifico di eliminare le revisioni dei prodotti.
* **ACSD-47107** (per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5) - Corregge il problema in cui lo sconto Regola prezzo catalogo viene applicato alle opzioni di prodotto personalizzate.
* **ACSD-47232** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui i coupon con condizioni di peso totale non possono essere applicati nell’amministratore.
* **ACSD-46519** (per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.6) - Risolve il problema in cui la richiesta categoryList di GraphQL restituisce un product_count errato per una categoria di ancoraggio.
* **ACSD-47027** (per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.6) - Corregge una richiesta lenta updateCompanyRole GraphQL .
* **ACSD-47666** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema in cui la funzione di filtro non funziona in Amministratore > Sistema > Autorizzazioni > Ruoli utente > un ruolo > Griglia Utenti ruolo.
* **ACSD-47497** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema a causa del quale la scheda Servizi non è visibile nella configurazione in Admin.
* Patch aggiornata: ACSD-47743.
* Patch sostituite: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.3) - Corregge il _Tentativo di accedere all&#39;offset della matrice sul valore di tipo bool_ errore durante l&#39;accesso a determinati percorsi di categoria non esistenti per i prodotti noti su PHP 7.4.
* **ACSD-47332** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema in cui il cron non riesce con un errore che viene segnalato solo quando è in esecuzione tra le 00:00 e le 00:59 UTC.
* **ACSD-47280** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema che impedisce il corretto funzionamento della disattivazione della funzione di catalogo condiviso su un ambito specifico.
* **ACSD-47106** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui un valore non può essere salvato in un nuovo attributo personalizzato in una pagina di creazione di un&#39;azienda.
* Patch aggiornata: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.6) - Risolve il problema per cui un utente riceve un errore quando assegna un numero elevato di sorgenti di prodotto.
* **ACSD-46856** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Migliora le prestazioni aggiornando i prezzi tramite Sistema > Configurazione > Importa > Prezzi avanzati.
* **ACSD-46541** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.4) - Risolve il problema per cui un utente amministratore non può creare una nota di credito se un elemento dell&#39;ordine viene eliminato.
* **ACSD-46581** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui il totale fiscale stimato non viene aggiornato dopo aver selezionato un paese nel carrello.
* **ACSD-46618** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema in cui il widget elenco prodotti mostra prezzi memorizzati nella cache errati per un cliente connesso.
* **ACSD-46674** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema per cui le opzioni personalizzate di un tipo di immagine vengono visualizzate come HTML nelle e-mail dei clienti.
* **ACSD-46988** (per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema in cui la richiesta API &quot;currency&quot; di GraphQL restituisce valori NULL per una valuta personalizzata.
* **ACSD-47076** (per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5) - Corregge il problema per cui i video Vimeo non possono essere riprodotti sulla vetrina.
* **ACSD-45071** (per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4) - Corregge il problema per cui l&#39;origine predefinita viene aggiunta al prodotto durante l&#39;importazione.
* **AC-3023** (per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6) - Aggiorna lo schema DHL alla versione più recente 10.0.
* Patch aggiornate: MDVA-42584.
* Patch sostituite: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema per cui un utente ottiene uno stato di ordine errato quando viene rimborsato utilizzando il credito del negozio.
* **ACSD-46703** (*per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6*): risolve il problema che impediva il trascinamento e il rilascio di opzioni personalizzate in una pagina di modifica del prodotto.
* **ACSD-44851** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6*): risolve il problema che impediva l&#39;apertura o l&#39;espansione di una categoria con sottocategorie.
* **ACSD-46815** (*per Adobe Commerce e Magenti Open Source >=2.4.5 &lt;2.4.6*) - Corregge il problema per cui la richiesta di albero di categoria è limitata a 20 categorie.
* **ACSD-45675** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.6*): risolve il problema per cui l&#39;esportazione del prodotto utilizza i nomi delle categorie dal *Visualizzazione store predefinita* ambito di applicazione.
* **ACSD-46869** (*per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.6*) - Corregge il problema per cui un prodotto configurabile in un carrello non viene aggiornato tramite un *API REST di PUT* richiesta senza modificare la quantità del prodotto.
* **MDVA-42768-V2** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui il prodotto configurabile visualizza il prezzo regolare come *0* quando *Visualizzazione esaurita* è *Sì*.
* Patch aggiornate: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleta: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui la richiesta di albero di categoria è limitata a 20 categorie.
* **ACSD-45781** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.2*): risolve il problema di visualizzazione del campo di ricerca iniziale dello store su dispositivi mobili.
* **ACSD-46192** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;2.4.5*) - Risolve il problema dell&#39;utilizzo di `async/bulk/V1/configurable-products/bySku/options` punto finale.
* **ACSD-46404** (*per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.5*) - Corregge il problema per cui un utente amministratore non può accedere dopo l&#39;aggiornamento alla versione 2.4.4.
* Patch aggiornate: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui una mutazione del prodotto GraphQL per uno specifico archivio restituisce tutte le varianti configurabili, incluse quelle non assegnate allo store richiesto.
* **ACSD-46146** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.6*): risolve il problema per cui vengono inviate due e-mail di conferma dell’ordine dopo l’invio di un ordine dall’amministratore.
* **ACSD-45255** (*per Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corregge un&#39;eccezione nella pagina Rapporto Stock bassi per un utente amministratore con restrizioni.
* **ACSD-45488** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.6*) - Corregge il problema per cui un prodotto configurabile con più origini non viene restituito automaticamente in In Stock .
* **ACSD-45754** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui i punti premio non vengono aggiunti dopo aver applicato un coupon al carrello.
* **ACSD-45849** (*per Adobe Commerce >=2.4.3 &lt;2.4.4*): risolve il problema della perdita dei metadati video dopo l&#39;applicazione di un aggiornamento di staging.
* **ACSD-45257** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.4*): risolve il problema per cui GraphQL non visualizza correttamente uno sconto del carrello.
* **ACSD-44938** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.4*) - Risolve il problema in cui `VAT_ID` non può essere applicata in una richiesta GraphQL per un utente guest.
* Patch aggiornate: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.4.4*): risolve il problema in cui la quantità di azioni per un prodotto virtuale viene calcolata in modo errato dopo la creazione di una nota di credito.
* **ACSD-43887** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema che causava la visualizzazione di dettagli errati nella pagina Pagamento per il pagamento in pagamento quando sono abilitati Ordini di acquisto per le società.
* **ACSD-45143** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.5*) - Risolve il problema in cui la `setShippingAddressesOnCart` la mutazione non consente di impostare il codice di area numerica come *regione*.
* **ACSD-44591** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.6*) - Corregge l&#39;errore che si verifica quando un ordine viene inserito senza conferma CAPTCHA.
* **ACSD-45520** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.6*): risolve il problema per cui le opzioni di campione non vengono preselezionate nella pagina dei dettagli del prodotto quando un utente modifica i prodotti configurabili dal carrello.
* **ACSD-45169** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.6*) - Risolve il problema in cui [!DNL Visual Merchandiser] non visualizza il magazzino e il prezzo corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento dello staging.
* **ACSD-45424** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.6*) - Corregge il problema in cui viene creata una compensazione errata della prenotazione dopo un rimborso parziale (nota di credito).
* **MDVA-42807** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui il segno di valuta personalizzato non viene visualizzato sul lato store.
* Patch aggiornate: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui i totali degli ordini nel rapporto Ordini non vengono calcolati correttamente per l’utente con restrizioni di amministrazione.
* **MDVA-44940** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge l&#39;errore SQL che si verifica durante il salvataggio della categoria dall&#39;amministratore.
* **MDVA-44562** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.2-p2*) - Corregge il problema per cui l&#39;ID store non predefinito per gli elementi del preventivo viene sostituito dall&#39;ID store predefinito, nonostante la richiesta GraphQL proveniente dalla vista store non predefinita.
* **MDVA-43167** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui l&#39;azione di massa della griglia dell&#39;ordine di amministrazione non si applica per più pagine quando l&#39;utente amministratore seleziona tutti gli ordini.
* **MDVA-44044** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.2-p2*): risolve il problema di mancata visualizzazione di un prodotto nella pagina della categoria dopo l’assegnazione a un nuovo sito web.
* **MDVA-42509** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;2.4.4*) - Corregge il problema per cui non era possibile caricare un CSV per un ordine rapido con conseguente *Impossibile inviare il cookie* errore.
* Patch aggiornate: MDVA-41061, MDVA-42584.
* Prefisso per il nuovo [!DNL Quality Patches Tool] le patch verranno modificate da *MDVA* a *ACSD* a causa di modifiche interne del processo.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*): risolve il problema per cui non è possibile aggiungere un elemento aggiuntivo al carrello quando la quantità minima dell&#39;elemento è già nel carrello.
* **MDVA-44887** (*per Adobe Commerce e Magenti Open Source >=2.4.4 &lt;2.4.5*) - Corregge il *Errore di sintassi non rilevato: Token &#39;const&#39; imprevisto* nel pannello Amministrazione.
* **MDVA-43718** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Correzioni *Il consumatore non è autorizzato ad accedere a %resources.* errore visualizzato quando si accede a un catalogo condiviso da un&#39;integrazione personalizzata.
* **MDVA-44660** (*per Adobe Commerce e Magenti Open Source >=2.4.2-p1 &lt;2.4.5*) - Corregge il problema in cui il carattere accento grave ``` ` ``` non può essere utilizzato per il nome e il cognome di un cliente.
* **MDVA-40896** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge il *Errore: TypeError: Argomento 3 passato al Magento* errore nell’API di massa del prodotto asincrono.
* **MDVA-38559** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.3*) - Corregge il */V1/customer/search API* errore per i clienti con più di un abbonamento.
* **MDVA-44533** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;2.4.4*): risolve il problema in cui lo sconto viene applicato erroneamente a un bundle di prodotti figlio.
* Patch aggiornate: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*): risolve il problema in cui i prodotti *Non visibile individualmente* vengono comunque visualizzati in Risultati ricerca avanzata catalogo.
* **MDVA-44100** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*): risolve il problema in cui tutti i FPT vengono assegnati all&#39;ultimo prodotto nel carrello e reimpostati per altri prodotti.
* **MDVA-43605** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui i dati dell&#39;ordine restituiscono valori negativi per i totali delle righe quando si utilizza l&#39;API Rest.
* **MDVA-43102** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui la quantità vendibile non viene aggiornata correttamente quando un rimborso viene effettuato tramite API REST.
* **MDVA-43178** (*per Adobe Commerce e Magenti Open Source >=2.4.3-p2 &lt;2.4.5*) - Corregge il problema per cui un token cliente per un archivio personalizzato non può essere recuperato in GraphQL.
* **MDVA-43859** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema in cui l&#39;errore *Nessuna entità con customerId =* viene registrato quando un cliente eliminato tenta di accedere.
* **MDVA-44147** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*): risolve il problema per cui una richiesta GraphQL non restituisce elenchi di richieste di acquisto.
* **MDVA-44505** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.3*) - Corregge i problemi in cui l&#39;applicazione dei punti premio GraphQL non aggiorna il totale complessivo e in cui il credito store viene applicato più volte durante il posizionamento dell&#39;ordine.
* Patch aggiornate: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.3*): risolve il problema in cui la regola di prodotto correlata funziona solo quando il segmento del cliente è impostato su *Tutto*.
* **MDVA-39605** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il valore TTL della cache Redis (data di scadenza) è errato.
* **MDVA-43862** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;2.4.5*): risolve il problema per cui il cliente non può aggiornare gli articoli del carrello a causa di un GraphQL *Modifica UpdateCartItems* errore.
* **MDVA-43824** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.7-p3 | | >=2.4.1 &lt;2.4.5*): risolve il problema in cui viene visualizzato un errore in caso di annullamento di ordini con uno sconto.
* **MDVA-43451** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema in cui l&#39;errore *Impossibile trovare il negozio richiesto. Verifica lo store e riprova.* viene visualizzato durante la configurazione di un catalogo condiviso per un sito Web specifico.
* **MDVA-43491** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.4.5*): risolve il problema per cui l&#39;etichetta dell&#39;immagine di base non viene aggiornata quando si importano prodotti per un sito web multi-store.
* **MDVA-43601** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema dei trigger mancanti dopo la reindicizzazione completa.
* **MDVA-42046** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;=2.3.5-p2 | | >=2.4.0 &lt;2.4.5*): risolve il problema in cui un valore errato viene assegnato a un attributo di prodotto con un campo di immissione data durante l&#39;aggiornamento di un prodotto.
* **MDVA-43935** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5*): risolve il problema per cui il prodotto Upselling viene visualizzato due volte.
* **MDVA-44188** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*) - Risolve il problema relativo alle e-mail emesse dal sistema con `.-` gli indirizzi in non vengono inviati.
* **MDVA-42283** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il formato data-ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali francesi non è valido.
* Patch aggiornate: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Aggiunti metadati delle patch per il [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.3.6*): risolve il problema per cui l&#39;utente è in grado di modificare l&#39;ora di inizio di un aggiornamento pianificato attivo.
* **MDVA-42410** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui nei rapporti sulle cedole viene visualizzata solo la valuta di base predefinita.
* **MDVA-41136** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui la data di scadenza del `mage-cache-sessid` non viene esteso, con conseguente pulizia dei dati del cliente.
* **MDVA-39993** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;=2.3.7-p2 | | >=2.4.0 &lt;2.4.4*): risolve il problema a causa del quale le modifiche all’inventario effettuate tramite API non si riflettono sulla pagina del prodotto sul fronte.
* **MDVA-42855** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui un nuovo indirizzo cliente non viene salvato nella rubrica durante il pagamento.
* **MDVA-42645** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*): risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.
* **MDVA-43414** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corregge l&#39;errore fatale PHP che si verifica quando si esegue il `inventory.reservations.updateSalabilityStatus` consumatore in coda su SKU numerici.
* **MDVA-41628** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.5*): risolve il problema per cui gli utenti amministratori con restrizioni esistenti possono accedere alle nuove risorse quando vengono aggiunti nuovi moduli.
* **MDVA-43348** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema in cui la richiesta GraphQL della carta regalo mostra un errore se `gift_card_options` contain *uid*.
* **MDVA-39546** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui la data di inizio dell&#39;aggiornamento dell&#39;area di gestione temporanea può essere impostata su una data precedente alla data corrente durante la modifica.
* **MDVA-42950** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*): risolve il problema per cui i video non vengono riprodotti nella pagina del prodotto.
* **MDVA-42689** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema in cui Adobe Commerce genera un *Violazione del vincolo di integrità* errore durante l&#39;aggiornamento delle categorie di prodotti durante l&#39;importazione.
* **MDVA-41229** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*): risolve il problema per cui le immagini disponibili sul backend non vengono visualizzate sul front-end dopo l’importazione di prodotti configurabili.
* **MDVA-43731** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Risolve il problema in cui *Sinonimi di ricerca* non funziona più quando viene aggiunto il valore in *Termini minimi da abbinare*.
* **MDVA-43232** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.5*) - Risolve il problema relativo all&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser] per Prezzo speciale in basso/in alto causa un errore durante il salvataggio della categoria.
* **MDVA-43726** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui la regola del prezzo del catalogo basata sulla corrispondenza dell&#39;attributo a livello di archivio non viene applicata dopo la reindicizzazione parziale.
* Patch aggiornate: MDVA-36464, MDVA-37478, MDVA-38608.
* Aggiunti metadati delle patch per il [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui gli attributi del prezzo del prodotto non possono essere aggiornati per un sito web specifico tramite API REST.
* **MDVA-41350** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*): risolve il problema in cui viene generata un&#39;eccezione quando un utente amministratore con accesso limitato aggiunge un prodotto al di fuori del proprio ambito di ruolo da SKU in un ordine.
* **MDVA-42269** (*per Adobe Commerce e Magenti Open Source >=2.4.3-p1 &lt;2.4.5*) - Corregge il problema per cui un utente amministratore non può accedere all&#39;amministratore a causa del *TypeError: strtotime() prevede che il parametro 1 sia stringa, dato null* errore.
* **MDVA-40830** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il credito store viene applicato più volte durante il posizionamento dell&#39;ordine.
* **MDVA-42237** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui un prezzo speciale di prodotto configurabile non viene aggiornato dopo modifiche nel prezzo del sottoprodotto.
* **MDVA-42520** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema in cui l&#39;aliquota d&#39;imposta viene applicata due volte se *Attiva scambi transfrontalieri* viene utilizzato.
* Patch aggiornate: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleta: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*per Adobe Commerce e Magenti Open Source >=2.3.2 &lt;2.4.5*) - Corregge il problema per cui l&#39;aggiornamento dell&#39;attributo di massa crea una riscrittura URL per l&#39;archivio predefinito solo dopo la modifica *Visibilità del prodotto*.
* **MDVA-43091** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui l&#39;ordine di un prodotto bundle dall&#39;amministratore nel back-end restituisce l&#39;errore *Impossibile utilizzare la quantità decimale per questo prodotto*.
* **MDVA-40816** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui le regole del prodotto correlate mostrano prodotti provenienti da categorie non definite nelle condizioni della regola.
* **MDVA-41305** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la mutazione GraphQL non restituisce opzioni di prodotto configurabili dopo l&#39;aggiunta all&#39;elenco dei desideri.
* **MDVA-39181** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui le regole del prodotto correlate mostrano prodotti provenienti da categorie non definite nelle condizioni della regola.
* **MDVA-42584** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*): risolve il problema per cui lo stato di stock configurabile nel backend non viene aggiornato dopo la modifica dello stato di quantità e stock tramite Importazione o API.
* **MDVA-40175** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.3*) - Risolve il problema in cui *Fare clic per modificare il metodo di spedizione* non mostra pulsanti di scelta per selezionare i metodi di spedizione nell&#39;amministratore durante il riordino.
* **MDVA-42768** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il prezzo normale del prodotto configurabile viene visualizzato come 0 quando *Visualizzazione esaurita* Sì.
* **MDVA-43201** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema in cui si verifica un errore nell&#39;accesso del cliente quando si utilizza l&#39;attributo DOB con determinate impostazioni internazionali.
* Patch aggiornate: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.5*): risolve il problema che causava il mancato funzionamento dei filtri data quando il fuso orario di Adobe Commerce è diverso da quello dell’ambiente locale.
* **MDVA-42657** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5*): risolve il problema che impediva all&#39;utente amministratore di selezionare categorie nelle condizioni del segmento del cliente.
* **MDVA-42806** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema in cui un *Nuova registrazione aziendale* L’e-mail viene inviata ogni volta che un’azienda esistente viene aggiornata tramite API REST.
* **MDVA-37984** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.5*) - Risolve il problema in cui la [!DNL Visual Merchandiser] *Confronta prodotto per regola* La funzionalità non filtra correttamente i prodotti con aggiornamenti di staging.
* **MDVA-40488** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella gamma di prezzi corretta.
* **MDVA-42507** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui la cache a pagina intera viene pulita dopo l&#39;applicazione dell&#39;aggiornamento di staging per la regola del carrello.
* **MDVA-39163** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.4.5*) - Corregge il problema a causa del quale i metodi di spedizione non sono disponibili quando un nuovo utente viene registrato e i prodotti nel carrello provengono dalla sessione guest.
* **MDVA-38626** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;2.4.5*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di effettuare un ordine sul backend utilizzando [!DNL PayPal Payflow Pro] pagamento.
* **MDVA-38666** (*per Adobe Commerce e Magenti Open Source >=2.3.2 &lt;2.3.6*): risolve il problema per cui l&#39;utente amministratore non è in grado di modificare le opzioni di prodotto configurabili nel carrello del cliente.
* **MDVA-38526** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di accedere al [!DNL Site-Wide Analysis tool].
* Patch aggiornate: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui gli utenti ottengono l&#39;errore 500 dopo aver impostato il *mage-messages* cookie se esiste già, ma non sono presenti nuovi messaggi.
* **MDVA-41139** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui i prodotti configurabili non sono disponibili dopo l’importazione del prodotto quando qty=0 di un prodotto semplice per una delle sue sorgenti.
* **MDVA-42326** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*): risolve il problema per cui i clienti ottengono un errore in caso di pagamento dopo un timeout di sessione anche se il carrello acquisti permanente è abilitato.
* **MDVA-42341** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema in cui la `categoryList` La query GraphQL non filtra i risultati se una richiesta ha l’intestazione Store.
* **MDVA-38393** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui le regole del catalogo smettono di funzionare per un prodotto configurabile se il suo prodotto semplice viene rinominato.
* **MDVA-39153** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui l&#39;importo di uno sconto viene calcolato in modo errato durante il riordino in Admin.
* Patch aggiornate: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.3*): risolve il problema per cui gli utenti amministratori non possono accedere alla griglia del cliente dopo l’eliminazione del sito web.
* **MDVA-40311** (*per Adobe Commerce e Magenti Open Source >=2.4.2-p2 &lt;2.4.4*) - Corregge il problema per cui gli utenti amministratori ricevono il messaggio di errore *Protezione o chiave del modulo non valida. Aggiorna la pagina* dopo l&#39;accesso all&#39;amministratore se il percorso dell&#39;amministratore personalizzato è configurato e la chiave segreta è abilitata.
* **MDVA-41631** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui gli utenti ottengono un errore quando tentano di recuperare le informazioni sull&#39;ordine senza un *telefono* tramite GraphQL.
* **MDVA-27239** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.3.6*): risolve il problema di mancata visualizzazione dei prodotti di cross-selling.
* Patch aggiornate: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.4.4*) - Corregge il problema dei prodotti mancanti sul fronte durante la reindicizzazione.
* **MDVA-40120** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui l&#39;ordinamento GraphQL tramite DESC/ASC non funziona con prodotti che hanno la stessa rilevanza o lo stesso prezzo.
* **MDVA-41399** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui gli utenti amministratori non possono accedere al *Gestisci carrello acquisti* se un cliente aggiunge un prodotto all’elenco dei desideri.
* **MDVA-40609** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema dell&#39;assenza di dati sui prodotti disattivati nel `cataloginventory_stock_status` tabella indice, visualizzazione di quantità di prodotto disattivate non corrette.
* **MDVA-39031** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.4*): risolve il problema per cui l’aggiunta di un prodotto al carrello tramite GraphQL è possibile anche se non viene assegnato al sito web di destinazione.
* **MDVA-41597** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui gli utenti ricevono un errore quando aggiungono più di un prodotto configurabile al carrello utilizzando GraphQL.
* **MDVA-27456** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.3.7*) - Corregge il problema per cui gli utenti ottengono un errore durante il tentativo di caricamento [!DNL Swagger].
* **MDVA-32776** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui lo stato delle scorte non viene aggiornato quando un ordine viene effettuato ma non spedito.
* **MDVA-30862** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.0*) - Corregge il problema relativo alla data di ordine errata nella fattura di PDF stampata.
* È stata migliorata la pagina dell&#39;indice per il [!DNL Quality Patch Tool]. È stata aggiunta una ricerca e un filtro utili per [!DNL quality patches] all’ultima versione dello strumento.
* Patch aggiornate: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*): risolve il problema per cui è impossibile creare un nuovo aggiornamento o modificare un aggiornamento pianificato esistente per un prodotto se la data di fine è stata rimossa in precedenza.
* **MDVA-41046** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*): risolve il problema a causa del quale sono disponibili prodotti semplici con opzioni personalizzate per l’assegnazione a prodotti configurabili/raggruppati.
* **MDVA-40545** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*): risolve il problema per cui veniva recuperato solo il primo nodo per una pagina anche se c&#39;erano più nodi per la stessa pagina.
* **MDVA-41164** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3-p1*): risolve il problema per cui un utente amministratore non è in grado di salvare o modificare un&#39;azienda con un attributo cliente personalizzato di tipo file o immagine.
* **MDVA-39229** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema che causa la visualizzazione del seguente errore dopo l&#39;aggiornamento della regola del catalogo Ora di inizio dell&#39;aggiornamento dell&#39;staging: *Errore del processo Cron staging_sync_entity_period: Impossibile eliminare l&#39;aggiornamento attivo.*
* **MDVA-40619** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui le modifiche alla gerarchia delle pagine CMS causano un errore 500 quando si tenta di eseguire la modifica in linea su una pagina CMS.
* **MDVA-41061** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*): risolve il problema per cui lo stato delle scorte viene reimpostato su salabile quando un prodotto viene salvato dall&#39;amministratore.
* **MDVA-31763** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*): risolve il problema per cui le regole del prezzo di catalogo vengono ripristinate (o non applicate) fino alla reindicizzazione manuale.
* **MDVA-37748** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*): risolve il problema in cui una query GraphQL restituisce prodotti non assegnati a un catalogo condiviso.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui le fatture parziali per lo stesso ordine non possono essere create simultaneamente tramite API REST.
* **MDVA-40101** (*per Adobe Commerce e Magenti Open Source >=2.3.2 &lt;2.4.0*) - Corregge il problema per cui gli elementi non vengono rimossi dal mini carrello dopo il corretto posizionamento dell&#39;ordine utilizzando [!DNL PayPal Express] Pagamento.
* **MDVA-40401** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui il valore di utilizzo del coupon cambia anche se l&#39;ordine non riesce.
* **MDVA-40537** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;=2.4.0-p1*) - Corregge il problema per cui gli utenti ottengono un errore durante la creazione di una visualizzazione store se esistono diverse pagine CMS con la stessa chiave URL.
* **MDVA-37725** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corregge il problema per cui le e-mail di ordine asincrono inviate da siti web non predefiniti contengono URL di logo dal sito web predefinito.
* **MDVA-39482** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.7-p2 | | >=2.4.1 &lt;2.4.4*): risolve il problema per cui un prodotto esaurisce le scorte se importato con una quantità &quot;0&quot; quando gli ordini precedenti sono abilitati.
* **MDVA-40435** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;2.4.4*): risolve il problema con uno sconto errato sui prodotti bundle con prezzi dinamici se applicati tramite GraphQL.
* **MC-42528** (*per Adobe Commerce e Magenti Open Source >=2.4.3 &lt;=2.4.3-p1*) - Risolve il problema in cui la `categoryList` La query GraphQL restituisce categorie assegnate e non assegnate.
* **MDVA-29400** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema degli ordini duplicati inseriti con [!DNL PayPal Express Checkout].
* **MDVA-26005** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corregge il problema per cui è impossibile selezionare una categoria in un albero di categorie per le condizioni della regola di prezzo del carrello.
* **MDVA-25631** (*per Adobe Commerce e Magenti Open Source >=2.3.3 &lt;=2.3.5-p2*): migliora le prestazioni per modificare e salvare i segmenti di clienti che contengono un gran numero di clienti.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui le query di ricerca GraphQL non vengono visualizzate nei termini di ricerca più comuni nell&#39;amministratore.
* **MDVA-40601** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corregge il problema per cui gli utenti ottengono un errore quando tentano di ottenere informazioni sulla categoria modificata da un aggiornamento pianificato tramite GraphQL.
* **MDVA-37234** (*per Adobe Commerce e Magenti Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corregge il problema per cui l’aggiunta di un elemento al carrello più volte (richiesta parallela) per lo stesso SKU crea un elemento duplicato per lo stesso ID carrello.
* **MDVA-33606** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corregge il problema per cui gli utenti ottengono un *Violazione univoca dei vincoli* errore durante il salvataggio di una pagina CMS assegnata a una gerarchia.
* **MDVA-31590** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corregge il problema per cui gli utenti non sono in grado di aggiornare gli attributi in blocco utilizzando le code asincrone di MySQL.
* **MDVA-36309** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;=2.4.2-p2*): risolve il problema di lentezza nella ricerca dei prodotti in base agli attributi nelle griglie di amministrazione.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui la fattura con FPT mostra un totale complessivo errato quando l&#39;ordine viene pagato dal credito del negozio.
* **MDVA-37364** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;=2.4.3*): risolve il problema per cui l&#39;attributo del cliente personalizzato di tipo data interrompe l&#39;interfaccia utente della griglia del cliente.
* **MDVA-39195** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;=2.4.2-p2*) - Risolve il problema in cui *Aggiungi al carrello* pulsante non attivo nella pagina della categoria quando è abilitato il reindirizzamento al carrello.
* **MDVA-37115** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;=2.4.2-p2*) - Risolve il problema in cui un *Solo 0 a sinistra* nella pagina di prodotto configurabile viene visualizzato un avviso.
* **MDVA-39521** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.4*): risolve il problema per cui l&#39;utente non è in grado di impostare gli indirizzi di spedizione sul carrello con un numero di telefono vuoto tramite GraphQL.
* **MDVA-39384** (*per Adobe Commerce e Magenti Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*): risolve il problema in cui l&#39;attributo cliente personalizzato per un utente aziendale non viene salvato.
* **MDVA-39043** (*per Adobe Commerce e Magenti Open Source >=2.3.4 &lt;=2.4.3*) - Corregge il problema per cui l&#39;utente amministratore con accesso limitato riceve un errore quando cerca di aggiungere il *Prodotti* alla pagina CMS.
* **MDVA-39966** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema relativo alla distribuzione di impostazioni internazionali non corrette.
* **MDVA-38852** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corregge il problema per cui l&#39;inventario del catalogo per progettazione blocca le tabelle per gli aggiornamenti che riducono notevolmente le prestazioni in casi con più ordini paralleli.
* **MDVA-39986** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.3*): risolve il problema per cui l’utente non è in grado di effettuare un ordine in Admin on MacOS utilizzando il browser Safari.
* **MDVA-38447** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.4*) - Risolve due problemi: se *Non visibile individualmente* i prodotti figlio configurabili vengono restituiti nella risposta di GraphQL e ottimizzano la query MySQL per la query dei prodotti GraphQL con filtro categoria.
* **MDVA-40134** (*per Adobe Commerce e Magenti Open Source >=2.4.2 &lt;2.4.3*): risolve il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato.
* **MDVA-39935** (*per Adobe Commerce e Magenti Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui GraphQL restituisce prodotti figlio configurabili disabilitati a livello di sito web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;2.4.4*) - Risolve il problema in cui la *Chiamata a una funzione membro getId()* viene visualizzato un errore nella pagina dei dettagli dell&#39;ordine in Admin.
* **MDVA-34948** (*per Adobe Commerce e Magenti Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema con le query a lungo termine, come `GET_LOCK`.
* **MDVA-39305** (*per Adobe Commerce e Magenti Open Source >=2.4.0 &lt;=2.4.2-p1*) - Corregge il problema per cui i clienti registrati non sono in grado di accedere con Google ReCaptcha abilitato.
* **MDVA-37897** (*per Adobe Commerce e Magenti Open Source >=2.3.0 &lt;2.4.4*): risolve il problema con un reindirizzamento errato quando un cliente tenta di aggiungere prodotti con opzioni dal widget Visualizzato di recente.

## v1.1.0 {#v1-1-0}

* Sono state introdotte categorie di patch per migliorare l’esperienza utente e semplificare la ricerca delle patch richieste ai clienti.
* La `patches.json` è stato rinominato in `support-patches.json`.
* **MDVA-38799** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*): risolve il problema per cui i prodotti scaricabili non venivano salvati dopo la creazione di un aggiornamento di staging.
* **MDVA-37592** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): risolve il problema che si verifica quando l&#39;ordinamento in base al prezzo non funziona correttamente per i prodotti a prezzo zero assegnati al catalogo condiviso.
* **MDVA-38827** (*per Adobe Commerce >=2.3.3-p1 &lt;2.4.4*): risolve il problema per cui i clienti ricevono un messaggio e-mail di spedizione dell&#39;ordine contenente un messaggio di errore.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*per Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Corregge l&#39;errore durante il salvataggio delle pagine CMS: *L&#39;elemento con lo stesso ID PAGE_ID esiste già*.
* **MDVA-34680** (*per Adobe Commerce >=2.3.6 &lt;=2.3.7 | | >=2.4.1 &lt;2.4.3*): risolve il problema per cui i tempi di creazione dell&#39;account cliente non vengono filtrati correttamente nella griglia dei clienti.
* **MDVA-37068** (*per Adobe Commerce >=2.3.1 &lt;2.4.4*): risolve il problema in cui l&#39;aliquota fiscale errata viene visualizzata quando il carrello ha solo prodotti virtuali.
* **MDVA-38608** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui le tabelle temporanee non vengono eliminate quando la reindicizzazione non viene completata correttamente.
* **MDVA-38308** (*per Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 | | >=2.4.2 &lt;2.4.4*) - Corregge i problemi relativi all&#39;aggiunta di [!DNL Vimeo] video sui prodotti.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema per cui il cliente non viene portato alla pagina Conferma pagamento quando si utilizza il [!DNL Paypal Payment Advanced] metodo .
* **MDVA-37082** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*): risolve il problema che si verifica quando si salvano le scorte personalizzate di prodotti raggruppati, causando la visualizzazione del prodotto come non disponibile sul fronte.
* **MDVA-36572** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corregge il problema che si verificava quando gli aggiornamenti di Nota di credito non causavano più aggiornamenti duplicati della prenotazione dei prodotti nel database.
* **MDVA-38132** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*): risolve il problema quando il pannello di amministrazione non è raggiungibile a causa di un *troppi reindirizzamenti* errore.
* **MDVA-38270** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corregge il problema relativo alle informazioni mancanti sulla carta regalo nel totale dell&#39;ordine in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*per Adobe Commerce >=2.4.2 &lt;=2.4.4*): risolve il problema relativo all’aggiunta di un prodotto configurabile al carrello tramite GraphQL quando l’ID del sito web non coincide con l’ID dello store.
* **MDVA-36832** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): risolve il problema della duplicazione delle immagini sulle pagine quando la larghezza di visualizzazione è di 768 px.
* **MDVA-37874** (*per Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Risolve il problema in cui *Importo fisso dello sconto per il carrello intero* è applicato in modo errato a un prodotto bundle contenente più di un&#39;opzione.
* **MDVA-37913** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*): risolve il problema a causa del quale i collegamenti scaricabili spariscono se il prodotto scaricabile viene aggiornato tramite API.
* **MDVA-34330** (*per Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*): risolve il problema per cui gli ordini nella griglia Ordini non vengono filtrati in base al fuso orario dell’amministratore.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*per Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Corregge il problema per cui Adobe Commerce genera un errore durante la creazione di una fattura parziale per gli ordini inseriti con il *Pagamento in conto* metodo di pagamento tramite REST API.
* **MDVA-37362** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corregge il problema per cui i valori delle opzioni di prodotto configurabili e i valori degli attributi di variante erano vuoti nella risposta GraphQL.
* **MDVA-37288** (*per Adobe Commerce 2.4.2*) - Corregge il problema per cui i prezzi di livello errati venivano restituiti dopo la richiesta di GraphQL.
* **MDVA-37225** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*): risolve il problema di blocco del processo di caricamento durante la creazione di un ordine rapido in presenza di un valore intero negli SKU importati.
* **MDVA-37224** (*per Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corregge il problema per cui i clienti non possono pagare il preventivo negoziabile con [!DNL PayFlow Pro] con un altro prodotto nel carrello.
* **MDVA-36286** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): risolve il problema dell’interruzione dell’anteprima dei widget dei prodotti Page Builder se lo stesso SKU ha una posizione diversa nelle sottocategorie.
* **MDVA-30186** (*per Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corregge il problema per cui le opzioni attributo vengono ordinate in base al valore dell&#39;opzione invece del conteggio degli elementi attributo nella risposta di GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*per Adobe Commerce >=2.3.0 &lt;=2.4.2*): risolve il problema per cui le vecchie opzioni personalizzate rimangono dopo essere state modificate tramite API.
* **MDVA-35773** (*per Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corregge il problema di mancata visualizzazione del totale complessivo come zero sulla fattura per gli ordini con sconto del 100%.
* **MDVA-36833** (*per Adobe Commerce 2.4.2*): risolve il problema con i risultati della ricerca che mostrano un numero casuale di prodotti per pagina dopo l’esclusione di alcuni prodotti dal catalogo condiviso.
* **MDVA-37182** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corregge il problema di ottenere risultati di ricerca errati in entrambi [!DNL Elasticsearch] versione 6 e 7.
* **MDVA-36253** (*per Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Corregge il problema in cui il subtotale errato viene visualizzato nel mini carrello dopo l&#39;eliminazione dell&#39;elemento.
* **MDVA-36853** (*per Adobe Commerce 2.4.2*): risolve il problema senza che vengano visualizzate immagini durante il caricamento di grandi raccolte di contenuti multimediali.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*per Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Corregge il problema dei prodotti bundle mancanti sulle pagine delle categorie.
* **MDVA-36615** (*per Adobe Commerce 2.4.2*) - Corregge il problema relativo al conteggio dei prodotti errato nella griglia dei prodotti Admin.
* **MDVA-36464** (*per Adobe Commerce >=2.4.0 &lt;=2.4.2*): risolve il problema di mancato funzionamento della configurazione della notifica e-mail a livello di store-view.
* **MDVA-36138** (*per Adobe Commerce ^2.3.2*) - Corregge il problema in cui il prezzo di spedizione non viene corretto e il prezzo di spedizione completo viene mostrato ai clienti se non tutti gli articoli nel carrello soddisfano la regola del carrello di spedizione gratuita.
* **MDVA-36424** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 | | >=2.0.0 &lt;2.2.0*): risolve il problema a causa del quale le immagini multimediali collegate agli elementi del generatore di pagine scompaiono quando il contenuto viene modificato ripetutamente se l’URL di base del back-end è diverso dall’URL di base della vetrina.
* **MDVA-35984** (*per Adobe Commerce ^2.4.0*): risolve il problema relativo alla quantità di prodotto errata e alla quantità vendibile dopo la creazione di più spedizioni simultanee per lo stesso prodotto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Questo risolve il problema per cui la query GraphQL non viene memorizzata nella cache utilizzando il tag cache della categoria.
* **MDVA-33168** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*): risolve il problema durante l&#39;aggiornamento di un attributo di prodotto tramite API, tutti gli altri attributi vengono modificati in un valore vuoto.
* **MDVA-19640** (*per Adobe Commerce >=2.3.0*) - Risolve il problema in cui [!DNL Advanced Reporting] non visualizza dati.
* **MDVA-11189** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Risolve il problema che si verificava dopo l’importazione di un file CSV per aggiornare le scorte di prodotto, ovvero le righe dal `cataloginventory_stock` la tabella è eliminata.
* **MDVA-26639** (*per Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corregge il problema per cui, se viene creato un nuovo modello e-mail di conferma dell’ordine, gli elementi dell’ordine risultano mancanti nella e-mail dell’ordine.
* **MDVA-15546** (*per Adobe Commerce >=2.3.0*) - Risolve il problema in cui dopo la creazione di un ordine a *Column entity_id dove clausola è ambigua* viene visualizzato un errore nel registro delle eccezioni.
* **MDVA-21095** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Risolve il problema quando una query `INSERT INTO search_tmp` non termina dopo l&#39;aggiornamento del valore dell&#39;attributo di massa.
* **MDVA-23845** (*per Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): risolve il problema che impediva l’anteprima dei modelli e-mail dopo l’abilitazione della minimizzazione JavaScript.
* **MDVA-22026** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema che impediva l’importazione di prodotti da file CSV, incluse immagini da URL esterni.
* **MDVA-22383** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*): risolve il problema in cui il salvataggio di un prodotto richiede molto tempo e la pagina si interrompe.
* **MC-41359** (*per Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corregge il problema delle impostazioni errate dei parametri dei cookie SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*per Adobe Commerce 2.4.1*) - Corregge il problema in cui Page Builder genera il seguente errore: *Errore durante l&#39;avvio di Page Builder. Contatta il tuo contatto per il supporto tecnico.*
* **MDVA-35356** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla restituzione errata del credito all&#39;archivio dopo l&#39;annullamento dell&#39;ordine parzialmente fatturato.
* **MDVA-33289** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corregge il problema per cui il codice JavaScript non elaborato viene visualizzato nell&#39;interfaccia utente dell&#39;indirizzo di fatturazione durante l&#39;estrazione se [!DNL Google Tag Manager] è abilitato.
* **MDVA-35982** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*): risolve il problema per cui gli utenti amministratori limitati a un sito Web specifico non possono creare una spedizione per l&#39;ordine inserito sullo stesso sito web.
* **MDVA-35155** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*): risolve il problema per cui è impossibile acquistare un bundle product se il titolo dell&#39;opzione è stato modificato.
* **MDVA-35910** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*): risolve il problema per cui è impossibile creare un nuovo account cliente dopo aver disabilitato la funzionalità Accesso come cliente.
* **MDVA-34474** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*): risolve il problema relativo all&#39;aggiunta di un prodotto all&#39;elenco delle richieste di acquisto utilizzando l&#39;API.
* **MDVA-34591** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema con un calcolo errato dello sconto della regola del carrello per *Sconto Qtà massimo applicato a* e *Fase di Qtà Sconto (Acquista X)*.
* **MDVA-33704** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Risolve il problema in cui la *Ritiro in negozio* l&#39;opzione di spedizione non viene visualizzata, anche se configurata per essere disponibile.
* **MDVA-34928** (*per Adobe Commerce >=2.3.5 &lt;2.3.5-p2*): risolve il problema di visualizzazione indefinita del caricatore di pagina dopo la rimozione del credito del negozio dal pagamento.
* **MDVA-35254** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corregge i problemi con CAPTCHA durante l’estrazione.
* **MDVA-35569** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Risolve il problema in cui la *imposte sul prodotto fisso* Il campo non viene popolato nella risposta GraphQL quando è specificato lo stato .
* **MDVA-35847** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corregge il problema B2B a causa del quale il modulo Utenti società si interrompe se viene utilizzato un attributo cliente personalizzato.
* **MDVA-31307** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*): risolve il problema in cui sono presenti *Memoria esaurita* errori su alcune categorie a causa di problemi con la whitelist CSP dinamica per i blocchi memorizzati nella cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge l&#39;errore *in corso* stato del messaggio *completato* messaggio per il consumatore `quoteItemCleaner` dopo aver eliminato diversi prodotti.
* **MDVA-34102** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge la quantità di Scorte predefinite pari a zero per i prodotti disabilitati nelle pagine Griglia prodotto e Modifica prodotto nell’area Amministratore.
* **MDVA-35286** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*): risolve il problema in cui si verifica un errore se un cliente ha raggruppato i prodotti nel carrello e passa dall&#39;estrazione a più indirizzi al pagamento di una pagina singola.
* **MDVA-35312** (*per Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corregge il codice di risposta 500 quando una richiesta GraphQL vuota.
* **MDVA-34189** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corregge il timeout del primo byte di 503 il [!DNL Visual Merchandiser] durante il caricamento della pagina Categoria amministratore.
* **MDVA-34695** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correzioni negative `children_count` dopo l&#39;eliminazione delle categorie.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Risolve il problema in cui la *Usa valore predefinito* viene deselezionata dopo l’applicazione delle modifiche pianificate. Il problema viene visualizzato una volta che le modifiche pianificate non sono più attive.
* **MDVA-35064** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui le riscritture URL non vengono generate per i prodotti configurabili creati tramite API.
* **MDVA-34943** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema per cui l’ordine rapido memorizza in cache gli SKU immessi in precedenza.
* **MDVA-35197** (*per Adobe Commerce >=2.3.5 &lt;2.4.0*): risolve il problema in cui si verifica un errore durante l&#39;aggiunta al carrello utilizzando GraphQL se i prodotti aggiunti in precedenza non erano disponibili.
* **MDVA-34850** (*per Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corregge il problema per cui le opzioni esaurite di un prodotto configurabile non vengono visualizzate invece di essere visualizzate come scelte positive.
* **MDVA-34867** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema del mancato salvataggio dei valori per un campo condizione impostato per un aggiornamento pianificato.
* **MDVA-35092** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corregge il problema per cui gli utenti non possono aggiungere [!DNL Vimeo] video a causa di elementi obsoleti [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema per cui l’anteprima del tipo di contenuto Prodotti di Page Builder si interrompe se i prodotti corrispondenti hanno prezzi diversi per ogni sito web.
* **MDVA-32634** (*per Adobe Commerce ^2.3.1*) - Risolve il problema in cui la `url_path` della categoria assegnata a tutti gli archivi rimane invariata dopo lo spostamento della categoria nella gerarchia.
* **MDVA-33344** (*per Adobe Commerce ^2.3.0*) - Corregge il problema in cui il codice rigido è stato codificato `rma_item` al posto del valore del database viene utilizzato l’ID set di attributi predefinito dell’entità.
* **MDVA-34192** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Risolve il problema che rendeva impossibile modificare/specificare la data di nascita del cliente utilizzando il formato gg/mm/aaaa.
* **MDVA-34847** (*per Adobe Commerce ^2.3.0*) - Corregge la conversione del tipo di ID dell&#39;archivio in numero intero per la condizione SQL nelle raccolte Amministratore per l&#39;utente amministratore con autorizzazioni personalizzate.
* **MDVA-34886** (*per Adobe Commerce ^2.3.2*) - Corregge il problema per cui la ricerca non restituisce i risultati se *weight* l’attributo di prodotto è configurato come ricercabile.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Risolve il problema di [!DNL PayPal Payflow Pro] errore di pagamento con errore di formato elenco parametri di reindirizzamento.
* **MDVA-34023** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema in cui l&#39;errore *Nessuna entità con addressId* viene visualizzato in modo casuale sui browser dei visitatori.
* **MDVA-32759** (*per Adobe Commerce >=2.3.1 &lt;2.4.3 con estensione B2B*): risolve il problema relativo all&#39;eliminazione dei prezzi di livello esistenti da parte dei cataloghi condivisi.
* **MDVA-33482** (*per Adobe Commerce ^2.3.5*) - Corregge il problema per cui la generazione di una nota di accredito in base a una fattura parziale determina l&#39;imposta per l&#39;ordine totale invece dell&#39;imposta per quella fattura parziale.
* **MDVA-33393** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge l&#39;errore *Il valore countryId specificato non esiste*.
* **MDVA-33632** (*per Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fornisce una correzione in cui viene visualizzato il messaggio di eccezione *Questo prodotto è esaurito* viene ora visualizzato a un utente amministratore quando tenta di riordinare un prodotto non disponibile.
* **MDVA-34469** (*per Adobe Commerce >=2.4.1 &lt;2.4.2*): risolve il problema di errore nelle mutazioni GraphQL nel carrello di un cliente quando si utilizzano più viste store.
* **MDVA-33976** (*per Adobe Commerce >=2.3.0 &lt;2.3.7*): risolve il problema per cui il prodotto del bundle viene mostrato Out Of Stock sulla vetrina dopo aver rimosso la seconda opzione dal prodotto del bundle.
* **MDVA-33894** (*per Adobe Commerce >=2.4.0 &lt;2.4.1 con estensione B2B*) - Corregge diversi problemi relativi alla funzionalità Ordine rapido, tra cui l’aggiunta e la rimozione di più prodotti e la sensibilità alle maiuscole/minuscole degli SKU.
* **MDVA-27664** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Risolve il problema nel modulo di registrazione del cliente che causava la visualizzazione di un errore: *ERRORE - La data di nascita non deve essere maggiore di quella odierna.*
* **MDVA-33970** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema in cui c&#39;è il segno di valuta errato nella nota di accredito quando l&#39;ambito dell&#39;attributo di prezzo è impostato su sito web.
* **MDVA-33992** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema della visualizzazione errata dei prezzi speciali B2B durante il pagamento.
* **MDVA-34100** (*per Adobe Commerce >=2.3.4 &lt;2.4.2 con estensione B2B*): risolve il problema per cui non è possibile creare un account aziendale dalla pagina della struttura dell&#39;azienda.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*per Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*): risolve il problema delle immagini duplicate dopo l’importazione di un prodotto da un file CSV.
* **MDVA-33382** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge i problemi di invalidazione degli indici dopo la rimozione dei prodotti da una categoria.
* **MDVA-28511** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Risolve il problema in cui non è possibile completare l&#39;operazione [!DNL PayPal] estrazione se il campo Nome contiene alcuni caratteri (come lettere maiuscole accentate).
* **MDVA-31519** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corregge il problema dei timeout di attesa nel pagamento degli ospiti quando è in uso una regola di vendita a livello di sito.
* **MDVA-33281** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Risolve il problema in cui si verifica un errore irreversibile in `inventory:reservation:list-inconsistencies` a causa di un tipo di parametro SKU errato.
* **MDVA-24201** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*): risolve il problema per cui i prezzi non riflettono la regola del prezzo del carrello programmato fino a quando non vengono reindicizzati manualmente.
* **MDVA-32694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*): risolve il problema per cui un utente amministratore non può aggiungere un prodotto a un preventivo negoziabile se è correlato a un archivio non predefinito.
* **MDVA-33516** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Risolve il problema che causava un errore durante la modifica di un bundle di prodotto in un elenco di richieste di acquisto.
* **MDVA-33975** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge diversi problemi relativi al calcolo dei prezzi nelle richieste GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema con [!DNL PayPal] Rapporti di regolamento non disponibili in **Rapporti** > **Vendite** > **[!DNL PayPal]** Regolamento come previsto.
* **MCP-87** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*): è stato migliorato il tempo di indicizzazione per gli indici dei prodotti e delle azioni di categoria per i profili di grandi dimensioni.
* **MDVA-33106** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui le modifiche del prodotto riprogrammate vengono cancellate dopo il cron `run` viene eseguito il comando .
* **MDVA-19391** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Risolve il problema in cui `analytics_collect_data` sta generando un errore a causa di record di descrizione NULL nel `catalog_category_entity_text` tabella.
* **MDVA-20376** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema con *Nessuna entità con customerId = 1* errore nel `exception.log` per i clienti registrati dopo il posizionamento dell&#39;ordine.
* **MDVA-23764** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
* **MDVA-13203** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema in cui la *Violazione del vincolo di integrità tabella search_tmp_* viene visualizzato un errore dopo una reindicizzazione completa.
* **MDVA-23426** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*): risolve il problema per cui le e-mail di notifica inviate da Adobe Commerce contengono un corpo vuoto con il contenuto aggiunto come allegato.
* **MDVA-22150** (*per Adobe Commerce >=2.3.1 &lt;2.3.4*) - Corregge il problema per cui i clienti con un prodotto configurabile nel carrello e un coupon applicato non possono accedere se tale prodotto configurabile è disabilitato nell’amministratore.
* **MDVA-32545** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema per cui le fatture non vengono inviate automaticamente durante la creazione di ordini da parte dell&#39;amministratore.
* **MDVA-32714** (*per Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corregge il problema per cui il prezzo del gruppo di clienti non funziona nella query del prodotto GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Aggiunge il *Subtotale (Incl. Imposta)* opzione per determinare il prezzo delle condizioni della regola.
* **MDVA-31236** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*): risolve il problema per cui gli amministratori con accesso alle risorse personalizzate non sono in grado di impostare 2FA o di effettuare l&#39;accesso.
* **MDVA-30845** (*per Adobe Commerce >=2.3.5 &lt;2.3.7*) - Risolve il problema in cui la *Al momento non sono disponibili preventivi per questo ordine* viene visualizzato un errore quando non si riesce a connettersi a UPS XML/USPS/DHL e non è disponibile nessun altro metodo di spedizione.
* **MDVA-32133** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corregge il problema per cui in alcuni casi la raccolta multimediale non viene caricata da Page Builder.
* **MDVA-12304** (*per Adobe Commerce >=2.3.0*) - Aumenta il numero massimo di cookie da 50 a 200.
* **MDVA-32632** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge il problema in cui gli ordini vengono visualizzati nel sistema di pagamento, ma non in Adobe Commerce.
* **MDVA-32449** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0 || >=2.4.1 &lt;2.4.2 con estensione B2B*) - Corregge il problema per cui la cronologia degli ordini si carica molto lentamente o non viene caricata affatto.
* **MDVA-32739** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema per cui l’abilitazione di Notifiche e-mail asincrone invia e-mail di vendita precedenti.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*per Adobe Commerce 2.3.6, 2.4.1*) - Risolve il problema in cui la *Creare un account* il pulsante rimane disattivato dopo la correzione dei dati non validi nel *Crea nuovo account cliente* modulo.
* **MDVA-31006** (*per Adobe Commerce 2.3.0, 2.3.1*) - Corregge il problema in cui gli ordini duplicati vengono visualizzati dopo aver effettuato un ordine utilizzando [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*per Adobe Commerce 2.3.0*) - Correzione del problema relativo [!DNL PayPal Payflow Pro] metodo di pagamento e trattamento dei cookie come `SameSite=Lax` per impostazione predefinita, nel browser Chrome 80 e nella risposta API reindirizza alla pagina di accesso del cliente.

## v1.0.10 {#v1-0-10}

Correzioni minori per le versioni delle patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui la Regola del prezzo del carrello con coupon non si applica tramite GraphQL quando *Sconto fisso per intero carrello* viene utilizzata l&#39;azione .
* **MDVA-30889** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema in cui si verifica un errore dopo la fatturazione di un bundle con prodotti virtuali e semplici come opzioni.
* **MDVA-31791** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*): migliora le prestazioni della pagina prodotto nei casi in cui vengono utilizzate regole di destinazione o prodotti collegati.
* **MDVA-31168** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema in cui il file CSV di esportazione del prodotto non viene visualizzato e si verifica un errore di allocazione della memoria.
* **MDVA-32313** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema per cui i prodotti configurabili possono essere aggiunti alla lista dei desideri con le opzioni di configurazione errate.
* **MDVA-31759** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i prodotti non vengono aggiornati con *menu a discesa* e *area di testo* valori di attributo durante l’importazione CSV.
* **MDVA-32012** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i codici postali in Corea e Argentina non possono essere convalidati.
* **MDVA-31640** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 | | >=2.4.0 &lt;2.4.1*) - Corregge il problema per cui un prezzo speciale non può essere aggiornato tramite API REST.
* **MDVA-28651** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 | >2.4.0 con estensione B2B*) - Corregge il problema in cui si verificano problemi di prestazioni durante il caricamento di virgolette negoziabili tramite API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*per Adobe Commerce >=2.3.0 &lt;2.4.1 con estensione B2B*) - Corregge il problema di visualizzazione di un segno di valuta errato nella griglia Nota di credito.
* **MDVA-31295** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema a causa del quale i punti premio non vengono calcolati quando un ordine parziale viene completato e gli articoli vengono tassati.
* **MDVA-30112** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*): risolve il problema se il numero di ordini supera il *mazzetto* valore, Adobe Commerce considera gli ordini con *in sospeso* stato come incongruenze.
* **MDVA-31150** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i saldi delle carte di credito e regalo del negozio non vengono restituiti dalla chiamata API GET Invoice Rest, quando la fattura è stata registrata dalla chiamata API Rest e l&#39;ordine è stato parzialmente pagato dai conti di credito e carta regalo del negozio.
* **MDVA-30963** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui i risultati del filtro prodotti impostati per contenere solo i valori specificati per *Tutte le visualizzazioni store* nell’ambito dell’amministratore, includi i prodotti con valori sottoposti a override a livello di visualizzazione store.
* **MDVA-29954** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0 | | 2.4.2 con estensione B2B*) - Risolve il problema in cui la *Nuova richiesta di registrazione della società* e *Sei stato collegato a un&#39;azienda* le e-mail vengono inviate dall’indirizzo errato.
* **MDVA-28357** (*per Adobe Commerce >=2.3.2 &lt;2.3.6 | | >=2.4.0 &lt;2.4.1*) - Sostituisce l&#39;analizzatore standard con un analizzatore personalizzato con keyword tokenizer per il campo SKU in [!DNL ElasticSearch] indice per far funzionare le query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema in cui lo stato dell&#39;ordine personalizzato veniva modificato in *Elaborazione* dopo la creazione della spedizione parziale utilizzando WebApi.
* **MDVA-30428** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corregge il problema per cui i clienti non possono aggiungere un prodotto all’elenco dei desideri se il prodotto è assegnato a un’origine di inventario personalizzata.
* **MDVA-30594** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che impediva il salvataggio di un ordine con più indirizzi durante il pagamento con configurazione FPT.
* **MDVA-29148** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema durante la creazione di un prodotto tramite una chiamata API, l&#39;attributo personalizzato del prodotto di `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) il tipo non utilizza il valore predefinito se nel payload non è stato fornito alcun valore.
* **MDVA-30837** (*per Adobe Commerce >=2.3.1 &lt;2.3.5*) - Aggiunta di un&#39;impostazione di configurazione *Includi imposta su importo: Sì/No* nella configurazione del metodo di spedizione gratuita. Quando *Includi imposta in importo* è impostato su *Sì*, Importo ordine minimo viene calcolato come Subtotale + Imposta. Quando *Includi imposta in importo* è impostato su *No*, Importo minimo dell&#39;ordine calcolato come Subtotale
* **MDVA-25028** (*per Adobe Commerce >=2.3.2 &lt;2.3.3 | | >=2.3.5 &lt;2.3.6*): risolve il problema quando gli ordini inseriti utilizzando [!DNL PayPal Payflow Pro] non sono impostati sullo stato di frode sospetta quando vengono attivati i filtri di frode.
* **MDVA-31224** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*) - Migliora le prestazioni del `catalog_product_price` reindicizzare il funzionamento per i prodotti bundle.
* **MDVA-31321** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge una pagina vuota (errore) quando *Mostra tutto* è selezionato. [!DNL Elasticsearch] restituisce un elenco esteso di ID prodotto. In questo scenario, la clausola order by viene convertita in un formato SQL errato.
* **MDVA-30815** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema per cui quando si modifica il numero di risultati di ricerca da visualizzare nella pagina dei risultati di ricerca, Adobe Commerce visualizza una pagina vuota. [!DNL Elasticsearch] ora visualizza correttamente i risultati delle pagine delle categorie quando si modifica il numero di risultati di ricerca visualizzati per pagina.
* **MDVA-30782** (*per Adobe Commerce >=2.3.5 &lt;2.4.2*): risolve il problema di visualizzazione del blocco dinamico indipendentemente dalla regola del carrello.
* **MDVA-31021** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema in cui esistono problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`. Se ci sono più di circa 100.000 record in `catalog_product_option` per la convalida di un nuovo CSV con un singolo prodotto sono necessari meno di 10 secondi.
* **MDVA-31007** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corregge il problema per cui gli attributi dell’indirizzo personalizzato non vengono visualizzati correttamente nella pagina dei dettagli dell’ordine nell’area del mio account e nel backend.
* **MDVA-29389** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema della generazione di rapporti avanzati in cui la `analytics_collect_data` cronjob scrive: *La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*.
* **MDVA-31343** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corregge il problema relativo alla classe body rimossa `page-layout-category-full-width` quando viene pianificata una categoria.
* **MDVA-30945** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui ricevi un messaggio di errore fatale durante l&#39;aggiornamento dei carrelli `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*per Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa la *Il valore minimo deve corrispondere a* funzionalità e ricerca parziale [!DNL Elasticsearch] motore. Risolve i problemi relativi ai trattini nelle query di ricerca.
* **MDVA-30102** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corregge il problema per cui la cache Redis cresce rapidamente poiché le cache di layout non dispongono di TTL.
* **MDVA-30599** (*per Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corregge il problema per cui le virgolette ospiti create utilizzando API vengono contrassegnate in modo errato come virgolette per i clienti registrati.
* **MDVA-29446** (*per Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corregge il problema per cui il prezzo del metodo di spedizione non applicabile viene visualizzato come zero durante il pagamento.
* **MDVA-30357** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*): risolve il problema con gli URL immagine errati che vengono creati quando si genera una mappa del sito per cron.
* **MDVA-30565** (*per Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Risolve il problema in cui *Nessuna entità con cartid = 0* viene visualizzato un errore per i clienti ospiti al momento del pagamento nella vetrina se il carrello è abilitato.
* **MDVA-29787** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0*): risolve il problema in cui la regola di destinazione per i prodotti correlati non funziona quando *è uno di* viene utilizzata per definire i prodotti da visualizzare.
* **MDVA-30977** (*per Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corregge il problema dei prodotti casuali mancanti dalle categorie dopo la reindicizzazione.
* **MDVA-28202** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corregge il problema per cui la navigazione a livelli non filtra correttamente i prodotti configurabili quando viene utilizzato MSI.
* **MDVA-28300** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui la richiesta GQL non riflette le modifiche di prezzo rispetto alle regole del prezzo di catalogo.
* **MDVA-31006** (*per Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corregge il problema in cui gli ordini duplicati vengono visualizzati dopo aver effettuato un ordine utilizzando [!DNL Paypal Express] pagamento.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Risolve il problema della navigazione a livelli, dove il *No* il valore per gli attributi di prodotto di tipo booleano non è stato incluso nella navigazione a livelli se [!DNL Elasticsearch] è stato utilizzato come motore di ricerca.
* **MDVA-28191** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*): risolve il problema per cui non vengono caricati metodi di pagamento durante la creazione dell&#39;ordine tramite l&#39;amministratore.
* **MDVA-29959** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 con estensione B2B*) - Corregge il problema per cui l&#39;utente con restrizioni dell&#39;amministratore con *Aziende* le autorizzazioni non sono consentite per eliminare l&#39;account aziendale.
* **MDVA-30265** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema di funzionamento del collegamento di tracciamento della spedizione dopo la creazione della fattura.
* **MDVA-28409** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Risolve il problema in cui la `sales_clean_quotes` il lavoro cron non riesce con *memoria esaurita* errore quando il numero di virgolette scadute nel database è enorme.
* **MDVA-30593** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema per cui le virgolette scadute in base all’impostazione Citazione a vita non vengono ripulite.
* **MDVA-30107** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui lo switcher dello store non funziona come previsto se vengono utilizzati URL di base diversi per le viste dello store.
* **MDVA-28763** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema per cui l’immagine del prodotto viene duplicata dopo aver aggiornato le informazioni sul prodotto utilizzando l’API REST più di una volta.
* **MDVA-30284** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema di errore dell&#39;indicizzatore di Ricerca nel catalogo a causa dei seguenti *[!DNL Elasticsearch]errore: è stato superato il limite dei campi totali nell&#39;indice.*
* **MDVA-29042** (*per Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 con estensione B2B*) - Corregge il problema in cui le autorizzazioni Catalogo sono state modificate in *Consenti* automaticamente dopo l&#39;aggiunta di un nuovo prodotto al catalogo condiviso.
* **MDVA-30428** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui i clienti non possono aggiungere un prodotto all’elenco dei desideri se il prodotto è assegnato a un’origine di inventario personalizzata.
* **MDVA-28661** (*per Adobe Commerce >=2.3.0 &lt;2.4.2 con estensione B2B*) - Corregge il problema in cui viene generato un errore nella sezione dell&#39;account aziendale Utenti società dopo che l&#39;amministratore dell&#39;azienda è stato modificato.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*per Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corregge il problema in cui i processi cron non riescono se il nome del database è troppo lungo, causando l&#39;aggiornamento delle categorie sul fronte.
* **MDVA-30106** (*per Adobe Commerce ^2.3.0*) - Corregge un problema a causa del quale durante l&#39;estrazione i pagamenti non vengono caricati con *Impossibile leggere la proprietà &#39;length&#39; di null* errore nella console JS.
* **MDVA-28656** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 | | >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui, se un ordine è stato effettuato senza informazioni di pagamento richieste (ad esempio, con uno sconto del 100%) e per l&#39;ordine è stata creata una fattura, lo stato dell&#39;ordine viene modificato in *Chiuso* anziché Completo.
* **MDVA-30209** (*per Adobe Commerce 2.3.0 - 2.3.3-p1*): risolve il problema per cui il gruppo di clienti veniva modificato in predefinito se il cliente aggiornava le informazioni sul proprio account.
* **MDVA-30123** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*): risolve il problema per cui le etichette delle opzioni di attributo non vengono tradotte correttamente per le query GraphQL.
* **MDVA-29996** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui, dopo aver abilitato l’autorizzazione per categoria, la pagina della categoria non viene memorizzata nella cache da Full Page Cache.
* **MDVA-30164** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*): risolve il problema per cui i record cliente non possono essere esportati dalla griglia Clienti se esistono attributi cliente personalizzati.
* **MDVA-30444** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema per cui non viene inviato alcun messaggio e-mail di conferma per gli ordini effettuati utilizzando GraphQL.
* **MDVA-30490** (*per Adobe Commerce 2.3.4 - 2.3.5-p2*): risolve il problema per cui il confronto dei prodotti genera la pagina di errore 500 se uno dei prodotti presenta una breve descrizione vuota.
* **MDVA-30232** (*per Adobe Commerce >=2.3.1 &lt;2.4.1*): risolve il problema in cui non è possibile riordinare se l&#39;ordine originale contiene una carta regalo.
* **MDVA-29965** (*per Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corregge il problema per cui i clienti ottengono un errore di tipo Form Key non valido quando si aggiunge un prodotto al carrello.
* **MDVA-30008** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*): risolve il problema B2B in cui non è possibile effettuare ordini tramite l&#39;API amministratore per un prodotto presente in un catalogo pubblico.
* **MDVA-22469** (*per Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Corregge il problema per cui dopo l’aggiornamento ad Adobe Commerce 2.3.3, Page Builder non funziona nel pannello Amministratore e alcuni file JS e CSS non vengono caricati.
* **MC-35984** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*): risolve il problema per cui i commercianti non potevano interagire con elementi di pagina nella pagina Restituisce dopo la creazione di un’etichetta di spedizione per un’autorizzazione RMA (Return Merchandise Authorization).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*per Adobe Commerce 2.3.0 - 2.3.4*) - Risolve il problema con [!DNL PayPal Payflow Pro] metodo di pagamento e trattamento dei cookie come `SameSite=Lax` per impostazione predefinita, nel browser Chrome 80 e nella risposta API reindirizza alla pagina di accesso del cliente.
* **MDVA-26694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 | 2.4.0*): risolve il problema della scadenza giornaliera delle cache di prodotti e cataloghi, anche se la loro scadenza era pianificata in modo diverso.
* **MDVA-27825** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*): risolve il problema di esportazione di grandi quantità di dati non riuscita a causa di perdita di memoria.
* **MDVA-29085** (*per Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corregge il problema B2B in cui non vengono inviate nuove e-mail aziendali richieste se un’azienda viene creata tramite API.
* **MDVA-29344** (*per Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*): risolve il problema per cui Page Builder si blocca dopo aver copiato il testo da un elemento di intestazione a un elemento di testo.
* **MDVA-29835** (*per Adobe Commerce >2.3.1 &lt;2.4.2*) - Corregge il problema per cui gli ordini con carta regalo contenevano due codici invece di uno.
* **MDVA-30052** (*per Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): risolve il problema relativo al mancato popolamento corretto del contenuto privato (archiviazione locale), che causava problemi di prestazioni.
* **MDVA-30131** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 | 2.4.0*) - Risolve il problema della navigazione a livelli, dove il *No* il valore per gli attributi di prodotto di tipo booleano non è stato incluso nella navigazione a livelli se [!DNL Elasticsearch] è stato utilizzato come motore di ricerca.
* **MDVA-35514** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*): risolve il problema relativo alla creazione di un&#39;etichetta di spedizione e all&#39;aggiunta di prodotti ordinati a un pacchetto nella finestra modale Crea pacchetti.

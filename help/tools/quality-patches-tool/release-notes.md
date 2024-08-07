---
title: Note sulla versione
description: Scopri le patch disponibili per Adobe Commerce e i problemi che risolvono.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7c294a9450be46049090c78074d4fbe722a75119
workflow-type: tm+mt
source-wordcount: '20855'
ht-degree: 0%

---

# Note sulla versione

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) distribuisce singole patch sviluppate da Adobe e dalla community di Magento Open Source. Consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce. Puoi applicare patch ai progetti Adobe Commerce e Magento Open Source indipendentemente da chi ha sviluppato la patch. Ad esempio, puoi applicare ai progetti Adobe Commerce una patch sviluppata dalla community.

>[!INFO]
>
>Per istruzioni sull&#39;applicazione di patch ai progetti Adobe Commerce, consulta [Applicare patch](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches). Vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella Guida all&#39;aggiornamento software per esaminare l&#39;elenco completo delle patch rilasciate.

>[!INFO]
>
>Per informazioni sulle [!DNL quality patches] create dalla community per il Magento Open Source, consulta le [note sulla versione](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Risolve il problema della rimozione delle immagini del prodotto dopo l&#39;eliminazione di un aggiornamento della gestione temporanea.
* **ACSD-57086** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati non vengono elaborati correttamente.
* **ACSD-57588** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui la spedizione di un ordine a più indirizzi genera un errore durante l&#39;elaborazione dell&#39;ID di regione.
* **ACSD-57643** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema relativo all&#39;aggiunta errata di prodotti con opzioni personalizzate al carrello tramite GraphQL.
* **ACSD-57846** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui la ricerca di prodotti GraphQL con un filtro per prezzi zero non restituisce alcun risultato a causa di un&#39;eccezione.
* **ACSD-57941** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema di assegnazione errata delle opzioni prodotto all&#39;archivio di amministrazione anziché ai rispettivi archivi.
* **ACSD-58375** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema di errore causato dalla configurazione *[!DNL YouTube API Key]* errata durante l&#39;aggiunta di un video [!DNL YouTube] a livello di visualizzazione archivio.
* **ACSD-58739** (per Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corregge il problema che causa la reindicizzazione parziale.
* **ACSD-58446** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema se durante l’eliminazione di un team con utenti o team secondari a prescindere dal loro stato (inattivo), il sistema fornisce un messaggio di errore non informativo non coerente con l’interfaccia utente.
* **ACSD-58054** (per Adobe Commerce >=2.4.4 &lt;2.4.6) - Risolve il problema della possibilità di generare token cliente per i clienti inattivi tramite API.
* **ACSD-58163** (per Adobe Commerce >=2.4.3 &lt;2.4.7) - Corregge il problema per cui *[!UICONTROL Cart Price Rule]* non applica uno sconto per un cliente ospite dal carrello *[!UICONTROL Customer Segment]* corrispondente senza un codice coupon.
* **ACSD-57045** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui le riscritture URL causano un ciclo di pagina infinito dopo la deselezione di *[!UICONTROL Website Root]* da *[!UICONTROL Hierarchy]*.
* Patch aggiornate: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (per Adobe Systems Commerce e la mutazione Magento Open Source >=2.4.3`mergeCart` &lt;2.4.7) - Fixes the issue where the non riesce con un &quot;*Errore* server interno&quot; nella [!DNL GraphQL] risposta quando si uniscono carrelli di origine e di destinazione che hanno gli stessi elementi del bundle.
* **ACSD-56546** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui i prodotti configurabili e bundle vengono visualizzati come **esauriti** nella vetrina quando **visualizzazione esaurita** è *Disabilitato*.
* **ACSD-56635** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Risolve il problema relativo alla duplicazione del cliente importato con lo stesso indirizzo e-mail, quando viene utilizzata un&#39;importazione con **condivisione account** impostata su *Global*.
* **ACSD-56741** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il messaggio di errore &quot;*Tentativo di accedere all&#39;offset dell&#39;array sul valore di tipo null*&quot; visualizzato durante `setup:upgrade` quando il database contiene un trigger [!DNL MySQL] personalizzato non correlato al meccanismo di indicizzazione e [!DNL MView].
* **ACSD-57315** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante [!UICONTROL Fetch] nella schermata **[!UICONTROL View transaction]** dell&#39;amministratore.
* **ACSD-57337** (per Adobe Commerce >=2.4.4 &lt;2.4.6) - Corregge il problema per cui un utente amministratore con restrizioni di accesso a siti Web specifici è in grado di visualizzare società di tutti i siti Web nella griglia **[!UICONTROL Companies]**.
* **ACSD-57394** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema di un ordinamento errato dei prodotti in base a più campi di ordinamento in [!DNL GraphQL].
* **ACSD-57565** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che causava la visualizzazione di informazioni di ordine errate nel dashboard **[!UICONTROL Order]** fino all&#39;aggiornamento del periodo di tempo. Il dashboard visualizza ora le statistiche dell’ordine corrette al primo caricamento.
* **ACSD-57854** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): è stato risolto il problema che si verificava se le richieste del prodotto [!DNL GraphQL] restituivano categorie disabilitate nelle aggregazioni di categorie.
* **ACSD-58008** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui l&#39;aggiornamento di un aggiornamento pianificato ha rimosso la versione precedente di un elemento nell&#39;area di gestione temporanea, se non è stata specificata una data di fine.
* Patch aggiornate: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui gli attributi *[!UICONTROL Used]* e *[!UICONTROL Times Used]* visualizzano valori non corretti per i coupon generati quando vengono utilizzati durante il pagamento con più indirizzi.
* **ACSD-56760** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema per cui un utente amministratore limitato a un sito Web specifico non può ordinare o aggiungere nuovi prodotti all&#39;interno di una categoria nel caso in cui il webstore abbia una propria categoria radice.
* **ACSD-56858** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione errata delle autorizzazioni del ruolo aziendale B2B per un amministratore società con restrizioni.
* **ACSD-57074** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui l&#39;attributo personalizzato *Yes/No* con `attrbute_code` che inizia con `price_` non funziona correttamente con l&#39;indicizzazione e i prodotti con tali attributi non sono disponibili nel front-end.
* Patch aggiornate: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the category page caches invalidate when the stock quantity changes, even if the product is still in stock.
* **ACSD-54656** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the invisible Recaptcha fails during checkout, preventing an order from being placed.
* **ACSD-55100** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where GraphQL does not return more than 10k products in the search results.
* **ACSD-56621** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il nome e il cognome aggiornati non vengono riportati nella sezione dell&#39;intestazione dei saluti per l&#39;utente amministratore della società.
* **ACSD-56842** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema di mancanza dei proxy differiti e delle directory proxy differite dopo l&#39;esecuzione di `setup:di:compile`.
* **ACSD-57003** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui lo stato dell&#39;ordine viene modificato in *[!UICONTROL Complete]* invece di essere modificato in *[!UICONTROL Processing]* quando un ordine viene parzialmente rimborsato e parzialmente spedito.
* Patch aggiornate: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7): è stato risolto il problema relativo alla esaurimento di un prodotto configurabile quando uno dei due prodotti secondari viene disabilitato da un aggiornamento pianificato.
* **ACSD-56616** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where bundled products display as in stock on the storefront when their simple products are out of stock.
* **ACSD-56515** (for Adobe Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where admin with website level permissions cannot add or edit a dynamic block.
* **ACSD-56447** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where adding the same product to the cart via parallel REST web API requests results in two separate items in the cart.
* **ACSD-56415** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema relativo al rallentamento delle prestazioni dell&#39;indicizzazione parziale dei prezzi dovuto a una query `DELETE` quando il database contiene molti dati parziali sui prezzi da indicizzare.
* **ACSD-54965** (per Adobe Commerce >=2.4.5 &lt;2.4.6) - Corregge il problema per cui nella griglia di Visual Merchandising non viene visualizzato lo stock corretto quando un prodotto viene assegnato solo a stock personalizzati.
* **ACSD-52824** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where PayPal Express, Google Pay, and Apple Pay buttons are displayed for company customers when such payment methods are disabled in company settings.
* Patch aggiornate: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a user is redirected to the Admin Dashboard when sorting category products using the **Spostati dall&#39;opzione Stock a quella inferiore** e l&#39;errore `Invalid security or form key. Please refresh the page` appare nella parte superiore dello schermo.
* **ACSD-56280** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Corregge il problema per cui l&#39;ordinamento di articoli da un registro regali genera un&#39;eccezione.
* **ACSD-56246** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Risolve il problema della rimozione dei dati dall&#39;attributo di selezione multipla personalizzato quando diventa attivo un aggiornamento pianificato per un prodotto.
* **ACSD-56193** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Corregge il problema per cui la cache Vernice/Fastly non viene aggiornata quando si utilizza un blocco pianificato nella descrizione della categoria mediante Page Builder.
* **ACSD-56158** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema in cui la query &quot;cart&quot; restituisce il valore fiscale totale per ogni regola fiscale.
* **ACSD-56023** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il contenuto del widget non viene aggiornato nella pagina CMS quando la cache è abilitata.
* **ACSD-55427** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui l&#39;utente amministratore non può annullare l&#39;assegnazione di un prodotto da un catalogo condiviso dalla pagina prodotto in Admin.
* **ACSD-55352** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where after creating a partial credit memo with customer reward points, the order status changes to Closed and credit memo options disappear from the Admin order page.
* **ACSD-55231** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Risolve il problema che impediva l&#39;aggiunta di prodotti al carrello con la funzionalità ordine rapido.
* **ACSD-54283** (per Adobe Commerce >=2.4.3 &lt;2.4.4) - Corregge il problema per cui Prodotti/Categorie non assegnati al Catalogo condiviso per il Valore predefinito (Gruppo generale) sono ancora inclusi in Sitemap XML.
* Patch aggiornate: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui l&#39;URL canonico della categoria non viene aggiornato dopo la modifica dell&#39;URL della categoria.
* **ACSD-53636** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Risolve il problema che non consentiva la visualizzazione del prezzo normale nelle pagine dell&#39;elenco dei prodotti configurabili con prodotti secondari a prezzi speciali.
* **ACSD-54885** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema dell&#39;estrazione di più indirizzi quando l&#39;utente amministratore utilizza la funzionalità *Accedi come cliente*.
* **ACSD-55610** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui un ordine parzialmente annullato presenta un importo di sconto errato.
* **ACSD-55334** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge le traduzioni per le etichette tramite i dizionari di traduzione nella risposta di GraphQL.
* **ACSD-54739** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui la condizione dello stato delle scorte di prodotto non viene applicata per le regole del prodotto correlate.
* **ACSD-53925** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui l&#39;amministratore non è in grado di salvare il blocco CMS con il carosello prodotti quando la modalità dimensioni `catalog_product_price` è impostata su *sito Web*.
* **ACSD-52714** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo al mancato funzionamento del filtro data nella griglia di amministrazione quando il formato data è impostato su *Y-m-d*.
* **ACSD-55055** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Migliora le prestazioni di caricamento degli attributi del prodotto nelle regole di prezzo del carrello nel carrello.
* **ACSD-53790** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where Multiple RMAs for a single product can be created via REST API.
* **ACSD-56090** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the GraphQL request is responding with all stores&#39; data rather than the specifically requested store data.
* **ACSD-54983** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where getting the company user UID with GraphQL request is not possible when the user status is set to *[!UICONTROL Inactive]*.
* **ACSD-53309** (per Adobe Systems Commerce ed etichetta Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where tax is not fully applied in the *[!UICONTROL Regular Price]* quando è selezionata l&#39;opzione personalizzabile.
* **ACSD-55305** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Corregge il problema per cui la finestra a comparsa *[!UICONTROL Edit Company User]* nella pagina **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** si blocca con un caricatore sullo schermo.
* Patch aggiornate: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui i dati di prodotto *[!UICONTROL Recently Viewed]* non vengono aggiornati correttamente nella visualizzazione archivio.
* **ACSD-54626** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema che impedisce la creazione di una nuova regola ordine fornitore (`createPurchaseOrderApprovalRule`) con l&#39;attributo `NUMBER_OF_SKUS` tramite [!DNL GraphQL].
* **ACSD-53845** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the [!DNL MySQL] problema di timeout della connessione quando `consumer max_messages` = 0.
* **ACSD-54890** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo a `aggregate_sales_report_bestsellers_data` che causa [!DNL MySQL] errori a causa di spazio insufficiente sul disco `/tmp`.
* **ACSD-55112** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui è possibile fare clic più volte sul pulsante *[!UICONTROL Submit review]* senza la convalida [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (per Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corregge il problema per il quale viene visualizzato il messaggio di errore *&quot;Impossibile aggiornare l&#39;attributo richiesto. L&#39;ID riga: store_id&quot;* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione archivio.
* **ACSD-54418** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Risolve il problema relativo all&#39;applicazione errata di una quantità fissa di sconto a ogni prodotto figlio del bundle a prezzo dinamico.
* **ACSD-55238** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes saving the empty product *[!UICONTROL Meta Description]*.
* **ACSD-54966** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a coupon code with a limited-use per customer can&#39;t be reused if the previous order failed.
* **ACSD-54060** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a restricted admin can&#39;t save a product if it&#39;s a child of another product assigned to a different scope.
* **ACSD-48910** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixed the issue where a bundle product assigned to multiple sources goes out-of-stock after an order is invoiced and shipped, even if it still has a non-zero quantity.
* **ACSD-55381** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge un errore interno del server durante la query di `configurable_product_option_uid` e `configurable_product_option_value_uid` campi da un [!DNL B2B] *[!UICONTROL Requisition list]* tramite [!DNL GraphQL].
* **ACSD-55628** (per Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Corregge il caricamento di un file nel modulo di registrazione della società e la sostituzione di un file per un attributo del cliente nella vetrina.
* Patch aggiornate: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema che si verifica nel carrello quando un prodotto viene rimosso dal catalogo condiviso dopo essere già stato aggiunto al carrello.
* **ACSD-53722** (per Adobe Systems Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where the bundled product options price changes to $0 when scheduled updates for different scopes become active.
* **ACSD-53643** (per Adobe Systems Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where the order has an incorrect total when placing a purchase order with disabled or out-of-stock products. Viene risolto nascondendo il *[!UICONTROL Place Order]* pulsante per tali ordini di acquisto.
* **ACSD-54067** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Risolve il problema della mancata riproduzione di un video prodotto su un dispositivo mobile.
* **ACSD-55414** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Migliora le prestazioni quando MariaDB tenta di eseguire il cast di entity_id EAV da stringa a numero intero.
* **ACSD-51819** (per Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Corregge il problema per cui è possibile inserire più ordini con lo stesso ID preventivo.
* **ACSD-53118** (per Adobe Commerce >=2.4.0 &lt;2.4.7) - Risolve il problema relativo all&#39;applicazione di *[!UICONTROL Cart Price Rule]* tramite il codice coupon mentre il prodotto ha un attributo vuoto.
* **ACSD-54324** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui la richiesta di GraphQL request_LISTS non considera le impostazioni di impaginazione e restituisce tutti i risultati.
* Patch aggiornate: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (per Adobe Commerce >=2.4.0 &lt;2.4.6) - Risolve il problema che impediva l&#39;elaborazione di un preventivo B2B inviato per un prodotto con più origini assegnate.
* **ACSD-54040** (per Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Corregge il problema per cui il campo *[!UICONTROL Created]* è vuoto nei dettagli dell’ordine quando i moduli B2B sono abilitati.
* **ACSD-54319** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui il prezzo del prodotto mostra zero nel report *[!UICONTROL Product in Cart]*.
* **ACSD-53378** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Migliora il tempo di caricamento delle pagine di pagamento per i clienti che dispongono di rubriche di grandi dimensioni.
* **ACSD-52657** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema se il minicart non viene aggiornato nella visualizzazione archivio secondaria, che utilizza un sottodominio.
* **ACSD-53414** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema per cui un utente amministratore con restrizioni può visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni.
* **ACSD-54472** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema per cui i clienti di un&#39;azienda rifiutata possono ancora autenticarsi e i clienti di un&#39;azienda bloccata e rifiutata possono ancora effettuare ordini. La patch aggiunge una convalida aggiuntiva per gli endpoint di GraphQL.
* **ACSD-52801** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiunge l&#39;opzione per effettuare una corrispondenza parziale durante la ricerca di prodotti in GraphQL.
* **ACSD-55004** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema relativo agli arresti anomali della convalida durante il caricamento di un file di importazione di dimensioni superiori al valore configurato in `php.ini`.
* **ACSD-54989** (per Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corregge il problema per cui un amministratore società non può effettuare un ordine quando *[!UICONTROL Enable Purchase Orders]* è impostato su *[!UICONTROL Yes]* e *[!UICONTROL Purchase Order]* è impostato su *[!UICONTROL No]*.
* **ACSD-54007** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l&#39;errore *&quot;Chiave di array &quot;_scope&quot;&quot;* non definita durante l&#39;importazione dei dati dei clienti.
* **ACSD-55031** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge l&#39;errore *Tipo &quot;misto&quot; non può ammettere i valori Null* durante la compilazione.
* **ACSD-54961** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui un utente amministratore con restrizioni non può aggiornare in massa lo stato *Product Review*.
* **ACSD-55256** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Risolve il problema della corretta visualizzazione nel cursore immagine solo della prima immagine.
* Patch aggiornate: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (per Adobe Commerce >=2.4.0 &lt;2.4.7) - Corregge il problema per cui la cronologia del saldo dei punti premio viene calcolata in modo errato dopo la scadenza dei punti premio.
* **ACSD-53583** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Migliora le prestazioni di reindicizzazione parziale per gli indicizzatori *Categoria prodotti* e *Categorie prodotti*.
* **ACSD-54026** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge un messaggio di errore non corretto per una richiesta GraphQL `updateCompanyRole` per un utente non autorizzato.
* **ACSD-54106** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corregge il problema per cui l&#39;ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi non è corretto.
* **ACSD-52219** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema relativo al funzionamento imprevisto dei filtri salvati dalle griglie di amministrazione quando si passa di frequente da una visualizzazione all&#39;altra.
* **ACSD-54342** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge un messaggio di errore errato *Errore nella struttura dati: valori misti* durante l&#39;importazione di un file CSV senza dati validi.
* **ACSD-54660** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Aggiunto un nuovo attributo di input *sort* per ordinare gli ordini dei clienti in GraphQL in base a `sort_field` e `sort_direction`.
* **ACSD-54776** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui i valori non selezionati *[!UICONTROL Use Default Value]* e non predefiniti dei campi prodotto non vengono salvati per la seconda visualizzazione sito Web, archivio e archivio.
* **ACSD-53998** (per Adobe Commerce e Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Corregge il problema per cui **[!UICONTROL Dynamic Block]** basato su **[!UICONTROL Customer Segment]** non funziona correttamente dopo la disconnessione da un account cliente.
* **ACSD-53204** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Correzioni *Impossibile salvare il prodotto.Errore* durante l&#39;esecuzione di richieste simultanee per l&#39;aggiunta di immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`.
* **ACSD-47657** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiunto un meccanismo di caching per le credenziali di AWS. Un provider di credenziali ora utilizza la cache del Magento per memorizzare nella cache le credenziali recuperate da AWS per la configurazione EC2.
* Aggiornate patch: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corregge il problema per cui i prodotti assegnati a un catalogo condiviso non vengono visualizzati nella vetrina quando viene eseguito un indice parziale.
* **ACSD-54018** (per Adobe Systems Commerce e widget Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the performance issues with the [!UICONTROL Product List] che utilizza un attributo non globale nella condizione di widget.
* **ACSD-54111** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui le immagini delle miniature del prodotto non vengono visualizzate nella vetrina quando le proporzioni dell&#39;immagine della filigrana non corrispondono all&#39;immagine del prodotto.
* **ACSD-47669** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge *Violazione del vincolo di integrità: 1452 Impossibile aggiungere o aggiornare una riga figlio: errore di vincolo di chiave esterna* durante l&#39;importazione del file CSV dei prodotti.
* **ACSD-53347** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo all&#39;esecuzione dell&#39;indicizzatore prezzi.
* **ACSD-52287** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Risolve il problema relativo allo stato dell&#39;ordine errato nella griglia dell&#39;ordine archiviata quando è abilitata l&#39;indicizzazione asincrona della griglia.
* **ACSD-52929** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo alle richieste ridondanti di reindicizzazione degli elementi di origine predefiniti quando l&#39;indicizzatore inventario è configurato in modalità asincrona.
* **ACSD-53824** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui la patch dei dati di migrazione di `UpdateMultiselectAttributesBackendTypes` supera il limite delle dimensioni delle transazioni del database durante `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema relativo all&#39;aggiornamento delle cache e degli indici anche quando l&#39;API REST non aggiorna `Inventory_source` elementi.
* **ACSD-51884** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che causava la correzione del percorso della cache delle immagini del prodotto dopo l&#39;esecuzione del comando di ridimensionamento.
* **ACSD-53628** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione di caratteri speciali non corretti nel rapporto CSV degli ordini di vendita.
* **ACSD-53148** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui due richieste parallele in GraphQL per l&#39;aggiunta dello stesso prodotto configurabile al carrello hanno prodotto due elementi separati sul carrello con lo stesso SKU prodotto.
* **ACSD-52606** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo al messaggio di errore *Quando l&#39;utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**, l&#39;ordine non è pronto per il ritiro*.
* **ACSD-51574** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema se l&#39;immagine non viene aggiornata sul front-end dopo averla sostituita con un&#39;altra immagine con lo stesso nome.
* **ACSD-53728** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che causava il ritardo nel completamento dell&#39;indicizzatore EAV del prodotto.
* **ACSD-53979** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the JS issue that occurs on the homepage if the welcome message contains a single quote.
* **ACSD-52085** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a configurable product with a special price is not visible in the product&#39;s carousel.
* **ACSD-53795** (per Adobe Systems Commerce e cron job Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue with invalid data type in `indexer_update_all_views` .
* **ACSD-52143** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where custom options are removed after product import.
* **ACSD-53750** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 *&lt;2.4.7) - Fixes the  Pipe guasto o errore di connessione* chiusa durante la reindicizzazione multithread.`catalog_product_price`
* **ACSD-49843** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 ||=&quot;&quot;>=2.4.1 &lt;2.4.7) - Fixes the issue where the link on product download is not available after the ordered item is auto-invoiced by online payment method with the **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** impostazione abilitata.&lt;/2.4.0>
* **ACSD-47054** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.6) - Fixes the issue where the preview reindex runs reindex for all stores, causing slowness.
* Aggiunte nuove versioni per ACSD-46541, ACSD-47079.
* ACSD-49970-v3 sostituito da ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt; 2.4.6): è stato risolto il problema che determinava la pulizia di tutte le cache da parte dell&#39;indicizzatore di inventario nella modalità Aggiorna secondo pianificazione.
* **ACSD-50887** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui la proprietà dell&#39;attributo di prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostata su *Yes* senza che l&#39;opzione *[!UICONTROL Use in search]* sia impostata su *Yes*.
* **ACSD-51846** (per Adobe Systems Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Fixes the *Problema di Errore* interno Ciò si verifica perché non vengono convalidati tutti i livelli di payload dell&#39;API REST.
* **ACSD-52906** (for Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where the X-Magento-Vary cookie is set incorrectly for logged-in customers that belong to the same customer segment causing improper caching for some pages.
* **ACSD-52736** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where a *Cart Price Rule* that includes requirements for configurable product quantity does not work as expected.
* **ACSD-47875** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva agli utenti amministratori di aggiungere un prodotto al carrello di un cliente dall&#39;amministratore per un determinato ambito di visualizzazione archivio con gestione inventario.
* **ACSD-53176** (per Adobe Systems Commerce >=2.3.7 &lt;2.4.5) - Fixes the issue where *La regola* del prodotto correlato con *è una delle* condizioni non corrisponde ai prodotti.
* **ACSD-51666** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the error *La sessione è scaduta, login di nuovo.* Ciò avviene dopo che un cliente tenta di accedere.
* Sono state aggiunte nuove versioni per MDVA-39305-v2.
* Requisiti aggiornati per ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui l&#39;indirizzo di spedizione predefinito nella fase di spedizione di pagamento viene popolato automaticamente con un indirizzo di prelievo in-store selezionato in precedenza.
* **ACSD-52041** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema relativo al rendering del messaggio di errore: *[ERROR] [!DNL Page Builder] per 5 secondi senza rilasciare blocchi.* viene visualizzato nel browser Chrome durante il salvataggio del contenuto modificato con [!DNL Page Builder].
* **ACSD-52095** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema per cui il valore `manage_stock` veniva erroneamente impostato su 0 nel file CSV dopo l&#39;esportazione del prodotto.
* **ACSD-51358** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema se la rimozione di un aggiornamento pianificato senza data di fine comporta la rimozione di altri aggiornamenti pianificati per la stessa entità.
* **ACSD-48070** (per Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where editing a scheduled update triggers an exception.
* **ACSD-51890** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Submit review] pulsante può essere cliccato più volte senza [!DNL Google reCAPTCHA] convalida v3.
* **ACSD-51984** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where unchecked *[!UICONTROL Use Default Value]* e *[!UICONTROL non-default product field]* i valori non vengono salvati per la seconda visualizzazione Web, store e store.
* **ACSD-52398** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l&#39;errore *La quantità richiesta non è disponibile* che si verifica quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
* **ACSD-52786** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui una condizione *SKU del catalogo è* si applica a tutti i prodotti che iniziano con lo SKU specificato.
* **ACSD-52921** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Risolve il problema relativo a un errore interno che si verificava se si richiedevano i dettagli del carrello a GraphQL quando nel carrello era presente un prodotto configurabile esaurito.
* **ACSD-51683** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui non è possibile aggiungere al carrello un&#39;opzione personalizzabile tramite GraphQL.
* **ACSD-52133** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Risolve il problema che impediva il salvataggio di un account cliente dopo un aggiornamento.
* **ACSD-52202** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui la quantità vendibile delle scorte predefinite cambia erroneamente in 0 quando una scorta non predefinita viene modificata in 0 qtà all&#39;evasione dell&#39;ordine.
* **ACSD-51265** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7): è stato risolto il problema relativo alle prestazioni di reindicizzazione di `catalog_product_price` in presenza di troppi prodotti inclusi nel .
* **ACSD-52831** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Risolve il problema che impediva ai clienti di inserire ordini di preventivo negoziabili quando [!DNL Google reCAPTCHA v3 Invisible] è abilitato.
* **ACSD-51845** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui i prodotti successivi con prezzi di livello e set di attributi diversi non possono essere aggiornati tramite API REST in blocco asincrona.
* **ACSD-52815** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;input per il campo della quantità di un&#39;origine non predefinita supporta solo fino a 6 cifre, a differenza di 8 per un titolo predefinito.
* **ACSD-51149** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;ImportazioneEsportazione pianificata con autorizzazioni catalogo abilitate invalida gli indicizzatori e quindi scarica i dati nella cache in base a cron.
* **ACSD-50815** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui la quantità decimale per un prodotto semplice non può essere utilizzata per una nuova opzione Prodotto in bundle.
* Versioni aggiornate per ACSD-47803.
* Titolo aggiornato per ACSD-51892.
* Aggiornato ACSD-51379.
* Aggiornato ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where an admin user is not redirected properly after selecting a store view when creating a new order in Admin.
* **ACSD-50813** (per funzionalità Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where Admin was not able to add bundled products containing a slash in the SKU with the [!UICONTROL Add Products by SKU] per l&#39;ordine dell&#39;amministratore.
* **ACSD-51630** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a large amount of system messages slows the downloading of admin pages.
* **ACSD-51853** (per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Fixes the issue where copied text styles are not applied when using the [!UICONTROL Page Builder].
* **ACSD-52160** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the product validation result against the cart price rule was not properly evaluated based on the rule condition &#39;If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true&#39;.
* **ACSD-51636** (per Adobe Commerce >=2.4.5 &lt;2.4.7): è stato risolto il problema che impediva all&#39;amministratore della società di aggiungere nuovi utenti dalla sezione account cliente nonostante l&#39;esistenza di tutti i ruoli e le autorizzazioni necessari.
* **ACSD-51739** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema per cui viene restituito un errore quando `structure_id` viene richiesto in una richiesta CompanyTeam GraphQL.
* **ACSD-51857** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo alle prestazioni lente del report cron `aggregate_sales_report_bestsellers_data` sulle tabelle sales_order e `sales_order_item` di database di grandi dimensioni dovute al modo in cui è stata scritta la query di dati principale.
* **ACSD-48448** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo a una situazione di tipo &quot;race condition&quot; che si verifica durante l&#39;annullamento dell&#39;ordine e causa la duplicazione di una voce nella tabella `inventory_reservation`.
* **ACSD-52689** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.6) - Fixes the issue where images cannot be uploaded to Amazon S3 storage using REST API.
* **B2B-2674** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Add caching capability to the 1customAttributeMetadata1 GraphQL query.
* Nuove versioni aggiunte per ACSD-44938.
* Nuovi requisiti per ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Corregge il comando di rollback del database per un caso in cui il dump del database contiene trigger e un comando SQL *delimiter*.
* **ACSD-50512** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge *Errore: il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova.* errore che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto.
* **ACSD-50949** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il filtro del prezzo in Ricerca avanzata non restituisce risultati corretti se utilizzato con il filtro SKU.
* **ACSD-51645** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge l&#39;errore generato durante il salvataggio di una nuova regola prezzo carrello se l&#39;estensione `Magento_OfflineShipping` è disabilitata.
* **ACSD-50895** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where [!DNL Google Analytics] 3 I tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
* **ACSD-51102** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where a catalog rule that is applied to a large number of products is not correctly indexed when the rule is enabled by a scheduled update.
* **ACSD-50368** (per Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corregge il problema per cui `group_id` del cliente viene ignorato quando viene creato un cliente tramite API REST asincrona o API REST in blocco asincrono.
* **ACSD-51497** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7): è stato risolto un problema che impediva al cliente di ordinare una pagina di catalogo per attributo personalizzato del tipo a discesa.
* **ACSD-51408** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt; 2.4.7) - Corregge il problema se lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL Backordered]*.
* **ACSD-51735** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge il problema per cui lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando lo stock del prodotto è *0*.
* **ACSD-51792** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where a page does not have the impression event when [!DNL Google Tag Manager] 4 è abilitato.
* **ACSD-51471** (per Adobe Systems Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where an admin user cannot save a scheduled update for a bundled product that uses a simple product that itself has a scheduled update.
* **ACSD-51700** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge l&#39;errore che si verifica quando si passa da una visualizzazione archivio a un&#39;altra pagina di modifica prodotto scaricabile nell&#39;amministratore.
* **ACSD-51120** (per Adobe Commerce >=2.3.7 &lt;2.4.3) - Corregge il problema per cui la cache delle richieste GraphQL GET non viene cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging.
* **ACSD-51240** (per Adobe Commerce >=2.4.4 &lt;2.4.6) - Corregge il problema di mancanza del file caricato se la registrazione viene effettuata tramite il modulo di registrazione della società.
* **ACSD-51907** (per Adobe Commerce >=2.4.2 &lt;2.4.3) - Corregge il problema per cui un utente amministratore con restrizioni non può creare una nota di credito con un rimborso offline.
* **ACSD-52148** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema relativo a errori occasionali di accesso dell&#39;amministratore [!DNL Google V3 reCAPTCHA].
* **ACSD-51431** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo allo stato dell&#39;indicizzatore *working* anche se non sono presenti nuove voci nel changelog.
* **ACSD-51892** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema di prestazioni, in cui i file di configurazione vengono caricati più volte.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui [!UICONTROL Page Builder's] errori multipli impediscono all&#39;amministratore di salvare un prodotto senza autorizzazioni per il contenuto.
* **ACSD-51305** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che impediva la disponibilità di prodotti secondari configurabili esauriti nella risposta di GraphQL.
* **ACSD-50621** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui [!UICONTROL Tier Prices] per siti Web diversi nel catalogo condiviso non sono visibili quando si tenta di modificarli in un ambiente con più siti Web.
* **ACSD-51041** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - Migliora le prestazioni dell’indicizzatore dei prezzi.
* **ACSD-51379** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui le modifiche apportate al contenuto del testo della pagina tramite [!UICONTROL Page Builder] non vengono salvate.
* **ACSD-49480** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Risolve il problema relativo all&#39;applicazione di una sola regola di prezzo al carrello.
* **ACSD-51230** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema di eliminazione dell&#39;account gift card quando viene elaborato un rimborso parziale di un prodotto semplice da un ordine.
* **ACSD-51238** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Risolve il problema della rimozione dell&#39;origine inventario durante l&#39;aggiornamento dei prodotti configurabili e la modifica del prezzo.
* **ACSD-50794** (per Adobe Commerce >=2.4.1 &lt;2.4.7) - Corregge il problema per cui i dettagli del messaggio regalo o del pacchetto regalo non vengono aggiornati nel database quando vengono rimossi tramite GraphQL.
* **ACSD-51528** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema se la colonna *x_forwarded_for* contiene valori Null nella tabella *sales_order*.
* **ACSD-50849** (per Adobe Commerce >=2.4.4 &lt;2.4.6): è stato risolto il problema che causava una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti quando si aggiungeva un nuovo prodotto alla categoria dopo aver cancellato la cache.
* **ACSD-51294** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui prezzo GTM/GA, quantità, imposte, spedizione e ricavi vengono inviati come stringa a [!DNL Google Analytics] e GTM.
* **ACSD-51204** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Risolve il problema che impediva la restituzione di un prodotto completamente venduto in magazzino dopo la creazione di una nota di credito.
* **ACSD-51291** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Corregge il problema per cui un amministratore con accesso limitato a un sito web può aggiungere immagini/video al prodotto assegnato a più siti web.
* Added new versions for ACSD-50336.
* Replaced patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Fixes the issue where Recaptcha v2 does not reload after submitting a failed payment.
* **ACSD-50817** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): ottimizza il processo Cron `sales_clean_quotes` per un&#39;esecuzione più rapida.
* **ACSD-49392** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corregge il problema se lo stato dell&#39;ordine cambia in chiuso dopo un rimborso parziale per un prodotto nel pacchetto.
* **ACSD-51036** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where race conditions during concurrent REST API calls result in an overwrite of shipping status information in the [!UICONTROL Items Ordered] table.
* **ACSD-50858** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Improves performance for loading banners contents.
* Added new versions for MDVA-39305-v2, ACSD-45169.
* Updated patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (per Adobe Commerce e Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Corregge il problema per cui le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo disponibile o il prezzo viene modificato.
* **ACSD-50367** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;esportazione dell&#39;indirizzo del cliente non funziona quando viene creato un attributo dell&#39;indirizzo del cliente a selezione multipla senza valori.
* **ACSD-49877** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui la riproduzione automatica video non funziona sul dispositivo mobile [!DNL Safari] quando il video è collegato direttamente a un file video remoto e non a un servizio di streaming.
* **ACSD-50165** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l&#39;errore *Impossibile eliminare il file. Avviso!unlink: file o directory non esistente* durante lo svuotamento della cache JS/CSS dall&#39;amministratore.
* **ACSD-49737** (per Adobe Commerce e Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Risolve il problema relativo al caso in cui un coupon viene contrassegnato in modo errato come utilizzato dopo un pagamento con carta non riuscito.
* **ACSD-50814** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che impediva a un utente amministratore di creare una nota di credito.
* **ACSD-50116** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui un utente amministratore non può creare una riscrittura URL per sottocategorie di livello 3 o inferiore.
* **ACSD-49513** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5): è stato risolto il problema che impediva la sincronizzazione dell&#39;archiviazione remota a causa di file da 0 byte.
* **ACSD-46683** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo al prezzo di spedizione, che indica *Non ancora calcolato*.
* **ACSD-49129** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui l&#39;attributo *[!UICONTROL content]* (codice immagine base64) non viene restituito nelle risposte API dei supporti di prodotto `rest/V1/products/sku/media`.
* **ACSD-50276** (per Adobe Commerce >=2.4.0 &lt;2.4.7) - Risolve il problema relativo al mancato funzionamento del modulo di registrazione cliente nella vetrina se viene creato un attributo cliente a selezione multipla.
* **ACSD-50527** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge l&#39;errore che si verifica quando si salva una pagina con un blocco dinamico vuoto.
* **ACSD-49973** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Migliora le prestazioni del recupero dei prodotti in bundle tramite GraphQL.
* **ACSD-51114** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a random product disappears from large catalogs when asynchronous indexing is enabled. Migliora le prestazioni della reindicizzazione asincrona per cataloghi di grandi dimensioni.
* **B2B-2598** (per le query Adobe Systems Commerce e Magento Open Source >=2.4.4[!UICONTROL availableStores]&lt;2.4.7) - Add caching capability to the  , [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency]e [!UICONTROL storeConfig] GraphQL.
* Nuove versioni aggiunte per MDVA-42806, ACSD-48627, ACSD-46815.
* Patch aggiornate metadati per ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a ready-to-pick-up email is sent by API when the order is not ready for pickup.
* **ACSD-49822** (per Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where updates in the [!UICONTROL Requisition List] non vengono riflessi in [!UICONTROL Print Requisition List].
* **ACSD-48771** (per le versioni Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue with upgrading the column-block content type from older [!DNL Page Builder] .
* **ACSD-49464** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema che impedisce lo spostamento di fatture, spedizioni e note di accredito dall&#39;archivio se l&#39;ID ordine è diverso.
* **ACSD-49773** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema se l&#39;esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archivio remoto.
* **ACSD-49748** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Risolve il problema che impediva l&#39;invio degli inviti.
* **ACSD-49502** (per Adobe Commerce >=2.4.3 &lt;2.4.7): è stato risolto il problema che impediva l&#39;aggiornamento corretto del collegamento scaricabile dopo l&#39;applicazione di un aggiornamento di staging al prodotto scaricabile.
* **ACSD-49527** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the default value is saved for a visual swatch attribute when no value is selected.
* **ACSD-49835** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui il valore della casella di controllo Usa predefinito non viene salvato correttamente a livello di archivio per un attributo a selezione multipla.
* **ACSD-49898** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6): è stato risolto il problema che causava la generazione di un&#39;eccezione da parte della griglia prodotti quando un prodotto incluso aveva un prezzo speciale superiore a 1000.
* **ACSD-50234** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.5) - Risolve il problema relativo al nome del cliente errato nell&#39;e-mail di conferma se si effettua un ordine con [!DNL PayPal].
* **ACSD-49960** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui il filtro per data non funziona per la griglia degli ordini cliente.
* **ACSD-49849** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema relativo alla sostituzione dell&#39;e-mail del cliente con [!DNL PayPal] al momento dell&#39;ordine con [!DNL PayPal Express] tramite GraphQL.
* **ACSD-49839** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione di Shared Catalog Pricing e alla struttura genera un errore in Amministratore quando i prodotti presentano virgolette singole o doppie in SKU.
* **ACSD-49970** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge la gestione errata degli errori di GraphQL quando il reporting [!DNL New Relic] è attivato.
* **ACSD-50260** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema per cui i risultati della ricerca prodotti GraphQL sono limitati solo a 10.000.
* **ACSD-48813** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui la ricerca non mostra risultati rilevanti in base al peso della ricerca degli attributi.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corregge il problema per cui una regola del prezzo di catalogo creata in base all&#39;attributo Sì/No non considera l&#39;ambito selezionato.
* **ACSD-47704** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione del prezzo dei soli prodotti in magazzino nel prodotto in bundle.
* **ACSD-49370** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;attributo di prodotto *Date Time* ha un tipo *FilterMatchTypeInput* nello schema di GraphQL.
* **ACSD-48807** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corregge il problema per cui le recensioni dei prodotti dei clienti non vengono filtrate tramite storeview tramite GraphQL.
* **ACSD-49433** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui l&#39;importo predefinito viene visualizzato come subtotale nel carrello della gift card con un importo aperto.
* **ACSD-48866** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema che si verifica in caso di errore durante la richiesta del feed RSS per le categorie.
* **ACSD-48784** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla memorizzazione errata nella cache dei prezzi del segmento cliente tra i gruppi di clienti.
* **ACSD-48857** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui un utente non è in grado di salvare le modifiche dopo averle modificate con Page Builder.
* **ACSD-49065** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli elementi delle virgolette non sono visibili nell&#39;amministratore se assegnati solo alle azioni personalizzate.
* **ACSD-49179** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui nel rapporto Ordini vengono visualizzati importi non corretti in caso di valute diverse per negozi diversi.
* **ACSD-49286** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Risolve il problema relativo all&#39;aggiunta di un prodotto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.
* **ACSD-49574** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Aggiunge funzionalità per supportare gli aggiornamenti dei prodotti Gift Card nel carrello tramite GraphQL.
* Aggiornamento della patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (per Adobe Commerce >=2.4.1 &lt;2.4.7) - Corregge il problema relativo all&#39;utilizzo dell&#39;indirizzo di spedizione predefinito anziché di uno nuovo quando si effettua un ordine utilizzando un preventivo negoziabile.
* **ACSD-48059** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli esercenti non possono salvare &quot;[!UICONTROL Match product by rule]&quot; nella categoria.
* **ACSD-48216** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the issue where [!UICONTROL AUTO_INCREMENT] degli aumenti della [!UICONTROL inventory_source_item] tabella sull&#39;operazione [!UICONTROL UPDATE] .&lt;/2.3.8>
* **ACSD-47908** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the error &quot;A value less than or equal to 0 is expected&quot; when selecting the source and qty on the shipping step during checkout.&lt;/2.3.8>
* **ACSD-49497** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where an order remains in the processing state after shipment and a partial refund is applied.
* **ACSD-48694** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.1 &lt;2.4.7) - Fixes the issue where the error &quot;Invalid state change requested&quot; prevents a customer from placing an order.&lt;/2.3.8>
* **ACSD-49013** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where email confirmation is not translated to the website locale when creating customers using bulk API.
* **ACSD-48164** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where a restricted admin cannot save a website-level value.
* **ACSD-48404** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where &quot;Remember Category Pagination = Yes&quot; causes an error when pressing the browser&#39;s back button.
* **ACSD-48634** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes JS errors on a staging update page when &quot;[!UICONTROL Google Analytics Content Experiments]&quot; è abilitato.
* **ACSD-49042** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where a product with infinite backorder cannot be ordered from the Storefront.
* Patch aggiornate: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (per Adobe Commerce e Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Corregge il problema per cui le notifiche di calo del prezzo non vengono sempre inviate a causa del caching a livello di applicazione.
* **ACSD-48661** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema per cui se il limite di credito della società è maggiore di 999, il separatore di virgola impedisce il salvataggio della società a causa di un errore di convalida.
* **ACSD-48773** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il modello e-mail dei punti premio viene prelevato dall&#39;archivio errato.
* **ACSD-48587** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo alla mancata visualizzazione dei prodotti corrispondenti da parte dei caratteri speciali HTML nelle regole di corrispondenza dei widget prodotti.
* **ACSD-48212** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where product import assigns the product to the wrong source.
* **ACSD-47988** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where product export trims HTML tags from the page builder product description.
* **ACSD-48366** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the product image is not displayed on the Back to Stock email template.
* **ACSD-48417** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where an SQL error appears after creating a schedule change for a product and saving another product.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Risolve il problema relativo al mancato funzionamento della reindicizzazione del prezzo del prodotto se il prodotto bundle non è assegnato ad alcun sito Web.
* **ACSD-48262** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui i prodotti non sono visibili sul front-end quando &quot;Consenti tutti i prodotti per pagina&quot; è impostato su Sì.
* **ACSD-48293** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corregge il problema relativo all&#39;esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte.
* **ACSD-47520** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema della perdita di punti premio da parte dei clienti durante la creazione di una nota di credito.
* **ACSD-48044** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema che impedisce l&#39;inserimento di ordini quando si applicano più carte regalo a un singolo ordine con spedizione multipla.
* **ACSD-48300** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where a return cannot be created if the configurable product is removed.
* **ACSD-47910** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue of missing orders, invoices, shipments, and credit memos in respective entity grids.
* **ACSD-47292** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where out-of-stock bundled products are not available in the GraphQL response if the &quot;show out-of-stock products&quot; is set to Yes.
* **ACSD-48234** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the catalog search result shows an incorrect category item count when the &quot;show out of stock&quot; option is enabled.
* **ACSD-48313** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Fixes the issue where the &quot;configurable_variations&quot; column is not parsed if the attribute value contains a comma. Lo stesso algoritmo di analisi viene utilizzato per &quot;additional_attributes.
* **ACSD-48627** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the out-of-stock configurable product causes an error when sending a GraphQL request to get cart details.
* Patch aggiornata: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where SEO-friendly URLs are not generated for products that have *url_key* attributi ignorati a livello di visualizzazione store.
* **ACSD-46865** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the Shipment and Credit Memo grid is not populated when asynchronous indexing is enabled.
* **ACSD-47004** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui l&#39;IVA non viene applicata a un indirizzo di fatturazione senza un ID IVA.
* **ACSD-47803** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6): è stato risolto il problema che causava la visualizzazione dei campioni di prodotto configurabili esauriti come disponibili.
* **ACSD-47137** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Migliora la velocità di caricamento della galleria di immagini quando la cartella pub/media è molto grande.
* **ACSD-46770** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui le e-mail degli ordini amministratore vengono inviate anche quando la *conferma dell&#39;ordine e-mail* non è selezionata.
* **ACSD-47955** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui GraphQL non visualizza correttamente lo sconto sul carrello.
* **ACSD-46617** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui il pulsante *Continua a estrarre* è disattivato anche se il subtotale è maggiore dell&#39;*importo ordine minimo* configurato.
* **ACSD-47079** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge il problema per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei sottoprodotti cambia tramite REST API POST /rest/V1/inventory/source-items.
* **ACSD-47336** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Correzioni *Si è verificato un errore.* errore durante l&#39;eliminazione delle notifiche nell&#39;amministrazione di Commerce.
* **ACSD-47559** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema se l&#39;area Anteprima modello e-mail non è completamente visibile.
* **ACSD-47920** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui è possibile effettuare ordini tramite l&#39;API REST come utente guest anche quando *Consenti estrazione utenti guest* è disattivato.
* Patch sostituite: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui un amministratore con accesso limitato a un ambito specifico non può eliminare le revisioni dei prodotti.
* **ACSD-47107** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Risolve il problema relativo all&#39;applicazione dello sconto Regola prezzo catalogo alle opzioni di prodotto personalizzate.
* **ACSD-47232** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema che impediva l&#39;applicazione di coupon con condizioni di peso totale nell&#39;amministratore.
* **ACSD-46519** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6) - Corregge il problema se la richiesta categoryList di GraphQL restituisce un valore product_count errato per una categoria di ancoraggio.
* **ACSD-47027** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge una richiesta GraphQL updateCompanyRole lenta.
* **ACSD-47666** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema relativo al mancato funzionamento della funzione filtro nella griglia Amministrazione > Sistema > Autorizzazioni > Ruoli utente > Ruolo > Utenti ruolo.
* **ACSD-47497** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui la scheda Servizi non è visibile in Configurazione in Amministrazione.
* Updated patch: ACSD-47743.
* Replaced patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.3) - Fixes the _Trying to access array offset on value of type bool_ error when accessing certain non-existing category paths for known products on PHP 7.4.
* **ACSD-47332** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where cron fails with an error that is only reported when running between 00:00 and 00:59 UTC.
* **ACSD-47280** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui la disattivazione della funzione di catalogo condiviso in un ambito specifico non funziona correttamente.
* **ACSD-47106** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Risolve il problema che impediva il salvataggio di un valore in un nuovo attributo personalizzato nella pagina di creazione di una società.
* Updated patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where a user gets an error when assigning a large number of product sources.
* **ACSD-46856** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Improves performance updating tier prices via System > Configuration > Import > Advanced Pricing.
* **ACSD-46541** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema per cui un utente amministratore non può creare una nota di credito se viene eliminato un articolo dell&#39;ordine.
* **ACSD-46581** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui il totale imposte stimato non viene aggiornato dopo aver selezionato un  nel carrello.
* **ACSD-46618** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema che causava la visualizzazione di prezzi non corretti nella cache da parte del widget elenco prodotti per un cliente connesso.
* **ACSD-46674** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema della visualizzazione delle opzioni personalizzate di un tipo di immagine come HTML nelle e-mail dei clienti.
* **ACSD-46988** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui la richiesta API &quot;currency&quot; di GraphQL restituisce valori NULL per una valuta personalizzata.
* **ACSD-47076** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) - Corregge il problema che impedisce la riproduzione di video Vimeo nella vetrina.
* **ACSD-45071** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Risolve il problema relativo all&#39;aggiunta dell&#39;origine predefinita al prodotto durante l&#39;importazione.
* **AC-3023** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Aggiorna lo schema DHL alla versione 10.0 più recente.
* Patch aggiornate: MDVA-42584.
* Patch sostituite: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema se un utente ottiene uno stato dell&#39;ordine errato quando viene rimborsato utilizzando il credito dell&#39;archivio.
* **ACSD-46703** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corregge il problema se non è possibile trascinare opzioni personalizzate in una pagina di modifica del prodotto.
* **ACSD-44851** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corregge il problema che impediva l&#39;apertura o l&#39;espansione di una categoria con sottocategorie.
* **ACSD-46815** (*per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6*) - Corregge il problema se la richiesta della struttura delle categorie è limitata a 20 categorie.
* **ACSD-45675** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6*) - Corregge il problema se l&#39;esportazione del prodotto utilizza nomi di categoria dell&#39;ambito *Visualizzazione archivio predefinita*.
* **ACSD-46869** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6*) - Corregge il problema se un prodotto configurabile in un carrello non viene aggiornato tramite una richiesta REST API *di* PUT senza modificare la quantità del prodotto.
* **MDVA-42768-V2** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui il prezzo regolare del prodotto configurabile è *0* quando *Visualizzazione esaurita* è *Sì*.
* Patch aggiornate: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Patch obsoleta: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema se la richiesta della struttura delle categorie è limitata a 20 categorie.
* **ACSD-45781** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Corregge il problema per cui il campo di ricerca front-end dell&#39;archivio non viene visualizzato su dispositivi mobili.
* **ACSD-46192** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;2.4.5*) - Corregge il problema relativo all&#39;utilizzo dell&#39;endpoint `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corregge il problema per cui un utente amministratore non può accedere dopo l&#39;aggiornamento alla versione 2.4.4.
* Patch aggiornate: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui una mutazione di prodotto GraphQL per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all&#39;archivio richiesto.
* **ACSD-46146** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corregge il problema per cui vengono inviate due e-mail di conferma dell&#39;ordine dopo aver effettuato un ordine dall&#39;amministratore.
* **ACSD-45255** (*per Adobe Commerce >=2.4.3 &lt;2.4.6*) - Corregge un&#39;eccezione nella pagina Report scorte limitate per un utente amministratore con restrizioni.
* **ACSD-45488** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Corregge il problema per cui un prodotto configurabile con più origini non viene restituito automaticamente a In Stock.
* **ACSD-45754** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui i punti premio non vengono aggiunti dopo l&#39;applicazione di un coupon al carrello.
* **ACSD-45849** (*per Adobe Commerce >=2.4.3 &lt;2.4.4*) - Corregge il problema della perdita dei metadati video dopo l&#39;applicazione di un aggiornamento di staging.
* **ACSD-45257** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Corregge il problema per cui GraphQL non visualizza correttamente uno sconto sul carrello.
* **ACSD-44938** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema per cui `VAT_ID` non può essere applicato in una richiesta GraphQL per un utente guest.
* Patch aggiornate: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corregge il problema relativo al calcolo errato della quantità di azioni per un prodotto virtuale dopo la creazione di una nota di credito.
* **ACSD-43887** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema della visualizzazione di dettagli non corretti nella pagina Pagamento di pagamento di pagamento di pagamento quando gli ordini di acquisto per le società sono abilitati.
* **ACSD-45143** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema per cui la mutazione `setShippingAddressesOnCart` non consente di impostare il codice di area numerico come *region*.
* **ACSD-44591** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.6*) - Corregge l&#39;errore che si verifica quando un ordine viene effettuato senza conferma CAPTCHA.
* **ACSD-45520** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Corregge il problema per cui le opzioni dei campioni non sono preselezionate nella pagina dei dettagli del prodotto quando un utente modifica prodotti configurabili dal carrello.
* **ACSD-45169** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.6*) - Corregge il problema per cui [!DNL Visual Merchandiser] non visualizza il prezzo e le azioni corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento di staging.
* **ACSD-45424** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.6*) - Corregge il problema di creazione di una compensazione di prenotazione non corretta dopo un rimborso parziale (nota di credito).
* **MDVA-42807** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Corregge il problema per cui il segno di valuta personalizzato non viene visualizzato nella parte anteriore dell&#39;archivio.
* Aggiornate patch: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui i totali degli ordini nel report Ordini vengono calcolati in modo errato per l&#39;utente amministratore con restrizioni.
* **MDVA-44940** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge l&#39;errore SQL che si verifica durante il salvataggio della categoria dall&#39;amministratore.
* **MDVA-44562** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Risolve il problema per cui l&#39;ID store non predefinito per le voci di citazione viene sovrascritto dall&#39;ID store predefinito, nonostante il richiesta GraphQL provenga dalla vista store non predefinita.
* **MDVA-43167** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui l&#39;azione di massa della griglia degli ordini amministratore non viene applicata a più pagine quando l&#39;utente amministratore seleziona tutti gli ordini.
* **MDVA-44044** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corregge il problema che impedisce la visualizzazione di un prodotto nella pagina della categoria dopo l&#39;assegnazione a un nuovo sito Web.
* **MDVA-42509** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corregge il problema relativo all&#39;impossibilità di caricare un file CSV per un ordine rapido, causando un errore *Impossibile inviare il cookie*.
* Patch aggiornate: MDVA-41061, MDVA-42584.
* Il prefisso per le nuove patch [!DNL Quality Patches Tool] verrà modificato da *MDVA* a *ACSD* a causa di modifiche di processo interne.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Risolve il problema per cui un articolo aggiuntivo non può essere aggiunto al carrello quando il valore minimo dell&#39;articolo è già nel carrello.
* **MDVA-44887** (*per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corregge l&#39;errore *Uncaught SyntaxError: Errore &#39;const&#39;* token imprevisto nel pannello di amministrazione.
* **MDVA-43718** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0*&lt;2.4.5 ) - Correzioni *Il consumatore non è autorizzato a accesso %risorse.* Errore visualizzato quando si accede a un catalogo condiviso da un&#39;integrazione personalizzata.
* **MDVA-44660** (*per Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corregge il problema per cui non è possibile utilizzare il carattere accento grave ``` ` ``` per il nome e il cognome di un cliente.
* **MDVA-40896** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge l&#39;errore *Errore: TypeError: l&#39;argomento 3 passato al Magento* nell&#39;API di massa del prodotto asincrono.
* **MDVA-38559** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corregge l&#39;errore */V1/customers/search API* per i clienti con più abbonamenti.
* **MDVA-44533** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.4*) - Risolve il problema relativo all&#39;applicazione errata dello sconto a un prodotto secondario del bundle.
* Patch aggiornate: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui i prodotti *Non visibili singolarmente* continuano a essere visualizzati nei risultati della ricerca avanzata nel catalogo.
* **MDVA-44100** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui tutti gli FPT vengono assegnati all&#39;ultimo prodotto nel carrello e reimpostati per altri prodotti.
* **MDVA-43605** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui i dati dell&#39;ordine restituiscono valori negativi per i totali delle righe quando si utilizza l&#39;API Rest.
* **MDVA-43102** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui la quantità vendibile non viene aggiornata correttamente quando viene effettuato un rimborso tramite API REST.
* **MDVA-43178** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Risolve il problema per cui un token cliente per un store personalizzato non può essere recuperato in GraphQL.
* **MDVA-43859** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Risolve il problema in cui l&#39;errore *Nessuna entità con customerId =* viene registrata quando un cliente eliminato tenta di accedere.
* **MDVA-44147** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Risolve il problema per cui un richiesta GraphQL non restituisce gli elenchi di richieste.
* **MDVA-44505** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Risolve i problemi in cui GraphQL Applying Reward Punti non aggiorna il totale complessivo e in cui store credito viene applicato più volte durante il posizionamento dell&#39;ordine.
* Patch aggiornate: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge il problema relativo al funzionamento della regola prodotto correlata solo quando Segmento cliente è impostato su *All*.
* **MDVA-39605** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il valore TTL (data di scadenza) della cache Redis è errato.
* **MDVA-43862** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corregge il problema per cui il cliente non può aggiornare gli elementi del carrello a causa di un errore *UpdateCartItems* di GraphQL.
* **MDVA-43824** (*per Adobe Systems Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 ||=&quot;&quot;>=2.4.1 &lt;2.4.5*) - Risolve il problema a causa del quale viene visualizzato un errore durante l&#39;annullamento degli ordini con uno sconto.&lt;/=2.3.7-p3>
* **MDVA-43451** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3*&lt;2.4.5 ) - Risolve il problema in cui l&#39;errore *Impossibile trovare il store richiesto. Verifica l&#39;store e riprova.* Viene visualizzato durante la configurazione di un catalogo condiviso per un sito Web specifico.
* **MDVA-43491** (*per Adobe Systems Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Risolve il problema per cui l&#39;etichetta dell&#39;immagine di base non si aggiorna durante l&#39;importazione di prodotti per un sito Web store contenuti.
* **MDVA-43601** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema dei trigger mancanti dopo la reindicizzazione completa.
* **MDVA-42046** (*per Adobe Systems Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 ||=&quot;&quot;>=2.4.0 &lt;2.4.5*) - Risolve il problema per cui un valore non corretto viene assegnato a un attributo del prodotto con un campo di immissione della data durante l&#39;aggiornamento di un prodotto.&lt;/=2.3.5-p2>
* **MDVA-43935** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Risolve il problema per cui il prodotto Upsell viene mostrato due volte.
* **MDVA-44188** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3*&lt;2.4.5 ) - Risolve il problema per cui le e-mail emesse dal sistema con `.-` indirizzi non vengono inviate.
* **MDVA-42283** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema per cui il formato data-ora nella griglia dell&#39;ordine di amministrazione per la lingua Francese è non valido.
* Patch aggiornate: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Sono state aggiunte patch metadati per .[!DNL Site-Wide Analysis Tool]

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui l&#39;utente è in grado di modificare l&#39;ora di inizio di un aggiornamento pianificato attivo.
* **MDVA-42410** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui nei report coupon viene visualizzata solo la valuta di base predefinita.
* **MDVA-41136** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema che impedisce l&#39;estensione della data di scadenza di `mage-cache-sessid`, causando la pulizia dei dati del cliente.
* **MDVA-39993** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Corregge il problema per cui le modifiche di inventario eseguite tramite API non si riflettono sulla pagina del prodotto sul front-end.
* **MDVA-42855** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui un nuovo indirizzo del cliente non viene salvato nella rubrica durante l&#39;estrazione.
* **MDVA-42645** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.
* **MDVA-43414** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Corregge l&#39;errore irreversibile PHP che si verifica durante l&#39;esecuzione del consumer di coda `inventory.reservations.updateSalabilityStatus` negli SKU numerici.
* **MDVA-41628** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Corregge il problema per cui gli utenti amministratori con restrizioni esistenti accedono alle nuove risorse quando vengono aggiunti nuovi moduli.
* **MDVA-43348** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la richiesta GraphQL di gift card visualizza un errore se `gift_card_options` contiene *uid*.
* **MDVA-39546** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui la data di inizio per l&#39;aggiornamento dello staging potrebbe essere impostata su una data precedente a quella corrente durante la modifica.
* **MDVA-42950** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema della mancata riproduzione dei video nella pagina del prodotto.
* **MDVA-42689** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui Adobe Commerce genera un errore *Violazione del vincolo di integrità* durante l&#39;aggiornamento delle categorie di prodotti durante l&#39;importazione.
* **MDVA-41229** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui le immagini disponibili nel back-end non vengono visualizzate nel front-end dopo l&#39;importazione di prodotti configurabili.
* **MDVA-43731** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui *Sinonimi di ricerca* non funzionano più quando viene aggiunto valore in *Termini minimi da abbinare*.
* **MDVA-43232** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser] in base al prezzo speciale Inferiore/Superiore causa un errore durante il salvataggio della categoria.
* **MDVA-43726** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui la regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio non viene applicata dopo la reindicizzazione parziale.
* Patch aggiornate: MDVA-36464, MDVA-37478, MDVA-38608.
* Sono stati aggiunti i metadati delle patch per [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui gli attributi del prezzo del prodotto non possono essere aggiornati per un sito Web specifico tramite API REST.
* **MDVA-41350** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo alla generazione di un&#39;eccezione quando un utente amministratore con accesso limitato aggiunge un prodotto al di fuori del proprio ambito di ruolo da parte di SKU in un ordine.
* **MDVA-42269** (*per Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corregge il problema che impedisce a un utente amministratore di accedere all&#39;amministratore a causa di *Errore di tipo: strtotime() prevede che il parametro 1 sia una stringa, null specificato* errore.
* **MDVA-40830** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il credito dell&#39;archivio viene applicato più volte durante il posizionamento dell&#39;ordine.
* **MDVA-42237** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema che impedisce l&#39;aggiornamento di un prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del relativo sottoprodotto.
* **MDVA-42520** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema di applicazione dell&#39;aliquota due volte se si utilizza *Abilita commercio transfrontaliero*.
* Patch aggiornate: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleta: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*per Adobe Systems Commerce e Magento Open Source >=2.3.2*&lt;2.4.5 ) - Risolve il problema per cui l&#39;aggiornamento dell&#39;attributo mass crea URL riscrittura per Default Store solo dopo aver modificato *la visibilità del* prodotto.
* **MDVA-43091 (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 *) - Risolve il problema per cui ordinare un prodotto in bundle dall&#39;amministratore nel backend dà l&#39;errore*Non è possibile utilizzare quantità decimali per questo prodotto *.***
* **MDVA-40816** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-41305** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la mutazione GraphQL non restituisce opzioni di prodotto configurabili dopo l&#39;aggiunta del prodotto alla lista dei desideri.
* **MDVA-39181** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-42584** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui lo stato delle scorte configurabili nel backend non viene aggiornato dopo la modifica della quantità e dello stato delle scorte tramite Importazione o API.
* **MDVA-40175** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corregge il problema per cui *Fare clic per modificare il metodo di spedizione* non mostra i pulsanti di scelta per selezionare i metodi di spedizione nell&#39;amministratore durante il riordino.
* **MDVA-42768** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il prezzo regolare del prodotto configurabile è 0 quando *Visualizzazione esaurita* è Sì.
* **MDVA-43201** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema per cui si verifica un errore nell&#39;login del cliente quando si utilizza l&#39;attributo DOB con determinate impostazioni locali.
* Patch aggiornate: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo al malfunzionamento dei filtri data quando il fuso orario di Adobe Commerce è diverso da quello dell&#39;ambiente locale.
* **MDVA-42657** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di selezionare le categorie nelle condizioni del segmento cliente.
* **MDVA-42806** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema per cui un&#39;e-mail *registrazione* di una società Nuovo viene inviata ogni volta che un&#39;azienda esistente viene aggiornata tramite API REST.
* **MDVA-37984** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1*&lt;2.4.5 ) - Risolve il problema per cui la [!DNL Visual Merchandiser] *funzionalità Abbina prodotto per regola* non filtra correttamente i prodotti con aggiornamenti di staging.
* **MDVA-40488** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema per cui i prodotti configurabili con prodotti figlio esauriti non vengono visualizzati nella fascia di prezzo corretta.
* **MDVA-42507** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Risolve il problema per cui la cache dell&#39;intera pagina viene pulita dopo l&#39;applicazione dell&#39;aggiornamento di staging per il carrello regola.
* **MDVA-39163** (*per Adobe Systems Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Risolve il problema per cui i metodi di spedizione non sono disponibili quando viene registrato un nuovo utente e i prodotti nel carrello provengono dalla sessione ospite.
* **MDVA-38626** (*per Adobe Systems Commerce e Magento Open Source >=2.3.3*&lt;2.4.5 ) - Risolve il problema per cui il utente amministratore non è in grado di effettuare un ordine sul back-end utilizzando il [!DNL PayPal Payflow Pro] pagamento.
* **MDVA-38666** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.3.6*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di modificare le opzioni di prodotto configurabili nel carrello del cliente.
* **MDVA-38526** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di accedere a [!DNL Site-Wide Analysis tool].
* Patch aggiornate: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui gli utenti ricevono l&#39;errore 500 dopo aver impostato il cookie *mage-messages*, se esiste già, ma non sono presenti nuovi messaggi.
* **MDVA-41139** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*): è stato risolto il problema che causava la perdita di scorte dei prodotti configurabili dopo l&#39;importazione quando per una delle relative origini veniva utilizzato il parametro qty=0 di un prodotto semplice.
* **MDVA-42326** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui i clienti ricevono un errore al momento del pagamento dopo un timeout della sessione anche se il carrello acquisti persistente è abilitato.
* **MDVA-42341** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui la query GraphQL `categoryList` non filtra i risultati se una richiesta ha l&#39;intestazione Store.
* **MDVA-38393** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui le regole del catalogo cessano di funzionare per un prodotto configurabile se il relativo prodotto semplice viene rinominato.
* **MDVA-39153** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per il quale l&#39;importo dello sconto viene calcolato in modo errato durante il riordino in Amministrazione.
* Patch aggiornate: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui gli utenti amministratori non possono accedere alla griglia del cliente dopo l&#39;eliminazione del sito Web.
* **MDVA-40311** (*per Adobe Commerce e Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Corregge il problema che causa la visualizzazione del messaggio di errore *Sicurezza o chiave modulo non valida. Aggiornare la pagina* dopo l&#39;accesso all&#39;amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata.
* **MDVA-41631** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema che si verifica quando si riceve un errore durante il tentativo di recuperare informazioni sull&#39;ordine senza un valore *phone* facoltativo tramite GraphQL.
* **MDVA-27239** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Corregge il problema della mancata visualizzazione dei prodotti di cross-selling.
* Patch aggiornate: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.4*) - Corregge il problema relativo ai prodotti mancanti sul front-end durante la reindicizzazione.
* **MDVA-40120** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema che impedisce l&#39;utilizzo dell&#39;ordinamento GraphQL in base a DESC/ASC con prodotti che hanno la stessa rilevanza o prezzo.
* **MDVA-41399** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui gli utenti amministratori non sono in grado di accedere alla pagina *Gestisci carrello* se un cliente aggiunge un prodotto alla lista dei desideri.
* **MDVA-40609** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema relativo all&#39;assenza di dati di prodotti disabilitati nella tabella indice `cataloginventory_stock_status`, con la visualizzazione di quantità di prodotti disabilitati errate.
* **MDVA-39031** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui è possibile aggiungere un prodotto al carrello tramite GraphQL anche se non è assegnato al sito Web di destinazione.
* **MDVA-41597** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema che si verifica quando si aggiunge più di un prodotto configurabile al carrello tramite GraphQL.
* **MDVA-27456** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.3.7*) - Corregge il problema che causa un errore agli utenti che tentano di caricare [!DNL Swagger].
* **MDVA-32776** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui lo stato delle scorte non viene aggiornato quando viene effettuato un ordine ma non viene spedito.
* **MDVA-30862** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Corregge il problema con la data ordine errata nella fattura PDF stampata.
* È stata migliorata la pagina indice per [!DNL Quality Patch Tool]. Sono stati aggiunti una pratica funzione di ricerca e filtro per [!DNL quality patches] all&#39;ultima versione dello strumento.
* Patch aggiornate: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema se non è possibile creare un nuovo aggiornamento pianificato o modificarne uno esistente se la data di fine è stata precedentemente rimossa.
* **MDVA-41046** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema della disponibilità di prodotti semplici con opzioni personalizzate da assegnare a prodotti configurabili/raggruppati.
* **MDVA-40545** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema relativo al recupero del solo primo nodo di una pagina, anche se per la stessa pagina erano presenti più nodi.
* **MDVA-41164** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Corregge il problema per cui un utente amministratore non è in grado di salvare o modificare un&#39;azienda con un attributo cliente personalizzato di tipo file o immagine.
* **MDVA-39229** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema che causa la visualizzazione del seguente errore dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento dell&#39;aggiornamento dell&#39;ambiente di gestione temporanea della regola del catalogo: *Errore di staging_synchronize_entities_period del processo Cron: impossibile eliminare l&#39;aggiornamento attivo.*
* **MDVA-40619** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui le modifiche alla gerarchia delle pagine di CMS causano un errore 500 quando si tenta di eseguire la modifica in linea in una pagina di CMS.
* **MDVA-41061** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema se lo stato delle scorte viene reimpostato su vendibile quando un prodotto viene salvato dall&#39;amministratore.
* **MDVA-31763** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema di ripristino (o mancata applicazione) delle regole dei prezzi di catalogo fino alla reindicizzazione manuale.
* **MDVA-37748** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema se una query GraphQL restituisce prodotti non assegnati a un catalogo condiviso.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite API REST.
* **MDVA-40101** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.0*) - Corregge il problema per cui gli elementi non vengono rimossi dal mini carrello dopo il corretto inserimento dell&#39;ordine tramite l&#39;estrazione [!DNL PayPal Express].
* **MDVA-40401** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui il valore di utilizzo del coupon cambia anche se l’invio di un ordine non riesce.
* **MDVA-40537** (*per Adobe Systems Commerce e Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Risolve il problema per cui gli utenti ricevono un errore durante la creazione di una vista store se esistono più pagine CMS con la stessa chiave URL.
* **MDVA-37725** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Corregge il problema relativo all&#39;ordine asincrono delle e-mail inviate da siti Web non predefiniti contenenti gli URL del logo del sito Web predefinito.
* **MDVA-39482** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Risolve il problema relativo all’esaurimento delle scorte per un prodotto importato con quantità pari a &quot;0&quot; quando gli ordini inevasi sono abilitati.
* **MDVA-40435** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.4*) - Risolve il problema con uno sconto errato sui prodotti bundle con prezzi dinamici quando applicati tramite GraphQL.
* **MC-42528** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Corregge il problema per cui la query di GraphQL `categoryList` restituisce sia le categorie assegnate che quelle non assegnate.
* **MDVA-29400** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema relativo agli ordini duplicati effettuati con [!DNL PayPal Express Checkout].
* **MDVA-26005** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Corregge il problema relativo all&#39;impossibilità di selezionare una categoria in una struttura ad albero per le condizioni della regola Prezzo carrello.
* **MDVA-25631** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Migliora le prestazioni per la modifica e il salvataggio di segmenti di clienti che contengono un numero elevato di clienti.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui le query di ricerca di GraphQL non vengono visualizzate in termini di ricerca comuni nell&#39;amministratore.
* **MDVA-40601** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Corregge il problema che gli utenti ricevono quando tentano di ottenere informazioni sulla categoria modificata tramite l&#39;aggiornamento pianificato tramite GraphQL.
* **MDVA-37234** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Corregge il problema per cui l’aggiunta di un elemento al carrello più volte (richiesta parallela) per lo stesso SKU crea una riga duplicata per lo stesso ID carrello.
* **MDVA-33606** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Corregge il problema per cui gli utenti ricevono un errore *Violazione del vincolo univoco* durante il salvataggio di una pagina CMS assegnata a una gerarchia.
* **MDVA-31590** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corregge il problema che impedisce agli utenti di aggiornare gli attributi in blocco utilizzando le code asincrone MySQL.
* **MDVA-36309** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corregge il problema relativo alla lentezza della ricerca dei prodotti in base agli attributi nelle griglie di amministrazione.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Corregge il problema per cui la fattura con FPT mostra un totale complessivo errato quando l&#39;ordine viene pagato dal credito dell&#39;archivio.
* **MDVA-37364** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;=2.4.3*) - Corregge il problema per cui l&#39;attributo cliente personalizzato del tipo di data interrompe l&#39;interfaccia utente della griglia del cliente.
* **MDVA-39195** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Corregge il problema per cui il pulsante *Aggiungi al carrello* non era attivo nella pagina categoria quando il reindirizzamento al carrello era abilitato.
* **MDVA-37115 (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2 *) - Risolve il problema per cui nella pagina del prodotto configurabile viene visualizzato un avviso Solo 0* lasciato non necessario *.***
* **MDVA-39521** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Risolve il problema per cui il utente non è in grado di impostare gli indirizzi di spedizione sul carrello con un numero di telefono vuoto tramite GraphQL.
* **MDVA-39384** (*per Adobe Systems Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 ||=&quot;&quot;>=2.4.1 &lt;=2.4.3*) - Risolve il problema per cui l&#39;attributo cliente personalizzato per un utente aziendale non viene salvato.&lt;/=2.3.6>
* **MDVA-39043** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corregge il problema per cui l&#39;utente amministratore con accesso limitato riceve un errore durante il tentativo di aggiungere il widget *Products* alla pagina CMS.
* **MDVA-39966** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema relativo alla distribuzione di impostazioni internazionali non corrette.
* **MDVA-38852** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corregge il problema che impedisce all&#39;inventario dei cataloghi per progettazione di bloccare le tabelle per gli aggiornamenti che riducono in modo significativo le prestazioni nei casi con diversi ordini paralleli.
* **MDVA-39986** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge il problema per cui l&#39;utente non è in grado di effettuare un ordine in Admin su MacOS utilizzando il browser Safari.
* **MDVA-38447** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge due problemi: in cui i prodotti secondari configurabili *Non visibili singolarmente* vengono restituiti nella risposta di GraphQL e la query MySQL viene ottimizzata per i prodotti GraphQL con filtro categoria.
* **MDVA-40134** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Risolve il problema per cui GraphQL non restituisce i prodotti correlati quando il catalogo condiviso è abilitato.
* **MDVA-39935** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.4*) - Fixes the issue where the GraphQL returns configurable child products disabled at the website level.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema per cui l&#39;errore *Richiama a una funzione membro getId()* viene visualizzato nella pagina dei dettagli dell&#39;ordine nell&#39;amministratore.
* **MDVA-34948 (per Adobe Systems Commerce e Magento Open Source >=2.3.6 &lt;=2.3.6-p1 ||=&quot;&quot;>=2.4.0 &lt;=2.4.0-p1 *) - Risolve il problema con query con tempi lunghi, like `GET_LOCK`.&lt;/=2.3.6-p1>***
* **MDVA-39305** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Risolve il problema per cui i clienti registrati non sono in grado di accedere con Google ReCaptcha abilitato.
* **MDVA-37897** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema con un&#39;reindirizzare errata quando un cliente tenta di aggiungere prodotti con opzioni dal widget Visualizzati di recente.

## v1.1.0 {#v1-1-0}

* Sono state introdotte categorie di patch per migliorare il esperienza di utilizzo e rendere più facile per i clienti la ricerca delle patch richieste.
* Il `patches.json` file è stato rinominato in `support-patches.json`.
* **MDVA-38799** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema che impediva il salvataggio dei prodotti scaricabili dopo la creazione di un aggiornamento della gestione temporanea.
* **MDVA-37592** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Risolve il problema quando l&#39;ordinamento in base al prezzo non funziona correttamente per i prodotti con un prezzo zero assegnato al catalogo condiviso.
* **MDVA-38827** (*per Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Corregge il problema per cui i clienti ricevono un&#39;e-mail di spedizione dell&#39;ordine contenente un messaggio di errore.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*per Adobe Systems Commerce >=2.3.2*&lt;=2.3.5-p2 ) - Corregge l&#39;errore durante il salvataggio delle pagine CMS: *Elemento con lo stesso ID PAGE_ID esiste* già.
* **MDVA-34680** (*per Adobe Systems Commerce >=2.3.6 &lt;=2.3.7 ||=&quot;&quot;>=2.4.1 &lt;2.4.3*) - Risolve il problema per cui il tempo di creazione dell&#39;account cliente non viene filtrato correttamente nella griglia dei clienti.&lt;/=2.3.7>
* **MDVA-37068** (*per Adobe Systems Commerce >=2.3.1 &lt;2.4.4*) - Risolve il problema per cui l&#39;aliquota fiscale errata viene visualizzata quando il carrello contiene solo prodotti virtuali.
* **MDVA-38608** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla mancata eliminazione delle tabelle temporanee al termine della reindicizzazione.
* **MDVA-38308** (*per Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2,4,0 &lt;=2,4,1-p1 || >=2.4.2 &lt;2.4.4*) - Corregge i problemi relativi all&#39;aggiunta di [!DNL Vimeo] video ai prodotti.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema per cui il cliente non viene reindirizzato alla pagina Conferma pagamento quando si utilizza il metodo [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*): è stato risolto il problema che si verificava quando si salvava la scorta personalizzata di prodotti raggruppati causando la visualizzazione del prodotto esaurito nel front-end.
* **MDVA-36572** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*): è stato risolto il problema che si verificava quando gli aggiornamenti delle note di credito non causavano più aggiornamenti duplicati delle prenotazioni di prodotti nel database.
* **MDVA-38132** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corregge il problema quando il pannello Amministratore non è raggiungibile a causa di un errore *di troppi reindirizzamenti*.
* **MDVA-38270** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corregge il problema relativo alle informazioni mancanti sulla gift card nel totale dell&#39;ordine in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*per Adobe Commerce >=2.4.2 &lt;=2.4.4*): è stato risolto il problema relativo all&#39;aggiunta di un prodotto configurabile al carrello tramite GraphQL quando l&#39;ID del sito Web non coincide con l&#39;ID dello store.
* **MDVA-36832** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Risolve il problema della duplicazione delle immagini nelle pagine quando la larghezza di visualizzazione è 768 px.
* **MDVA-37874** (*per Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Corregge il problema per cui *L&#39;importo dello sconto fisso per l&#39;intero carrello* viene applicato in modo errato a un prodotto bundle contenente più di un&#39;opzione.
* **MDVA-37913** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Corregge il problema della scomparsa dei collegamenti scaricabili se il prodotto scaricabile viene aggiornato tramite API.
* **MDVA-34330** (*per Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Corregge il problema per cui gli ordini nella griglia Ordini non vengono filtrati in base al fuso orario dell&#39;amministratore.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*per Adobe Systems Commerce >=2.3.0*&lt;=2.3.7 ) - Risolve il problema per cui Adobe Systems Commerce genera un errore durante la creazione di una fattura parziale per gli ordini effettuati con il *metodo di pagamento Pagamento in acconto* tramite API REST.
* **MDVA-37362** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corregge il problema per cui i valori delle opzioni di prodotto configurabili e gli attributi della variante erano vuoti nella risposta di GraphQL.
* **MDVA-37288** (*per Adobe Commerce 2.4.2*) - Corregge il problema relativo alla restituzione di prezzi di livello errati dopo la richiesta GraphQL.
* **MDVA-37225** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Risolve il problema relativo al blocco del processo di caricamento durante la creazione rapida dell&#39;ordine in presenza di un valore intero negli SKU importati.
* **MDVA-37224** (*per Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corregge il problema che impedisce ai clienti di pagare un preventivo negoziabile con [!DNL PayFlow Pro] con un altro prodotto nel carrello.
* **MDVA-36286** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Risolve il problema relativo all&#39;interruzione dell&#39;anteprima del widget prodotti Page Builder se lo stesso SKU ha una posizione diversa nelle sottocategorie.
* **MDVA-30186** (*per Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corregge il problema in cui le opzioni degli attributi vengono ordinate in base al valore dell&#39;opzione invece del conteggio degli elementi degli attributi nella risposta di GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*per Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Corregge il problema se le vecchie opzioni personalizzate rimangono dopo essere state modificate tramite API.
* **MDVA-35773** (*per Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corregge il problema che impedisce la visualizzazione del totale complessivo come zero nella fattura per gli ordini con sconto del 100%.
* **MDVA-36833** (*per Adobe Commerce 2.4.2*): è stato risolto il problema che causava la visualizzazione di numeri casuali di prodotti per pagina nei risultati di ricerca dopo l&#39;esclusione di alcuni prodotti dal catalogo condiviso.
* **MDVA-37182** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Corregge il problema relativo all&#39;ottenimento di risultati di ricerca non corretti in [!DNL Elasticsearch] versione 6 e versione 7.
* **MDVA-36253** (*per Adobe Systems Commerce >=2.4.0 &lt;=2.4.1-p1*) - Risolve il problema per cui il subtotale errato viene visualizzato nel mini carrello dopo l&#39;eliminazione dell&#39;articolo.
* **MDVA-36853** (*per Adobe Systems Commerce 2.4.2*) - Risolve il problema della mancata visualizzazione di immagini durante il caricamento di gallerie di media di grandi dimensioni.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*per Adobe Systems Commerce >=2.3.4 &lt;=2.3.4-p2*) - Risolve il problema dei prodotti in bundle mancanti nelle pagine delle categorie.
* **MDVA-36615** (*per Adobe Systems Commerce 2.4.2*) - Risolve il problema relativo al conteggio errato dei prodotti nella griglia dei prodotti Admin.
* **MDVA-36464** (*per Adobe Systems Commerce >=2.4.0 &lt;=2.4.2*) - Risolve il problema per cui la configurazione della notifica e-mail non funziona a livello di store-view.
* **MDVA-36138** (*per Adobe Commerce ^2.3.2*) - Corregge il problema che causa la mancata rettifica del prezzo di spedizione e la visualizzazione del prezzo di spedizione completo ai clienti se non tutti gli articoli nel carrello sono idonei per la regola del carrello di spedizione gratuito.
* **MDVA-36424** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Corregge il problema per cui le immagini multimediali associate agli elementi Page Builder scompaiono quando il contenuto viene modificato ripetutamente, se l’URL di base del back-end è diverso dall’URL di base dello storefront.
* **MDVA-35984** (*per Adobe Commerce ^2.4.0*) - Corregge il problema relativo alla quantità di prodotto e alla quantità vendibile errate dopo la creazione di più spedizioni simultanee per lo stesso prodotto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.2*) - Questo risolve il problema per cui la query GraphQL non viene caching utilizzando la categoria cache tag.
* **MDVA-33168** (*per Adobe Systems Commerce >=2.3.3 &lt;2.4.2*) - Risolve il problema quando si aggiorna un attributo di prodotto tramite API; tutti gli altri attributi diventano un valore vuoto.
* **MDVA-19640** (*per Adobe Commerce >=2.3.0*) - Corregge il problema se [!DNL Advanced Reporting] non visualizza alcun dato.
* **MDVA-11189** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Risolve il problema quando, dopo l&#39;importazione di un file CSV per aggiornare il materiale promozionale, le righe della tabella `cataloginventory_stock` vengono eliminate.
* **MDVA-26639** (*per Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corregge il problema per cui se viene creato un nuovo modello e-mail di conferma dell&#39;ordine, gli elementi dell&#39;ordine mancano nell&#39;e-mail dell&#39;ordine.
* **MDVA-15546** (*per Adobe Commerce >=2.3.0*) - Corregge il problema per cui dopo la creazione di un ordine nel registro eccezioni viene visualizzato un errore *Column entity_id where clause is ambiguous*.
* **MDVA-21095** (*per Adobe Systems Commerce >=2.3.0*&lt;2.3.5 ) - Risolve il problema quando una query `INSERT INTO search_tmp` non termina dopo l&#39;aggiornamento di massa del valore dell&#39;attributo.
* **MDVA-23845** (*per Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Corregge il problema che impedisce la visualizzazione in anteprima dei modelli di posta elettronica dopo l&#39;abilitazione della minimizzazione di JavaScript.
* **MDVA-22026** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*): è stato risolto il problema che impediva l&#39;importazione di prodotti da un file CSV, incluse immagini da URL esterni.
* **MDVA-22383** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema relativo ai tempi lunghi di salvataggio di un prodotto e alle interruzioni di pagina.
* **MC-41359** (*per Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Corregge il problema delle impostazioni errate dei parametri dei cookie SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*per Adobe Commerce 2.4.1*) - Corregge il problema che causa il seguente errore: *Si è verificato un errore durante l&#39;avvio di Page Builder. Contattare il supporto tecnico.*
* **MDVA-35356** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla restituzione non corretta del credito dell&#39;archivio dopo l&#39;annullamento di un ordine parzialmente fatturato.
* **MDVA-33289** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corregge il problema relativo alla visualizzazione del codice JavaScript non elaborato nell&#39;interfaccia utente degli indirizzi di fatturazione durante l&#39;estrazione se [!DNL Google Tag Manager] è abilitato.
* **MDVA-35982** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui gli utenti amministratori limitati a un sito Web specifico non possono creare una spedizione per l&#39;ordine effettuato sullo stesso sito Web.
* **MDVA-35155** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema relativo all&#39;impossibilità di acquistare un prodotto bundle se il titolo dell&#39;opzione è stato modificato.
* **MDVA-35910** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*): è stato risolto il problema che impediva la creazione di un nuovo account cliente dopo la disattivazione della funzionalità Accesso come cliente.
* **MDVA-34474** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo all&#39;aggiunta di un prodotto all&#39;elenco delle richieste di acquisto tramite l&#39;API.
* **MDVA-34591** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Risolve il problema con un calcolo errato dello sconto della regola del carrello per *Sconto Qtà massimo applicato a* e *Passaggio Qtà sconto (Acquista X)*.
* **MDVA-33704** (*per Adobe Commerce >=2.4.0 &lt;2.4.3*) - Corregge il problema per cui l&#39;opzione di spedizione *In store pickup* non viene visualizzata, anche se configurata per essere disponibile.
* **MDVA-34928** (*per Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Risolve il problema della visualizzazione indefinita del caricatore di pagine dopo la rimozione del credito dello store dal pagamento.
* **MDVA-35254** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corregge i problemi con CAPTCHA durante l&#39;estrazione.
* **MDVA-35569** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema per cui il campo *imposte sui prodotti fisse* non viene popolato nella risposta di GraphQL quando viene specificato lo stato.
* **MDVA-35847** (*per Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corregge il problema B2B in cui il modulo Utenti società non funziona se viene utilizzato un attributo cliente personalizzato.
* **MDVA-31307** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corregge il problema di *memoria insufficiente* in alcune categorie a causa di problemi con l&#39;inserimento di CSP dinamici nella whitelist per i blocchi memorizzati nella cache.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge lo stato del messaggio *in corso* errato nel messaggio *completo* corretto per il consumatore `quoteItemCleaner` dopo l&#39;eliminazione di diversi prodotti.
* **MDVA-34102** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge se la quantità di scorte predefinite è zero per i prodotti disabilitati nella griglia prodotti e nelle pagine Modifica prodotto nell&#39;area Amministrazione.
* **MDVA-35286** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corregge il problema se un cliente ha raggruppato prodotti nel carrello e passa dall&#39;estrazione di più indirizzi all&#39;estrazione di Onepage.
* **MDVA-35312** (*per Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Corregge il codice di risposta 500 quando una richiesta GraphQL vuota.
* **MDVA-34189** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corregge il timeout del primo byte 503 nelle query [!DNL Visual Merchandiser] durante il caricamento della pagina Categoria amministratore.
* **MDVA-34695** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il valore negativo `children_count` dopo l&#39;eliminazione delle categorie.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*per Adobe Commerce >=2.3.1 &lt;2.4.3*) - Corregge il problema per cui la casella di controllo *Usa valore predefinito* viene deselezionata dopo l&#39;applicazione delle modifiche pianificate. Il problema viene visualizzato quando le modifiche pianificate non sono più in vigore.
* **MDVA-35064** (*per Adobe Commerce >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui non vengono generate riscritture URL per prodotti configurabili creati tramite API.
* **MDVA-34943** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema relativo all&#39;ordine rapido nella cache degli SKU immessi in precedenza.
* **MDVA-35197** (*per Adobe Commerce >=2.3.5 &lt;2.4.0*) - Risolve il problema relativo alla presenza di un errore durante l&#39;aggiunta al carrello tramite GraphQL se i prodotti aggiunti in precedenza non sono più disponibili.
* **MDVA-34850** (*per Adobe Commerce >=2.3.1 &lt;2.4.0*) - Corregge il problema per cui le opzioni esaurite di un prodotto configurabile non vengono visualizzate invece di essere visualizzate come barrate.
* **MDVA-34867** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.3*) - Risolve il problema per cui i valori di un campo di condizione impostato per un aggiornamento pianificato non vengono salvati.
* **MDVA-35092** (*per Adobe Commerce >=2.3.5 &lt;2.4.3*) - Corregge il problema che impediva agli utenti di aggiungere [!DNL Vimeo] video a causa dell&#39;API [!DNL Vimeo] obsoleta.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema relativo al tipo di contenuto Anteprima prodotti Page Builder che si interrompe se i prodotti corrispondenti hanno prezzi diversi per ciascun sito Web.
* **MDVA-32634** (*per Adobe Commerce ^2.3.1*) - Corregge il problema per cui `url_path` della categoria assegnata a tutti gli archivi rimane invariato dopo lo spostamento della categoria nella gerarchia.
* **MDVA-33344** (*per Adobe Commerce ^2.3.0*): è stato risolto il problema che causava l&#39;utilizzo dell&#39;ID del set di attributi predefiniti dell&#39;entità `rma_item` hardcoded invece del valore del database.
* **MDVA-34192** (*per Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corregge il problema che rende impossibile modificare o specificare la data di nascita del cliente nel formato gg/mm/aaaa.
* **MDVA-34847** (*per Adobe Commerce ^2.3.0*) - Corregge la conversione del tipo ID archivio in numero intero per la condizione SQL nelle raccolte amministratore per l&#39;utente amministratore con autorizzazioni personalizzate.
* **MDVA-34886** (*per Adobe Commerce ^2.3.2*) - Corregge il problema per cui la ricerca non restituisce risultati se l&#39;attributo di prodotto *weight* è configurato come ricercabile.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema del pagamento di [!DNL PayPal Payflow Pro] non riuscito con errore di formato dell&#39;elenco di parametri di reindirizzamento.
* **MDVA-34023** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui l&#39;errore *Nessuna entità con addressId* viene visualizzata in modo casuale nei browser dei visitatori.
* **MDVA-32759** (*per Adobe Commerce >=2.3.1 &lt;2.4.3 con estensione B2B*) - Corregge il problema di eliminazione dei prezzi dei livelli esistenti nei cataloghi condivisi.
* **MDVA-33482** (*per Adobe Commerce ^2.3.5*) - Corregge il problema per cui la generazione di una nota di accredito a fronte di una fattura parziale determina l&#39;applicazione di un&#39;imposta per l&#39;ordine totale anziché l&#39;imposta per la fattura parziale.
* **MDVA-33393** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge l&#39;errore *Il countryId fornito non esiste*.
* **MDVA-33632** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.7*) - Fornisce una correzione in cui il messaggio *di eccezione Questo prodotto è esaurito* viene ora visualizzato a un utente di amministrazione quando si tenta di riordinare un prodotto esaurito.
* **MDVA-34469** (*per Adobe Systems Commerce >=2.4.1 &lt;2.4.2*) - Risolve il problema per cui le mutazioni GraphQL sul carrello di un cliente non riescono quando si utilizzano più viste store.
* **MDVA-33976** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.7*) - Risolve il problema per cui il prodotto del bundle viene visualizzato Out Of Stock sul negozio dopo aver rimosso la seconda opzione dal prodotto del bundle.
* **MDVA-33894** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.1 with B2B extension*) - Risolve diversi problemi relativi alla funzionalità Quick Order, tra cui l&#39;aggiunta e la rimozione di più prodotti e la referenza di magazzino distinzione tra maiuscole e minuscole.
* **MDVA-27664** (*per Adobe Systems Commerce >=2.3.4*&lt;2.3.6 ) - Risolve il problema nel modulo registrazione cliente che causava la visualizzazione di un errore: *ERRORE - La data di nascita non deve essere successiva a quella odierna.*
* **MDVA-33970** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.2*) - Risolve il problema per cui è presente il segno di valuta errato nel promemoria di credito quando l&#39;ambito dell&#39;attributo price è impostato sul sito web.
* **MDVA-33992** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema della visualizzazione errata di B2B prezzi speciali durante il checkout.
* **MDVA-34100** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.2 with B2B extension*) - Risolve il problema per cui non è possibile creare un account aziendale dalla pagina della struttura aziendale.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*per Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Risolve il problema relativo alle immagini duplicate dopo l&#39;importazione del prodotto da un file CSV.
* **MDVA-33382** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge i problemi di invalidazione degli indicizzatori dopo la rimozione dei prodotti da una categoria.
* **MDVA-28511** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Risolve il problema che impediva il completamento dell&#39;estrazione di [!DNL PayPal] se il campo Nome contiene determinati caratteri (ad esempio lettere maiuscole accentate).
* **MDVA-31519** (*for Adobe Commerce >=2.3.5 &lt;2.3.6*) - Fixes the issue with wait timeouts in guest checkout when a site-wide sales rule is in use.
* **MDVA-33281** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) - Fixes the issue where there is a fatal error in `inventory:reservation:list-inconsistencies` because of wrong SKU parameter type.
* **MDVA-24201** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema per cui i prezzi riflettono la regola del prezzo del carrello pianificato solo dopo la reindicizzazione manuale.
* **MDVA-32694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Corregge il problema per cui un utente amministratore non può aggiungere un prodotto a un preventivo negoziabile se è correlato a un archivio non predefinito.
* **MDVA-33516** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.6*) - Risolve il problema per cui la modifica di un prodotto in bundle in un elenco di richieste porta a un errore.
* **MDVA-33975** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.2*) - Risolve diversi problemi relativi al calcolo dei prezzi nelle richieste GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*per Adobe Systems Commerce >=2.3.0*&lt;2.4.2 ) - Risolve il problema con [!DNL PayPal] i report di liquidazione che non erano disponibili in **Report** > **vendite** > **[!DNL PayPal]** liquidazione come previsto.
* **MCP-87** (*per Adobe Systems Commerce >=2.3.1 &lt;2.4.2*) - Migliorato il tempo di indicizzazione per gli indicizzatori di prodotti e azioni di categoria per profili di grandi dimensioni.
* **MDVA-33106 (per Adobe Systems Commerce >=2.3.0 &lt;2.4.2 *) - Risolve il problema per cui le modifiche di prodotto riprogrammate vengono cancellate dopo l&#39;esecuzione del comando cron`run`.***
* **MDVA-19391** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema per cui `analytics_collect_data` genera un errore a causa di record di descrizione NULL nella tabella `catalog_category_entity_text`.
* **MDVA-20376** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema con *Nessuna entità di questo tipo con customerId = 1* errore in `exception.log` per i clienti connessi dopo l&#39;inserimento dell&#39;ordine.
* **MDVA-23764** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
* **MDVA-13203** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che causa la visualizzazione dell&#39;errore *Violazione del vincolo di integrità search_tmp_ table* dopo la reindicizzazione completa.
* **MDVA-23426** (*per Adobe Systems Commerce >=2.3.3 &lt;2.3.5*) - Risolve il problema per cui notifica e-mail inviate da Adobe Systems Commerce contengono un corpo vuoto con contenuto aggiunti come allegati.
* **MDVA-22150** (*per Adobe Systems Commerce >=2.3.1 &lt;2.3.4*) - Risolve il problema per cui i clienti con un prodotto configurabile nel carrello e un coupon applicato non possono login se il prodotto configurabile è disabilitato nell&#39;amministratore.
* **MDVA-32545** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui le fatture non vengono inviate automaticamente durante la creazione di ordini dall&#39;amministratore.
* **MDVA-32714** (*per Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corregge il problema relativo al mancato funzionamento del prezzo del gruppo di clienti nella query del prodotto GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Aggiunge il *Subtotale (incl. Imposta)* opzione per le condizioni della regola di prezzo.
* **MDVA-31236** (*per Adobe Commerce >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui gli amministratori con accesso alle risorse personalizzate non sono in grado di configurare 2FA o di accedere.
* **MDVA-30845** (*per Adobe Commerce >=2.3.5 &lt;2.3.7*) - Corregge il problema per cui *Non sono disponibili preventivi per questo ordine al momento* viene visualizzato un errore se non si riesce a connettersi a UPS XML/USPS/DHL e non è disponibile alcun altro metodo di spedizione.
* **MDVA-32133** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corregge il problema relativo al mancato caricamento della raccolta multimediale da Page Builder in alcuni casi.
* **MDVA-12304** (*per Adobe Commerce >=2.3.0*) - Aumenta il numero massimo di cookie da 50 a 200.
* **MDVA-32632** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Risolve il problema relativo agli ordini visualizzati nel sistema di pagamento, ma non in Adobe Commerce.
* **MDVA-32449** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con estensione B2B*) - Corregge il problema relativo al caricamento molto lento della cronologia degli ordini o al mancato caricamento.
* **MDVA-32739** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui l&#39;attivazione delle notifiche e-mail asincrone invia le e-mail di vendita precedenti.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*per Adobe Commerce 2.3.6, 2.4.1*) - Corregge il problema per cui il pulsante *Crea account* rimane disabilitato dopo la correzione di dati non validi nel modulo *Crea nuovo account cliente*.
* **MDVA-31006** (*per Adobe Systems Commerce 2.3.0, 2.3.1*) - Risolve il problema per cui vengono visualizzati ordini duplicati dopo aver effettuato un ordine tramite [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*per Adobe Systems Commerce 2.3.0*) - Risolve il problema con il metodo di pagamento e il [!DNL PayPal Payflow Pro] trattamento dei cookie come `SameSite=Lax` per impostazione predefinita nella reindirizzare di risposta dell&#39;browser e dell&#39;API di Effetto cromatura alla pagina login del cliente.

## v1.0.10 {#v1-0-10}

Correzioni minori per le versioni delle patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363 (per Adobe Systems Commerce >=2.3.2 &lt;2.4.2 *) - Risolve il problema per cui la regola del prezzo del carrello con coupon non viene applicata tramite GraphQL quando*viene utilizzato lo sconto sull&#39;importo fisso per l&#39;azione dell&#39;intero carrello *.***
* **MDVA-30889** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema in cui si verifica un errore dopo la fatturazione di un pacchetto con prodotti virtuali e semplici come opzioni.
* **MDVA-31791** (*per Adobe Systems Commerce >=2.3.4 &lt;2.3.5*) - Migliora le prestazioni della pagina prodotto nei casi in cui vengono utilizzate regole destinazione o prodotti collegati.
* **MDVA-31168** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui il file CSV di esportazione del prodotto non viene visualizzato e si verifica un errore di allocazione della memoria.
* **MDVA-32313** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.4*) - Risolve il problema per cui i prodotti configurabili potevano essere aggiunti alla lista dei desideri con le opzioni di configurazione errate.
* **MDVA-31759** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i prodotti non vengono aggiornati con i valori degli attributi *dropdown* e *textarea* durante l&#39;importazione CSV.
* **MDVA-32012** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i codici postali in Corea e Argentina non possono essere convalidati.
* **MDVA-31640** (*per Adobe Systems Commerce >=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.1*) - Risolve il problema per cui un prezzo speciale non può essere aggiornato tramite API REST.&lt;/2.3.6>
* **MDVA-28651** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.6 ||=&quot;&quot;>2.4.0 con estensione* B2B) - Risolve il problema in cui si verificano problemi di prestazioni con il caricamento di preventivi negoziabili tramite API REST.&lt;/2.3.6>

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.1 with B2B extension*) - Risolve il problema per cui viene visualizzato un segno di valuta errato nella griglia del promemoria di credito.
* **MDVA-31295** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui i punti premio non vengono calcolati quando un ordine parziale viene completato e gli articoli vengono tassati.
* **MDVA-30112 (per Adobe Systems Commerce >=2.3.4 *&lt;2.4.2 ) - Risolve il problema per cui, se il numero di ordini supera il*valore della dimensione *del gruppo, Adobe Systems Commerce considera gli ordini con*stato in sospeso *come incoerenze.***
* **MDVA-31150** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui i saldi store di credito e di scheda regalo non vengono restituiti dalla chiamata API Rest di GET Invoice, quando la fattura è stata registrata tramite chiamata API Rest e l&#39;ordine è stato parzialmente pagato da store account di credito e scheda regalo.
* **MDVA-30963** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui i risultati del filtro dei prodotti impostati per contenere solo i valori specificati per l&#39;ambito *Tutte le visualizzazioni dello store* nell&#39;ambito Amministratore, includi i prodotti con valori sostituiti a livello di visualizzazione dello store.
* **MDVA-29954** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con estensione B2B*): è stato risolto il problema che causava l&#39;invio di *New Company Registration Request* e *You&#39;ve been linked to a company* email da un indirizzo errato.
* **MDVA-28357** (*per Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Sostituisce l&#39;analizzatore standard con un analizzatore personalizzato con un tokenizzatore di parole chiave per il campo SKU nell&#39;indice [!DNL ElasticSearch] per far funzionare le query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*per Adobe Systems Commerce >=2.3.0*&lt;2.4.2 ) - Risolve il problema per cui lo stato dell&#39;ordine personalizzato veniva modificato in *Elaborazione* dopo la creazione parziale della spedizione tramite WebApi.
* **MDVA-30428** (*per Adobe Systems Commerce >=2.3.4 &lt;2.3.5*) - Risolve il problema per cui i clienti non possono aggiungere un prodotto alla lista dei desideri se questo prodotto è assegnato a un&#39;origine di inventario personalizzata.
* **MDVA-30594** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui un ordine con più indirizzi non poteva essere salvato durante il checkout quando FPT è configurato.
* **MDVA-29148** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema durante la creazione di un prodotto tramite una chiamata API. L&#39;attributo personalizzato del prodotto di tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) non utilizza il valore predefinito se nel payload non è stato fornito alcun valore.
* **MDVA-30837** (*per Adobe Commerce >=2.3.1 &lt;2.3.5*) - Aggiunta di un&#39;impostazione di configurazione *Includi imposta nell&#39;importo: Sì/No* nella configurazione del metodo di spedizione gratuita. Quando *Includi imposta in importo* è impostato su *Sì*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale + Imposta. Quando *Includi imposta in importo* è impostato su *No*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale
* **MDVA-25028** (*per Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corregge il problema quando gli ordini effettuati utilizzando [!DNL PayPal Payflow Pro] non sono impostati sullo stato Sospetto di frode quando vengono attivati i filtri antifrode.
* **MDVA-31224** (*per Adobe Systems Commerce >=2.3.3*&lt;2.3.5 ) - Migliora le prestazioni dell&#39;operazione di reindicizzazione per i `catalog_product_price` prodotti in bundle.
* **MDVA-31321** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge una pagina vuota (errore) quando si seleziona *Mostra tutto*. [!DNL Elasticsearch] restituisce un elenco esteso di ID prodotto. In questo scenario la clausola order by viene convertita in un formato SQL non corretto.
* **MDVA-30815** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema per cui quando si modifica il numero di risultati da visualizzare nella pagina dei risultati della ricerca, Adobe Commerce visualizza una pagina vuota. [!DNL Elasticsearch] visualizza ora correttamente i risultati delle pagine delle categorie quando si modifica il numero di risultati di ricerca visualizzati per pagina.
* **MDVA-30782** (*per Adobe Commerce >=2.3.5 &lt;2.4.2*) - Corregge il problema di visualizzazione del blocco dinamico indipendentemente dalla regola del carrello.
* **MDVA-31021** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema di presenza di problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`. Se nella tabella `catalog_product_option` sono presenti più di ~100.000 record, la convalida di un nuovo file CSV con un singolo prodotto richiede meno di 10 secondi.
* **MDVA-31007** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*): è stato risolto il problema che impediva la corretta visualizzazione degli attributi degli indirizzi personalizzati nella pagina dei dettagli dell&#39;ordine nell&#39;area Il mio account e nel backend.
* **MDVA-29389** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema relativo ai report avanzati in cui il cronjob `analytics_collect_data` afferma: *La porta deve essere configurata all&#39;interno del parametro host (come localhost:3306)*.
* **MDVA-31343** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corregge il problema relativo alla classe body rimossa `page-layout-category-full-width` quando viene pianificata una categoria.
* **MDVA-30945** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui viene visualizzato un messaggio di errore irreversibile durante l&#39;aggiornamento dei carrelli `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*per Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementa la funzionalità *Minimum deve corrispondere* e la ricerca parziale per il motore [!DNL Elasticsearch]. Risolve i problemi relativi ai trattini nelle query di ricerca.
* **MDVA-30102** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corregge il problema della rapida espansione della cache Redis, poiché il TTL non è disponibile nelle cache di layout.
* **MDVA-30599** (*per Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Corregge il problema per cui le virgolette dei guest create mediante API non vengono contrassegnate correttamente come virgolette per i clienti connessi.
* **MDVA-29446** (*per Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Corregge il problema per cui il prezzo del metodo di spedizione non applicabile viene visualizzato come zero durante il pagamento.
* **MDVA-30357** (*per Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Corregge il problema relativo alla creazione di URL immagine errati durante la generazione di una sitemap da cron.
* **MDVA-30565** (*per Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Corregge il problema per cui *Nessuna entità con cartid = 0* viene visualizzata per il cliente ospite all&#39;estrazione della vetrina se il carrello acquisti persistente è abilitato.
* **MDVA-29787** (*per Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Corregge il problema per cui la regola di destinazione per i prodotti correlati non funziona quando *è una delle* condizioni utilizzate per definire i prodotti da visualizzare.
* **MDVA-30977** (*per Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Corregge il problema di mancanza di prodotti casuali dalle categorie dopo la reindicizzazione.
* **MDVA-28202** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Corregge il problema per cui la navigazione a livelli non filtra correttamente i prodotti configurabili quando viene utilizzato MSI.
* **MDVA-28300** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema per cui la richiesta GQL non riflette le modifiche di prezzo dalle regole di prezzo del catalogo.
* **MDVA-31006** (*per Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corregge il problema relativo alla visualizzazione di ordini duplicati dopo l&#39;invio di un ordine tramite il pagamento [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - È stato risolto il problema relativo alla navigazione a livelli, in cui il valore *No* per gli attributi del prodotto di tipo booleano non veniva incluso nella navigazione a livelli se [!DNL Elasticsearch] veniva utilizzato come motore di ricerca.
* **MDVA-28191** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where no payment methods are loaded during order creation via the Admin.
* **MDVA-29959** (*for Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension*) - Fixes the issue where restricted admin user with *Companies* permissions is not allowed to delete company account.
* **MDVA-30265** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where shipment tracking link stops working after Invoice creation.
* **MDVA-28409** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - È stato risolto il problema che causava l&#39;errore *memoria insufficiente* del processo cron `sales_clean_quotes` quando il numero di virgolette scadute nel database era molto elevato.
* **MDVA-30593** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema che impedisce la pulizia delle virgolette scadute in base all&#39;impostazione della durata delle virgolette.
* **MDVA-30107** (*for Adobe Commerce >=2.3.0 &lt;2.3.6*) - Fixes the issue where store switcher doesn&#39;t work as expected if different base URLs are used for store views.
* **MDVA-28763** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) - Fixes the issue where product image is getting duplicated after updating product information using REST API more than once.
* **MDVA-30284** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where Catalog Search indexer fails due to the following *[!DNL Elasticsearch]error: limit of total fields in index has been exceeded.*
* **MDVA-29042** (*for Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 with B2B extension*) - Fixes the issue where Catalog permissions were changed to *Allow* automatically after new product was added to the shared catalog.
* **MDVA-30428** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where customers cannot add a product to wishlist if this product is assigned to a custom inventory source.
* **MDVA-28661** (*per Adobe Commerce >=2.3.0 &lt;2.4.2 con estensione B2B*) - Corregge il problema relativo alla generazione di un errore nella sezione dell&#39;account società Utenti dopo la modifica dell&#39;amministratore della società.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*per Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corregge il problema che causa l&#39;errore dei processi cron se il nome del database è troppo lungo, con conseguente mancato aggiornamento delle categorie sul front-end.
* **MDVA-30106** (*per Adobe Commerce ^2.3.0*) - Corregge un problema a causa del quale durante l&#39;estrazione i pagamenti non vengono caricati con *Impossibile leggere la proprietà &#39;length&#39; di null* errore nella console JS.
* **MDVA-28656** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui se un ordine è stato effettuato senza che fossero richieste informazioni sul pagamento (ad esempio, con uno sconto del 100%) ed è stata creata una fattura per l&#39;ordine, lo stato dell&#39;ordine cambia in *Chiuso* invece di Completo.
* **MDVA-30209** (*per Adobe Commerce 2.3.0 - 2.3.3-p1*) - Corregge il problema relativo al passaggio del gruppo di clienti al gruppo predefinito se il cliente ha aggiornato le informazioni sul proprio account.
* **MDVA-30123** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema di traduzione errata delle etichette di opzione degli attributi per le query GraphQL.
* **MDVA-29996** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui dopo l&#39;abilitazione dell&#39;autorizzazione per la categoria, la pagina della categoria non viene memorizzata nella cache dalla cache a pagina intera.
* **MDVA-30164** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corregge il problema per cui i record dei clienti non possono essere esportati dalla griglia Clienti se sono presenti attributi cliente personalizzati.
* **MDVA-30444** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema per cui non viene inviata alcuna e-mail di conferma per gli ordini effettuati tramite GraphQL.
* **MDVA-30490** (*per Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corregge il problema per cui il confronto dei prodotti genera la pagina di errore 500 se uno dei prodotti presenta una descrizione breve vuota.
* **MDVA-30232** (*per Adobe Commerce >=2.3.1 &lt;2.4.1*) - Risolve il problema che impediva il riordino se l&#39;ordine originale conteneva una gift card.
* **MDVA-29965** (*per Adobe Commerce >=2.3.3 &lt;2.4.0*) - Corregge il problema relativo all&#39;errore di chiave del modulo non valida durante l&#39;aggiunta di un prodotto al carrello.
* **MDVA-30008** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema B2B che impedisce di effettuare ordini tramite Admin API per un prodotto presente in un catalogo pubblico.
* **MDVA-22469** (*per Adobe Systems Commerce 2.3.2-p2 - 2.3.3-p1*) - Risolve il problema per cui, dopo l&#39;aggiornamento a Adobe Systems Commerce 2.3.3, Pagina Builder non funziona nel pannello di amministrazione e alcuni file JS e CSS non vengono caricati.
* **MC-35984** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema per cui i commercianti non potevano interagire con gli elementi della pagina Resi dopo aver creato un&#39;etichetta di spedizione per un&#39;autorizzazione al reso della merce (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*per Adobe Systems Commerce 2.3.0 - 2.3.4*) - Risolve il problema con il metodo di pagamento e il [!DNL PayPal Payflow Pro] trattamento dei cookie come `SameSite=Lax` per impostazione predefinita nel browser Effetto cromatura 80 e nella risposta API reindirizzare alla pagina login del cliente.
* **MDVA-26694** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Risolve il problema relativo alla scadenza giornaliera delle cache di prodotti e cataloghi, anche se la cui scadenza è diversa.
* **MDVA-27825** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.1*) - Risolve il problema per cui l&#39;esportazione di grandi quantità di dati non riusciva a causa di una perdita di memoria.
* **MDVA-29085** (*per Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corregge il problema B2B che non richiede l&#39;invio di e-mail nuove società se queste vengono create tramite API.
* **MDVA-29344** (*per Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corregge il problema di blocco di Page Builder dopo la copia di testo da un elemento intestazione a un elemento testo.
* **MDVA-29835** (*per Adobe Commerce >2.3.1 &lt;2.4.2*) - Corregge il problema per cui gli ordini di gift card contenevano due codici invece di uno.
* **MDVA-30052** (*per Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): è stato risolto il problema che impediva il corretto popolamento del contenuto privato (archiviazione locale), causando problemi di prestazioni.
* **MDVA-30131** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - È stato risolto il problema relativo alla navigazione a livelli, in cui il valore *No* per gli attributi del prodotto di tipo booleano non veniva incluso nella navigazione a livelli se [!DNL Elasticsearch] veniva utilizzato come motore di ricerca.
* **MDVA-35514** (*per Adobe Commerce >=2.4.0 &lt;2.4.1*) - Corregge il problema relativo alla creazione di un&#39;etichetta di spedizione e all&#39;aggiunta di prodotti ordinati a un pacchetto nella finestra modale Crea pacchetti.

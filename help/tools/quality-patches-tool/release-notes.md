---
title: Note sulla versione
description: Scopri le patch disponibili per Adobe Commerce e i problemi che risolvono.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: d870d98caf2b2576f3bf179e860e711d1cea9afc
workflow-type: tm+mt
source-wordcount: '21346'
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

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge l&#39;errore *Chiamata al metodo non definito ReflectionUnionType::getName()* che si verifica durante l&#39;installazione delle versioni 2.4.4-pX.
* **ACSD-45049** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Corregge il problema per cui l&#39;impostazione di un attributo del cliente *[!UICONTROL Is required]* non funziona correttamente in base all&#39;ambito del sito Web in Amministrazione.
* **ACSD-46938** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema relativo alle prestazioni dei trigger del database per la ricreazione durante `setup:upgrade`.
* **ACSD-48210** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7): è stato risolto il problema che si verificava se l&#39;aggiornamento di un attributo *[!UICONTROL Website Scope]* in una visualizzazione archivio specifica ignorava i valori dell&#39;attributo nell&#39;ambito globale.
* **ACSD-54887** (per Adobe Commerce e Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2,4,5-p3 &lt;2,4,5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Corregge il problema per cui il carrello acquisti del cliente viene cancellato dopo la scadenza della sessione del cliente con [!UICONTROL Persistent Shopping Cart] abilitato.
* **ACSD-58141** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Corregge il problema di rigenerazione di PHPSESSID nelle richieste POST nell&#39;area di vetrina per un cliente connesso se [!DNL L2 Redis cache] è abilitato e il cliente è aggiornato da Amministratore.
* **ACSD-58352** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Corregge il problema in cui le etichette degli attributi restituiti per la visualizzazione archivio predefinita vengono restituite tramite API GraphQL quando nell&#39;intestazione della richiesta è specificata una visualizzazione archivio non predefinita.
* **ACSD-58442** (per Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Risolve il problema che causava il caricamento del menu e dell&#39;intestazione in una visualizzazione mobile anziché desktop.
* **ACSD-58790** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.8) - Fixes pinch-to-zoom functionality on the product detail page images in mobile view on [!DNL Chrome].
* **ACSD-59036** (per Adobe Commerce e Magento Open Source >=2.4.7 &lt;2.4.8) - Corregge un&#39;eccezione che si verifica quando si caricano i prezzi dei prodotti con limiti inferiore e superiore uguali a $0.
* **ACSD-59229** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui le informazioni relative al gruppo del cliente vengono salvate nel segmento errato a causa del vecchio valore di X-Magento-Vary nella richiesta.
* **ACSD-59378** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where store-level URL rewrites are incorrectly updated during import.
* **ACSD-59514** (for Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Fixes the issue where forms in the Admin area with [!DNL Page Builder] throw the error *[!DNL Page Builder]was rendering for 5 seconds without releasing locks.* nella console del browser dopo l&#39;invio del modulo e le modifiche non possono essere salvate.
* **ACSD-60303** (per Adobe Systems Commerce >=2.4.4-p9 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p8 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p6 &lt;2.4.8) - Fixes the issue where an order from Admin cannot be placed if HTML minification is enabled.&lt;/2.4.6>&lt;/2.4.5>
* **ACSD-60441** (per Adobe Systems Commerce e Magento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Risolve il problema con l&#39;aggiornamento dei clienti tramite `V1/customers` [!DNL REST API] endpoint quando si utilizza il token di integrazione accesso generato dal backend.
* Patch aggiornate: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where product images are removed after deleting a staging update.
* **ACSD-57086** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the orders placed from non-default websites with terms and conditions enabled are not processed correctly.
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

* **ACSD-55566** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the `mergeCart` mutation fails with an &quot;*Internal Server Error*&quot; in the [!DNL GraphQL] response when merging source and destination carts that have the same bundle items.
* **ACSD-56546** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where configurable and bundle products display as **Out of Stock** on the storefront when the **display out of product configuration** is *Disabled*.
* **ACSD-56635** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where the imported customer is duplicated with the same email address, when an import is used with **account sharing** set to *Global*.
* **ACSD-56741** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the error message &quot;*Trying to access array offset on value of type null*&quot; that displays during `setup:upgrade` when the database contains a custom [!DNL MySQL] trigger not related to the indexation mechanism and [!DNL MView].
* **ACSD-57315** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante [!UICONTROL Fetch] nella schermata **[!UICONTROL View transaction]** dell&#39;amministratore.
* **ACSD-57337** (for Adobe Commerce >=2.4.4 &lt;2.4.6) - Fixes the issue where an admin user with access restrictions to specific websites is able to see companies from all the websites in the **[!UICONTROL Companies]** grid.
* **ACSD-57394** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue of incorrect product sorting by multiple sort fields in [!DNL GraphQL].
* **ACSD-57565** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7): è stato risolto il problema che causava la visualizzazione di informazioni di ordine errate nel dashboard **[!UICONTROL Order]** fino all&#39;aggiornamento del periodo di tempo. Il dashboard ora visualizza le statistiche dell&#39;ordine corrette al primo carico.
* **ACSD-57854** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7): è stato risolto il problema che si verificava se le richieste del prodotto [!DNL GraphQL] restituivano categorie disabilitate nelle aggregazioni di categorie.
* **ACSD-58008** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui l&#39;aggiornamento di un aggiornamento pianificato ha rimosso la versione precedente di un elemento nell&#39;area di gestione temporanea, se non è stata specificata una data di fine.
* Patch aggiornate: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where *[!UICONTROL Used]* e *[!UICONTROL Times Used]* gli attributi visualizzano valori errati per i coupon generati quando vengono utilizzati durante il checkout con più indirizzi.
* **ACSD-56760** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where an admin user restricted to a specific website cannot sort or add new products inside a category in case the webstore has its own root category.
* **ACSD-56858** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where B2B company role permissions are displayed incorrectly for a restricted company admin.
* **ACSD-57074** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui l&#39;attributo personalizzato *Yes/No* con `attrbute_code` che inizia con `price_` non funziona correttamente con l&#39;indicizzazione e i prodotti con tali attributi non sono disponibili nel front-end.
* Updated patches: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the category page caches invalidate when the stock quantity changes, even if the product is still in stock.
* **ACSD-54656** (for Adobe Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the invisible Recaptcha fails during checkout, preventing an order from being placed.
* **ACSD-55100** (per Adobe Commerce >=2.4.6 &lt;2.4.7) - Corregge il problema per cui GraphQL non restituisce più di 10.000 prodotti nei risultati di ricerca.
* **ACSD-56621** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il nome e il cognome aggiornati non vengono riportati nella sezione dell&#39;intestazione dei saluti per l&#39;utente amministratore della società.
* **ACSD-56842** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema di mancanza dei proxy differiti e delle directory proxy differite dopo l&#39;esecuzione di `setup:di:compile`.
* **ACSD-57003** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui lo stato dell&#39;ordine viene modificato in *[!UICONTROL Complete]* invece di essere modificato in *[!UICONTROL Processing]* quando un ordine viene parzialmente rimborsato e parzialmente spedito.
* Patch aggiornate: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where a configurable product becomes out of stock when one of two child products is disabled by a scheduled update.
* **ACSD-56616** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Risolve il problema della visualizzazione dei prodotti in bundle come in stock sullo storefront quando i loro prodotti semplici sono esauriti.
* **ACSD-56515** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema per cui l&#39;amministratore con autorizzazioni a livello di sito Web non può aggiungere o modificare un blocco dinamico.
* **ACSD-56447** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui l’aggiunta dello stesso prodotto al carrello tramite richieste API web REST parallele genera due elementi separati nel carrello.
* **ACSD-56415** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the performance of the partial price indexing is slowed down due to a `DELETE` query when the database has a lot of partial price data to index.
* **ACSD-54965** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the Visual Merchandising grid does not display the correct stock when a product is assigned to custom stock only.
* **ACSD-52824** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where PayPal Express, Google Pay, and Apple Pay buttons are displayed for company customers when such payment methods are disabled in company settings.
* Patch aggiornate: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a user is redirected to the Admin Dashboard when sorting category products using the **Spostati dall&#39;opzione Stock a quella inferiore** e l&#39;errore `Invalid security or form key. Please refresh the page` appare nella parte superiore dello schermo.
* **ACSD-56280** (per Adobe Systems Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where ordering items from a gift registry leads to an exception.
* **ACSD-56246** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where data is removed from the custom multi-select attribute when a scheduled update for a product becomes active.
* **ACSD-56193** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Fixes the issue where the Varnish/Fastly cache is not updated when a scheduled block is used in the category description using Page Builder.
* **ACSD-56158** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the &quot;cart&quot; query returns the total tax value for each tax rule.
* **ACSD-56023** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where widget content is not updating on the CMS page when cache is enabled.
* **ACSD-55427** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the admin user cannot unassign a product from a shared catalog from the product page in the Admin.
* **ACSD-55352** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui dopo la creazione di una nota di credito parziale con punti premio cliente, lo stato dell&#39;ordine cambia in Chiuso e le opzioni della nota di credito scompaiono dalla pagina Ordine amministratore.
* **ACSD-55231** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Risolve il problema che impediva l&#39;aggiunta di prodotti al carrello con la funzionalità ordine rapido.
* **ACSD-54283** (per Adobe Commerce >=2.4.3 &lt;2.4.4) - Corregge il problema per cui Prodotti/Categorie non assegnati al Catalogo condiviso per il Valore predefinito (Gruppo generale) sono ancora inclusi in Sitemap XML.
* Patch aggiornate: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the canonical category URL doesn&#39;t update after changing the category URL.
* **ACSD-53636** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5) - Risolve il problema che non consentiva la visualizzazione del prezzo normale nelle pagine dell&#39;elenco dei prodotti configurabili con prodotti secondari a prezzi speciali.
* **ACSD-54885** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema dell&#39;estrazione di più indirizzi quando l&#39;utente amministratore utilizza la funzionalità *Accedi come cliente*.
* **ACSD-55610** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui un ordine parzialmente annullato presenta un importo di sconto errato.
* **ACSD-55334** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge le traduzioni per le etichette tramite i dizionari di traduzione nella risposta di GraphQL.
* **ACSD-54739** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui la condizione dello stato delle scorte di prodotto non viene applicata per le regole del prodotto correlate.
* **ACSD-53925** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui l&#39;amministratore non è in grado di salvare il blocco CMS con il carosello prodotti quando la modalità dimensioni `catalog_product_price` è impostata su *sito Web*.
* **ACSD-52714** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo al mancato funzionamento del filtro data nella griglia di amministrazione quando il formato data è impostato su *Y-m-d*.
* **ACSD-55055** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Improves performance of loading product attributes in cart price rules in the shopping cart.
* **ACSD-53790** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where Multiple RMAs for a single product can be created via REST API.
* **ACSD-56090** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.5) - Fixes the issue where the GraphQL request is responding with all stores&#39; data rather than the specifically requested store data.
* **ACSD-54983** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where getting the company user UID with GraphQL request is not possible when the user status is set to *[!UICONTROL Inactive]*.
* **ACSD-53309** (per Adobe Systems Commerce ed etichetta Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where tax is not fully applied in the *[!UICONTROL Regular Price]* quando è selezionata l&#39;opzione personalizzabile.
* **ACSD-55305** (per Adobe Systems Commerce >=2.4.4 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Edit Company User]* popup sulla **[!UICONTROL myAccount]** pagina > **[!UICONTROL Company Structure]** si blocca con un caricatore sullo schermo.
* Patch aggiornate: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui i dati di prodotto *[!UICONTROL Recently Viewed]* non vengono aggiornati correttamente nella visualizzazione archivio.
* **ACSD-54626** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where you can&#39;t create a new purchase order rule (`createPurchaseOrderApprovalRule`) con l&#39;attributo `NUMBER_OF_SKUS` tramite [!DNL GraphQL].
* **ACSD-53845** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the [!DNL MySQL] problema di timeout della connessione quando `consumer max_messages` = 0.
* **ACSD-54890** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where `aggregate_sales_report_bestsellers_data` causa [!DNL MySQL] errori a causa dell&#39;esaurimento `/tmp` dello spazio su disco.
* **ACSD-55112** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui è possibile fare clic più volte sul pulsante *[!UICONTROL Submit review]* senza la convalida [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (per Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corregge il problema per il quale viene visualizzato il messaggio di errore *&quot;Impossibile aggiornare l&#39;attributo richiesto. L&#39;ID riga: store_id&quot;* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione archivio.
* **ACSD-54418** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where a fixed amount of discount is incorrectly applied to each child product of the dynamically priced bundle.
* **ACSD-55238** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes saving the empty product *[!UICONTROL Meta Description]*.
* **ACSD-54966** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a coupon code with a limited-use per customer can&#39;t be reused if the previous order failed.
* **ACSD-54060** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a restricted admin can&#39;t save a product if it&#39;s a child of another product assigned to a different scope.
* **ACSD-48910** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixed the issue where a bundle product assigned to multiple sources goes out-of-stock after an order is invoiced and shipped, even if it still has a non-zero quantity.
* **ACSD-55381** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes an internal server error when querying `configurable_product_option_uid` e `configurable_product_option_value_uid` campi da a [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (per Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6) - Corregge il caricamento di un file nel modulo di registrazione della società e la sostituzione di un file per un attributo del cliente nella vetrina.
* Patch aggiornate: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema che si verifica nel carrello quando un prodotto viene rimosso dal catalogo condiviso dopo essere già stato aggiunto al carrello.
* **ACSD-53722** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Corregge il problema per cui il prezzo delle opzioni di prodotto in bundle cambia a $0 quando diventano attivi aggiornamenti pianificati per ambiti diversi.
* **ACSD-53643** (per Adobe Commerce >=2.4.3 &lt;2.4.7) - Risolve il problema relativo a un totale errato dell&#39;ordine quando si effettua un ordine di acquisto con prodotti disabilitati o esauriti. Per risolvere il problema, nasconde il pulsante *[!UICONTROL Place Order]* per tali ordini fornitore.
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
* **ACSD-55004** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the validator crashes while uploading an import file larger than the value configured in `php.ini`.
* **ACSD-54989** (per Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2,4,5-p4 &lt;2,4,6 || >=2.4.6-p2 &lt;2.4.7) - Corregge il problema per cui un amministratore società non può effettuare un ordine quando *[!UICONTROL Enable Purchase Orders]* è impostato su *[!UICONTROL Yes]* e *[!UICONTROL Purchase Order]* è impostato su *[!UICONTROL No]*.
* **ACSD-54007** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *&quot;Undefined array key &quot;_scope&quot;&quot;* on importing customer data.
* **ACSD-55031** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the *Type &quot;mixed&quot; cannot be nullable* error during compilation.
* **ACSD-54961** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui un utente amministratore con restrizioni non può aggiornare in massa lo stato *Product Review*.
* **ACSD-55256** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where only the first image is successfully displayed in the image slider.
* Patch aggiornate: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (per Adobe Commerce >=2.4.0 &lt;2.4.7) - Corregge il problema per cui la cronologia del saldo dei punti premio viene calcolata in modo errato dopo la scadenza dei punti premio.
* **ACSD-53583** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Migliora le prestazioni di reindicizzazione parziale per gli indicizzatori *Categoria prodotti* e *Categorie prodotti*.
* **ACSD-54026** (for Adobe Commerce >=2.4.6 &lt;2.4.7) - Fixes an incorrect error message for an `updateCompanyRole` GraphQL request for a non-authorized user.
* **ACSD-54106** (for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.5) - Fixes the issue where category product sorting by name for Turkish accented characters is incorrect.
* **ACSD-52219** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema relativo al funzionamento imprevisto dei filtri salvati dalle griglie di amministrazione quando si passa di frequente da una visualizzazione all&#39;altra.
* **ACSD-54342** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge un messaggio di errore errato *Errore nella struttura dati: valori misti* durante l&#39;importazione di un file CSV senza dati validi.
* **ACSD-54660** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Aggiunto un nuovo attributo di input *sort* per ordinare gli ordini dei clienti in GraphQL in base a `sort_field` e `sort_direction`.
* **ACSD-54776** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui i valori non selezionati *[!UICONTROL Use Default Value]* e non predefiniti dei campi prodotto non vengono salvati per la seconda visualizzazione sito Web, archivio e archivio.
* **ACSD-53998** (per Adobe Commerce e Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Corregge il problema per cui **[!UICONTROL Dynamic Block]** basato su **[!UICONTROL Customer Segment]** non funziona correttamente dopo la disconnessione da un account cliente.
* **ACSD-53204** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Correzioni *Impossibile salvare il prodotto.Errore* durante l&#39;esecuzione di richieste simultanee per l&#39;aggiunta di immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`.
* **ACSD-47657** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiunto un meccanismo di caching per le credenziali di AWS. Un provider di credenziali ora utilizza la cache del Magento per memorizzare nella cache le credenziali recuperate da AWS per la configurazione EC2.
* Aggiornate patch: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4) - Fixes the issue where products assigned to a shared catalog do not appear on the storefront when a partial index is executed.
* **ACSD-54018** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the performance issues with the [!UICONTROL Product List] widget that uses a non-global attribute in the widget condition.
* **ACSD-54111** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product thumbnail images are not displayed on the storefront when the aspect ratio of the watermark image does not match the product image.
* **ACSD-47669** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes *Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails* error when importing products CSV.
* **ACSD-53347** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo all&#39;esecuzione dell&#39;indicizzatore prezzi.
* **ACSD-52287** (for Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue with incorrect order status in the archived order grid when asynchronous grid indexing is enabled.
* **ACSD-52929** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue with redundant requests to reindex default source items when the inventory indexer is configured in async mode.
* **ACSD-53824** (per la patch dei dati di migrazione di Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where `UpdateMultiselectAttributesBackendTypes` supera il limite di dimensione delle transazioni del database durante `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema relativo all&#39;aggiornamento delle cache e degli indici anche quando l&#39;API REST non aggiorna `Inventory_source` elementi.
* **ACSD-51884** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che causava la correzione del percorso della cache delle immagini del prodotto dopo l&#39;esecuzione del comando di ridimensionamento.
* **ACSD-53628** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione di caratteri speciali non corretti nel rapporto CSV degli ordini di vendita.
* **ACSD-53148** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Corregge il problema per cui due richieste parallele in GraphQL per l&#39;aggiunta dello stesso prodotto configurabile al carrello hanno prodotto due elementi separati sul carrello con lo stesso SKU prodotto.
* **ACSD-52606** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo al messaggio di errore *Quando l&#39;utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**, l&#39;ordine non è pronto per il ritiro*.
* **ACSD-51574** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Risolve il problema se l&#39;immagine non viene aggiornata sul front-end dopo averla sostituita con un&#39;altra immagine con lo stesso nome.
* **ACSD-53728** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the product EAV indexer is taking longer to complete.
* **ACSD-53979** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema JS che si verifica nella home page se il messaggio di benvenuto contiene una virgoletta singola.
* **ACSD-52085** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where a configurable product with a special price is not visible in the product&#39;s carousel.
* **ACSD-53795** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue with invalid data type in `indexer_update_all_views` cron job.
* **ACSD-52143** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where custom options are removed after product import.
* **ACSD-53750** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the *Broken pipe or closed connection* error during multi-threaded `catalog_product_price` reindex.
* **ACSD-49843** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Fixes the issue where the link on product download is not available after the ordered item is auto-invoiced by online payment method with the **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** setting enabled.
* **ACSD-47054** (per Adobe Commerce >=2.4.2 &lt;2.4.6) - Corregge il problema di reindicizzazione della reindicizzazione dell&#39;anteprima per tutti gli archivi, causando lentezza.
* Sono state aggiunte nuove versioni per ACSD-46541 e ACSD-47079.
* ACSD-49970-v3 sostituito da ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt; 2.4.6): è stato risolto il problema che determinava la pulizia di tutte le cache da parte dell&#39;indicizzatore di inventario nella modalità Aggiorna secondo pianificazione.
* **ACSD-50887** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 *[!UICONTROL Use in Search Results Layered Navigation]* &lt;2.4.7) - Fixes the issue where the product attribute property può essere impostato su *Sì* senza l&#39;opzione *[!UICONTROL Use in search]* impostata su *Sì*.
* **ACSD-51846** (per Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Corregge il problema *Errore interno* che si verifica perché non tutti i livelli del payload dell&#39;API REST sono convalidati.
* **ACSD-52906** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui il cookie X-Magento-Vary non è impostato correttamente per i clienti connessi che appartengono allo stesso segmento di clienti, causando la memorizzazione nella cache non corretta di alcune pagine.
* **ACSD-52736** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema per cui una *Regola prezzo carrello* che include i requisiti per la quantità di prodotto configurabile non funziona come previsto.
* **ACSD-47875** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): è stato risolto il problema che impediva agli utenti amministratori di aggiungere un prodotto al carrello di un cliente dall&#39;amministratore per un determinato ambito di visualizzazione archivio con gestione inventario.
* **ACSD-53176** (for Adobe Commerce >=2.3.7 &lt;2.4.5) - Fixes the issue where *Related Product Rule* with *is one of* condition does not match products.
* **ACSD-51666** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the error *The session has expired, please login again.* Ciò avviene dopo che un cliente tenta di accedere.
* Added new versions for MDVA-39305-v2.
* Updated requirements for ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the default shipping address on the checkout shipping step is auto-populated with a previously selected in-store pickup address.
* **ACSD-52041** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the error message: *[ERROR] [!DNL Page Builder] was rendering for 5 seconds without releasing locks.* appears in Chrome browser when saving content edited with [!DNL Page Builder].
* **ACSD-52095** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema per cui il valore `manage_stock` veniva erroneamente impostato su 0 nel file CSV dopo l&#39;esportazione del prodotto.
* **ACSD-51358** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema se la rimozione di un aggiornamento pianificato senza data di fine comporta la rimozione di altri aggiornamenti pianificati per la stessa entità.
* **ACSD-48070** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui la modifica di un aggiornamento pianificato genera un&#39;eccezione.
* **ACSD-51890** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Submit review] button can be clicked multiple times without [!DNL Google reCAPTCHA] v3 validation.
* **ACSD-51984** (for Adobe Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where unchecked *[!UICONTROL Use Default Value]* and *[!UICONTROL non-default product field]* values are not saved for the second website, store, and store view.
* **ACSD-52398** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge l&#39;errore *La quantità richiesta non è disponibile* che si verifica quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
* **ACSD-52786** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui una condizione *SKU del catalogo è* si applica a tutti i prodotti che iniziano con lo SKU specificato.
* **ACSD-52921** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Risolve il problema relativo a un errore interno che si verificava se si richiedevano i dettagli del carrello a GraphQL quando nel carrello era presente un prodotto configurabile esaurito.
* **ACSD-51683** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge il problema per cui non è possibile aggiungere al carrello un&#39;opzione personalizzabile tramite GraphQL.
* **ACSD-52133** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a customer account cannot be saved after an upgrade.
* **ACSD-52202** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the salable qty of default stock wrongly changes to 0 when a non-default stock is changed to 0 qty on order fulfillment.
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

* **ACSD-52277** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo a un utente amministratore che non viene reindirizzato correttamente dopo aver selezionato una visualizzazione archivio durante la creazione di un nuovo ordine in Admin.
* **ACSD-50813** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - È stato risolto il problema che impediva all&#39;amministratore di aggiungere all&#39;ordine di amministrazione prodotti in bundle contenenti una barra nello SKU con la funzionalità [!UICONTROL Add Products by SKU].
* **ACSD-51630** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema che rallenta il download delle pagine di amministrazione a causa di una grande quantità di messaggi di sistema.
* **ACSD-51853** (per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.7) - Corregge il problema per cui gli stili di testo copiati non vengono applicati quando si utilizza [!UICONTROL Page Builder].
* **ACSD-52160** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue where the product validation result against the cart price rule was not properly evaluated based on the rule condition &#39;If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true&#39;.
* **ACSD-51636** (per Adobe Systems Commerce >=2.4.5 &lt;2.4.7) - Fixes the issue where the company admin cannot add new users from the customer account section despite having all necessary roles and permissions.
* **ACSD-51739** (per Adobe Systems Commerce >=2.4.6 &lt;2.4.7) - Fixes the issue where an error is returned when the `structure_id` è richiesto in un richiesta GraphQL di CompanyTeam.
* **ACSD-51857** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema relativo alle prestazioni lente del report cron `aggregate_sales_report_bestsellers_data` sulle tabelle sales_order e `sales_order_item` di database di grandi dimensioni dovute al modo in cui è stata scritta la query di dati principale.
* **ACSD-48448** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo a una situazione di tipo &quot;race condition&quot; che si verifica durante l&#39;annullamento dell&#39;ordine e causa la duplicazione di una voce nella tabella `inventory_reservation`.
* **ACSD-52689** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.6) - Fixes the issue where images cannot be uploaded to Amazon S3 storage using REST API.
* **B2B-2674** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Add caching capability to the 1customAttributeMetadata1 GraphQL query.
* Nuove versioni aggiunte per ACSD-44938.
* Nuovi requisiti per ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (per Adobe Systems Commerce e comando SQL delimitatore *Magento Open Source >=2.4.0&lt;2.4.5) - Fixes the database rollback command for a case when the DB dump contains triggers and a*.
* **ACSD-50512** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge *Errore: il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova.* errore che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto.
* **ACSD-50949** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il filtro del prezzo in Ricerca avanzata non restituisce risultati corretti se utilizzato con il filtro SKU.
* **ACSD-51645** (per Adobe Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Corregge l&#39;errore generato durante il salvataggio di una nuova regola prezzo carrello se l&#39;estensione `Magento_OfflineShipping` è disabilitata.
* **ACSD-50895** (per Adobe Commerce >=2.4.5 &lt;2.4.7) - Corregge il problema per cui [!DNL Google Analytics] 3 tag GTM non vengono attivati se [!DNL Google Analytics] 4 GTM non è configurato.
* **ACSD-51102** (per Adobe Commerce >=2.4.2 &lt;2.4.7) - Corregge il problema per cui una regola di catalogo applicata a un numero elevato di prodotti non viene indicizzata correttamente quando la regola è abilitata da un aggiornamento pianificato.
* **ACSD-50368** (per Adobe Commerce e Magento Open Source >= 2.4.3 &lt;2.4.5) - Corregge il problema per cui `group_id` del cliente viene ignorato quando viene creato un cliente tramite API REST asincrona o API REST in blocco asincrono.
* **ACSD-51497** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7): è stato risolto un problema che impediva al cliente di ordinare una pagina di catalogo per attributo personalizzato del tipo a discesa.
* **ACSD-51408** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt; 2.4.7) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Backordered]*.
* **ACSD-51735** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge il problema per cui lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando lo stock del prodotto è *0*.
* **ACSD-51792** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui una pagina non ha l&#39;evento di impression quando [!DNL Google Tag Manager] 4 è abilitato.
* **ACSD-51471** (per Adobe Commerce >=2.4.3 &lt;2.4.7) - Corregge il problema per cui un utente amministratore non può salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
* **ACSD-51700** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge l&#39;errore che si verifica quando si passa da una visualizzazione archivio a un&#39;altra pagina di modifica prodotto scaricabile nell&#39;amministratore.
* **ACSD-51120** (per Adobe Commerce >=2.3.7 &lt;2.4.3) - Corregge il problema per cui la cache delle richieste GraphQL GET non viene cancellata per le pagine CMS che contengono blocchi CMS aggiornati tramite un aggiornamento di staging.
* **ACSD-51240** (per Adobe Systems Commerce >=2.4.4 &lt;2.4.6) - Fixes the issue where the uploaded file is missing if the registration is done via the company registration form.
* **ACSD-51907** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.3) - Fixes the issue where a restricted admin user cannot create a credit memo with an offline refund.
* **ACSD-52148** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where the [!DNL Google V3 reCAPTCHA] Admin login si verifica occasionalmente.
* **ACSD-51431** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 lineare &lt;2.4.7) - Fixes the issue where an indexer status is *di lavoro* se non ci sono nuove voci nel changelog.
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
* **ACSD-51294** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GTM/GA price, quantity, tax, shipping, and revenue are sent as a string to [!DNL Google Analytics] and GTM.
* **ACSD-51204** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Risolve il problema che impediva la restituzione di un prodotto completamente venduto in magazzino dopo la creazione di una nota di credito.
* **ACSD-51291** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Corregge il problema per cui un amministratore con accesso limitato a un sito web può aggiungere immagini/video al prodotto assegnato a più siti web.
* Sono state aggiunte nuove versioni di ACSD-50336.
* Sostituzione delle patch ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Corregge il problema per cui Recaptcha v2 non si ricarica dopo l’invio di un pagamento non riuscito.
* **ACSD-50817** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7): ottimizza il processo Cron `sales_clean_quotes` per un&#39;esecuzione più rapida.
* **ACSD-49392** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Corregge il problema se lo stato dell&#39;ordine cambia in chiuso dopo un rimborso parziale per un prodotto nel pacchetto.
* **ACSD-51036** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Corregge il problema per cui le race condition durante le chiamate API REST simultanee determinano la sovrascrittura delle informazioni sullo stato della spedizione nella tabella [!UICONTROL Items Ordered].
* **ACSD-50858** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Migliora le prestazioni per il caricamento dei contenuti dei banner.
* Sono state aggiunte nuove versioni per MDVA-39305-v2, ACSD-45169.
* Updated patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (for Adobe Commerce and Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Fixes the issue where product alert emails are not sent when a product is back in stock or the price is changed.
* **ACSD-50367** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;esportazione dell&#39;indirizzo del cliente non funziona quando viene creato un attributo dell&#39;indirizzo del cliente a selezione multipla senza valori.
* **ACSD-49877** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui la riproduzione automatica video non funziona sul dispositivo mobile [!DNL Safari] quando il video è collegato direttamente a un file video remoto e non a un servizio di streaming.
* **ACSD-50165** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *The file can&#39;t be deleted. Warning!unlink: No such file or directory* when flushing JS/CSS cache from the Admin.
* **ACSD-49737** (for Adobe Commerce and Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Fixes the issue where a coupon is incorrectly marked as used after a failed card payment.
* **ACSD-50814** (per Adobe Systems Commerce e Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where an admin user is not able to create a credit memo.
* **ACSD-50116** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui un utente amministratore non può creare una riscrittura URL per sottocategorie di livello 3 o inferiore.
* **ACSD-49513** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5): è stato risolto il problema che impediva la sincronizzazione dell&#39;archiviazione remota a causa di file da 0 byte.
* **ACSD-46683** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema relativo al prezzo di spedizione, che indica *Non ancora calcolato*.
* **ACSD-49129** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Corregge il problema per cui l&#39;attributo *[!UICONTROL content]* (codice immagine base64) non viene restituito nelle risposte API dei supporti di prodotto `rest/V1/products/sku/media`.
* **ACSD-50276** (per Adobe Commerce >=2.4.0 &lt;2.4.7) - Risolve il problema relativo al mancato funzionamento del modulo di registrazione cliente nella vetrina se viene creato un attributo cliente a selezione multipla.
* **ACSD-50527** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge l&#39;errore che si verifica quando si salva una pagina con un blocco dinamico vuoto.
* **ACSD-49973** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5) - Migliora le prestazioni del recupero dei prodotti in bundle tramite GraphQL.
* **ACSD-51114** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7): è stato risolto il problema che causava la scomparsa di un prodotto casuale da cataloghi di grandi dimensioni quando l&#39;indicizzazione asincrona era abilitata. Migliora le prestazioni della reindicizzazione asincrona per i cataloghi di grandi dimensioni.
* **B2B-2598** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.7) - Aggiungi funzionalità di caching alle query GraphQL [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] e [!UICONTROL storeConfig].
* Nuove versioni aggiunte per MDVA-42806, ACSD-48627, ACSD-46815.
* Aggiornamento dei metadati delle patch per ACSD-49773, ACSD-47179 e ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.7) - Corregge il problema per cui un&#39;e-mail pronta per il prelievo viene inviata dall&#39;API quando l&#39;ordine non è pronto per il prelievo.
* **ACSD-49822** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli aggiornamenti nella pagina [!UICONTROL Requisition List] non vengono riflessi in [!UICONTROL Print Requisition List].
* **ACSD-48771** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema di aggiornamento del tipo di contenuto a blocchi di colonna dalle versioni [!DNL Page Builder] precedenti.
* **ACSD-49464** (per Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where invoices, shipments, and credit memos are not moved back from the archive when the orderId is different.
* **ACSD-49773** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where product export fails when AWS S3 is used as remote storage.
* **ACSD-49748** (per Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where invitations cannot be sent.
* **ACSD-49502** (per Adobe Systems Commerce >=2.4.3 &lt;2.4.7) - Fixes the issue where the downloadable link is not updated properly after a staging update is applied to the downloadable product.
* **ACSD-49527** (per Adobe Systems Commerce >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL company roles don&#39;t display pagination correctly.
* **ACSD-49706** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the default value is saved for a visual swatch attribute when no value is selected.
* **ACSD-49835** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the Use default checkbox value is not saved correctly on a store level for a multi-select attribute.
* **ACSD-49898** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the products grid throws an exception when a bundled product has a special price that exceeds 1000.
* **ACSD-50234** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.5) - Fixes the issue with the wrong customer name in the confirmation email if placing an order with [!DNL PayPal].
* **ACSD-49960** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where filtering by date does not work for the customer order grid.
* **ACSD-49849** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where customer email was replaced with [!DNL PayPal] email when placing an order with [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (for Adobe Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where Shared Catalog Pricing and structure throws an error in Admin when products have single or double quotes in SKU.
* **ACSD-49970** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes incorrect handling of GraphQL errors when [!DNL New Relic] reporting is turned on.
* **ACSD-50260** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where GraphQL product search results are limited to 10,000 results only.
* **ACSD-48813** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where the search is not showing relevant results based on the search weight of the attributes.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.3) - Corregge il problema per cui una regola del prezzo di catalogo creata in base all&#39;attributo Sì/No non considera l&#39;ambito selezionato.
* **ACSD-47704** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla visualizzazione del prezzo dei soli prodotti in magazzino nel prodotto in bundle.
* **ACSD-49370** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui l&#39;attributo di prodotto *Date Time* ha un tipo *FilterMatchTypeInput* nello schema di GraphQL.
* **ACSD-48807** (for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.7) - Fixes the issue where customer Product Reviews are not filtered by storeview via GraphQL.
* **ACSD-49433** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui l&#39;importo predefinito viene visualizzato come subtotale nel carrello della gift card con un importo aperto.
* **ACSD-48866** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema che si verifica in caso di errore durante la richiesta del feed RSS per le categorie.
* **ACSD-48784** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Risolve il problema relativo alla memorizzazione errata nella cache dei prezzi del segmento cliente tra i gruppi di clienti.
* **ACSD-48857** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Corregge il problema per cui un utente non è in grado di salvare le modifiche dopo averle modificate con Page Builder.
* **ACSD-49065** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli elementi delle virgolette non sono visibili nell&#39;amministratore se assegnati solo alle azioni personalizzate.
* **ACSD-49179** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the Orders Report shows incorrect amounts in case of different currencies for different stores.
* **ACSD-49286** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where a product is added twice to a cart when multiple product widgets are present on the page.
* **ACSD-49574** (per Adobe Commerce >=2.4.4 &lt;2.4.7) - Aggiunge funzionalità per supportare gli aggiornamenti dei prodotti Gift Card nel carrello tramite GraphQL.
* Aggiornamento della patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (per Adobe Commerce >=2.4.1 &lt;2.4.7) - Corregge il problema relativo all&#39;utilizzo dell&#39;indirizzo di spedizione predefinito anziché di uno nuovo quando si effettua un ordine utilizzando un preventivo negoziabile.
* **ACSD-48059** (per Adobe Commerce >=2.3.7 &lt;2.4.7) - Corregge il problema per cui gli esercenti non possono salvare &quot;[!UICONTROL Match product by rule]&quot; nella categoria.
* **ACSD-48216** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Corregge il problema per cui [!UICONTROL AUTO_INCREMENT] della tabella [!UICONTROL inventory_source_item] aumenta con l&#39;operazione [!UICONTROL UPDATE].
* **ACSD-47908** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the error &quot;A value less than or equal to 0 is expected&quot; when selecting the source and qty on the shipping step during checkout.&lt;/2.3.8>
* **ACSD-49497** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where an order remains in the processing state after shipment and a partial refund is applied.
* **ACSD-48694** (per Adobe Systems Commerce e Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.1 &lt;2.4.7) - Fixes the issue where the error &quot;Invalid state change requested&quot; prevents a customer from placing an order.&lt;/2.3.8>
* **ACSD-49013** (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where email confirmation is not translated to the website locale when creating customers using bulk API.
* **ACSD-48164** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema per cui un amministratore con restrizioni non può salvare un valore a livello di sito Web.
* **ACSD-48404** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema &quot;Ricorda paginazione categoria = Sì&quot; causa un errore quando si preme il pulsante Indietro del browser.
* **ACSD-48634** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge gli errori JS in una pagina di aggiornamento dell&#39;area di gestione temporanea quando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; è abilitato.
* **ACSD-49042** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where a product with infinite backorder cannot be ordered from the Storefront.
* Updated patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (for Adobe Commerce and Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Fixes the issue where price drop notifications are not always sent due to application-level caching.
* **ACSD-48661** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where if the company&#39;s credit limit is larger than 999, the comma separator prevents the saving of the company due to a validation error.
* **ACSD-48773** (per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.7) - Corregge il problema per cui il modello e-mail dei punti premio viene prelevato dall&#39;archivio errato.
* **ACSD-48587** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.7) - Corregge il problema relativo alla mancata visualizzazione dei prodotti corrispondenti da parte dei caratteri speciali HTML nelle regole di corrispondenza dei widget prodotti.
* **ACSD-48212** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema se l&#39;importazione del prodotto assegna il prodotto all&#39;origine errata.
* **ACSD-47988** (per Adobe Commerce e Magento Open Source >=2.3.7 &lt;2.4.6) - Corregge il problema relativo al taglio dei tag HTML nell&#39;esportazione del prodotto dalla descrizione del prodotto Page Builder.
* **ACSD-48366** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the product image is not displayed on the Back to Stock email template.
* **ACSD-48417** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.7) - Corregge il problema relativo alla visualizzazione di un errore SQL dopo la creazione di una modifica della pianificazione per un prodotto e il salvataggio di un altro prodotto.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Risolve il problema relativo al mancato funzionamento della reindicizzazione del prezzo del prodotto se il prodotto bundle non è assegnato ad alcun sito Web.
* **ACSD-48262** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui i prodotti non sono visibili sul front-end quando &quot;Consenti tutti i prodotti per pagina&quot; è impostato su Sì.
* **ACSD-48293** (per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4) - Corregge il problema relativo all&#39;esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte.
* **ACSD-47520** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema della perdita di punti premio da parte dei clienti durante la creazione di una nota di credito.
* **ACSD-48044** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Corregge il problema che impedisce l&#39;inserimento di ordini quando si applicano più carte regalo a un singolo ordine con spedizione multipla.
* **ACSD-48300** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Risolve il problema che impediva la creazione di una restituzione se il prodotto configurabile veniva rimosso.
* **ACSD-47910** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema di ordini, fatture, spedizioni e note di credito mancanti nelle rispettive griglie di entità.
* **ACSD-47292** (per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Corregge il problema per cui i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL se &quot;mostra prodotti esauriti&quot; è impostato su Sì.
* **ACSD-48234** (per Adobe Systems Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the catalog search result shows an incorrect category item count when the &quot;show out of stock&quot; option is enabled.
* **ACSD-48313** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.5) - Fixes the issue where the &quot;configurable_variations&quot; column is not parsed if the attribute value contains a comma. Lo stesso algoritmo di analisi viene utilizzato per &quot;additional_attributes.
* **ACSD-48627** (per Adobe Commerce e Magento Open Source >=2.4.5 &lt;2.4.6) - Corregge il problema per cui il prodotto configurabile esaurito causa un errore durante l&#39;invio di una richiesta GraphQL per ottenere i dettagli del carrello.
* Aggiornamento della patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where SEO-friendly URLs are not generated for products that have *url_key* attributi ignorati a livello di visualizzazione store.
* **ACSD-46865** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the Shipment and Credit Memo grid is not populated when asynchronous indexing is enabled.
* **ACSD-47004** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where VAT is not applied to a billing address without a VAT ID.
* **ACSD-47803** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where out-of-stock configurable product swatches are displayed as available.
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
* **ACSD-47666** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the filter function does not work in the Admin > System > Permissions > User roles > a role > Role Users grid.
* **ACSD-47497** (per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Corregge il problema per cui la scheda Servizi non è visibile in Configurazione in Amministrazione.
* Aggiornamento della patch: ACSD-47743.
* Patch sostituite: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.3) - Fixes the _Tentativo di accesso offset array sul valore di tipo bool_ error quando si accede a determinati percorsi di categorie non esistenti per prodotti noti su PHP 7.4.
* **ACSD-47332** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where cron fails with an error that is only reported when running between 00:00 and 00:59 UTC.
* **ACSD-47280** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where disabling the shared catalog feature on a specific scope does not work correctly.
* **ACSD-47106** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where a value cannot be saved in a new custom attribute on a company creation page.
* Patch aggiornata: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where a user gets an error when assigning a large number of product sources.
* **ACSD-46856** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) -=&quot;&quot; improves=&quot;&quot; performance=&quot;&quot; updating=&quot;&quot; tier=&quot;&quot; prices=&quot;&quot; via=&quot;&quot; system=&quot;&quot;> configurazione > Importa > Avanzate prezzi.&lt;/2.4.6)>
* **ACSD-46541** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where an admin user cannot create a credit memo if an order item is deleted.
* **ACSD-46581** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the estimated tax total is not updated after selecting a country in the shopping cart.
* **ACSD-46618** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where the product list widget shows incorrect cached prices for a logged-in customer.
* **ACSD-46674** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where custom options of an image type are displayed as HTML in customer emails.
* **ACSD-46988** (per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the GraphQL &#39;currency&#39; API Request returns NULL values for a custom currency.
* **ACSD-47076** (per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.5) -  Fixes the issue where Vimeo videos cannot be played on the storefront.
* **ACSD-45071** (per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4) - Fixes the issue where the default source is added to the product during import.
* **AC-3023** (per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.6) - Update DHL scheme to latest version 10.0.
* Patch aggiornate: MDVA-42584.
* Patch sostituite: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Risolve il problema per cui un utente ottiene uno stato d&#39;ordine errato quando viene rimborsato utilizzando il credito store.
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
* **ACSD-45781** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.2*) - Risolve il problema per cui il campo ricerca anteriore store non viene visualizzato sul dispositivo mobile.
* **ACSD-46192 (per Adobe Systems Commerce e Magento Open Source >=2.3.6 &lt;2.4.5 *) - Risolve il problema con l&#39;utilizzo dell&#39;endpoint`async/bulk/V1/configurable-products/bySku/options`.***
* **ACSD-46404** (*per Adobe Systems Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Risolve il problema per cui un utente amministratore non può accedere dopo l&#39;aggiornamento a 2.4.4.
* Patch aggiornate: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Risolve il problema per cui una mutazione del prodotto GraphQL per un store specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate al store richiesto.
* **ACSD-46146** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.6*) - Risolve il problema per cui vengono inviate due e-mail di conferma dell&#39;ordine dopo aver effettuato un ordine dall&#39;amministratore.
* **ACSD-45255** (*per Adobe Systems Commerce >=2.4.3 &lt;2.4.6*) - Risolve un&#39;eccezione nella pagina Rapporto Stock basso per un utente di amministrazione con restrizioni.
* **ACSD-45488** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.6*) - Risolve il problema per cui un prodotto configurabile con più origini non viene restituito automaticamente a In Stock.
* **ACSD-45754** (*per Adobe Systems Commerce e Magento Open Source >=2.3.1 &lt;2.4.6*) - Risolve il problema per cui i punti Reward non vengono aggiunti dopo aver applicato un coupon al carrello.
* **ACSD-45849** (*for Adobe Commerce >=2.4.3 &lt;2.4.4*) - Fixes the issue where video metadata is lost after a staging update is applied.
* **ACSD-45257** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;2.4.4*) - Fixes the issue where GraphQL doesn&#39;t display a cart discount correctly.
* **ACSD-44938** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4*) - Fixes the issue where `VAT_ID` cannot be applied in a GraphQL request for a guest user.
* Updated patches: MDVA-43417.

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
* **MDVA-44562** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Corregge il problema per cui l&#39;ID dell&#39;archivio non predefinito per gli elementi dell&#39;offerta viene sostituito dall&#39;ID dell&#39;archivio predefinito, nonostante la richiesta GraphQL provenga dalla visualizzazione dell&#39;archivio non predefinito.
* **MDVA-43167** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui l&#39;azione di massa della griglia degli ordini amministratore non viene applicata a più pagine quando l&#39;utente amministratore seleziona tutti gli ordini.
* **MDVA-44044** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Corregge il problema che impedisce la visualizzazione di un prodotto nella pagina della categoria dopo l&#39;assegnazione a un nuovo sito Web.
* **MDVA-42509** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.4*) - Corregge il problema relativo all&#39;impossibilità di caricare un file CSV per un ordine rapido, causando un errore *Impossibile inviare il cookie*.
* Patch aggiornate: MDVA-41061, MDVA-42584.
* Il prefisso per le nuove patch [!DNL Quality Patches Tool] verrà modificato da *MDVA* a *ACSD* a causa di modifiche di processo interne.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui non è possibile aggiungere al carrello un elemento aggiuntivo se la quantità minima dell&#39;elemento è già nel carrello.
* **MDVA-44887** (*per Adobe Commerce e Magento Open Source >=2.4.4 &lt;2.4.5*) - Corregge *Errore di sintassi non rilevato: errore &#39;const&#39;* del token imprevisto nel pannello di amministrazione.
* **MDVA-43718** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Correzioni *Il consumatore non è autorizzato ad accedere a %resources.Errore* visualizzato quando si accede a un catalogo condiviso da un&#39;integrazione personalizzata.
* **MDVA-44660** (*per Adobe Commerce e Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Corregge il problema per cui non è possibile utilizzare il carattere accento grave ``` ` ``` per il nome e il cognome di un cliente.
* **MDVA-40896** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge l&#39;errore *Errore: TypeError: l&#39;argomento 3 passato al Magento* nell&#39;API di massa del prodotto asincrono.
* **MDVA-38559** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.3*) - Fixes the */V1/customers/search API* error for customers with more than one subscription.
* **MDVA-44533** (*for Adobe Commerce and Magento Open Source >=2.3.1 &lt;2.4.4*) - Fixes the issue where the discount is wrongly applied to a bundle child product.
* Updated patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.5*) - Fixes the issue where products *Not Visible Individually* still appear in Catalog Advanced Search Results.
* **MDVA-44100** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui tutti gli FPT vengono assegnati all&#39;ultimo prodotto nel carrello e reimpostati per altri prodotti.
* **MDVA-43605** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui i dati dell&#39;ordine restituiscono valori negativi per i totali delle righe quando si utilizza l&#39;API Rest.
* **MDVA-43102** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;2.4.5*) - Corregge il problema per cui la quantità vendibile non viene aggiornata correttamente quando viene effettuato un rimborso tramite API REST.
* **MDVA-43178** (*per Adobe Commerce e Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Corregge il problema per cui non è possibile recuperare in GraphQL un token cliente per un archivio personalizzato.
* **MDVA-43859** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.5*) - Fixes the issue where the error *No such entity with customerId =* is logged when a deleted customer tries to log in.
* **MDVA-44147** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui una richiesta GraphQL non restituisce gli elenchi di richieste.
* **MDVA-44505** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge i problemi in cui l&#39;applicazione dei punti premio di GraphQL non aggiorna il totale complessivo e in cui il credito dell&#39;archivio viene applicato più volte durante il posizionamento dell&#39;ordine.
* Patch aggiornate: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge il problema relativo al funzionamento della regola prodotto correlata solo quando Segmento cliente è impostato su *All*.
* **MDVA-39605** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui il valore TTL (data di scadenza) della cache Redis è errato.
* **MDVA-43862** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corregge il problema per cui il cliente non può aggiornare gli elementi del carrello a causa di un errore *UpdateCartItems* di GraphQL.
* **MDVA-43824** (*per Adobe Commerce e Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Corregge il problema relativo alla visualizzazione di un errore durante l’annullamento di ordini con uno sconto.
* **MDVA-43451** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui l&#39;errore *Impossibile trovare l&#39;archivio richiesto. Verifica l’archivio e riprova.* viene visualizzato durante la configurazione di un catalogo condiviso per un sito Web specifico.
* **MDVA-43491** (*per Adobe Systems Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Risolve il problema per cui l&#39;etichetta dell&#39;immagine di base non si aggiorna durante l&#39;importazione di prodotti per un sito Web store contenuti.
* **MDVA-43601** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema dei trigger mancanti dopo la reindicizzazione completa.
* **MDVA-42046** (*per Adobe Systems Commerce e Magento Open Source >=2.3.4 &lt;=2.3.5-p2 ||=&quot;&quot;>=2.4.0 &lt;2.4.5*) - Risolve il problema per cui un valore non corretto viene assegnato a un attributo del prodotto con un campo di immissione della data durante l&#39;aggiornamento di un prodotto.&lt;/=2.3.5-p2>
* **MDVA-43935** (*per Adobe Systems Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Risolve il problema per cui il prodotto Upsell viene mostrato due volte.
* **MDVA-44188** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui le e-mail emesse dal sistema con `.-` negli indirizzi non vengono inviate.
* **MDVA-42283** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il formato data-ora nella griglia dell&#39;ordine di amministrazione per le impostazioni locali francesi non è valido.
* Patch aggiornate: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Sono state aggiunte patch metadati per .[!DNL Site-Wide Analysis Tool]

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.3.6*) - Risolve il problema per cui il utente è in grado di modificare l&#39;ora di inizio per un aggiornamento pianificato attivo.
* **MDVA-42410** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.5*) - Fixes the issue where coupon reports display only the default base currency.
* **MDVA-41136** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0*&lt;2.4.5 ) - Risolve il problema per cui la data di scadenza del non viene estesa, con conseguente pulizia dei `mage-cache-sessid` dati dei clienti.
* **MDVA-39993** (*per Adobe Systems Commerce e Magento Open Source >=2.3.5 &lt;=2.3.7-p2 ||=&quot;&quot;>=2.4.0 &lt;2.4.4*) - Risolve il problema per cui le modifiche all&#39;inventario effettuate tramite API non si riflettono sulla pagina del prodotto sul frontend.&lt;/=2.3.7-p2>
* **MDVA-42855** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Risolve il problema per cui un nuovo indirizzo cliente non viene salvato nella rubrica durante il checkout.
* **MDVA-42645** (*per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se store funzionalità di credito è disabilitata.
* **MDVA-43414** (*per Adobe Systems Commerce e Magento Open Source >=2.3.6*&lt;=2.3.7-p2 ) - Corregge l&#39;errore irreversibile di PHP che si verifica durante l&#39;esecuzione del `inventory.reservations.updateSalabilityStatus` consumer coda su SKU numerici.
* **MDVA-41628** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;2.4.5*) - Risolve il problema per cui gli utenti amministratori con restrizioni esistenti ottengono accesso alle nuove risorse quando vengono aggiunti nuovi moduli.
* **MDVA-43348** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Risolve il problema per cui gift scheda GraphQL richiesta mostra un errore se `gift_card_options` contiene *uid*.
* **MDVA-39546** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema per cui la data di inizio dell&#39;aggiornamento temporaneo poteva essere impostata su una data precedente a quella corrente durante la modifica.
* **MDVA-42950** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema per cui i video non vengono riprodotti sulla pagina del prodotto.
* **MDVA-42689** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema per cui Adobe Systems Commerce genera un *errore di integrità Vincolo violazione* durante l&#39;aggiornamento delle categorie di prodotti durante l&#39;importazione.
* **MDVA-41229** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Risolve il problema per cui le immagini disponibili sul backend non vengono visualizzate sul frontend dopo l&#39;importazione di prodotti configurabili.
* **MDVA-43731** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4*) - Fixes the issue where *Search Synonyms* no longer work when value is added in *Minimum Terms to Match*.
* **MDVA-43232** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;2.4.5*) - Corregge il problema per cui l&#39;ordinamento dei prodotti in [!DNL Visual Merchandiser] in base al prezzo speciale Inferiore/Superiore causa un errore durante il salvataggio della categoria.
* **MDVA-43726** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.3*) - Corregge il problema per cui la regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio non viene applicata dopo la reindicizzazione parziale.
* Patch aggiornate: MDVA-36464, MDVA-37478, MDVA-38608.
* Sono state aggiunte patch metadati per .[!DNL Site-Wide Analysis Tool]

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema per cui gli attributi del prezzo del prodotto non possono essere aggiornati per un sito Web specifico tramite API REST.
* **MDVA-41350** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo alla generazione di un&#39;eccezione quando un utente amministratore con accesso limitato aggiunge un prodotto al di fuori del proprio ambito di ruolo da parte di SKU in un ordine.
* **MDVA-42269** (*per Adobe Commerce e Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Corregge il problema che impedisce a un utente amministratore di accedere all&#39;amministratore a causa di *Errore di tipo: strtotime() prevede che il parametro 1 sia una stringa, null specificato* errore.
* **MDVA-40830** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui il credito dell&#39;archivio viene applicato più volte durante il posizionamento dell&#39;ordine.
* **MDVA-42237** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema che impedisce l&#39;aggiornamento di un prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del relativo sottoprodotto.
* **MDVA-42520 (per Adobe Systems Commerce e Magento Open Source >=2.4.3 &lt;2.4.4 *) - Risolve il problema per cui l&#39;aliquota fiscale viene applicata due volte se*si utilizza Enable Cross Bordo Trade *.***
* Patch aggiornate: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Patch obsoleta: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*per Adobe Commerce e Magento Open Source >=2.3.2 &lt;2.4.5*) - Corregge il problema che causa la riscrittura dell&#39;URL per l&#39;archivio predefinito solo dopo la modifica di *Visibilità prodotto*.
* **MDVA-43091** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.4*) - Corregge il problema per cui l&#39;ordinamento di un prodotto bundle dall&#39;amministratore nel backend restituisce l&#39;errore *Impossibile utilizzare una quantità decimale per questo prodotto*.
* **MDVA-40816** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-41305** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.5*) - Corregge il problema per cui la mutazione GraphQL non restituisce opzioni di prodotto configurabili dopo l&#39;aggiunta del prodotto alla lista dei desideri.
* **MDVA-39181** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui le regole di prodotto correlate mostrano prodotti di categorie non definite nelle condizioni della regola.
* **MDVA-42584** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui lo stato delle scorte configurabili nel backend non viene aggiornato dopo la modifica della quantità e dello stato delle scorte tramite Importazione o API.
* **MDVA-40175** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.3*) - Corregge il problema per cui *Fare clic per modificare il metodo di spedizione* non mostra i pulsanti di scelta per selezionare i metodi di spedizione nell&#39;amministratore durante il riordino.
* **MDVA-42768** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;2.4.5*) - Fixes the issue where Configurable product displays regular price as 0 when *Display Out-of-Stock* is Yes.
* **MDVA-43201** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes the issue where an error occurs in customer login when using DOB attribute with certain locales.
* Updated patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;2.4.5*) - Corregge il problema relativo al malfunzionamento dei filtri data quando il fuso orario di Adobe Commerce è diverso da quello dell&#39;ambiente locale.
* **MDVA-42657** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di selezionare le categorie nelle condizioni del segmento cliente.
* **MDVA-42806** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui viene inviata un&#39;e-mail di *Registrazione nuova società* ogni volta che una società esistente viene aggiornata tramite API REST.
* **MDVA-37984** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.5*) - Corregge il problema per cui la funzionalità [!DNL Visual Merchandiser] *Corrispondenza prodotto per regola* non filtra correttamente i prodotti con aggiornamenti di staging.
* **MDVA-40488** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.4*) - Corregge il problema per cui i prodotti configurabili con prodotti figlio esauriti non vengono visualizzati nell&#39;intervallo di prezzo corretto.
* **MDVA-42507** (*per Adobe Commerce e Magento Open Source >=2.4.3 &lt;2.4.5*) - Corregge il problema di pulizia della cache di pagina intera dopo l&#39;applicazione dell&#39;aggiornamento di staging per la regola del carrello.
* **MDVA-39163** (*per Adobe Commerce e Magento Open Source >=2.3.5 &lt;2.4.5*) - Corregge il problema per cui i metodi di spedizione non sono disponibili quando viene registrato un nuovo utente e i prodotti nel carrello provengono dalla sessione guest.
* **MDVA-38626** (*per Adobe Commerce e Magento Open Source >=2.3.3 &lt;2.4.5*) - Corregge il problema per cui l&#39;utente amministratore non è in grado di effettuare un ordine sul backend utilizzando il pagamento [!DNL PayPal Payflow Pro].
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
* **MDVA-41399** (*per Adobe Systems Commerce e Magento Open Source >=2.3.3 &lt;2.4.2*) - Risolve il problema per cui gli utenti amministratori non sono in grado di accesso la *pagina Gestisci carrello* se un cliente aggiunge un prodotto alla lista dei desideri.
* **MDVA-40609** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema relativo all&#39;assenza di dati di prodotti disabilitati nella tabella indice `cataloginventory_stock_status`, con la visualizzazione di quantità di prodotti disabilitati errate.
* **MDVA-39031** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui è possibile aggiungere un prodotto al carrello tramite GraphQL anche se non è assegnato al sito Web di destinazione.
* **MDVA-41597** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes the issue where users get an error when adding more than one configurable product to the cart using GraphQL.
* **MDVA-27456** (*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.3.7*) - Fixes the issue where users get an error when trying to load [!DNL Swagger].
* **MDVA-32776** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.2*) - Corregge il problema per cui lo stato delle scorte non viene aggiornato quando viene effettuato un ordine ma non viene spedito.
* **MDVA-30862** (*per Adobe Systems Commerce e Magento Open Source >=2.3.4 &lt;2.4.0*) - Risolve il problema con la data dell&#39;ordine errata sulla fattura PDF stampata.
* È stata migliorata la pagina indice per .[!DNL Quality Patch Tool] Sono stati aggiunti utili ricerca e filtri per [!DNL quality patches] l&#39;ultima versione di strumento.
* Patch aggiornate: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema in cui è impossibile creare un nuovo aggiornamento pianificato o modificare un aggiornamento pianificato esistente per un prodotto se la data di fine è stata precedentemente rimossa.
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
* **MDVA-40401** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Fixes the issue where coupon usage value changes even if placing an order fails.
* **MDVA-40537** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Fixes the issue where users get an error when creating a store view if several CMS pages with the same URL key exist.
* **MDVA-37725** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Fixes the issue where asynchronous order emails sent from non-default websites contain logo URLs from the default website.
* **MDVA-39482** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Fixes the issue where a product goes out of stock if imported with &quot;0&quot; quantity when backorders enabled.
* **MDVA-40435** (*for Adobe Commerce and Magento Open Source >=2.3.4 &lt;2.4.4*) - Fixes the issue with an incorrect discount on bundle products with dynamic prices when applied via GraphQL.
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
* **MDVA-36309** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Risolve il problema per cui il ricerca degli attributi del prodotto è lento nelle griglie di amministrazione.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*) - Fixes the issue where the invoice with FPT shows a wrong Grand Total when the order is paid from the store credit.
* **MDVA-37364** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;=2.4.3*) - Fixes the issue where the custom customer attribute of date type breaks the customer&#39;s grid UI.
* **MDVA-39195** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Fixes the issue where *Add to Cart* button was inactive on the category page when redirect to cart enabled.
* **MDVA-37115** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Fixes the issue where an unnecessary *Only 0 left* notice is shown on the configurable product page.
* **MDVA-39521** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4*) - Fixes the issue where the user is not able to set shipping addresses on the cart with an empty telephone number via GraphQL.
* **MDVA-39384** (*per Adobe Commerce e Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Corregge il problema per cui l’attributo cliente personalizzato per un utente aziendale non viene salvato.
* **MDVA-39043** (*per Adobe Commerce e Magento Open Source >=2.3.4 &lt;=2.4.3*) - Corregge il problema per cui l&#39;utente amministratore con accesso limitato riceve un errore durante il tentativo di aggiungere il widget *Products* alla pagina CMS.
* **MDVA-39966** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Corregge il problema relativo alla distribuzione di impostazioni internazionali non corrette.
* **MDVA-38852** (*per Adobe Commerce e Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Corregge il problema che impedisce all&#39;inventario dei cataloghi per progettazione di bloccare le tabelle per gli aggiornamenti che riducono in modo significativo le prestazioni nei casi con diversi ordini paralleli.
* **MDVA-39986** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.3*) - Corregge il problema per cui l&#39;utente non è in grado di effettuare un ordine in Admin su MacOS utilizzando il browser Safari.
* **MDVA-38447** (*per Adobe Systems Commerce e Magento Open Source >=2.4.2*&lt;2.4.4 ) - Risolve due problemi: in cui i prodotti secondari non visibili configurabili individualmente *vengono restituiti nella risposta GraphQL e ottimizzano la* query MySQL per la query dei prodotti GraphQL con filtro di categoria.
* **MDVA-40134** (*per Adobe Commerce e Magento Open Source >=2.4.2 &lt;2.4.3*) - Corregge il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato.
* **MDVA-39935** (*per Adobe Commerce e Magento Open Source >=2.4.1 &lt;2.4.4*) - Corregge il problema per cui GraphQL restituisce prodotti secondari configurabili disabilitati a livello di sito Web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*per Adobe Commerce e Magento Open Source >=2.4.0 &lt;2.4.4*) - Corregge il problema per cui l&#39;errore *Richiama a una funzione membro getId()* viene visualizzato nella pagina dei dettagli dell&#39;ordine nell&#39;amministratore.
* **MDVA-34948** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Fixes the issue with long-running queries, like `GET_LOCK`.
* **MDVA-39305** (*per Adobe Systems Commerce e Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Risolve il problema per cui i clienti registrati non sono in grado di accedere con Google ReCaptcha abilitato.
* **MDVA-37897** (*per Adobe Systems Commerce e Magento Open Source >=2.3.0 &lt;2.4.4*) - Risolve il problema con un&#39;reindirizzare errata quando un cliente tenta di aggiungere prodotti con opzioni dal widget Visualizzati di recente.

## v1.1.0 {#v1-1-0}

* Sono state introdotte categorie di patch per migliorare il esperienza di utilizzo e rendere più facile per i clienti la ricerca delle patch richieste.
* Il `patches.json` file è stato rinominato in `support-patches.json`.
* **MDVA-38799** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.3*) - Risolve il problema per cui i prodotti scaricabili non venivano salvati dopo la creazione di un aggiornamento di staging.
* **MDVA-37592** (*per Adobe Systems Commerce >=2.3.6 &lt;=2.4.2-p1*) - Risolve il problema quando l&#39;ordinamento per prezzo non funziona correttamente per i prodotti con un prezzo zero assegnato al catalogo condiviso.
* **MDVA-38827** (*per Adobe Systems Commerce >=2.3.3-p1 &lt;2.4.4*) - Risolve il problema per cui i clienti ricevono un&#39;e-mail di spedizione dell&#39;ordine contenente un messaggio di errore.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*per Adobe Systems Commerce >=2.3.2*&lt;=2.3.5-p2 ) - Corregge l&#39;errore durante il salvataggio delle pagine CMS: *Elemento con lo stesso ID PAGE_ID esiste* già.
* **MDVA-34680** (*per Adobe Systems Commerce >=2.3.6 &lt;=2.3.7 ||=&quot;&quot;>=2.4.1 &lt;2.4.3*) - Risolve il problema per cui il tempo di creazione dell&#39;account cliente non viene filtrato correttamente nella griglia dei clienti.&lt;/=2.3.7>
* **MDVA-37068** (*for Adobe Commerce >=2.3.1 &lt;2.4.4*) - Fixes the issue where the incorrect tax rate displays when the shopping cart has only virtual products.
* **MDVA-38608** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema relativo alla mancata eliminazione delle tabelle temporanee al termine della reindicizzazione.
* **MDVA-38308** (*per Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2,4,0 &lt;=2,4,1-p1 || >=2.4.2 &lt;2.4.4*) - Corregge i problemi relativi all&#39;aggiunta di [!DNL Vimeo] video ai prodotti.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*per Adobe Systems Commerce >=2.3.6*&lt;2.4.3 ) - Risolve il problema per cui il cliente non viene indirizzato alla pagina di conferma del pagamento quando utilizza il [!DNL Paypal Payment Advanced] metodo.
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

* **MDVA-37478** (*per Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Corregge il problema che genera un errore in Adobe Commerce durante la creazione di una fattura parziale per gli ordini effettuati con il metodo di pagamento *Pagamento in conto* tramite API REST.
* **MDVA-37362** (*per Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Corregge il problema per cui i valori delle opzioni di prodotto configurabili e gli attributi della variante erano vuoti nella risposta di GraphQL.
* **MDVA-37288** (*per Adobe Commerce 2.4.2*) - Corregge il problema relativo alla restituzione di prezzi di livello errati dopo la richiesta GraphQL.
* **MDVA-37225** (*per Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Risolve il problema relativo al blocco del processo di caricamento durante la creazione rapida dell&#39;ordine in presenza di un valore intero negli SKU importati.
* **MDVA-37224** (*per Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Corregge il problema che impedisce ai clienti di pagare un preventivo negoziabile con [!DNL PayFlow Pro] con un altro prodotto nel carrello.
* **MDVA-36286** (*per Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Risolve il problema relativo all&#39;interruzione dell&#39;anteprima del widget prodotti Page Builder se lo stesso SKU ha una posizione diversa nelle sottocategorie.
* **MDVA-30186** (*per Adobe Systems Commerce >=2.3.4 &lt;=2.3.5-p2,>=2.4.0 &lt;=2.4.0-p1,>=2.4.2 &lt;=2.4.2-p1*) - Risolve il problema per cui le opzioni degli attributi vengono ordinate in base al valore dell&#39;opzione anziché al conteggio degli elementi dell&#39;attributo nella risposta GraphQL.&lt;/=2.4.0-p1,>&lt;/=2.3.5-p2,>

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*per Adobe Systems Commerce >=2.3.0 &lt;=2.4.2*) - Risolve il problema per cui le vecchie opzioni personalizzate rimangono dopo essere state modificate tramite API.
* **MDVA-35773** (*per Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Corregge il problema che impedisce la visualizzazione del totale complessivo come zero nella fattura per gli ordini con sconto del 100%.
* **MDVA-36833** (*per Adobe Commerce 2.4.2*): è stato risolto il problema che causava la visualizzazione di numeri casuali di prodotti per pagina nei risultati di ricerca dopo l&#39;esclusione di alcuni prodotti dal catalogo condiviso.
* **MDVA-37182** (*per Adobe Systems Commerce >=2.4.1*&lt;=2.4.2 ) - Risolve il problema con l&#39;ottenimento di risultati di ricerca errati sia nella versione 6 che [!DNL Elasticsearch] nella versione 7.
* **MDVA-36253** (*per Adobe Systems Commerce >=2.4.0 &lt;=2.4.1-p1*) - Risolve il problema per cui il subtotale errato viene visualizzato nel mini carrello dopo l&#39;eliminazione dell&#39;articolo.
* **MDVA-36853** (*per Adobe Systems Commerce 2.4.2*) - Risolve il problema della mancata visualizzazione di immagini durante il caricamento di gallerie di media di grandi dimensioni.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*per Adobe Systems Commerce >=2.3.4 &lt;=2.3.4-p2*) - Risolve il problema dei prodotti in bundle mancanti nelle pagine delle categorie.
* **MDVA-36615** (*per Adobe Systems Commerce 2.4.2*) - Risolve il problema relativo al conteggio errato dei prodotti nella griglia dei prodotti Admin.
* **MDVA-36464** (*per Adobe Commerce >=2.4.0 &lt;=2.4.2*): è stato risolto il problema che impediva il funzionamento della configurazione della notifica e-mail a livello di visualizzazione archivio.
* **MDVA-36138** (*per Adobe Commerce ^2.3.2*) - Corregge il problema che causa la mancata rettifica del prezzo di spedizione e la visualizzazione del prezzo di spedizione completo ai clienti se non tutti gli articoli nel carrello sono idonei per la regola del carrello di spedizione gratuito.
* **MDVA-36424** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Corregge il problema per cui le immagini multimediali associate agli elementi Page Builder scompaiono quando il contenuto viene modificato ripetutamente, se l’URL di base del back-end è diverso dall’URL di base dello storefront.
* **MDVA-35984** (*per Adobe Commerce ^2.4.0*) - Corregge il problema relativo alla quantità di prodotto e alla quantità vendibile errate dopo la creazione di più spedizioni simultanee per lo stesso prodotto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Questo risolve il problema se la query GraphQL non viene memorizzata nella cache utilizzando il tag cache delle categorie.
* **MDVA-33168** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Risolve il problema durante l&#39;aggiornamento di un attributo di prodotto tramite API. Tutti gli altri attributi vengono modificati in un valore vuoto.
* **MDVA-19640** (*per Adobe Commerce >=2.3.0*) - Corregge il problema se [!DNL Advanced Reporting] non visualizza alcun dato.
* **MDVA-11189** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Risolve il problema quando, dopo l&#39;importazione di un file CSV per aggiornare il materiale promozionale, le righe della tabella `cataloginventory_stock` vengono eliminate.
* **MDVA-26639** (*per Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Corregge il problema per cui se viene creato un nuovo modello e-mail di conferma dell&#39;ordine, gli elementi dell&#39;ordine mancano nell&#39;e-mail dell&#39;ordine.
* **MDVA-15546** (*per Adobe Commerce >=2.3.0*) - Corregge il problema per cui dopo la creazione di un ordine nel registro eccezioni viene visualizzato un errore *Column entity_id where clause is ambiguous*.
* **MDVA-21095** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema che si verifica quando una query `INSERT INTO search_tmp` non termina dopo l&#39;aggiornamento di massa del valore dell&#39;attributo.
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
* **MDVA-34591** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue with an incorrect cart rule discount calculation for *Maximum Qty Discount is Applied To* and *Discount Qty Step (Buy X)*.
* **MDVA-33704** (*for Adobe Commerce >=2.4.0 &lt;2.4.3*) - Fixes the issue where the *In store pickup* shipping option doesn&#39;t show up, though being configured to be available.
* **MDVA-34928** (*per Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Risolve il problema della visualizzazione indefinita del caricatore di pagine dopo la rimozione del credito dello store dal pagamento.
* **MDVA-35254** (*per Adobe Systems Commerce >=2.3.1 &lt;2.4.3*) - Risolve i problemi relativi al CAPTCHA durante il checkout.
* **MDVA-35569** (*per Adobe Systems Commerce >=2.3.4*&lt;2.4.2 ) - Risolve il problema per cui il *campo imposte* sul prodotto fisso non viene compilato nella risposta GraphQL quando viene specificato lo stato.
* **MDVA-35847** (*per Adobe Systems Commerce >=2.4.1 &lt;2.4.3*) - Risolve il B2B problema per cui il modulo Utenti società si interrompe se viene utilizzato un attributo cliente personalizzato.
* **MDVA-31307** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.2*) - Risolve il problema in cui sono presenti *errori di Memoria* esaurita in alcune categorie a causa di problemi con la whitelist CSP dinamica per i blocchi memorizzati nella cache.

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
* **MDVA-34850** (*for Adobe Commerce >=2.3.1 &lt;2.4.0*) - Fixes the issue where the out-of-stock options of a configurable product are not displayed instead of being displayed as struck-through.
* **MDVA-34867** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue where values for a condition field set for a scheduled update are not being saved.
* **MDVA-35092** (*for Adobe Commerce >=2.3.5 &lt;2.4.3*) - Fixes the issue where users are not able to add [!DNL Vimeo] videos due to deprecated [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*per Adobe Commerce >=2.3.6 &lt;2.4.3*) - Corregge il problema relativo al tipo di contenuto Anteprima prodotti Page Builder che si interrompe se i prodotti corrispondenti hanno prezzi diversi per ciascun sito Web.
* **MDVA-32634** (*for Adobe Commerce ^2.3.1*) - Fixes the issue where the `url_path` of the category assigned to all store remains unchanged after moving the category in the hierarchy.
* **MDVA-33344** (*per Adobe Systems Commerce ^2.3.0*) - Risolve il problema in cui l&#39;ID del set di attributi predefinito dell&#39;entità hardcoded `rma_item` viene utilizzato al posto del valore del database.
* **MDVA-34192** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.3*) - Risolve il problema che impediva di modificare/specificare la data di nascita del cliente utilizzando il formato gg/mm/aaaa.
* **MDVA-34847** (*per Adobe Commerce ^2.3.0*) - Corregge la conversione del tipo ID archivio in numero intero per la condizione SQL nelle raccolte amministratore per l&#39;utente amministratore con autorizzazioni personalizzate.
* **MDVA-34886** (*per Adobe Commerce ^2.3.2*) - Corregge il problema per cui la ricerca non restituisce risultati se l&#39;attributo di prodotto *weight* è configurato come ricercabile.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema del pagamento di [!DNL PayPal Payflow Pro] non riuscito con errore di formato dell&#39;elenco di parametri di reindirizzamento.
* **MDVA-34023** (*per Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corregge il problema per cui l&#39;errore *Nessuna entità con addressId* viene visualizzata in modo casuale nei browser dei visitatori.
* **MDVA-32759** (*per Adobe Commerce >=2.3.1 &lt;2.4.3 con estensione B2B*) - Corregge il problema di eliminazione dei prezzi dei livelli esistenti nei cataloghi condivisi.
* **MDVA-33482** (*per Adobe Systems Commerce ^2.3.5*) - Risolve il problema per cui la generazione di una nota di credito contro una fattura parziale comporta imposte per l&#39;ordine totale anziché imposte per quella fattura parziale.
* **MDVA-33393 (per Adobe Systems Commerce >=2.3.0 *&lt;2.4.2 ) - Corregge l&#39;errore*Il countryId fornito non esiste *.***
* **MDVA-33632** (*for Adobe Commerce >=2.3.0 &lt;2.3.7*) - Provides a fix where the exception message *This product is out of stock* is now displayed to an admin user when trying to re-order an out of stock product.
* **MDVA-34469** (*for Adobe Commerce >=2.4.1 &lt;2.4.2*) - Fixes the issue where GraphQL mutations on a customer&#39;s cart fail when using multiple store views.
* **MDVA-33976** (*for Adobe Commerce >=2.3.0 &lt;2.3.7*) - Fixes the issue where the bundle product is shown Out Of Stock on the storefront after removing the second option from the bundle product.
* **MDVA-33894** (*for Adobe Commerce >=2.4.0 &lt;2.4.1 with B2B extension*) - Fixes multiple issues for Quick Order functionality including adding and removing multiple products and SKU case sensitivity.
* **MDVA-27664** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) - Fixes the issue in the customer registration form causing an error to display: *ERROR - The Date of Birth should not be greater than today.*
* **MDVA-33970** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) - Fixes the issue where there is the wrong currency sign in the Credit Memo when the price attribute&#39;s scope is set to website.
* **MDVA-33992** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema della visualizzazione errata dei prezzi speciali B2B durante l&#39;estrazione.
* **MDVA-34100** (*per Adobe Commerce >=2.3.4 &lt;2.4.2 con estensione B2B*) - Corregge il problema per cui non è possibile creare un account aziendale dalla pagina della struttura aziendale.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*per Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Risolve il problema relativo alle immagini duplicate dopo l&#39;importazione del prodotto da un file CSV.
* **MDVA-33382** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge i problemi di invalidazione degli indicizzatori dopo la rimozione dei prodotti da una categoria.
* **MDVA-28511** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Risolve il problema che impediva il completamento dell&#39;estrazione di [!DNL PayPal] se il campo Nome contiene determinati caratteri (ad esempio lettere maiuscole accentate).
* **MDVA-31519** (*per Adobe Commerce >=2.3.5 &lt;2.3.6*) - Corregge il problema relativo ai timeout di attesa durante il pagamento degli ospiti quando è in uso una regola di vendita a livello di sito.
* **MDVA-33281** (*per Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corregge il problema relativo a un errore irreversibile in `inventory:reservation:list-inconsistencies` a causa di un tipo di parametro SKU errato.
* **MDVA-24201** (*per Adobe Commerce >=2.3.0 &lt;2.3.5*) - Corregge il problema per cui i prezzi riflettono la regola del prezzo del carrello pianificato solo dopo la reindicizzazione manuale.
* **MDVA-32694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Corregge il problema per cui un utente amministratore non può aggiungere un prodotto a un preventivo negoziabile se è correlato a un archivio non predefinito.
* **MDVA-33516** (*for Adobe Commerce >=2.3.0 &lt;2.3.6*) - Fixes the issue where editing a bundle product in a requisition list leads to an error.
* **MDVA-33975** (*per Adobe Systems Commerce >=2.3.4 &lt;2.4.2*) - Risolve diversi problemi relativi al calcolo dei prezzi nelle richieste GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*per Adobe Systems Commerce >=2.3.0*&lt;2.4.2 ) - Risolve il problema con [!DNL PayPal] i report di liquidazione che non erano disponibili in **Report** > **vendite** > **[!DNL PayPal]** liquidazione come previsto.
* **MCP-87** (*per Adobe Systems Commerce >=2.3.1 &lt;2.4.2*) - Migliorato il tempo di indicizzazione per gli indicizzatori di prodotti e azioni di categoria per profili di grandi dimensioni.
* **MDVA-33106 (per Adobe Systems Commerce >=2.3.0 &lt;2.4.2 *) - Risolve il problema per cui le modifiche di prodotto riprogrammate vengono cancellate dopo l&#39;esecuzione del comando cron`run`.***
* **MDVA-19391** (*per Adobe Systems Commerce >=2.3.0*&lt;2.3.5 ) - Risolve il problema in cui `analytics_collect_data` viene generato un errore a causa di `catalog_category_entity_text` record di descrizione NULL nella tabella.
* **MDVA-20376 (per Adobe Systems Commerce >=2.3.2 &lt;2.3.4 *) ) - Risolve il problema relativo all&#39;errore Nessuna entità con customerId = 1* nella per i clienti che hanno effettuato l&#39;accesso dopo la posizionamento dell&#39;ordine `exception.log` *.***
* **MDVA-23764** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge il bug in `JsFooterPlugin.php` che influisce sulla visualizzazione dei blocchi dinamici.
* **MDVA-13203** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che causa la visualizzazione dell&#39;errore *Violazione del vincolo di integrità search_tmp_ table* dopo la reindicizzazione completa.
* **MDVA-23426** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*) - Corregge il problema per cui le e-mail di notifica inviate da Adobe Commerce contengono un corpo vuoto con contenuto aggiunto come allegato.
* **MDVA-22150** (*for Adobe Commerce >=2.3.1 &lt;2.3.4*) - Fixes the issue where customers with a configurable product in cart and a coupon applied cannot login if that configurable product is disabled in the Admin.
* **MDVA-32545** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where invoices are not sent out automatically when creating orders from the Admin.
* **MDVA-32714** (*per Adobe Commerce >=2.3.4 &lt;2.4.1*) - Corregge il problema relativo al mancato funzionamento del prezzo del gruppo di clienti nella query del prodotto GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Aggiunge il *Subtotale (incl. Imposta)* opzione per le condizioni della regola di prezzo.
* **MDVA-31236** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.2*) - Risolve il problema per cui gli amministratori con accesso risorse personalizzate non sono in grado di impostare 2FA o accedere.
* **MDVA-30845** (*per Adobe Systems Commerce >=2.3.5 &lt;2.3.7*) - Risolve il problema per cui al momento *non sono disponibili preventivi per questo ordine viene visualizzato un* errore quando non si riesce a connettersi a UPS XML/USPS/DHL e nessun altro metodo di spedizione è disponibile.
* **MDVA-32133** (*for Adobe Commerce >=2.4.0 &lt;2.4.1*) - Fixes the issue where media gallery is not loading from Page Builder in certain cases.
* **MDVA-12304** (*per Adobe Commerce >=2.3.0*) - Aumenta il numero massimo di cookie da 50 a 200.
* **MDVA-32632** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Risolve il problema relativo agli ordini visualizzati nel sistema di pagamento, ma non in Adobe Commerce.
* **MDVA-32449** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con estensione B2B*) - Corregge il problema relativo al caricamento molto lento della cronologia degli ordini o al mancato caricamento.
* **MDVA-32739** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui l&#39;attivazione delle notifiche e-mail asincrone invia le e-mail di vendita precedenti.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*per Adobe Systems Commerce 2.3.6, 2.4.1*) - Risolve il problema per cui il *Crea un account* pulsante rimane disabilitato dopo aver *corretto non valido dati nel modulo Crea Nuovo Account* cliente.
* **MDVA-31006** (*per Adobe Systems Commerce 2.3.0, 2.3.1*) - Risolve il problema per cui vengono visualizzati ordini duplicati dopo aver effettuato un ordine tramite [!DNL Paypal Express] pagamento.
* **MDVA-25602** (*per Adobe Systems Commerce 2.3.0*) - Risolve il problema con il metodo di pagamento e il [!DNL PayPal Payflow Pro] trattamento dei cookie come `SameSite=Lax` per impostazione predefinita nella reindirizzare di risposta dell&#39;browser e dell&#39;API di Effetto cromatura alla pagina login del cliente.

## v1.0.10 {#v1-0-10}

Correzioni minori per le versioni delle patch

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui la regola prezzo carrello con coupon non viene applicata tramite GraphQL quando viene utilizzata l&#39;azione *Sconto importo fisso per intero carrello*.
* **MDVA-30889** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che si verifica in seguito alla fatturazione di un bundle con prodotti virtuali e semplici come opzioni.
* **MDVA-31791** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*) - Migliora le prestazioni della pagina di prodotto nei casi in cui vengono utilizzati regole di destinazione o prodotti collegati.
* **MDVA-31168** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui il file CSV di esportazione del prodotto non viene visualizzato e si verifica un errore di allocazione della memoria.
* **MDVA-32313** (*per Adobe Systems Commerce >=2.3.0 &lt;2.3.4*) - Risolve il problema per cui i prodotti configurabili potevano essere aggiunti alla lista dei desideri con le opzioni di configurazione errate.
* **MDVA-31759** (*per Adobe Systems Commerce >=2.3.0*&lt;2.4.2 ) - Risolve il problema per cui i prodotti non vengono aggiornati con *i valori degli* attributi a discesa e *textarea* durante l&#39;importazione CSV.
* **MDVA-32012** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui i codici postali in Corea e Argentina non possono essere convalidati.
* **MDVA-31640** (*per Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Corregge il problema per cui non è possibile aggiornare un prezzo speciale tramite API REST.
* **MDVA-28651** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 con estensione B2B*) - Corregge il problema relativo alle prestazioni in caso di problemi nel caricamento di preventivi negoziabili tramite API REST.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.1 with B2B extension*) - Risolve il problema per cui viene visualizzato un segno di valuta errato nella griglia del promemoria di credito.
* **MDVA-31295** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui i punti premio non vengono calcolati quando un ordine parziale viene completato e gli articoli vengono tassati.
* **MDVA-30112 (per Adobe Systems Commerce >=2.3.4 *&lt;2.4.2 ) - Risolve il problema per cui, se il numero di ordini supera il*valore della dimensione *del gruppo, Adobe Systems Commerce considera gli ordini con*stato in sospeso *come incoerenze.***
* **MDVA-31150** (*per Adobe Systems Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema per cui i saldi store di credito e di scheda regalo non vengono restituiti dalla chiamata API Rest di GET Invoice, quando la fattura è stata registrata tramite chiamata API Rest e l&#39;ordine è stato parzialmente pagato da store account di credito e scheda regalo.
* **MDVA-30963** (*per Adobe Commerce >=2.3.2 &lt;2.4.2*) - Corregge il problema per cui i risultati del filtro dei prodotti impostati per contenere solo i valori specificati per l&#39;ambito *Tutte le visualizzazioni dello store* nell&#39;ambito Amministratore, includi i prodotti con valori sostituiti a livello di visualizzazione dello store.
* **MDVA-29954** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con estensione B2B*): è stato risolto il problema che causava l&#39;invio di *New Company Registration Request* e *You&#39;ve been linked to a company* email da un indirizzo errato.
* **MDVA-28357** (*per Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Sostituisce l&#39;analizzatore standard con un analizzatore personalizzato con un tokenizzatore di parole chiave per il campo SKU nell&#39;indice [!DNL ElasticSearch] per far funzionare le query di ricerca con caratteri jolly con SKU contenenti un trattino (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema per cui lo stato dell&#39;ordine personalizzato è stato modificato in *Elaborazione* dopo la creazione parziale della spedizione tramite WebApi.
* **MDVA-30428** (*per Adobe Commerce >=2.3.4 &lt;2.3.5*) - Corregge il problema che impedisce ai clienti di aggiungere un prodotto alla lista dei desideri se il prodotto è assegnato a un&#39;origine inventario personalizzata.
* **MDVA-30594** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema che impediva il salvataggio di un ordine con più indirizzi durante l&#39;estrazione durante la configurazione di FPT.
* **MDVA-29148** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Risolve il problema durante la creazione di un prodotto tramite una chiamata API. L&#39;attributo personalizzato del prodotto di tipo `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (come Multiselect) non utilizza il valore predefinito se nel payload non è stato fornito alcun valore.
* **MDVA-30837** (*per Adobe Commerce >=2.3.1 &lt;2.3.5*) - Aggiunta di un&#39;impostazione di configurazione *Includi imposta nell&#39;importo: Sì/No* nella configurazione del metodo di spedizione gratuita. Quando *Includi imposta in importo* è impostato su *Sì*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale + Imposta. Quando *Includi imposta in importo* è impostato su *No*, l&#39;importo minimo dell&#39;ordine viene calcolato come Subtotale
* **MDVA-25028** (*per Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Corregge il problema quando gli ordini effettuati utilizzando [!DNL PayPal Payflow Pro] non sono impostati sullo stato Sospetto di frode quando vengono attivati i filtri antifrode.
* **MDVA-31224** (*per Adobe Commerce >=2.3.3 &lt;2.3.5*) - Migliora le prestazioni dell&#39;operazione di reindicizzazione `catalog_product_price` per i prodotti bundle.
* **MDVA-31321** (*per Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corregge una pagina vuota (errore) quando si seleziona *Mostra tutto*. [!DNL Elasticsearch] restituisce un elenco esteso di ID prodotto. In questo scenario la clausola order by viene convertita in un formato SQL non corretto.
* **MDVA-30815** (*per Adobe Systems Commerce >=2.3.2 &lt;2.3.4*) - Risolve il problema per cui, quando si modifica il numero di risultati ricerca devono essere visualizzati nella pagina dei risultati ricerca, Adobe Systems Commerce visualizza una pagina vuota. [!DNL Elasticsearch] Ora visualizza correttamente i risultati dalle pagine di categoria quando si modifica il numero di ricerca risultati visualizzati per pagina.
* **MDVA-30782** (*per Adobe Systems Commerce >=2.3.5 &lt;2.4.2*) - Risolve il problema per cui il blocco dinamico viene visualizzato indipendentemente dal regola del carrello.
* **MDVA-31021 (per Adobe Systems Commerce >=2.3.0 &lt;2.4.2 *) - Risolve il problema in cui si verificano problemi di prestazioni in `module-catalog-import-export/Model/Import/Product/Option.php`.*** Se la tabella contiene più di ~100.000 record `catalog_product_option` , la convalida di un nuovo CSV con un singolo prodotto richiede meno di 10 secondi.
* **MDVA-31007** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema per cui gli attributi dell&#39;indirizzo personalizzato non vengono visualizzati correttamente nella pagina Dettagli ordine nell&#39;area La mia account e nel back-end.
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
* **MDVA-28202** (*for Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Fixes the issue where Layered Navigation doesn&#39;t filter configurable products correctly when MSI is used.
* **MDVA-28300** (*for Adobe Commerce >=2.3.0 &lt;2.3.6*) - Fixes the issue where GQL request doesn&#39;t reflect the price changes from catalog price rules.
* **MDVA-31006** (*per Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Corregge il problema relativo alla visualizzazione di ordini duplicati dopo l&#39;invio di un ordine tramite il pagamento [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - È stato risolto il problema relativo alla navigazione a livelli, in cui il valore *No* per gli attributi del prodotto di tipo booleano non veniva incluso nella navigazione a livelli se [!DNL Elasticsearch] veniva utilizzato come motore di ricerca.
* **MDVA-28191** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema relativo all&#39;assenza di metodi di pagamento caricati durante la creazione dell&#39;ordine tramite l&#39;amministratore.
* **MDVA-29959** (*per Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 con estensione B2B*) - Corregge il problema per cui l&#39;utente amministratore con restrizioni con autorizzazioni *Aziende* non è autorizzato a eliminare l&#39;account aziendale.
* **MDVA-30265** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*): è stato risolto il problema che causava l&#39;interruzione del funzionamento del collegamento di verifica della spedizione dopo la creazione della fattura.
* **MDVA-28409** (*per Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - È stato risolto il problema che causava l&#39;errore *memoria insufficiente* del processo cron `sales_clean_quotes` quando il numero di virgolette scadute nel database era molto elevato.
* **MDVA-30593** (*per Adobe Commerce >=2.3.0 &lt;2.3.4*) - Corregge il problema che impedisce la pulizia delle virgolette scadute in base all&#39;impostazione della durata delle virgolette.
* **MDVA-30107** (*per Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corregge il problema relativo al funzionamento imprevisto del commutatore dell&#39;archivio se vengono utilizzati URL di base diversi per le visualizzazioni dell&#39;archivio.
* **MDVA-28763** (*per Adobe Commerce >=2.3.2 &lt;2.3.4*) - Corregge il problema di duplicazione dell&#39;immagine del prodotto dopo l&#39;aggiornamento delle informazioni sul prodotto tramite l&#39;API REST più di una volta.
* **MDVA-30284** (*per Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corregge il problema relativo a un errore dell&#39;indicizzatore Catalog Search a causa del seguente errore *[!DNL Elasticsearch]: limite dei campi totali nell&#39;indice superato.*
* **MDVA-29042** (*for Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 with B2B extension*) - Fixes the issue where Catalog permissions were changed to *Allow* automatically after new product was added to the shared catalog.
* **MDVA-30428** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where customers cannot add a product to wishlist if this product is assigned to a custom inventory source.
* **MDVA-28661** (*for Adobe Commerce >=2.3.0 &lt;2.4.2 with B2B extension*) - Fixes the issue where an error is thrown in the Company Users company account section after company admin is changed.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*per Adobe Commerce 2.3.1 - 2.3.4-p2*) - Corregge il problema che causa l&#39;errore dei processi cron se il nome del database è troppo lungo, con conseguente mancato aggiornamento delle categorie sul front-end.
* **MDVA-30106** (*for Adobe Commerce ^2.3.0*) - Fixes an issue where during checkout payments are not loaded with *Cannot read property &#39;length&#39; of null* error in JS console.
* **MDVA-28656 (per Adobe Systems Commerce >=2.3.1 &lt;2.3.6 ||=&quot;&quot;>=2.4.0 &lt;2.4.2 *) - Risolve il problema per cui se un ordine è stato effettuato senza informazioni di pagamento richieste (ad esempio, con uno sconto del 100%) ed è stata creata una fattura per l&#39;ordine, lo stato dell&#39;ordine cambia in*Chiuso *anziché Tutte le applicazioni.&lt;/2.3.6>***
* **MDVA-30209** (*per Adobe Systems Commerce 2.3.0 - 2.3.3-p1*) - Risolve il problema per cui il gruppo di clienti veniva modificato in predefinito se il cliente aggiornava le informazioni account.
* **MDVA-30123** (*per Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corregge il problema di traduzione errata delle etichette di opzione degli attributi per le query GraphQL.
* **MDVA-29996** (*per Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corregge il problema per cui dopo l&#39;abilitazione dell&#39;autorizzazione per la categoria, la pagina della categoria non viene memorizzata nella cache dalla cache a pagina intera.
* **MDVA-30164** (*per Adobe Commerce >=2.3.1 &lt;2.4.2*) - Corregge il problema per cui i record dei clienti non possono essere esportati dalla griglia Clienti se sono presenti attributi cliente personalizzati.
* **MDVA-30444** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema per cui non viene inviata alcuna e-mail di conferma per gli ordini effettuati tramite GraphQL.
* **MDVA-30490** (*per Adobe Commerce 2.3.4 - 2.3.5-p2*) - Corregge il problema per cui il confronto dei prodotti genera la pagina di errore 500 se uno dei prodotti presenta una descrizione breve vuota.
* **MDVA-30232** (*per Adobe Commerce >=2.3.1 &lt;2.4.1*) - Risolve il problema che impediva il riordino se l&#39;ordine originale conteneva una gift card.
* **MDVA-29965** (*per Adobe Systems Commerce >=2.3.3 &lt;2.4.0*) ) - Risolve il problema per cui i clienti ricevono un errore Chiave modulo non valida quando aggiungono un prodotto al carrello.
* **MDVA-30008** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the B2B issue where it is not possible to place orders through Admin API for a product which is in a public catalog.
* **MDVA-22469** (*for Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Fixes the issue where after upgrading to Adobe Commerce 2.3.3, Page Builder is not working in the Admin panel and some JS and CSS files are not loading.
* **MC-35984** (*for Adobe Commerce >=2.4.0 &lt;2.4.1*) - Fixes the issue where merchants could not interact with any page elements on the Returns page after creating a shipping label for a Return Merchandise Authorization (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*per Adobe Commerce 2.3.0 - 2.3.4*) - Corregge il problema relativo al metodo di pagamento [!DNL PayPal Payflow Pro] e considera i cookie come `SameSite=Lax` per impostazione predefinita nel browser Chrome 80 e la risposta API viene reindirizzata alla pagina di accesso del cliente.
* **MDVA-26694** (*per Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Corregge il problema relativo alla scadenza giornaliera delle cache di prodotti e cataloghi, anche se con una pianificazione diversa.
* **MDVA-27825** (*per Adobe Commerce >=2.3.0 &lt;2.4.1*) - Corregge il problema che impediva l&#39;esportazione di grandi quantità di dati a causa di perdite di memoria.
* **MDVA-29085** (*per Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Corregge il problema B2B che non richiede l&#39;invio di e-mail nuove società se queste vengono create tramite API.
* **MDVA-29344** (*per Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Corregge il problema di blocco di Page Builder dopo la copia di testo da un elemento intestazione a un elemento testo.
* **MDVA-29835** (*per Adobe Systems Commerce >2.3.1 &lt;2.4.2*) - Risolve il problema per cui gli ordini di scheda regalo contenevano due codici invece di uno.
* **MDVA-30052** (*per Adobe Systems Commerce >=2.3.2-p2 &lt;2.3.5*) - Risolve il problema con contenuto privati (archiviazione locale) che non venivano compilati correttamente, causando problemi di prestazioni.
* **MDVA-30131** (*per Adobe Systems Commerce >=2.3.4*&lt;2.3.6 || 2.4.0 ) - Risolve il problema con le navigazione a più livelli, in cui il *valore Nessun* valore per gli attributi di prodotto di tipo booleano non veniva incluso nel navigazione a più livelli se [!DNL Elasticsearch] utilizzato come motore ricerca.
* **MDVA-35514** (*per Adobe Systems Commerce >=2.4.0 &lt;2.4.1*) - Risolve il problema relativo alla creazione di un&#39;etichetta di spedizione e all&#39;aggiunta dei prodotti ordinati a un pacco nella finestra modale Crea Pacchetti.

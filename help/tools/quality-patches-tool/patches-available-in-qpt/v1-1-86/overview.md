---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.86.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 86872648c372158143f5bbe707ba7a3f15552bc3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.86

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.86.

QPT v1.1.86 include le seguenti patch:


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**: è stato risolto il problema per cui l&#39;aggiornamento della pagina durante la creazione di un ordine nell&#39;amministratore aggiunge più volte lo stesso SKU.
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**: è stato risolto il problema che causava la mancata risposta del browser se si visualizzava o si modificava **[!UICONTROL Category Permissions]** per una categoria con molte autorizzazioni.
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**: è stato risolto il problema che impediva la visualizzazione o il salvataggio di un RMA nell&#39;amministratore per visualizzare il numero RMA nel report **[!UICONTROL Action Logs]**.
1. **ACP2E-5057**: è stato corretto il problema per cui [!DNL GraphQL] query per i prodotti bundle restituiscono i prezzi delle opzioni del bundle globali anziché i prezzi specifici del sito Web quando **[!UICONTROL Catalog Price Scope]** è impostato su **[!UICONTROL Website]**.
1. **[ACP2E-5061](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5061.md)**: è stato risolto il problema che impediva a una regola di merchandising di categoria di combinare le condizioni AND con una condizione che corrispondesse a uno qualsiasi dei diversi valori.
1. **ACP2E-5071**: è stato risolto il problema che impediva la visualizzazione del messaggio di disponibilità delle scorte nella pagina del prodotto quando il carrello contiene già la quantità totale disponibile.
1. **ACP2E-5094**: è stato risolto il problema che rallenta notevolmente il caricamento delle pagine quando viene impostata una variabile di ambiente `MAGENTO_DC_*`.
1. **ACP2E-5118**: è stato risolto il problema che impediva il rendering dell&#39;anteprima di [!DNL Page Builder] quando la cache di **[!UICONTROL Translations]** era disabilitata.
1. **ACP2E-5134**: è stato risolto il problema che causava la rimozione del prodotto componente di un bundle da [!UICONTROL Shared Catalog] di un&#39;azienda e l&#39;uscita del prodotto dal carrello, causando un errore nel carrello e durante il pagamento.
1. **ACP2E-5146**: è stato risolto il problema per cui un utente amministratore limitato a siti Web specifici non può eliminare clienti quando un cliente su un altro sito Web ha lo stesso ID dell&#39;utente amministratore.
1. **ACP2E-5176**: è stato risolto il problema per cui gli eventi di e-commerce inviati a [!DNL Google Analytics 4] tramite [!DNL Google Tag Manager] utilizzano il formato [!DNL Universal Analytics] e omettono diversi eventi di estrazione.
1. **ACP2E-5185**: è stato risolto il problema che causava la visualizzazione dell&#39;errore `There was a category move error` durante lo spostamento di una categoria nell&#39;albero delle categorie oppure il completamento dell&#39;operazione richiedeva diversi minuti quando l&#39;archivio aveva molti URL riscritti.
1. **ACP2E-4191**: è stato risolto il problema relativo a determinate richieste REST API che immettono un ciclo infinito quando la cache **[!UICONTROL EAV types and attributes]** è disabilitata.
1. **ACP2E-4973**: è stato risolto il problema che impediva la cancellazione dell&#39;indirizzo dell&#39;archivio associato dal carrello passando da **[!UICONTROL In-Store Delivery]** a un altro metodo di consegna.
1. **ACP2E-5221**: è stato risolto il problema per cui l&#39;indicizzatore **[!UICONTROL Catalog Product Permissions]** richiede molto più tempo se **[!UICONTROL Quick Order]** è abilitato in installazioni con molti store e gruppi di clienti.
1. **ACP2E-5245**: è stato risolto il problema che si verificava quando un cliente appena registrato che utilizzava lo stesso indirizzo per la spedizione e la fatturazione al primo ordine visualizzava l&#39;indirizzo elencato due volte durante il successivo pagamento.
1. **ACP2E-5248**: è stato risolto il problema per cui gli utenti amministratori senza l&#39;autorizzazione **[!UICONTROL Edit Product Status]** visualizzano l&#39;errore di deprecazione `null as array offset` all&#39;apertura della pagina **[!UICONTROL Add Product]** il [!DNL PHP] 8.5.
1. **ACP2E-5254**: è stato risolto il problema che impediva la visualizzazione dei prodotti aggiunti a un elenco di richieste di acquisto quando un cliente apre l&#39;elenco fino a quando la cache non viene cancellata.
1. **ACP2E-5268**: è stato risolto il problema che impediva la creazione di un prodotto configurabile se **[!UICONTROL Enable Frontend Resize]** è impostato su **[!UICONTROL No]**.
1. **ACP2E-3752**: è stato corretto il problema a causa del quale l&#39;elaborazione dell&#39;importazione dei prodotti generava l&#39;errore `Undefined array key "apply_to"` quando venivano create molte operazioni di importazione dei prodotti.
1. **ACP2E-5280**: è stato risolto il problema che si verificava se i clienti riscontravano un errore durante l&#39;accesso mentre **[!UICONTROL Category Permissions]** era abilitato.
1. **ACP2E-5295**: è stato risolto il problema che impediva la reindicizzazione del prezzo del prodotto parallelo con l&#39;errore `Fail in child process` quando viene eseguito dopo l&#39;indicizzatore **[!UICONTROL Inventory]** nello stesso processo.
1. **ACP2E-5298**: è stato risolto il problema che consentiva agli utenti amministratori con accesso in sola visualizzazione alle regole di prezzo del carrello di generare o eliminare codici coupon.
1. **ACP2E-5333**: è stato risolto il problema che impediva l&#39;aggiornamento di un segmento del cliente con una condizione **[!UICONTROL Total Number of Orders]** che utilizza l&#39;operatore **[!UICONTROL is not]** e un valore di uno o più errori con errore `Unknown operator specified`.
1. **ACP2E-5425**: è stato risolto il problema che causava la ricezione di e-mail di conferma dell&#39;ordine duplicate da parte dei clienti per lo stesso ordine.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

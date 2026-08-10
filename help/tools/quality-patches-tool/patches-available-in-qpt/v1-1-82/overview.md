---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.82'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.82.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 9d633a740669926896517108dad44f48a6c4e503
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.82

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.82.

QPT v1.1.82 include le seguenti patch:

1. **ACP2E-4815**: sono stati risolti diversi problemi di GraphQL che causavano eccezioni PHP nei registri, la corretta associazione degli ordini agli account cliente creati dopo l&#39;ordine tramite GraphQL e l&#39;allineamento delle risposte alle specifiche GraphQL su HTTP.
1. **ACP2E-4194**: è stato corretto il problema a causa del quale le risposte GraphQL restituivano codici di stato HTTP non corretti per richieste non valide, non autorizzate o non corrette.
1. **[ACP2E-4682](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682.md)**: è stato risolto il problema che si verificava quando, visitando una pagina Storefront in cui viene verificato lo stato di attivazione dell&#39;offerta, venivano creati record di offerta vuoti a ogni caricamento della pagina.
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)**: è stato risolto il problema che impediva a un utente amministratore di utilizzare **[!UICONTROL Add Products By SKU]** nell&#39;amministratore per aggiungere prodotti dal catalogo predefinito a un ordine per una società assegnata a un gruppo di clienti non collegato a un catalogo condiviso.
1. **[ACP2E-4593](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593.md)**: è stato risolto il problema che impediva la corretta visualizzazione della pagina CMS per le restrizioni dei siti Web nei siti Web secondari nelle distribuzioni multisito.
1. **ACP2E-4695**: è stato risolto il problema che impediva il completamento dell&#39;indicizzatore della regola del catalogo e utilizzava una quantità eccessiva di memoria, causando instabilità ed errori di memoria insufficiente.
1. **ACP2E-4698**: è stato risolto il problema per cui la modifica di un&#39;immagine di nuovo nel contenuto di testo di Page Builder consente di salvare un URL multimediale assoluto anziché conservare una direttiva multimediale portatile.
1. **[ACP2E-4797](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797.md)**: è stato risolto il problema che impediva il corretto blocco dell&#39;immissione di caratteri Unicode a 4 byte nell&#39;editor di WYSIWYG o del contenuto di Page Builder nell&#39;amministratore anche quando il database è configurato per supportare utf8mb4.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**: è stato risolto il problema relativo alla scadenza lenta dei punti premio nei negozi con una cronologia dei punti premio di grandi dimensioni, causando ritardi nella scadenza dei punti premio.
1. **[ACP2E-4799](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799.md)**: è stato risolto il problema per cui la query `requisition_lists GraphQL` restituisce un valore `total_count` che riflette solo il numero di elementi nella pagina corrente invece del numero totale di elenchi di richieste di acquisto che corrispondono ai criteri della query.
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**: è stato risolto il problema che rallenta notevolmente le richieste API di pagamento per i prodotti configurabili con molti prodotti secondari quando il primo prodotto secondario vendibile viene visualizzato in ritardo nell&#39;elenco.
1. **ACP2E-4840**: è stato corretto il problema a causa del quale il valore di quantità richiesto nella query GraphQL `products` restituisce *null*.
1. **ACP2E-4870**: è stato risolto il problema per cui **[!UICONTROL Product Alerts]** notifiche e-mail ignorano le impostazioni e-mail della visualizzazione archivio.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**: è stato risolto il problema che causava la disconnessione imprevista degli utenti Admin durante la visualizzazione di account cliente con rubriche di grandi dimensioni nell&#39;amministratore.
1. **ACP2E-4894**: è stato risolto il problema che causava il ritardo nella visualizzazione dei nuovi ordini nelle griglie di gestione degli ordini di amministrazione quando **[!UICONTROL Asynchronous Indexing]** era abilitato negli archivi di grandi volumi.
1. **ACP2E-4981**: è stato risolto il problema per cui i caroselli di prodotti Page Builder visualizzano i prodotti in un ordine che non riflette la posizione impostata nell&#39;amministratore e includono prodotti configurabili quando i prodotti secondari corrispondenti sono visibili singolarmente.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

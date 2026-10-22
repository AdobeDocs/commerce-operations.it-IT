---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.84.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: ea739d12f02672cf585925b90860bca3b44de02a
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.84

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.84.

QPT v1.1.84 include le seguenti patch:

1. **[ACP2E-5005](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5005.md)**: è stato risolto il problema che si verificava se la quantità di un&#39;opzione di prodotto bundle in un preventivo negoziabile tornava al valore precedente quando il prodotto bundle veniva riconfigurato in Amministrazione e la quantità veniva modificata.
1. **[ACP2E-4913](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4913.md)**: è stato risolto il problema che causava errori permanenti nella spedizione e nella creazione della fattura REST API dopo un deadlock del database.
1. **ACP2E-5009**: è stato risolto il problema che impediva la corretta migrazione dei dati da Magento Open Source ad Adobe Commerce delle modifiche di progettazione pianificate per la categoria e degli aggiornamenti pianificati per il prodotto **[!UICONTROL Special Price]**. Alcuni aggiornamenti pianificati risultavano mancanti o ignorati durante la migrazione e ne migliorava le prestazioni.
1. **[ACP2E-5017](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5017.md)**: è stato risolto il problema che si verificava se l&#39;esecuzione di una query sul cliente `role` tramite GraphQL restituiva *Errore interno del server* quando il cliente non era assegnato a una società.
1. **ACP2E-5027**: è stato risolto il problema che causava il blocco degli indicizzatori in un loop e il mancato completamento della reindicizzazione quando il blocco dei file era abilitato.
1. **ACP2E-5029**: è stato risolto il problema per cui le modifiche alle regole dei prezzi di catalogo non vengono visualizzate in **[!DNL Live Search]** finché non viene eseguita una risincronizzazione manuale.
1. **ACP2E-5041**: è stato risolto il problema che causava la visualizzazione del prezzo regolare da parte della vetrina al posto di **[!UICONTROL Special Price]** al termine dell&#39;aggiornamento in seguito al salvataggio di un prodotto durante un aggiornamento pianificato.
1. **[ACP2E-5059](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5059.md)**: è stato risolto il problema che causava la ricezione di e-mail di conferma dell&#39;ordine duplicate da parte dei clienti per lo stesso ordine.
1. **[ACP2E-5122](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5122.md)**: è stato risolto il problema che causava la registrazione errata degli errori gestiti dalle richieste GraphQL per il carrello come errori dell&#39;applicazione nei registri eccezioni.
1. **[ACP2E-5143](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5143.md)**: è stato risolto il problema che determinava il rendering del contenuto completo della pagina CMS da parte della query GraphQL `route` quando veniva richiesto solo il routing dei metadati, aumentando il numero di query di database per le pagine CMS che contengono widget di Page Builder.
1. **ACP2E-5183**: è stato risolto il problema che impediva la distribuzione di contenuto statico in PHP 8.5 durante la compilazione di un file `LESS` che utilizza la direttiva `@magento_import`.
1. **ACP2E-5242**: è stato risolto il problema che impediva la ricerca della disponibilità del prodotto durante l&#39;aggiunta di elementi al carrello.
1. **ACP2E-5263**: è stato risolto il problema che consentiva di interrompere l&#39;esportazione dei prodotti in un file CSV prima dell&#39;inclusione di tutti i prodotti, creando un file incompleto.
1. **ACP2E-5034**: è stato risolto il problema che causava il ripristino errato dei totali in *zero* durante il ricalcolo di un preventivo dopo aver selezionato un metodo di spedizione, lo scarto degli aggiornamenti alle quantità di opzioni prodotto nel bundle effettuati tramite l&#39;azione **[!UICONTROL Configure]** in Amministrazione e non rifletteva correttamente gli sconti a livello di articolo applicati ai prodotti del bundle prezzi dinamici nei subtotali del preventivo.
1. **[ACP2E-4741](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4741.md)**: è stato risolto il problema che causava la scomparsa di un prodotto dal Negozio dopo il salvataggio di un prodotto collegato come Prodotto correlato, Vendita al rialzo o Vendita incrociata mentre erano in uso un magazzino e un&#39;origine non predefiniti.
1. **[ACP2E-5127](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5127.md)**: è stato risolto il problema che causava la reimpostazione di **[!UICONTROL Credit Limit]** in `0` dell&#39;account di una società in Admin con impostazioni locali non predefinite.
1. **[ACP2E-5079](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5079.md)**: risolve il problema per cui un segmento di clienti assegnato a più siti Web restituisce clienti corrispondenti solo dal primo sito Web quando gli account dei clienti sono condivisi a livello globale.
1. **AC-15494**: è stato corretto il problema per cui la query prodotti restituisce nomi di prodotti con caratteri speciali con escape di HTML invece dei caratteri originali.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

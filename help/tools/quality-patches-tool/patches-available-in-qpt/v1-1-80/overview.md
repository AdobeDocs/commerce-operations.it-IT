---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.80'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.80.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: f8a08611109d9c8e5e686e0c451b0a58ecc12e21
workflow-type: tm+mt
source-wordcount: 596
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.80

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.80.

QPT v1.1.80 include le seguenti patch:

1. **ACP2E-4239**: è stato corretto il problema a causa del quale i filtri della griglia di amministrazione che utilizzano gli attributi di data restituiscono risultati non corretti a causa di differenze di fuso orario tra la data selezionata, i valori UTC archiviati e il fuso orario dell&#39;archivio configurato.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: è stato risolto il problema relativo alla creazione di un record di virgolette null nella tabella del database `quote` durante il flusso **[!UICONTROL Login as Customer]**.
1. **ACP2E-4481**: è stato risolto il problema che impediva il ricalcolo corretto della vendibilità del prodotto bundle dopo l&#39;annullamento di un ordine.
1. **[ACP2E-4488](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488.md)**: è stato risolto il problema che rallenta il salvataggio o la modifica dei prodotti in Admin per i prodotti con set di attributi di grandi dimensioni.
1. **ACP2E-4493**: è stato risolto il problema che causava la visualizzazione di uno stato dell&#39;ordine errato nella griglia di Archivio ordini di vendita quando l&#39;indicizzazione asincrona era abilitata.
1. **ACP2E-4496**: è stato risolto il problema che causava il deterioramento delle prestazioni durante l&#39;esecuzione del processo cron di Analytics, con conseguente miglioramento delle prestazioni complessive del sistema.
1. **ACP2E-4533**: è stato risolto il problema che impediva il caricamento delle immagini segnaposto in Storefront quando nell&#39;URL è incluso un codice store.
1. **ACP2E-4552**: è stato risolto il problema che impediva la restituzione dello stato della società nella risposta di GraphQL.
1. **[ACP2E-4610](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610.md)**: è stato risolto il problema relativo ai problemi di prestazioni del processo cron `sales_clean_quotes`.
1. **[ACP2E-4552](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552.md)**: è stato risolto il problema che impediva la restituzione dello stato della società nella risposta di GraphQL.
1. **[ACP2E-4496](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496.md)**: è stato risolto il problema che causava il deterioramento delle prestazioni durante l&#39;esecuzione del processo cron di Analytics, con conseguente miglioramento delle prestazioni complessive del sistema.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: è stato risolto il problema che impediva il caricamento delle immagini segnaposto nella vetrina quando nell&#39;URL è incluso un codice store.
1. **ACP2E-4610**: è stato risolto il problema relativo ai problemi di prestazioni del processo cron `sales_clean_quotes`.
1. **[ACP2E-4615](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615.md)**: è stato risolto il problema che impediva il rimborso degli ordini online con un errore PayPal che indicava *Il gateway PayPal rifiuta la richiesta. Errore interno.*.
1. **[ACP2E-4626](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626.md)**: è stato risolto il problema che causava la richiesta e l&#39;esecuzione di alcuni file JavaScript di Storefront due volte, causando caricamenti duplicati intermittenti e un comportamento instabile.
1. **ACP2E-4653**: è stato risolto il problema che impediva l&#39;esposizione dell&#39;ambito dell&#39;attributo condizione **[!UICONTROL Cart Price Rule]** per **[!UICONTROL Category (Parent Only)]** e **[!UICONTROL Category (Children Only)]** durante il recupero o l&#39;aggiornamento delle regole tramite l&#39;API REST.
1. **ACP2E-4808**: è stato risolto il problema che causava la visualizzazione di un solo valore numerico non elaborato nella sezione **[!UICONTROL Additional Information]** o **[!UICONTROL More Information]** senza l&#39;unità di misura configurata (libbre o kg) da parte dell&#39;attributo Weight della pagina di prodotto della vetrina.
1. **[ACP2E-4813](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813.md)**: è stato risolto il problema relativo alla mancata disponibilità dei metodi di spedizione USPS al momento del pagamento e all&#39;errata stima della spedizione per alcuni prodotti, inclusi gli ordini suddivisi in più pacchetti.
1. **ACP2E-4626**: è stato risolto il problema che causava la richiesta e l&#39;esecuzione di alcuni file JavaScript di Storefront due volte, causando caricamenti duplicati intermittenti e un comportamento instabile.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: è stato risolto il problema che impediva l&#39;esposizione dell&#39;ambito dell&#39;attributo condizione prezzo carrello per **[!UICONTROL Category (Parent Only)]** e **[!UICONTROL Category (Children Only)]** durante il recupero o l&#39;aggiornamento delle regole tramite l&#39;API [!DNL REST].
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: è stato risolto il problema che causava la visualizzazione di un solo valore numerico non elaborato nella sezione **[!UICONTROL Additional Information]** o **[!UICONTROL More Information]** senza l&#39;unità di misura configurata (libbre o kg) da parte dell&#39;attributo Weight della pagina di prodotto della vetrina.
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: è stato risolto il problema per cui la convalida degli indirizzi di spedizione nell&#39;API [!DNL REST] non è conforme alla configurazione degli attributi definita in Admin.
1. **ACP2E-4813**: è stato risolto il problema relativo alla mancata disponibilità dei metodi di spedizione USPS al momento del pagamento e all&#39;errata stima della spedizione per alcuni prodotti, inclusi gli ordini suddivisi in più pacchetti.
1. **[ACSD-53502](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502.md)**: è stato risolto il problema che causava errori intermittenti di **[!UICONTROL Add to Cart]** nella vetrina di iOS [!DNL Safari] a causa di chiamate ricorsive allo script di monitoraggio di New Relic, con conseguente ricaricamento delle pagine.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

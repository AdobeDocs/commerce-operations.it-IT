---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a1cc81ee1a8d0bbcbea322558da75a31e65d66a4
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%
---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.85

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.85.

QPT v1.1.85 include le seguenti patch:

1. **[ACP2E-4929](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-4929.md)**: è stato risolto il problema per cui le etichette degli attributi nella pagina Confronta prodotti visualizzano le traduzioni da una visualizzazione diversa dello store anziché dalla visualizzazione dello store corrente.
1. **ACP2E-5075**: è stato risolto il problema che causava l&#39;applicazione errata di uno sconto a tutti gli elementi figlio di un prodotto bundle a prezzo dinamico quando la regola corrispondeva solo al prodotto padre del bundle da parte di una regola a prezzo fisso del carrello con una condizione di categoria.
1. **ACP2E-5077**: è stato risolto il problema che causava la creazione di carrelli attivi duplicati da parte di `customerCart` query GraphQL simultanee o `POST /V1/carts/mine` richieste REST per clienti che non avevano già un carrello attivo.
1. **ACP2E-5088**: è stato risolto il problema che causava la cancellazione del carrello permanente di un cliente alla scadenza della sessione.
1. **[ACP2E-3991](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-3991.md)**: è stato risolto il problema che impediva la corretta determinazione dell&#39;indirizzo IP del client.
1. **ACP2E-5092**: è stato risolto il problema che causava la visualizzazione di un errore nella pagina **[!UICONTROL Company Profile]** e nella pagina Modifica cliente amministratore quando un indirizzo aziendale salvato senza un&#39;area geografica veniva aggiunto al paese.
1. **ACP2E-5124**: è stato risolto il problema per cui il pulsante **[!UICONTROL Import]** rimane disponibile nei risultati di convalida dopo la convalida non riesce quando **[!UICONTROL Validation Strategy]** è impostato su **[!UICONTROL Stop on Error]**.
1. **AC-17456**: è stato corretto il problema per cui la modifica dell&#39;ambito **[!UICONTROL Global]** nella pagina **[!UICONTROL Design Configuration]** del pannello di amministrazione restituisce un errore *HTTP 500* in PHP 8.4 e 8.5.
1. **ACP2E-5212**: è stato risolto il problema per cui **[!UICONTROL Quick Order]** accetta file non CSV rinominati con un&#39;estensione `.csv`.
1. **ACP2E-5300**: è stato risolto il problema per cui le ricerche di più numeri di ordine separati da spazi o virgole nella griglia del Pannello di amministrazione **[!UICONTROL Orders]** non restituiscono ordini corrispondenti.
1. **ACP2E-5354**: è stato risolto il problema che causava la visualizzazione più volte di un cliente associato a un account società nella griglia di amministrazione **[!UICONTROL Customers]** a causa dell&#39;aggiornamento di un cliente tramite l&#39;API REST.
1. **ACP2E-5208**: è stato risolto il problema che causava il ricaricamento della sezione **[!UICONTROL Requisition List]** in ogni navigazione delle pagine Storefront, anche quando non erano state apportate modifiche.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

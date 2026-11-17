---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.85

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.85.

QPT v1.1.85 include le seguenti patch:

1. **ACP2E-4929**: è stato risolto il problema per cui le etichette degli attributi nella pagina **[!UICONTROL Compare Products]** visualizzano le traduzioni da una visualizzazione archivio diversa anziché dalla visualizzazione archivio corrente.
1. **ACP2E-5075**: è stato risolto il problema che causava l&#39;applicazione errata di uno sconto a tutti gli elementi figlio di un prodotto bundle a prezzo dinamico quando la regola corrispondeva solo al prodotto padre del bundle da parte di una regola a prezzo fisso del carrello con una condizione di categoria.
1. **ACP2E-5077**: è stato risolto il problema che causava la creazione di carrelli attivi duplicati da parte di `customerCart` query GraphQL simultanee o `POST /V1/carts/mine` richieste REST per clienti che non avevano già un carrello attivo.
1. **ACP2E-5088**: è stato risolto il problema che causava la cancellazione del carrello permanente di un cliente alla scadenza della sessione.
1. **ACP2E-3991**: è stato risolto il problema che impediva la corretta determinazione dell&#39;indirizzo IP del client.
1. **ACP2E-5092**: è stato risolto il problema che causava la visualizzazione di un errore nella pagina **[!UICONTROL Company Profile]** e nella pagina Modifica cliente amministratore quando un indirizzo aziendale salvato senza un&#39;area geografica veniva aggiunto al paese.
1. **ACP2E-5124**: è stato risolto il problema per cui il pulsante **[!UICONTROL Import]** rimane disponibile nei risultati di convalida dopo la convalida non riesce quando **[!UICONTROL Validation Strategy]** è impostato su **[!UICONTROL Stop on Error]**.
1. **AC-17456**: è stato corretto il problema per cui la modifica dell&#39;ambito **[!UICONTROL Global]** nella pagina **[!UICONTROL Design Configuration]** del pannello di amministrazione restituisce un errore *HTTP 500* in PHP 8.4 e 8.5.
1. **ACP2E-5212**: è stato risolto il problema per cui **[!UICONTROL Quick Order]** accetta file non CSV rinominati con un&#39;estensione `.csv`.
1. **ACP2E-5300**: è stato risolto il problema per cui le ricerche di più numeri di ordine separati da spazi o virgole nella griglia del Pannello di amministrazione **[!UICONTROL Orders]** non restituiscono ordini corrispondenti.
1. **ACP2E-5354**: è stato risolto il problema che causava la visualizzazione più volte di un cliente associato a un account società nella griglia di amministrazione **[!UICONTROL Customers]** a causa dell&#39;aggiornamento di un cliente tramite l&#39;API REST.
1. **ACP2E-5208**: è stato risolto il problema che causava il ricaricamento della sezione **[!UICONTROL Requisition List]** in ogni navigazione delle pagine Storefront, anche quando non erano state apportate modifiche.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

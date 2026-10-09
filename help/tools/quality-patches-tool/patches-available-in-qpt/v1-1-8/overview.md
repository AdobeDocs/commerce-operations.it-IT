---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.8'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.8.
feature: Tools and External Services
role: Admin
exl-id: bcc35189-bed7-4076-bd9e-3d4ca47b3215
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---
# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.1.8

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.8.

QPT v1.1.8 include le seguenti patch:

1. **MDVA-38393**: è stato risolto il problema che causava l&#39;interruzione del funzionamento delle regole del catalogo per un prodotto configurabile se il relativo prodotto semplice veniva rinominato.
1. **MDVA-39153**: è stato risolto il problema relativo al calcolo errato dell&#39;importo dello sconto durante il riordino in Admin.
1. **MDVA-41139**: è stato risolto il problema che causava l&#39;esaurimento delle scorte dei prodotti configurabili dopo l&#39;importazione quando per una delle origini di un prodotto semplice veniva utilizzato il valore qty=0.
1. **MDVA-41215**: è stato corretto il problema a causa del quale gli utenti ricevevano l&#39;errore 500 dopo aver impostato il cookie *mage-messages*, se esiste già, ma non sono presenti nuovi messaggi.
1. **MDVA-42326**: è stato risolto il problema che causava un errore durante l&#39;estrazione dopo un timeout della sessione anche se il carrello acquisti persistente era abilitato.
1. **MDVA-42341**: è stato risolto il problema per cui la query GraphQL `categoryList` non filtra i risultati se una richiesta ha l&#39;intestazione Store.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.39'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.39.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6116f566-2ff8-4148-ab60-cec65f9b7a6f
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.39

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.39.

QPT v1.1.39 include le seguenti patch:

1. **ACSD-53704**: risolve il problema relativo al calcolo errato della cronologia del saldo dei punti premio dopo la scadenza dei punti premio.
1. **ACSD-53583**: migliora le prestazioni di reindicizzazione parziale per *Prodotti categoria* e *Indicizzatori categorie prodotto*.
1. **ACSD-54026**: è stato corretto un messaggio di errore non corretto per una richiesta GraphQL `updateCompanyRole` per un utente non autorizzato.
1. **ACSD-54106**: è stato corretto il problema che impediva l&#39;ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi.
1. **ACSD-52219**: è stato risolto il problema che causava il mancato funzionamento previsto dei filtri salvati dalle griglie di amministrazione quando si passava spesso da una visualizzazione a un&#39;altra.
1. **ACSD-54342**: è stato corretto un messaggio di errore non corretto *Errore nella struttura dei dati: i valori sono misti* quando si importa un file CSV senza dati validi.
1. **ACSD-54660**: aggiunto un nuovo attributo di input *sort* per ordinare gli ordini cliente in GraphQL in base a `sort_field` e `sort_direction`.
1. **ACSD-54776**: è stato risolto il problema che impediva il salvataggio dei valori non selezionati *[!UICONTROL Use Default Value]* e non predefiniti dei campi prodotto per la seconda visualizzazione sito Web, archivio e archivio.
1. **ACSD-53998**: è stato risolto il problema che impediva il corretto funzionamento di **[!UICONTROL Dynamic Block]** basato su **[!UICONTROL Customer Segment]** dopo la disconnessione da un account cliente.
1. **ACSD-53204**: correzioni *Impossibile salvare il prodotto.* errore durante l&#39;esecuzione di richieste simultanee di aggiunta di immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`.
1. **ACSD-47657**: aggiunto un meccanismo di caching per le credenziali di AWS. Un provider di credenziali ora utilizza la cache di Magento per memorizzare nella cache le credenziali recuperate da AWS per la configurazione EC2.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

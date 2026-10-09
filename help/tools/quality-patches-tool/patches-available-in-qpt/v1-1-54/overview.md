---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
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
source-wordcount: '300'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.54

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 include le seguenti patch:

1. **ACSD-60267**: risolve il problema relativo alla corretta applicazione di FPT (Fixed Product Tax) quando si aggiungono prodotti semplici con FPT direttamente al carrello, ma non riesce quando si selezionano questi prodotti tramite opzioni di prodotto configurabili.
1. **ACSD-61103**: è stato corretto il problema per cui il conteggio degli errori nella tabella `customer_entity` non viene reimpostato su zero dopo che un cliente ha effettuato correttamente l&#39;accesso tramite gli endpoint API.
1. **ACSD-61134**: è stato risolto il problema relativo alla deselezione automatica del metodo di pagamento [!DNL Braintree Vault] nel flusso di lavoro di pagamento quando un acquirente aggiorna il proprio indirizzo di fatturazione deselezionando la casella di controllo *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199**: è stato risolto il problema che impediva alla scheda Gerarchia pagine di CMS di visualizzare una struttura ad albero corretta durante la modifica di una pagina di CMS con una gerarchia esistente.
1. **ACSD-61200**: è stato risolto il problema che causava discrepanze nei dati dell&#39;ordine di vendita nei calcoli per *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* nelle vendite e nei calcoli per *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]*.
1. **ACSD-61522**: è stato risolto il problema che impediva l&#39;immissione di indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* del cliente ospite e l&#39;invio di e-mail di conferma dell&#39;ordine non valide.
1. **ACSD-61756**: migliora le prestazioni di `AdvancedSalesRule` filtri.
1. **ACSD-61799**: risolve il problema che causa il calcolo errato dello sconto totale quando più regole del carrello con sconti fissi vengono applicate al preventivo.
1. **ACSD-61845**: è stato corretto l&#39;errore che si verifica quando viene inviata una richiesta con solo *testo/html* intestazione di accettazione.
1. **ACSD-62056**: è stato risolto il problema che impediva il caricamento dell&#39;immagine per un prodotto configurabile se MSI era installato.
1. **ACSD-62485**: è stato risolto il problema che causava l&#39;interruzione del funzionamento del consumer `async.operations.all` durante la creazione di un&#39;azienda.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

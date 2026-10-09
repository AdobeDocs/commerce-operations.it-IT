---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.62'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
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
source-wordcount: '238'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.62

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.62.

QPT v1.1.62 include le seguenti patch:

1. **ACSD-63406**: è stato corretto il problema per cui le virgolette persistenti scadute non vengono cancellate da alcun processo cron durante l&#39;esecuzione del processo cron `persistent_clear_expired`.
1. **ACSD-63520**: è stato corretto il problema per cui le immagini aggiunte tramite **[!UICONTROL Configurations]** nel pannello di amministrazione non rispettano il limite di dimensioni massime per il caricamento.
1. **ACSD-64523**: è stato risolto il problema che impediva la creazione di nuovi prodotti senza un nome tramite il processo di importazione (tramite Admin o API), interrompendo l&#39;interfaccia di amministrazione e causando la creazione di prodotti non validi.
1. **ACSD-64532**: è stato corretto il problema per cui una variabile ENV impostata su *false* viene trattata come stringa *false* invece di un valore booleano false.
1. **ACSD-64592**: è stato risolto il problema che causava il reindirizzamento della richiesta di risarcimento dal sito Web predefinito da parte del collegamento della richiesta di rimborso presente nell&#39;e-mail di una gift card in negozi non predefiniti.
1. **ACSD-65164**: è stato risolto il problema relativo al messaggio di errore *Alcune delle opzioni selezionate per l&#39;elemento non sono attualmente disponibili* si verifica quando si riordina un prodotto configurabile con una singola opzione selezionata per la casella di controllo personalizzata.
1. **ACSD-64732**: è stato risolto il problema che impediva la corretta memorizzazione nella cache dei controller di terze parti con i segmenti dei clienti.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

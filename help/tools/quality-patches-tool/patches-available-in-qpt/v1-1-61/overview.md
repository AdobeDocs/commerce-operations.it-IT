---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
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
source-wordcount: '339'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.61

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.61.

QPT v1.1.61 include le seguenti patch:

1. **ACP2E-3689**: sono stati risolti diversi problemi relativi alla visualizzazione dell&#39;albero delle categorie su livelli più profondi e che riflettono relazioni di ancoraggio/non di ancoraggio.
1. **ACP2E-3705**: è stato risolto un problema che impediva l&#39;esecuzione del cron `indexer_update_all_views` se `MAGE_INDEXER_THREADS_COUNT` era impostato.
1. **ACSD-63883**: è stato risolto il problema per cui [!UICONTROL Requisition List] restituisce un `items_count` non corretto nella risposta [!DNL GraphQL].
1. **ACSD-63974**: è stato risolto il problema relativo al caricamento della pagina [!UICONTROL Requisition List] troppo lungo in presenza di troppi elementi, aggiungendo una funzionalità di impaginazione alla griglia [!UICONTROL Requisition List] nella vetrina che visualizza solo porzioni di record limitate al numero di record per pagina, anziché tutti i record contemporaneamente.
1. **ACSD-64178**: è stato risolto il problema che causava il caricamento lento della pagina di modifica [!UICONTROL Attribute Set] se erano presenti migliaia di attributi di prodotto.
1. **ACSD-64209**: è stato risolto il problema che causava il recupero da parte del modulo di pianificazione cron di tutti i preventivi negoziabili senza escludere quelli con stato **[!UICONTROL ordered]**, causando l&#39;attivazione di un messaggio e-mail o di messaggi e-mail.
1. **ACSD-64431**: la mutazione `placeOrder` che contiene le informazioni sul codice coupon nella richiesta non genera più un errore interno, ma mostra che l&#39;ordine è stato effettuato correttamente.
1. **ACSD-64467**: è stato risolto il problema che causava la visualizzazione di un editor di WYSIWYG vuoto dopo il salvataggio di una descrizione di categoria nel livello di visualizzazione archivio.
1. **ACSD-64546**: è stato risolto il problema che causava la visualizzazione di un messaggio di errore generico nell&#39;interfaccia utente e l&#39;eccezione *Array to string conversion* nei registri durante la creazione delle etichette di spedizione UPS, in modo che l&#39;errore effettivo venga visualizzato nell&#39;interfaccia utente e il messaggio di errore corretto venga archiviato nei registri.
1. **ACSD-64684**: è stato risolto il problema che si verificava in caso di errore di convalida durante la modifica e il salvataggio di una gift card con valore maggiore di *999* a causa della virgola (separatore delle migliaia) nel numero *mille (1.000)*.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

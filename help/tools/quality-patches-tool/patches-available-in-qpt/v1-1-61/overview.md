---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 0800285df83eb3e3ffcfb003bf984248b750db32
workflow-type: tm+mt
source-wordcount: '336'
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

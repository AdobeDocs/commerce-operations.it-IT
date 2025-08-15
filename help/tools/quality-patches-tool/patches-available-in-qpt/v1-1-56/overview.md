---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.56

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.56.

QPT v1.1.56 include le seguenti patch:

1. JavaScript **ACSD-63244**: sono stati risolti i problemi che impediscono il corretto rendering di [!DNL Google Maps] e che impediscono il corretto rendering di *TypeError non rilevato: questo errore._each non è un errore di funzione* nella console nel pannello [!UICONTROL Admin].
1. **ACSD-63242**: risolve il problema della lentezza di importazione quando si aggiungono prodotti catalogo con più di 10.000 voci.
1. **ACSD-63062**: è stato risolto il problema che causava l&#39;applicazione di più regole di sovrapposizione quando si verificavano calcoli non corretti dello sconto sul carrello.
1. **ACSD-62979**: è stato corretto il problema per cui l&#39;utilizzo di [!UICONTROL Store ID] errato nell&#39;intestazione di GraphQL causava un errore irreversibile di memoria.
1. **ACSD-62971**: è stato risolto il problema che si verificava se l&#39;importazione di origini di magazzino con valori non numerici nella colonna *[!UICONTROL Quantity]* determinava l&#39;impostazione di *quantity* su *0*.
1. **ACSD-62872**: è stato risolto il problema di convalida dell&#39;attributo univoco in cui gli aggiornamenti della pianificazione non vengono convalidati correttamente.
1. **ACSD-62755**: è stato risolto il problema per cui [!DNL TinyMCE] 7 richiede che la dimensione e il tipo di carattere vengano aggiunti in modo specifico nelle impostazioni di inizializzazione dell&#39;editor.
1. **ACSD-62670**: è stato corretto il problema che si verificava se l&#39;esportazione del report [!UICONTROL Products Ordered] in formato CSV e XML restituiva un errore.
1. **ACSD-62577**: è stato risolto il problema relativo alle prestazioni lente delle query di ricerca storefront ottimizzando gli indici di query e di tabella.
1. **ACSD-62475**: risolve il problema relativo all&#39;unione errata dei prodotti [!UICONTROL Gift Card] nel carrello.
1. **ACSD-62428**: è stato corretto il problema per cui `is_out_of_stock` è impostato su un valore non corretto nell&#39;indice di ricerca del catalogo quando [!DNL SKU] non è impostato come attributo ricercabile.
1. **ACSD-62355**: migliora il tempo di caricamento della pagina di modifica del prodotto configurabile quando il prodotto configurabile è basato su molti attributi con molti valori.
1. **ACSD-61805**: è stato risolto il problema che causava l&#39;esaurimento delle scorte dei prodotti nella vetrina dopo l&#39;aggiornamento dello stato dell&#39;ordine inevaso tramite [!DNL REST API].
1. **ACSD-60811**: è stato corretto il problema per cui l&#39;aggiornamento dello stato dell&#39;ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è *[!UICONTROL Processing]* o *[!UICONTROL Fraud]*.
1. **ACSD-62952**: è stato risolto il problema che causava la visualizzazione non corretta della data [!UICONTROL Gift Registry] nella vetrina.
1. **ACSD-55339**: è stato risolto il problema che causava la rimozione di [!DNL SKU]0 *da parte di un prodotto* che inizia con *0* (zero), impedendo l&#39;aggiornamento del preventivo.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

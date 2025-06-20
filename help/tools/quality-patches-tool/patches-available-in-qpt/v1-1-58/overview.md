---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.58.
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.58

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.58.

QPT v1.1.58 include le seguenti patch:

1. **ACSD-48570**: è stato risolto il problema che impediva di raggiungere la pagina di reimpostazione della password facendo clic sul collegamento di reimpostazione della password [!UICONTROL Admin] quando **Aggiungi codice archivio agli URL** era *abilitato*. In precedenza veniva visualizzata la pagina di accesso o una pagina 404.
1. **ACSD-62118**: è stato risolto il problema che impediva l&#39;aggiornamento completo della tabella `sales_order_tax_item` quando [!DNL B2B] ordini vengono effettuati utilizzando il metodo Purchase Order.
1. **ACSD-63067**: è stato risolto il problema che causava l&#39;evidenziazione errata di tutte le quantità di prodotti e la visualizzazione del messaggio *[!DNL Please specify the quantity of product(s).]* per tutti i prodotti di un prodotto raggruppato quando una sola quantità non era corretta.
1. **ACSD-63090**: risolve il problema della rimozione degli articoli del carrello quando un prodotto viene eliminato, dopo essere stato aggiunto al carrello.
1. **ACSD-63182**: è stato risolto il problema che si verificava quando si salvava un prodotto bundle duplicato con **[!DNL MSI]** *enabled*.
1. **ACSD-63283**: è stato risolto il problema che causava un&#39;eccezione durante l&#39;ordinamento di elementi dal registro regali e che causava l&#39;inclusione di elementi non appartenenti al registro.
1. **ACSD-63299**: è stato risolto il problema che impediva la visualizzazione del prezzo speciale di un prodotto configurabile nella vetrina.
1. **ACSD-63325**: è stato risolto il problema che si verificava con un errore `Syntax Error: Unexpected <EOF>` durante l&#39;invio di una richiesta [!DNL GraphQL] vuota.
1. **ACSD-63329**: è stato corretto il problema per cui i valori predefiniti per gli attributi con tipi di input **[!UICONTROL Date]** o **[!UICONTROL Date and Time]** non sono impostati durante la creazione di prodotti tramite [!DNL REST API].
1. **ACSD-63572**: è stato risolto il problema che impediva la pulizia delle tabelle temporanee dell&#39;indicizzatore `CatalogRule` se il processo dell&#39;indicizzatore è terminato.
1. **ACSD-63578**: è stato corretto il problema per cui se si fa clic sul pulsante **[!UICONTROL Delete]** in **[!UICONTROL Add to Order by SKU]** in [!UICONTROL Admin], [!DNL SKU] non viene rimosso.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

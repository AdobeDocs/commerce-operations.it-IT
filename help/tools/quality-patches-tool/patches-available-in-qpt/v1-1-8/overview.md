---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.8'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.8.
feature: Tools and External Services
role: Admin
exl-id: bcc35189-bed7-4076-bd9e-3d4ca47b3215
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '192'
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

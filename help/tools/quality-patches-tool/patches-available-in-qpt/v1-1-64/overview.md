---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.64

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.64.

QPT v1.1.64 include le seguenti patch:

1. **ACP2E-3838**: è stato risolto il problema che impediva a [!DNL Page Builder] errori CORS di salvare le modifiche nel pannello di amministrazione in modalità di produzione.
1. **ACP2E-3841**: è stato risolto il problema per cui le regole del prezzo del carrello per i prodotti di spedizione multipla non vengono applicate correttamente quando vengono utilizzate `subselect` condizioni e **[!UICONTROL Free Shipping]** è abilitato.
1. **ACSD-63139**: è stato risolto il problema che impediva l&#39;esportazione del prodotto se gli attributi del prodotto contenevano migliaia di valori di opzione.
1. **ACSD-65100**: è stato risolto il problema che causava un errore durante il processo di ottimizzazione dell&#39;immagine se si rimuovevano i valori per **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** nella configurazione **[!UICONTROL Media Gallery Image Optimization]**.
1. **ACSD-65127**: è stato risolto il problema che causava la generazione di errori nella console del browser da parte di [!DNL TinyMCE] 6 in seguito all&#39;attivazione della minimizzazione di JavaScript in modalità di produzione, con conseguente impatto sulla funzionalità e sull&#39;esperienza utente.
1. **ACSD-65787**: è stato risolto il problema che causava l&#39;arresto anomalo della classe `SchemaBuilder` durante la creazione dello schema o gli aggiornamenti a causa di una chiave di matrice non definita *column* durante l&#39;elaborazione dei dati della tabella.
1. **ACSD-65223**: risolve il problema che causava la visualizzazione di un errore nei termini e nei contratti selezionati manualmente per [!DNL B2B] ordini fornitore.
1. **ACSD-65540**: è stato risolto il problema che si verificava in presenza di un errore di sintassi SQL dovuto all&#39;assenza della funzione `REGEXP_LIKE` durante l&#39;aggiornamento della tabella `company_structure`.
1. **ACSD-65684**: è stato risolto il problema di prestazioni a causa del quale l&#39;aggiornamento del modulo `Magento_Company` dopo l&#39;aggiornamento a [!DNL B2B] 1.5.2 richiedeva un tempo eccessivamente lungo durante l&#39;elaborazione di un numero elevato di record (~100.000+) nella tabella `company_structure`.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

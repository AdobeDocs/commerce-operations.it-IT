---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a6a18a4cbab9d2e5a0c4824fc5ad9463f9e61c1c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.72

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 include le seguenti patch:
1. **ACSD-68040**: la pagina di ricerca di Frontend ha registrato un calo delle prestazioni nelle [!DNL MariaDB] 10.6 e 11.4 con molte richieste di ricerca cronologica.
1. **ACSD-67941**: le richieste GraphQL con nomi di filtro sconosciuti causano i registri eccezioni PHP.
1. **ACSD-68064**: la creazione di aggiornamenti pianificati genera voci duplicate in ambienti con un numero elevato di categorie nidificate.
1. **ACSD-66807**: la tabella `report_viewed_product_index` mostra un conteggio errato delle visualizzazioni delle pagine dei prodotti.
1. **ACSD-67383**: l&#39;accesso come cliente con due account amministratore società nella stessa sessione causa un errore *Nessuna entità di questo tipo con cartId*.
1. **ACSD-67518**: il reporting avanzato genera righe di intestazione duplicate quando il conteggio delle righe supera le dimensioni del batch.
1. **ACSD-67639**: la creazione di una nota di credito non riesce per i prodotti bundle con **[!UICONTROL Dynamic Price]** impostato su *No*.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: `media_gallery` voci non vengono restituite nel nodo del prodotto Cart GraphQL dopo uno scaricamento della cache.
1. **ACSD-67946**: gli aggiornamenti del carrello mostrano banner di errore duplicati.
1. **ACSD-68011**: è possibile assegnare SKU inesistenti a un catalogo condiviso tramite l&#39;API `/V1/sharedCatalog/:id/assignProducts` [!DNL REST].
1. **ACSD-68118**: la query di GraphQL `customerCart` restituisce valori di attributi di prodotto che non riflettono l&#39;intestazione dell&#39;archivio, causando una localizzazione incoerente.
1. **ACSD-68092**: le opzioni del prodotto del bundle vengono perse dopo più salvataggi a causa di una sincronizzazione non corretta tra gli aggiornamenti pianificati e i dati del prodotto di base.
1. **ACSD-67424**: il valore `updated_at` nella risposta API `GET /carts/search` di [!DNL REST] non corrisponde al valore visualizzato in **[!UICONTROL Admin panel]** quando si utilizzano le virgolette negoziabili.
1. **ACSD-67187**: gli utenti amministratori limitati a siti Web non predefiniti visualizzano l&#39;errore, *&quot;*Crea almeno un catalogo condiviso pubblico per continuare* e non può accedere al pulsante **[!UICONTROL Add New Company]** nella griglia dell&#39;azienda.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '276'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.72

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 include le seguenti patch:

1. **ACSD-66807**: la tabella `report_viewed_product_index` mostra un conteggio errato delle visualizzazioni delle pagine dei prodotti.
1. **ACSD-67187**: gli utenti amministratori limitati a siti Web non predefiniti visualizzano l&#39;errore, *&quot;* Crea almeno un catalogo condiviso pubblico per continuare* e non può accedere al pulsante **[!UICONTROL Add New Company]** nella griglia dell&#39;azienda.
1. **ACSD-67383**: errore durante l&#39;accesso come cliente con due account amministratore società nella stessa sessione.
1. **ACSD-67424**: il valore `updated_at` nella risposta API [!DNL REST] di `GET /carts/search` non corrisponde al valore visualizzato in **[!UICONTROL Admin panel]** quando si utilizzano le virgolette negoziabili.
1. **ACSD-67518**: il reporting avanzato genera righe di intestazione duplicate quando il conteggio delle righe supera le dimensioni del batch.
1. **ACSD-67639**: la creazione di una nota di credito non riesce per i prodotti bundle con **[!UICONTROL Dynamic Price]** impostato su *No*.
1. **ACSD-67696**: `media_gallery` voci non vengono restituite nel nodo del prodotto Cart GraphQL dopo uno scaricamento della cache.
1. **ACSD-67941**: le richieste GraphQL con nomi di filtro sconosciuti causano i registri eccezioni PHP.
1. **ACSD-67946**: l&#39;aggiornamento del carrello mostra banner di errore duplicati.
1. **ACSD-68011**: SKU non esistenti assegnati al catalogo condiviso tramite l&#39;API /V1/sharedCatalog/:id/assignProducts.
1. **ACSD-68040**: la pagina di ricerca front-end rallenta su [!DNL MariaDB] 10.6 con una cronologia di grandi dimensioni.
1. **ACSD-68064**: voci duplicate create durante gli aggiornamenti pianificati in ambienti con categorie annidate in modo approfondito.
1. **ACSD-68092**: le opzioni del prodotto del bundle vengono perse dopo più salvataggi a causa di una sincronizzazione non corretta tra gli aggiornamenti pianificati e i dati del prodotto di base.
1. **ACSD-68118**: la query `customerCart` [!DNL GraphQL] restituisce valori di attributi di prodotto non corretti per la visualizzazione archivio.


Utilizza il menu a sinistra per passare a una pagina patch specifica.

---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
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
source-wordcount: '185'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.71

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 include le seguenti patch:


* **ACSD-60624**: il caricamento dell&#39;immagine non riesce per il contenuto vuoto nelle sezioni Immagine, Banner e Cursore in [!DNL Page Builder]
* **ACSD-67089**: problema di paginazione nell&#39;API `inventory/export-stock-salable-qty`, che limita erroneamente `total_count` alle dimensioni della pagina.
* **ACSD-67093**: il recupero degli ordini tramite [!DNL GraphQL] tramite il filtro dell&#39;intervallo di date restituisce risultati non corretti.
* **ACSD-67459**: impossibile importare prodotti con descrizioni che superano i 65.536 caratteri.
* **ACSD-67603**: tempi di elaborazione lunghi per la generazione di sitemap per i prodotti con inclusione di immagini abilitata
* **ACSD-67643**: le voci duplicate vengono create durante gli aggiornamenti pianificati in ambienti con un numero elevato di categorie nidificate.
* **ACSD-67652**: lo stato del prodotto del bundle viene restituito come esaurito nelle chiamate di [!DNL GraphQL] anche con i prodotti secondari e principali in magazzino.
* **ACSD-67904**: non è possibile inserire ordini se il nome della città contiene cifre (0-9), e commerciale (&amp;), punto (.) o parentesi ().

Utilizza il menu a sinistra per passare a una pagina patch specifica.

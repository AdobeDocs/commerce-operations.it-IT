---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: db405ed4cc0f600e24b22242db9e5f48f31c2756
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.71

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 include le seguenti patch:


* **ACSD-60624**: **[!UICONTROL Upload Image]** non funziona per il contenuto vuoto nelle sezioni [!UICONTROL Image], [!UICONTROL Banner] e [!UICONTROL Slider] in [!DNL Page Builder].
* **ACSD-67089**: problema di paginazione nell&#39;API `inventory/export-stock-salable-qty`, che limita erroneamente `total_count` alle dimensioni della pagina.
* **ACSD-67093**: il recupero degli ordini tramite [!DNL GraphQL] tramite il filtro dell&#39;intervallo di date restituisce risultati non corretti.
* **ACSD-67459**: impossibile importare prodotti con descrizioni che superano i 65.536 caratteri.
* **ACSD-67603**: la generazione di sitemap per i prodotti con esperienze abilitate all&#39;inclusione di immagini richiede tempi di elaborazione lunghi.
* **ACSD-67643**: le voci duplicate vengono create durante gli aggiornamenti pianificati in ambienti con un numero elevato di categorie nidificate.
* **ACSD-67652**: lo stato del prodotto del bundle viene restituito come esaurito nelle chiamate di [!DNL GraphQL] anche con i prodotti secondari e principali in magazzino.
* **ACSD-67904**: non è possibile inserire ordini se il nome della città contiene cifre (0-9), e commerciale (&amp;), punto (.) o parentesi ().

Utilizza il menu a sinistra per passare a una pagina patch specifica.

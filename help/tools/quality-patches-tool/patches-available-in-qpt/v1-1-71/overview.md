---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4660942d90435eaeb6960206c29733bed6453b6a
workflow-type: tm+mt
source-wordcount: '181'
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

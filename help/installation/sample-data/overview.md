---
title: Panoramica dei dati di esempio
description: Scopri come installare i dati di esempio di Adobe Commerce per demo e corsi di formazione, come si comporta la vetrina basata su Luma e le limitazioni per lo sviluppo della produzione.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '257'
ht-degree: 0%
---
# Panoramica dei dati di esempio

I dati di esempio forniscono una vetrina basata sul tema Luma con prodotti, categorie, registrazione del cliente e così via. Funziona come una vetrina Commerce e puoi manipolare prezzi, inventario e regole dei prezzi promozionali utilizzando l&#39;amministratore.

>[!NOTE]
>
>Per esaminare e analizzare il database e varie funzioni, è consigliabile utilizzare dati reali anziché dati di esempio. I dati di esempio sono progettati come simulazione di store pregenerata per dimostrare la progettazione del tema e il comportamento di base della vetrina. Tutte le entità di dati di esempio vengono scritte direttamente nelle tabelle del database, mentre i dati di esempio vengono installati.

È possibile installare dati di esempio prima o dopo l&#39;installazione del software Commerce. Una volta completati i dati di esempio, è possibile rimuoverli o installarli nuovamente come descritto in [Rimuovere i moduli dati di esempio o aggiornare i dati di esempio](remove-or-update.md).

>[!WARNING]
>
>Non è possibile disinstallare i dati di esempio. Utilizza solo i dati di esempio per scoprire come funziona Adobe Commerce. Evitare qualsiasi sviluppo in un sistema in cui sono stati installati dati di esempio.

È possibile installare dati di esempio facoltativi in uno dei modi seguenti:

| Metodo di installazione | Descrizione | Livello di abilità richiesto |
|--- |--- |--- |
| Utilizzo di Composer | [Eseguire `magento sampledata:deploy` per modificare la radice dell&#39;applicazione `composer.json`](composer-packages.md) per abilitare i moduli dati di esempio. | Richiede conoscenza del Compositore e accesso al file system di Commerce. |
| Clonazione degli archivi | [Clonare l&#39;archivio GitHub](git-repositories.md) e l&#39;archivio dati di esempio, quindi collegarli. | Solo per sviluppatori che contribuiscono. Tutti gli altri utenti devono utilizzare uno dei metodi precedenti. |

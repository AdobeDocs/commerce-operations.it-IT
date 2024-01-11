---
title: Panoramica dei dati di esempio
description: Scopri come utilizzare i dati di esempio per i progetti Adobe Commerce e Magento Open Source.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: decaac76955aaae011c308ed1295198abf791abe
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Panoramica dei dati di esempio

I dati di esempio forniscono una vetrina basata sul tema Luma con prodotti, categorie, registrazione del cliente e così via. Funziona come una vetrina Commerce e puoi manipolare prezzi, inventario e regole di prezzi promozionali utilizzando l’amministratore.

>[!NOTE]
>
>Per esaminare e analizzare il database e varie funzioni, è consigliabile utilizzare dati reali anziché dati di esempio. I dati di esempio sono progettati come simulazione di store pregenerata per dimostrare la progettazione del tema e il comportamento di base della vetrina. Tutte le entità di dati di esempio vengono scritte direttamente nelle tabelle del database, mentre i dati di esempio vengono installati.

È possibile installare dati di esempio prima o dopo l’installazione del software Commerce. Una volta completati i dati di esempio, puoi rimuoverli o installarli di nuovo come descritto in [Rimuovere i moduli di dati di esempio o aggiornare i dati di esempio](remove-or-update.md).

>[!WARNING]
>
>Non è possibile disinstallare i dati di esempio. Utilizza i dati di esempio solo per scoprire come funzionano Adobe Commerce e Magento Open Source. Evitare qualsiasi sviluppo in un sistema in cui sono stati installati dati di esempio.

È possibile installare dati di esempio facoltativi in uno dei modi seguenti:

| Metodo di installazione | Descrizione | Livello di abilità richiesto |
|--- |--- |--- |
| Utilizzo di Composer | [Esegui `magento sampledata:deploy` per modificare la directory principale dell&#39;applicazione `composer.json`](composer-packages.md) per abilitare i moduli dati di esempio. | Richiede conoscenza del Compositore e accesso al file system di Commerce. |
| Clonazione degli archivi | [Clonare l’archivio GitHub](git-repositories.md) e l’archivio dati di esempio, quindi collegali tra loro. | Solo per sviluppatori che contribuiscono. Tutti gli altri utenti devono utilizzare uno dei metodi precedenti. |

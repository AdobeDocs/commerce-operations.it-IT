---
title: Panoramica dei dati di esempio
description: Scopri come utilizzare i dati di esempio per i progetti Adobe Commerce e Magento Open Source.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Panoramica dei dati di esempio

I dati di esempio forniscono una vetrina basata sul tema Luma con prodotti, categorie, registrazione del cliente e così via. Funziona come una vetrina Commerce e puoi manipolare prezzi, inventario e regole di prezzi promozionali utilizzando l’amministratore.

È possibile installare dati di esempio prima o dopo l’installazione del software Commerce. Una volta completati i dati di esempio, puoi rimuoverli o installarli di nuovo come descritto in [Rimuovere i moduli di dati di esempio o aggiornare i dati di esempio](remove-or-update.md).

>[!WARNING]
>
>Non è possibile disinstallare i dati di esempio. È consigliabile utilizzare i dati di esempio solo per scoprire come funzionano Adobe Commerce e il Magento Open Source. Evitare qualsiasi sviluppo in un sistema in cui sono stati installati dati di esempio.

È possibile installare dati di esempio facoltativi in uno dei modi seguenti:

| Metodo di installazione | Descrizione | Livello di abilità richiesto |
|--- |--- |--- |
| Utilizzo di Composer | [Esegui `magento sampledata:deploy` per modificare la directory principale dell&#39;applicazione `composer.json`](composer-packages.md) per abilitare i moduli dati di esempio. | Richiede conoscenza del Compositore e accesso al file system di Commerce. |
| Clonazione degli archivi | [Clonare l’archivio GitHub](git-repositories.md) e l’archivio dati di esempio, quindi collegali tra loro. | Solo per sviluppatori che contribuiscono. Tutti gli altri utenti devono utilizzare uno dei metodi precedenti. |

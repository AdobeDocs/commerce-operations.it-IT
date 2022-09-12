---
title: Panoramica dei dati di esempio
description: Scopri come utilizzare dati di esempio per progetti Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Panoramica dei dati di esempio

I dati di esempio forniscono una vetrina basata sul tema Luma dotato di prodotti, categorie, registrazione dei clienti e così via. Funziona come una vetrina Commerce e puoi manipolare prezzi, scorte e regole di prezzo promozionali utilizzando l’amministratore.

È possibile installare i dati di esempio prima o dopo l’installazione del software Commerce. Una volta completati i dati di esempio, puoi rimuoverli o installarli nuovamente come descritto in [Rimuovere moduli di dati di esempio o aggiornare dati di esempio](remove-or-update.md).

>[!WARNING]
>
>Non è possibile disinstallare i dati di esempio. È consigliabile utilizzare solo dati di esempio per scoprire come funzionano Adobe Commerce e Magenti Open Source. Evita di eseguire qualsiasi sviluppo in un sistema in cui sono installati dati di esempio.

Puoi installare i dati di esempio facoltativi in uno dei seguenti modi:

| Metodo di installazione | Descrizione | Livello di abilità richiesto |
|--- |--- |--- |
| Utilizzo del Compositore | [Esegui `magento sampledata:deploy` per modificare la radice dell&#39;applicazione `composer.json`](composer-packages.md) per abilitare moduli di dati di esempio. | Richiede la conoscenza del Compositore e l’accesso al file system Commerce. |
| Clonazione degli archivi | [Clonare l’archivio GitHub](git-repositories.md) e l’archivio dati di esempio, quindi collegali. | Solo per sviluppatori contributori. Tutti gli altri devono utilizzare uno dei metodi precedenti. |

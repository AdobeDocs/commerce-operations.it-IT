---
title: Configurazione del sistema di sviluppo
description: Scopri come impostare un sistema di sviluppo per l’applicazione Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Configurazione del sistema di sviluppo

È possibile disporre di un numero qualsiasi di sistemi di sviluppo, purché sia soddisfatta la seguente condizione:

- Vengono tutti eseguiti Commerce 2.2 o versione successiva
- Tutto il codice Commerce è sotto il controllo del codice sorgente nello stesso archivio dei sistemi di build e produzione
- Ogni sistema di sviluppo deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode)
- Ha la proprietà del file system e le autorizzazioni impostate come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/technical-details.md).
- Assicurati che tutte le seguenti operazioni siano _escluso_ dal controllo del codice sorgente:

   - `vendor` directory (e sottodirectory)
   - `generated` directory (e sottodirectory)
   - `pub/static` directory (e sottodirectory)
   - `app/etc/env.php` file

- Assicurati che `app/etc/config.php` è _incluso_ nel controllo sorgente

Se usa Git, il `.gitignore` Il file fornisce la maggior parte delle informazioni precedenti. Consulta la [`.gitignore` riferimento](../reference/config-reference-gitignore.md).

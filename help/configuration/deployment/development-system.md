---
title: Configurazione del sistema di sviluppo
description: Scopri come impostare un sistema di sviluppo per l’applicazione Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Configurazione del sistema di sviluppo

È possibile disporre di un numero qualsiasi di sistemi di sviluppo, purché sia soddisfatta la seguente condizione:

- Tutti eseguono Commerce 2.2 o versione successiva
- Tutto il codice Commerce è sotto il controllo del codice sorgente nello stesso archivio dei sistemi di build e produzione
- Ogni sistema di sviluppo deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode)
- Ha la proprietà del file system e le autorizzazioni impostate come descritto in [Prerequisiti per i sistemi di sviluppo, compilazione e produzione](../deployment/technical-details.md).
- Assicurarsi che tutti i seguenti elementi siano _esclusi_ dal controllo del codice sorgente:

   - Directory `vendor` (e sottodirectory)
   - Directory `generated` (e sottodirectory)
   - Directory `pub/static` (e sottodirectory)
   - `app/etc/env.php` file

- Assicurarsi che `app/etc/config.php` sia _incluso_ nel controllo del codice sorgente

Se si utilizza Git, il file `.gitignore` fornisce la maggior parte dei dati precedenti. Vedi il riferimento [`.gitignore`](../reference/config-reference-gitignore.md).

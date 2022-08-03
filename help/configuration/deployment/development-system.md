---
title: Configurazione del sistema di sviluppo
description: Scopri come configurare un sistema di sviluppo per l’applicazione Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Configurazione del sistema di sviluppo

È possibile disporre di un numero qualsiasi di sistemi di sviluppo, purché sia vero quanto segue:

- Tutti eseguono Commerce 2.2 o versione successiva
- Tutto il codice Commerce è sotto il controllo del codice sorgente nello stesso archivio dei sistemi di generazione e produzione
- Ogni sistema di sviluppo deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode)
- Possiede la proprietà e le autorizzazioni del file system impostate come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/technical-details.md).
- Assicurati che tutti i seguenti elementi siano _esclusi_ dal controllo della sorgente:

   - `vendor` directory (e sottodirectory)
   - `generated` directory (e sottodirectory)
   - `pub/static` directory (e sottodirectory)
   - `app/etc/env.php` file

- Assicurati `app/etc/config.php` è _incluso_ nel controllo della sorgente

Se utilizzi Git, la `.gitignore` Il file fornisce la maggior parte dei precedenti. Consulta la sezione [`.gitignore` riferimento](../reference/config-reference-gitignore.md).

---
title: Come funziona la migrazione dei dati
description: Scopri il processo di migrazione dei dati tra il Magento 1 e il Magento 2, compresi la terminologia, i diagrammi del flusso di lavoro e i passaggi.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Come funziona la migrazione dei dati

Questo argomento fornisce una panoramica di alto livello delle modalità di migrazione dei dati dal Magento 1 al Magento 2 utilizzando [!DNL Data Migration Tool].

La [!DNL Data Migration Tool] è uno strumento di interfaccia a riga di comando (CLI) utilizzato per il trasferimento di dati dal Magento 1 al Magento 2. Lo strumento verifica la coerenza tra le strutture del database di Magento 1 e 2 (tabelle e campi), tiene traccia dell’avanzamento del trasferimento dei dati, crea registri ed esegue test di verifica dei dati.

## Terminologia

* **Modalità** - un set ordinato di operazioni per la migrazione dei dati da Magento 1.x a Magento 2.x.
* **Passaggi** - le attività in una modalità che definiscono i tipi di dati da migrare.
* **Fasi** - le attività al passaggio che convalidano, trasferiscono e verificano i dati.
* **Mappa i file** - File XML che definiscono le regole e le connessioni tra le strutture dati di Magento 1.x e Magento 2.x per il completamento delle fasi.

## Modalità

La [!DNL Data Migration Tool] divide il processo di migrazione in tre fasi o *modalità* al fine di trasferire e adattare i dati dal Magento 1.x al Magento 2.x. Le tre modalità sono elencate qui e devono essere eseguite in questo ordine:

1. **Modalità impostazioni**: esegue la migrazione della configurazione di sistema e delle impostazioni relative al sito web.
1. **Modalità dati**: esegue la migrazione in massa delle risorse del database.
1. **Modalità Delta**: esegue la migrazione delle modifiche incrementali (modifiche dall’ultima esecuzione), ad esempio nuovi clienti e ordini.

![Modalità di migrazione](../../assets/data-migration/MigrationModes2.png)

## Passaggi

La [!DNL Data Migration Tool] utilizza un elenco di *step* all’interno di ogni modalità per migrare un particolare tipo di dati. Ad esempio, in modalità Impostazioni sono disponibili due passaggi per migrare tutti i dati delle impostazioni: il passaggio Memorizza e il passaggio Impostazioni . I dettagli sui dati specifici migrati in ciascuno di questi passaggi (e per i passaggi nelle altre modalità) si trovano nella [[!DNL Data Migration Tool] Specifiche tecniche](technical-specification.md).

![Panoramica sulla migrazione](../../assets/data-migration/MigrationOverview2.png)

## Fasi

All&#39;interno di ogni passaggio sono tre *stadi* che vengono sempre eseguiti in questo modo per garantire la corretta migrazione dei dati:

1. **Controllo integrità**: Confronta i nomi dei campi, i tipi e altre informazioni della tabella per verificare la compatibilità tra le strutture di dati dei Magenti 1 e 2.
1. **Trasferimento dati**: Trasferisce la tabella di dati per tabella dai Magenti 1 e 2.
1. **Controllo volume**: Confronta il numero di record tra tabelle per verificare che il trasferimento sia stato eseguito correttamente.

![Fasi della migrazione](../../assets/data-migration/MigrationSteps2.png)

## Mappa i file

Al livello più basso dei processi di migrazione sono i *mappatura dei file*. La [!DNL Data Migration Tool] utilizza i file di mappa nelle fasi di un passaggio per trasformare diverse strutture di dati tra le tabelle Magento 1.x e 2.x.

Ad esempio, quando si trasformano i dati da un database Magenti Open Source 1.8.0.0 a Magenti Open Source 2.x.x, il file di mappa tiene conto del fatto che una tabella è stata rinominata e la rinomina di conseguenza nel database di destinazione. Se non vi sono differenze nella struttura dei dati o nel formato dei dati, la [!DNL Data Migration Tool] lo trasferisce così come è, compresi i dati provenienti da tabelle create da estensioni, al database di Magento 2.

Quando le differenze non vengono dichiarate nei file di mappa, la variabile [!DNL Data Migration Tool] visualizza un errore e non si avvia.

La mappatura dei file viene discussa più dettagliatamente in [[!DNL Data Migration Tool] Specifiche tecniche].

## Diagramma del flusso di migrazione

![Flusso di migrazione](../../assets/data-migration/migration_flow.png)

<!-- Link definitions -->
[[!DNL Data Migration Tool] Specifiche tecniche]: technical-Specification.md

[Migration Modes]: ../../assets/data-migration/MigrationModes2.png

[Migration Overview]: ../../assets/data-migration/MigrationOverview2.png

[Migration Steps]: ../../assets/data-migration/MigrationSteps2.png

Siamo lieti che tu stia considerando di passare dalla piattaforma commerciale #1 del mondo — Magento 1.x — alla piattaforma del futuro, Magento 2. Siamo entusiasti di condividere i dettagli di questo processo, che chiamiamo migrazione.

## Componenti di migrazione

La migrazione al Magento 2 comprende quattro componenti: dati, estensioni e codice personalizzato, temi e personalizzazioni.

### Dati

Abbiamo sviluppato il **Magento 2[!DNL Data Migration Tool]** per aiutarti a spostare in modo efficiente tutti i tuoi prodotti, clienti e i dati degli ordini, le configurazioni degli archivi, le promozioni e altro ancora al Magento 2. Questa guida fornisce informazioni sullo strumento e sulle best practice per utilizzarlo per migrare i dati.

### Estensioni e codice personalizzato

Abbiamo lavorato sodo con la community di sviluppo per aiutarti a utilizzare le estensioni Magento 1 nel Magento 2. Ora siamo orgogliosi di presentare il [Commerce Marketplace](https://marketplace.magento.com/), dove puoi scaricare o acquistare le versioni più recenti delle estensioni preferite.

Ulteriori informazioni sullo sviluppo di estensioni per il Magento 2 sono disponibili in [Guida per gli sviluppatori PHP](https://developer.adobe.com/commerce/php/development/).

### Temi e personalizzazioni

Il Magento 2 utilizza nuovi approcci e tecnologie che offrono ai commercianti una capacità ineguagliabile di creare esperienze di acquisto innovative e di scalare a nuovi livelli. Per sfruttare questi progressi, gli sviluppatori devono apportare modifiche ai temi e alle personalizzazioni. La documentazione è disponibile online per la creazione del Magento 2 [temi](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)e [personalizzazioni](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## sforzi in materia di migrazione

Proprio come un aggiornamento tra le versioni 1.x (ad esempio, dalla v1.12 alla v1.14), il livello di impegno per la migrazione dal Magento 1 al Magento 2 dipende da come hai creato il tuo sito e dal suo livello di personalizzazione.
Tuttavia, miglioriamo costantemente la [!DNL Data Migration Tool] (vedi [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) per maggiori dettagli); quindi gli sforzi di migrazione sono in continuo calo.

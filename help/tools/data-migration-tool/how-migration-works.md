---
title: Funzionamento della migrazione dei dati
description: Scopri il processo di migrazione dei dati tra Magento 1 e Magento 2, inclusa la terminologia, i diagrammi di flusso di lavoro e i passaggi.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Funzionamento della migrazione dei dati

In questo argomento viene fornita una panoramica generale della migrazione dei dati da Magento 1 a Magento 2 tramite [!DNL Data Migration Tool].

[!DNL Data Migration Tool] è uno strumento dell&#39;interfaccia della riga di comando (CLI) utilizzato per trasferire dati da Magento 1 a Magento 2. Lo strumento verifica la coerenza tra le strutture di database di Magento 1 e 2 (tabelle e campi), tiene traccia dell’avanzamento del trasferimento dei dati, crea registri ed esegue i test di verifica dei dati.

## Terminologia

* **Modalità**: un set ordinato di operazioni per la migrazione dei dati da Magento 1.x a Magento 2.x.
* **Passaggi**: le attività in una modalità che definiscono i tipi di dati da migrare.
* **Fasi**: le attività nel passaggio che convalidano, trasferiscono e verificano i dati.
* **File di mapping**: file XML che definiscono le regole e le connessioni tra le strutture di dati di Magento 1.x e Magento 2.x per il completamento delle fasi.

## Modalità

[!DNL Data Migration Tool] divide il processo di migrazione in tre fasi o *modalità* per trasferire e adattare i dati da Magento 1.x a Magento 2.x. Le tre modalità sono elencate qui e devono essere eseguite in questo ordine:

1. **Modalità impostazioni**: esegue la migrazione della configurazione di sistema e delle impostazioni relative al sito Web.
1. **Modalità dati**: esegue la migrazione in blocco delle risorse del database.
1. **Modalità delta**: esegue la migrazione delle modifiche incrementali (modifiche dall&#39;ultima esecuzione), ad esempio nuovi clienti e ordini.

![Modalità di migrazione](../../assets/data-migration/MigrationModes2.png)

## Passaggi

[!DNL Data Migration Tool] utilizza un elenco di *passaggi* in ogni modalità per migrare un particolare tipo di dati. Ad esempio, nella modalità Impostazioni sono disponibili due passaggi per la migrazione di tutti i dati delle impostazioni: il passaggio Archivi e il passaggio Impostazioni. I dettagli sui dati specifici migrati in ciascuno di questi passaggi (e per i passaggi nelle altre modalità) sono disponibili nelle [[!DNL Data Migration Tool] Specifiche tecniche](technical-specification.md).

![Panoramica sulla migrazione](../../assets/data-migration/MigrationOverview2.png)

## Fasi

All&#39;interno di ogni passaggio sono presenti tre *fasi* che vengono sempre eseguite in questo ordine per garantire la corretta migrazione dei dati:

1. **Controllo di integrità**: confronta i nomi dei campi di tabella, i tipi e altre informazioni per verificare la compatibilità tra le strutture di dati di Magento 1 e 2.
1. **Trasferimento dati**: trasferisce la tabella dati per tabella da Magento 1 e 2.
1. **Controllo volume**: confronta il numero di record tra le tabelle per verificare che il trasferimento sia stato eseguito correttamente.

![Fasi di migrazione](../../assets/data-migration/MigrationSteps2.png)

## File mappa

Al livello più basso dei processi di migrazione si trovano i *file di mapping* XML. [!DNL Data Migration Tool] utilizza i file mappa nelle fasi di un passaggio per trasformare diverse strutture di dati tra le tabelle Magento 1.x e 2.x.

Quando ad esempio si trasformano dati da un database di Magento Open Source 1.8.0.0 a Magento Open Source 2.x.x, il file di mapping tiene conto del fatto che una tabella è stata rinominata e la rinomina di conseguenza nel database di destinazione. Se non esistono differenze nella struttura o nel formato dei dati, [!DNL Data Migration Tool] li trasferisce così come sono, inclusi i dati delle tabelle create dalle estensioni, al database di Magento 2.

Quando le differenze non vengono dichiarate nei file di mappa, [!DNL Data Migration Tool] visualizza un errore e non si avvia.

I file di mappatura vengono descritti più dettagliatamente in [[!DNL Data Migration Tool] Specifiche tecniche].

## Diagramma del flusso di migrazione

![Flusso di migrazione](../../assets/data-migration/migration_flow.png)

[Specifiche tecniche [!DNL Data Migration Tool]](technical-specification.md)

Siamo lieti che tu stia considerando di passare dalla piattaforma di #1 commerce del mondo, Magento 1.x, alla piattaforma del futuro, Magento 2. Siamo entusiasti di condividere i dettagli di questo processo, che chiamiamo migrazione.

## Componenti di migrazione

La migrazione a Magento 2 prevede quattro componenti: dati, estensioni e codice personalizzato, temi e personalizzazioni.

### Dati

Abbiamo sviluppato **Magento 2[!DNL Data Migration Tool]** per aiutarti a trasferire in modo efficiente tutti i tuoi prodotti, clienti e dati degli ordini, configurazioni di store, promozioni e altro ancora in Magento 2. Questa guida fornisce informazioni sullo strumento e sulle best practice per utilizzarlo per migrare i dati.

### Estensioni e codice personalizzato

Abbiamo lavorato sodo con la community di sviluppo per aiutarti a utilizzare le estensioni Magento 1 in Magento 2. Ora siamo orgogliosi di presentare [Commerce Marketplace](https://marketplace.magento.com/), dove puoi scaricare o acquistare le versioni più recenti delle tue estensioni preferite.

Ulteriori informazioni sullo sviluppo di estensioni per Magento 2 sono disponibili nella [Guida per gli sviluppatori PHP](https://developer.adobe.com/commerce/php/development/).

### Temi e personalizzazioni

Magento 2 utilizza nuovi approcci e tecnologie che offrono ai commercianti la possibilità di creare esperienze di acquisto innovative e scalare a nuovi livelli. Per sfruttare questi progressi, gli sviluppatori devono apportare modifiche ai temi e alle personalizzazioni. La documentazione è disponibile online per la creazione di [temi](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) e [personalizzazioni](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) di Magento 2.

## Attività di migrazione

Proprio come per un aggiornamento tra versioni 1.x (ad esempio, da v1.12 a v1.14), il livello di impegno per la migrazione da Magento 1 a Magento 2 dipende da come è stato creato il sito e dal relativo livello di personalizzazione.
Tuttavia, stiamo migliorando costantemente [!DNL Data Migration Tool] (consulta il [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) per ulteriori dettagli); pertanto gli sforzi di migrazione sono in continua diminuzione.

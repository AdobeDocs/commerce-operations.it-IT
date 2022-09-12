---
title: Aggiornare lo schema e i dati del database
description: Segui questi passaggi per aggiornare lo schema del database Adobe Commerce o Magenti Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Aggiornare lo schema e i dati del database

Prima di utilizzare questo comando, è necessario [installare l&#39;applicazione](../advanced.md).

## Aggiornare lo schema e i dati del database

Ogni volta che esegui un&#39;azione che causa la [schema di database](https://glossary.magento.com/database-schema) o i dati da modificare, è necessario aggiornarli eseguendo il comando descritto in questa sezione. Segue un elenco parziale dei motivi:

* È stata aggiornata l&#39;applicazione utilizzando la riga di comando
* È stato installato o aggiornato un componente utilizzando la riga di comando
* È stato abilitato o disabilitato un componente utilizzando la riga di comando

>[!NOTE]
>
>A *component* può essere un modulo, un tema o un Language Pack; non importa se il componente proviene dalla Commerce Marketplace o meno.

1. Avvia l&#39;aggiornamento:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Dove `--keep-generated` è un argomento facoltativo che non viene aggiornato [file di visualizzazione statici](../../configuration/cli/static-view-file-deployment.md). Questo argomento facoltativo è da utilizzare *only* in circostanze limitate da integratori di sistemi esperti. Deve essere utilizzato *only* in [modalità di produzione](../../configuration/bootstrap/application-modes.md#production-mode). Dovrebbe *not* sono utilizzati in [modalità sviluppatore](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

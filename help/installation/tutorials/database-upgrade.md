---
title: Aggiornare lo schema e i dati del database
description: Per aggiornare lo schema del database Adobe Commerce, segui la procedura riportata di seguito.
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Aggiornare lo schema e i dati del database

Prima di utilizzare questo comando, è necessario [installare l&#39;applicazione](../advanced.md).

## Aggiornare lo schema e i dati del database

Ogni volta che si esegue un&#39;azione che causa la modifica dello schema o dei dati del database, è necessario aggiornarli eseguendo il comando descritto in questa sezione. Segue un elenco parziale dei motivi:

* L’applicazione è stata aggiornata utilizzando la riga di comando
* È stato installato o aggiornato un componente utilizzando la riga di comando
* È stato abilitato o disabilitato un componente utilizzando la riga di comando

>[!NOTE]
>
>Un *componente* può essere un modulo, un tema o un Language Pack; non importa se il componente proviene da Commerce Marketplace o meno.

1. Avvia l&#39;aggiornamento:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Dove `--keep-generated` è un argomento facoltativo che non aggiorna [i file di visualizzazione statica](../../configuration/cli/static-view-file-deployment.md). Questo argomento facoltativo deve essere utilizzato *solo* in circostanze limitate da integratori di sistema esperti. Deve essere utilizzato *solo* in [modalità di produzione](../../configuration/bootstrap/application-modes.md#production-mode). *non* deve essere utilizzato in [modalità sviluppatore](../../configuration/bootstrap/application-modes.md#developer-mode).

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

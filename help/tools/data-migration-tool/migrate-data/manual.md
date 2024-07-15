---
title: Dati che richiedono la migrazione manuale
description: Scopri i dati che devono essere migrati manualmente durante la migrazione dei dati dal Magento 1 al Magento 2 e come farlo.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Dati che richiedono la migrazione manuale

È necessario eseguire la migrazione manuale di quattro tipi di dati:

* Media

* Progettazione vetrina

* Account utente amministratore

* Elenchi di controllo di accesso (ACL)

## Media

Questa sezione illustra come eseguire manualmente la migrazione dei file multimediali.

### File multimediali memorizzati nel database

>[!WARNING]
>
>Il metodo di archiviazione dei supporti del database è obsoleto a partire dal Magento 2.4.3.


Questa sezione è valida per *solo* se i file multimediali vengono archiviati nel database di Magento. Questo passaggio deve essere eseguito prima della [migrazione dei dati](data.md):

1. Accedere al pannello di amministrazione di Magento 1 come amministratore.

1. Fare clic su **Sistema** > **Configurazione** > AVANZATE > **Sistema**.

1. Nel riquadro di destra, scorri fino a **Configurazione archiviazione per file multimediali**.

1. Nell&#39;elenco **Seleziona database multimediale** fare clic sul nome del database di archiviazione multimediale.

1. Fare clic su **Sincronizza**.

Quindi, ripeti gli stessi passaggi nel pannello di amministrazione di Magento 2.

### File multimediali nel file system

Tutti i file multimediali (immagini per prodotti, categorie, editor WYSIWYG e così via) devono essere copiati manualmente da `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Tuttavia, *non* copiare i file `.htaccess` presenti nella cartella `media` del Magento 1. Il Magento 2 ha un proprio `.htaccess` che deve essere mantenuto.

## Progettazione vetrina

* La progettazione in file (CSS, JS, modelli, layout XML) ne ha modificato posizione e formato

* Aggiornamenti del layout memorizzati nel database. Inserito tramite l’amministratore del Magento 1 in pagine CMS, widget CMS, pagine di categorie e pagine di prodotti

## Elenchi di controllo di accesso (ACL)

È necessario ricreare manualmente tutti gli elementi:

* credenziali per le API dei servizi Web (SOAP, XML-RPC e REST)

* account utente amministrativi e associarli ai privilegi di accesso

>[!NOTE]
>
>È possibile regolare il fuso orario per un&#39;entità di database utilizzando il gestore `\Migration\Handler\Timezone`. Per ulteriori dettagli, consulta la sezione [follow-up](follow-up.md).

---
title: Dati che richiedono la migrazione manuale
description: Scopri i dati che devono essere migrati manualmente durante la migrazione dei dati dal Magento 1 al Magento 2 e come farlo.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Dati che richiedono la migrazione manuale

È necessario eseguire la migrazione manuale di quattro tipi di dati:

* Contenuti multimediali

* Progettazione vetrina

* Account utente amministratore

* Elenchi di controllo di accesso (ACL)

## Contenuti multimediali

Questa sezione illustra come eseguire manualmente la migrazione dei file multimediali.

### File multimediali memorizzati nel database

>[!WARNING]
>
>Il metodo di archiviazione dei supporti del database è obsoleto a partire dal Magento 2.4.3.


Questa sezione si applica a te *solo* se si memorizzano file multimediali nel database di Magento. Questo passaggio deve essere eseguito prima di [migrazione dei dati](data.md):

1. Accedere al pannello di amministrazione di Magento 1 come amministratore.

1. Clic **Sistema** > **Configurazione** > AVANZATE > **Sistema**.

1. Nel riquadro di destra, scorri fino a **Configurazione archiviazione per contenuti multimediali**.

1. Dalla sezione **Seleziona database multimediale** fare clic sul nome del database di archiviazione dei supporti.

1. Clic **Sincronizza**.

Quindi, ripeti gli stessi passaggi nel pannello di amministrazione di Magento 2.

### File multimediali nel file system

Tutti i file multimediali (immagini per prodotti, categorie, editor WYSIWYG e così via) devono essere copiati manualmente da `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Tuttavia, eseguire *non* copia `.htaccess` file nel Magento 1 `media` cartella. Il Magento 2 ha il proprio `.htaccess` questo dovrebbe essere mantenuto.

## Progettazione vetrina

* La progettazione in file (CSS, JS, modelli, layout XML) ne ha modificato posizione e formato

* Aggiornamenti del layout memorizzati nel database. Inserito tramite l’amministratore del Magento 1 in pagine CMS, widget CMS, pagine di categorie e pagine di prodotti

## Elenchi di controllo di accesso (ACL)

È necessario ricreare manualmente tutti gli elementi:

* credenziali per le API dei servizi Web (SOAP, XML-RPC e REST)

* account utente amministrativi e associarli ai privilegi di accesso

>[!NOTE]
>
>È possibile regolare il fuso orario per un&#39;entità di database utilizzando `\Migration\Handler\Timezone` handler. Consulta la [seguito](follow-up.md) per ulteriori dettagli.

---
title: Dati che richiedono la migrazione manuale
description: Scopri i dati che devono essere migrati manualmente durante una migrazione di dati da Magento 1 a Magento 2 e come farlo.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
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
>Il metodo di archiviazione dei supporti del database è diventato obsoleto a partire dalla versione 2.4.3 di Magento.


Questa sezione è valida per *solo* se archivi file multimediali nel database di Magento. Questo passaggio deve essere eseguito prima della [migrazione dei dati](data.md):

1. Accedi al pannello di amministrazione di Magento 1 come amministratore.

1. Fare clic su **Sistema** > **Configurazione** > AVANZATE > **Sistema**.

1. Nel riquadro di destra, scorri fino a **Configurazione archiviazione per file multimediali**.

1. Nell&#39;elenco **Seleziona database multimediale** fare clic sul nome del database di archiviazione multimediale.

1. Fare clic su **Sincronizza**.

Quindi, ripeti gli stessi passaggi nel pannello di amministrazione di Magento 2.

### File multimediali nel file system

Tutti i file multimediali (immagini per prodotti, categorie, editor di WYSIWYG e così via) devono essere copiati manualmente da `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Tuttavia, *non* copia i file `.htaccess` presenti nella cartella `media` di Magento 1. Magento 2 ha un proprio `.htaccess` che deve essere mantenuto.

## Progettazione vetrina

* La progettazione in file (CSS, JS, modelli, layout XML) ne ha modificato posizione e formato

* Aggiornamenti del layout memorizzati nel database. Inserito tramite l’amministratore di Magento 1 in pagine CMS, widget CMS, pagine categorie e pagine prodotto

## Elenchi di controllo di accesso (ACL)

È necessario ricreare manualmente tutti gli elementi:

* credenziali per le API dei servizi Web (SOAP, XML-RPC e REST)

* account utente amministrativi e associarli ai privilegi di accesso

>[!NOTE]
>
>È possibile regolare il fuso orario per un&#39;entità di database utilizzando il gestore `\Migration\Handler\Timezone`. Per ulteriori dettagli, consulta la sezione [follow-up](follow-up.md).

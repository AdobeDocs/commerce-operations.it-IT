---
title: Dati che richiedono migrazione manuale
description: Scopri come eseguire la migrazione manuale dei dati da un Magento 1 a un Magento 2 e come migrare manualmente.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Dati che richiedono migrazione manuale

Ci sono quattro tipi di dati che devono essere migrati manualmente:

* Media

* Progettazione della vetrina

* Account utente amministratore

* Elenchi di controllo di accesso (ACL)

## Media

Questa sezione illustra come migrare manualmente i file multimediali.

### File multimediali memorizzati nel database

>[!WARNING]
>
>Il metodo di archiviazione dei supporti di database è obsoleto a partire dal Magento 2.4.3.


Questa sezione si applica a te *only* se si memorizzano file multimediali nel database di Magento. Questo passaggio deve essere eseguito prima di [migrazione dei dati](data.md):

1. Accedi al pannello di amministrazione del Magento 1 come amministratore.

1. Fai clic su **Sistema** > **Configurazione** > AVANZATO > **Sistema**.

1. Nel riquadro a destra, scorri fino a **Configurazione dell&#39;archiviazione per i file multimediali**.

1. Da **Seleziona database multimediale** fare clic sul nome del database di archiviazione multimediale.

1. Fai clic su **Sincronizza**.

Quindi, ripeti gli stessi passaggi nel pannello Amministratore Magento 2.

### File multimediali nel file system

Tutti i file multimediali (immagini per prodotti, categorie, editor WYSIWYG e così via) devono essere copiati manualmente da `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Tuttavia, sì *not* copia il `.htaccess` file presenti nel Magento 1 `media` cartella. Il Magento 2 ha il proprio `.htaccess` ciò dovrebbe essere preservato.

## Progettazione della vetrina

* La progettazione nei file (CSS, JS, modelli, layout XML) ha modificato la posizione e il formato

* Aggiornamenti di layout memorizzati nel database. Inserito tramite l’amministratore del Magento 1 nelle pagine CMS, nei widget CMS, nelle pagine delle categorie e nelle pagine dei prodotti

## Elenchi di controllo di accesso (ACL)

È necessario ricreare manualmente tutti gli elementi:

* credenziali per le API dei servizi Web (SOAP, XML-RPC e REST)

* account utente amministrativi e associali ai privilegi di accesso

>[!NOTE]
>
>È possibile modificare il fuso orario di un&#39;entità di database utilizzando `\Migration\Handler\Timezone` handler. Consulta la sezione [follow-up](follow-up.md) per ulteriori dettagli.

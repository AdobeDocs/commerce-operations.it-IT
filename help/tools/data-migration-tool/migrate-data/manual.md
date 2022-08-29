---
title: Dati che richiedono migrazione manuale
description: 'Scopri come eseguire la migrazione manuale dei dati da un Magento 1 a un Magento 2 e come migrare manualmente. '
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Dati che richiedono migrazione manuale

Ci sono quattro tipi di dati che devono essere migrati manualmente:

* Media

* [Vetrina](https://glossary.magento.com/storefront) progettazione

* [Amministratore](https://glossary.magento.com/admin) account utente

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

1. Da **Seleziona database multimediale** fai clic sul nome del tuo [archiviazione su supporti](https://glossary.magento.com/media-storage) database.

1. Fai clic su **Sincronizza**.

Quindi, ripeti gli stessi passaggi nel pannello Amministratore Magento 2.

### File multimediali nel file system

Tutti i file multimediali (immagini per prodotti, categorie, [WYSIWYG](https://glossary.magento.com/wysiwyg) e così via) devono essere copiati manualmente da `<your Magento 1 install dir>/media` a `<your Magento 2 install dir>/pub/media`.

Tuttavia, sì *not* copia il `.htaccess` file presenti nel Magento 1 `media` cartella. Il Magento 2 ha il proprio `.htaccess` ciò dovrebbe essere preservato.

## Progettazione della vetrina

* Progettazione in file (CSS, JS, modelli, [XML](https://glossary.magento.com/xml) layout) ha cambiato posizione e formato

* [Layout](https://glossary.magento.com/layout) Aggiornamenti memorizzati nel database. Inserito tramite l’amministratore del Magento 1 in [CMS](https://glossary.magento.com/cms) Pagine, Widget CMS, [Categoria](https://glossary.magento.com/category) Pagine e pagine di prodotto

## Elenchi di controllo di accesso (ACL)

È necessario ricreare manualmente tutti gli elementi:

* credenziali per le API dei servizi Web (SOAP, XML-RPC e REST)

* account utente amministrativi e associali ai privilegi di accesso

>[!NOTE]
>
>È possibile modificare il fuso orario di un&#39;entità di database utilizzando `\Migration\Handler\Timezone` handler. Consulta la sezione [follow-up](follow-up.md) per ulteriori dettagli.

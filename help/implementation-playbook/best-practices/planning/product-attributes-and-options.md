---
title: Best practice per la configurazione degli attributi del prodotto
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di attributi di prodotto, opzioni di attributi e set di attributi
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Best practice per la configurazione dell’attributo di prodotto

- Per ottenere prestazioni ottimali, non configurare un numero di attributi di prodotto o opzioni di attributi di prodotto superiore a quello massimo consigliato.

- **Attributi del prodotto**—
   - Per Adobe Commerce versione 2.3.x e da 2.4.0 a 2.4.1-p1, configura non più di 500 attributi
   - Per Adobe Commerce versione 2.4.2 e successive, configura fino a 1500 attributi di prodotto
- **Opzioni degli attributi del prodotto**-Configurare fino a 100 opzioni di attributo per ciascun attributo
- **Set di attributi del prodotto**-Configurare un massimo di 1000 set di attributi _

>[!NOTE]
>
>Gli attributi del prodotto specificano le funzioni che si applicano a livello globale a tutti i prodotti. Le opzioni dell’attributo del prodotto sono personalizzazioni per specificare le funzioni applicabili a prodotti specifici.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Riduci il numero di attributi del prodotto

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati di prodotto nella vetrina:

- Utilizzare diversi modelli di prodotto (set di attributi) per prodotti diversi.
- Sfruttare opzioni personalizzate e prodotti complessi per la gestione delle varianti
- Riduci al minimo il numero di attributi ricercabili.
- Rimuovi le proprietà del prodotto non utilizzate.
- Archivia e gestisci attributi non correlati all’e-commerce in sistemi esterni di gestione dei prodotti (PMS).

## Ridurre il numero di opzioni degli attributi di prodotto

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati di prodotto nella vetrina:

- Utilizza diversi meccanismi di variante per creare prodotti: prodotti complessi, opzioni personalizzate come origine di varianti di prodotto.
- Crea modelli di prodotto specifici con attributi di targeting e opzioni per evitare modelli di prodotto e contenitori di opzioni generalizzati.
- Gestisce un elenco delle opzioni di attributo effettive.
- Gestire le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

## Ridurre il numero di set di attributi di prodotto

Rimuovere i set di attributi di prodotto inutilizzati utilizzando MySQL.

### Verifica la configurazione del set di attributi

1. [Connessione al database del sito](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Trovare il numero di set di attributi utilizzando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Rimuovere tutti i set di attributi inutilizzati.

## Potenziali impatti sulle prestazioni

Configurazione di molti **attributi prodotto** aumenta le dimensioni del modello di prodotto per ciascun prodotto (struttura EAV) e la quantità di dati da recuperare. Questo aumento influisce sulle operazioni nei seguenti modi:

- Aumento del traffico delle query SQL correlate al recupero dei dati EAV e della quantità di dati elaborati, con conseguente riduzione della velocità effettiva del database
- Aumento significativo della dimensione degli indici Adobe Commerce e dell’indice di ricerca full-text
- Raggiungimento dei limiti rigidi di MySQL durante la creazione di un indice FLAT per modelli di prodotto di dimensioni eccessive e impossibilità di utilizzarlo

L’aumento dei dati di prodotto e delle dimensioni dell’indice può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più elevati per la maggior parte degli scenari di vetrina relativi alla navigazione del catalogo, alla ricerca (rapida e avanzata) e alla navigazione su più livelli.
- Le operazioni di gestione dei prodotti nell’amministratore subiscono un rallentamento significativo, che può causare timeout.
- È possibile bloccare la funzionalità Azioni di massa prodotto.
- I tempi di ricreazione degli indici per i cataloghi di medie e grandi dimensioni non possono essere eseguiti su base giornaliera a causa dei lunghi tempi di esecuzione.

Configurazione di molti **opzioni attributo** può influire sulle prestazioni del sito nei seguenti modi:

- Lunghi tempi di richiesta e rendering sui dettagli prodotto (PDP) e sulle pagine di categorie contenenti prodotti complessi.
- Il tempo di risposta per le operazioni di salvataggio dei prodotti dell’amministratore aumenta oltre gli obiettivi di prestazioni ottimali.
- Aumento del tempo di rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Informazioni aggiuntive

- [Panoramica degli attributi del prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Set di attributi](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutorial di personalizzazione > Personalizza modulo di creazione prodotto](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

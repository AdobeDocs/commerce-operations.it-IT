---
title: Best practice per la configurazione degli attributi di prodotto
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di attributi di prodotto, opzioni di attributi e set di attributi
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Best practice per la configurazione degli attributi di prodotto

- Per ottenere le migliori prestazioni, non configurare più del numero massimo consigliato di attributi di prodotto o opzioni di attributi di prodotto.

- **Attributi del prodotto**—
   - Per Adobe Commerce versione 2.3.x e da 2.4.0 a 2.4.1-p1, configura non più di 500 attributi
   - Per Adobe Commerce versione 2.4.2 e successive, configura fino a 1500 attributi di prodotto
- **Opzioni attributo prodotto**- Configura fino a 100 opzioni di attributi per ogni attributo
- **Set di attributi di prodotto**- Configura un massimo di 1000 set di attributi _

>[!NOTE]
>
>Gli attributi del prodotto specificano le funzioni che si applicano globalmente a tutti i prodotti. Le opzioni di attributo del prodotto sono personalizzazioni per specificare le funzioni applicabili a prodotti specifici.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione del numero di attributi di prodotto

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati dei prodotti nella vetrina:

- Utilizza diversi modelli di prodotto (set di attributi) per diversi prodotti.
- Utilizzo di opzioni personalizzate e prodotti complessi per la gestione delle varianti
- Riduci al minimo il numero di attributi ricercabili.
- Rimuovere le proprietà del prodotto non utilizzate.
- Archiviare e gestire gli attributi non relativi al commercio nei sistemi di gestione dei prodotti esterni (PMS).

## Riduci il numero di opzioni attributo del prodotto

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati dei prodotti nella vetrina:

- Utilizza diversi meccanismi di variazione per creare prodotti: prodotti complessi, opzioni personalizzate come origine di varianti di prodotto.
- Crea modelli di prodotto specifici con attributi e opzioni di targeting per evitare modelli di prodotto e contenitori di opzioni generalizzati.
- Gestisci un elenco di opzioni di attributi effettive.
- Gestisci le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

## Riduzione del numero di set di attributi di prodotto

Rimuovere i set di attributi di prodotto non utilizzati utilizzando MySQL.

### Verifica la configurazione del set di attributi

1. [Connessione al database del sito](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Trovare il numero di set di attributi utilizzando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Rimuovi eventuali set di attributi non utilizzati.

## Effetti potenziali sulle prestazioni

Configurazione di molti **attributi del prodotto** aumenta le dimensioni del modello di prodotto per ciascun prodotto (struttura EAV) e la quantità di dati da recuperare. Questo aumento influisce sulle operazioni nei seguenti modi:

- Aumento del traffico delle query SQL relativo al recupero dei dati EAV e alla quantità di dati elaborati che si traduce in una riduzione del throughput del database
- Incremento significativo delle dimensioni degli indici Adobe Commerce e dell’indice di ricerca full-text
- Raggiungere i limiti rigidi di MySQL durante la creazione di un indice FLAT per i modelli di prodotto di grandi dimensioni e l&#39;impossibilità di utilizzarlo

L’aumento dei dati di prodotto e delle dimensioni dell’indice può influire sulle prestazioni del sito nei seguenti modi:

- Maggiore tempo di risposta per la maggior parte degli scenari di vetrina relativi alla navigazione nel catalogo, alla ricerca (rapida e avanzata) e alla navigazione a più livelli.
- Le operazioni di gestione dei prodotti in Admin rallentano in modo significativo, il che può causare timeout.
- La funzionalità Azioni di massa del prodotto può essere bloccata.
- Il tempo di ricostruzione dell’indice per i cataloghi di medie e grandi dimensioni non può essere eseguito su base giornaliera a causa di lunghi tempi di esecuzione.

Configurazione di molti **opzioni attributo** può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di richiesta e rendering lunghi sulle pagine dei dettagli del prodotto (PDP) e delle categorie contenenti prodotti complessi.
- I tempi di risposta delle operazioni di salvataggio dei prodotti amministratore aumentano al di sopra degli obiettivi prestazionali ottimali.
- Aumento del tempo di rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Informazioni aggiuntive

- [Panoramica degli attributi del prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Set di attributi](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Esercitazioni sulla personalizzazione > Personalizza modulo di creazione del prodotto](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)


---
title: Gestire gli indicizzatori
description: Vedi esempi di come visualizzare e gestire gli indicizzatori Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Gestire gli indicizzatori

{{file-system-owner}}

Per visualizzare un elenco di tutti gli indicizzatori:

```bash
bin/magento indexer:info
```

L’elenco viene visualizzato come segue:

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> I commercianti di Adobe Commerce che utilizzano Live Search, Catalog Service o Product Recommendations possono utilizzare [Indicizzazione dei prezzi basata su SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Visualizza stato indicizzatore

Utilizzare questo comando per visualizzare lo stato di tutti gli indicizzatori o di indicizzatori specifici. Ad esempio, scopri se un indicizzatore deve essere reindicizzato.

Opzioni comando:

```bash
bin/magento indexer:status [indexer]
```

Dove `[indexer]` è un elenco di indicizzatori separato da spazi. Ometti `[indexer]` per visualizzare lo stato di tutti gli indici.

Risultato di esempio:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Reindicizza

Utilizzare questo comando per reindicizzare tutti gli indicizzatori o gli indicizzatori selezionati una sola volta.

>[!INFO]
>
>Questo comando reindicizza una sola volta. Per mantenere gli indicizzatori aggiornati, è necessario impostare un [lavoro cron](../cli/configure-cron-jobs.md).

Opzioni comando:

```bash
bin/magento indexer:reindex [indexer]
```

Dove `[indexer]` è un elenco di indicizzatori separato da spazi. Ometti `[indexer]` per reindicizzare tutti gli indici.

Risultato di esempio:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>La reindicizzazione di tutti gli indicizzatori può richiedere molto tempo per i negozi con un numero elevato di prodotti, clienti, categorie e regole promozionali.

### Reindicizzazione in modalità parallela

{{php-process-control}}

Gli indicizzatori sono con ambito e multithread per supportare la reindicizzazione in modalità parallela. Viene eseguito in parallelo dalla dimensione dell’indicizzatore su più thread, riducendo il tempo di elaborazione.

In questo contesto: `dimension` è il campo di applicazione della reindicizzazione, ad esempio `website` o solo uno specifico `customer_group`.

La parallelizzazione degli indici influisce solo sugli indicizzatori con ambito, il che significa che Commerce divide i dati in più tabelle utilizzando l’indicizzatore come ambito anziché mantenere tutti i dati in un’unica tabella.

Puoi eseguire i seguenti indici in modalità parallela:

- `Catalog Search Fulltext` può essere affiancato dalle visualizzazioni dello store.
- `Category Product` può essere affiancato dalle visualizzazioni dello store.
- `Catalog Price` può essere affiancato da siti web e gruppi di clienti.
- `Catalog Permissions` possono essere affiancati dai gruppi di clienti.

>[!INFO]
>
>Per impostazione predefinita, è abilitata la parallelizzazione per il prodotto full-text e per la categoria di ricerca nel catalogo.

Per utilizzare la parallelizzazione, impostare una delle modalità di dimensione disponibili per l&#39;indicizzatore prezzo prodotto:

- `none` (impostazione predefinita)
- `website`
- `customer_group`
- `website_and_customer_group`

Ad esempio, per impostare la modalità per sito Web:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Per utilizzare la parallelizzazione per le autorizzazioni del catalogo, imposta una delle modalità di dimensioni disponibili per l’indicizzatore delle autorizzazioni del catalogo:

- `none` (impostazione predefinita)
- `customer_group`

Oppure per controllare la modalità corrente:

```bash
bin/magento indexer:show-dimensions-mode
```

Per reindicizzare in modalità parallela, esegui il comando reindicizza utilizzando la variabile di ambiente `MAGE_INDEXER_THREADS_COUNT`o aggiungere una variabile di ambiente al `env.php` file. Questa variabile imposta il numero di thread per la reindicizzazione.

Ad esempio, il comando seguente esegue `Catalog Search Fulltext` indicizzatore su tre thread:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Reimposta indicizzatore

Utilizzare questo comando per invalidare lo stato di tutti gli indicizzatori o di indicizzatori specifici.

Opzioni comando:

```bash
bin/magento indexer:reset [indexer]
```

Dove ```[indexer]``` è un elenco di indicizzatori separato da spazi. Ometti `[indexer]` per annullare la validità di tutti gli indicizzatori.

Risultato di esempio:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Configurare gli indici

Utilizzare questo comando per impostare le opzioni di indicizzazione seguenti:

- **Aggiorna al salvataggio (`realtime`)**: i dati indicizzati vengono aggiornati quando viene apportata una modifica in Admin. Ad esempio, l’indice dei prodotti di categoria viene reindicizzato dopo l’aggiunta dei prodotti a una categoria in Admin. Questa è l&#39;impostazione predefinita.
- **Aggiorna per pianificazione (`schedule`)**: i dati vengono indicizzati in base alla pianificazione impostata dal processo cron.

[Ulteriori informazioni sull’indicizzazione](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visualizza la configurazione corrente

Per visualizzare la configurazione corrente dell&#39;indicizzatore:

```bash
bin/magento indexer:show-mode [indexer]
```

Dove `[indexer]` è un elenco di indicizzatori separato da spazi. Ometti `[indexer]` per visualizzare tutte le modalità degli indicizzatori. Ad esempio, per visualizzare la modalità di tutti gli indicizzatori:

Risultato di esempio:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Configurare gli indici

>[!INFO]
>
>Prima di passare a una modalità di indicizzazione, si consiglia di inserire il sito Web in [manutenzione](../../installation/tutorials/maintenance-mode.md) modalità e [disabilita processi cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). In questo modo si evita di subire blocchi del database.

Per specificare la configurazione dell&#39;indicizzatore:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dove:

- `realtime`- Imposta gli indicizzatori selezionati da aggiornare al salvataggio.
- `schedule`- Imposta gli indicizzatori specificati per il salvataggio in base alla pianificazione cron.
- `indexer`- È un elenco di indicizzatori separato da spazi. Ometti `indexer` per configurare tutti gli indicizzatori allo stesso modo.

Ad esempio, per modificare solo gli indici dei prodotti e delle categorie di prodotti per l&#39;aggiornamento in base alla programmazione, immettere:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Risultato di esempio:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

I trigger del database relativi agli indicizzatori vengono aggiunti quando la modalità di indicizzazione è impostata su `schedule` e viene rimosso quando la modalità indicizzatore è impostata su `realtime`. Se i trigger non sono presenti nel database mentre gli indicizzatori sono impostati su `schedule`, modifica gli indicizzatori in `realtime` e quindi riportarli a `schedule`. In questo modo vengono ripristinati i trigger.

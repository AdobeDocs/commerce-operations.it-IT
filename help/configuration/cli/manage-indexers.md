---
title: Gestire gli indici
description: Vedi esempi su come visualizzare e gestire gli indici Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: beee479caeb4145d759c105012ffc8b6b55a6e39
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Gestire gli indici

{{file-system-owner}}

Per visualizzare un elenco di tutti gli indici:

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
> I commercianti Adobe Commerce che utilizzano Live Search, Catalog Service o Product Recommendations hanno la possibilità di utilizzare [Indicizzazione dei prezzi basata su SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-index/index.html).

## Visualizza lo stato dell&#39;indicizzatore

Utilizzare questo comando per visualizzare lo stato di tutti gli indici o indici specifici. Ad esempio, scopri se è necessario reindicizzare un indicizzatore.

Opzioni di comando:

```bash
bin/magento indexer:status [indexer]
```

Dove `[indexer]` è un elenco di indici separati da spazi. Ometti `[indexer]` per visualizzare lo stato di tutti gli indici.

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

## Reindicizzazione

Utilizzare questo comando per reindicizzare tutti gli indici o selezionati una sola volta.

>[!INFO]
>
>Questo comando reindicizza una sola volta. Per mantenere gli indici aggiornati, è necessario impostare un [cron](../cli/configure-cron-jobs.md).

Opzioni di comando:

```bash
bin/magento indexer:reindex [indexer]
```

Dove `[indexer]` è un elenco di indici separati da spazi. Ometti `[indexer]` reindicizzare tutti gli indici.

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
>La reindicizzazione di tutti gli indici può richiedere molto tempo per i negozi con un gran numero di prodotti, clienti, categorie e regole promozionali.

### Reindicizzazione in modalità parallela

Gli indicizzatori sono delimitati e multithread per supportare la reindicizzazione in modalità parallela. Assegna un parallelismo in base alla dimensione dell’indicizzatore ed esegue più thread, riducendo il tempo di elaborazione.

In tale contesto, `dimension` è l&#39;ambito di applicazione della reindicizzazione, ad esempio a `website` o semplicemente `customer_group`.

La parallelizzazione degli indici influisce solo sugli indici con ambito, il che significa che Commerce suddivide i dati in più tabelle utilizzando l’indicizzatore come ambito, invece di mantenere tutti i dati in un’unica tabella.

Puoi eseguire i seguenti indici in modalità parallela:

- `Catalog Search Fulltext` può essere affiancato dalle viste del negozio.
- `Category Product` può essere affiancato dalle viste del negozio.
- `Catalog Price` può essere affiancato da siti web e gruppi di clienti.
- `Catalog Permissions` può essere affiancato dai gruppi di clienti.

>[!INFO]
>
>Per impostazione predefinita, la parallelizzazione per la ricerca nel catalogo per il testo completo e il prodotto per categoria è abilitata.

Per utilizzare la parallelizzazione, impostare una delle modalità di dimensioni disponibili per l&#39;indicizzatore del prezzo del prodotto:

- `none` (predefinito)
- `website`
- `customer_group`
- `website_and_customer_group`

Ad esempio, per impostare la modalità per sito Web:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Per utilizzare la parallelizzazione per le autorizzazioni Catalogo, impostare una delle modalità di dimensioni disponibili per l&#39;indicizzatore Autorizzazioni catalogo:

- `none` (predefinito)
- `customer_group`

Oppure per controllare la modalità corrente:

```bash
bin/magento indexer:show-dimensions-mode
```

Per reindicizzare in modalità parallela, esegui il comando reindicizzazione utilizzando la variabile di ambiente `MAGE_INDEXER_THREADS_COUNT`oppure aggiungi una variabile di ambiente al `env.php` file. Questa variabile imposta il numero di thread per l&#39;elaborazione del reindicizzazione.

Ad esempio, il comando seguente esegue il comando `Catalog Search Fulltext` indicizzatore tra tre thread:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Ripristina indicizzatore

Utilizzare questo comando per annullare la validità dello stato di tutti gli indici o indici specifici.

Opzioni di comando:

```bash
bin/magento indexer:reset [indexer]
```

Dove ```[indexer]``` è un elenco di indici separati da spazi. Ometti `[indexer]` per annullare la validità di tutti gli indici.

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

## Configurare gli indicizzatori

Utilizzare questo comando per impostare le seguenti opzioni di indicizzazione:

- **Aggiorna al salvataggio (`realtime`)**: I dati indicizzati vengono aggiornati quando viene apportata una modifica nell’amministratore. Ad esempio, l’indice dei prodotti della categoria viene reindicizzato dopo l’aggiunta dei prodotti a una categoria nell’amministratore. Questa è l’impostazione predefinita.
- **Aggiorna per pianificazione (`schedule`)**: I dati vengono indicizzati in base alla pianificazione impostata dal lavoro cron.

[Ulteriori informazioni sull&#39;indicizzazione](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visualizza la configurazione corrente

Per visualizzare la configurazione dell&#39;indicizzatore corrente:

```bash
bin/magento indexer:show-mode [indexer]
```

Dove `[indexer]` è un elenco di indici separati da spazi. Ometti `[indexer]` per visualizzare tutte le modalità degli indicizzatori. Ad esempio, per visualizzare la modalità di tutti gli indici:

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

### Configurare gli indicizzatori

>[!INFO]
>
>Prima di cambiare le modalità di indicizzazione, si consiglia di inserire il sito Web in [manutenzione](../../installation/tutorials/maintenance-mode.md) modalità e [disattivare cron jobs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). In questo modo non si verificano blocchi del database.

Per specificare la configurazione dell&#39;indicizzatore:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dove:

- `realtime`- Imposta gli indici selezionati da aggiornare al salvataggio.
- `schedule`- Imposta gli indicizzatori specificati da salvare in base alla pianificazione cron.
- `indexer`- È un elenco di indici separati da spazi. Ometti `indexer` per configurare tutti gli indici nello stesso modo.

Ad esempio, per modificare solo gli indici dei prodotti e delle categorie di prodotti della categoria da aggiornare in base alla pianificazione, immettere:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Risultato di esempio:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Gli attivatori del database relativi agli indicizzatori vengono aggiunti quando la modalità dell&#39;indicizzatore è impostata su `schedule` e rimossi quando la modalità di indicizzazione è impostata su `realtime`. Se i trigger mancano nel database mentre gli indicizzatori sono impostati su `schedule`, modifica gli indici in `realtime` e poi cambiarli in `schedule`. Questo reimposta i trigger.

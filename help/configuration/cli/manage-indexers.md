---
title: Gestire gli indicizzatori
description: Consulta alcuni esempi su come visualizzare e gestire gli indicizzatori Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Gestire gli indicizzatori

{{file-system-owner}}

Per visualizzare un elenco di tutti gli indicizzatori:

```bash
bin/magento indexer:info
```

L’elenco viene visualizzato come segue:

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> I commercianti di Adobe Commerce che utilizzano Live Search, Catalog Service o Product Recommendations possono utilizzare l&#39;indicizzazione dei prezzi basata su [SaaS](https://experienceleague.adobe.com/it/docs/commerce/price-indexer/price-indexing).

## Visualizza stato indicizzatore

Utilizzare questo comando per visualizzare lo stato di tutti gli indicizzatori o di indicizzatori specifici. Ad esempio, scopri se un indicizzatore deve essere reindicizzato.

Opzioni comando:

```bash
bin/magento indexer:status [indexer]
```

Dove `[indexer]` è un elenco separato da spazi di indicizzatori. Ometti `[indexer]` per visualizzare lo stato di tutti gli indicizzatori.

Risultato di esempio:

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## Reindicizza

Utilizzare questo comando per reindicizzare tutti gli indicizzatori o gli indicizzatori selezionati una sola volta.

>[!INFO]
>
>Questo comando reindicizza una sola volta. Per mantenere aggiornati gli indicizzatori, è necessario impostare un [processo cron](../cli/configure-cron-jobs.md).

Opzioni comando:

```bash
bin/magento indexer:reindex [indexer]
```

Dove `[indexer]` è un elenco separato da spazi di indicizzatori. Ometti `[indexer]` per reindicizzare tutti gli indici.

Risultato di esempio:

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>La reindicizzazione di tutti gli indicizzatori può richiedere molto tempo per i negozi con un numero elevato di prodotti, clienti, categorie e regole promozionali.

### Reindicizzazione in modalità parallela

{{php-process-control}}

Gli indicizzatori sono con ambito e multithread per supportare la reindicizzazione in modalità parallela. Viene eseguito in parallelo dalla dimensione dell’indicizzatore su più thread, riducendo il tempo di elaborazione.

In questo contesto, `dimension` è l&#39;ambito della reindicizzazione, ad esempio un `website` o solo un `customer_group` specifico.

La parallelizzazione degli indici ha effetto solo sugli indicizzatori con ambito, il che significa che Commerce divide i dati in più tabelle utilizzando l&#39;indicizzatore come ambito anziché mantenere tutti i dati in un&#39;unica tabella.

Puoi eseguire i seguenti indici in modalità parallela:

- `Catalog Search Fulltext` può essere affiancato dalle visualizzazioni dello store.
- `Category Product` può essere affiancato dalle visualizzazioni dello store.
- `Catalog Price` può essere affiancato da siti Web e gruppi di clienti.
- `Catalog Permissions` può essere affiancato dai gruppi di clienti.

>[!INFO]
>
>Per impostazione predefinita, è abilitata la parallelizzazione per il prodotto full-text e per la categoria di ricerca nel catalogo.

Per utilizzare la parallelizzazione, impostare una delle modalità di dimensione disponibili per l&#39;indicizzatore prezzo prodotto:

- `none` (predefinito)
- `website`
- `customer_group`
- `website_and_customer_group`

Ad esempio, per impostare la modalità per sito Web:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Per utilizzare la parallelizzazione per le autorizzazioni del catalogo, imposta una delle modalità di dimensioni disponibili per l’indicizzatore delle autorizzazioni del catalogo:

- `none` (predefinito)
- `customer_group`

Oppure per controllare la modalità corrente:

```bash
bin/magento indexer:show-dimensions-mode
```

Per reindicizzare in modalità parallela, eseguire il comando reindicizza utilizzando la variabile di ambiente `MAGE_INDEXER_THREADS_COUNT` oppure aggiungere una variabile di ambiente al file `env.php`. Questa variabile imposta il numero di thread per la reindicizzazione.

Il comando seguente, ad esempio, esegue l&#39;indicizzatore `Catalog Search Fulltext` su tre thread:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Reimposta indicizzatore

Utilizzare questo comando per invalidare lo stato di tutti gli indicizzatori o di indicizzatori specifici.

Opzioni comando:

```bash
bin/magento indexer:reset [indexer]
```

Dove ```[indexer]``` è un elenco separato da spazi di indicizzatori. Ometti `[indexer]` per annullare la validità di tutti gli indicizzatori.

Risultato di esempio:

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## Configurare gli indici

Utilizzare questo comando per impostare le opzioni di indicizzazione seguenti:

- **Aggiornamento al salvataggio (`realtime`)**: i dati indicizzati vengono aggiornati quando viene apportata una modifica nell&#39;amministratore. Ad esempio, l’indice dei prodotti di categoria viene reindicizzato dopo l’aggiunta dei prodotti a una categoria in Admin.
- **Aggiornamento in base alla pianificazione (`schedule`)**: i dati sono indicizzati in base alla pianificazione impostata dal processo cron.

[Ulteriori informazioni sull&#39;indicizzazione](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visualizza la configurazione corrente

Per visualizzare la configurazione corrente dell&#39;indicizzatore:

```bash
bin/magento indexer:show-mode [indexer]
```

Dove `[indexer]` è un elenco separato da spazi di indicizzatori. Ometti `[indexer]` per visualizzare tutte le modalità degli indicizzatori. Ad esempio, per visualizzare la modalità di tutti gli indicizzatori:

Risultato di esempio:

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### Impostare la modalità di indicizzazione

>[!IMPORTANT]
>
>Il comportamento dell&#39;indicizzatore [!DNL Customer Grid] è stato modificato nella versione 2.4.8:
>
>- **Prima della versione 2.4.8**: l&#39;indicizzatore [!DNL Customer Grid] può essere reindicizzato solo utilizzando l&#39;opzione [!UICONTROL Update on Save] e non supporta l&#39;opzione [!UICONTROL Update by Schedule].
>
>   Utilizza il seguente comando per impostare questo indicizzatore da aggiornare al salvataggio:
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 e versioni successive**: l&#39;indicizzatore [!DNL Customer Grid] supporta sia la modalità [!UICONTROL Update on Save] che la modalità [!UICONTROL Update by Schedule]. Impostazione predefinita: [!UICONTROL Update by Schedule].
>
>Consulta [Best practice per la configurazione dell&#39;indicizzatore](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) nella _Playbook di implementazione_.

>[!INFO]
>
>Prima di cambiare modalità di indicizzazione, impostare il sito Web sulla modalità [manutenzione](../../installation/tutorials/maintenance-mode.md) e [disabilitare i processi cron](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property). In questo modo non si verificheranno blocchi del database.

Per specificare la configurazione dell&#39;indicizzatore:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Dove:

- `realtime` - Imposta gli indici selezionati da aggiornare al momento del salvataggio.
- `schedule` - Imposta gli indicizzatori specificati per il salvataggio in base alla pianificazione cron.
- `indexer` - Elenco di indicizzatori separato da spazi. Ometti `indexer` per configurare tutti gli indicizzatori allo stesso modo.

Ad esempio, per modificare solo gli indici dei prodotti e delle categorie di prodotti per l&#39;aggiornamento in base alla programmazione, immettere:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Risultato di esempio:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

I trigger del database relativi agli indicizzatori vengono aggiunti quando la modalità indicizzatore è impostata su `schedule` e rimossi quando la modalità indicizzatore è impostata su `realtime`. Se nel database mancano i trigger mentre gli indicizzatori sono impostati su `schedule`, modificare gli indicizzatori in `realtime` e quindi riportarli in `schedule`. In questo modo vengono ripristinati i trigger.

### Imposta stato indicizzatore

Comando `bin/magento indexer:set-status` introdotto in Adobe Commerce 2.4.7. Consente agli amministratori di modificare lo stato operativo di uno o più indicizzatori, ottimizzando le prestazioni del sistema durante operazioni estese come l’importazione di dati, aggiornamenti o manutenzione.

Sintassi del comando:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Dove:

- `invalid` - Contrassegna gli indicizzatori come non aggiornati, richiedendo la reindicizzazione nella successiva esecuzione cron, a meno che non vengano sospesi.
- `suspended` - Interrompe temporaneamente gli aggiornamenti automatici attivati da cron per gli indicizzatori. Questo stato si applica sia alla modalità in tempo reale che alla modalità di pianificazione, garantendo che gli aggiornamenti automatici vengano messi in pausa durante le operazioni intensive.
- `valid` - Indica che i dati dell&#39;indicizzatore sono aggiornati, senza necessità di reindicizzazione.
- `indexer` - Elenco di indicizzatori separato da spazi. Ometti `indexer` per configurare tutti gli indicizzatori allo stesso modo.

Ad esempio, per sospendere indicizzatori specifici, immettere:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Risultato di esempio:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Gestione dello stato dell’indicizzatore sospeso

Quando un indicizzatore è impostato sullo stato `suspended`, influisce principalmente sulla reindicizzazione automatica e sugli aggiornamenti delle viste materializzate. Ecco una breve panoramica:

**Reindicizzazione ignorata**: il sistema ignora la reindicizzazione automatica per gli indicizzatori `suspended` e per tutti gli indicizzatori che condividono lo stesso `shared_index`. Questo approccio consente di risparmiare le risorse di sistema evitando la reindicizzazione dei dati relativi ai processi sospesi.

**Aggiornamenti delle viste materializzate ignorati**: analogamente alla reindicizzazione, il sistema mette in pausa anche gli aggiornamenti alle viste materializzate correlate agli indicizzatori `suspended` o ai relativi indici condivisi. Questa pausa riduce ulteriormente il carico del sistema durante i periodi di sospensione.

>[!INFO]
>
>Il comando `indexer:reindex` reindicizza tutti gli indicizzatori, inclusi quelli contrassegnati come `suspended`, rendendolo utile per gli aggiornamenti manuali quando si mettono in pausa quelli automatici.

>[!IMPORTANT]
>
>La modifica dello stato di un indicizzatore in `valid` da `suspended` o `invalid` richiede cautela. Questa azione può causare il deterioramento delle prestazioni in caso di accumulo di dati non indicizzati.
>
>È fondamentale assicurarsi che tutti i dati siano indicizzati accuratamente prima di aggiornare manualmente lo stato a `valid` per mantenere le prestazioni del sistema e l&#39;integrità dei dati.

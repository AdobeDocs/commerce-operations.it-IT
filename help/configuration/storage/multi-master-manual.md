---
title: Configurare manualmente i database master
description: Consulta le istruzioni sulla configurazione manuale della soluzione di database suddivisi.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---


# Configurare manualmente i database master

{#ee-only}

{{deprecate-split-db}}

Se l’applicazione Commerce è già in produzione o se hai già installato codice o componenti personalizzati, potrebbe essere necessario configurare manualmente i database suddivisi. Prima di continuare, contatta il supporto Adobe Commerce per verificare se è necessario nel tuo caso.

La suddivisione manuale dei database comporta:

- Crea il [pagamento](https://glossary.magento.com/checkout) e le banche dati del sistema di gestione degli ordini (OMS)
- Esegui una serie di script SQL che:

   - Elimina chiavi esterne
   - Esegui il backup delle tabelle del database delle vendite e dei preventivi
   - Spostare le tabelle dal database principale ai database delle vendite e dei preventivi

>[!WARNING]
>
>Se un codice personalizzato utilizza JOINs con tabelle nei database delle vendite e delle quotazioni, l&#39;utente _impossibile_ utilizzare database divisi. In caso di dubbi, contatta gli autori di eventuali codici personalizzati o estensioni per assicurarti che il loro codice non utilizzi JOIN.

In questo argomento vengono utilizzate le seguenti convenzioni di denominazione:

- Il nome del database principale è `magento` e il nome utente e la password sono entrambi `magento`
- Il nome del database delle virgolette è `magento_quote` e il nome utente e la password sono entrambi `magento_quote`

   Il database delle quotazioni è anche denominato _pagamento_ database.

- Il nome del database di vendita è `magento_sales` e il nome utente e la password sono entrambi `magento_sales`

   La banca dati sulle vendite è anche denominata banca dati OMS.

>[!INFO]
>
>Questa guida presuppone che tutti e tre i database si trovino sullo stesso host dell&#39;applicazione Commerce. Tuttavia, spetta a te scegliere dove individuare i database e il loro nome. Speriamo che i nostri esempi rendano le istruzioni più facili da seguire.

## Backup del sistema Commerce

L&#39;Adobe consiglia vivamente di eseguire il backup del database e del file system correnti in modo da poterli ripristinare in caso di problemi durante il processo.

**Per eseguire il backup del sistema**:

1. Accedi al tuo server Commerce come o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Immetti i seguenti comandi:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Procedi alla sezione successiva.

## Configurare database master aggiuntivi

Questa sezione illustra come creare istanze di database per le vendite e [preventivo](https://glossary.magento.com/quote) tabelle.

**Creazione di banche dati sulle vendite e sulle quotazioni OMS**:

1. Accedi al server di database come qualsiasi utente.
1. Immettere il comando seguente per accedere a un prompt dei comandi MySQL:

   ```bash
   mysql -u root -p
   ```

1. Immettere MySQL `root` password dell&#39;utente quando richiesto.
1. Immettere i seguenti comandi nell&#39;ordine mostrato per creare istanze di database denominate `magento_quote` e `magento_sales` con gli stessi nomi utente e password:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Invio `exit` per uscire dal prompt dei comandi.

1. Verificare i database, uno alla volta:

   database delle virgolette:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Se viene visualizzato il monitoraggio MySQL, il database è stato creato correttamente. Se viene visualizzato un errore, ripetere i comandi precedenti.

1. Procedi alla sezione successiva.

## Configurare il database delle vendite

In questa sezione viene illustrato come creare ed eseguire script SQL che alterano le tabelle del database e consentono di eseguire il backup dei dati di tali tabelle.

I nomi delle tabelle del database di vendita iniziano con:

- `salesrule_`
- `sales_`
- `magento_sales_`
- La `magento_customercustomattributes_sales_flat_order` anche la tabella è interessata

>[!INFO]
>
>Questa sezione contiene script con nomi di tabella di database specifici. Se hai eseguito personalizzazioni o se desideri visualizzare un elenco completo delle tabelle prima di eseguire azioni su di esse, consulta [Script di riferimento](#reference-scripts).

Per ulteriori informazioni, consulta:

- [Crea script SQL del database di vendita](#create-sales-database-sql-scripts)
- [Backup dei dati di vendita](#back-up-sales-data)

### Crea script SQL del database di vendita

Creare i seguenti script SQL in un percorso accessibile dall&#39;utente con cui si effettua l&#39;accesso al server Commerce. Ad esempio, se esegui l&#39;accesso o esegui comandi come `root`, è possibile creare gli script nel `/root/sql-scripts` directory.

#### Rimuovi chiavi esterne

Questo script rimuove dal database di vendita le chiavi esterne che fanno riferimento a tabelle non di vendita.

Crea il seguente script e assegnagli un nome come `1_foreign-sales.sql`. Sostituisci `<your main DB name>` con il nome del database.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Configurare il database delle vendite

Esegui lo script precedente:

1. Accedi al database MySQL come `root` o utente amministrativo:

   ```bash
   mysql -u root -p
   ```

1. Alla `mysql>` prompt, esegui lo script come segue:

   ```shell
   source <path>/<script>.sql
   ```

   Ad esempio:

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Dopo l’esecuzione dello script, immetti `exit`.

### Backup dei dati di vendita

Questa sezione illustra come eseguire il backup delle tabelle di vendita dal database Commerce principale in modo da poterle ripristinare nel database di vendite separato.

Se ti trovi al `mysql>` prompt, immettere `exit` per tornare alla shell dei comandi.

Esegui quanto segue `mysqldump` comandi, uno alla volta, dalla shell dei comandi. In ciascuna, sostituisci quanto segue:

- `<your database root username>` con il nome dell&#39;utente principale del database
- `<your database root user password>` con la password dell&#39;utente
- `<your main Commerce DB name>` con il nome del database Commerce
- `<path>` con un percorso del file system scrivibile

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Ripristina dati di vendita

Questo script ripristina i dati di vendita nel database delle offerte.

#### Requisito NDB

Se utilizzi un [Database di rete (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Converti tabelle da InnoDb in tipo NDB nei file di dump:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Rimuovi le righe con una chiave FULLTEXT dalle immagini perché le tabelle NDB non supportano FULLTEXT.

#### Ripristinare i dati

Esegui i seguenti comandi:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Dove

- `<your sales DB name>` con il nome del database di vendita.

   In questo argomento, il nome del database di esempio è `magento_sales`.

- `<root username>` con il nome utente principale MySQL
- `<root user password>` con la password dell&#39;utente
- Verificare il percorso dei file di backup creati in precedenza (ad esempio, `/var/sales.sql`)

## Configurare il database delle virgolette

Questa sezione descrive le attività necessarie per eliminare le chiavi esterne dalle tabelle del database di vendita e spostare le tabelle nel database di vendita.

>[!INFO]
>
>Questa sezione contiene script con nomi di tabella di database specifici. Se hai eseguito personalizzazioni o se desideri visualizzare un elenco completo delle tabelle prima di eseguire azioni su di esse, consulta [Script di riferimento](#reference-scripts).

I nomi delle tabelle del database del preventivo iniziano con `quote`. La `magento_customercustomattributes_sales_flat_quote` e `magento_customercustomattributes_sales_flat_quote_address` anche le tabelle sono interessate

### Elimina le chiavi esterne dalle tabelle delle virgolette

Questo script rimuove le chiavi esterne che fanno riferimento a tabelle non basate su virgolette dalle tabelle delle virgolette. Sostituisci `<your main Commerce DB name>` con il nome del database Commerce.

Crea il seguente script e assegnagli un nome come `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Esegui lo script come segue:

1. Accedere al database MySQL come utente principale o amministrativo:

   ```bash
   mysql -u root -p
   ```

1. Alla `mysql >` prompt, esegui lo script come segue:
   `source <path>/<script>.sql`

   Ad esempio:

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Dopo l’esecuzione dello script, immetti `exit`.

### Tabelle di preventivo di backup

Questa sezione illustra come eseguire il backup delle tabelle dei preventivi dal database principale e ripristinarle nel database dei preventivi.

Esegui il comando seguente da un prompt dei comandi:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### Requisito NDB

Se utilizzi un [Database di rete (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Converti tabelle da InnoDb in tipo NDB nei file di dump:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Rimuovi le righe con una chiave FULLTEXT dalle immagini perché le tabelle NDB non supportano FULLTEXT.

### Ripristinare le tabelle nel database delle virgolette

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Elimina le tabelle di vendita e di preventivo dal database

Tabelle di vendita e preventivi script dal database Commerce. Sostituisci `<your main DB name>` con il nome del database Commerce.

Crea il seguente script e assegnagli un nome come `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Esegui lo script come segue:

1. Accedere al database MySQL come utente principale o amministrativo:

   ```bash
   mysql -u root -p
   ```

1. Alla `mysql>` prompt, esegui lo script come segue:

   ```shell
   source <path>/<script>.sql
   ```

   Ad esempio:

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Dopo l’esecuzione dello script, immetti `exit`.

## Aggiorna la configurazione della distribuzione

L’ultimo passaggio nella suddivisione manuale dei database consiste nell’aggiungere informazioni sulla connessione e sulle risorse alla configurazione di distribuzione di Commerce, `env.php`.

Per aggiornare la configurazione della distribuzione:

1. Accedi al tuo server Commerce come o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Esegui il backup della configurazione di distribuzione:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Apri `<magento_root>/app/etc/env.php` in un editor di testo e aggiornalo utilizzando le linee guida illustrate nelle sezioni seguenti.

### Aggiorna connessioni database

Individua il blocco che inizia con `'default'` (4) `'connection'`) e aggiungi `'checkout'` e `'sales'` sezioni. Sostituisci i valori di esempio con i valori appropriati per il sito.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Aggiorna risorse

Individua il blocco che inizia con `'resource'` e aggiungere `'checkout'` e `'sales'` le sezioni seguenti:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Script di riferimento

Questa sezione fornisce script che è possibile eseguire per stampare un elenco completo delle tabelle interessate senza eseguire alcuna azione su di esse. È possibile utilizzarle per visualizzare le tabelle interessate prima di suddividere manualmente i database. Questa funzione può essere utile se si utilizzano estensioni che personalizzano [schema di database](https://glossary.magento.com/database-schema).

Per utilizzare questi script:

1. Crea uno script SQL con il contenuto di ogni script in questa sezione.
1. In ogni script, sostituisci `<your main DB name>` con il nome del database Commerce.

   In questo argomento, il nome del database di esempio è `magento`.

1. Esegui ogni script dal `mysql>` richiedi `source <script name>`
1. Esamina l&#39;output.
1. Copia il risultato di ogni script in un altro script SQL, rimuovendo i caratteri di barra verticale (`|`).
1. Esegui ogni script dal `mysql>` richiedi `source <script name>`.

   L’esecuzione di questo secondo script esegue le azioni nel database Commerce principale.

### Rimuovi chiavi esterne (tabelle di vendita)

Questo script rimuove dal database di vendita le chiavi esterne che fanno riferimento a tabelle non di vendita.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Rimuovi chiavi esterne (tabelle virgolette)

Questo script rimuove le chiavi esterne che fanno riferimento a tabelle non basate su virgolette dalle tabelle delle virgolette.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Tabelle di vendita ridotte

Questo script rilascia le tabelle di vendita dal database Commerce.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Tabelle a preventivo

Rilascia tutte le tabelle che iniziano con `quote_`.

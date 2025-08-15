---
title: Migrare i dati
description: Scopri come avviare la migrazione dei dati da Magento 1 a Magento 2 con  [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Migrare i dati

Prima di iniziare, effettua le seguenti operazioni di preparazione:

1. Accedi al server applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory di installazione dell&#39;applicazione o assicurarsi che sia aggiunta al sistema `PATH`.

Per ulteriori dettagli, consulta la sezione [primi passaggi](overview.md#first-steps).

## Eseguire il comando di migrazione dei dati

Per avviare la migrazione dei dati, eseguire:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall&#39;inizio. È possibile utilizzare questo argomento per testare la migrazione.

* `{<path to config.xml>}` è il percorso assoluto del file system per `config.xml`. Questo argomento è obbligatorio

In questo passaggio, [!DNL Data Migration Tool] crea tabelle e trigger aggiuntivi per le tabelle di migrazione nel database di Magento 1. Sono utilizzati nel passaggio di migrazione [incrementale/delta](delta.md). Altre tabelle contengono informazioni sui record modificati dopo l’esecuzione della migrazione finale. I trigger del database vengono utilizzati per popolare queste tabelle aggiuntive, pertanto se viene eseguita una nuova operazione sulla tabella specifica (viene aggiunto/modificato/rimosso un record), questi trigger del database salvano le informazioni sull&#39;operazione nella tabella aggiuntiva. Quando si esegue un processo di migrazione delta, [!DNL Data Migration Tool] verifica la presenza di record non elaborati nelle tabelle e migra il contenuto necessario nel database di Magento 2.

Ogni nuova tabella contiene:

* Prefisso `m2_cl`
* `INSERT`, `UPDATE`, `DELETE` trigger di evento.

Ad esempio, per `sales_flat_order` [!DNL Data Migration Tool] crea:

* Tabella `m2_cl_sales_flat_order`:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` trigger:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>[!DNL Data Migration Tool] salva l&#39;avanzamento corrente durante l&#39;esecuzione. Se si verificano errori o un intervento dell&#39;utente ne interrompe l&#39;esecuzione, lo strumento riprende l&#39;avanzamento all&#39;ultimo stato valido noto. Per forzare l&#39;esecuzione di [!DNL Data Migration Tool] dall&#39;inizio, utilizzare l&#39;argomento `--reset`. In tal caso, si consiglia di ripristinare il dump del database di Magento 2 per evitare la duplicazione dei dati migrati in precedenza.


## Possibili errori di coerenza

Durante l&#39;esecuzione, [!DNL Data Migration Tool] potrebbe segnalare incoerenze tra i database di Magento 1 e Magento 2 e visualizzare messaggi come i seguenti:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Per ulteriori informazioni e raccomandazioni, consulta la sezione [Risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360033020451) di questa guida.

## Passaggio successivo della migrazione

[Migra modifiche](delta.md)

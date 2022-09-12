---
title: Eseguire la migrazione dei dati
description: Scopri come avviare la migrazione dei dati dal Magento 1 al Magento 2 con [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Eseguire la migrazione dei dati

Prima di iniziare, procedi come segue per preparare:

1. Accedi al server delle applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).
1. Passa alla directory di installazione dell&#39;applicazione o accertati che venga aggiunta al sistema `PATH`.

Consulta la sezione [primi passi](overview.md#first-steps) per ulteriori dettagli.

## Esegui il comando di migrazione dati

Per avviare la migrazione dei dati, esegui:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-a|--auto]` è un argomento facoltativo che impedisce l’arresto della migrazione in caso di errori di controllo dell’integrità.

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. Puoi utilizzare questo argomento per testare la migrazione.

* `{<path to config.xml>}` è il percorso assoluto del file system a `config.xml`; questo argomento è obbligatorio

In questo passaggio, la [!DNL Data Migration Tool] crea tabelle e trigger aggiuntivi per le tabelle di migrazione nel database Magento 1. Vengono utilizzati nella [incrementale/delta](delta.md) passaggio di migrazione. Le tabelle aggiuntive contengono informazioni sui record modificati dopo l’esecuzione finale della migrazione. I trigger del database vengono utilizzati per compilare queste tabelle aggiuntive, quindi se viene eseguita una nuova operazione sulla tabella specifica (viene aggiunto/modificato/rimosso un record), queste informazioni di salvataggio vengono salvate nella tabella aggiuntiva. Quando eseguiamo un processo di migrazione delta, la variabile [!DNL Data Migration Tool] verifica la presenza di record non elaborati in queste tabelle ed esegue la migrazione del contenuto necessario nel database di Magento 2.

Ogni nuova tabella contiene:

* `m2_cl` prefisso
* `INSERT`, `UPDATE`, `DELETE` trigger di evento.

Ad esempio, per `sales_flat_order` la [!DNL Data Migration Tool] crea:

* `m2_cl_sales_flat_order` tabella:

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
>La [!DNL Data Migration Tool] salva l&#39;avanzamento corrente durante l&#39;esecuzione. Se gli errori o un intervento dell’utente impediscono l’esecuzione, lo strumento riprende l’avanzamento all’ultimo stato valido noto. Per forzare la [!DNL Data Migration Tool] per eseguire dall&#39;inizio, utilizza `--reset` argomento. In questo caso, ti consigliamo di ripristinare il dump del database di Magento 2 per evitare la duplicazione dei dati migrati in precedenza.


## Possibili errori di coerenza

Durante l&#39;esecuzione, il [!DNL Data Migration Tool] possono segnalare incongruenze tra i database di Magento 1 e di Magento 2 e messaggi di visualizzazione come i seguenti:

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

Consulta la sezione [Risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360033020451) per ulteriori informazioni e consigli, consulta la sezione .

## Passaggio di migrazione successivo

[Migrare le modifiche](delta.md)

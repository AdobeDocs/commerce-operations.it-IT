---
title: Prerequisiti per l’aggiornamento di Adobe Commerce per MariaDB
description: Scopri come preparare il database di Adobe Commerce per aggiornare MariaDB da una versione precedente.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Prerequisiti per l&#39;aggiornamento di MariaDB

Prima di aggiornare Adobe Commerce sull’infrastruttura cloud, potrebbe essere necessario aggiornare il software del database se si utilizza MariaDB. Ad esempio:

- Adobe Commerce 2.4.6 con MariaDB versione 10.5.1 o successiva
- Adobe Commerce 2.3.5 con MariaDB versione 10.3 o precedente

## Adobe Commerce 2.4.6

A partire da MariaDB 10.5.1, le colonne con i vecchi formati temporali sono contrassegnate con `/* mariadb-5.3 */` commento nell’output del `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE` e nella sezione `COLUMN_TYPE` colonna del `INFORMATION_SCHEMA.COLUMNS` tabella. [Consulta la documentazione di MariaDB](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce non è in grado di mappare le colonne di date su un tipo di dati corretto a causa del commento MariaDB, che potrebbe causare un comportamento imprevisto nel codice personalizzato.

Per evitare un comportamento imprevisto durante l’aggiornamento di MariaDB dalle versioni precedenti alla versione 10.6, l’Adobe consiglia di migrare le colonne al nuovo formato interno.

### Configurazione predefinita

In MariaDB 10.1.2, è stato introdotto un nuovo formato temporale da MySQL 5.6. Il `mysql56_temporal_format` variabile di sistema consente al database di convertire automaticamente il formato data precedente in quello nuovo quando viene eseguita una tabella alter o viene importato un database. Configurazione predefinita per `mysql56_temporal_format` è sempre abilitato su Adobe Commerce su infrastruttura cloud.

### Colonne data di migrazione

La query seguente mostra la tabella e le colonne interessate che devono essere migrate dopo l&#39;aggiornamento di MariaDB a 10.5.1 o versione successiva:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

La migrazione delle colonne al nuovo formato di data interno richiede la reimportazione del database o l’esecuzione di alter sulla colonna identificata con la stessa definizione di colonna. La query seguente genera le query di modifica necessarie:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>È importante migrare le colonne nel nuovo formato data interno _prima di_ distribuzione del nuovo codice per evitare comportamenti imprevisti.

## Adobe Commerce 2.3.5

L&#39;aggiornamento del servizio MariaDB sull&#39;infrastruttura cloud dalla versione 10.0 o 10.2 alla versione 10.3, 10.4 o 10.5. La versione 10.3 o successiva di MariaDB richiede che il database utilizzi il formato di riga dinamico e Adobe Commerce richiede l&#39;utilizzo del motore di archiviazione InnoDB per le tabelle. Questo articolo spiega come aggiornare il database per soddisfare i requisiti MariaDB.

Dopo aver preparato il database, invia un ticket di supporto Adobe Commerce per aggiornare la versione del servizio MariaDB nell’infrastruttura cloud prima di procedere con il processo di aggiornamento di Adobe Commerce.

### Preparare il database per l&#39;aggiornamento

Prima che il team di supporto Adobe Commerce inizi il processo di aggiornamento, preparare il database convertendo le tabelle di database:

- Converti il formato della riga da `COMPACT` a `DYNAMIC`
- Cambia il motore di archiviazione da `MyISAM` a `InnoDB`

Quando pianifichi e pianifichi la conversione, tieni presenti le seguenti considerazioni:

- Conversione da `COMPACT` a `DYNAMIC` le tabelle possono richiedere diverse ore con un database di grandi dimensioni.

- Per evitare il danneggiamento dei dati, non completare il lavoro di conversione su un sito live.

- Completa il lavoro di conversione durante un periodo di traffico ridotto sul tuo sito.

- Cambia sito in [modalità di manutenzione](../../../installation/tutorials/maintenance-mode.md) prima di eseguire i comandi per convertire le tabelle di database.

#### Converti formato riga tabella database

È possibile convertire le tabelle in un nodo del cluster. Le modifiche vengono replicate automaticamente negli altri nodi del servizio.

1. Dall’ambiente Adobe Commerce sull’infrastruttura cloud, utilizza SSH per connettersi al nodo 1.

1. Accedi a MariaDB.

1. Identificare le tabelle da convertire dal formato compatto a quello dinamico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Determina le dimensioni della tabella in modo da poter pianificare il lavoro di conversione.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   La conversione di tabelle più grandi richiede più tempo. Esaminare le tabelle e raggruppare il lavoro di conversione in base alla priorità e alla dimensione della tabella per pianificare le finestre di manutenzione necessarie.

1. Converte tutte le tabelle in formato dinamico una alla volta.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Converti formato di archiviazione tabella database

È possibile convertire le tabelle in un nodo del cluster. Le modifiche vengono replicate automaticamente negli altri nodi del servizio.

Il processo di conversione del formato di archiviazione è diverso per i progetti Adobe Commerce Starter e Adobe Commerce Pro.

- Per l&#39;architettura Starter, utilizzare MySQL `ALTER` per convertire il formato.
- Nell&#39;architettura Pro, utilizzare MySQL `CREATE` e `SELECT` comandi per creare una tabella di database con `InnoDB` e copiare i dati dalla tabella esistente nella nuova tabella. Questo metodo assicura che le modifiche vengano replicate in tutti i nodi del cluster.

**Converti formato di archiviazione tabella per progetti Adobe Commerce Pro**

1. Identificare le tabelle che utilizzano `MyISAM` archiviazione.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converti tutte le tabelle in `InnoDB` formato di archiviazione uno alla volta.

   - Rinomina la tabella esistente per evitare conflitti di nomi.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Creare una tabella che utilizza `InnoDB` archiviazione utilizzando i dati della tabella esistente.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Verifica che la nuova tabella contenga tutti i dati richiesti.

   - Eliminare la tabella originale rinominata.


**Converti formato di archiviazione tabella per progetti Adobe Commerce Starter**

1. Identificare le tabelle che utilizzano `MyISAM` archiviazione.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertire le tabelle che utilizzano `MyISAM` archiviazione in `InnoDB` archiviazione.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Verificare la conversione del database

Il giorno prima dell’aggiornamento pianificato a MariaDB versione 10.3, 10.4 o 10.6, verifica che tutte le tabelle abbiano il formato di riga e il motore di archiviazione corretti. La verifica è necessaria perché le distribuzioni del codice effettuate dopo il completamento della conversione potrebbero causare il ripristino della configurazione originale di alcune tabelle.

1. Accedi al database.

1. Verifica la presenza di tabelle che presentano ancora il `COMPACT` formato riga.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Verifica la presenza di eventuali tabelle che utilizzano ancora `MyISAM` formato di archiviazione

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Se sono state ripristinate delle tabelle, ripetere i passaggi per modificare il formato delle righe della tabella e il motore di archiviazione.

### Cambia il motore di archiviazione

Consulta [Conversione di tabelle MyISAM in InnoDB](../planning/database-on-cloud.md).

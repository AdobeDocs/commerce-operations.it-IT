---
title: Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5 per MariaDB
description: Scopri come preparare il database Adobe Commerce per l’aggiornamento da Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: bc38dd658401d3cd4c64159b1b2b2efe89979a93
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# Prerequisiti per l’aggiornamento per MariaDB

L&#39;aggiornamento da Adobe Commerce 2.3.4 o versioni precedenti a qualsiasi versione più recente richiede l&#39;aggiornamento del servizio MariaDB sull&#39;infrastruttura cloud dalla versione 10.0 o 10.2 alla versione 10.3 o 10.4. Per le tabelle, MariaDB versione 10.3 o successive richiede che il database utilizzi il formato di riga della tabella dinamica e Adobe Commerce richiede l&#39;utilizzo del motore di archiviazione InnoDB. Questo articolo spiega come aggiornare il database per conformarsi a questi requisiti MariaDB.

Dopo aver preparato il database, invia una richiesta di supporto Adobe Commerce per aggiornare la versione del servizio MariaDB sull&#39;infrastruttura cloud prima di procedere con il processo di aggiornamento Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud con Adobe Commerce versione 2.3.4 o precedente e MariaDB versione 10.0 o precedente.

## Preparare il database per l&#39;aggiornamento

Prima che il team di supporto Adobe Commerce inizi il processo di aggiornamento, preparare il database convertendo le tabelle del database:

- Converti il formato della riga da `COMPACT` a `DYNAMIC`
- Modificare il motore di archiviazione da `MyISAM` a `InnoDB`

Quando pianifichi e pianifichi la conversione, tieni presente le seguenti considerazioni:

- Conversione da `COMPACT` a `DYNAMIC` le tabelle possono richiedere diverse ore con un database di grandi dimensioni.

- Per evitare il danneggiamento dei dati, non completare il lavoro di conversione su un sito live.

- Completa il lavoro di conversione durante un periodo di traffico limitato sul sito.

- Passa al sito in [modalità di manutenzione](../../../installation/tutorials/maintenance-mode.md) prima di eseguire i comandi per convertire le tabelle del database.

### Converti formato riga tabella database

È possibile convertire le tabelle su un nodo del cluster. Le modifiche vengono replicate automaticamente negli altri nodi del servizio.

1. Dall’ambiente Adobe Commerce sull’infrastruttura cloud, utilizza SSH per connettersi al nodo 1.

1. Accedi a MariaDB.

1. Identifica le tabelle da convertire dal formato compatto a quello dinamico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Determina le dimensioni della tabella in modo da poter pianificare il lavoro di conversione.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   La conversione delle tabelle più grandi richiede più tempo. Esaminare le tabelle e creare in batch il lavoro di conversione in base alla priorità e alle dimensioni della tabella per pianificare le finestre di manutenzione richieste.

1. Convertire tutte le tabelle in formato dinamico una alla volta.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### Converti formato di archiviazione tabella database

È possibile convertire le tabelle su un nodo del cluster. Le modifiche vengono replicate automaticamente negli altri nodi del servizio.

Il processo di conversione del formato di archiviazione è diverso per i progetti Adobe Commerce Starter e Adobe Commerce Pro.

- Per l&#39;architettura Starter, utilizzare MySQL `ALTER` per convertire il formato.
- Nell&#39;architettura Pro, utilizzare MySQL `CREATE` e `SELECT` comandi per creare una tabella di database con `InnoDB` archiviare e copiare i dati dalla tabella esistente nella nuova tabella. Questo metodo assicura che le modifiche vengano replicate in tutti i nodi del cluster.

**Conversione del formato di storage delle tabelle per i progetti Adobe Commerce Pro**

1. Identificare le tabelle che utilizzano `MyISAM` archiviazione.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Converti tutte le tabelle in `InnoDB` il formato di storage uno alla volta.

   - Rinominare la tabella esistente per evitare conflitti di nomi.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Creare una tabella che utilizza `InnoDB` archiviazione utilizzando i dati della tabella esistente.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Verifica che la nuova tabella contenga tutti i dati richiesti.

   - Eliminare la tabella originale rinominata.


**Conversione del formato di archiviazione della tabella per i progetti Adobe Commerce Starter**

1. Identificare le tabelle che utilizzano `MyISAM` archiviazione.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Conversione di tabelle utilizzate `MyISAM` archiviazione su `InnoDB` archiviazione.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Verificare la conversione del database

Il giorno prima dell&#39;aggiornamento pianificato a MariaDB versione 10.2, verifica che tutte le tabelle abbiano il formato riga e il motore di archiviazione corretti. È necessaria una verifica perché le distribuzioni del codice effettuate dopo il completamento della conversione potrebbero causare il ripristino della configurazione originale di alcune tabelle.

1. Accedi al tuo database.

1. Controlla eventuali tabelle che contengono ancora il `COMPACT` formato riga.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Controlla eventuali tabelle che utilizzano ancora `MyISAM` formato di archiviazione

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Se sono state ripristinate tabelle, ripetere i passaggi per modificare il formato delle righe della tabella e il motore di archiviazione.

## Modificare il motore di storage

Vedi [Converti tabelle MyISAM in InnoDB](../planning/database-on-cloud.md).

## Informazioni aggiuntive

- [Best practice per il database per Adobe Commerce sull’infrastruttura cloud](../planning/database-on-cloud.md)
- [Aggiornamento di MariaDB dalla 10.0 alla 12.0 per Adobe Commerce su Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)


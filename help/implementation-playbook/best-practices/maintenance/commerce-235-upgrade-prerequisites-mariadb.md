---
title: Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5 per MariaDB
description: Scopri come preparare il database Adobe Commerce per l’aggiornamento da Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5

Questo articolo spiega come preparare il database durante l&#39;aggiornamento ad Adobe Commerce 2.3.5 dalla versione 2.3.4 o precedente.

Questo aggiornamento richiede che il team di supporto aggiorni MariaDB sull&#39;infrastruttura cloud da MariaDB 10.0 a 10.2 per soddisfare i requisiti per Adobe Commerce . Adobe Commerce versione 2.3.5 e successive.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud con Adobe Commerce versione 2.3.4 o precedente e MariaDB versione 10.0 o precedente.

## Preparare il database per l&#39;aggiornamento

Prima che il team di supporto Adobe Commerce inizi il processo di aggiornamento, devi preparare il database convertendo il formato per tutte le tabelle da `COMPACT` a `DYNAMIC`. È inoltre necessario convertire il tipo di motore di archiviazione da `MyISAM` a `InnoDB`.

Quando si crea il piano e si pianifica la conversione del database, tenere presenti le seguenti linee guida.

- Conversione da `COMPACT` a `DYNAMIC` le tabelle possono richiedere diverse ore con un database di grandi dimensioni.

- Per evitare il danneggiamento dei dati, non eseguire la conversione quando il sito è attivo.

- Completa il lavoro di conversione durante un periodo di traffico limitato sul sito.

- Passa al sito in [modalità di manutenzione](../../../installation/tutorials/maintenance-mode.md) prima di eseguire `ALTER` comandi.

### Converti tabelle database

È possibile convertire le tabelle su un nodo del cluster. Le modifiche verranno replicate negli altri nodi core del cluster.

1. Dall’ambiente Adobe Commerce sull’infrastruttura cloud, utilizza SSH per connettersi al nodo 1.

1. Accedi a MariaDB.

1. Converti il formato della tabella.

   - Identifica le tabelle da convertire dal formato compatto a quello dinamico.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Determina le dimensioni della tabella in modo da poter pianificare il lavoro di conversione.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      La conversione delle tabelle più grandi richiede più tempo. È necessario pianificare di conseguenza, quando si prende il sito in e fuori dalla modalità di manutenzione, quali batch di tabelle per convertire in quale ordine, in modo da pianificare i tempi delle finestre di manutenzione necessarie

   - Convertire tutte le tabelle in formato dinamico una alla volta.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Aggiornare il motore di memorizzazione della tabella.

   - Identificare le tabelle che utilizzano `MyISAM` archiviazione.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Conversione di tabelle utilizzate `MyISAM` archiviazione su `InnoDB` archiviazione.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Verifica la conversione.

   Questo passaggio è necessario perché le distribuzioni del codice effettuate dopo il completamento della conversione potrebbero causare il ripristino della configurazione originale di alcune tabelle.

   - Il giorno prima dell&#39;aggiornamento pianificato a MariaDB versione 10.2, accedi al tuo database ed esegui le query per controllare il formato e il motore di archiviazione.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Se sono state ripristinate tabelle, ripetere i passaggi per modificare il formato della tabella e il motore di archiviazione.

## Informazioni aggiuntive

[Best practice per il database per Adobe Commerce sull’infrastruttura cloud](../planning/database-on-cloud.md)

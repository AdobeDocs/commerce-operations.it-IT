---
title: Linee guida di MySQL
description: Segui questi passaggi per installare e configurare MySQL e MariaDB per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Linee guida generali di MySQL

Vedi [Requisiti di sistema](../../system-requirements.md) per le versioni supportate di MySQL.

Adobe _fortemente_ consiglia di osservare il seguente standard quando si configura il database:

* Utilizzo di Adobe Commerce e Magenti Open Source [Trigger del database MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) migliorare l&#39;accesso al database durante la reindicizzazione. Questi vengono creati quando la modalità di indicizzazione è impostata su [pianificazione](../../../configuration/cli/manage-indexers.md#configure-indexers). L&#39;applicazione non supporta alcun trigger personalizzato nel database perché i trigger personalizzati possono introdurre incompatibilità con le versioni future di Adobe Commerce e Magenti Open Source.
* Acquisisci familiarità con [queste potenziali limitazioni del trigger MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) prima di continuare.
* Per migliorare la posizione di sicurezza del database, abilita [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) Modalità SQL per impedire la memorizzazione di valori di dati non validi, che potrebbero causare interazioni indesiderate nel database.
* Adobe Commerce e Magenti Open Source _not_ supporto della replica basata su istruzioni MySQL. Assicurati di utilizzare _only_ [replica basata su riga](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce e Magenti Open Source attualmente utilizzano `CREATE TEMPORARY TABLE` dichiarazioni all&#39;interno di transazioni, che sono [incompatibile](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) con le implementazioni del database si utilizza la replica basata su GTID, ad esempio [istanze di seconda generazione di Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Considera MySQL per Cloud SQL 8.0 come alternativa.

>[!NOTE]
>
>Se il server Web e il server di database si trovano su host diversi, eseguire le attività descritte in questo argomento sull&#39;host del server di database, quindi vedere [Impostare una connessione remota al database MySQL](mysql-remote.md).

## Installazione di MySQL su Ubuntu

Adobe Commerce e Magenti Open Source 2.4 richiedono un&#39;installazione pulita di MySQL 8.0. Per istruzioni sull&#39;installazione di MySQL nel computer, seguire i collegamenti riportati di seguito.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Se si prevede di importare un numero elevato di prodotti, è possibile aumentare il valore per [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) maggiore del valore predefinito, 16 MB.

>[!NOTE]
>
>Il valore predefinito si applica ad Adobe Commerce nell’infrastruttura cloud _e_ progetti locali. I clienti Adobe Commerce su infrastruttura cloud Pro devono aprire un ticket di supporto per aumentare il `max_allowed_packet` valore. Adobe Commerce su infrastruttura cloud I clienti Starter possono aumentare il valore aggiornando la configurazione nel `/etc/mysql/mysql.cnf` file.

Per aumentare il valore, apri la `/etc/mysql/mysql.cnf` in un editor di testo e individuare il valore per `max_allowed_packet`. Salva le modifiche apportate al `mysql.cnf` file, chiudere l&#39;editor di testo e riavviare MySQL (`service mysql restart`).

Per verificare facoltativamente il valore impostato, immettere il comando seguente in una `mysql>` prompt:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Allora, [Configurare l’istanza di database](#configuring-the-database-instance).

## Modifiche di MySQL 8

Per Adobe Commerce e Magenti Open Source 2.4, è stato aggiunto il supporto per MySQL 8.
Questa sezione descrive le modifiche principali apportate a MySQL 8 che gli sviluppatori devono conoscere.

### Larghezza rimossa per i tipi interi (spaziatura interna)

La specifica della larghezza di visualizzazione per i tipi di dati interi (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) è stata deprecata in MySQL 8.0.17. Le istruzioni che includono le definizioni dei tipi di dati nel loro output non mostrano più la larghezza di visualizzazione per i tipi interi, fatta eccezione per TINYINT(1). I connettori MySQL presuppongono che le colonne TINYINT(1) siano state create come colonne BOOLEAN. Questa eccezione consente loro di continuare a fare questo presupposto.

#### Esempio

Descrivi admin_user in mysql 8.19

| Campo | Tipo | Null | Chiave | Predefinito | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | SÌ |  | `NULL` |  |
| `lastname` | `varchar(32`) | SÌ |  | `NULL` |  |
| `email` | `varchar(128)` | SÌ |  | `NULL` |  |
| `username` | `varchar(40)` | SÌ | UNI | `NULL` |  |
| `password` | `varchar(255)` | NO |  | `NULL` |  |
| `created` | `timestamp` | NO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` all&#39;aggiornamento `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | SÌ |  | `NULL` |  |
| `lognum` | `smallint unsigned` | NO |  | `0` |  |

Eccetto _TINYINT(1)_, tutte le imbottiture di numeri interi (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) devono essere rimosse dalla `db_schema.xml` file.

Per ulteriori informazioni, consulta [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportamento ORDINE PREDEFINITO PER

Prima della versione 8.0, le voci venivano ordinate in base alla chiave esterna. L’ordinamento predefinito dipende dal motore utilizzato.
Specifica sempre un ordinamento se il codice dipende da un ordinamento specifico.

### Qualificatori ASC e DESC obsoleti per GRUPPO DA

A partire da MySQL 8.0.13, il `ASC` o `DESC` qualificatori per `GROUP BY` Le clausole sono state rimosse. Query su cui si era basato in precedenza `GROUP BY` l&#39;ordinamento può produrre risultati diversi dalle versioni precedenti di MySQL. Per produrre un determinato ordinamento, fornisci un `ORDER BY` clausola .

## Commerce e MySQL 8

Sono state apportate alcune modifiche ad Adobe Commerce e al Magento Open Source per supportare correttamente MySQL 8.

### Comportamento query e inserimento

Adobe Commerce e Magento Open Source hanno disabilitato il normale comportamento di convalida impostando SET SQL_MODE=&#39;&#39; in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Se la convalida è disabilitata, è possibile che MySQL tronchi i dati. In MySQL il comportamento della query è stato modificato: `Select * on my_table where IP='127.0.0.1'` non restituisce più i risultati perché l&#39;indirizzo IP viene ora visualizzato correttamente come stringa, anziché come numero intero.

## Aggiornamento da MySQL 5.7 a MySQL 8

Per aggiornare correttamente MySQL dalla versione 5.7 alla versione 8, è necessario seguire questi passaggi nell&#39;ordine seguente:

1. Aggiorna Adobe Commerce o Magenti Open Source alla versione 2.4.0. Verifica tutto e assicurati che il sistema funzioni come previsto.
1. Attiva la modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

1. Esegui un backup del database:

   ```bash
   bin/magento setup:backup --db
   ```

1. Aggiorna MySQL alla versione 8.
1. Importa i dati di backup in MySQL.
1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Disattiva la modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

## Configurazione dell’istanza di database

Questa sezione illustra come creare un&#39;istanza di database per Adobe Commerce o Magenti Open Source. Sebbene sia consigliata una nuova istanza di database, è possibile installare Adobe Commerce o Magento Open Source con un&#39;istanza di database esistente.

Per configurare un&#39;istanza di database MySQL:

1. Accedi al server di database come qualsiasi utente.
1. Passare a un prompt dei comandi MySQL:

   ```bash
   mysql -u root -p
   ```

1. Immettere MySQL `root` password dell&#39;utente quando richiesto.
1. Immettere i seguenti comandi nell&#39;ordine mostrato per creare un&#39;istanza di database denominata `magento` con nome utente `magento`:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Invio `exit` per uscire dal prompt dei comandi.

1. Verifica il database:

   ```bash
   mysql -u magento -p
   ```

   Se viene visualizzato il monitoraggio MySQL, il database è stato creato correttamente. Se viene visualizzato un errore, ripetere i comandi precedenti.

1. Se il server Web e il server di database si trovano su host diversi, eseguire le attività descritte in questo argomento sull&#39;host del server di database, quindi vedere [Impostare una connessione remota al database MySQL](mysql-remote.md).

   È consigliabile configurare l’istanza di database in modo appropriato per la propria azienda. Durante la configurazione del database, tieni presente quanto segue:

   * Gli indicizzatori richiedono valori più elevati `tmp_table_size` e `max_heap_table_size` valori (ad esempio, 64 M). Se configuri le `batch_size` è possibile regolare tale valore insieme alle impostazioni delle dimensioni della tabella per migliorare le prestazioni dell&#39;indicizzatore. Fai riferimento a [Guida all’ottimizzazione](../../../performance/configuration.md) per ulteriori informazioni.

   * Per prestazioni ottimali, assicurarsi che tutte le tabelle dell&#39;indice MySQL e Adobe Commerce o Magenti Open Source possano essere mantenute in memoria (ad esempio, configurare `innodb_buffer_pool_size`).

   * La reindicizzazione su MariaDB 10.4 richiede più tempo rispetto ad altre versioni MariaDB o MySQL. Vedi [Best practice di configurazione](../../../performance/configuration.md#indexers).

1. Per MySQL `TIMESTAMP` campi per seguire le preferenze e la composizione previste dall&#39;architettura dichiarativa dello schema dell&#39;applicazione, la variabile di sistema `explicit_defaults_for_timestamp` deve essere impostato su `on`.

   Riferimenti:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Se questa impostazione non è abilitata, `bin/magento setup:db:status` segnala sempre che `Declarative Schema is not up to date`.

>[!NOTE]
>
>La `explicit_defaults_for_timestamp` è obsoleta. Questa impostazione controlla i comportamenti obsoleti di TIMESTAMP che verranno rimossi in una futura versione di MySQL. Quando tali comportamenti vengono rimossi, la funzione `explicit_defaults_for_timestamp` viene rimossa anche l’impostazione .

>[!WARNING]
>
>Per Adobe Commerce sui progetti di infrastruttura cloud, la `explicit_defaults_for_timestamp` impostazione predefinita per MySQL (MariaDB) su _OFF_.

La reindicizzazione su MariaDB 10.4 richiede più tempo rispetto ad altre versioni MariaDB o MySQL. Per velocizzare la reindicizzazione, si consiglia di impostare questi parametri di configurazione MariaDB:

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_selectivity = 1

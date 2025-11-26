---
title: Linee guida MySQL
description: Segui questi passaggi per installare e configurare MySQL e MariaDB per le installazioni locali di Adobe Commerce.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 2d17da1f8cbda1462839ad2fa3ea569833443827
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Linee guida generali di MySQL

Vedere [Requisiti di sistema](../../system-requirements.md) per le versioni supportate di MySQL.

Adobe _consiglia vivamente_ di rispettare il seguente standard durante la configurazione del database:

* Adobe Commerce utilizza [i trigger del database MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) per migliorare l&#39;accesso al database durante la reindicizzazione. Vengono creati quando la modalità indicizzatore è impostata su [pianificazione](../../../configuration/cli/manage-indexers.md#configure-indexers). L’applicazione non supporta i trigger personalizzati nel database, poiché tali trigger possono introdurre incompatibilità con le versioni future di Adobe Commerce.
* Acquisisci familiarità con [le potenziali limitazioni del trigger MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) prima di continuare.
* Per migliorare la postura di sicurezza del database, attivare la modalità SQL [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) per impedire l&#39;archiviazione di valori di dati non validi, che potrebbero causare interazioni di database indesiderate.
* Adobe Commerce _non_ supporta la replica basata su istruzioni MySQL. Utilizzare _only_ [replica basata su righe](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce attualmente utilizza `CREATE TEMPORARY TABLE` istruzioni nelle transazioni, che sono [incompatibili](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) con le implementazioni del database, utilizzando la replica basata su GTID, ad esempio [istanze di seconda generazione di Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Considera MySQL per Cloud SQL 8.0 come alternativa.

>[!NOTE]
>
>Se il server Web e il server di database si trovano su host diversi, eseguire le attività descritte in questo argomento sull&#39;host del server di database, quindi vedere [Configurare una connessione remota al database MySQL](mysql-remote.md).

## Installazione di MySQL su Ubuntu

Adobe Commerce 2.4 richiede un&#39;installazione pulita di MySQL 8.0. Per istruzioni sull&#39;installazione di MySQL nel computer, seguire i collegamenti riportati di seguito.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Se si prevede di importare un numero elevato di prodotti, è possibile aumentare il valore di [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) che è maggiore del valore predefinito, ovvero 16 MB.

>[!NOTE]
>
>Il valore predefinito si applica ai progetti locali di Adobe Commerce sull&#39;infrastruttura cloud _e_. I clienti Adobe Commerce su infrastruttura cloud Pro devono aprire un ticket di supporto per aumentare il valore `max_allowed_packet`. I clienti di Adobe Commerce su infrastruttura cloud Starter possono aumentare il valore aggiornando la configurazione nel file `/etc/mysql/mysql.cnf`.

Per aumentare il valore, aprire il file `/etc/mysql/mysql.cnf` in un editor di testo e individuare il valore per `max_allowed_packet`. Salvare le modifiche apportate al file `mysql.cnf`, chiudere l&#39;editor di testo e riavviare MySQL (`service mysql restart`).

Per verificare facoltativamente il valore impostato, immettere il comando seguente al prompt `mysql>`:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Quindi [Configurare l&#39;istanza del database](#configuring-the-database-instance).

## Modifiche a MySQL 8

Per Adobe Commerce 2.4 è stato aggiunto il supporto per MySQL 8.
In questa sezione vengono descritte le modifiche principali apportate a MySQL 8 di cui gli sviluppatori devono essere a conoscenza.

### Larghezza rimossa per i tipi interi (spaziatura interna)

La specifica della larghezza di visualizzazione per i tipi di dati integer (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) è stata rimossa in MySQL 8.0.17. Le istruzioni che includono definizioni dei tipi di dati nell&#39;output non mostrano più la larghezza di visualizzazione per i tipi interi, ad eccezione di TINYINT(1). I connettori MySQL presuppongono che le colonne TINYINT(1) abbiano avuto origine come colonne BOOLEANE. Questa eccezione consente loro di continuare a fare tale presupposto.

#### Esempio

Descrizione di admin_user in mysql 8.19

| Campo | Tipo | Nullo | Chiave | Predefinito | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | SÌ | | `NULL` | |
| `lastname` | `varchar(32`) | SÌ | | `NULL` | |
| `email` | `varchar(128)` | SÌ | | `NULL` | |
| `username` | `varchar(40)` | SÌ | UNI | `NULL` | |
| `password` | `varchar(255)` | NO | | `NULL` | |
| `created` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` sull&#39;aggiornamento `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | SÌ | | `NULL` | |
| `lognum` | `smallint unsigned` | NO | | `0` | |

Ad eccezione di _TINYINT(1)_, tutte le spaziature intere (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) devono essere rimosse dal file `db_schema.xml`.

Per ulteriori informazioni, vedere [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportamento predefinito di ORDER BY

Prima della versione 8.0, le voci venivano ordinate in base alla chiave esterna. L’ordinamento predefinito dipende dal motore utilizzato.
Specificare sempre un ordinamento se il codice dipende da un ordinamento specifico.

### Qualificatori ASC e DESC obsoleti per GROUP BY

A partire da MySQL 8.0.13, i qualificatori `ASC` o `DESC` obsoleti per le clausole `GROUP BY` sono stati rimossi. Le query che in precedenza utilizzavano l&#39;ordinamento `GROUP BY` possono produrre risultati diversi dalle versioni precedenti di MySQL. Per generare un determinato ordinamento, specificare una clausola `ORDER BY`.

## Commerce e MySQL 8

Sono state apportate alcune modifiche ad Adobe Commerce per supportare correttamente MySQL 8.

### Comportamento query e inserimento

Adobe Commerce ha disabilitato il comportamento di convalida regolare impostando SET SQL_MODE=&#39;&#39; in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Se la convalida è disattivata, è possibile che MySQL tronchi i dati. In MySQL il comportamento della query è cambiato: `Select * on my_table where IP='127.0.0.1'` non restituisce più risultati perché l&#39;indirizzo IP viene ora visualizzato correttamente come stringa, anziché come numero intero.

## Aggiornamento da MySQL 5.7 a MySQL 8

Per aggiornare correttamente MySQL dalla versione 5.7 alla versione 8, è necessario seguire i passaggi seguenti nell&#39;ordine indicato:

1. Aggiornare Adobe Commerce alla versione 2.4.0.
Esegui il test completo e assicurati che il sistema funzioni come previsto.
1. Abilita modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

1. Eseguire un backup del database:

   ```bash
   bin/magento setup:backup --db
   ```

1. Aggiornare MySQL alla versione 8.
1. Importare i dati di backup in MySQL.
1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Disattiva modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

## Configurazione dell’istanza del database

Questa sezione illustra come creare un’istanza di database per Adobe Commerce. Sebbene sia consigliata una nuova istanza di database, è possibile installare Adobe Commerce con un&#39;istanza di database esistente.

Per configurare un&#39;istanza di database MySQL:

1. Accedere al server del database come qualsiasi utente.
1. Passare al prompt dei comandi MySQL:

   ```bash
   mysql -u root -p
   ```

1. Immettere la password dell&#39;utente MySQL `root` quando richiesto.
1. Immettere i comandi seguenti nell&#39;ordine indicato per creare un&#39;istanza di database denominata `magento` con nome utente `magento`:

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

1. Immettere `exit` per uscire dal prompt dei comandi.

1. Verificare il database:

   ```bash
   mysql -u magento -p
   ```

   Se viene visualizzato il monitoraggio MySQL, il database è stato creato correttamente. Se viene visualizzato un errore, ripetere i comandi precedenti.

1. Se il server Web e il server di database si trovano su host diversi, eseguire le attività descritte in questo argomento sull&#39;host del server di database, quindi vedere [Configurare una connessione remota al database MySQL](mysql-remote.md).

   È consigliabile configurare l&#39;istanza di database in base alle esigenze aziendali. Durante la configurazione del database, tenere presente quanto segue:

   * Gli indicizzatori richiedono valori `tmp_table_size` e `max_heap_table_size` superiori (ad esempio, 64 M). Se si configura il parametro `batch_size`, è possibile regolare tale valore insieme alle impostazioni delle dimensioni della tabella per migliorare le prestazioni dell&#39;indicizzatore. Per ulteriori informazioni, consultare la [Guida all&#39;ottimizzazione](../../../performance/configuration.md).

   * Per prestazioni ottimali, assicurarsi che tutte le tabelle indice MySQL e Adobe Commerce possano essere mantenute in memoria, ad esempio configurare `innodb_buffer_pool_size`.

   * La reindicizzazione su MariaDB 10.4 richiede più tempo rispetto ad altre versioni di MariaDB o MySQL. Consulta [Best practice per la configurazione](../../../performance/configuration.md#indexers).

1. Affinché i campi MySQL `TIMESTAMP` seguano le preferenze e la composizione previste dall&#39;architettura dello schema dichiarativo dell&#39;applicazione, la variabile di sistema `explicit_defaults_for_timestamp` deve essere impostata su `on`.

   Riferimenti:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Se questa impostazione non è abilitata, `bin/magento setup:db:status` segnala sempre che `Declarative Schema is not up to date`.

>[!NOTE]
>
>L&#39;impostazione `explicit_defaults_for_timestamp` è obsoleta. Questa impostazione consente di controllare i comportamenti di MARCA TEMPORALE obsoleti che verranno rimossi in una futura versione di MySQL. Quando questi comportamenti vengono rimossi, viene rimossa anche l&#39;impostazione `explicit_defaults_for_timestamp`.

>[!WARNING]
>
>Per i progetti di infrastruttura cloud di Adobe Commerce, l&#39;impostazione `explicit_defaults_for_timestamp` per MySQL (MariaDB) è _OFF_.

{{$include /help/_includes/maria-db-config.md}}

<!-- Last updated from includes: 2025-11-25 11:39:51 -->

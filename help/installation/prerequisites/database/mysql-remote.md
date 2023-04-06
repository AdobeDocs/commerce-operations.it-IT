---
title: Impostare una connessione remota al database MySQL
description: Segui questi passaggi per configurare una connessione al database remoto per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Impostare una connessione remota al database MySQL

A volte può essere necessario ospitare il database su un server separato invece di eseguire il server di database e il server Web sullo stesso computer.

Adobe ha fornito un modo per connettersi a un server MySQL su un computer diverso. A partire da Adobe Commerce e Magenti Open Source 2.4.3, puoi anche configurare l’applicazione per l’utilizzo di un database Amazon Web Services (AWS) Aurora senza modifiche al codice.

Aurora è un server MySQL ad alte prestazioni e pienamente compatibile ospitato su AWS.

## Connessione a un database AWS Aurora

L&#39;utilizzo di Aurora come database è semplice come specificare il database nella normale configurazione di Adobe Commerce e Magento Open Source, utilizzando il connettore di database predefinito.

In esecuzione `bin/magento setup:install`, utilizza le informazioni di Aurora nel `db-` campi:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

La `db-host` è l’URL di Aurora con il `https://` e finali `:portnumber`  rimosso.

## Configurazione di una connessione al database remoto

>[!NOTE]
>
>Questo argomento avanzato deve essere utilizzato solo da un amministratore di rete o di database esperti. Devi avere `root` accedere al file system e accedere a MySQL come `root`.

### Prerequisiti

Prima di iniziare, devi:

* [Installazione del server MySQL](mysql.md) sul server di database.
* [Creare un’istanza di database](mysql.md#configuring-the-database-instance) sul server di database.
* Installa il client MySQL sul nodo Web Adobe Commerce o Magenti Open Source. Per ulteriori informazioni, consultare la documentazione di MySQL.

### Elevata disponibilità

Utilizzare le seguenti linee guida per configurare le connessioni al database remoto se il server Web o il server di database sono in cluster:

* È necessario configurare una connessione per ogni nodo del server web.
* In genere, si configura una connessione al database con load balancer; tuttavia, il clustering del database può essere complesso e la sua configurazione dipende da te. Adobe non formula raccomandazioni specifiche per il clustering di database.

   Per ulteriori informazioni, consulta [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Risoluzione dei problemi di connessione

In caso di problemi di connessione a uno degli host, effettua prima il ping dell&#39;altro host per assicurarti che sia raggiungibile. Potrebbe essere necessario consentire le connessioni da un host a un altro modificando le regole firewall e SELinux (se si utilizza SELinux).

## Creare la connessione remota

Per creare una connessione remota:

1. Sul server di database, come utente con `root` , aprire il file di configurazione MySQL.

   Per individuarlo, immettere il comando seguente:

   ```bash
   mysql --help
   ```

   La posizione viene visualizzata in modo simile al seguente:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Su Ubuntu 16, il percorso è tipicamente `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Cerca nel file di configurazione `bind-address`.

   Se esiste, modificare il valore come segue.

   Se non esiste, aggiungilo al `[mysqld]` sezione .

   ```conf
   bind-address = <ip address of your web node>
   ```

   Vedi [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), soprattutto se disponi di un server web cluster.

1. Salva le modifiche apportate al file di configurazione e esci dall’editor di testo.
1. Riavvia il servizio MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Se l&#39;avvio di MySQL non riesce, cercare nel registro di sistema l&#39;origine del problema. Risolvere il problema utilizzando [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) o un&#39;altra fonte autorevole.

## Concedere l’accesso a un utente del database

Per abilitare la connessione del nodo Web al server del database, è necessario concedere a un utente del database del nodo Web l&#39;accesso al database sul server remoto.

In questo esempio viene concesso il `root` accesso completo dell&#39;utente al database sull&#39;host remoto.

Per concedere l&#39;accesso a un utente del database:

1. Accedi al server di database.
1. Connettersi al database MySQL come `root` utente.
1. Immetti il seguente comando:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Ad esempio:

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Se il server web è in cluster, immetti lo stesso comando su ogni server web. Devi usare lo stesso nome utente per ogni server web.

## Verifica accesso al database

Nell&#39;host del nodo Web, immettere il comando seguente per verificare il funzionamento della connessione:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Se il monitoraggio MySQL viene visualizzato come segue, il database è pronto per Adobe Commerce o Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Se il server web è in cluster, immetti il comando su ogni host del server web.

## Installare Adobe Commerce o il Magento Open Source

Quando installi Adobe Commerce o Magenti Open Source, devi specificare quanto segue:

* L’URL di base (indicato anche come *indirizzo del negozio*) specifica il nome host o l&#39;indirizzo IP del *nodo web*
* L&#39;host del database è *database server remoto* Indirizzo IP (o load balancer se il server di database è in cluster)
* Il nome utente del database è *nodo web locale* utente del database a cui è stato concesso l&#39;accesso
* Password database è la password dell&#39;utente del nodo Web locale
* Nome database è il nome del database sul server remoto

---
title: Configurare una connessione remota al database MySQL
description: Per configurare una connessione al database remoto per le installazioni locali di Adobe Commerce e Magenti Open Source, eseguire la procedura seguente.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Configurare una connessione remota al database MySQL

A volte può essere necessario ospitare il database su un server separato anziché eseguire il server di database e il server web sullo stesso computer.

L&#39;Adobe ha fornito un modo per connettersi a un server MySQL su un computer diverso. A partire da Adobe Commerce e dal Magento Open Source 2.4.3, puoi anche configurare l’applicazione per l’utilizzo di un database Amazon Web Services (AWS) Aurora senza modifiche al codice.

Aurora è un server MySQL ad alte prestazioni e completamente conforme ospitato su AWS.

## Connessione a un database AWS Aurora

L’utilizzo di Aurora come database è semplice come specificare il database nella normale configurazione di Adobe Commerce e configurazione del Magento Open Source, utilizzando il connettore di database predefinito.

Durante l’esecuzione `bin/magento setup:install`, utilizza le informazioni di Aurora in `db-` campi:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

Il `db-host` valore è l’URL di Aurora con `https://` e finale `:portnumber`  è stato rimosso.

## Impostazione di una connessione al database remoto

>[!NOTE]
>
>Si tratta di un argomento avanzato che deve essere utilizzato solo da un amministratore di rete o da un amministratore di database esperto. Devi avere `root` accesso al file system e accedere a MySQL come `root`.

### Prerequisiti

Prima di iniziare, è necessario:

* [Installa server MySQL](mysql.md) sul server di database.
* [Creare un’istanza di database](mysql.md#configuring-the-database-instance) sul server di database.
* Installare il client MySQL nel nodo Web di Adobe Commerce o di Magento Open Source. Per ulteriori informazioni, consultare la documentazione MySQL.

### Elevata disponibilità

Utilizzare le linee guida seguenti per configurare le connessioni al database remoto se il server Web o il server di database sono cluster:

* È necessario configurare una connessione per ogni nodo del server Web.
* In genere si configura una connessione al database load balancer; tuttavia, il clustering del database può essere complesso e la configurazione dipende dall&#39;utente. L&#39;Adobe non fornisce raccomandazioni specifiche per il clustering del database.

   Per ulteriori informazioni, consulta [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Risoluzione dei problemi di connessione

In caso di problemi di connessione a uno degli host, effettua prima il ping dell’altro host per assicurarti che sia raggiungibile. Potrebbe essere necessario consentire le connessioni da un host all&#39;altro modificando le regole firewall e SELinux (se si utilizza SELinux).

## Creare la connessione remota

Per creare una connessione remota:

1. Sul server di database, come utente con `root` , aprire il file di configurazione MySQL.

   Per individuarlo, immetti il seguente comando:

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

   Se esiste, modificare il valore come indicato di seguito.

   Se non esiste, aggiungilo al `[mysqld]` sezione.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Consulta [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), soprattutto se si dispone di un server web cluster.

1. Salva le modifiche nel file di configurazione e chiudi l’editor di testo.
1. Riavviare il servizio MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Se MySQL non viene avviato correttamente, cercare l&#39;origine del problema in syslog. Risolvi il problema utilizzando [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) o da un’altra fonte autorevole.

## Concedere l’accesso a un utente del database

Per consentire al nodo Web di connettersi al server di database, è necessario concedere a un nodo Web l&#39;accesso utente al database sul server remoto.

In questo esempio viene concesso il `root` accesso completo dell&#39;utente al database sull&#39;host remoto.

Per concedere l&#39;accesso a un utente del database:

1. Accedere al server del database.
1. Connessione al database MySQL come `root` utente.
1. Immetti il comando seguente:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Ad esempio:

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Se il server Web è in cluster, immettere lo stesso comando su ogni server Web. È necessario utilizzare lo stesso nome utente per ogni server web.

## Verificare l&#39;accesso al database

Nell’host del nodo web, immetti il seguente comando per verificare il funzionamento della connessione:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Se il monitoraggio MySQL viene visualizzato come segue, il database è pronto per Adobe Commerce o Magenti Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Se il server Web è in cluster, immettere il comando su ciascun host del server Web.

## Installare Adobe Commerce o Magenti Open Source

Quando installi Adobe Commerce o Magenti Open Source, devi specificare quanto segue:

* L’URL di base (noto anche come *indirizzo store*) specifica il nome host o l’indirizzo IP del *nodo web*
* L&#39;host del database è *server di database remoto* Indirizzo IP (o load balancer se il server di database è in cluster)
* Database username è il *nodo web locale* utente del database a cui è stato concesso l&#39;accesso
* La password del database è la password dell&#39;utente del nodo Web locale
* Nome database è il nome del database sul server remoto

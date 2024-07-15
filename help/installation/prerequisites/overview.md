---
title: Prerequisiti per l'installazione locale
description: Ulteriori informazioni sulle dipendenze software necessarie per le installazioni locali di Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---

# Prerequisiti per l&#39;installazione locale

Prima di installare Adobe Commerce, è necessario effettuare le seguenti operazioni:

* Configura uno o più host che soddisfano i [requisiti di sistema](../system-requirements.md).
* Se stai configurando più di un nodo web con bilanciamento del carico, configura e verifica quella parte del sistema _prima_ di installare l&#39;applicazione.
* Assicurarsi di poter eseguire il backup dell&#39;intero sistema in vari punti durante l&#39;installazione in modo da poterlo ripristinare in caso di problemi.

>[!NOTE]
>
>Si presuppone che si stia installando Adobe Commerce in un **ambiente di sviluppo**, che si disponga dell&#39;accesso utente root al computer, **e** che il computer non debba essere altamente protetto. Se si sta configurando un computer più sicuro, si consiglia di consultare un amministratore di rete per ulteriore assistenza.

Si consiglia vivamente di aggiornare e aggiornare il software del sistema operativo. Questi aggiornamenti possono fornire correzioni software e di sicurezza che potrebbero evitare problemi futuri. Non sapete cosa significa tutto questo? Consulta la [pagina di panoramica dell&#39;installazione](../overview.md).

Immettere i seguenti comandi come utente con privilegi `root`:

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## Verifica prerequisiti

Per verificare la presenza di prerequisiti nel sistema, immettete i seguenti comandi:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce supporta Apache versione 2.4 come indicato di seguito:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Per installare o aggiornare Apache, vedi [Apache](web-server/apache.md).

### PHP

Consulta [requisiti di sistema](../system-requirements.md) per le versioni supportate di PHP e [PHP](../system-requirements.md#php-settings) per i requisiti PHP.

### MySQL

Verificare di disporre di una versione compatibile di MySQL per la versione di Adobe Commerce da installare. Consulta [Requisiti di sistema](../system-requirements.md) per le versioni supportate.

```bash
mysql -u <database root user or database owner name> -p
```

Ad esempio:

```bash
mysql -u magento -p
```

Il risultato seguente indica la versione in esecuzione.

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Digitare `help` o `\h` per la Guida. Digitare `\c` per cancellare l&#39;istruzione di input corrente.

Immetti `exit` al prompt `mysql>` per uscire.

Per installare o aggiornare MySQL, vedere [MySQL](database/mysql.md).

### Motore di ricerca

Per verificare l&#39;installazione di OpenSearch:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Per verificare l&#39;installazione dell&#39;Elasticsearch:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Ad esempio:

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```

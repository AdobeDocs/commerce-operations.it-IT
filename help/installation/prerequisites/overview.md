---
title: Prerequisiti per l'installazione locale
description: Ulteriori informazioni sulle dipendenze software necessarie per le installazioni locali di Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# Prerequisiti per l&#39;installazione locale

Prima di installare Adobe Commerce o Magento Open Source, è necessario effettuare le seguenti operazioni:

* Configurare uno o più host che soddisfino i requisiti [requisiti di sistema](../system-requirements.md).
* Se stai impostando più di un nodo web con bilanciamento del carico, imposta e verifica quella parte del sistema _prima di_ installare l&#39;applicazione.
* Assicurarsi di poter eseguire il backup dell&#39;intero sistema in vari punti durante l&#39;installazione in modo da poterlo ripristinare in caso di problemi.

>[!NOTE]
>
>Supponiamo che tu stia installando Adobe Commerce o il Magento Open Source in un **ambiente di sviluppo**, di disporre dell&#39;accesso utente root al computer, **e** che la macchina non deve essere altamente sicura. Se si sta configurando un computer più sicuro, si consiglia di consultare un amministratore di rete per ulteriore assistenza.

Si consiglia vivamente di aggiornare e aggiornare il software del sistema operativo. Questi aggiornamenti possono fornire correzioni software e di sicurezza che potrebbero evitare problemi futuri. Non sapete cosa significa tutto questo? Consulta la nostra [pagina panoramica dell’installazione](../overview.md).

Immetti i seguenti comandi come utente con `root` privilegi:

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

Verificare di disporre di una versione compatibile di MySQL per la versione di Adobe Commerce o del Magento Open Source da installare. Consulta [Requisiti di sistema](../system-requirements.md) versioni supportate.

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

Tipo `help` o `\h` per assistenza. Tipo `\c` per cancellare l&#39;istruzione di input corrente.

Invio `exit` alla `mysql>` per uscire.

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

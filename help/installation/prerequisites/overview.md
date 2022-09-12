---
title: Prerequisiti per l’installazione in locale
description: Ulteriori informazioni sulle dipendenze software necessarie per le installazioni on-premise di Adobe Commerce e Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---


# Prerequisiti per l’installazione in locale

Prima di installare Adobe Commerce o Magenti Open Source, è necessario effettuare le seguenti operazioni:

* Imposta uno o più host che soddisfano i requisiti [requisiti di sistema](../system-requirements.md).
* Se si impostano più nodi Web con bilanciamento del carico, impostare e testare tale parte del sistema _prima_ installare l&#39;applicazione.
* Assicurati di poter eseguire il backup dell&#39;intero sistema in vari punti durante l&#39;installazione, in modo da poterlo riportare in caso di problemi.

>[!NOTE]
>
>Presupponiamo che tu stia installando Adobe Commerce o il Magento Open Source in un **ambiente di sviluppo**, che l&#39;utente root abbia accesso al computer, **e** che la macchina non deve essere altamente sicura. Se si sta configurando un computer più sicuro, è consigliabile consultare un amministratore di rete per ulteriori informazioni.

Si consiglia vivamente di aggiornare e aggiornare il software del sistema operativo. Questi aggiornamenti possono fornire correzioni di sicurezza e software che potrebbero impedire problemi futuri. Non sa cosa significa tutto questo? Consulta il nostro [pagina di panoramica dell’installazione](../overview.md).

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

## Controllo prerequisito

Per verificare la presenza di prerequisiti nel sistema, immetti i seguenti comandi:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce e Magenti Open Source supportano Apache versione 2.4 come indicato dal seguente risultato:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Per installare o aggiornare Apache, vedi [Apache](web-server/apache.md).

### PHP

Vedi [requisiti di sistema](../system-requirements.md) per le versioni supportate di PHP e [PHP] per i requisiti PHP.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

Ad esempio:

```bash
mysql -u magento -p
```

Verificare di disporre della versione corretta di MySQL per la versione di Adobe Commerce o del Magento Open Source che si sta installando ([controlla qui per le versioni supportate](../system-requirements.md). Il risultato seguente indica la versione in esecuzione.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Tipo `help` o `\h` per aiuto. Tipo `\c` cancellare l’istruzione di input corrente.

Invio `exit` a `mysql>` richiedi l&#39;uscita.

Per installare o aggiornare MySQL, vedere [MySQL](database/mysql.md).

### Elasticsearch o OpenSearch

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

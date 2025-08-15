---
title: Prerequisiti per i motori di ricerca
description: Segui questi passaggi per installare e configurare il software dei motori di ricerca supportato per le installazioni locali di Adobe Commerce.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Prerequisiti per i motori di ricerca

A partire da Adobe Commerce 2.4, tutte le installazioni devono essere configurate per utilizzare [Elasticsearch](https://www.elastic.co) o [OpenSearch](https://opensearch.org/) come soluzione di ricerca nel catalogo.

>[!NOTE]
>
>Il supporto di OpenSearch è stato aggiunto nella versione 2.4.4. OpenSearch è un fork compatibile di Elasticsearch. Tutte le istruzioni per configurare Elasticsearch 7 valgono per OpenSearch. [Migrazione da Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) fornisce indicazioni sul passaggio a OpenSearch.

## Versioni supportati

È necessario installare e configurare Elasticsearch o OpenSearch prima di installare Adobe Commerce 2.4.4 e versioni successive.

Per informazioni specifiche sulla versione, consultare [Requisiti di sistema](../../system-requirements.md).

## Configurazione consigliata

Consigliamo quanto segue:

* [Configurare nginx per il motore di ricerca](configure-nginx.md)
* [Configurare Apache per il motore di ricerca](configure-apache.md)

## Percorso di installazione

Le seguenti attività presuppongono che il sistema sia stato configurato in base al diagramma seguente:

![Diagramma motore di ricerca](../../../assets/installation/search-engine-config.svg)

Il diagramma precedente mostra:

* L&#39;applicazione Commerce e il motore di ricerca sono installati su host diversi.

  L&#39;esecuzione su host separati richiede il funzionamento del proxy. Il clustering del motore di ricerca esula dall&#39;ambito di questa guida, ma puoi trovare ulteriori informazioni nella [documentazione sul clustering di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).

* Ogni host ha il proprio server web; i server web non devono essere gli stessi.

  Ad esempio, l’applicazione Commerce può eseguire Apache e il motore di ricerca può eseguire nginx.

* Entrambi i server web utilizzano Transport Layer Security (TLS).

  La configurazione di TLS va oltre l’ambito della nostra documentazione.

Le richieste di ricerca vengono elaborate come segue:

1. Una richiesta di ricerca da parte di un utente viene ricevuta dal server Web Commerce, che la inoltra al server del motore di ricerca.

   È possibile configurare il motore di ricerca per la connessione all&#39;host e alla porta del proxy. Consigliamo la porta SSL del server web (per impostazione predefinita, 443).

1. Il server web del motore di ricerca (in ascolto sulla porta 443) invia la richiesta al server del motore di ricerca (per impostazione predefinita, ascolta sulla porta 9200).

1. L’accesso al motore di ricerca è ulteriormente protetto dall’autenticazione HTTP Basic. Affinché una richiesta possa raggiungere il motore di ricerca, deve viaggiare su SSL *e* fornire un nome utente e una password validi.

1. Il motore di ricerca elabora la richiesta.

1. La comunicazione viene restituita lungo la stessa route, con il server web Elasticsearch che funge da proxy inverso sicuro.

## Prerequisiti

Le attività descritte in questa sezione richiedono quanto segue:

* [Firewall e SELinux](#firewall-and-selinux)
* [Installare Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Installare il motore di ricerca](#install-the-search-engine)
* [Aggiornamento di Elasticsearch](#upgrading-elasticsearch)

### Firewall e SELinux

Per impostazione predefinita, il software relativo alla sicurezza (iptables, SELinux, AppArmor) può essere configurato per bloccare la comunicazione tra i sottosistemi. Può essere una buona idea controllarli se ci sono problemi.

#### Imposta le regole per iptables e SELinux

Per impostare le regole che consentono la comunicazione con il firewall o con SELinux abilitato, consulta le risorse seguenti:

* [iptables procedura](https://help.ubuntu.com/community/IptablesHowTo)
* [Come modificare le regole iptables (progetto fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introduzione a SELinux (CentOS.org)](https://www.centos.org)
* [Wiki tutorial SELinux (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installare Java Software Development Kit

Per determinare se Java è già installato, immetti il seguente comando:

```bash
java -version
```

Se viene visualizzato il messaggio `java: command not found`, è necessario installare Java SDK come descritto nella sezione successiva.

Vedere una delle sezioni seguenti:

* [Installare il JDK più recente su CentOS](#install-the-jdk-on-centos)
* [Installare il JDK più recente su Ubuntu](#install-the-jdk-on-ubuntu)

#### Installare JDK su CentOS

Consulta questa [esercitazione sull&#39;oceano digitale](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Assicurarsi di installare JDK e *non* JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java versione 8 potrebbe non essere disponibile per tutti i sistemi operativi. Ad esempio, puoi [cercare nell&#39;elenco dei pacchetti disponibili Ubuntu](https://packages.ubuntu.com/).

#### Installare JDK su Ubuntu

Per installare JDK 1.8 su Ubuntu, immettere i seguenti comandi come utente con privilegi `root`:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Per altre opzioni, consulta [Documentazione di Oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installare il motore di ricerca

Segui [Installazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) o [Installa e configura OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) per i passaggi specifici della tua piattaforma.

Per verificare che Elasticsearch funzioni, immetti il comando seguente sul server su cui è in esecuzione:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Viene visualizzato un messaggio simile al seguente:

```
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Per verificare il funzionamento di OpenSearch, immettete i seguenti comandi:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Aggiornamento di Elasticsearch

Consulta [Aggiornamento di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete sul backup dei dati, l&#39;individuazione di potenziali problemi di migrazione e il test degli aggiornamenti prima della distribuzione in produzione. A seconda della versione corrente di Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

Elasticsearch richiede JDK 1.8 o versione successiva. Consulta [Installare Java Software Development Kit](#install-the-java-software-development-kit) per verificare quale versione di JDK è installata.

## Risorse aggiuntive

Consulta la documentazione di [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) o [OpenSearch](https://opensearch.org/docs/latest/).

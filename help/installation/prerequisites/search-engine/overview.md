---
title: Prerequisiti per i motori di ricerca
description: Segui questi passaggi per installare e configurare il software di motori di ricerca supportato per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# Prerequisiti per i motori di ricerca

A partire da Adobe Commerce e Magenti Open Source 2.4, tutte le installazioni devono essere configurate per l’utilizzo [Elasticsearch](https://www.elastic.co) o [OpenSearch](https://opensearch.org/) come soluzione di ricerca nel catalogo.

>[!NOTE]
>
>Il supporto OpenSearch è stato aggiunto in 2.4.4. OpenSearch è un fork di Elasticsearch compatibile. Tutte le istruzioni per configurare l&#39;Elasticsearch 7 si applicano a OpenSearch. [Migrazione da Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) fornisce indicazioni sul passaggio a OpenSearch.

## Versioni supportate

È necessario installare e configurare Elasticsearch o OpenSearch prima di installare Adobe Commerce 2.4.4 e versioni successive.

Fai riferimento a [Requisiti di sistema](../../system-requirements.md) per informazioni specifiche sulla versione.

## Configurazione consigliata

Si consiglia quanto segue:

* [Configurare l’allegato per il motore di ricerca](configure-nginx.md)
* [Configurare Apache per il motore di ricerca](configure-apache.md)

## Posizione di installazione

Le seguenti attività presuppongono che il sistema sia stato configurato in base al diagramma seguente:

![Diagramma del motore di ricerca](../../../assets/installation/search-engine-config.svg)

Il diagramma precedente mostra quanto segue:

* L’applicazione Commerce e il motore di ricerca sono installati su host diversi.

   L’esecuzione su host separati richiede il proxy per funzionare. (Il clustering del motore di ricerca va oltre l’ambito di questa guida, ma è possibile trovare ulteriori informazioni nel [Documentazione sul clustering di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Ogni host ha un proprio server web; i server web non devono necessariamente essere gli stessi.

   Ad esempio, l’applicazione Commerce può eseguire Apache e il motore di ricerca può eseguire nginx.

* Entrambi i server web utilizzano TLS (Transport Layer Security).

   L’impostazione di TLS va oltre l’ambito della nostra documentazione.

Le richieste di ricerca vengono elaborate come segue:

1. Una richiesta di ricerca di un utente viene ricevuta dal server Web Commerce, che la inoltra al server del motore di ricerca.

   Puoi configurare il motore di ricerca per la connessione all&#39;host e alla porta del proxy. Si consiglia la porta SSL del server web (per impostazione predefinita, 443).

1. Il server web del motore di ricerca (in ascolto sulla porta 443) proxy la richiesta al server del motore di ricerca (per impostazione predefinita, ascolta sulla porta 9200).

1. L&#39;accesso al motore di ricerca è ulteriormente protetto dall&#39;autenticazione HTTP Basic. Per una richiesta di raggiungere il motore di ricerca, deve viaggiare su SSL *e* fornire un nome utente e una password validi.

1. Il motore di ricerca elabora la richiesta.

1. La comunicazione torna lungo lo stesso percorso, con l&#39;Elasticsearch web server che agisce come un proxy inverso sicuro.

## Prerequisiti

Le attività descritte in questa sezione richiedono quanto segue:

* [Firewall e SELinux](#firewall-and-selinux)
* [Installare il Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Installare il motore di ricerca](#install-the-search-engine)
* [Aggiornamento dell’Elasticsearch](#upgrading-elasticsearch)

### Firewall e SELinux

Il software relativo alla sicurezza (iptables, SELinux, AppArmor) può essere configurato per impostazione predefinita per bloccare la comunicazione tra sottosistemi. Può essere una buona idea controllarli in caso di problemi.

#### Imposta regole per iptables e SELinux

Per impostare regole per consentire la comunicazione con il firewall o SELinux abilitato, consulta le risorse seguenti:

* [guida introduttiva](https://help.ubuntu.com/community/IptablesHowTo)
* [Come modificare le regole di iptables (progetto fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introduzione a SELinux (CentOS.org)](https://www.centos.org)
* [SELinux Come-To Wiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installare il kit di sviluppo software Java

Per determinare se Java è già installato, immetti il comando seguente:

```bash
java -version
```

Se il messaggio `java: command not found` viene visualizzato , devi installare Java SDK come descritto nella sezione successiva.

Vedere una delle sezioni seguenti:

* [Installa l&#39;ultimo JDK su CentOS](#install-the-jdk-on-centos)
* [Installa l&#39;ultimo JDK su Ubuntu](#install-the-jdk-on-ubuntu)

#### Installa JDK su CentOS

Vedi questo [Esercitazione sull&#39;Oceano Digitale](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Assicurati di installare JDK e *not* JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java versione 8 potrebbe non essere disponibile per tutti i sistemi operativi. Ad esempio, puoi [cerca l&#39;elenco dei pacchetti disponibili per Ubuntu](https://packages.ubuntu.com/).

#### Installa JDK su Ubuntu

Per installare JDK 1.8 su Ubuntu, immetti i seguenti comandi come utente con `root` privilegi:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Per altre opzioni, vedi [Documentazione di Oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installare il motore di ricerca

Segui [Installazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) o [Installa e configura OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) per i passaggi specifici della piattaforma.

Per verificare che l&#39;Elasticsearch funzioni, immettere il seguente comando sul server su cui è in esecuzione:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Viene visualizzato un messaggio simile al seguente:

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Per verificare il funzionamento di OpenSearch, immettere i seguenti comandi:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Aggiornamento dell’Elasticsearch

Fai riferimento a [Aggiornamento dell’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete su come eseguire il backup dei dati, rilevare potenziali problemi di migrazione e testare gli aggiornamenti prima dell’implementazione in produzione. A seconda della versione corrente dell&#39;Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

Elasticsearch richiede JDK 1.8 o versione successiva. Vedi [Installare il kit di sviluppo software Java](#install-the-java-software-development-kit) per verificare quale versione di JDK è installata.

## Risorse aggiuntive

Consulta la sezione [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html) o [OpenSearch](https://opensearch.org/docs/latest/) documentazione.

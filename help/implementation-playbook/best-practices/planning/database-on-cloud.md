---
title: Best practice di configurazione del database per le distribuzioni cloud
description: Scopri come configurare le impostazioni del database e delle applicazioni per migliorare le prestazioni durante la distribuzione di Adobe Commerce sull’infrastruttura cloud.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Best practice per la configurazione del database

Scopri le best practice per migliorare le prestazioni del database e lavorare in modo efficiente con il database durante la distribuzione di Adobe Commerce sull’infrastruttura cloud.

## Prodotti interessati

Adobe Commerce su infrastruttura cloud

## Converti tutte le tabelle MyISAM in InnoDB

Adobe consiglia di utilizzare il motore di database InnoDB. In un&#39;installazione Adobe Commerce predefinita, tutte le tabelle nel database vengono memorizzate utilizzando il motore InnoDB. Tuttavia, alcuni moduli di terze parti (estensioni) possono introdurre tabelle in formato MyISAM. Dopo aver installato un modulo di terze parti, controlla il database per identificare eventuali tabelle in `myisam` formattarli e convertirli in `innodb` formato.

### Determinare se un modulo include tabelle MyISAM

È possibile analizzare il codice del modulo di terze parti prima di installarlo, per determinare se utilizza le tabelle MyISAM.

Se hai già installato un&#39;estensione, esegui la seguente query per determinare se il database contiene tabelle MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Cambia il motore di archiviazione in InnoDB

In `db_schema.xml` impostare il `engine` valore dell&#39;attributo per il corrispondente `table` nodo a `innodb`. Per riferimento, vedi [Configura schema dichiarativo > nodo tabella](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) nella documentazione per gli sviluppatori.

Lo schema dichiarativo è stato introdotto in Adobe Commerce sulla versione 2.3 dell’infrastruttura cloud.

## Configura il motore di ricerca consigliato per la ricerca nativa MySQL

Adobe consiglia di impostare sempre Elasticsearch o OpenSearch per il progetto di infrastruttura cloud Adobe Commerce anche se si prevede di configurare uno strumento di ricerca di terze parti per l&#39;applicazione Adobe Commerce. Questa configurazione fornisce un’opzione di fallback nel caso in cui lo strumento di ricerca di terze parti non riesca.

Il motore di ricerca utilizzato dipende dalla versione di Adobe Commerce sul cloud installata:

- Per Adobe Commerce 2.4.4 e versioni successive, utilizzare il servizio OpenSearch per la ricerca nativa MySQL.

- Per le versioni precedenti di Adobe Commerce, utilizza Elasticsearch.

Per determinare quale motore di ricerca è attualmente in uso, esegui il seguente comando:

```bash
./bin/magento config:show catalog/search/engine
```

Per le istruzioni di configurazione, consulta la Guida per gli sviluppatori per Adobe Commerce sul cloud:

- [Configurazione del servizio OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configurazione del servizio Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Evitare attivatori personalizzati

Evita di usare attivatori personalizzati, se possibile.

I trigger vengono utilizzati per registrare le modifiche nelle tabelle di controllo. L’Adobe consiglia di configurare l’applicazione per scrivere direttamente nelle tabelle di controllo anziché utilizzare la funzionalità di attivazione per i motivi seguenti:

- I trigger vengono interpretati come codice e MySQL non li precompila. Aggrappandosi allo spazio di transazione della query, aggiungono il sovraccarico a un parser e a un interprete per ogni query eseguita con la tabella.
- I trigger condividono lo stesso spazio di transazione delle query originali e, mentre tali query sono in concorrenza per i blocchi nella tabella, i trigger competono in modo indipendente sui blocchi in un’altra tabella.

Per informazioni sulle alternative all&#39;utilizzo dei trigger personalizzati, vedi [Utilizzare i trigger MySQL in modo efficace](mysql-triggers-usage.md) nella nostra base di conoscenze di supporto.

## Aggiornamento [!DNL ECE-Tools] alla versione 2002.0.21 o successiva {#ece-tools-version}

Per evitare potenziali problemi con blocchi di stallo, aggiorna ECE-Tools alla versione 2002.0.21 o successiva. Per istruzioni, consulta [Aggiorna `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) nella documentazione per gli sviluppatori.

## Modalità indice commutatore sicuro

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

La sostituzione degli indici genera [!DNL data definition language] (DDL) istruzioni per creare trigger che possono causare blocchi al database. È possibile evitare questo problema inserendo il sito web in modalità di manutenzione e disabilitando i processi cron prima di modificare la configurazione.
Per istruzioni, consulta [Configurare gli indicizzatori](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) in *Guida alla configurazione di Adobe Commerce*.

## Non eseguire istruzioni DDL in Produzione

Evita di eseguire istruzioni DDL nell’ambiente di produzione per evitare conflitti (come modifiche e creazioni di tabelle). La `setup:upgrade` Il processo è un&#39;eccezione.

Se è necessario eseguire un&#39;istruzione DDL, mettere il sito web in modalità manutenzione e disabilitare cron (vedere le istruzioni per cambiare gli indici in modo sicuro nella sezione precedente).

## Abilita archiviazione ordini

Abilita l&#39;archiviazione degli ordini dall&#39;amministratore per ridurre lo spazio necessario per le tabelle Vendite man mano che i dati degli ordini aumentano. L&#39;archiviazione consente di risparmiare spazio su disco MySQL e migliora le prestazioni di checkout.

Vedi [Abilita archiviazione](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) nella documentazione Adobe Commerce Merchant.

## Informazioni aggiuntive

- [Motori di archiviazione MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5 per MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Best practice per risolvere i problemi di prestazioni del database](../maintenance/resolve-database-performance-issues.md)

---
title: Best practice per la configurazione del database per le distribuzioni cloud
description: Scopri come configurare le impostazioni di database e applicazioni per migliorare le prestazioni durante l’implementazione di Adobe Commerce sull’infrastruttura cloud.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Best practice per la configurazione del database

Scopri le best practice per migliorare le prestazioni del database e utilizzarlo in modo efficiente durante l’implementazione di Adobe Commerce sull’infrastruttura cloud.

## Prodotti interessati

Adobe Commerce sull’infrastruttura cloud

## Convertire tutte le tabelle MyISAM in InnoDB

L&#39;Adobe consiglia di utilizzare il motore di database InnoDB. In un&#39;installazione predefinita di Adobe Commerce, tutte le tabelle del database vengono memorizzate utilizzando il motore InnoDB. Tuttavia, alcuni moduli di terze parti (estensioni) possono introdurre tabelle in formato MyISAM. Dopo aver installato un modulo di terze parti, controllare il database per identificare eventuali tabelle in formato `myisam` e convertirle nel formato `innodb`.

### Determinare se un modulo include tabelle MyISAM

Puoi analizzare il codice del modulo di terze parti prima di installarlo, per determinare se utilizza le tabelle MyISAM.

Se è già stata installata un&#39;estensione, eseguire la query seguente per determinare se nel database sono presenti tabelle MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Cambia il motore di archiviazione in InnoDB

Nel file `db_schema.xml` che dichiara la tabella, impostare il valore dell&#39;attributo `engine` per il nodo `table` corrispondente su `innodb`. Per maggiori informazioni, consulta [Configurare lo schema dichiarativo > nodo della tabella](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) nella documentazione per gli sviluppatori.

Lo schema dichiarativo è stato introdotto in Adobe Commerce sulla versione 2.3 dell’infrastruttura cloud.

## Configura il motore di ricerca consigliato per la ricerca MySQL nativa

L’Adobe consiglia di configurare sempre Elasticsearch o OpenSearch per il progetto di infrastruttura cloud di Adobe Commerce, anche se prevedi di configurare uno strumento di ricerca di terze parti per l’applicazione Adobe Commerce. Questa configurazione fornisce un’opzione di fallback nel caso in cui lo strumento di ricerca di terze parti non riesca.

Il motore di ricerca utilizzato dipende dalla versione di Adobe Commerce su cloud installata:

- Per Adobe Commerce 2.4.4 e versioni successive, utilizzare il servizio OpenSearch per la ricerca MySQL nativa.

- Per le versioni precedenti di Adobe Commerce, utilizza Elasticsearch.

Per determinare quale motore di ricerca è attualmente in uso, eseguire il comando seguente:

```bash
./bin/magento config:show catalog/search/engine
```

Per le istruzioni di configurazione, consulta la Guida per gli sviluppatori per Adobe Commerce sul cloud:

- [Configura il servizio OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configura il servizio Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Evita trigger personalizzati

Se possibile, evita di utilizzare trigger personalizzati.

Gli attivatori vengono utilizzati per registrare le modifiche nelle tabelle di controllo. L’Adobe consiglia di configurare l’applicazione per scrivere direttamente nelle tabelle di controllo, anziché utilizzare la funzionalità di attivazione per i seguenti motivi:

- I trigger vengono interpretati come codice e MySQL non li precompila. Collegandosi allo spazio delle transazioni della query, il sovraccarico viene aggiunto a un parser e a un interprete per ogni query eseguita con la tabella.
- I trigger condividono lo stesso spazio di transazione delle query originali e, mentre tali query competono per i blocchi della tabella, i trigger competono in modo indipendente sui blocchi di un&#39;altra tabella.

Per informazioni sulle alternative all&#39;utilizzo di trigger personalizzati, vedere [Trigger MySQL](mysql-configuration.md#triggers).

## Aggiorna [!DNL ECE-Tools] alla versione 2002.0.21 o successiva {#ece-tools-version}

Per evitare potenziali problemi con deadlock cron, aggiorna ECE-Tools alla versione 2002.0.21 o successiva. Per istruzioni, consulta [Aggiornare `ece-tools` versione](https://devdocs.magento.com/cloud/project/ece-tools-update.html) nella documentazione per gli sviluppatori.

## Cambia la modalità di indicizzazione in modo sicuro

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Il passaggio degli indicizzatori genera istruzioni [!DNL data definition language] (DDL) per creare trigger che possono causare blocchi del database. Per evitare questo problema, imposta il sito Web in modalità di manutenzione e disabilita i processi cron prima di modificare la configurazione.
Per istruzioni, vedere [Configurare gli indicizzatori](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) nella *Guida alla configurazione di Adobe Commerce*.

## Non eseguire istruzioni DDL in produzione

Evita di eseguire istruzioni DDL nell’ambiente di produzione per evitare conflitti (come modifiche e creazioni di tabelle). Il processo `setup:upgrade` è un&#39;eccezione.

Se devi eseguire un’istruzione DDL, imposta il sito web in modalità di manutenzione e disattiva cron (consulta le istruzioni per il passaggio sicuro degli indici nella sezione precedente).

## Abilita archiviazione ordini

Abilita l’archiviazione degli ordini dall’amministratore per ridurre lo spazio necessario per le tabelle Vendite in base alla crescita dei dati dell’ordine. L&#39;archiviazione consente di risparmiare spazio su disco MySQL e di migliorare le prestazioni di estrazione.

Consulta [Abilitare l&#39;archiviazione](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) nella documentazione di Adobe Commerce Merchant.

## Informazioni aggiuntive

- [Motori di archiviazione MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5 per MariaDB](../maintenance/mariadb-upgrade.md)
- [Best practice per risolvere i problemi di prestazioni del database](../maintenance/resolve-database-performance-issues.md)

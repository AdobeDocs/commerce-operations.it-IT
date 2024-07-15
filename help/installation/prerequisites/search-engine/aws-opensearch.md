---
title: AWS OpenSearch
description: Segui questi passaggi per configurare il servizio web AWS OpenSearch per le installazioni locali di Adobe Commerce.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 supporta l’utilizzo di cluster del servizio Amazon OpenSearch. Questo servizio succede al servizio Amazon Elasticsearch. In questo argomento viene descritto come configurare Commerce per l&#39;utilizzo di AWS OpenSearch e come migrare i dati da un&#39;istanza di Elasticsearch locale o OpenSearch a un cluster AWS OpenSearch.

## Creazione di un dominio del servizio AWS OpenSearch

Devi innanzitutto stabilire un’istanza di OpenSearch in AWS.
Per istruzioni dettagliate, leggi [Creazione e gestione dei domini del servizio Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html).

## Ottieni dati da AWS OpenSearch

Una volta che tutto è preparato su AWS, è ora di compilarlo con i dati.

Per le installazioni più piccole, è consigliabile creare indici direttamente sull’istanza di AWS per i seguenti motivi:

* Ricreare gli indici è un&#39;operazione rapida.
* Potrebbero esserci incompatibilità di versione tra la vecchia istanza e l’istanza di AWS, che possono essere evitate generando direttamente sull’istanza di AWS.

Per le installazioni più grandi può essere utile eseguire la migrazione degli indici di dati dall’istanza esistente ad AWS. Anche se questo può ridurre i tempi di inattività, esiste ancora un piccolo rischio di problemi di incompatibilità a causa di versioni diverse tra il vecchio server Elasticsearch e AWS.

Non è necessario eseguire la migrazione degli indici, in quanto possono essere facilmente ricreati nell’istanza di AWS.
Tuttavia, durante la migrazione degli indici di dati, assicurati che le versioni di Elasticsearch/OpenSearch siano compatibili.

Per ulteriori informazioni, consulta le istruzioni [Migrazione ad Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) di Amazon.

### Configurare Commerce per OpenSearch

I passaggi per configurare OpenSearch sono descritti nell&#39;argomento [Installazione avanzata](../../advanced.md).

Per verificare il funzionamento della nuova configurazione, verifica direttamente l’endpoint OpenSearch:

1. Crea un prodotto nell’amministratore (ad esempio: sku=&quot;testproduct1&quot;).
1. Reindicizza tramite l’Amministratore.
1. Esegui una query sull’endpoint OpenSearch (presente nell’interfaccia utente di AWS):

   Per ottenere gli indici, aggiungere `/_cat/indices/*?v=true` all&#39;URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Per ottenere i prodotti dall&#39;indice, aggiungere `/magento2docker_product_1/_search?q=*` all&#39;URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Risorse aggiuntive

Per ulteriori informazioni, consulta la [documentazione di OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).

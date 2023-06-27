---
title: AWS OpenSearch
description: Segui questi passaggi per configurare il servizio web AWS OpenSearch per le installazioni locali di Adobe Commerce e Magenti Open Source.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce e Magenti Open Source 2.4.5 supportano l’utilizzo di cluster del servizio Amazon OpenSearch. Questo servizio succede al servizio Amazon Elasticsearch. Questo argomento descrive come configurare Commerce per l’utilizzo di AWS OpenSearch e come migrare i dati da un’istanza di Elasticsearch locale o OpenSearch a un cluster AWS OpenSearch.

## Creazione di un dominio del servizio AWS OpenSearch

Devi innanzitutto stabilire un’istanza di OpenSearch in AWS.
Letto [Creazione e gestione dei domini del servizio Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) per istruzioni dettagliate.

## Ottieni dati da AWS OpenSearch

Una volta che tutto è preparato su AWS, è ora di compilarlo con i dati.

Per le installazioni più piccole, è consigliabile creare indici direttamente sull’istanza di AWS per i seguenti motivi:

* Ricreare gli indici è un&#39;operazione rapida.
* Potrebbero esserci incompatibilità di versione tra la vecchia istanza e l’istanza di AWS, che possono essere evitate generando direttamente sull’istanza di AWS.

Per le installazioni più grandi può essere utile eseguire la migrazione degli indici di dati dall’istanza esistente ad AWS. Anche se questo può ridurre i tempi di inattività, esiste ancora un piccolo rischio di problemi di incompatibilità a causa di versioni diverse tra il vecchio server Elasticsearch e AWS.

Non è necessario eseguire la migrazione degli indici, in quanto possono essere facilmente ricreati nell’istanza di AWS.
Tuttavia, durante la migrazione degli indici di dati, assicurati che le versioni di Elasticsearch/OpenSearch siano compatibili.

Consulta la documentazione di Amazon [Migrazione al servizio Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) istruzioni per ulteriori informazioni.

### Configurare Commerce per OpenSearch

I passaggi per configurare OpenSearch sono descritti nel [Installazione avanzata](../../advanced.md) argomento.

Per verificare il funzionamento della nuova configurazione, verifica direttamente l’endpoint OpenSearch:

1. Crea un prodotto nell’amministratore (ad esempio: sku=&quot;testproduct1&quot;).
1. Reindicizza tramite l’Amministratore.
1. Esegui una query sull’endpoint OpenSearch (presente nell’interfaccia utente di AWS):

   Per ottenere gli indici, aggiungi: `/_cat/indices/*?v=true` all’URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Per ottenere i prodotti dall’indice, aggiungi: `/magento2docker_product_1/_search?q=*` all’URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Risorse aggiuntive

Per ulteriori informazioni, vedere [Documentazione di OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).

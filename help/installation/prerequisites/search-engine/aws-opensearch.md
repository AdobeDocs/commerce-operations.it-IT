---
title: AWS OpenSearch
description: Segui questi passaggi per configurare il servizio Web AWS OpenSearch per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# AWS OpenSearch

Adobe Commerce e Magenti Open Source 2.4.3 supportano l’utilizzo di cluster Amazon OpenSearch Service. Questo servizio sostituisce Amazon Elasticsearch Service. Questo argomento descrive come configurare Commerce per l’utilizzo di AWS OpenSearch e come migrare i dati da un’istanza di Elasticsearch locale o OpenSearch a un cluster AWS OpenSearch.

## Creare un dominio del servizio AWS OpenSearch

È innanzitutto necessario stabilire un&#39;istanza OpenSearch in AWS.
Leggi [Creazione e gestione dei domini del servizio OpenSearch di Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) per istruzioni dettagliate.

## Ottieni dati da AWS OpenSearch

Una volta che tutto è preparato su AWS, è ora di popolarlo con i dati.

Per installazioni più piccole, ti consigliamo di creare indici direttamente sull’istanza AWS per i seguenti motivi:

* Ricreare gli indici è un&#39;operazione rapida.
* Potrebbero esserci incompatibilità di versione tra la vecchia istanza e l’istanza di AWS, e queste possono essere evitate creando direttamente sull’istanza di AWS.

Installazioni più grandi potrebbero voler valutare la migrazione dei loro indici di dati dall’istanza esistente ad AWS. Anche se questo può ridurre i tempi di inattività, esiste ancora un piccolo rischio di incompatibilità dovuto alle diverse versioni tra il vecchio server Elasticsearch e AWS.

Non è necessario eseguire la migrazione degli indici, in quanto questi possono essere facilmente ricreati nell’istanza di AWS.
Tuttavia, durante la migrazione degli indici di dati, assicurati che le versioni di Elasticsearch/OpenSearch siano compatibili.

Consulta Amazon [Migrazione al servizio OpenSearch di Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) istruzioni per ulteriori informazioni.

### Configurare Commerce per OpenSearch

I passaggi per la configurazione di OpenSearch sono descritti nella sezione [Installazione avanzata](../../advanced.md) argomento.

Per verificare che la nuova configurazione funzioni, verifica direttamente l’endpoint OpenSearch:

1. Crea un prodotto nell’amministratore (ad esempio: sku=&quot;testproduct1&quot;).
1. Reindicizza tramite l&#39;amministratore.
1. Esegui una query sull’endpoint OpenSearch (nell’interfaccia utente di AWS):

   Per ottenere gli indici, aggiungi: `/_cat/indices/*?v=true` all’URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Per ottenere i prodotti dall&#39;indice, aggiungi: `/magento2docker_product_1/_search?q=*` all’URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Risorse aggiuntive

Per ulteriori informazioni, consulta la sezione [Documentazione di OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).

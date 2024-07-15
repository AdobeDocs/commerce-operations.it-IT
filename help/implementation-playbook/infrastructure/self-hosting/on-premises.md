---
title: Infrastruttura locale
description: Scopri l’infrastruttura locale di Adobe Commerce e i servizi cloud di terze parti.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Infrastruttura Adobe Commerce on-premise

Le motivazioni per avviare una nuova implementazione Adobe Commerce o per spostare sul cloud un’implementazione Adobe Commerce on-premise esistente sono numerose, ma i fattori strategici più comuni sono la riduzione delle spese in conto capitale, la riduzione dei costi correnti, il miglioramento della scalabilità e dell’elasticità, il miglioramento del time-to-market e il raggiungimento di miglioramenti in termini di sicurezza e conformità.

Il diagramma seguente mostra l’architettura di riferimento per l’implementazione di Adobe Commerce on-premise sull’infrastruttura AWS. Altri fornitori di servizi cloud come Azure, Google Cloud e Alibaba Cloud condividono una progettazione dell’infrastruttura e servizi omologhi simili.

![Diagramma che mostra l&#39;infrastruttura Adobe Commerce con hosting autonomo sui servizi cloud di terze parti](/help/assets/playbooks/on-premises-infrastructure.svg)

Approfondiamo i ruoli e le funzioni di ogni aspetto dell&#39;infrastruttura mostrata sopra:

1. Amazon Route 53 fornisce la configurazione DNS.

1. AWS WAF è un firewall per applicazioni web che protegge Adobe Commerce da attacchi web comuni.

1. Amazon CloudFront è una rete CDN (Fast Content Delivery Network) che consente di velocizzare la distribuzione di contenuti web statici e dinamici.

1. Il primo load balancer di applicazioni Elastic Load Balancing distribuisce il traffico tra le istanze di Vernice in un gruppo di scalabilità automatica AWS in più aree di disponibilità.

1. La cache di vernice è un acceleratore di applicazioni web che memorizza nella cache il proxy inverso HTTP. La versione Enterprise, disponibile tramite AWS Marketplace, è consigliata in quanto dispone di funzioni migliori per supportare i back-end cloud e l’eliminazione della cache tra host dinamici.

1. Il secondo load balancer dell&#39;applicazione di bilanciamento del carico elastico distribuisce il traffico dalla cache di vernice nel gruppo di scalabilità automatica AWS delle istanze Adobe Commerce in più aree di disponibilità.

1. Installa la versione più recente di Adobe Commerce sulle istanze di Amazon EC2. L’installazione è costituita dall’applicazione Adobe Commerce, dal server web Nginx e dal PHP. Create l&#39;Amazon Machine Image (AMI) per avviare nuove istanze in un gruppo di ridimensionamento automatico.

1. Amazon Elasticsearch Service è un servizio di Elasticsearch gestito per la ricerca nel catalogo Adobe Commerce.

1. Amazon ElastiCache per Redis fornisce un livello di caching per il database.

1. Utilizza Amazon Aurora o AmazonRDS per semplificare l’amministrazione del database (inclusa la configurazione multi-master e l’elevata disponibilità).

1. EFSMount Target facilita la mappatura del file system elastico di Amazon (AmazonEFS) sulle istanze di vernice e Adobe Commerce.

1. Utilizza Amazon EFS per accedere alla configurazione condivisa tra le risorse multimediali condivise e Vernice tra le istanze Adobe Commerce.

## Servizi cloud

Oltre a fornire una piattaforma tecnologica di supporto per l&#39;abilitazione dei processi DevOps su AWS nell&#39;ambiente Adobe Commerce, AWS fornisce una raccolta di servizi in grado di fornire (in assenza di) o potenziare le soluzioni di gestione della configurazione software (SCM) esistenti. Questo include AWSCodeCommit, AWSCodeBuild, AWSCodePipeline e AWSCodeDeploy, che consentono il controllo del codice sorgente gestito, la compilazione, l&#39;integrazione continua/distribuzione continua (CI/CD) e i servizi di distribuzione.

## Migrazione cloud

La proposta di valore per la migrazione di Adobe Commerce ad AWS è ulteriormente migliorata dalla disponibilità di diversi servizi che forniscono informazioni operative approfondite e agilità. Ciò che intendiamo per approfondimento operativo della piattaforma non solo da un punto di vista tecnico (ad esempio, richieste all’ora), ma anche da un punto di vista operativo (ad esempio, ordini all’ora), in particolare quando le due serie di dati possono essere unite. Questo fornisce un’analisi quasi in tempo reale delle prestazioni della campagna, dei costi operativi della piattaforma e di un numero pressoché infinito di altri indicatori.

La configurazione di Adobe Commerce per AWS può sostituire dipendenze di applicazioni specifiche con alternative completamente gestite disponibili nel cloud. Ad esempio, invece di ospitare direttamente un database relazionale sulle istanze EC2, il database per molte applicazioni può essere facilmente sostituito da Amazon Relational Database Service (AmazonRDS). Il vantaggio di questa strategia è che la responsabilità operativa dei componenti indifferenziati può essere trasferita ad AWS senza richiedere modifiche significative all’applicazione di base.

Sono disponibili diverse opzioni di distribuzione per eseguire Adobe Commerce su AWS. La scelta più appropriata dipende dai requisiti di costo, scalabilità, disponibilità e flessibilità, nonché dalle competenze AWS e Adobe Commerce della tua organizzazione.

{{$include /help/_includes/hosting-related-links.md}}

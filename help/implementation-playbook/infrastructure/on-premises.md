---
title: Infrastruttura interna
description: Scopri l’infrastruttura on-premise di Adobe Commerce e i servizi cloud di terze parti.
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Infrastruttura on-premise Adobe Commerce

Le motivazioni per avviare una nuova implementazione di Adobe Commerce o spostare un&#39;implementazione Adobe Commerce esistente sul cloud sono numerose, ma i fattori strategici più comuni sono la riduzione della spesa in capitale, la riduzione dei costi correnti, il miglioramento della scalabilità e dell&#39;elasticità, il miglioramento del time-to-market e il miglioramento della sicurezza e della conformità.

Il diagramma seguente illustra l’architettura di riferimento per l’implementazione on-premise di Adobe Commerce nell’infrastruttura AWS. Altri provider di cloud come Azure, Google Cloud e Alibaba Cloud condividono un progetto di infrastruttura e servizi omologhi simili.

![Diagramma che mostra l’infrastruttura Adobe Commerce self-hosting su servizi cloud di terze parti](../../assets/playbooks/on-premises-infrastructure.svg)

Approfondiamo i ruoli e le funzioni di ogni aspetto dell’infrastruttura sopra illustrata:

1. Amazon Route 53 fornisce la configurazione DNS.

1. AWS WAF è un firewall per applicazioni web che protegge Adobe Commerce dalle comuni applicazioni web.

1. Amazon CloudFront è una rete per la distribuzione rapida dei contenuti (CDN) che velocizza la distribuzione dei contenuti web statici e dinamici.

1. Il primo sistema di bilanciamento del carico dell&#39;applicazione Elastic Load Balancing distribuisce il traffico tra le istanze Varnish in un gruppo di ridimensionamento automatico AWS in più aree di disponibilità.

1. Varnish Cache è un acceleratore dell&#39;applicazione web che memorizza in cache il proxy inverso HTTP. La versione enterprise, disponibile tramite AWS marketplace, è consigliata in quanto dispone di funzioni migliori per supportare i backend cloud e l’eliminazione della cache tra gli host dinamici.

1. Il secondo servizio di bilanciamento del carico elastico dell’applicazione distribuisce il traffico dalla cache vernish al gruppo di scalabilità automatica AWS delle istanze Adobe Commerce in più aree di disponibilità.

1. Installa la versione più recente di Magenti Open Source o Adobe Commerce sulle istanze di Amazon EC2. L&#39;installazione è costituita dall&#39;applicazione Adobe Commerce, dal server Web Nginx e da PHP. Crea l’immagine macchina Amazon (AMI) per avviare nuove istanze in un gruppo di ridimensionamento automatico.

1. Amazon Elasticsearch Service è un servizio di Elasticsearch gestito per la ricerca nel catalogo Adobe Commerce.

1. Amazon ElastiCache per Redis fornisce un livello di memorizzazione in cache per il database.

1. Utilizza Amazon Aurora o AmazonRDS per semplificare l’amministrazione del database (inclusa l’alta disponibilità e la configurazione multi-master).

1. EFSMount Target facilita la mappatura del file system elastico (AmazonEFS) di Amazon alle istanze Varnish e Adobe Commerce.

1. Utilizza Amazon EFS per accedere alla configurazione condivisa tra le istanze Adobe Commerce di Varnish e le risorse multimediali condivise.

## Servizi cloud

Oltre a fornire una piattaforma tecnologica di supporto per l&#39;abilitazione dei processi DevOps su AWS in tutto l&#39;ambiente Adobe Commerce, AWS fornisce una raccolta di servizi che possono fornire (in assenza di) o potenziare le soluzioni SCM (Software Configuration Management) esistenti. Ciò include AWSCodeCommit, AWSCodeBuild, AWSCodePipeline e AWSCodeDeploy, che consente un controllo del codice sorgente gestito, una build, integrazione continua/distribuzione continua (CI/CD) e servizi di distribuzione.

## Migrazione cloud

La proposta di valore per la migrazione di Adobe Commerce ad AWS è ulteriormente migliorata dalla disponibilità di diversi servizi che forniscono informazioni operative e agilità. Ciò che intendiamo è un&#39;analisi operativa della piattaforma da un punto di vista non solo tecnico (ad esempio, richieste all&#39;ora), ma anche operativo (ad esempio, ordini all&#39;ora), in particolare quando le due serie di dati possono essere sposate. Questo fornisce un&#39;analisi in tempo quasi reale delle prestazioni della campagna, dei costi operativi della piattaforma e un numero quasi infinito di altri indicatori.

La configurazione di Adobe Commerce in AWS può sostituire dipendenze specifiche dell’applicazione con alternative completamente gestite disponibili nel cloud. Ad esempio, anziché ospitare direttamente un database relazionale sulle istanze EC2, il database per molte applicazioni può essere facilmente sostituito dal servizio di database relazionale di Amazon (AmazonRDS). Il vantaggio di questa strategia è che la responsabilità operativa dei componenti indifferenziati può essere scaricata in AWS senza richiedere modifiche significative all’applicazione core.

Sono disponibili diverse opzioni di distribuzione per l’esecuzione di Adobe Commerce (versioni sia di Magento Open Source che di Adobe Commerce) su AWS. La scelta più appropriata dipende dalle tue esigenze in termini di costi, scalabilità, disponibilità e flessibilità, nonché dalle competenze AWS e Adobe Commerce della tua organizzazione.

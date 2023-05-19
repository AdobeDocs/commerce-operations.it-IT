---
title: Soluzione per la suddivisione delle prestazioni del database
description: Scopri la soluzione di database diviso per Adobe Commerce e Magenti Open Source.
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Panoramica della soluzione di database suddiviso

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce offre diversi vantaggi in termini di scalabilità, tra cui la possibilità di utilizzare tre database master separati per diverse aree funzionali dell’applicazione Commerce.

Il checkout, gli ordini e i dati dei prodotti possono utilizzare un database master separato che è possibile replicare. Questa separazione consente di scalare in modo indipendente il carico dalle attività di checkout sul sito web, gestione degli ordini, navigazione sul sito web e merchandising, in base alle esigenze. Queste modifiche forniscono una notevole flessibilità nelle modalità di scalabilità del livello del database.

>[!INFO]
>
>Adobe Commerce su infrastruttura cloud _non_ supporta questa funzione.

Il `ResourceConnections` La classe fornisce la connessione unificata del database MySQL all&#39;applicazione Commerce. Per le query sui database master, viene implementato il modello di database CQRS (Command Query Responsibility Segregation). Questo modello gestisce la logica per l&#39;instradamento delle query di lettura e scrittura ai database appropriati. Gli sviluppatori non devono sapere quale configurazione viene utilizzata e non esistono connessioni separate al database di lettura e scrittura.

Se si imposta la replica di database facoltativa, si otterranno i seguenti vantaggi:

- Backup dei dati
- Analisi dei dati senza influire sul database principale
- Scalabilità

I database MySQL vengono replicati in modo asincrono, il che significa che non è necessario che gli slave siano connessi in modo permanente per ricevere gli aggiornamenti dal master.

Nella figura seguente viene illustrato il funzionamento di questa feature.

![Adobe Commerce utilizza database diversi per memorizzare le tabelle](../../assets/configuration/split-db-diagram-ee.png)

In Magenti Open Source viene utilizzato un solo database master.

Adobe Commerce utilizza tre database master e un numero configurabile di database slave per la replica. Adobe Commerce dispone di un&#39;unica interfaccia per le connessioni ai database, che offre prestazioni più veloci e una migliore scalabilità.

## Opzioni di configurazione

A causa del modo in cui è progettata la soluzione di prestazioni del database suddiviso, il codice personalizzato e i componenti installati _non può_ eseguire una delle operazioni seguenti:

- Scrivere direttamente nel database (è necessario utilizzare l&#39;interfaccia del database di Adobe Commerce)
- Utilizzare JOIN che influiscono sui database delle vendite o delle offerte
- Utilizzare le chiavi esterne per le tabelle nei database di pagamento, vendite o principali

>[!WARNING]
>
>Contatta gli sviluppatori di componenti per verificare se i loro componenti eseguono una delle operazioni precedenti. In tal caso, è necessario scegliere solo una delle seguenti opzioni:
>
>- Chiedi agli sviluppatori di componenti di aggiornare i loro componenti.
>- Utilizzare i componenti così come sono _senza_ la soluzione di database diviso.
>- Rimuovere i componenti in modo da poter utilizzare la soluzione di database suddiviso.


Ciò significa anche che è possibile:

- Configurare la soluzione di database suddiviso _prima di_ mettere Commerce in produzione.

   L’Adobe consiglia di configurare i database suddivisi il prima possibile dopo l’installazione del software Commerce.

- [Configura manualmente](multi-master-manual.md) la soluzione di database diviso.

   È necessario eseguire questa attività se sono già stati installati componenti o se Commerce è già in produzione. (_Do not_ aggiornare un sistema di produzione; apportare gli aggiornamenti in un sistema di sviluppo e sincronizzare le modifiche dopo averle testate.)

   >[!WARNING]
   >
   >È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell’istanza di database principale. Il [`magento setup:backup --db`](../../installation/tutorials/backup.md) nelle opzioni Command e Admin non viene eseguito il backup delle tabelle aggiuntive.

## Prerequisiti

Il database diviso richiede l&#39;impostazione di tre database master MySQL su qualsiasi host (tutti e tre sul server Commerce, ogni database su un server separato e così via). Queste sono le _principale_ e vengono utilizzati come segue:

- Un database master per le tabelle di estrazione
- Un database principale per le tabelle di vendita (denominato anche _Sistema di gestione ordini_, o _OMS_, tabelle)
- Un database master per le altre tabelle dell’applicazione Commerce 2

Inoltre, è possibile impostare un numero qualsiasi di _schiavo_ database che fungono da load balancer e backup.

In questa guida viene descritto come impostare solo i database master. Se lo si desidera, vengono forniti esempi di configurazioni e riferimenti per l&#39;impostazione di database slave.

In questa guida vengono denominati i tre database principali:

- `magento_quote`
- `magento_sales`
- `magento`

È possibile assegnare ai database qualsiasi nome si desideri.

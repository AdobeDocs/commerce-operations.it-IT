---
title: Soluzione per le prestazioni del database diviso
description: Scopri la soluzione di database suddiviso per Adobe Commerce e Magenti Open Source.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# Panoramica della soluzione di database diviso

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce offre diversi vantaggi in termini di scalabilità, tra cui la possibilità di utilizzare tre database master distinti per diverse aree funzionali dell’applicazione Commerce.

L&#39;estrazione, gli ordini e i dati di prodotto possono utilizzare un database principale separato che è possibile replicare facoltativamente. Questa separazione scala in modo indipendente il carico dai checkout del sito web, le attività di gestione degli ordini, la navigazione nel sito web e le attività di merchandising, a seconda delle tue esigenze. Queste modifiche forniscono una notevole flessibilità nel modo in cui il livello di database può essere ridimensionato.

>[!INFO]
>
>L’infrastruttura cloud di Adobe Commerce funziona _not_ supporta questa funzione.

La `ResourceConnections` La classe fornisce la connessione al database MySQL unificato all&#39;applicazione Commerce. Per le query ai database master, implementiamo il pattern di database CQRS (Command Query Responsibility Segregation). Questo pattern gestisce la logica per l’indirizzamento delle query di lettura e scrittura ai database appropriati. Gli sviluppatori non devono sapere quale configurazione viene utilizzata e non esistono connessioni di database in lettura e scrittura separate.

Se si imposta la replica di database opzionale, si ottengono i seguenti vantaggi:

- Backup dei dati
- Analisi dei dati senza influire sul database master
- Scalabilità

I database MySQL vengono replicati in modo asincrono, il che significa che gli slave non devono essere connessi in modo permanente per ricevere gli aggiornamenti dal master.

La figura seguente mostra come funziona questa funzione.

![Adobe Commerce utilizza diversi database per memorizzare le tabelle](../../assets/configuration/split-db-diagram-ee.png)

Al Magento Open Source, viene utilizzato un solo database master.

Adobe Commerce utilizza tre database master e un numero configurabile di database slave per la replica. Adobe Commerce dispone di un’unica interfaccia per le connessioni al database, che consente prestazioni più veloci e una migliore scalabilità.

## Opzioni di configurazione

A causa del modo in cui è progettata la soluzione di prestazioni del database diviso, il codice personalizzato e i componenti installati _impossibile_ effettua una delle seguenti operazioni:

- Scrivere direttamente nel database (è invece necessario utilizzare l&#39;interfaccia del database Adobe Commerce)
- Utilizzare JOIN che influenzano le vendite o [preventivo](https://glossary.magento.com/quote) database
- Utilizzare chiavi esterne per le tabelle nei database di pagamento, di vendita o principale

>[!WARNING]
>
>Contatta gli sviluppatori di componenti per verificare se i loro componenti eseguono una delle operazioni precedenti. In tal caso, è necessario scegliere solo una delle seguenti opzioni:
>
>- Chiedi agli sviluppatori di componenti di aggiornare i loro componenti.
>- Utilizza i componenti così come sono _senza_ la soluzione di database diviso.
>- Rimuovi i componenti in modo da poter utilizzare la soluzione di database divisa.


Ciò significa anche che è possibile:

- Configurare la soluzione di database diviso _prima_ l&#39;introduzione del commercio nella produzione.

   Adobe consiglia di configurare i database suddivisi il prima possibile dopo l’installazione del software Commerce.

- [Configurazione manuale](multi-master-manual.md) la soluzione di database diviso.

   Devi eseguire questa attività se hai già installato componenti o se Commerce è già in produzione. (_Non_ aggiornare un sistema di produzione; apporta gli aggiornamenti in un sistema di sviluppo e sincronizza le modifiche dopo averle testate).

   >[!WARNING]
   >
   >È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell’istanza di database principale. La [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) Le opzioni di comando e amministratore non consentono di eseguire il backup delle tabelle aggiuntive.

## Prerequisiti

Il database suddiviso richiede l&#39;impostazione di tre database master MySQL su qualsiasi host (tutti e tre sul server Commerce, ogni database su un server separato e così via). Questi sono _maestro_ database e sono utilizzati come segue:

- Un database master per [pagamento](https://glossary.magento.com/checkout) tabelle
- Un database principale per le tabelle di vendita (noto anche come _Sistema di gestione degli ordini_ oppure _OMS_, tabelle)
- Un database principale per il resto delle tabelle dell&#39;applicazione Commerce 2

Inoltre, è possibile impostare un numero qualsiasi di _secondario_ database che fungono da load balancer e backup.

Questa guida illustra come impostare solo i database master. Forniamo configurazioni di esempio e riferimenti per la configurazione dei database slave, se lo desideri.

In questa guida, i tre database master sono denominati:

- `magento_quote`
- `magento_sales`
- `magento`

(È possibile denominare i database come si desidera.)

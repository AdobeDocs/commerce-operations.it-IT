---
title: Registrazione personalizzata
description: Scopri come individuare gli errori utilizzando la registrazione personalizzata.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Panoramica registrazione personalizzata

I registri forniscono visibilità sui processi di sistema; ad esempio, informazioni di debug che consentono di comprendere quando si è verificato un errore o cosa ha causato l’errore.

Questo argomento si concentra sulla registrazione basata su file, anche se Commerce offre la flessibilità di archiviare i registri anche nel database.

L&#39;Adobe consiglia di utilizzare la registrazione centralizzata delle applicazioni per i motivi seguenti:

- Consente lo storage dei registri su un server diverso da quello dell&#39;applicazione e riduce le operazioni di I/O del disco, semplificando il supporto del server dell&#39;applicazione.

- Rende più efficace l’elaborazione dei dati dei registri utilizzando strumenti speciali, ad esempio [Logstash], [Logplex], o [fluente]senza impatto su un server di produzione.

   >[!INFO]
   >
   >L’Adobe non consiglia né approva alcuna particolare soluzione di registrazione.

## Conformità PSR-3

Il [Standard PSR-3][laminas] definisce un&#39;interfaccia PHP comune per le librerie di registrazione. L&#39;obiettivo principale di PSR-3 è consentire alle librerie di ricevere `Psr\Log\LoggerInterface` gli oggetti e scrivervi i registri in modo semplice e universale.

Questo consente di sostituire facilmente l’implementazione senza preoccuparsi che possa interrompere il codice dell’applicazione. Inoltre, garantisce che un componente personalizzato funzioni anche quando l’implementazione del registro viene modificata in una versione futura del sistema.

## Monologo

Commerce 2 è conforme allo standard PSR-3. Per impostazione predefinita, Commerce utilizza [Monologo]. Monologo implementato come preferenza per `Psr\Log\LoggerInterface` nell’applicazione Commerce [`di.xml`][di].

Monologo è una popolare soluzione di registrazione PHP con una vasta gamma di gestori che consentono di creare strategie di registrazione avanzate. Di seguito è riportato un riepilogo del funzionamento di Monolog.

Un monologo _logger_ è un canale con un proprio set di _handler_. Monolog ha molti gestori, tra cui:

- Accedere a file e syslog
- Inviare avvisi e messaggi di posta elettronica
- Registrazione di server specifici e registrazione in rete
- Accesso allo sviluppo (integrazione con FireBug e Chrome Logger, tra gli altri)
- Accedi al database

Ogni gestore può elaborare il messaggio di input e interrompere la propagazione oppure passare il controllo al gestore successivo in una catena.

I messaggi del registro possono essere elaborati in molti modi diversi. Ad esempio, è possibile archiviare tutte le informazioni di debug in un file su disco, inserire i messaggi con livelli di registro superiori in un database e infine inviare messaggi con livello di registro &quot;critico&quot; tramite posta elettronica.

Altri canali possono avere un set diverso di gestori e logica.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluente]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monologo]: https://github.com/Seldaek/monolog

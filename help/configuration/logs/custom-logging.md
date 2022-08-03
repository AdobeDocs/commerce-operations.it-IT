---
title: Registrazione personalizzata
description: Scopri come indagare gli errori utilizzando la registrazione personalizzata.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Panoramica sulla registrazione personalizzata

I registri forniscono visibilità ai processi di sistema; ad esempio, informazioni di debug che consentono di comprendere quando si è verificato un errore o cosa ha generato l’errore.

Questo argomento si concentra sulla registrazione basata su file, anche se Commerce offre la flessibilità di memorizzare i registri anche nel database.

L&#39;Adobe consiglia di utilizzare la registrazione centralizzata delle applicazioni per i motivi seguenti:

- Consente lo storage dei log su un server diverso dall&#39;application server e riduce le operazioni di I/O su disco, semplificando il supporto dell&#39;application server.

- Rende l&#39;elaborazione dei dati dei registri più efficace utilizzando strumenti speciali, come [Logstash], [Logplex]oppure [fluido]- senza impatto su un server di produzione.

   >[!INFO]
   >
   >L’Adobe non consiglia né approva alcuna particolare soluzione di registrazione.

## Conformità PSR-3

La [Standard PSR-3][laminas] definisce un&#39;interfaccia PHP comune per le librerie di log. L&#39;obiettivo principale del PSR-3 è quello di consentire alle librerie di ricevere un `Psr\Log\LoggerInterface` oggetto e scrivi i log ad esso in modo semplice e universale.

Questo consente di sostituire facilmente l&#39;implementazione senza preoccuparsi che tale sostituzione possa interrompere il codice dell&#39;applicazione. Garantisce inoltre che un componente personalizzato funzioni anche quando l’implementazione del registro viene modificata in una versione futura del sistema.

## Monologo

Commerce 2 è conforme allo standard PSR-3. Per impostazione predefinita, Commerce utilizza [Monologo]. Monolog implementato come preferenza per `Psr\Log\LoggerInterface` nell’applicazione Commerce [`di.xml`][di].

Monolog è una popolare soluzione di registrazione PHP con un&#39;ampia gamma di gestori che consentono di creare strategie di registrazione avanzate. Di seguito è riportato un riassunto di come funziona Monolog.

Un monologo _logger_ è un canale con il proprio set di _gestori_. Monolog ha molti gestori, tra cui:

- Accedi a file e syslog
- Inviare avvisi ed e-mail
- Registrare server specifici e registrare in rete
- Accesso allo sviluppo (integrazione con FireBug e Chrome Logger, tra gli altri)
- Accedere al database

Ogni gestore può elaborare il messaggio di input e interrompere la propagazione oppure passare il controllo al gestore successivo in una catena.

I messaggi di registro possono essere elaborati in diversi modi. Ad esempio, è possibile memorizzare tutte le informazioni di debug in un file su disco, inserire i messaggi con livelli di log più alti in un database e infine inviare messaggi con livello di log &quot;critico&quot; tramite e-mail.

Altri canali possono avere un set diverso di gestori e logiche.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluido]: http://www.fluentd.org
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monologo]: https://github.com/Seldaek/monolog

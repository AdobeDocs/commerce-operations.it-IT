---
title: Panoramica delle code di messaggi
description: Scopri il framework della coda di messaggi e come funziona con l’applicazione Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Panoramica delle code di messaggi

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Definisce inoltre i [consumer](consumers.md) che riceveranno i messaggi in modo asincrono. MQF supporta più broker di messaggistica:

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** - Gestore di messaggistica primario, che fornisce una piattaforma scalabile per l&#39;invio e la ricezione di messaggi. Include un meccanismo per l’archiviazione dei messaggi non consegnati ed è basato sulla specifica AMQP (Advanced Message Queuing Protocol) 0.9.1.
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** - Gestore di messaggistica alternativo che utilizza il protocollo STOMP (Simple Text Oriented Messaging Protocol) per la messaggistica affidabile e scalabile. Introdotto in Adobe Commerce 2.4.5 e versioni successive.

## RabbitMQ (AMQP)

Il diagramma seguente illustra il framework della coda di messaggi:

![Framework coda messaggi](../../assets/configuration/mq-framework.png)

- Un editore è un componente che invia messaggi a uno scambio. Sa a quale scambio pubblicare e il formato dei messaggi che invia.

- Uno scambio riceve messaggi dagli editori e li invia alle code. Sebbene [!DNL RabbitMQ] supporti più tipi di scambi, Commerce utilizza solo gli scambi di argomenti. Un argomento include una chiave di instradamento, che contiene stringhe di testo separate da punti. Il formato del nome di un argomento è `string1.string2`, ad esempio `customer.created` o `customer.sent.email`.

  Il broker consente di utilizzare i caratteri jolly per impostare le regole per l’inoltro dei messaggi. È possibile utilizzare un asterisco (`*`) per sostituire _una_ stringa o un cancelletto (`#`) per sostituire 0 o più stringhe. Ad esempio, `customer.*` filtrerebbe su `customer.create` e `customer.delete`, ma non su `customer.sent.email`. Tuttavia `customer.#` filtrerebbe su `customer.create`, `customer.delete` e `customer.sent.email`.

- Una coda è un buffer che memorizza i messaggi.

- Un consumatore riceve messaggi. Sa quale coda consumare. Può mappare i processori del messaggio a una coda specifica.

## Apache ActiveMQ Artemis (STOMP)

In alternativa a RabbitMQ, Adobe Commerce supporta anche [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/) come broker di messaggistica utilizzando il protocollo STOMP (Simple Text Oriented Messaging Protocol).

>[!NOTE]
>
>ActiveMQ Artemis è stato introdotto in Adobe Commerce 2.4.5 e versioni successive.

Il diagramma seguente illustra il framework STOMP con ActiveMQ Artemis:

![Framework STOMP](../../assets/configuration/stomp-framework.png)

### Componenti framework STOMP

- Un **editore** è un componente che invia messaggi a una destinazione (coda o argomento). Sa a quale destinazione pubblicare e il formato dei messaggi che invia.

- Una **destinazione** in STOMP svolge un ruolo simile agli scambi in AMQP, ricevendo messaggi dagli editori e instradandoli. STOMP utilizza l&#39;indirizzamento di destinazione diretto con un modello di denominazione gerarchica utilizzando i punti: ad esempio, `customer.created` o `inventory.updated`.

  Adobe Commerce utilizza la modalità di indirizzamento **ANYCAST** per le destinazioni STOMP, che fornisce la consegna di messaggi point-to-point. In modalità ANYCAST, i messaggi vengono inviati a un solo consumatore da un pool di consumatori disponibili, consentendo il bilanciamento del carico e la distribuzione del lavoro tra più istanze.

- Una **coda** è un buffer che memorizza i messaggi. Grazie all&#39;indirizzamento ANYCAST, la coda assicura che i messaggi vengano inviati a un solo utente, anche quando più utenti sono connessi alla stessa destinazione.

- Un **consumatore** riceve messaggi dalle destinazioni. Sa a quale destinazione abbonarsi e può elaborare i messaggi con diverse modalità di riconoscimento (auto, client o client-individuale).

## Scheda MySQL (fallback)

È inoltre possibile configurare un sistema di code di messaggi di base senza utilizzare broker di messaggi esterni. In questo sistema, un adattatore MySQL memorizza i messaggi nel database. Tre tabelle di database (`queue`, `queue_message` e `queue_message_status`) gestiscono il carico di lavoro della coda messaggi. I lavori di cron garantiscono che i consumatori siano in grado di ricevere messaggi. Questa soluzione non è molto scalabile. Se possibile, per gli ambienti di produzione è necessario utilizzare gestori di messaggi esterni come [!DNL RabbitMQ] o Apache ActiveMQ Artemis.

## Informazioni correlate

Per le istruzioni di installazione e configurazione:

- [Installare e configurare RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [Installare e configurare ActiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [Gestire le code dei messaggi](manage-message-queues.md)
- [Consumatori coda messaggi](consumers.md)

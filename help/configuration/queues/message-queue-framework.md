---
title: Panoramica delle code di messaggi
description: Scopri il framework della coda di messaggi e come funziona con l’applicazione Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Panoramica delle code di messaggi

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Inoltre, definisce [consumatori](consumers.md) che riceverà i messaggi in modo asincrono. MQF utilizza [[!DNL RabbitMQ]](https://www.rabbitmq.com) as the messaging broker, che fornisce una piattaforma scalabile per l’invio e la ricezione di messaggi. Include inoltre un meccanismo per l’archiviazione dei messaggi non consegnati. [!DNL RabbitMQ] è basato sulla specifica AMQP 0.9.1.

Il diagramma seguente illustra il framework della coda di messaggi:

![Framework coda messaggi](../../assets/configuration/mq-framework.png)

- Un editore è un componente che invia messaggi a uno scambio. Sa a quale scambio pubblicare e il formato dei messaggi che invia.

- Uno scambio riceve messaggi dagli editori e li invia alle code. Anche se [!DNL RabbitMQ] supporta più tipi di scambi, Commerce utilizza solo gli scambi di argomenti. Un argomento include una chiave di instradamento, che contiene stringhe di testo separate da punti. Il formato del nome di un argomento è `string1.string2`: ad esempio, `customer.created` o `customer.sent.email`.

  Il broker consente di utilizzare i caratteri jolly per impostare le regole per l’inoltro dei messaggi. È possibile utilizzare un asterisco (`*`) da sostituire _uno_ stringa o cancelletto (`#`) per sostituire 0 o più stringhe. Ad esempio: `customer.*` filtrerebbe per `customer.create` e `customer.delete`, ma non `customer.sent.email`. Tuttavia `customer.#` filtrerebbe per `customer.create`,  `customer.delete`, e `customer.sent.email`.

- Una coda è un buffer che memorizza i messaggi.

- Un consumatore riceve messaggi. Sa quale coda consumare. Può mappare i processori del messaggio a una coda specifica.

È inoltre possibile configurare un sistema di code di messaggi di base senza utilizzare [!DNL RabbitMQ]. In questo sistema, un adattatore MySQL memorizza i messaggi nel database. Tre tabelle di database (`queue`, `queue_message`, e `queue_message_status`) gestire il carico di lavoro della coda dei messaggi. I lavori di cron garantiscono che i consumatori siano in grado di ricevere messaggi. Questa soluzione non è molto scalabile. [!DNL RabbitMQ] devono essere utilizzati quando possibile.

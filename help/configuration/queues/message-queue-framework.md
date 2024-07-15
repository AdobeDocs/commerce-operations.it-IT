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

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Definisce inoltre i [consumer](consumers.md) che riceveranno i messaggi in modo asincrono. MQF utilizza [[!DNL RabbitMQ]](https://www.rabbitmq.com) come broker di messaggistica, che fornisce una piattaforma scalabile per l&#39;invio e la ricezione di messaggi. Include inoltre un meccanismo per l’archiviazione dei messaggi non consegnati. [!DNL RabbitMQ] è basato sulla specifica AMQP 0.9.1.

Il diagramma seguente illustra il framework della coda di messaggi:

![Framework coda messaggi](../../assets/configuration/mq-framework.png)

- Un editore è un componente che invia messaggi a uno scambio. Sa a quale scambio pubblicare e il formato dei messaggi che invia.

- Uno scambio riceve messaggi dagli editori e li invia alle code. Sebbene [!DNL RabbitMQ] supporti più tipi di scambi, Commerce utilizza solo gli scambi di argomenti. Un argomento include una chiave di instradamento, che contiene stringhe di testo separate da punti. Il formato del nome di un argomento è `string1.string2`, ad esempio `customer.created` o `customer.sent.email`.

  Il broker consente di utilizzare i caratteri jolly per impostare le regole per l’inoltro dei messaggi. È possibile utilizzare un asterisco (`*`) per sostituire _una_ stringa o un cancelletto (`#`) per sostituire 0 o più stringhe. Ad esempio, `customer.*` filtrerebbe su `customer.create` e `customer.delete`, ma non su `customer.sent.email`. Tuttavia `customer.#` filtrerebbe su `customer.create`, `customer.delete` e `customer.sent.email`.

- Una coda è un buffer che memorizza i messaggi.

- Un consumatore riceve messaggi. Sa quale coda consumare. Può mappare i processori del messaggio a una coda specifica.

È inoltre possibile configurare un sistema di coda di messaggi di base senza utilizzare [!DNL RabbitMQ]. In questo sistema, un adattatore MySQL memorizza i messaggi nel database. Tre tabelle di database (`queue`, `queue_message` e `queue_message_status`) gestiscono il carico di lavoro della coda messaggi. I lavori di cron garantiscono che i consumatori siano in grado di ricevere messaggi. Questa soluzione non è molto scalabile. Se possibile, utilizzare [!DNL RabbitMQ].

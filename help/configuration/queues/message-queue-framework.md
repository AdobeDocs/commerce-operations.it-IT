---
title: Panoramica delle code di messaggi
description: Scopri il framework della coda dei messaggi e come funziona con l’applicazione Adobe Commerce e Magenti Open Source.
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Panoramica delle code di messaggio

MQF (Message Queue Framework) è un sistema che consente [modulo](https://glossary.magento.com/module) per pubblicare i messaggi nelle code. Definisce anche i consumatori che riceveranno i messaggi in modo asincrono. L&#39;MQF utilizza [[!DNL RabbitMQ]](https://www.rabbitmq.com) come broker di messaggistica, che fornisce una piattaforma scalabile per l’invio e la ricezione di messaggi. Include inoltre un meccanismo per memorizzare i messaggi non consegnati. [!DNL RabbitMQ] si basa sulla specifica AMQP (Advanced Message Queuing Protocol) 0.9.1.

Il diagramma seguente illustra il Framework di coda messaggi:

![Framework di coda messaggi](../../assets/configuration/mq-framework.png)

- A [editore](https://glossary.magento.com/publisher-subscriber-pattern) è un componente che invia messaggi a uno scambio. Sa in quale scambio pubblicare e il formato dei messaggi che invia.

- Uno scambio riceve messaggi dagli editori e li invia alle code. Nonostante [!DNL RabbitMQ] supporta più tipi di scambi, Commerce utilizza solo gli scambi di argomenti. Un argomento include una chiave di routing contenente stringhe di testo separate da punti. Il formato del nome di un argomento è `string1.string2`: ad esempio, `customer.created` o `customer.sent.email`.

   Il broker consente di utilizzare i caratteri jolly quando si impostano le regole per l’inoltro dei messaggi. È possibile utilizzare un asterisco (`*`) in sostituzione di _uno_ stringa o cancelletto (`#`) per sostituire 0 o più stringhe. Ad esempio: `customer.*` applica un filtro `customer.create` e `customer.delete`, ma non `customer.sent.email`. Tuttavia `customer.#` applica un filtro `customer.create`,  `customer.delete`e `customer.sent.email`.

- Una coda è un buffer che memorizza i messaggi.

- Un consumatore riceve i messaggi. Sa quale coda consumare. Può mappare i processori del messaggio a una coda specifica.

È inoltre possibile impostare un sistema di coda messaggi di base senza utilizzare [!DNL RabbitMQ]. In questo sistema, un MySQL [adattatore](https://glossary.magento.com/adapter) memorizza i messaggi nel database. Tre tabelle di database (`queue`, `queue_message`e `queue_message_status`) gestisce il carico di lavoro della coda messaggi. I lavori di Cron garantiscono ai consumatori la possibilità di ricevere messaggi. Questa soluzione non è molto scalabile. [!DNL RabbitMQ] deve essere utilizzato quando possibile.

---
title: Scheda [!DNL RabbitMQ]
description: Scopri la scheda [!DNL RabbitMQ] di [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Scheda [!UICONTROL [!DNL RabbitMQ]]

La scheda **[!UICONTROL [!DNL RabbitMQ]]** contiene informazioni incentrate su [!DNL RabbitMQ] segnali.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] eventi di infrastruttura](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Il frame **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** mostra gli eventi di infrastruttura che coinvolgono [!DNL RabbitMQ] che si sono verificati nell&#39;intervallo di tempo selezionato:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) come `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) come `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) come `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) come `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) come `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) come `node2_timeout_exceeded`
* `%401 Unauthorized%`) come `401_unauth`
* `%401 Unauthorized%`) come `401_unauth`
* `%Service restarted: rabbitmq-server%`) come `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) come `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) come `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) come `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) come `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) come `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) come `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) come `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) come `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) come `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) come `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] segnali di avvio/arresto del servizio](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Questo frame mostra [!DNL RabbitMQ] segnali di avvio/arresto del servizio che si sono verificati durante l&#39;intervallo di tempo selezionato:

* `%RabbitMQ is asked to stop...%`) come `rabbitmq_stop`
* `%Starting RabbitMQ%`) come `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errori](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Questo frame mostra [!DNL RabbitMQ] errori che si sono verificati durante l&#39;intervallo di tempo selezionato:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` come `exit_timeout`
* `%client unexpectedly closed TCP connection%`) come `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) come `undef_exit`
* `%Connection attempt from disallowed node%`) come `disallowed_node`
* `%closing AMQP connection%`) come `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] stato nodo](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) come `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) come `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) come `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) come `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) come `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) come `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

Stato riepilogo di alto livello del messaggio ![[!DNL RabbitMQ] per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** mostra il numero di messaggi pubblicati dalla coda [!DNL RabbitMQ] per l&#39;intervallo di tempo selezionato.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

Riepilogo dettagli messaggio ![[!DNL RabbitMQ]](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) come `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) come `queue_err`
* `%authenticated and granted access to vhost%`) come `auth`
* `%closing AMQP connection%`) come `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] consumo coda MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** mostra il numero di byte utilizzati da ogni coda [!DNL RabbitMQ] nel periodo di tempo selezionato.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] messaggi pubblicati dalla coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** mostra il numero di byte utilizzati da ogni coda [!DNL RabbitMQ] nel periodo di tempo selezionato.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] velocità effettiva dei messaggi pubblicati dalla coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** mostra il numero medio di messaggi pubblicati al secondo da ogni coda [!DNL RabbitMQ] nel periodo di tempo selezionato.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] velocità effettiva messaggi totale dalla coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** mostra il numero totale medio di messaggi al secondo per ogni coda [!DNL RabbitMQ] nell&#39;intervallo di tempo selezionato.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] utenti per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Il grafico **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** mostra il numero totale medio di consumer per ogni coda [!DNL RabbitMQ] nell&#39;arco temporale selezionato.

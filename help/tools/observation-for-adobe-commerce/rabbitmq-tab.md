---
title: "Il [!UICONTROL [!DNL RabbitMQ]] scheda"
description: Scopri le [!UICONTROL [!DNL RabbitMQ]] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# La [!UICONTROL [!DNL RabbitMQ]] scheda

La **[!UICONTROL [!DNL RabbitMQ]]** la scheda contiene informazioni su cui è incentrato [!DNL RabbitMQ] segnali.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Eventi infrastrutturali](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** il frame mostra gli eventi infrastrutturali che coinvolgono [!DNL RabbitMQ] che si è verificato nell’arco temporale selezionato:

* %Risposta [errore] per nodo [rabbit@host1]: risposta http inattesa da%) come &#39;inaspettato_risp_node1&#39;
* &#39;%Response [errore] per nodo [rabbit@host2]: risposta http inattesa da%) come &#39;inaspettato_risp_node2&#39;
* &#39;%Response [errore] per nodo [rabbit@host3]: risposta http inattesa da%) come &#39;inaspettato_risp_node3&#39;
* &#39;%Response [errore] per nodo [rabbit@host3]: Ottieni &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;: scadenza del contesto superata%) come &#39;node3_timeout_superamento&#39;
* &#39;%Response [errore] per nodo [rabbit@host1]: Ottieni &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;: scadenza del contesto superata%) come &#39;node1_timeout_superamento
* &#39;%Response [errore] per nodo [rabbit@host2]: Ottieni &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;: scadenza del contesto superata%) come &#39;node2_timeout_superamento&#39;
* &#39;%401 Unauthorized%&#39;) come &#39;401_unauth&#39;
* &#39;%401 Unauthorized%&#39;) come &#39;401_unauth&#39;
* %Service riavviato: rabbitmq-server%&#39;) come &#39;rmq_service_riavvio&#39;
* &#39;%Response [fallito] per nodo [rabbit@host1]: nodedown%) come &#39;rmq_node1_down&#39;
* &#39;%Response [fallito] per nodo [rabbit@host2]: nodedown%) come &#39;rmq_node2_down&#39;
* &#39;%Response [fallito] per nodo [rabbit@host2]: nodedown%) come &#39;rmq_node2_down&#39;
* &#39;%Entità modificata: exchange/bindings.destination%&quot;) come &#39;rmq_entity_modified&#39;
* &#39;%Entità modificata: exchange/bindings.destination%&quot;) come &#39;rmq_entity_modified&#39;
* &#39;%Entità modificata: queue/esclusivo%&#39;) come &#39;rmq_entity_created_q_esclusive&#39;&#39;%Entità modificata: queue/auto_delete%&#39;) come &#39;rmq_entity_q_delete&#39;
* &#39;%Entità modificata: queue/durable%) come &#39;rmq_entity_modified_q_durable&#39;
* &#39;%Entità modificata: version/management%) as &#39;rmq_entity_modified_ver_mgt&#39;
* &#39;%Entità modificata: version/management%) as &#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] segnali di avvio/arresto del servizio](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Questo fotogramma mostra [!DNL RabbitMQ] segnali di avvio/arresto del servizio che si sono verificati durante l&#39;intervallo temporale selezionato:

* &#39;%[!DNL RabbitMQ] viene richiesto di fermarsi...%) come &#39;rabbitmq_stop&#39;
* &#39;%Avvio [!DNL RabbitMQ]%) come &#39;rabbitmq_start&#39;

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errori](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Questo fotogramma mostra [!DNL RabbitMQ] errori che si sono verificati nel periodo di tempo selezionato:

* &#39;%exit con motivo {case_clausola,timeout} e stacktrace {rabbit_mgmt_wm_health_thchs%&#39;} come &#39;exit_timeout&#39;
* &#39;%client ha chiuso inaspettatamente la connessione TCP%&#39;) come &#39;client_closed_tcp_conn&#39;
* &#39;%at uscita non definita con arresto del motivo nel contesto shutdown_error%&#39;) come &#39;undef_exit&#39;
* &#39;%Tentativo di connessione dal nodo non consentito%&#39;) come &#39;disallowed_node&#39;
* &#39;%chiusura connessione AMQP%&#39;) come &#39;rmq_err_amqp_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] stato del nodo](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &#39;%rabbit sul nodo rabbit@host1 down%&#39;) come &#39;rmq_node1_down&#39;
* &#39;%rabbit sul nodo rabbit@host2 down%&#39;) come &#39;rmq_node2_down&#39;
* &#39;%rabbit sul nodo rabbit@host3 down%&#39;) come &#39;rmq_node3_down&#39;
* &#39;%rabbit sul nodo rabbit@host1 up%&#39;) come &#39;rmq_node1_up&#39;
* &#39;%rabbit sul nodo rabbit@host2 up%&#39;) come &#39;rmq_node2_up&#39;
* &#39;%rabbit sul nodo rabbit@host3 up%&#39;) come &#39;rmq_node3_up&#39;

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Messaggio stato di riepilogo di alto livello per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** il grafico mostra il numero di messaggi pubblicati dal [!DNL RabbitMQ] coda per l&#39;intervallo temporale selezionato.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Riepilogo dettagli messaggio](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* &#39;%report.ERROR: Cron Job Consumer_runner ha un errore: NOT_FOUND - nessuna coda%) come &#39;queue_err&#39;
* &#39;%report.ERROR: Cron Job Consumer_runner ha un errore: NOT_FOUND - nessuna coda%) come &#39;queue_err&#39;
* &#39;%autenticato e concesso l&#39;accesso a vhost%&#39;) come &#39;auth&#39;
* &#39;%chiusura connessione AMQP%&#39;) come &#39;close_conn&#39;

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] MB consumo coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** Il grafico mostra il numero di byte utilizzati da ogni [!DNL RabbitMQ] Coda nell&#39;intervallo temporale selezionato.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Messaggi pubblicati per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** Il grafico mostra il numero di byte utilizzati da ogni [!DNL RabbitMQ] Coda nell&#39;intervallo temporale selezionato.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Throughput messaggi pubblicati per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** grafico mostra il numero medio di messaggi pubblicati al secondo per ogni [!DNL RabbitMQ] Coda nell&#39;intervallo temporale selezionato.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Throughput messaggi totale per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** grafico mostra il numero totale medio di messaggi al secondo per ogni [!DNL RabbitMQ] Coda nell&#39;intervallo temporale selezionato.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Consumatori per coda](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

La **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** grafico mostra il numero totale medio di consumatori per ciascun [!DNL RabbitMQ] Coda nell&#39;intervallo temporale selezionato.

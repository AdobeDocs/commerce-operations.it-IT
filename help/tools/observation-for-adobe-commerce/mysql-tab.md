---
title: Scheda [!UICONTROL MySQL]
description: Scopri la scheda [!UICONTROL MySQL] di [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---

# Scheda [!UICONTROL MySQL]

## [!UICONTROL MySQL% free storage by node]

![Archiviazione libera MySQL% per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

Molti problemi sono causati dall&#39;esaurimento dello spazio di archiviazione di MySQL nell&#39;archiviazione assegnata a MySQL (`datadir` impostazione di configurazione MySQL, impostazione predefinita: `/data/mysql`) o dallo spazio insufficiente di `tmpdir`. Il valore predefinito `tmpdir` (impostazione MySQL) è `/tmp`. Il frame **[!UICONTROL MySQL% free storage by node]** esamina `/, /tmp` (se definito come montaggio separato) e la percentuale `/data/mysql` di spazio di archiviazione libero. A partire da MySQL versione 5.7 (MariaDB versione 10.2), le tabelle non compresse `tmp` vengono scritte in una tablespace `tmp` nella directory `/data/mysql` nel file (ibtmp1). Per impostazione predefinita, questo file si espande automaticamente senza limiti. Trattandosi di una tablespace, le dimensioni non diminuiranno e verranno ripristinate a 12 MB al riavvio di MySQL.

## [!UICONTROL MySQL Connections by Node]

![Connessioni MySQL per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

Il frame **[!UICONTROL MySQL Connections by Node]** indica periodi di interruzioni del nodo del database o di elevati volumi di connessioni.

## [!UICONTROL MySQL Node Summary]

![Riepilogo nodo MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

La tabella **[!UICONTROL MySQL Node Summary]** mostra i dettagli del nodo del database, ad esempio la versione del software e il tipo di istanza (dimensione).

## [!UICONTROL Galera Number of Nodes in cluster]

![Numero di nodi Galera nel cluster](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

Nel frame **[!UICONTROL Galera Number of Nodes in cluster]** vengono visualizzate le informazioni dei log MySQL. Quando i nodi si uniscono e lasciano un cluster, vengono visualizzati solo i messaggi per l’intervallo di tempo selezionato. Se un nodo lascia il cluster prima dell’intervallo di tempo, non esisterà alcun messaggio in tale intervallo di tempo. Se si sospetta che il database sia a corto di un nodo, espandere l&#39;intervallo di tempo a un periodo più lungo per verificare se è possibile visualizzare ulteriori informazioni. Se durante il periodo di tempo sono presenti informazioni che indicano meno di tutti i nodi nel cluster [!DNL Galera], espandere l&#39;intervallo di tempo per verificare se è possibile determinare quando il nodo ha lasciato il cluster.

## [!UICONTROL MySQL shutdowns and starts]

![Arresto e avvio di MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

Il frame **[!UICONTROL MySQL shutdowns and starts]** rileva quando si verifica l&#39;arresto di un nodo. I nodi [!DNL Galera] verranno rimossi e rimossi automaticamente dal nodo [!DNL Galera]. In genere, questo comporta il riavvio del servizio MySQL.

## [!UICONTROL Galera log]

![Registro Galera](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

Il frame **[!UICONTROL Galera log]** mostra i conteggi di segnali particolari provenienti dai registri MySQL relativi ai nodi [!DNL Galera], ai relativi stati e alle modifiche di stato del cluster [!DNL Galera].

* &#39;%1047 WSREP non ha ancora preparato il nodo per l&#39;utilizzo dell&#39;applicazione (percentuale)&#39; come &#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP: impossibile leggere da: wsrep_sst_xtrabackup-v2%&#39;) come &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: processo completato con errore: wsrep_sst_xtrabackup-v2 %&#39;) come &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) come &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;) come &#39;susp_node&#39;
* &#39;%members = 3/3 (join/total)%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 (join/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) come &#39;2of2&#39;
* &#39;%members = 1/2%&#39;) come &#39;1of2&#39;
* &#39;%members = 1/3%&#39;) come &#39;1of3&#39;
* &#39;%members = 1/1%&#39;) come &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) as&#39;sql_restart&#39;
* &#39;%Quorum: nessun nodo con stato completo:%&#39;) come &#39;no_node_count&#39;
* &#39;%WSREP: membro 0%&#39;) come &#39;mem_0&#39;
* &#39;%WSREP: membro 1.0%&#39;) come &#39;mem_1&#39;
* &#39;%WSREP: membro 2%&#39;) come &#39;mem2&#39;
* &#39;%WSREP: sincronizzato con il gruppo, pronto per le connessioni%&#39;) come &#39;ready&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) come &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Nota\] WSREP: nuova visualizzazione cluster: stato globale:%&#39;) come &#39;galera_cluster_view_chng&#39;

## [!UICONTROL Galera Log by Host]

![Registro Galera per host](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

Il frame **[!UICONTROL Galera Log by Host]** è uguale al frame **[!UICONTROL Galera log]**, con la differenza che viene suddiviso per nodo per facilitare la risoluzione dei problemi.

## [!UICONTROL Database performance]

![Prestazioni del database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

Il frame **[!UICONTROL Database performance]** mostra le prestazioni del database durante richieste specifiche. Puoi visualizzare ogni metrica facendo clic su di essa nelle icone colorate sotto il grafico. Molte delle metriche richiamate in [Monitoraggio delle prestazioni del database MySQL con New Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) si trovano in questo frame.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Conteggio chiamate al database transazioni](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

Il frame **[!UICONTROL Transaction Database Call Count]** mostra il numero di chiamate al database effettuate da ogni facet di transazione. Questo sembra essere incentrato sulle righe e non sulle istruzioni.

## [!UICONTROL Cron_schedule table updates]

![Aggiornamenti tabella Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

Nel frame **[!UICONTROL Cron_schedule table updates]** viene visualizzata la durata massima degli aggiornamenti del database alla tabella cron_schedule per il periodo di tempo selezionato.

## [!UICONTROL Slow Query Traces]

![Tracce query lente](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

Nel frame **[!UICONTROL Slow Query Traces]** vengono visualizzati la tabella e il tipo di richiesta in cui sono presenti tracce di query lente. Viene creata una traccia di query lenta per le transazioni di query che richiedono più di cinque secondi. Per questo frame sono importanti le query di aggiornamento. Se una tabella viene aggiornata da `UPDATE`, `DELETE` e `INSERT` istruzioni, queste potrebbero bloccare le tabelle per un periodo di tempo.

Anche le istruzioni `SELECT` possono bloccare le righe se utilizzate con FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tabelle operazioni archivio dati](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Modifica della tabella Cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

Il frame **[!UICONTROL Cron table change]** cerca messaggi di errore &quot;Impossibile acquisire il blocco per il processo cron:&quot;, insieme a un errore di memoria PHP specifico e blocchi che riguardano la tabella `cron_schedule`. Se la tabella `cron_schedule` è bloccata (ad esempio, da una query `DELETE` eseguita su di essa), l&#39;esecuzione di altri nodi verrà bloccata.

## [!UICONTROL Deadlocks]

![Deadlock](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

Il frame **[!UICONTROL Deadlocks]** esamina le stringhe seguenti analizzate dai log MySQL:

* &#39;%PHP Errore irreversibile: dimensione di memoria consentita pari a%&#39;) come php_mem_error
* &#39;%get lock; provare a riavviare la transazione, query: DELETE FROM \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock per il processo cron: indexer_reindex_all_invalid%&#39;) come &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% lock per job cron: cron_schedule%&#39;) come &#39;lock_cron_schedule&#39;
* &#39;% lock per il processo cron:%&#39;) come &#39;total_cron_lock&#39;
* &#39;%Errore generale: timeout attesa blocco 1205 superato%&#39;) come &#39;sql_1205_lock&#39;
* &#39;%ERROR 1213 (40001): Deadlock trovato durante il tentativo di ottenere il blocco%&#39;) come &#39;sql_1213_lock&#39;
* &#39;%SQLSTATE[40001]: errore di serializzazione: blocco critico 1213 trovato%&#39;) come &#39;sql_1213_lock2&#39;
* &#39;% lock per il processo cron: indexer_update_all_views%&#39;) come &#39;lock_indexer_update_all_views&#39;
* &#39;% lock per job cron: sales_grid_order_invoc_async_insert%&#39;) come &#39;lock_sales_grid_order_invoc_async_insert&#39;,
* &#39;% lock per il processo cron: staging_remove_updates%&#39;) come &#39;lock_staging_remove_updates&#39;
* &#39;% lock per OdL cron: sales_grid_order_shipping_async_insert%&#39;) come &#39;lock_sales_grid_order_shipping_async_insert&#39;
* &#39;% lock per job cron: amazon_payments_process_queued_returns%&#39;) come &#39;lock_amazon_payments_process_queued_returns&#39;
* &#39;% lock per OdL cron: sales_send_order_shipping_emails%&#39;) as &#39;lock_sales_send_order_shipping_emails&#39;
* &#39;% lock per job cron: staging_synchronize_entities_period%&#39;) come &#39;lock_staging_synchronize_entities_period&#39;
* &#39;% lock per il processo cron: indexer_clean_all_changelogs%&#39;) come &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% lock per il processo cron: magento_targetrule_index_reindex%&#39;) come &#39;lock_magento_targetrule_index_reindex&#39;
* &#39;% lock per il processo cron: newsletter_send_all%&#39;) come &#39;lock_newsletter_send_all&#39;
* &#39;% lock per il processo cron: newsletter_send_all%&#39;) come &#39;lock_newsletter_send_all&#39;
* &#39;% lock per processo cron: sales_send_order_emails%&#39;) as &#39;lock_sales_send_order_emails&#39;
* &#39;% lock per processo cron: sales_send_order_creditmemo_emails%&#39;) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock per job cron: sales_grid_order_creditmemo_async_insert%&#39;) come &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% lock per il processo cron: bulk_cleanup%&#39;) come &#39;lock_bulk_cleanup&#39;
* &#39;% lock per il processo cron: flush_preview_parts%&#39;) come &#39;lock_flush_preview_parts&#39;
* &#39;% lock per OdL cron: sales_send_order_voice_emails%&#39;) as &#39;lock_sales_send_order_voice_emails&#39;
* &#39;% lock per OdL cron: sales_send_order_voice_emails%&#39;) as &#39;lock_sales_send_order_voice_emails&#39;
* &#39;% lock per il processo cron: captcha_delete_expiry_images%&#39;) come &#39;lock_captcha_delete_espirato_images&#39;
* &#39;% lock per il processo cron: magento_newrelicreporting_cron%&#39;) come &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% lock per il processo cron: outdated_authentication_failures_cleanup%&#39;) come &#39;lock_outdated_authentication_failures_cleanup&#39;
* &#39;% lock per il processo cron: send_notification%&#39;) come &#39;lock_send_notification&#39;
* &#39;% lock per il processo cron: magento_givtcardaccount_generage_codes_pool%&#39;) come &#39;lock_magento_givtcardaccount_generage_codes_pool&#39;
* &#39;% lock per il processo cron: catalog_product_frontend_actions_flush%&#39;) come &#39;lock_catalog_product_frontend_actions_flush&#39;
* &#39;% lock per il processo cron: mysqlmq_clean_messages%&#39;) come &#39;mysqlmq_clean_messages&#39;
* &#39;% lock per il processo cron: catalog_product_attribute_value_synchronize%&#39;) come &#39;lock_catalog_product_attribute_value_synchronize&#39;
* &#39;% lock per il processo cron: ddg_automation_importer%&#39;) come &#39;lock_ddg_automation_importer&#39;
* &#39;% lock for cron job: ddg_automation_Reviews_and_wishlist%&#39;) as &#39;lock_ddg_automation_Reviews_and_wishlist&#39;
* &#39;% lock per il processo cron: captcha_delete_old_attempted%&#39;) come &#39;lock_captcha_delete_old_attempted&#39;
* &#39;% lock per job cron: catalog_product_outdated_price_values_cleanup%&#39;) come &#39;lock_catalog_product_outdated_price_values_cleanup&#39;
* &#39;% lock per il processo cron: consumer_runner%&#39;) come &#39;lock_consumer_runner&#39;
* &#39;% lock per il processo cron: ddg_automation_customer_subscriber_guest_sync%&#39;) come &#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* &#39;% lock per il processo cron: get_amazon_capture_updates%&#39;) come &#39;lock_get_amazon_capture_updates&#39;
* &#39;% lock per il processo cron: get_amazon_authorization_updates%&#39;) come &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% lock per il processo cron: temando_process_platform_events%&#39;) come &#39;lock_temando_process_platform_events&#39;
* &#39;% lock per il processo cron: ddg_automation_status%&#39;) come &#39;lock_ddg_automation_status&#39;
* &#39;% lock per il processo cron: ddg_automation_status%&#39;) come &#39;lock_ddg_automation_status&#39;
* &#39;% lock per processo cron: sales_clean_orders%&#39;) as &#39;lock_sales_clean_orders&#39;
* &#39;% lock per job cron: catalog_index_refresh_price%&#39;) come &#39;lock_catalog_index_refresh_price&#39;
* &#39;% lock per job cron: magento_reward_balance_warning_notification%&#39;) come &#39;lock_magento_reward_balance_warning_notification&#39;
* &#39;% lock per il processo cron: analytics_update%&#39;) come &#39;lock_analytics_update&#39;
* &#39;% lock per il processo cron: messagequeue_clean_outdated_locks%&#39;) come &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock per il processo cron: messagequeue_clean_outdated_locks%&#39;) come &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock per il processo cron: staging_apply_version%&#39;) come &#39;lock_staging_apply_version&#39;
* &#39;% lock per job cron: magento_reward_expire_points%&#39;) come &#39;lock_magento_reward_expire_points&#39;
* &#39;% lock per il processo cron: yotpo_yotpo_orders_sync%&#39;) come &#39;lock_yotpo_yotpo_orders_sync&#39;
* &#39;% lock per il processo cron: catalog_event_status_checker%&#39;) come &#39;lock_catalog_event_status_checker&#39;
* &#39;% lock per il processo cron: ddg_automation_campaign%&#39;) come &#39;lock_ddg_automation_campaign&#39;
* &#39;% lock per il processo cron: visitor_clean%&#39;) come &#39;lock_visitor_clean&#39;
* &#39;% lock per il processo cron: scconnector_verify_website%&#39;) come &#39;lock_scconnector_verify_website&#39;
* &#39;% lock for cron job: ddg_automation_email_templates%&#39;) as &#39;lock_ddg_automation_email_templates&#39;
* &#39;% lock per job cron: aggregate_sales_report_order_data%&#39;) come &#39;lock_aggregate_sales_report_order_data&#39;
* &#39;% lock per il processo cron: ddg_automation_catalog_sync%&#39;) come &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![Statistiche database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

Nel frame **[!UICONTROL DB Statistics]** vengono visualizzate eliminazioni, scritture, righe lette, aggiornamenti e query lente al secondo.

## [!UICONTROL Request frequency]

![Frequenza richiesta](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![Errori database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

Il frame **[!UICONTROL Database Errors]** mostra diversi [avvisi ed errori](https://mariadb.com/kb/en/mariadb-error-codes/) del database:

* &#39;%La dimensione della memoria allocata per la tabella temporanea è superiore al 20% di innodb_buffer_pool_size%&#39; come &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) come &#39;rbr_write_fail&#39;
* &#39;%mysqld: disco pieno%&#39;) come &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) come &#39;err_28&#39;
* &#39;%rollback%&#39;) come &#39;rollback&#39;
* &#39;%Foreign key_constraint&#39; non riesce per la tabella%&#39;) come &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) come &#39;sql_1114_full&#39;%CRITICAL: SQLSTATE[HY000] [2006] Il server MySQL è scomparso%&#39;) come &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040] Troppe connessioni%&#39;) come &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2002]%&#39;) come &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) come &#39;sql_1047&#39;
* &#39;%[Avviso] Connessione interrotta%&#39;) come &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: violazione del vincolo di integrità:%&#39;) come &#39;sql_23000&#39;
* &#39;%1205 Lock wait timeout%&#39;) come &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Database sconosciuto%&#39;) come &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: tabella o vista di base non trovata:%&#39;) come &#39;sql_42S02&#39;
* &#39;%Errore generale: 1114%&#39;) come &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) come &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: colonna non trovata: 1054 Colonna sconosciuta%&#39;) come &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: errore di sintassi o violazione di accesso:%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: violazione di cardinalità:%&#39;) come &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) come &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Client con indirizzo IP%&#39;) come &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: errore generale: 2014%&#39;) come &#39;sql_2014&#39;
* &#39;%1927 Connessione terminata%&#39;) come &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) come &#39;sql_1062_e&#39;
* &#39;&#39;%[Nota] WSREP: scaricamento mappa memoria su disco...%&#39;) come &#39;mem_map_flush&#39;
* &#39;%Internal MariaDB error code: 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Internal MariaDB codice errore: 1062%&#39;) come &#39;sql_1062&#39; * &#39;%1062 [Avviso] InnoDB:%&#39;) come &#39;sql_1062_w&#39;
* &#39;%Internal MariaDB error code: 1064%&#39;) as &#39;sql_1064&#39;
* &#39;%InnoDB: errore di asserzione nel file%&#39;) come &#39;assertion_err&#39;
* &#39;%mysqld_safe Numero di processi attualmente in esecuzione: 0%&#39;) come &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld ha ottenuto il segnale%&#39;) come &#39;mysql_sigterm&#39;
* &#39;%1452 Impossibile aggiungere%&#39;) come &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) come &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: errore generale: 3%&#39;) come &#39;cnt_wrt_tmp&#39;
* &#39;%General error: 1 %&#39;) come &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) come &#39;sql_42S22&#39;
* &#39;%InnoDB: errore (chiave duplicata)%&#39;) come &#39;innodb_dup_key&#39; FROM LOG TIMESERIES

## [!UICONTROL DB Error Table]

![Tabella errori DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

Il frame **[!UICONTROL DB Error Table]** mostra le stesse informazioni del frame **[!UICONTROL Database Errors]**, ma è possibile visualizzarlo per nodo e in formato tabella. Per ulteriori informazioni, vedere [Codici di errore MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/).

## [!UICONTROL Database Traces]

![Tracce database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

Il frame **[!UICONTROL Database Traces]** mostra le tracce del database per tipo nella sequenza temporale selezionata.

## [!UICONTROL Database processes]

![Processi database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

Il frame **[!UICONTROL Database processes]** mostra i processi di database, gli ambienti e gli identificatori di nodo.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads non sospesa MySQL per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

Il frame **[!UICONTROL MySQL Non-Sleeping Threads by Node]** mostra i thread di connessione al database. Questo frame mostra i thread attivi.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL in esecuzione e sospensione di Threads per ambiente](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

Il frame **[!UICONTROL MySQL Running and Sleeping Threads by environment]** mostra le connessioni al database attive e in sospeso. Se sono presenti connessioni al database in cui le query lente sono passate alla modalità di sospensione, le connessioni saranno interrotte. Le connessioni in sospensione possono essere query di database bloccate da righe o tabelle bloccate. Questi collegamenti in sospensione sono anche i collegamenti dei lavoratori PHP.

## [!UICONTROL MySQL mem used by node]

![Mem MySQL utilizzato dal nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

Il frame **[!UICONTROL MySQL mem used by node]** mostra l&#39;utilizzo della memoria da parte di MySQL. Su siti più grandi, questo frame può essere barre continue con GB di memoria utilizzata.

## [!UICONTROL Database mysql-slow.log]

![Database mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

Il frame **[!UICONTROL Database mysql-slow.log]** mostra i tipi di istruzioni di query presenti nel file `mysql-slow.log` per l&#39;intervallo di tempo selezionato.

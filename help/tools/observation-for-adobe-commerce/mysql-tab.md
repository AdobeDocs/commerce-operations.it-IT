---
title: Il [!UICONTROL MySQL] scheda
description: Scopri circa la [!UICONTROL MySQL] scheda di [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---

# Il [!UICONTROL MySQL] scheda

## [!UICONTROL MySQL% free storage by node]

![MySQL% gratuito archiviazione per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

Molti problemi sono causati dall&#39;esaurimento dello spazio di archiviazione di MySQL nell&#39;archivio assegnato a MySQL (`datadir` impostazione di configurazione MySQL, l&#39;impostazione predefinita è `/data/mysql`) o dall&#39;esaurimento `tmpdir` dello spazio. L&#39;impostazione predefinita `tmpdir` (MySQL) è `/tmp`. Il **[!UICONTROL MySQL% free storage by node]** telaio esamina il `/, /tmp` (se definito come un supporto separato) e la `/data/mysql` percentuale di memorizzazione gratuito. A partire dalla versione 5.7 di MySQL (MariaDB versione 10.2), le `/data/mysql` tabelle non compresse `tmp` vengono scritte in un `tmp` tablespace nella directory del file (ibtmp1). Per impostazione predefinita, questo file si espande automaticamente senza limiti. Poiché si tratta di un tablespace, non diminuirà di dimensioni e verrà ripristinato a 12 MB al riavvio di MySQL.

## [!UICONTROL MySQL Connections by Node]

![Connessioni MySQL per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

Il frame **[!UICONTROL MySQL Connections by Node]** indica periodi di interruzioni del nodo del database o di elevati volumi di connessioni.

## [!UICONTROL MySQL Node Summary]

![Riepilogo nodo MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

La tabella **[!UICONTROL MySQL Node Summary]** mostra i dettagli del nodo del database, ad esempio la versione del software e il tipo di istanza (dimensione).

## [!UICONTROL Galera Number of Nodes in cluster]

![Numero di nodi di Galera nel cluster](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

Il **[!UICONTROL Galera Number of Nodes in cluster]** frame visualizza informazioni dai log MySQL. Quando i nodi si uniscono ed escono da un cluster, vengono visualizzati solo i messaggi per il arco temporale selezionato. Se un nodo lascia il cluster prima del arco temporale, non sarà presente alcun messaggio durante tale arco temporale. Se si sospetta che il database sia a corto di un nodo, espandere il arco temporale a un periodo più lungo per vedere se è possibile visualizzare ulteriori informazioni. Se durante il periodo di tempo sono presenti informazioni che indicano meno di tutti i nodi nel cluster [!DNL Galera], espandere l&#39;intervallo di tempo per verificare se è possibile determinare quando il nodo ha lasciato il cluster.

## [!UICONTROL MySQL shutdowns and starts]

![Arresto e avvio di MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

Il frame **[!UICONTROL MySQL shutdowns and starts]** rileva quando si verifica l&#39;arresto di un nodo. I nodi [!DNL Galera] verranno rimossi e rimossi automaticamente dal nodo [!DNL Galera]. In genere, questo comporta il riavvio del servizio MySQL.

## [!UICONTROL Galera log]

![Registro Galera](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

Il frame **[!UICONTROL Galera log]** mostra i conteggi di segnali particolari provenienti dai registri MySQL relativi ai nodi [!DNL Galera], ai relativi stati e alle modifiche di stato del cluster [!DNL Galera].

* &#39;%1047 WSREP non ha ancora preparato il nodo per l&#39;utilizzo dell&#39;applicazione (percentuale)&#39; come &#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP: impossibile leggere da: wsrep_sst_xtrabackup-v2%&#39;) come &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: Processo completato con errore: wsrep_sst_xtrabackup-v2 %&#39;) come &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) come &#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;) come &#39;susp_node&#39;
* &#39;%members = 3/3 (join/total)%&#39;) as&#39;3of3&#39;
* &#39;%members = 2/3 (join/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) come &#39;2of2&#39;
* &#39;%members = 1/2%&#39;) come &#39;1of2&#39;
* &#39;%membri = 1/3%&#39;) come &#39;1of3&#39;
* &#39;%membri = 1/1%&#39;) come &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) come &#39;sql_restart&#39;
* &#39;%Quorum: nessun nodo con stato completo:%&#39;) come &#39;no_node_count&#39;
* &#39;%WSREP: iscritto 0%&#39;) come &#39;mem_0&#39;
* &#39;%WSREP: iscritto 1.0%&#39;) come &#39;mem_1&#39;
* &#39;%WSREP: iscritto 2%&#39;) as&#39;mem2&#39;
* &#39;%WSREP: Sincronizzato con il gruppo, pronto per le connessioni%&#39;) come &#39;pronto&#39;
* &#39;%/usr/sbin/mysqld, Versione:%&#39;) as &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Nota\] WSREP: Nuovo cluster view: global state:%&#39;) come &#39;galera_cluster_view_chng&#39;

## [!UICONTROL Galera Log by Host]

![Galera Log per host](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

Il **[!UICONTROL Galera Log by Host]** frame è uguale al frame, tranne per il fatto che è suddiviso per nodo per facilitare la **[!UICONTROL Galera log]** risoluzione dei problemi.

## [!UICONTROL Database performance]

![Prestazioni del database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

Il **[!UICONTROL Database performance]** frame mostra le prestazioni del database durante richieste specifiche. Puoi vedere ogni metrica facendo clic su di essa nelle icone colorate sotto il grafico. Molte delle metriche richiamate in [Monitoraggio delle prestazioni del database MySQL con Nuovo Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) si trovano in questo frame.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* media(db.tablesLocksWaitedPerSecond)
* media (db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Conteggio chiamate al database transazioni](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

Il frame **[!UICONTROL Transaction Database Call Count]** mostra il numero di chiamate al database effettuate da ogni facet di transazione. Questo sembra essere incentrato sulle righe e non sulle istruzioni.

## [!UICONTROL Cron_schedule table updates]

![Aggiornamenti tabella Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

Nel frame **[!UICONTROL Cron_schedule table updates]** viene visualizzata la durata massima degli aggiornamenti del database alla tabella cron_schedule per il periodo di tempo selezionato.

## [!UICONTROL Slow Query Traces]

![Tracce di query lente](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

Nel **[!UICONTROL Slow Query Traces]** frame vengono visualizzati la tabella e il tipo di richiesta in cui sono presenti tracce di query lente. Viene creata una traccia di query lenta per le transazioni di query che richiedono più di cinque secondi. Importanti per questo frame sono le query di aggiornamento. Se una tabella viene aggiornata da `UPDATE`, `DELETE`e `INSERT` istruzioni, questi possono bloccare le tabelle per un certo periodo di tempo.

Anche `SELECT` le istruzioni possono bloccare le righe se utilizzate con FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tabelle delle operazioni del Datastore](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Modifica tabella cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

Il **[!UICONTROL Cron table change]** frame cerca i messaggi di errore &quot;impossibile acquisire il blocco per cron job:&quot;, insieme a uno specifico errore di memoria PHP e blocchi che coinvolgono la `cron_schedule` tabella. Se la `cron_schedule` tabella è bloccata (ad esempio, da una `DELETE` query eseguita su di essa), bloccherà l&#39;esecuzione di altri cron.

## [!UICONTROL Deadlocks]

![Deadlock](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

Il **[!UICONTROL Deadlocks]** frame esamina le seguenti stringhe analizzate dai log MySQL:

* &#39;%PHP Errore irreversibile: dimensione della memoria consentita di%&#39;) come php_mem_error
* &#39;%get lock; provare a riavviare la transazione, query: DELETE FROM \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock per il processo cron: indexer_reindex_all_invalid%&#39;) come &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% lock per job cron: cron_schedule%&#39;) come &#39;lock_cron_schedule&#39;
* &#39;% lock per il processo cron:%&#39;) come &#39;total_cron_lock&#39;
* &#39;%Errore generale: timeout attesa blocco 1205 superato%&#39;) come &#39;sql_1205_lock&#39;
* &#39;%ERRORE 1213 (40001): Deadlock rilevato durante il tentativo di ottenere il blocco%&#39;) come &#39;sql_1213_lock&#39;
* &#39;%SQLSTATE[40001]: Errore di serializzazione: 1213 Deadlock trovato%&#39;) come &#39;sql_1213_lock2&#39;
* &#39;% lock for cron job: indexer_update_all_views%&#39;) as &#39;lock_indexer_update_all_views&#39;
* &#39;% lock per job cron: sales_grid_order_invoc_async_insert%&#39;) come &#39;lock_sales_grid_order_invoc_async_insert&#39;,
* &#39;% lock per il processo cron: staging_remove_updates%&#39;) come &#39;lock_staging_remove_updates&#39;
* &#39;% lock per OdL cron: sales_grid_order_shipping_async_insert%&#39;) come &#39;lock_sales_grid_order_shipping_async_insert&#39;
* &#39;% lock per job cron: amazon_payments_process_queued_returns%&#39;) come &#39;lock_amazon_payments_process_queued_returns&#39;
* &#39;% lock per OdL cron: sales_send_order_shipping_emails%&#39;) as &#39;lock_sales_send_order_shipping_emails&#39;
* &#39;% lock per job cron: staging_synchronize_entities_period%&#39;) come &#39;lock_staging_synchronize_entities_period&#39;
* &#39;% lock per il processo cron: indexer_clean_all_changelogs%&#39;) come &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% lock per il processo cron: magento_targetrule_index_reindex%&#39;) come &#39;lock_magento_targetrule_index_reindex&#39;
* &#39;% lock for cron job: newsletter_send_all%&#39;) come &#39;lock_newsletter_send_all&#39;
* &#39;% lock per il processo cron: newsletter_send_all%&#39;) come &#39;lock_newsletter_send_all&#39;
* &#39;% lock per processo cron: sales_send_order_emails%&#39;) as &#39;lock_sales_send_order_emails&#39;
* &#39;% lock per processo cron: sales_send_order_creditmemo_emails%&#39;) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock per job cron: sales_grid_order_creditmemo_async_insert%&#39;) come &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% lock per il processo cron: bulk_cleanup%&#39;) come &#39;lock_bulk_cleanup&#39;
* &#39;% lock for cron job: flush_preview_quotas%&#39;) as &#39;lock_flush_preview_quotas&#39;
* &#39;% lock for cron job: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% lock for cron job: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% lock for cron job: captcha_delete_expired_images%&#39;) as &#39;lock_captcha_delete_expired_images&#39;
* &#39;% lock for cron job: magento_newrelicreporting_cron%&#39;) as &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% lock for cron job: outdated_authentication_failures_cleanup%&#39;) as &#39;lock_outdated_authentication_failures_cleanup&#39;
* &#39;% lock for cron job: send_notifica%&#39;) as &#39;lock_send_notifica&#39;
* &#39;% lock for cron job: magento_giftcardaccount_generage_codes_pool%&#39;) as &#39;lock_magento_giftcardaccount_generage_codes_pool&#39;
* &#39;% lock for cron job: catalog_product_frontend_actions_flush%&#39;) come &#39;lock_catalog_product_frontend_actions_flush&#39;
* &#39;% lock for cron job: mysqlmq_clean_messages%&#39;) come &#39;mysqlmq_clean_messages&#39;
* &#39;% lock for cron job: catalog_product_attribute_value_synchronize%&#39;) as &#39;lock_catalog_product_attribute_value_synchronize&#39;
* &#39;% lock for cron job: ddg_automation_importer%&#39;) as &#39;lock_ddg_automation_importer&#39;
* &#39;% lock for cron job: ddg_automation_reviews_and_wishlist%&#39;) come &#39;lock_ddg_automation_reviews_and_wishlist&#39;
* &#39;% lock for cron job: captcha_delete_old_attempts%&#39;) come &#39;lock_captcha_delete_old_attempts&#39;
* &#39;% lock for cron job: catalog_product_outdated_price_values_cleanup%&#39;) come &#39;lock_catalog_product_outdated_price_values_cleanup&#39;
* &#39;% lock for cron job: consumers_runner%&#39;) come &#39;lock_consumers_runner&#39;
* &#39;% lock for cron job: ddg_automation_customer_subscriber_guest_Sincronizzazione%&#39;) as &#39;lock_ddg_automation_customer_subscriber_guest_Sincronizzazione&#39;
* &#39;% lock per il processo cron: get_amazon_capture_updates%&#39;) come &#39;lock_get_amazon_capture_updates&#39;
* &#39;% lock per il processo cron: get_amazon_authorization_updates%&#39;) come &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% lock per il processo cron: temando_process_platform_events%&#39;) come &#39;lock_temando_process_platform_events&#39;
* &#39;% lock for cron job: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock for cron job: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock per processo cron: sales_clean_orders%&#39;) as &#39;lock_sales_clean_orders&#39;
* &#39;% lock per job cron: catalog_index_refresh_price%&#39;) come &#39;lock_catalog_index_refresh_price&#39;
* &#39;% lock per job cron: magento_reward_balance_warning_notification%&#39;) come &#39;lock_magento_reward_balance_warning_notification&#39;
* &#39;% lock per il processo cron: analytics_update%&#39;) come &#39;lock_analytics_update&#39;
* &#39;% lock per il processo cron: messagequeue_clean_outdated_locks%&#39;) come &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock per il processo cron: messagequeue_clean_outdated_locks%&#39;) come &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock for cron job: staging_apply_version%&#39;) as &#39;lock_staging_apply_version&#39;
* &#39;% lock for cron job: magento_reward_expire_points%&#39;) as &#39;lock_magento_reward_expire_points&#39;
* &#39;% lock for cron job: yotpo_yotpo_orders_Sincronizzazione%&#39;) as &#39;lock_yotpo_yotpo_orders_Sincronizzazione&#39;
* &#39;% lock for cron job: catalog_event_status_checker%&#39;) as &#39;lock_catalog_event_status_checker&#39;
* &#39;% lock for cron job: ddg_automation_campaign%&#39;) as &#39;lock_ddg_automation_campaign&#39;
* &#39;% lock for cron job: visitor_clean%&#39;) as &#39;lock_visitor_clean&#39;
* &#39;% lock for cron job: scconnector_verify_website%&#39;) as &#39;lock_scconnector_verify_website&#39;
* &#39;% lock for cron job: ddg_automation_email_templates%&#39;) as &#39;lock_ddg_automation_email_templates&#39;
* &#39;% lock for cron job: aggregato_sales_report_order_data%&#39;) as &#39;lock_aggregato_sales_report_order_data&#39;
* &#39;% lock for cron job: ddg_automation_catalog_Sincronizzazione%&#39;) as &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![Statistiche DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

Nel frame **[!UICONTROL DB Statistics]** vengono visualizzate eliminazioni, scritture, righe lette, aggiornamenti e query lente al secondo.

## [!UICONTROL Request frequency]

![Frequenza richiesta](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![Errori database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

Il **[!UICONTROL Database Errors]** frame mostra una varietà di avvisi ed errori[&#128279;](https://mariadb.com/kb/en/mariadb-error-codes/) del database:

* &#39;%La dimensione della memoria allocata per la tabella temporanea è superiore al 20% del innodb_buffer_pool_size%&#39; come &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: disco pieno%&#39;) come &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) come &#39;err_28&#39;
* &#39;%rollback%&#39;) come &#39;rollback&#39;
* &#39;%Foreign key_constraint&#39; non riesce per la tabella%&#39;) come &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) come &#39;sql_1114_full&#39;%CRITICAL: SQLSTATE[HY000] [2006] Il server MySQL è scomparso%&#39;) come &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040] Troppe connessioni%&#39;) come &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2002]%&#39;) come &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) come &#39;sql_1047&#39;
* &#39;%[Avvertenza] Connessione interrotta%&#39;) come &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: Violazione del vincolo di integrità:%&#39;) come &#39;sql_23000&#39;
* &#39;%1205 Lock wait timeout%&#39;) come &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Database sconosciuto%&#39;) come &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: Tabella di base o vista non trovata:%&#39;) come &#39;sql_42S02&#39;
* &#39;%Errore generale: 1114%&#39;) come &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) come &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Colonna non trovata: 1054 colonna sconosciuta%&#39;) come &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Errore di sintassi o violazione accesso:%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Violazione di cardinalità:%&#39;) come &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) come &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000 [] 9000] Client with IP address%&#39;) as &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Errore generale: 2014%&#39;) come &#39;sql_2014&#39;
* &#39;%1927 Connection was killed%&#39;) come &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) come &#39;sql_1062_e&#39;
* &#39;&#39;%[Nota] WSREP: Scaricamento della mappa della memoria su disco...%&#39;) come &#39;mem_map_flush&#39;
* &#39;%Internal MariaDB error code: 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Internal MariaDB error code: 1062%&#39;) as &#39;sql_1062&#39; * &#39;%1062 [Avvertenza] InnoDB:%&#39;) as &#39;sql_1062_w&#39;
* &#39;%Codice di errore MariaDB interno: 1064%&#39;) come &#39;sql_1064&#39;
* &#39;%InnoDB: Errore di asserzione nel file%&#39;) come &#39;assertion_err&#39;
* &#39;%mysqld_safe Numero di processi in esecuzione ora: 0%&#39;) come &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld got signal%&#39;) as &#39;mysql_sigterm&#39;
* &#39;%1452 Impossibile aggiungere%&#39;) come &#39;sql_1452&#39;
* &#39;%ERRORE 1698%&#39;) come &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: errore generale: 3%&#39;) come &#39;cnt_wrt_tmp&#39;
* &#39;%General error: 1 %&#39;) come &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) come &#39;sql_42S22&#39;
* &#39;%InnoDB: Errore (Duplicate key)%&#39;) as &#39;innodb_dup_key&#39; FROM Log TIMESERIES

## [!UICONTROL DB Error Table]

![Tabella Errore DB](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

Il **[!UICONTROL DB Error Table]** frame mostra le stesse informazioni del **[!UICONTROL Database Errors]** frame, ma è possibile visualizzarlo per nodo e in formato tabella. Per ulteriori informazioni, vedere [Codici di errore MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/).

## [!UICONTROL Database Traces]

![Tracce database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

Il frame **[!UICONTROL Database Traces]** mostra le tracce del database per tipo nella sequenza temporale selezionata.

## [!UICONTROL Database processes]

![Processi database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

Il frame **[!UICONTROL Database processes]** mostra i processi di database, gli ambienti e gli identificatori di nodo.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads non sospesa MySQL per nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

Il **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame mostra i thread di connessione al database. Questo frame mostra i thread attivi.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL Running and Sleep Threads per ambiente](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

Il **[!UICONTROL MySQL Running and Sleeping Threads by environment]** frame mostra le connessioni attive e dormienti al database. Se sono presenti connessioni al database in cui le query lente sono entrate in stato di sospensione, ci saranno connessioni in stato di sospensione. Le connessioni sospensione possono essere query di database bloccate da righe o tabelle bloccate. Queste connessioni dormienti contengono anche connessioni PHP worker.

## [!UICONTROL MySQL mem used by node]

![Mem MySQL utilizzato dal nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

Il **[!UICONTROL MySQL mem used by node]** frame mostra l&#39;utilizzo del nodo della memoria da parte di MySQL. Nei siti più grandi, questo frame può essere barre continue con GB di memoria utilizzata.

## [!UICONTROL Database mysql-slow.log]

![mysql-slow.log del database](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

Il **[!UICONTROL Database mysql-slow.log]** frame mostra i tipi di `mysql-slow.log` istruzioni di query presenti nel file nella arco temporale selezionata.

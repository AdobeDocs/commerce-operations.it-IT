---
title: "Il [!UICONTROL PHP] scheda"
description: Scopri le [!UICONTROL PHP] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 28055eb09235912c66c637990e2081a70e1c7808
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# La [!UICONTROL PHP] scheda

La **PHP** La scheda mostra i problemi del processo PHP per fornire un&#39;analisi più approfondita sui problemi PHP.

## [!UICONTROL PHP active process details]

![Dettagli del processo attivo PHP](../../assets/tools/php-active-process-details.jpg)

La **[!UICONTROL PHP active process details]** frame mostra i processi PHP, incluso php-fpm, nell&#39;arco temporale selezionato.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![Carico di processo PHP](../../assets/tools/php-process-load.jpg)

La **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** frame mostra il carico della CPU dai processi PHP-FPM nell&#39;arco temporale selezionato.

## [!UICONTROL PHP Memory detail]

![Dettagli della memoria PHP](../../assets/tools/php-memory-detail.jpg)

La **[!UICONTROL PHP Memory detail]** frame mostra l&#39;utilizzo della memoria dei processi PHP nell&#39;arco temporale selezionato.

## [!UICONTROL PHP CPU Utilization]

![Utilizzo della CPU PHP](../../assets/tools/php-cpu-utilization.jpg)

La **[!UICONTROL PHP CPU Utilization]** frame mostra la percentuale di utilizzo della CPU dei processi PHP nell&#39;arco temporale selezionato.

## [!UICONTROL PHP Process states]

![Stati del processo PHP](../../assets/tools/php-process-states-image-1.jpg)

La **[!UICONTROL PHP Process states]** Il frame mostra gli stati del processo PHP nell&#39;arco temporale selezionato. Viene visualizzato quando i processi PHP terminano e si riavviano. Attenzione ai processi PHP terminati che non mostrano riavvii.

* &#39;%AVVISO: Terminazione in corso..%) come &#39;php_term&#39;
* AVVISO &#39;%: Uscita, ciao!%) come &#39;php_exit&#39;
* AVVISO &#39;%: fpm è in esecuzione, pid%) come &#39;fpm_start&#39;
* &#39;%AVVISO: pronto per gestire le connessioni%) come &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![Errori PHP](../../assets/tools/php-errors-image-1.jpg)

La **[!UICONTROL PHP Errors]** frame mostra il numero di errori PHP worker nell&#39;arco temporale selezionato. I messaggi di errore analizzati e visualizzati includono:

* &#39;%worker_connections non sono sufficienti%&#39;) come &#39;worker&#39;
* &#39;%Errore irreversibile PHP: Dimensione della memoria consentita!%) come &#39;mem_size&#39;
* &#39;%exited on signal 11 (SIGSEGV)%&#39;) come &#39;sig_11&#39;
* &#39;%exited sul segnale 7 (SIGBUS)%&#39;) come &#39;sig_7&#39;
* &#39;%incrementare pm.start_servers%&#39;) come &#39;pmstart_serving&#39;
* &#39;%max_children%&#39;) come &#39;max_children_cnt&#39;
* &#39;%Errore irreversibile PHP: Dimensione della memoria consentita pari a%) come &#39;mem_exst_coun&#39;
* &#39;%Impossibile allocare memoria per pool%&#39;) come &#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;) come &#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;) come &#39;opc_sv_comments&#39;
* &#39;%Errore irreversibile PHP: RedisException non rilevata: errore di lettura sulla connessione%) come &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![Conteggio processi PHP](../../assets/tools/php-processes-count.jpg)

La **[!UICONTROL PHP processes count]** Il frame mostra un conteggio dei processi PHP nell&#39;arco temporale selezionato.

## [!UICONTROL Database Errors]

![Errori del database](../../assets/tools/php-tab-database-errors.jpg)

La **[!UICONTROL Database Errors]** frame mostra gli errori del database nell&#39;arco temporale selezionato. Gli errori analizzati includono:

* &#39;%La dimensione della memoria allocata per la tabella temporanea è superiore al 20% di innodb_buffer_pool_size%&#39;) come &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&quot;) come &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco pieno%) come &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) as &#39;err_28&#39;
* &#39;%rollback%&#39;) come &#39;rollback&#39;
* &#39;%Il vincolo di chiave esterna non riesce per la tabella%&#39;) come &#39;vincolo_chiave_esterna&#39;
* &#39;%Codice_errore: 1114%) come &#39;sql_1114_full&#39;
* &#39;%CRITICO: SQLSTATE[HY000] [2006] Il server MySQL è andato via%) come &#39;sql_go&#39;
* &#39;%SQLSTATE[HY000] [1040] Troppe connessioni%) come &#39;sql_1040&#39;
* &#39;%CRITICO: SQLSTATE[HY000] [2002]%) come &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%) come &#39;sql_1047&#39;
* &#39;%[Avviso] Connessione interrotta%) come &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: Violazione del vincolo di integrità:%) come &#39;sql_23000&#39;
* &#39;%1205 Timeout attesa blocco%&#39;) come &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Database sconosciuto%) come &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: Tabella o vista di base non trovata:%) come &#39;sql_42S02&#39;
* &#39;%Errore generale: 1114%) come &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) come &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Colonna non trovata: 1054 (colonna sconosciuta%) come &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Errore di sintassi o violazione dell&#39;accesso:%) come &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Violazione cardinalità:%) come &#39;sql_1241&#39;
* &#39;%SQLSTATE[2003]:%) come &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Client con indirizzo IP%) come &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Errore generale: 2014%) come &#39;sql_2014&#39;
* &#39;%1927 Connessione interrotta%&#39;) come &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) come &#39;sql_1062_e&#39;
* &#39;%[Nota] WSREP: Scaricamento della mappa di memoria sul disco in corso...%) come &#39;mem_map_flush&#39;
* &#39;%Codice errore interno MariaDB: 1146%) come &#39;sql_1146&#39;
* &#39;%Codice errore interno MariaDB: 1062%) come &#39;sql_1062&#39; * &#39;%1062&#39; [Avviso] InnoDB:%) come &#39;sql_1062_w&#39;
* &#39;%Codice errore interno MariaDB: 1064%) come &#39;sql_1064&#39;
* &#39;%InnoDB: Errore di asserzione nel file%) come &#39;assertion_err&#39;
* &#39;%mysqld_safe Numero di processi in esecuzione: 0%) come &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld ha ricevuto il segnale%&#39;) come &#39;mysql_sigterm&#39;
* &#39;%1452 Impossibile aggiungere%&#39;) come &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) come &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Errore generale: 3%) come &#39;cnt_wrt_tmp&#39;
* &#39;%Errore generale: 1 %) come &#39;sql_sintassi&#39;
* &#39;%42S22%&#39;) come &#39;sql_42S22&#39;
* &#39;%InnoDB: Errore (chiave duplicata)%) come &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![Tracce database](../../assets/tools/php-tab-database-traces.jpg)

La **[!UICONTROL Database traces]** frame mostra le informazioni di traccia del database. Questo fotogramma è in linea con la vista di riepilogo delle transazioni APM per la timeline selezionata.

## [!UICONTROL Database mysql-slow.log]

![Database mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

La **[!UICONTROL Database mysql-slow.log]** il frame mostra i tipi di istruzione query presenti nel `mysql-slow.log` nell’arco temporale selezionato.

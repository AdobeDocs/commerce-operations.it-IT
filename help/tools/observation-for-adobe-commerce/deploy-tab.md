---
title: "Il [!UICONTROL Deploy] scheda"
description: Scopri le [!UICONTROL Deploy] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: b95a35ee64cd8e844a51a9ff699eceb9c3a9266c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# La [!UICONTROL Deploy] scheda

Questa scheda è un tentativo di isolare rapidamente i problemi e le cause dei problemi di distribuzione.

## [!UICONTROL Deploy log Deployment Troubleshooter]

![Risoluzione dei problemi di distribuzione del registro di distribuzione](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

La **[!UICONTROL Deploy log Deployment Troubleshooter]** mostra un conteggio degli eventi di registro di distribuzione che si sono verificati nell’arco temporale selezionato. L’obiettivo è fornire una visualizzazione a colpo d’occhio dell’attività di distribuzione e determinare la complessità della distribuzione in base al conteggio. Più messaggi registrati, più complessa è in genere la distribuzione.

## [!UICONTROL Deploy State]

![Stato distribuzione](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

La **[!UICONTROL Deploy State]** mostra gli eventi di distribuzione che si sono verificati nell’arco temporale selezionato. Il parser per questo frame cerca questi segnali specifici:

* &#39;%AVVISO: Avvio di generate command%) come &#39;start_gen&#39;
* &#39;%git applica /app/vendor/magento/ece-tools/patch%&#39;) come &#39;apply_patches&#39;
* &#39;%Imposta flag: .static_content_deploy%&#39;) come &#39;SCD&#39;
* &#39;%AVVISO: Genera il comando completato%) come &#39;gen_compl&#39;
* &#39;%AVVISO: Avvio della distribuzione in corso.%) come &#39;start_deploy&#39;
* &#39;%AVVISO: Distribuzione completata%) come &#39;deploy_compl&#39;
* &#39;%AVVISO: Avvio della post-distribuzione.%) come &#39;start_pdeploy&#39;
* &#39;%AVVISO: Il post-distribuzione è completo%) come &quot;pdeploy&quot;
* &#39;%deploy-complete%&#39;) come &#39;cl_deploy_compl&#39;

## [!UICONTROL Deploy Log Detail]

![Distribuzione dei dettagli del registro](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

La **[!UICONTROL Deploy Log Detail]** frame mostra i dettagli del riepilogo del messaggio del registro di distribuzione che si sono verificati nell’arco temporale selezionato. Il frame sta analizzando le seguenti stringhe nei log di distribuzione:

* &#39;%AVVISO: Avvio della distribuzione in corso.%) come &#39;start_dply&#39;
* &#39;%INFO: Scenari iniziali: scenario/deploy.xml%) come &#39;start_scenario&#39;
* &#39;%AVVISO: Avvio di pre-deploy%) come &#39;start_predply&#39;
* INFO &#39;%: Ripristino del file di log delle patch%) come &#39;rstr_ptch_log&#39;
* &#39;%INFO: Aggiornamento della configurazione della cache.%) come &#39;update_cach_config&#39;
* &#39;%INFO: Imposta la connessione slave Redis%) come &#39;redis_sec_conn_set&#39;
* &#39;%INFO: La distribuzione del contenuto statico è stata eseguita durante il gancio di compilazione, pulendo il vecchio contenuto%&#39;) come &#39;scd_build_hk&#39;
* &#39;%INFO: Cancellazione di pub/static%) come &#39;clr_pub_static&#39;
* &#39;%NFO: Cancellazione della cache del disco rigido:%) come &#39;clr_redis_cache&#39;
* &#39;%INFO: Cancellazione della directory var/cache%&#39;) come &#39;clr_var_cach&#39;
* AVVISO &#39;%: Abilitazione della modalità di manutenzione%) come &#39;enable_maint_mode&#39;
* &#39;%INFO: Disattiva cron%) come &#39;disable_cron&#39;
* &#39;%INFO: Cercare di uccidere i lavori di cron in esecuzione e i processi dei consumatori%&#39;) come &#39;kill_cron_try&#39;
* &#39;%INFO: Impossibile trovare i processi di Magento cron e consumer in esecuzione.%) come &#39;no_cron_fnd&#39;,
* %AVVISO: Convalida della configurazione%) come &#39;validate_config&#39;
* &#39;%I seguenti dati amministrativi sono necessari per creare un utente amministratore durante l&#39;installazione iniziale%&#39;) come &#39;no_admin&#39;
* &#39;%versione PHP consigliata che soddisfa il vincolo%&#39;) come &#39;php_ver_Constré&#39;
* &#39;%WARNING: Correggi la configurazione con i suggerimenti dati:%) come &#39;fix_config_sugg&#39;
* &#39;%WARNING: [2003] Il valore del livello di nidificazione della directory per la segnalazione degli errori non è stato configurato.%&#39;) come &#39;nest_err_reporting&#39;
* &#39;%AVVISO: Fine della convalida%) come &#39;end_validation&#39;
* &#39;%AVVISO: Avvio dell&#39;aggiornamento in corso.%) come &#39;start_update&#39;
* &#39;%INFO: Aggiornamento di env.php.%) come &#39;update_php_env&#39;
* &#39;%INFO: Aggiornamento della configurazione della connessione env.php DB.%) come &#39;update_php_env_db&#39;
* &#39;%INFO: Aggiornamento della configurazione env.php AMQP%&#39;) come &#39;update_php_env_amqp&#39;
* &#39;%INFO: Imposta il motore di ricerca su: elasticsearch7%) come &#39;set_elastic7&#39;
* &#39;%elasticsearch 6.5.4 ha superato EOL%&#39;) come &#39;elastic_ver_EOL&#39;
* &#39;%INFO: Imposta il motore di ricerca su: elasticsearch6%) come &#39;set_elastic6&#39;
* &#39;%INFO: Aggiornamento degli URL sicuri e non sicuri (%) come &#39;update_urls&#39;
* &#39;%INFO: Esecuzione dell&#39;aggiornamento della configurazione.%) come &#39;setup_upgrade_run&#39;
* &#39;%INFO: Gancio post-distribuzione abilitato. Abilitazione Cron, pulizia cache e pre-warmingoperation sono posticipati%) come &#39;post_hook_enabled&#39;
* &#39;%AVVISO: La modalità di manutenzione è disabilitata.%) come &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(i) finito(i)(i)(i)) come &#39;scenario_finito&#39;
* &#39;%WARNING: Manutenzione dei comandi:attiva completata con un errore. Creazione di un file di flag di manutenzione%&#39;) come &#39;enable_maintenance_fail&#39;
* &#39;%MySQL server è andato via%&#39;) come &#39;MySQL_has_Go_away&#39;

## [!UICONTROL Post Deploy Log Detail]

![Dettagli del registro di distribuzione post](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

La **[!UICONTROL Post Deploy Log Detail]** frame mostra i dettagli del registro post-distribuzione che si sono verificati nell’arco temporale selezionato. Questo frame è incentrato su particolari messaggi di log che contengono le seguenti stringhe:

* &#39;%Disabilitato modalità manutenzione%&#39;) come &#39;disabled_maint_mode&#39;
* &#39;%INFO: Scenari iniziali: scenario/post-deploy.xml%) come &#39;start_pstdply_scenario&#39;
* AVVISO &#39;%: Convalida della configurazione%) come &#39;val_config&#39;
* AVVISO &#39;%: Fine della convalida%) come &#39;end_val_config&#39;
* &#39;%INFO: Attiva cron%) come &#39;cron_enabled&#39;
* INFO &#39;%: Crea backup di file importanti.%) come &#39;file_backup&#39;
* &#39;%INFO: Il backup%&quot; è stato creato come &#39;file_backup_success&#39;
* &#39;%INFO: Inizio riscaldamento pagina%) come &#39;pg_calore_start&#39;
* &#39;%INFO: Pagina riscaldata:%) come &#39;warmed_up_pg&#39;
* &#39;%ERRORE: Riscaldamento non riuscito:%) come &#39;riscaldamento_up_pg_err&#39;
* INFO &#39;%: Scenario(i) finito(i)(i)(i)) come &#39;scenario_finito&#39;

## [!UICONTROL Cloud Log Detail]

![Dettagli registro cloud](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

La **[!UICONTROL Cloud Log Detail]** frame mostra i dettagli del registro cloud che si sono verificati nell’arco temporale selezionato. Le seguenti stringhe vengono analizzate e restituite con l’etichetta &quot;AS&quot; riportata di seguito:

* &#39;%DEBUG: /bin/bash -c &quot;set -o pipefail; php ./bin/magento setup:upgrade%) come &#39;start_update&#39;
* &#39;%Creazione/aggiornamenti schema:%&#39;) come &#39;schema_Updates&#39;
* &#39;%Niente da importare.%) come &#39;mod_import_finish&#39;
* &#39;%AVVISO: Fine dell’aggiornamento.%) come &#39;update_completed&#39;
* &#39;%DEBUG: Passaggio in esecuzione: deploy-static-content%) come &#39;scd_run&#39;
* AVVISO &#39;%: Salta la distribuzione del contenuto statico. SCD on demand è abilitato.%) come &#39;scd_ondemand&#39;
* &#39;%INFO: Cancellazione di%&#39;) come &#39;clr_dirs&#39;
* &#39;%DEBUG: Passaggio &quot;deploy-static-content&quot; completato%) come &quot;scd_completed&quot;
* &#39;%AVVISO: La compressione del contenuto statico viene ignorata. SCD on demand è abilitato.%) come &#39;scd_compressione_run&#39;,
* &#39;%INFO: Cancellazione della directory var/cache%&#39;) come &#39;clr_var_cach&#39;
* &#39;%DEBUG: Passo &quot;compress-static-content&quot; finito%&quot;) come &#39;scd_compressione_completed&#39;
* &#39;%DEBUG: Passaggio in esecuzione: deploy-complete%) come &#39;deploy_completed&#39;
* &#39;%INFO: Gancio post-distribuzione abilitato. Le operazioni di abilitazione Cron, pulizia della cache e pre-riscaldamento vengono rimandate alla fase di post-distribuzione.%) come &#39;Post_deploy_hook_enabled&#39;
* &#39;%AVVISO: La modalità di manutenzione è disabilitata.%) come &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(i) finito(i)(i)(i)) come &#39;scenario_finito&#39;
* &#39;%post-deploy.xml%&#39;) come &#39;post_deploy_start&#39;
* &#39;%AVVISO: Convalida della configurazione%) come &#39;validate_config&#39;
* &#39;%WARNING: [2003] Il valore del livello di nidificazione della directory per la segnalazione degli errori non è stato configurato.%&#39;) come &#39;nest_err_reporting&#39;
* &#39;%AVVISO: Fine della convalida%) come &#39;end_validation&#39;
* &#39;%INFO: Attiva cron%) come &#39;enable_cron&#39;
* &#39;%INFO: Crea backup di file importanti%) come &#39;create_backup&#39;
* &#39;%DEBUG: Passaggio &quot;backup completato%&quot;) come &#39;backup_finito&#39;
* &#39;%INFO: Inizio riscaldamento pagina%) come &#39;calore_start&#39;
* &#39;%ERRORE: Riscaldamento non riuscito:%) come &#39;riscaldamento_up_fail&#39;
* &#39;%DEBUG: Passo &quot;riscaldamento&quot; finito%&quot;) come &#39;calore_finito&#39;
* &#39;% DEBUG: Passo &quot;time-to-first byte&quot; finito%&quot;) come &#39;ttfb_completed&#39;
* &#39;%INFO: Scenario(i) completato(i)%) come &#39;post_deploy_completed&#39;
* &#39;%DEBUG: Passaggio in esecuzione: pre-build%) come &#39;run_pre-build&#39;
* &#39;%DEBUG: Il contrassegno .static_content_deploy è già stato eliminato%) come &#39;scd_flag_del&#39;
* &#39;%DEBUG: Passaggio &quot;pre-build&quot; finito%&quot;) come &quot;pre-build_completed&quot;
* &#39;%AVVISO: Applicazione delle patch%) come &#39;apply_patch&#39;
* &#39;%è stato applicato%&#39;) come &#39;patch_apply&#39;
* &#39;%DEBUG: Passo &quot;apply-patches&quot; finito%) come &#39;apply_patches_complete&#39;
* &#39;%Distribuisci utilizzando strategia rapida%&#39;) come &#39;quick_strategy_deploy&#39;
* AVVISO &#39;%: Esecuzione di DI compilation%) come &#39;di_compliation_start&#39;
* &#39;%AVVISO: Fine dell&#39;esecuzione della compilazione DI%) come &#39;di_compliation_completed&#39;
* &#39;%AVVISO: Generazione di contenuto statico fresco%) come &#39;gen_frsh_static_content&#39;
* &#39;%magento setup:static-content:deploy%) come &#39;scd_execute&#39;
* &#39;%AVVISO: Fine della generazione del nuovo contenuto statico%) come &#39;gen_frsh_static_cont_completed&#39;
* &#39;%INFO: Scenari iniziali: scenario/build/transfer.xml%) come &#39;start_trasferxml&#39;
* &#39;%INFO: Cercare di uccidere i lavori di cron in corso%&#39;) come &#39;kill_crons&#39;
* &#39;%INFO: Cancellazione della cache del disco rigido:%) come &#39;clear_redis_cache&#39;
* &#39;%INFO: Verifica dell&#39;esistenza di db e hastables%) come &#39;db_check&#39;
* &#39;%WARNING: [2010] Il servizio di Elasticsearch è installato a livello di infrastruttura ma non viene utilizzato come motore di ricerca.%&#39;) come&#39;es_not_used&#39;
* &#39;%AVVISO: Avvio dell&#39;aggiornamento in corso.%) come &#39;start_update&#39;
* &#39;%INFO: Imposta il motore di ricerca su: mysql%) come &#39;mysql_search&#39;
* &#39;%SQLSTATE[HY000] [2006] Il server MySQL è andato via%) come &#39;mysql_go&#39;

## [!UICONTROL Count of modules imported during deploy]

![Numero di moduli importati durante la distribuzione](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

La **[!UICONTROL Count of modules imported during deploy]** frame mostra il numero di moduli importati durante la distribuzione nell&#39;arco temporale selezionato.

## [!UICONTROL Deployed module list]

![Elenco dei moduli distribuiti](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

La **[!UICONTROL Deployed module list]** Il frame mostra i moduli distribuiti nell’arco temporale selezionato.


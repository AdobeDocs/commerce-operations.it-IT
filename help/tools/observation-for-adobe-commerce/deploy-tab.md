---
title: "Il [!UICONTROL Deploy] scheda"
description: Scopri le [!UICONTROL Deploy] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 27ebd472dc4e81e58b36bf5fac529461beae4be1
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

* &#39;`%NOTICE: Starting generate command%`&quot;) come &quot;`start_gen`&#39;
* &#39;`%git apply /app/vendor/magento/ece-tools/patches%`&quot;) come &quot;`apply_patches`&#39;
* &#39;`%Set flag: .static_content_deploy%`&quot;) come &quot;`SCD`&#39;
* &#39;`%NOTICE: Generate command completed%`&quot;) come &quot;`gen_compl`&#39;
* &#39;`%NOTICE: Starting deploy.%`&quot;) come &quot;`start_deploy`&#39;
* &#39;`%NOTICE: Deployment completed%`&quot;) come &quot;`deploy_compl`&#39;
* &#39;`%NOTICE: Starting post-deploy.%`&quot;) come &quot;`start_pdeploy`&#39;
* &#39;`%NOTICE: Post-deploy is complete%`&quot;) come &quot;`pdeploy`&#39;
* &#39;`%deploy-complete%`&quot;) come &quot;`cl_deploy_compl`&#39;

## [!UICONTROL Deploy Log Detail]

![Distribuzione dei dettagli del registro](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

La **[!UICONTROL Deploy Log Detail]** frame mostra i dettagli del riepilogo del messaggio del registro di distribuzione che si sono verificati nell’arco temporale selezionato. Il frame sta analizzando le seguenti stringhe nei log di distribuzione:

* &#39;`%NOTICE: Starting deploy.%`&quot;) come &quot;`start_dply`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/deploy.xml%`&quot;) come &quot;`start_scenario`&#39;
* &#39;`%NOTICE: Starting pre-deploy%`&quot;) come &quot;`strt_predply`&#39;
* &#39;`%INFO: Restoring patch log file%`&quot;) come &quot;`rstr_ptch_log`&#39;
* &#39;`%INFO: Updating cache configuration.%`&quot;) come &quot;`updt_cach_config`&#39;
* &#39;`%INFO: Set Redis slave connection%`&quot;) come &quot;`redis_sec_conn_set`&#39;
* &#39;`%INFO: Static content deployment was performed during build hook, cleaning old content%`&quot;) come &quot;`scd_build_hk`&#39;
* &#39;`%INFO: Clearing pub/static%`&quot;) come &quot;`clr_pub_static`&#39;
* &#39;`%NFO: Clearing redis cache:%`&quot;) come &quot;`clr_redis_cach`&#39;
* &#39;`%INFO: Clearing var/cache directory%`&quot;) come &quot;`clr_var_cach`&#39;
* &#39;`%NOTICE: Enabling Maintenance mode%`&quot;) come &quot;`enable_maint_mode`&#39;
* &#39;`%INFO: Disable cron%`&quot;) come &quot;`disable_cron`&#39;
* &#39;`%INFO: Trying to kill running cron jobs and consumers processes%`&quot;) come &quot;`kill_cron_try`&#39;
* &#39;`%INFO: Running Adobe Commerce cron and consumers processes were not found.%`&quot;) come &quot;`no_cron_fnd`&#39;
* &#39;`%NOTICE: Validating configuration%`&quot;) come &quot;`validate_config`&#39;
* &#39;`%The following admin data is required to create an admin user during initial installation%`&quot;) come &quot;`no_admin`&#39;
* &#39;`%recommended PHP version satisfying the constraint%`&quot;) come &quot;`php_ver_constraint`&#39;
* &#39;`%WARNING: Fix configuration with given suggestions:%`&quot;) come &quot;`fix_config_sugg`&#39;
* &#39;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&quot;) come &quot;`nest_err_reporting`&#39;
* &#39;`%NOTICE: End of validation%`&quot;) come &quot;`end_validation`&#39;
* &#39;`%NOTICE: Starting update.%`&quot;) come &quot;`start_update`&#39;
* &#39;`%INFO: Updating env.php.%`&quot;) come &quot;`update_php_env`&#39;
* &#39;`%INFO: Updating env.php DB connection configuration.%`&quot;) come &quot;`update_php_env_db`&#39;
* &#39;`%INFO: Updating env.php AMQP configuration%`&quot;) come &quot;`update_php_env_amqp`&#39;
* &#39;`%INFO: Set search engine to: elasticsearch7%`&quot;) come &quot;`set_elastic7`&#39;
* &#39;`%elasticsearch 6.5.4 has passed EOL%`&quot;) come &quot;`elastic_ver_EOL`&#39;
* &#39;`%INFO: Set search engine to: elasticsearch6%`&quot;) come &quot;`set_elastic6`&#39;
* &#39;`%INFO: Updating secure and unsecure URLs%`&quot;) come &quot;`update_urls`&#39;
* &#39;`%INFO: Running setup upgrade.%`&quot;) come &quot;`setup_upgrade_run`&#39;
* &#39;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed%`&quot;) come &quot;`post_hook_enabled`&#39;
* &#39;`%NOTICE: Maintenance mode is disabled.%`&quot;) come &quot;`maint_mode_disabled`&#39;
* &#39;`%INFO: Scenario(s) finished%`&quot;) come &quot;`scenario_finished`&#39;
* &#39;`%WARNING: Command maintenance:enable finished with an error. Creating a maintenance flag file%`&quot;) come &quot;`enable_maintenance_fail`&#39;
* &#39;`%MySQL server has gone away%`&quot;) come &quot;`MySQL_has_gone_away`&#39;

## [!UICONTROL Post Deploy Log Detail]

![Dettagli del registro di distribuzione post](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

La **[!UICONTROL Post Deploy Log Detail]** frame mostra i dettagli del registro post-distribuzione che si sono verificati nell’arco temporale selezionato. Questo frame è incentrato su particolari messaggi di log che contengono le seguenti stringhe:

* &#39;`%Disabled maintenance mode%`&quot;) come &quot;`disabled_maint_mode`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/post-deploy.xml%`&quot;) come &quot;`start_pstdply_scenario`&#39;
* &#39;`%NOTICE: Validating configuration%`&quot;) come &quot;`val_config`&#39;
* &#39;`%NOTICE: End of validation%`&quot;) come &quot;`end_val_config`&#39;
* &#39;`%INFO: Enable cron%`&quot;) come &quot;`cron_enabled`&#39;
* &#39;`%INFO: Create backup of important files.%`&quot;) come &quot;`file_backup`&#39;
* &#39;`%INFO: Successfully created backup%`&quot;) come &quot;`file_backup_success`&#39;
* &#39;`%INFO: Starting page warming up%`&quot;) come &quot;`pg_warmup_start`&#39;
* &#39;`%INFO: Warmed up page:%`&quot;) come &quot;`warmed_up_pg`&#39;
* &#39;`%ERROR: Warming up failed:%`&quot;) come &quot;`warm_up_pg_err`&#39;
* &#39;`%INFO: Scenario(s) finished%`&quot;) come &quot;`scenario_finished`&#39;

## [!UICONTROL Cloud Log Detail]

![Dettagli registro cloud](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

La **[!UICONTROL Cloud Log Detail]** frame mostra i dettagli del registro cloud che si sono verificati nell’arco temporale selezionato. Le seguenti stringhe vengono analizzate e restituite con l’etichetta &quot;AS&quot; riportata di seguito:

* &#39;`%DEBUG: /bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade%`&quot;) come &quot;`start_update`&#39;
* &#39;`%Schema creation/updates:%`&quot;) come &quot;`schema_updates`&#39;
* &#39;`%Nothing to import.%`&quot;) come &quot;`mod_import_finish`&#39;
* &#39;`%NOTICE: End of update.%`&quot;) come &quot;`update_finished`&#39;
* &#39;`%DEBUG: Running step: deploy-static-content%`&quot;) come &quot;`scd_run`&#39;
* &#39;`%NOTICE: Skipping static content deploy. SCD on demand is enabled.%`&quot;) come &quot;`scd_ondemand`&#39;
* &#39;`%INFO: Clearing%`&quot;) come &quot;`clr_dirs`&#39;
* &#39;`%DEBUG: Step "deploy-static-content" finished%`&quot;) come &quot;`scd_finished`&#39;
* &#39;`%NOTICE: Skipping static content compression. SCD on demand is enabled.%`&quot;) come &quot;`scd_compression_run`&#39;
* &#39;`%INFO: Clearing var/cache directory%`&quot;) come &quot;`clr_var_cach`&#39;
* &#39;`%DEBUG: Step "compress-static-content" finished%`&quot;) come &quot;`scd_compression_finished`&#39;
* &#39;`%DEBUG: Running step: deploy-complete%`&quot;) come &quot;`deploy_finished`&#39;
* &#39;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed to post-deploy stage.%`&quot;) come &quot;`Post_deploy_hook_enabled`&#39;
* &#39;`%NOTICE: Maintenance mode is disabled.%`&quot;) come &quot;`maint_mode_disabled`&#39;
* &#39;`%INFO: Scenario(s) finished%`&quot;) come &quot;`scenario_finished`&#39;
* &#39;`%post-deploy.xml%`&quot;) come &quot;`post_deploy_start`&#39;
* &#39;`%NOTICE: Validating configuration%`&quot;) come &quot;`validate_config`&#39;
* &#39;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&quot;) come &quot;`nest_err_reporting`&#39;
* &#39;`%NOTICE: End of validation%`&quot;) come &quot;`end_validation`&#39;
* &#39;`%INFO: Enable cron%`&quot;) come &quot;`enable_cron`&#39;
* &#39;`%INFO: Create backup of important files%`&quot;) come &quot;`create_backup`&#39;
* &#39;`%DEBUG: Step "backup" finished%`&quot;) come &quot;`backup_finished`&#39;
* &#39;`%INFO: Starting page warming up%`&quot;) come &quot;`warmup_start`&#39;
* &#39;`%ERROR: Warming up failed:%`&quot;) come &quot;`warm_up_fail`&#39;
* &#39;`%DEBUG: Step "warm-up" finished%`&quot;) come &quot;`warmup_finished`&#39;
* &#39;`%DEBUG: Step "time-to-first-byte" finished%`&quot;) come &quot;`ttfb_finished`&#39;
* &#39;`%INFO: Scenario(s) finished%`&quot;) come &quot;`post_deploy_finished`&#39;
* &#39;`%DEBUG: Running step: pre-build%`&quot;) come &quot;`run_pre-build`&#39;
* &#39;`%DEBUG: Flag .static_content_deploy has already been deleted%`&quot;) come &quot;`scd_flag_del`&#39;
* &#39;`%DEBUG: Step "pre-build" finished%`&quot;) come &quot;`pre-build_completed`&#39;
* &#39;`%NOTICE: Applying patches%`&quot;) come &quot;`apply_patches`&#39;
* &#39;`%has been applied%`&quot;) come &quot;`patches_applied`&#39;
* &#39;`%DEBUG: Step "apply-patches" finished%`&quot;) come &quot;`apply_patches_complete`&#39;
* &#39;`%Deploy using quick strategy%`&quot;) come &quot;`quick_strategy_deploy`&#39;
* &#39;`%NOTICE: Running DI compilation%`&quot;) come &quot;`di_compliation_start`&#39;
* &#39;`%NOTICE: End of running DI compilation%`&quot;) come &quot;`di_compliation_finished`&#39;
* &#39;`%NOTICE: Generating fresh static content%`&quot;) come &quot;`gen_frsh_static_content`&#39;
* &#39;`%magento setup:static-content:deploy%`&quot;) come &quot;`scd_executing`&#39;
* &#39;`%NOTICE: End of generating fresh static content%`&quot;) come &quot;`gen_frsh_static_cont_finished`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/build/transfer.xml%`&quot;) come &quot;`start_transferxml`&#39;
* &#39;`%INFO: Trying to kill running cron jobs%`&quot;) come &quot;`kill_crons`&#39;
* &#39;`%INFO: Clearing redis cache:%`&quot;) come &quot;`clear_redis_cache`&#39;
* &#39;`%INFO: Checking if db exists and has tables%`&quot;) come &quot;`db_check`&#39;
* &#39;`%WARNING: [2010] Elasticsearch service is installed at infrastructure layer, but is not used as a search engine.%`) come &#39;`es_not_used`&#39;
* &#39;`%NOTICE: Starting update.%`&quot;) come &quot;`starting_update`&#39;
* &#39;`%INFO: Set search engine to: mysql%`&quot;) come &quot;`mysql_search`&#39;
* &#39;`%SQLSTATE[HY000] [2006] MySQL server has gone away%`&quot;) come &quot;`mysql_gone`&#39;

## [!UICONTROL Count of modules imported during deploy]

![Numero di moduli importati durante la distribuzione](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

La **[!UICONTROL Count of modules imported during deploy]** frame mostra il numero di moduli importati durante la distribuzione nell&#39;arco temporale selezionato.

## [!UICONTROL Deployed module list]

![Elenco dei moduli distribuiti](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

La **[!UICONTROL Deployed module list]** Il frame mostra i moduli distribuiti nell’arco temporale selezionato.


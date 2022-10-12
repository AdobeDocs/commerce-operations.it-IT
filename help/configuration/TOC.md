---
user-guide-title: Guida alla configurazione
user-guide-description: Configura le funzioni e i servizi dell’applicazione Adobe Commerce o Magenti Open Source.
source-git-commit: b872a61f74818990833ba6b48e061fa1ca69b7cb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Guida alla configurazione {#configuration-guide}

+ [Panoramica](overview.md)
+ Configurazione generale {#setup}
   + [Inizializzazione dell&#39;applicazione e avvio](bootstrap/initialization.md)
   + [Modalità di applicazione](bootstrap/application-modes.md)
   + [Bootstrap parametri](bootstrap/set-parameters.md)
   + [Profiling](bootstrap/mage-profiler.md)
   + [Percorsi directory di base](bootstrap/mage-directory.md)
+ Distribuzione {#deployment}
   + [Panoramica sulla distribuzione](deployment/overview.md)
   + [Distribuzione di singole macchine](deployment/single-machine.md)
   + [Distribuzione di pipeline](deployment/technical-details.md)
   + [Prerequisiti](deployment/prerequisites.md)
   + [Configurazione del sistema di sviluppo](deployment/development-system.md)
   + [Configurazione del sistema di generazione](deployment/build-system.md)
   + [Configurazione del sistema di produzione](deployment/production-system.md)
   + [Autorizzazioni di accesso ai file system](deployment/file-system-permissions.md)
   + Esempi {#examples}
      + [Utilizzo di una configurazione condivisa](deployment/example-shared-configuration.md)
      + [Utilizzo dei comandi CLI](deployment/example-using-cli.md)
      + [Utilizzo delle variabili di ambiente](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Panoramica sulla memorizzazione in cache](cache/caching-overview.md)
   + [Tipi di cache](cache/cache-types.md)
   + [Opzioni cache](cache/cache-options.md)
   + [Cache L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configura Redis](cache/config-redis.md)
      + [Usa Redis per la cache predefinita](cache/redis-pg-cache.md)
      + [Utilizzare Redis per l&#39;archiviazione delle sessioni](cache/redis-session.md)
   + Vernice {#varnish}
      + [Panoramica della vernice](cache/config-varnish.md)
      + [Installa Varnish](cache/config-varnish-install.md)
   + [Server web](cache/config-varnish-server.md)
   + [Configurare l’applicazione Commerce](cache/configure-varnish-commerce.md)
   + [Configurazione avanzata della vernice](cache/config-varnish-advanced.md)
   + [Cancellazione della cache](cache/use-varnish-cache.md)
   + [Cancellazione della cache di più istanze verniciate](cache/use-multiple-varnish-cache.md)
   + [Verificare la configurazione di Varnish](cache/config-varnish-final.md)
   + [Blocco ESI verniciato](cache/use-varnish-esi.md)
   + [Cache del contenuto statico](cache/static-content-signing.md)
+ Riga di comando {#cli}
   + [Strumento da riga di comando](cli/config-cli.md)
   + [Comandi comuni](cli/common-cli-commands.md)
   + [Abilita registrazione](cli/enable-logging.md)
   + [Gestire la cache](cli/manage-cache.md)
   + [Gestire gli indici](cli/manage-indexers.md)
   + [Configurare i lavori cron](cli/configure-cron-jobs.md)
   + [Codice di compilazione](cli/code-compiler.md)
   + [Modalità operativa](cli/set-mode.md)
   + [Avvia i consumatori della coda dei messaggi](cli/start-message-queues.md)
   + [Evidenziatore URN](cli/urn-highlighter.md)
   + [Rapporti di dipendenza](cli/dependency-reports.md)
   + [Localizzazione](cli/localization.md)
   + Gestione della configurazione {#configuration-management}
      + [Imposta valori](cli/set-configuration-values.md)
      + [Impostazioni di esportazione](cli/export-configuration.md)
      + [Importare dati](cli/import-configuration.md)
   + Vista statica {#static-view}
      + [Strategie di distribuzione](cli/static-view-file-strategy.md)
      + [Distribuzione di file di visualizzazione statici](cli/static-view-file-deployment.md)
   + [Creare collegamenti simbolici](cli/create-symlinks.md)
   + [Esecuzione di test di unità](cli/unit-tests.md)
   + [Conversione di file di layout](cli/convert-layout-files.md)
   + [Generare dati per il test delle prestazioni](cli/generate-data.md)
   + [Esegui utilità di supporto (solo Commerce)](cli/run-support-utilities.md)
+ File di configurazione {#files}
   + [File di configurazione per la distribuzione](reference/deployment-files.md)
   + [Tipi di configurazione](reference/config-create-types.md)
   + [File di modulo](reference/module-files.md)
   + [Uscita modulo](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Percorsi di configurazione {#paths}
   + [Generale](reference/config-reference-general.md)
   + [Estensione B2B](reference/config-reference-b2b.md)
   + [Catalogo](reference/config-reference-catalog.md)
   + [Clienti](reference/config-reference-customers.md)
   + [Metodi di pagamento](reference/config-reference-payment.md)
   + [Vendite](reference/config-reference-sales.md)
   + [Servizi](reference/config-reference-services.md)
   + [Impostazioni sensibili e specifiche del sistema](reference/config-reference-sens.md)
   + [Ignora impostazioni di configurazione](reference/override-config-settings.md)
+ Processi Cron {#crons}
   + [Processi e gruppi di lavoro](cron/custom-cron.md)
   + [Personalizzazione del riferimento cronologico](cron/custom-cron-reference.md)
   + [Configurare un processo cron personalizzato](cron/custom-cron-tutorial.md)
+ Registri {#logs}
   + [Registri personalizzati](logs/custom-logging.md)
   + [Interfaccia logger](logs/logger-interface.md)
   + [Attività del database di log](logs/database-activity.md)
   + [Scrivi in un file di registro personalizzato](logs/custom-log-files.md)
+ Code di messaggi {#message-queues}
   + [Framework di coda messaggi](queues/message-queue-framework.md)
   + [Gestire le code dei messaggi](queues/manage-message-queues.md)
   + [Configurare Amazon MQ](queues/aws-mq.md)
+ Siti multipli {#multi-sites}
   + [Più siti e visualizzazioni](multi-sites/ms-overview.md)
   + [ID incremento entità database](multi-sites/change-increment-id.md)
   + [Configurazione nell&#39;amministratore](multi-sites/ms-admin.md)
   + [Configurazione con Nginx](multi-sites/ms-nginx.md)
   + [Configurazione con Apache](multi-sites/ms-apache.md)
+ Motore di ricerca {#search}
   + [Panoramica dei motori di ricerca](search/overview-search.md)
   + [Configurare il motore di ricerca](search/configure-search-engine.md)
   + [Filtrare con fermacarte](search/search-stopwords.md)
+ Sicurezza {#security}
   + [Panoramica sulla sicurezza](security/overview.md)
   + [hashing password](security/password-hashing.md)
   + [Avvelenamento da cache](security/cache-poisoning.md)
   + [PHP cron sicuro](security/secure-cron-php.md)
   + [TXT di sicurezza](security/security-txt.md)
   + [Intestazione X-Frame-Options](security/xframe-options.md)
+ Storage {#storage}
   + [Profilo database](storage/db-profiler.md)
   + Archiviazione remota {#remote-storage}
      + [Modulo di archiviazione remota](remote-storage/remote-storage.md)
      + [bucket AWS S3](remote-storage/remote-storage-aws-s3.md)
      + [Ridimensionamento dell&#39;immagine](remote-storage/remote-storage-image-resize.md)
      + [Archiviazione remota per cloud](remote-storage/cloud-support.md)
   + Session storage {#session-storage}
      + [Percorso di archiviazione sessione](storage/sessions.md)
      + [memorizzato in cache per l&#39;archiviazione delle sessioni](storage/memcached.md)
      + [memorizzato in cache su CentOS](storage/memcache-centos.md)
      + [Mecca su Ubuntu](storage/memcache-ubuntu.md)
   + Database diviso {#split-db}
      + [Panoramica del database diviso](storage/multi-master.md)
      + [Configurazione automatica](storage/multi-master-masterdb.md)
      + [Configurazione manuale](storage/multi-master-manual.md)
      + [Verificare il database diviso](storage/multi-master-verify.md)
      + [Replica del database](storage/multi-master-replication.md)
      + [Ripristino del database singolo](storage/revert-split-database.md)

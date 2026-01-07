---
user-guide-title: Guida alla configurazione
user-guide-description: Configura le funzioni e i servizi dell’applicazione Adobe Commerce.
feature: Configuration
source-git-commit: d86b9eb07a9da6dc93234f8a02103c543bbead68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---


# Guida alla configurazione {#configuration-guide}

+ [Panoramica](overview.md)
+ Configurazione generale {#setup}
   + [Inizializzazione e avvio dell&#39;applicazione](bootstrap/initialization.md)
   + [Modalità di applicazione](bootstrap/application-modes.md)
   + [Parametri Bootstrap](bootstrap/set-parameters.md)
   + [Profilatura](bootstrap/mage-profiler.md)
   + [Percorsi directory base](bootstrap/mage-directory.md)
+ Distribuzione {#deployment}
   + [Panoramica sulla distribuzione](deployment/overview.md)
   + [Distribuzione di un singolo computer](deployment/single-machine.md)
   + [Distribuzione della pipeline](deployment/technical-details.md)
   + [Prerequisiti](deployment/prerequisites.md)
   + [Configurazione del sistema di sviluppo](deployment/development-system.md)
   + [Configurazione del sistema di build](deployment/build-system.md)
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
      + [Configurare Redis](cache/config-redis.md)
      + [Usa Redis per la cache predefinita](cache/redis-pg-cache.md)
      + [Usa Redis per l’archiviazione della sessione](cache/redis-session.md)
      + [Configurare ElastiCache per le istanze EC2](cache/redis-elasticache-for-ec2.md)
   + Valkey {#valkey}
      + [Configura Valkey](cache/config-valkey.md)
      + [Usa Valkey per la cache predefinita](cache/valkey-pg-cache.md)
      + [Usa Valkey per l&#39;archiviazione della sessione](cache/valkey-session.md)
   + Vernice {#varnish}
      + [Panoramica sulla vernice](cache/config-varnish.md)
      + [Installa vernice](cache/config-varnish-install.md)
   + [Server web](cache/config-varnish-server.md)
   + [Configurare l’applicazione Commerce](cache/configure-varnish-commerce.md)
   + [Configurazione vernice avanzata](cache/config-varnish-advanced.md)
   + [Cancellazione della cache](cache/use-varnish-cache.md)
   + [Cancellazione della cache di più istanze di vernice](cache/use-multiple-varnish-cache.md)
   + [Verifica configurazione vernice](cache/config-varnish-final.md)
   + [Blocco ESI vernice](cache/use-varnish-esi.md)
   + [Cache del contenuto statico](cache/static-content-signing.md)
+ Riga di comando {#cli}
   + [Strumento da riga di comando](cli/config-cli.md)
   + [Comandi comuni](cli/common-cli-commands.md)
   + [Abilita registrazione](cli/enable-logging.md)
   + [Gestire la cache](cli/manage-cache.md)
   + [Gestisci indicizzatori](cli/manage-indexers.md)
   + [Configurare i processi cron](cli/configure-cron-jobs.md)
   + [Compila codice](cli/code-compiler.md)
   + [Modalità operativa](cli/set-mode.md)
   + [Avvia consumer coda messaggi](cli/start-message-queues.md)
   + [Evidenziatore URN](cli/urn-highlighter.md)
   + [Rapporti sulle dipendenze](cli/dependency-reports.md)
   + [Localizzazione](cli/localization.md)
   + Gestione della configurazione {#configuration-management}
      + [Imposta valori](cli/set-configuration-values.md)
      + [Impostazioni di esportazione](cli/export-configuration.md)
      + [Importare dati](cli/import-configuration.md)
   + Vista statica {#static-view}
      + [Strategie di implementazione](cli/static-view-file-strategy.md)
      + [Distribuire file di visualizzazione statica](cli/static-view-file-deployment.md)
   + [Creare collegamenti simbolici](cli/create-symlinks.md)
   + [Eseguire unit test](cli/unit-tests.md)
   + [Conversione di file di layout](cli/convert-layout-files.md)
   + [Genera dati per test delle prestazioni](cli/generate-data.md)
   + [Esecuzione di utilità di supporto (solo Commerce)](cli/run-support-utilities.md)
+ File di configurazione {#files}
   + [File di configurazione per la distribuzione](reference/deployment-files.md)
   + [Tipi di configurazione](reference/config-create-types.md)
   + [File modulo](reference/module-files.md)
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
   + [Processi e gruppi di controllo](cron/custom-cron.md)
   + [Personalizzazione del riferimento crons](cron/custom-cron-reference.md)
   + [Configurare un processo cron personalizzato](cron/custom-cron-tutorial.md)
+ Registri {#logs}
   + [Registri personalizzati](logs/custom-logging.md)
   + [Interfaccia logger](logs/logger-interface.md)
   + [Registra attività database](logs/database-activity.md)
   + [Scrivi in un file di registro personalizzato](logs/custom-log-files.md)
+ Code messaggi {#message-queues}
   + [Framework coda messaggi](queues/message-queue-framework.md)
   + [Gestire le code dei messaggi](queues/manage-message-queues.md)
   + [Configurare Amazon MQ](queues/aws-mq.md)
   + [Consumatori](queues/consumers.md)
+ Più siti {#multi-sites}
   + [Più siti e visualizzazioni](multi-sites/ms-overview.md)
   + [ID incremento entità database](multi-sites/change-increment-id.md)
   + [Configurare in Admin](multi-sites/ms-admin.md)
   + [Configurazione con Nginx](multi-sites/ms-nginx.md)
   + [Configurazione con Apache](multi-sites/ms-apache.md)
+ Motore di ricerca {#search}
   + [Panoramica dei motori di ricerca](search/overview-search.md)
   + [Configurare il motore di ricerca](search/configure-search-engine.md)
   + [Filtra con parole d&#39;arresto](search/search-stopwords.md)
+ Sicurezza {#security}
   + [Panoramica sulla sicurezza](security/overview.md)
   + [Hashing password](security/password-hashing.md)
   + [Avvelenamento della cache](security/cache-poisoning.md)
   + [Cron PHP sicuro](security/secure-cron-php.md)
   + [TXT di sicurezza](security/security-txt.md)
   + [Prese clic su Exploits](security/xframe-options.md)
+ Storage {#storage}
   + [Database profiler](storage/db-profiler.md)
   + Archiviazione remota {#remote-storage}
      + [Modulo di archiviazione remota](remote-storage/remote-storage.md)
      + [Bucket AWS S3](remote-storage/remote-storage-aws-s3.md)
      + [Ridimensionamento immagine](remote-storage/remote-storage-image-resize.md)
      + [Archiviazione remota per cloud](remote-storage/cloud-support.md)
   + Archiviazione sessione {#session-storage}
      + [Percorso di archiviazione sessione](storage/sessions.md)
      + [memcached per l’archiviazione della sessione](storage/memcached.md)
      + [memcached su CentOS](storage/memcache-centos.md)
      + [memcached su Ubuntu](storage/memcache-ubuntu.md)
   + Dividi database {#split-db}
      + [Panoramica sulla suddivisione del database](storage/multi-master.md)
      + [Configurazione automatica](storage/multi-master-masterdb.md)
      + [Configurazione manuale](storage/multi-master-manual.md)
      + [Verifica database diviso](storage/multi-master-verify.md)
      + [Replica del database](storage/multi-master-replication.md)
      + [Ripristina database singolo](storage/revert-split-database.md)
+ [Torna alle guide operative](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html?lang=it)
---
user-guide-title: Playbook di implementazione
user-guide-description: Scopri le strategie per la pianificazione e l’implementazione di un sito Adobe Commerce di successo.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# Playbook di implementazione {#implementation-playbook}

- [Panoramica](overview.md)
- Commerce {#intro}
   - [Informazioni su Adobe Commerce](intro/about-commerce.md)
   - [Principi di sviluppo delle piattaforme](intro/platform-development.md)
- Ambito del progetto {#project-scope}
   - [La conoscenza è potere](project-scope/knowledge.md)
   - [Principali parti interessate](project-scope/key-stakeholders.md)
   - [Processo e timeline](project-scope/process-timeline.md)
   - [Deliverables](project-scope/deliverables.md)
   - [Elenchi di controllo dei requisiti](project-scope/requirement-checklists.md)
- Sviluppo {#development}
   - [Strumenti della piattaforma](development/platform-tools.md)
   - [Strumenti di gestione dei progetti](development/project-management-tools.md)
   - [Metodologia di attuazione del progetto](development/delivery.md)
   - [Controllo qualità](development/quality-control.md)
- Pianificazione e governance {#planning}
   - [Approccio di consegna e pianificazione](planning/delivery.md)
   - [Responsabilità e titolarità](planning/ownership.md)
   - [Governance dei progetti](planning/governance.md)
- Architettura e integrazioni {#architecture}
   - [Riferimento Enterprise](architecture/enterprise-blueprint.md)
   - Architettura di riferimento globale {#global-reference-architecture}
      - [Panoramica](architecture/global-reference/overview.md)
      - [Esempi](architecture/global-reference/examples.md)
      - Sviluppo del compositore {#composer}
         - [Panoramica](architecture/global-reference/composer/overview.md)
         - [Struttura del progetto](architecture/global-reference/composer/project-structure.md)
         - [Suggerimenti](architecture/global-reference/composer/tips-and-tricks.md)
- Infrastruttura e distribuzione {#infrastructure}
   - [Panoramica](infrastructure/overview.md)
   - Hosting autonomo {#self-hosting}
      - [Panoramica](infrastructure/self-hosting/overview.md)
      - [Infrastruttura locale](infrastructure/self-hosting/on-premises.md)
      - [Concetti di sicurezza](infrastructure/self-hosting/security-concepts.md)
      - [Monitoraggio di strumenti e telemetria](infrastructure/self-hosting/monitoring-tools.md)
      - [Idee di disaster recovery](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Suggerimenti sulle prestazioni](infrastructure/self-hosting/performance-tips.md)
   - Infrastruttura cloud {#cloud}
      - [Panoramica](infrastructure/cloud/overview.md)
      - [Aree geografiche](infrastructure/cloud/regions.md)
      - [Tecnologie](infrastructure/cloud/technology.md)
      - [Sicurezza e conformità](infrastructure/cloud/security.md)
   - Ottimizzazione delle prestazioni {#performance}
      - [Problemi tipici](infrastructure/performance/optimization.md)
      - [Benchmark](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Preparazione del lancio {#launch}
   - [Panoramica](launch/overview.md)
   - [Passaggi precedenti all’avvio](launch/pre-launch-steps.md)
   - [Passaggi di avvio](launch/launch-steps.md)
   - [Passaggi per l’avvio di Post](launch/post-launch-steps.md)
- Manutenzione e supporto {#maintenance}
   - [Panoramica](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Best practice {#best-practices}
   - [Panoramica](best-practices/phases.md)
   - Pianificazione di {#planning}
      - [Panoramica](best-practices/planning/overview.md)
      - [Gestione catalogo](best-practices/planning/catalog-management.md)
      - [Configurazione di siti, archivi e viste archivio](best-practices/planning/sites-stores-store-views.md)
      - [Configurazione del reporting](best-practices/planning/reporting-configuration.md)
      - [Configurazione del database per le distribuzioni cloud&#x200B;](best-practices/planning/database-on-cloud.md)
      - [Configurazione MySQL](best-practices/planning/mysql-configuration.md)
      - [Configurazione del servizio Redis](best-practices/planning/redis-service-configuration.md)
      - [Dimensioni memoria OPcache](best-practices/planning/opcache-memory-size.md)
      - [Dimensioni cache realpath](best-practices/planning/realpath-cache-size.md)
      - [Estensioni](best-practices/planning/extensions.md)
      - [Inoltri per partner](best-practices/planning/partner-escalation.md)
      - [Elaborazione archiviazione pagamenti](best-practices/planning/payment-processing-storage.md)
   - Sviluppo {#development}
      - [Panoramica](best-practices/development/overview.md)
      - [Best practice generali](best-practices/development/general.md)
      - [Gestione del codice](best-practices/development/code-management.md)
      - [Revisione del codice](best-practices/development/code-review.md)
      - [Debug](best-practices/development/debugging.md)
      - [Gestione delle eccezioni](best-practices/development/exception-handling.md)
      - [Diramazione Git](best-practices/development/git-branching.md)
      - [Ridimensionamento immagine catalogo](best-practices/development/catalog-image-resizing.md)
      - [Ottimizzazione immagine](best-practices/development/image-optimization.md)
      - [Risoluzione dei problemi](best-practices/development/troubleshooting.md)
      - [Ottimizzare i file CSS e JS](best-practices/development/optimize-css-js-files.md)
      - [Blocchi di contenuto privato](best-practices/development/private-content-block-configuration.md)
      - [Distribuzione di contenuti statici](best-practices/development/static-content-deployment.md)
      - [Modifica delle tabelle di database](best-practices/development/modifying-core-and-third-party-tables.md)
      - [Modifica del codice principale e di terze parti](best-practices/development/modifying-core-and-third-party-code.md)
   - Avvia {#launch}
      - [Panoramica](best-practices/launch/overview.md)
      - [Configura web crawler](best-practices/launch/robots-txt.md)
      - [Proteggere il sito e l&#39;infrastruttura](best-practices/launch/security-best-practices.md)
   - Manutenzione {#maintenance}
      - [Panoramica](best-practices/maintenance/overview.md)
      - [Verifica prestazioni front-end](best-practices/maintenance/frontend-performance.md)
      - [Ottimizzare le prestazioni del back-end](best-practices/maintenance/backend-performance.md)
      - [Configurazione indicizzatore](best-practices/maintenance/indexer-configuration.md)
      - [Applicazione di patch su scala](best-practices/maintenance/patching-at-scale.md)
      - [Elaborazione ordine](best-practices/maintenance/order-processing-configuration.md)
      - [Risolvere i problemi di prestazioni del database](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Rispondere agli incidenti di sicurezza](best-practices/maintenance/respond-to-security-incident.md)
      - [Pianificazione degli aggiornamenti dell’amministratore nei siti di produzione](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Aggiorna servizi](best-practices/maintenance/update-services.md)
      - [Elenco di controllo per l’aggiornamento](best-practices/maintenance/upgrade-checklist.md)
      - [Prerequisiti per l&#39;aggiornamento di MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [Torna alle guide operative](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)

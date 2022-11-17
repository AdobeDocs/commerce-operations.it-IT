---
user-guide-title: Playbook di implementazione
user-guide-description: Scopri le strategie per la pianificazione e l’implementazione di un sito Adobe Commerce di successo.
mini-toc-levels: 3
source-git-commit: e856fd2a6a5bde96896f624fc0914e990d20d4cc
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 6%

---


# Playbook di implementazione {#implementation-playbook}

- [Panoramica](overview.md)
- Commerce {#intro}
   - [Informazioni su Adobe Commerce](intro/about-commerce.md)
   - [Principi dello sviluppo delle piattaforme](intro/platform-development.md)
- Ambito del progetto {#project-scope}
   - [La conoscenza è potere](project-scope/knowledge.md)
   - [Principali soggetti interessati](project-scope/key-stakeholders.md)
   - [Processo e timeline](project-scope/process-timeline.md)
   - [Risultati finali](project-scope/deliverables.md)
   - [Lista di controllo dei requisiti](project-scope/requirement-checklists.md)
- Sviluppo {#development}
   - [Strumenti della piattaforma](development/platform-tools.md)
   - [Strumenti di gestione dei progetti](development/project-management-tools.md)
   - [Metodologia di implementazione del progetto](development/delivery.md)
   - [Controllo della qualità](development/quality-control.md)
- Pianificazione e governance {#planning}
   - [Approccio di distribuzione e pianificazione](planning/delivery.md)
   - [Responsabilità e proprietà](planning/ownership.md)
   - [Governance dei progetti](planning/governance.md)
- Architettura e integrazioni {#architecture}
   - [Funzionalità](architecture/capabilities.md)
   - [Strategia di integrazione](architecture/integration-strategy.md)
   - [Strategia di estensibilità](architecture/extensibility-strategy.md)
   - [Opzioni di integrazione](architecture/integration-options.md)
   - [Architettura di riferimento globale](architecture/global-reference.md)
   - Commercio headless {#headless}
      - [Vantaggi](architecture/headless/benefits.md)
      - [Percorso senza testa](architecture/headless/journey-to-headless.md)
      - [Microservizi](architecture/headless/microservices.md)
      - [Evoluzione senza testa](architecture/headless/evolution.md)
      - [Architettura della vetrina abbinata](architecture/headless/legacy-storefront.md)
      - [Architettura headless](architecture/headless/adobe-commerce.md)
- Infrastruttura e diffusione {#infrastructure}
   - [Panoramica](infrastructure/overview.md)
   - [Infrastruttura interna](infrastructure/on-premises.md)
   - Infrastruttura cloud {#cloud}
      - [Panoramica](infrastructure/cloud/overview.md)
      - [Aree geografiche](infrastructure/cloud/regions.md)
      - [Tecnologie](infrastructure/cloud/technology.md)
      - [Ambienti](infrastructure/cloud/environments.md)
      - [Servizi gestiti](infrastructure/cloud/managed-services.md)
      - [Sicurezza e conformità](infrastructure/cloud/security.md)
   - Ottimizzazione delle prestazioni {#performance}
      - [Problemi tipici](infrastructure/performance/optimization.md)
      - [Benchmark](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Preparazione al lancio {#launch}
   - [Panoramica](launch/overview.md)
   - [Passaggi pre-lancio](launch/pre-launch-steps.md)
   - [Passaggi di avvio](launch/launch-steps.md)
   - [Passaggi successivi al lancio](launch/post-launch-steps.md)
- Manutenzione e supporto {#maintenance}
   - [Panoramica](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Best practice {#best-practices}
   - [Panoramica](best-practices/phases.md)
   - Pianificazione {#planning}
      - [Panoramica](best-practices/planning/overview.md)
      - [Configurazione di siti, archivi e viste store](best-practices/planning/sites-stores-store-views.md)
      - [Configurazione del reporting](best-practices/planning/reporting-configuration.md)
      - [Configurazione del database per le distribuzioni cloud &#x200B;](best-practices/planning/database-on-cloud.md)
      - [&#x200B; di configurazione della connessione slave MySQL](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [Utilizzo di MySQL trigger](best-practices/planning/mysql-triggers-usage.md)
      - [Configurazione del servizio Redis](best-practices/planning/redis-service-configuration.md)
      - [Dimensione della memoria OPcache](best-practices/planning/opcache-memory-size.md)
      - [Dimensione della cache del percorso reale](best-practices/planning/realpath-cache-size.md)
      - [Categorie](best-practices/planning/category-limits.md)
      - [Prodotto](best-practices/planning/product-sku-limits.md)
      - [Varianti di prodotto](best-practices/planning/product-variations.md)
      - [Opzioni di prodotto](best-practices/planning/product-options.md)
      - [Attributi del prodotto](best-practices/planning/product-attributes-and-options.md)
      - [Paginazione dell’elenco dei prodotti](best-practices/planning/product-listing-pagination.md)
      - [Limite del carrello del prodotto](best-practices/planning/product-cart.md)
      - [Promozioni](best-practices/planning/product-cart-promotions.md)
      - [Estensioni](best-practices/planning/extensions.md)
      - [Aumento dei partner](best-practices/planning/partner-escalation.md)
      - [Elaborazione archiviazione pagamenti](best-practices/planning/payment-processing-storage.md)
   - Sviluppo {#development}
      - [Panoramica](best-practices/development/overview.md)
      - [Ottimizzazione delle immagini](best-practices/development/image-optimization.md)
      - [Risoluzione dei problemi](best-practices/development/troubleshooting.md)
      - [Ottimizzare i file CSS e JS](best-practices/development/optimize-css-js-files.md)
      - [Blocchi di contenuto privati](best-practices/development/private-content-block-configuration.md)
      - [Distribuzione di contenuti statici](best-practices/development/static-content-deployment.md)
      - [Modifica delle tabelle di database](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [Panoramica](best-practices/launch/overview.md)
      - [Servizio di notifica della sicurezza di Adobe](best-practices/launch/security-notification-service.md)
      - [Configurare il file robots.txt](best-practices/launch/robots-txt.md)
      - [Prevenire e rispondere agli incidenti di sicurezza](best-practices/launch/prevent-respond-security-incident.md)
   - Manutenzione {#maintenance}
      - [Panoramica](best-practices/maintenance/overview.md)
      - [Prestazioni frontali di controllo](best-practices/maintenance/frontend-performance.md)
      - [Configurazione indicizzatore](best-practices/maintenance/indexer-configuration.md)
      - [Elaborazione dell&#39;ordine](best-practices/maintenance/order-processing-configuration.md)
      - [Pianificazione degli aggiornamenti dell&#39;amministratore sui siti di produzione](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Aggiorna servizi](best-practices/maintenance/update-services.md)
      - [Elenco di controllo per l&#39;aggiornamento](best-practices/maintenance/upgrade-checklist.md)
      - [Risolvere i problemi di prestazioni del database &#x200B;](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Prerequisiti per l’aggiornamento ad Adobe Commerce 2.3.5 per MariaDB &#x200B;](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)

---
title: Strumenti della piattaforma
description: Scegli gli strumenti di piattaforma consigliati per l’implementazione di Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Platform tools

Non c&#39;è carenza di aspetti che devono essere ben pensati e rigorosamente testati per mantenere un sito di e-commerce in esecuzione senza interferenze. Non solo devi identificare le soluzioni giuste per affrontare ogni aspetto del sito, dall&#39;archiviazione e programmazione dei dati alla memorizzazione in cache e alla sicurezza, ma devi anche disporre del processo giusto per garantire la distribuzione di una piattaforma che funzioni in modo regolare e possa essere costruita e ottimizzata in modo efficiente.

Questa sezione offre non solo uno sguardo agli strumenti, alle soluzioni, ai processi e alle metodologie testati e perfezionati in diverse implementazioni di Adobe Commerce, ma anche i nostri consigli per i quali le soluzioni soddisfano al meglio specifiche esigenze e obiettivi aziendali.

The following table includes solutions that we recommend and can be used within Adobe Commerce to drive performance on the platform:

| Finalità | Strumento |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Linguaggio di programmazione | PHP, JS, HTML, MENO CSS |
| Ambiente di sviluppo integrato (IDE) | Eclipse, PHPStorm |
| Web server | Nginx, Apache |
| Caching services | Redis, Varnish |
| Servizi di ricerca | Elasticsearch |
| Servizi coda messaggi | RabbitMQ |
| Strumento di scansione della sicurezza | SonarQube, ZAP |

## Datbase

There are three different tools that we use depending on the needs of the brand. MySQL è una soluzione di base ideale come il database di Adobe Commerce se non si prevede che il tuo archivio gestisca carichi estremi.

MariaDB è più incentrata sulla comunità e funziona meglio per gli utenti che si preoccupano più delle funzionalità che delle prestazioni pure. MariaDB supporta un&#39;ampia gamma di motori di database, crittografia del disco, interconnettività orizzontale complessa e funzioni di scalabilità, che potrebbero essere interessanti per i grandi negozi Commerce di Adobe.

Percona is a fork of MySQL that centers around performance and peak load handling. Scegli MariaDB se hai bisogno di più qualità della vita e funzioni DevOps. Go for Percona if your goal is to gain high-load performance in large-scale datasets.

## Linguaggio di programmazione

Adobe Commerce is a PHP-based application and the newest releases are always compatible with the latest stable PHP version (for example, Adobe Commerce version 2.4 recommends using PHP 7.4). To get more security and performance, there are several factors to account for when configuring PHP to get maximum speed and efficiency on request processing. The Adobe Commerce web storefront is built with HTML, JavaScript, and the LESS CSS pre-processor.

## Web servers

Adobe Commerce fully supports the Nginx and Apache web servers. Adobe Commerce fornisce file di configurazione consigliati di esempio per entrambi:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## Servizi di memorizzazione nella cache

Adobe Commerce provides numerous options to store your cache and session data, including Redis, Memcache, filesystem, and database. For a setup with multiple web nodes, Redis is the best option.

We highly recommend using Varnish as the full-page cache server for your store. Adobe Commerce distributes a sample configuration file for Varnish that contains all recommended settings for performance.

## Servizi di ricerca

Ad Adobe, Commerce versione 2.4 e successive, tutte le installazioni devono essere configurate per utilizzare Elasticsearch come soluzione di ricerca nel catalogo. Elasticsearch fornisce ricerche rapide e avanzate sui prodotti nel catalogo. Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## Message queue services

Le code dei messaggi forniscono un meccanismo di comunicazione asincrono in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. RabbitMQ è un broker di messaggi open-source che offre un sistema di messaggistica affidabile, altamente disponibile, scalabile e portatile.

## Security tools

Il [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) consente di monitorare regolarmente i siti web del negozio e ricevere aggiornamenti per rischi noti di sicurezza, malware e software obsoleto. In genere, si inizia a utilizzare questo strumento quando si inizia il test di accettazione da parte dell&#39;utente (UAT). Oltre allo strumento Adobe Commerce Security Scan, gratuito e disponibile per tutte le implementazioni e le versioni di Adobe Commerce, ci sono altre scelte che possono essere utilizzate durante il processo CI/CD e prima di ogni versione.

SonarQube è una piattaforma di gestione della qualità open source progettata per analizzare e misurare la qualità tecnica del codice. SonarQube not only provides a complete report of code bugs, syntax errors, and vulnerabilities, but also offers suggestions and examples for fixing your code. SonarQube è perfetto per essere utilizzato in un ambiente CI/CD come strumento in grado di analizzare il codice prima di essere implementato.

Zed Attack Proxy (ZAP) è uno strumento gratuito di test di sicurezza utilizzato da migliaia di pen-tester in tutto il mondo. ZAP is developed by OWASPand is one of the most preferred tools for manual security testing.

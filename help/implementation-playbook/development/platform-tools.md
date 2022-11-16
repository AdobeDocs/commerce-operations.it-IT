---
title: Strumenti della piattaforma
description: Scegli gli strumenti di piattaforma consigliati per l’implementazione di Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Strumenti della piattaforma

Non c&#39;è carenza di aspetti che devono essere ben pensati e rigorosamente testati per mantenere un sito di e-commerce in esecuzione senza interferenze. Non solo devi identificare le soluzioni giuste per affrontare ogni aspetto del sito, dall&#39;archiviazione e programmazione dei dati alla memorizzazione in cache e alla sicurezza, ma devi anche disporre del processo giusto per garantire la distribuzione di una piattaforma che funzioni in modo regolare e possa essere costruita e ottimizzata in modo efficiente.

Questa sezione offre non solo uno sguardo agli strumenti, alle soluzioni, ai processi e alle metodologie testati e perfezionati in diverse implementazioni di Adobe Commerce, ma anche i nostri consigli per i quali le soluzioni soddisfano al meglio specifiche esigenze e obiettivi aziendali.

La tabella seguente include soluzioni consigliate e utilizzabili in Adobe Commerce per migliorare le prestazioni sulla piattaforma:

| Finalità | Strumento |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Linguaggio di programmazione | PHP, JS, HTML, MENO CSS |
| Ambiente di sviluppo integrato (IDE) | Eclipse, PHPStorm |
| Server web | Nginx, Apache |
| Servizi di memorizzazione nella cache | Redis, Varnish |
| Servizi di ricerca | Elasticsearch |
| Servizi coda messaggi | [!DNL RabbitMQ] |
| Strumento di scansione della sicurezza | SonarQube, ZAP |

## Database

Ci sono tre strumenti diversi che usiamo a seconda delle esigenze del marchio. MySQL è una soluzione di base ideale come il database Adobe Commerce, se non si prevede che lo store gestisca carichi estremi.

MariaDB è più incentrata sulla comunità e funziona meglio per gli utenti che si preoccupano più delle funzionalità che delle prestazioni pure. MariaDB supporta un&#39;ampia gamma di motori di database, crittografia del disco, interconnettività orizzontale complessa e funzioni di scalabilità, che potrebbero essere interessanti per i grandi negozi Adobe Commerce.

Percona è un fork di MySQL che ruota attorno alle prestazioni e alla gestione del carico di picco. Scegli MariaDB se hai bisogno di più qualità della vita e funzioni DevOps. Vai a Percona se il tuo obiettivo è quello di ottenere prestazioni ad alto carico in set di dati su larga scala.

## Linguaggio di programmazione

Adobe Commerce è un&#39;applicazione basata su PHP e le ultime versioni sono sempre compatibili con l&#39;ultima versione stabile di PHP (ad esempio, Adobe Commerce versione 2.4 consiglia di utilizzare PHP 7.4). Per ottenere maggiore sicurezza e prestazioni, ci sono diversi fattori da tenere in considerazione durante la configurazione di PHP per ottenere la massima velocità ed efficienza nell&#39;elaborazione delle richieste. La vetrina web Adobe Commerce è realizzata con HTML, JavaScript e il pre-processore CSS LESS.

## Server web

Adobe Commerce supporta completamente i server web Nginx e Apache. Adobe Commerce fornisce file di configurazione consigliati di esempio per entrambi:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

L&#39;esempio Nginx contiene le impostazioni per migliorare le prestazioni ed è progettato in modo da richiedere una piccola riconfigurazione.

## Servizi di memorizzazione nella cache

Adobe Commerce fornisce numerose opzioni per memorizzare la cache e i dati di sessione, tra cui Redis, Memcache, filesystem e database. Per una configurazione con più nodi web, l&#39;opzione migliore è Redis.

Consigliamo vivamente di utilizzare Varnish come server di cache a pagina intera per il tuo negozio. Adobe Commerce distribuisce un file di configurazione di esempio per Varnish che contiene tutte le impostazioni consigliate per le prestazioni.

## Servizi di ricerca

Per Adobe Commerce versione 2.4 e successive, tutte le installazioni devono essere configurate per utilizzare Elasticsearch come soluzione di ricerca nel catalogo. Elasticsearch fornisce ricerche rapide e avanzate sui prodotti nel catalogo. L’Elasticsearch è facoltativo per le versioni precedenti alla versione 2.4, ma è consigliato.

## Servizi coda messaggi

Le code dei messaggi forniscono un meccanismo di comunicazione asincrono in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. [!DNL RabbitMQ] è un broker di messaggi open-source che offre un sistema di messaggistica affidabile, altamente disponibile, scalabile e portatile.

## Strumenti di sicurezza

La [Strumento di scansione della sicurezza Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html) consente di monitorare regolarmente i siti web del negozio e ricevere aggiornamenti per rischi noti di sicurezza, malware e software obsoleto. In genere, si inizia a utilizzare questo strumento quando si inizia il test di accettazione da parte dell&#39;utente (UAT). Oltre allo strumento Adobe Commerce Security Scan, gratuito e disponibile per tutte le implementazioni e le versioni di Adobe Commerce, ci sono altre scelte che possono essere utilizzate durante il processo CI/CD e prima di ogni versione.

SonarQube è una piattaforma di gestione della qualità open source progettata per analizzare e misurare la qualità tecnica del codice. SonarQube non solo fornisce un rapporto completo di bug del codice, errori di sintassi e vulnerabilità, ma offre anche suggerimenti ed esempi per la correzione del codice. SonarQube è perfetto per essere utilizzato in un ambiente CI/CD come strumento in grado di analizzare il codice prima di essere implementato.

Zed Attack Proxy (ZAP) è uno strumento gratuito di test di sicurezza utilizzato da migliaia di pen-tester in tutto il mondo. ZAP è sviluppato da OWASPed è uno degli strumenti più preferiti per il test di sicurezza manuale.

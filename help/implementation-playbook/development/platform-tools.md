---
title: Strumenti della piattaforma
description: Scegli gli strumenti di piattaforma consigliati per la tua implementazione di Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Strumenti della piattaforma

Non mancano aspetti che devono essere attentamente studiati e testati per mantenere un sito di e-commerce in funzione senza interferenze. Non solo è necessario individuare le soluzioni più adatte per affrontare ogni aspetto del sito, dallo storage dei dati e dalla programmazione alla memorizzazione in cache e alla sicurezza, ma è necessario il processo giusto per garantire la distribuzione di una piattaforma che funzioni senza problemi e che possa essere creata e ottimizzata in modo efficiente.

In questa sezione troverai non solo strumenti, soluzioni, processi e metodologie testati e perfezionati in diverse implementazioni di Adobe Commerce, ma anche i nostri consigli per individuare le soluzioni più adatte a specifiche esigenze e obiettivi aziendali.

La tabella seguente include le soluzioni consigliate e utilizzabili in Adobe Commerce per migliorare le prestazioni sulla piattaforma:

| Finalità | Strumento |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Linguaggio di programmazione | PHP, JS, HTML, MENO CSS |
| Ambiente di sviluppo integrato (IDE) | Eclipse, PHPStorm |
| Server web | Nginx, Apache |
| Servizi di caching | Redis, vernice |
| Servizi di ricerca | Elasticsearch |
| Servizi coda messaggi | [!DNL RabbitMQ] |
| Strumento di analisi della sicurezza | SonarQube, ZAP |

## Database

A seconda delle esigenze del marchio, vengono utilizzati tre diversi strumenti. MySQL è un&#39;ottima soluzione di base come il database Adobe Commerce, se non ti aspetti che il tuo archivio gestisca carichi estremi.

MariaDB si concentra maggiormente sulla community e funziona meglio per gli utenti che si preoccupano più delle funzioni che delle prestazioni pure. MariaDB supporta una vasta gamma di motori di database, crittografia del disco, interconnettività orizzontale complessa e funzioni di scalabilità, che potrebbero essere interessanti per i grandi store Adobe Commerce.

Percona è un fork di MySQL incentrato sulle prestazioni e sulla gestione dei picchi di carico. Scegli MariaDB se hai bisogno di più qualità di vita e funzioni DevOps. Scegli Percona se il tuo obiettivo è quello di ottenere prestazioni ad alto carico in set di dati su larga scala.

## Linguaggio di programmazione

Adobe Commerce è un’applicazione basata su PHP e le versioni più recenti sono sempre compatibili con l’ultima versione stabile di PHP (ad esempio, Adobe Commerce versione 2.4 consiglia di utilizzare PHP 7.4). Per ottenere più sicurezza e prestazioni, ci sono diversi fattori da tenere in considerazione quando si configura PHP per ottenere la massima velocità ed efficienza sull&#39;elaborazione delle richieste. La vetrina web Adobe Commerce è realizzata con HTML, JavaScript e il preprocessore LESS CSS.

## Server web

Adobe Commerce supporta completamente i server web Nginx e Apache. Adobe Commerce fornisce esempi di file di configurazione consigliati per entrambi:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

L&#39;esempio di Nginx contiene impostazioni per prestazioni migliori ed è progettato in modo che sia richiesta una piccola riconfigurazione.

## Servizi di caching

Adobe Commerce offre numerose opzioni per memorizzare la cache e i dati di sessione, tra cui Redis, Memcache, file system e database. Per una configurazione con più nodi web, Redis è l’opzione migliore.

Si consiglia vivamente di utilizzare Varnish come server cache a pagina intera per il tuo store. Adobe Commerce distribuisce un file di configurazione di esempio per Vernice che contiene tutte le impostazioni consigliate per le prestazioni.

## Servizi di ricerca

Per Adobe Commerce versione 2.4 e successive, tutte le installazioni devono essere configurate per utilizzare Elasticsearch o OpenSearch come soluzione di ricerca nel catalogo. Elasticsearch fornisce ricerche rapide e avanzate sui prodotti nel catalogo. L’Elasticsearch è facoltativo per le versioni precedenti alla 2.4, ma è consigliato.

## Servizi coda messaggi

Le code di messaggi forniscono un meccanismo di comunicazione asincrono in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. [!DNL RabbitMQ] è un gestore di messaggi open-source che offre un sistema di messaggistica affidabile, altamente disponibile, scalabile e portatile.

## Strumenti di sicurezza

Lo strumento di analisi della sicurezza di [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) consente di monitorare regolarmente i siti Web degli archivi e di ricevere aggiornamenti per i rischi di sicurezza noti, il malware e il software obsoleto. In genere, si inizia a utilizzare questo strumento quando si inizia il test di accettazione da parte dell’utente (UAT). Oltre allo strumento Adobe Commerce Security Scan, gratuito e disponibile per tutte le implementazioni e versioni di Adobe Commerce, è possibile utilizzare altre opzioni durante il processo CI/CD e prima di ogni versione.

SonarQube è una piattaforma di gestione della qualità open-source, progettata per analizzare e misurare la qualità tecnica del codice. SonarQube non solo fornisce un rapporto completo sui bug del codice, sugli errori di sintassi e sulle vulnerabilità, ma offre anche suggerimenti ed esempi per la correzione del codice. SonarQube è perfetto da utilizzare in un ambiente CI/CD come strumento in grado di analizzare il codice prima che venga distribuito.

Zed Attack Proxy (ZAP) è uno strumento di test di sicurezza gratuito utilizzato da migliaia di pen-tester in tutto il mondo. ZAP è sviluppato da OWASP ed è uno degli strumenti più preferiti per i test di sicurezza manuali.

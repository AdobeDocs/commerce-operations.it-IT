---
title: Requisiti di sistema
description: Scopri le dipendenze software e i requisiti di sistema per Adobe Commerce. Consulta Configurazioni testate per la compatibilità con l’ambiente di implementazione.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: fdd98cea53f1a060b8b56268250b463c74abaaa1
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Requisiti di sistema

Di seguito sono riepilogate le dipendenze software e i servizi testati per Adobe Commerce.

Esistono alcune differenze nelle dipendenze per Commerce su Cloud. Il supporto per la versione del servizio e la compatibilità per Adobe Commerce on Cloud è determinato dai servizi testati e distribuiti negli ambienti cloud ospitati e talvolta differisce dalle versioni supportate dalle distribuzioni Adobe Commerce on-premise.

>[!NOTE]
>
>Le tabelle dei requisiti di sistema identificano le specifiche versioni di Adobe Commerce coperte, comprese quelle esplicitamente etichettate come versioni beta o con accesso anticipato. Per ulteriori informazioni sulle ultime versioni pubblicate di Adobe Commerce, consulta le [note sulla versione](../release/release-notes/overview.md).
>
>Le mancate corrispondenze delle versioni del servizio relative alla versione di Commerce possono introdurre un comportamento non riproducibile negli ambienti supportati. In questi casi, il Supporto può richiedere l’allineamento dell’ambiente a una configurazione supportata (ad esempio, aggiornamento o downgrade della versione del servizio) prima che sia possibile esaminare, risolvere i problemi o convalidare il comportamento riportato. Una volta allineate le versioni, il supporto può procedere con l’indagine.

Le tabelle seguenti mostrano le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce.

Adobe supporta solo la combinazione di requisiti di sistema descritti nelle tabelle seguenti. Ad esempio, 2.4.9 è completamente testato con MariaDB 12.3. Adobe consiglia di eseguire l’aggiornamento a MariaDB 12.3 prima di eseguire l’aggiornamento a 2.4.9.

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

Il modello [Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con una versione specifica di Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Per la configurazione predefinita, i servizi e le versioni sono definiti nel [file `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Per ulteriori dettagli, consulta [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) nella guida *Commerce su infrastruttura cloud*.

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 ha raggiunto la fine del supporto (EOS) il 30 aprile 2026.**
A partire da questa data, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 non fornirà compatibilità o
supporto per qualsiasi versione di MySQL rilasciata dopo MySQL 8.0. Adobe non
convalida o fornisce supporto per le versioni principali di MySQL più recenti in questo Adobe
Riga di rilascio Commerce.
Tutti i clienti Adobe Commerce on-premise che eseguono le versioni 2.4.7, 2.4.6, 2.4.5 e 2.4.4 sono fortemente
è stato consigliato di migrare i server di database a una versione compatibile di MariaDB.

**Elasticsearch 7.17 ha raggiunto la fine del supporto (EOS) il 15 gennaio 2026.**
A partire da questa data, Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 non fornirà compatibilità o
supporto per qualsiasi versione di Elasticsearch rilasciata dopo Elasticsearch 7. Adobe non
convalida o fornisce supporto per le versioni principali di Elasticsearch più recenti su questo Adobe
Riga di rilascio Commerce.
Tutti i clienti Adobe Commerce on-premise che eseguono le versioni 2.4.6, 2.4.5 e 2.4.4 di sono
è consigliabile migrare l’infrastruttura di ricerca a una versione compatibile di OpenSearch.

>[!ENDTABS]

>[!AVAILABILITY]
>
><sup>1</sup> La compatibilità tra MariaDB 12.3 e Adobe Commerce 2.4.9 verrà confermata dopo la versione ufficiale di MariaDB 12.3, prevista nel periodo maggio-giugno.

## Impostazioni PHP

Sono disponibili impostazioni di configurazione PHP particolari, ad esempio l&#39;impostazione `memory_limit`, che consentono di evitare problemi comuni durante l&#39;utilizzo di Adobe Commerce. Vedere [Impostazioni PHP richieste](prerequisites/php-settings.md).

Per informazioni sulla configurazione cloud, consulta [Impostazioni PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) nella guida *Commerce su infrastruttura cloud*.

### PHP OPcache

Adobe consiglia di verificare che [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) sia abilitato per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP.

- **Per le distribuzioni dell&#39;infrastruttura Adobe Commerce on Cloud**, l&#39;estensione `opcache` è installata per impostazione predefinita.
- **Per le distribuzioni locali di Adobe Commerce:**
   - [Verificare che l&#39;estensione PHP OPcache sia installata](prerequisites/php-settings.md#verify-php-is-installed).
   - Per informazioni specifiche sulle impostazioni delle prestazioni, vedere le raccomandazioni software per le [impostazioni PHP](../performance/software.md#php-settings) nella *Guida alle best practice per le prestazioni*.


Se devi installare OPcache separatamente, consulta la [documentazione di PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Controllo processo PHP

{{php-process-control}}

### PHPUnit

La versione principale di PHPUnit supportata dipende dalla versione di Adobe Commerce. Adobe esegue i test 2.4.9 con PHPUnit 12, 2.4.8-p5 con PHPUnit 10 e da 2.4.7-p10 a 2.4.4-p18 con PHPUnit 9. Installa PHPUnit come strumento da riga di comando nella versione principale che corrisponde alle configurazioni testate di Adobe per la versione in uso.

### Estensioni PHP

Le [istruzioni di installazione PHP](prerequisites/php-settings.md) includono un passaggio per l&#39;installazione di queste estensioni.

>[!TIP]
>
>Per le estensioni PHP nell&#39;infrastruttura cloud, vedere [Abilitare le estensioni PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) nella _guida di Commerce su infrastruttura cloud_.

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

La tabella seguente mostra le estensioni PHP supportate durante la distribuzione di Adobe Commerce sulla piattaforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce locale]

{{$include /help/_includes/templated/php-extensions.md}}

Per informazioni dettagliate sull&#39;installazione, consultare la [documentazione ufficiale PHP](https://www.php.net/manual/en/extensions.php).

>[!ENDTABS]

## Altri requisiti software

Questa sezione descrive il supporto e la compatibilità per tutti gli altri tipi di software richiesto e opzionale.

>[!NOTE]
>
>I seguenti requisiti si applicano alla versione più recente della patch 2.4.x di Adobe Commerce. Se pertinente, vengono fornite indicazioni sull’infrastruttura Commerce on Cloud.

### Browser

Storefront e amministratore:

- Microsoft Edge (versione principale più recente e precedente)
- Firefox (versione principale più recente e precedente su qualsiasi sistema operativo)
- Chrome (versione principale più recente e precedente su qualsiasi sistema operativo)
- Safari (versione principale più recente e precedente solo su macOS)
- Safari per iOS (versione principale più recente e precedente per la vetrina)
- Chrome per Android (versione principale più recente e precedente per la vetrina)

### Server di posta

Mail Transfer Agent (MTA) o un server SMTP. L&#39;infrastruttura Commerce on Cloud utilizza il servizio e-mail [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memoria

L’aggiornamento delle applicazioni e delle estensioni ottenute da Commerce Marketplace e da altre origini può richiedere fino a 2 GB di RAM. Se si utilizza un sistema con meno di 2 GB di RAM, creare un [file di scambio](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). In caso contrario, l’aggiornamento potrebbe non riuscire.

### Sistemi operativi (Linux x86-64)

Distribuzioni Linux, come Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e simili.

Microsoft Windows e macOS sono **non** supportati.

Per alcune operazioni Adobe Commerce richiede i seguenti strumenti di sistema:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Per HTTPS è necessario un certificato di sicurezza valido.
- I certificati SSL autofirmati non sono supportati.
- Requisito Transport Layer Security (TLS): PayPal e `repo.magento.com` richiedono entrambi TLS 1.2 o versione successiva.

Per l&#39;infrastruttura Commerce on Cloud, consulta [Configurazione rapida](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) nella guida *Commerce on Cloud Infrastructure*.

### Xdebug

Per Adobe Commerce, utilizza [php_xdebug 2.5.x](https://xdebug.org/download) o versione successiva (solo per ambienti di sviluppo; può avere un effetto negativo sulle prestazioni).

Per Adobe Commerce on Cloud, consulta [Configurare Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) nella guida *Commerce on Cloud Infrastructure*.

>[!NOTE]
>
>Si è verificato un problema noto con `xdebug` che può influire sulle installazioni di Adobe Commerce o sull&#39;accesso alla vetrina o all&#39;amministratore dopo l&#39;installazione. Vedere [Problema noto che riguarda l&#39;installazione di `xdebug`](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) nella _Knowledge Base del supporto Commerce_.

<!-- Last updated from includes: 2026-05-11 20:38:54 -->

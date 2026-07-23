---
title: Requisiti di sistema
description: Scopri le dipendenze software e i requisiti di sistema per Adobe Commerce. Consulta Configurazioni testate per la compatibilità con l’ambiente di implementazione.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: cba883644156d5eef54796003f46e4bc6cd08d5d
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# Requisiti di sistema

Le informazioni seguenti riepilogano le dipendenze software e i servizi testati per Adobe Commerce.

Esistono alcune differenze nelle dipendenze per Commerce su Cloud. Il supporto per la versione del servizio e la compatibilità per Adobe Commerce on Cloud è determinato dai servizi testati e distribuiti negli ambienti cloud ospitati e talvolta differisce dalle versioni supportate dalle distribuzioni Adobe Commerce on-premise.

>[!IMPORTANT]
>
>Le tabelle dei requisiti di sistema elencano le versioni di Adobe Commerce a cui si applicano, incluse le versioni etichettate come beta o accesso anticipato.
>Consulta le [note sulla versione](../release/release-notes/overview.md) per le ultime versioni pubblicate di Commerce.
>
>Quando le versioni del servizio non corrispondono alla configurazione supportata per la versione di Commerce, il comportamento potrebbe essere diverso da quello che Adobe può riprodurre nei test. Il Supporto Adobe può richiedere di allineare l’ambiente con una configurazione supportata prima di eseguire indagini, risolvere problemi o convalidare il comportamento riportato. Dopo aver allineato l’ambiente, il supporto Adobe può continuare l’indagine.

Le tabelle seguenti mostrano le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce.

Adobe supporta solo le combinazioni di requisiti di sistema elencate nelle tabelle seguenti. Adobe non convalida o supporta configurazioni che non corrispondono a una combinazione elencata. Ad esempio, Adobe Commerce 2.4.9 viene testato con MariaDB 12.3. Esegui l’aggiornamento a MariaDB 12.3 prima di passare alla versione 2.4.9.

## Requisiti di sistema per le versioni più recenti di Commerce

Nelle tabelle seguenti sono riepilogati i requisiti di sistema per l’ultima versione di tutte le versioni di Commerce supportate. Adobe consiglia a tutti i clienti di eseguire l’aggiornamento a queste versioni.

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

Il modello [Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con la versione più recente di Commerce per ogni riga di rilascio.

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

I clienti di Adobe Commerce on Cloud devono mantenere le dipendenze della piattaforma dalle versioni supportate. Vedi [Dipendenze piattaforma](../release/lifecycle-policy.md#platform-dependencies) nel criterio del ciclo di vita.

**Elasticsearch 7.17 ha raggiunto la fine del supporto (EOS) il 15 gennaio 2026.**
A partire da questa data, Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 non fornirà compatibilità o
supporto per qualsiasi versione di Elasticsearch rilasciata dopo Elasticsearch 7. Adobe non
convalida o fornisce supporto per le versioni principali di Elasticsearch più recenti su questo Adobe
Riga di rilascio Commerce.
Tutti i clienti Adobe Commerce on-premise che eseguono le versioni 2.4.6, 2.4.5 e 2.4.4 di sono
è consigliabile migrare l’infrastruttura di ricerca a una versione compatibile di OpenSearch.

>[!ENDTABS]

## Requisiti di sistema per le versioni precedenti di Commerce

Nelle tabelle seguenti sono elencati i requisiti di sistema per le versioni di Adobe Commerce, incluse quelle incluse nel supporto esteso. Queste tabelle sono fornite a scopo puramente indicativo. Adobe consiglia di non utilizzare versioni non supportate delle dipendenze software. Per poter esaminare, risolvere i problemi o convalidare il comportamento segnalato, è necessario che l’ambiente sia allineato a una configurazione supportata.

>[!NOTE]
>
>Adobe Commerce 2.4.6 si trova in [supporto esteso](../release/lifecycle-policy.md#extended-support) fino al **30 agosto 2027**, seguito da un [periodo transitorio di sola sicurezza](../release/lifecycle-policy.md#security-only-transitional-period) fino al **31 maggio 2028**. Queste disposizioni sono disponibili solo per i clienti Adobe Commerce. Non estendono il supporto per dipendenze di terze parti come MySQL.
>
>Se esegui Adobe Commerce su Cloud, devi eseguire l&#39;aggiornamento a una versione supportata o eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service] prima del **1 giugno 2028** [data di applicazione dell&#39;aggiornamento della versione](../release/version-upgrade-enforcement-policy.md). Per informazioni sulle date dell&#39;intero ciclo di vita, vedere la tabella [date di fine del supporto](../release/lifecycle-policy.md#end-of-support-dates).
>
>La tabella viene compressa per ridurre al minimo la lunghezza dell&#39;articolo. Seleziona l’intestazione per espanderla.

+++Requisiti per le versioni precedenti

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

Il modello [Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con una versione specifica di Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Per la configurazione predefinita, i servizi e le versioni sono definiti nel [file `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Per ulteriori dettagli, consulta [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) nella guida *Commerce su infrastruttura cloud*.

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 ha raggiunto la fine del supporto (EOS) il 30 aprile 2026.**
A partire da questa data, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 non fornirà compatibilità o
supporto per qualsiasi versione di MySQL rilasciata dopo MySQL 8.0. Adobe non
convalida o fornisce supporto per le versioni principali di MySQL più recenti in questo Adobe
Riga di rilascio Commerce.
Tutti i clienti Adobe Commerce on-premise che eseguono le versioni 2.4.7, 2.4.6, 2.4.5 e 2.4.4 sono fortemente
è stato consigliato di migrare i server di database a una versione compatibile di MariaDB.

I clienti di Adobe Commerce on Cloud devono mantenere le dipendenze della piattaforma dalle versioni supportate. Vedi [Dipendenze piattaforma](../release/lifecycle-policy.md#platform-dependencies) nel criterio del ciclo di vita.

**Elasticsearch 7.17 ha raggiunto la fine del supporto (EOS) il 15 gennaio 2026.**
A partire da questa data, Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 non fornirà compatibilità o
supporto per qualsiasi versione di Elasticsearch rilasciata dopo Elasticsearch 7. Adobe non
convalida o fornisce supporto per le versioni principali di Elasticsearch più recenti su questo Adobe
Riga di rilascio Commerce.
Tutti i clienti Adobe Commerce on-premise che eseguono le versioni 2.4.6, 2.4.5 e 2.4.4 di sono
è consigliabile migrare l’infrastruttura di ricerca a una versione compatibile di OpenSearch.

>[!ENDTABS]

+++

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

<!-- Last updated from includes: 2026-07-22 16:57:39 -->

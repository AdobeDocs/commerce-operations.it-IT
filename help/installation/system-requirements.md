---
title: Requisiti di sistema
description: Scopri le dipendenze software e i requisiti di sistema per Adobe Commerce. Scopri le configurazioni testate per garantire la compatibilità con il tuo ambiente di implementazione.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 96cdbae2fd6754e88e7e781b972f72ca6593d505
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Requisiti di sistema

Di seguito sono riepilogate le dipendenze software e i servizi testati per Adobe Commerce.

Esistono alcune differenze nelle dipendenze per Commerce su Cloud. Il supporto per la versione del servizio e la compatibilità per Adobe Commerce on Cloud è determinato dai servizi testati e distribuiti negli ambienti cloud ospitati e talvolta differisce dalle versioni supportate dalle distribuzioni Adobe Commerce on-premise. Ad esempio, Elasticsearch 7.17 è supportato per Commerce 2.4.4 per le distribuzioni on-premise, ma OpenSearch 1 è supportato per Adobe Commerce 2.4.4 su Cloud.

>[!NOTE]
>
>I requisiti di sistema si applicano solo alle versioni rilasciate di Adobe Commerce. Beta o le versioni ad accesso anticipato non sono incluse. Per ulteriori informazioni sulle ultime versioni rilasciate di Adobe Commerce, consulta le [note sulla versione](../release/release-notes/overview.md).

Le tabelle seguenti mostrano le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce.

Adobe supporta solo la combinazione di requisiti di sistema descritti nelle tabelle seguenti. Ad esempio, 2.4.5 è completamente testato con MariaDB 10.4. Adobe consiglia di eseguire l’aggiornamento a MariaDB 10.4 prima di passare alla versione 2.4.5.

Per garantire un processo di aggiornamento fluido ed evitare errori di distribuzione, Adobe consiglia di aggiornare le versioni di RabbitMQ in modo incrementale. Ad esempio, per l’aggiornamento dalla versione 3.8 alla versione 4.1, devi prima eseguire l’aggiornamento da 3.8 a 3.9, quindi da 3.9 a 3.10 e così via. Solo dopo aver raggiunto la versione 3.13 dovresti procedere con l’aggiornamento alla versione 4.1.

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

Il modello [Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con una versione specifica di Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

I servizi e le versioni sono definiti nel [file `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Di seguito è riportata la configurazione predefinita del servizio per Commerce 2.4.6 su infrastruttura Cloud:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Consulta [Configurare i servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) nella guida _Commerce su infrastruttura cloud_.

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Impostazioni PHP

Sono disponibili impostazioni di configurazione PHP particolari, ad esempio l&#39;impostazione `memory_limit`, che consentono di evitare problemi comuni durante l&#39;utilizzo di Adobe Commerce. Vedere [Impostazioni PHP richieste](prerequisites/php-settings.md).

Per informazioni sulla configurazione cloud, consulta [Impostazioni PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) nella guida _Commerce su infrastruttura cloud_.

### PHP OPcache

È consigliabile verificare che [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) sia abilitato per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP. L&#39;estensione `opcache` è installata per impostazione predefinita nell&#39;infrastruttura Commerce on Cloud.

Per le impostazioni locali, verificare che PHP OPcache sia installato. Vedere [Impostazioni PHP](prerequisites/php-settings.md). Oppure per indicazioni specifiche sulle impostazioni delle prestazioni, vedere le raccomandazioni software per le [impostazioni PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) nella _Guida alle best practice per le prestazioni_.

Se devi installare OPcache separatamente, consulta la [documentazione di PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Controllo processo PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (come strumento da riga di comando).

### Estensioni PHP

Le [istruzioni di installazione PHP](prerequisites/php-settings.md) includono un passaggio per l&#39;installazione di queste estensioni.

>[!TIP]
>
>Per le estensioni PHP nell&#39;infrastruttura cloud, vedere [Abilitare le estensioni PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) nella _guida di Commerce su infrastruttura cloud_.

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

La tabella seguente mostra le estensioni PHP supportate durante la distribuzione di Adobe Commerce sulla piattaforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce locale]

{{$include /help/_includes/templated/php-extensions.md}}

Per informazioni dettagliate sull&#39;installazione, consultare la [documentazione ufficiale PHP](https://www.php.net/manual/en/extensions.php).

>[!ENDTABS]

## Varie

Questa sezione descrive il supporto e la compatibilità per tutti gli altri tipi di software richiesto e opzionale.

>[!NOTE]
>
>I seguenti requisiti si applicano alla versione più recente della patch 2.4.x di Adobe Commerce. Se pertinente, vengono fornite indicazioni sull’infrastruttura Commerce on Cloud.

### Browser

Storefront e amministratore:

- Microsoft Edge (versione principale più recente e precedente)
- Firefox (versione principale più recente e precedente; qualsiasi sistema operativo)
- Chrome (versione principale più recente e precedente; qualsiasi sistema operativo)
- Safari (versione principale più recente e precedente; solo macOS)
- Safari per iOS (versione principale più recente e precedente, per storefront)
- Chrome per Android (versione principale più recente e precedente, per storefront)

### Server di posta

Mail Transfer Agent (MTA) o un server SMTP. L&#39;infrastruttura Commerce on Cloud utilizza il servizio e-mail [SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Memoria

L’aggiornamento delle applicazioni e delle estensioni ottenute da Commerce Marketplace e da altre origini può richiedere fino a 2 GB di RAM. Se si utilizza un sistema con meno di 2 GB di RAM, creare un [file di scambio](https://support.magento.com/hc/en-us/articles/360032980432). In caso contrario, l&#39;aggiornamento potrebbe non riuscire.

### Sistemi operativi (Linux x86-64)

Distribuzioni Linux, come RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e simili.

Microsoft Windows e macOS sono **non** supportati.

Per alcune operazioni Adobe Commerce richiede i seguenti strumenti di sistema:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Per HTTPS è necessario un certificato di sicurezza valido.
- I certificati SSL autofirmati non sono supportati.
- Requisito Transport Layer Security (TLS): PayPal e `repo.magento.com` richiedono entrambi TLS 1.2 o versione successiva.

Per l&#39;infrastruttura Commerce on Cloud, consulta [Configurazione rapida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nella guida _Commerce on Cloud Infrastructure_.

### Xdebug

Per Adobe Commerce, utilizza [php_xdebug 2.5.x](https://xdebug.org/download) o versione successiva (solo per ambienti di sviluppo; può avere un effetto negativo sulle prestazioni).

Per Adobe Commerce on Cloud, consulta [Configurare Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) nella guida _Commerce on Cloud Infrastructure_.

>[!NOTE]
>
>Si è verificato un problema noto con `xdebug` che può influire sulle installazioni di Adobe Commerce o sull&#39;accesso alla vetrina o all&#39;amministratore dopo l&#39;installazione. Vedere [Problema noto che riguarda l&#39;installazione di `xdebug`](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) nella _Knowledge Base del supporto Commerce_.


<!-- Last updated from includes: 2026-01-15 16:27:25 -->

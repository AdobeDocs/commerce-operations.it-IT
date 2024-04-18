---
title: Requisiti di sistema
description: Utilizza questo riferimento per identificare le dipendenze software richieste testate con le versioni di Adobe Commerce.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Requisiti di sistema

Di seguito sono riepilogate le dipendenze software e i servizi testati per Adobe Commerce.

Esistono alcune differenze nelle dipendenze di Commerce dall’infrastruttura Cloud. Il supporto per la versione del servizio e la compatibilità per l’infrastruttura cloud di Adobe Commerce è determinato dai servizi testati e distribuiti negli ambienti cloud ospitati e talvolta differisce dalle versioni supportate dalle distribuzioni Adobe Commerce on-premise. Ad esempio, l’Elasticsearch 7.17 è supportato per Commerce 2.4.4 per le distribuzioni on-premise, mentre OpenSearch 1.2 è supportato per Commerce 2.4.4 sull’infrastruttura cloud.

Le tabelle seguenti mostrano le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce.

Adobe supporta solo la combinazione di requisiti di sistema descritti nelle tabelle seguenti. Ad esempio, 2.4.5 è completamente testato con MariaDB 10.4. L’Adobe consiglia di eseguire l’aggiornamento a MariaDB 10.4 prima di eseguire l’aggiornamento a 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce su Cloud]

Il [Modello Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con una versione di Commerce specifica.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

I servizi e le versioni sono definiti in [il `services.yaml` file](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Di seguito è riportata la configurazione predefinita del servizio per Commerce 2.4.6 su infrastruttura Cloud:

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

Consulta [Configurare i servizi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) nel _Commerce su infrastruttura cloud_ guida.

>[!TAB Commerce on-premise]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Impostazioni PHP

Esistono impostazioni di configurazione PHP particolari, come `memory_limit` che può aiutarti a evitare problemi comuni quando utilizzi Adobe Commerce. Consulta [Impostazioni PHP richieste](prerequisites/php-settings.md).

Per istruzioni sulla configurazione del cloud, consulta [Impostazioni PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) nel _Commerce su infrastruttura cloud_ guida.

### PHP OPcache

È consigliabile verificare che [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) è abilitato per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP. Il `opcache` L’estensione è installata per impostazione predefinita nell’infrastruttura Commerce on Cloud.

Per gli on-premise, verificare che PHP OPcache sia installato, vedere [Impostazioni PHP](prerequisites/php-settings.md). Oppure, per indicazioni specifiche sulle impostazioni delle prestazioni, vedere le raccomandazioni software per [Impostazioni PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) nel _Best practice per le prestazioni_ guida.

Se è necessario installare OPcache separatamente, vedere [Documentazione di PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Controllo processo PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (come strumento da riga di comando).

### Estensioni PHP

Il [Istruzioni di installazione PHP](prerequisites/php-settings.md) includi un passaggio per installare queste estensioni.

>[!TIP]
>
>Per le estensioni PHP nell’infrastruttura Cloud, consulta [Abilitare le estensioni PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) nel _Commerce su infrastruttura cloud_ guida.

>[!BEGINTABS]

>[!TAB Commerce su Cloud]

La tabella seguente mostra le estensioni PHP supportate durante la distribuzione di Adobe Commerce sulla piattaforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce on-premise]

{{$include /help/_includes/templated/php-extensions.md}}

Fai riferimento a [documentazione ufficiale PHP](https://www.php.net/manual/en/extensions.php) per informazioni dettagliate sull&#39;installazione.

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
- Chrome per Android (versione principale più recente e precedente, per vetrina)

### Server di posta

Mail Transfer Agent (MTA) o un server SMTP. L’infrastruttura Commerce on Cloud utilizza [Servizio e-mail SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Memoria

L&#39;aggiornamento delle applicazioni e delle estensioni ottenute dalla Commerce Marketplace e da altre origini può richiedere fino a 2 GB di RAM. Se si utilizza un sistema con meno di 2 GB di RAM, creare un [file di scambio](https://support.magento.com/hc/en-us/articles/360032980432); in caso contrario, l’aggiornamento potrebbe non riuscire.

### Sistemi operativi (Linux x86-64)

Distribuzioni Linux, come RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e simili. Microsoft Windows e macOS non sono supportati.

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
- Requisito Transport Layer Security (TLS) - PayPal e `repo.magento.com` entrambi richiedono TLS 1.2 o versione successiva.

Per l’infrastruttura Commerce on Cloud, consulta [Configurazione rapida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) nel _Commerce su infrastruttura cloud_ guida.

### Xdebug

Per Adobe Commerce, utilizza [php_xdebug 2.5.x](https://xdebug.org/download) o versione successiva (solo per ambienti di sviluppo; può avere un effetto negativo sulle prestazioni).

Per Adobe Commerce su Cloud, consulta [Configura Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) nel _Commerce su infrastruttura cloud_ guida.

>[!NOTE]
>
>Si è verificato un problema noto con `xdebug` che possono influenzare le installazioni di Adobe Commerce o l’accesso alla vetrina o all’amministratore dopo l’installazione. Consulta [Problema noto che influisce `xdebug` installazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) nel _Knowledge Base del supporto Commerce_.

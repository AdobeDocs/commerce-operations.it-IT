---
title: Requisiti di sistema
description: Scopri le dipendenze software e i requisiti di sistema per Adobe Commerce. Consulta Configurazioni testate per la compatibilità con l’ambiente di implementazione.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-09-18
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# Requisiti di sistema

Le informazioni seguenti riepilogano le dipendenze software e i servizi testati per Adobe Commerce.

Le dipendenze software per l’infrastruttura Adobe Commerce su Cloud sono diverse da quelle per le distribuzioni locali. Adobe determina le versioni e la compatibilità dei servizi supportati in base ai servizi testati e distribuiti in ambienti cloud in hosting. Queste versioni a volte differiscono da quelle supportate per le distribuzioni on-premise.

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

Il file [`services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) definisce i servizi e le versioni predefiniti.
Consulta [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) nella guida *Commerce su infrastruttura cloud*.

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 ha raggiunto la fine del supporto (EOS) il 30 aprile 2026.**
Dopo questa data, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 non forniscono compatibilità o supporto per le versioni MySQL rilasciate dopo MySQL 8.0.
Adobe non convalida o supporta le versioni principali di MySQL più recenti per queste versioni di Commerce.
Se esegui Adobe Commerce on-premise versioni 2.4.7, 2.4.6, 2.4.5 o 2.4.4, Adobe consiglia vivamente di migrare i server di database a una versione MariaDB compatibile.

I clienti di Adobe Commerce on Cloud devono mantenere le dipendenze della piattaforma dalle versioni supportate. Vedi [Dipendenze piattaforma](../release/lifecycle-policy.md#platform-dependencies) nel criterio del ciclo di vita.

**Elasticsearch 7.17 ha raggiunto la fine del supporto (EOS) il 15 gennaio 2026.**
Dopo questa data, Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 non forniscono compatibilità o supporto per le versioni di Elasticsearch rilasciate dopo Elasticsearch 7.
Adobe non convalida o supporta le versioni principali più recenti di Elasticsearch per queste versioni di Commerce.
Se esegui Adobe Commerce on-premise versioni 2.4.6, 2.4.5 o 2.4.4, Adobe consiglia vivamente di migrare l’infrastruttura di ricerca a una versione compatibile di OpenSearch.

>[!ENDTABS]

## Requisiti di sistema per la versione 2.4.10-alpha Commerce

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## Requisiti di sistema per le versioni precedenti di Commerce

Nelle tabelle seguenti sono elencati i requisiti di sistema per le versioni di Adobe Commerce, inclusi quelli relativi al supporto esteso. Utilizzare queste tabelle solo come riferimento. Adobe sconsiglia di utilizzare versioni non supportate delle dipendenze software. Prima che il supporto Adobe indaghi, risolva i problemi o convalidi il comportamento segnalato, devi allineare il tuo ambiente con una configurazione supportata.

>[!NOTE]
>
>Adobe Commerce 2.4.6 si trova in [supporto esteso](../release/lifecycle-policy.md#extended-support) fino al **30 agosto 2027**, seguito da un [periodo transitorio di sola sicurezza](../release/lifecycle-policy.md#security-only-transitional-period) fino al **31 maggio 2028**. Queste disposizioni sono disponibili solo per i clienti Adobe Commerce. Non estendono il supporto per dipendenze di terze parti come MySQL.
>
>Se esegui Adobe Commerce su Cloud, devi eseguire l&#39;aggiornamento a una versione supportata o eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service] prima del **1 giugno 2028** [requisiti e scadenze di sicurezza](../release/security-enforcement-policy.md). Per informazioni sulle date dell&#39;intero ciclo di vita, vedere la tabella [date di fine del supporto](../release/lifecycle-policy.md#end-of-support-dates).
>
>La tabella viene compressa per ridurre al minimo la lunghezza dell&#39;articolo. Seleziona l’intestazione per espanderla.

+++Requisiti per le versioni precedenti

>[!BEGINTABS]

>[!TAB Commerce sul cloud]

Il modello [Commerce on Cloud](https://github.com/magento/magento-cloud) fornisce una configurazione predefinita per i servizi compatibili con una versione specifica di Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Il file [`services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) definisce i servizi e le versioni predefiniti.
Consulta [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) nella guida *Commerce su infrastruttura cloud*.

>[!TAB Commerce locale]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 ha raggiunto la fine del supporto (EOS) il 30 aprile 2026.**
Dopo questa data, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 e 2.4.4 non forniscono compatibilità o supporto per le versioni MySQL rilasciate dopo MySQL 8.0.
Adobe non convalida o supporta le versioni principali di MySQL più recenti per queste versioni di Commerce.
Se esegui Adobe Commerce on-premise versioni 2.4.7, 2.4.6, 2.4.5 o 2.4.4, Adobe consiglia vivamente di migrare i server di database a una versione MariaDB compatibile.

I clienti di Adobe Commerce on Cloud devono mantenere le dipendenze della piattaforma dalle versioni supportate. Vedi [Dipendenze piattaforma](../release/lifecycle-policy.md#platform-dependencies) nel criterio del ciclo di vita.

**Elasticsearch 7.17 ha raggiunto la fine del supporto (EOS) il 15 gennaio 2026.**
Dopo questa data, Adobe Commerce 2.4.6, 2.4.5 e 2.4.4 non forniscono compatibilità o supporto per le versioni di Elasticsearch rilasciate dopo Elasticsearch 7.
Adobe non convalida o supporta le versioni principali più recenti di Elasticsearch per queste versioni di Commerce.
Se esegui Adobe Commerce on-premise versioni 2.4.6, 2.4.5 o 2.4.4, Adobe consiglia vivamente di migrare l’infrastruttura di ricerca a una versione compatibile di OpenSearch.

>[!ENDTABS]

+++

## Impostazioni PHP

Configurare le impostazioni PHP, ad esempio `memory_limit`, per evitare problemi comuni quando si utilizza Adobe Commerce. Vedere [Impostazioni PHP richieste](prerequisites/php-settings.md).

Per informazioni sulla configurazione cloud, consulta [Impostazioni PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) nella guida *Commerce su infrastruttura cloud*.

### PHP OPcache

Adobe consiglia di verificare che [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) sia abilitato per migliorare le prestazioni. Molte distribuzioni PHP abilitano OPcache.

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

Per informazioni dettagliate sull&#39;installazione, vedere la [documentazione ufficiale PHP](https://www.php.net/manual/en/extensions.php).

>[!ENDTABS]

## Altri requisiti software

Questa sezione descrive il supporto e la compatibilità per tutti gli altri tipi di software richiesto e opzionale.

>[!NOTE]
>
>I seguenti requisiti si applicano alla versione più recente della patch 2.4.x di Adobe Commerce. Se pertinente, vengono fornite indicazioni sull’infrastruttura Commerce on Cloud.

### Browser

Adobe Commerce supporta le versioni principali più recenti e precedenti dei seguenti browser per la vetrina e l’amministratore, tranne dove indicato:

- Microsoft Edge
- Firefox (qualsiasi sistema operativo)
- Chrome (qualsiasi sistema operativo)
- Safari (solo macOS)
- Safari per iOS (solo vetrina)
- Chrome per Android (solo vetrina)

### Server di posta

Mail Transfer Agent (MTA) o un server SMTP. L&#39;infrastruttura Commerce on Cloud utilizza il servizio e-mail [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memoria

L&#39;aggiornamento di applicazioni ed estensioni da Commerce Marketplace e da altre origini può richiedere fino a 2 GB di RAM. Se il sistema dispone di meno di 2 GB di RAM, creare un [file di scambio](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Senza un file di scambio, l’aggiornamento potrebbe non riuscire.

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

Solo per gli ambienti di sviluppo Adobe Commerce, utilizza [php_xdebug 2.5.x](https://xdebug.org/download) o versione successiva. Xdebug può influire negativamente sulle prestazioni.

Per Adobe Commerce on Cloud, consulta [Configurare Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) nella guida *Commerce on Cloud Infrastructure*.

>[!NOTE]
>
>Un problema noto con Xdebug può influire sulle installazioni di Adobe Commerce o sull’accesso alla vetrina o all’amministratore dopo l’installazione. Vedere [Problema noto che riguarda l&#39;installazione di `xdebug`](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) nella _Knowledge Base del supporto Commerce_.

<!-- Last updated from includes: 2026-10-07 13:03:29 -->

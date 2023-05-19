---
title: Requisiti di sistema
description: Utilizza questo riferimento per identificare le dipendenze software richieste che sono state testate con Adobe Commerce e le versioni di Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Requisiti di sistema

Questa tabella mostra le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce e Magenti Open Source. Adobe supporta solo la combinazione di requisiti di sistema descritti nella tabella seguente.

Ad esempio, 2.4.5 è completamente testato con MariaDB 10.4. L’Adobe consiglia di eseguire l’aggiornamento a MariaDB 10.4 prima di eseguire l’aggiornamento a 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Varie

Questa sezione descrive il supporto e la compatibilità per tutti gli altri tipi di software richiesto e opzionale.

>[!NOTE]
>
>I seguenti requisiti si applicano alla versione più recente della patch 2.4.x di Adobe Commerce e Magenti Open Source.

### Server di posta

Mail Transfer Agent (MTA) o un server SMTP

### Sistemi operativi (Linux x86-64)

Distribuzioni Linux, come RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e simili. Microsoft Windows e macOS non sono supportati.

### Estensioni PHP

>[!NOTE]
>
>Il [Istruzioni di installazione PHP](prerequisites/php-settings.md) includi un passaggio per installare queste estensioni.

{{$include /help/_includes/templated/php-extensions.md}}

Fai riferimento a [documentazione ufficiale PHP](https://php.net/manual/en/extensions.php) per informazioni dettagliate sull&#39;installazione.

### PHP OPcache

È consigliabile verificare che [PHP OPcache](https://php.net/manual/en/intro.opcache.php) è abilitato per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP. Per verificare se è installato, consulta la [Documentazione PHP](prerequisites/php-settings.md).

Se è necessario installarlo separatamente, vedere [Documentazione di PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### Impostazioni PHP

Si consiglia di impostare particolari impostazioni di configurazione PHP, ad esempio `memory_limit`, che può evitare problemi comuni quando si utilizzano Adobe Commerce e Magenti Open Source.

Per ulteriori informazioni, consulta [Impostazioni PHP richieste](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (come strumento da riga di comando) 9.0.0

### RAM

L&#39;aggiornamento delle applicazioni e delle estensioni ottenute dalla Commerce Marketplace e da altre origini può richiedere fino a 2 GB di RAM. Se si utilizza un sistema con meno di 2 GB di RAM, si consiglia di creare un [file di scambio](https://support.magento.com/hc/en-us/articles/360032980432); in caso contrario, l’aggiornamento potrebbe non riuscire.

### Dipendenze di sistema

Per alcune operazioni, Adobe Commerce e Magenti Open Source richiedono i seguenti strumenti di sistema:

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

### Browser supportati

Storefront e amministratore:

- Microsoft Edge (versione principale più recente e precedente)
- Firefox (versione principale più recente e precedente; qualsiasi sistema operativo)
- Chrome (versione principale più recente e precedente; qualsiasi sistema operativo)
- Safari (versione principale più recente e precedente; solo macOS)
- Safari Mobile per iPad 2, iPad Mini, iPad con Retina Display (iOS 12 o versione successiva), per desktop storefront
- Safari Mobile per iPhone 6 o versione successiva; iOS 12 o versione successiva, per mobile storefront
- Chrome per dispositivi mobili (versione principale più recente e precedente) [Android 4 o versione successiva] per vetrina mobile)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) o versione successiva (solo per ambienti di sviluppo; può avere un effetto negativo sulle prestazioni)

>[!NOTE]
>
>Si è verificato un problema noto con `xdebug` che possono influenzare le installazioni di Adobe Commerce o di Magento Open Source o l’accesso alla vetrina o all’amministratore dopo l’installazione. Per ulteriori informazioni, consulta [Problema noto con xdebug](https://support.magento.com/hc/en-us/articles/360034242212).

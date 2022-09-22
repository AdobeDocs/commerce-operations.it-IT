---
title: Requisiti di sistema
description: Utilizza questo riferimento per identificare le dipendenze software richieste che sono state testate con Adobe Commerce e le versioni di Magento Open Source.
source-git-commit: 3ba17b62f595e5a02ca56753d81d67166ddbc413
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Requisiti di sistema

Questa tabella mostra le versioni delle dipendenze software di terze parti testate da Adobe con specifiche versioni di Adobe Commerce e Magento Open Source. L&#39;Adobe supporta solo la combinazione dei requisiti di sistema descritti nella tabella seguente.

Ad esempio, 2.4.3 è completamente testato con MariaDB 10.4. L&#39;Adobe consiglia di eseguire l&#39;aggiornamento a MariaDB 10.4 prima di eseguire l&#39;aggiornamento a 2.4.3.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Varie

Questa sezione descrive il supporto e la compatibilità per tutti gli altri tipi di software richiesti e opzionali.

>[!NOTE]
>
>I seguenti requisiti si applicano all’ultima versione delle patch 2.4.x di Adobe Commerce e Magenti Open Source.

### Server di posta

Agente di trasferimento della posta (MTA) o server SMTP

### Sistemi operativi (Linux x86-64)

Distribuzione Linux, come RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian e simili. Microsoft Windows e macOS non sono supportati.

### Estensioni PHP

>[!NOTE]
>
>La [Istruzioni per l&#39;installazione di PHP](prerequisites/php-settings.md) includi un passaggio per l’installazione di queste estensioni.

{{$include /help/_includes/php-extensions.md}}

Fai riferimento a [documentazione ufficiale PHP](https://php.net/manual/en/extensions.php) per informazioni sull&#39;installazione.

### PHP OPcache

Si consiglia vivamente di verificare [PHP OPcache](https://php.net/manual/en/intro.opcache.php) è abilitato per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP. Per verificare se è installato, consulta la nostra [Documentazione PHP](prerequisites/php-settings.md).

Se è necessario installarlo separatamente, consulta la [Documentazione PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### Impostazioni PHP

Si consiglia di configurare le impostazioni PHP in modo particolare, ad esempio `memory_limit`, che può evitare problemi comuni quando si utilizzano Adobe Commerce e Magenti Open Source.

Per ulteriori informazioni, consulta [Impostazioni PHP richieste](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (come strumento a riga di comando) 9.0.0

### RAM

L&#39;aggiornamento delle applicazioni e delle estensioni ottenute dalla Commerce Marketplace e da altre sorgenti può richiedere fino a 2 GB di RAM. Se utilizzi un sistema con meno di 2 GB di RAM, ti consigliamo di creare un [file di swap](https://support.magento.com/hc/en-us/articles/360032980432); in caso contrario, l&#39;aggiornamento potrebbe non riuscire.

### Dipendenze del sistema

Adobe Commerce e Magenti Open Source richiedono i seguenti strumenti di sistema per alcune operazioni:

- [colpo](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [carino](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [usato](https://www.gnu.org/software/sed/manual/sed.html)
- [catrame](https://linux.die.net/man/1/tar)

### SSL

- Una valida [certificato di sicurezza](https://glossary.magento.com/security-certificate) è richiesto per HTTPS.
- I certificati SSL autofirmati non sono supportati.
- Requisito Transport Layer Security (TLS) - PayPal e `repo.magento.com` entrambi richiedono TLS 1.2 o versione successiva.

### Browser supportati

Storefront e Admin:

- Microsoft Edge (versione principale più recente e precedente)
- Firefox (versione principale più recente e precedente; qualsiasi sistema operativo)
- Chrome (versione principale più recente e precedente; qualsiasi sistema operativo)
- Safari (versione principale più recente e precedente; Solo macOS)
- Safari Mobile per iPad 2, iPad Mini, iPad con display Retina (iOS 12 o versioni successive), per la vetrina desktop
- Safari Mobile per iPhone 6 o versione successiva; iOS 12 o versioni successive, per storefront mobile
- Chrome per dispositivi mobili (versione principale più recente e precedente) [Android 4 o successivo] per vetrina mobile)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) o versioni successive (solo ambienti di sviluppo; può avere un effetto negativo sulle prestazioni)

>[!NOTE]
>
>Esiste un problema noto con `xdebug` che possono influenzare le installazioni di Adobe Commerce o Magento Open Source o l&#39;accesso alla vetrina o all&#39;amministratore dopo l&#39;installazione. Per maggiori dettagli, vedi [Problema noto con xdebug](https://support.magento.com/hc/en-us/articles/360034242212).

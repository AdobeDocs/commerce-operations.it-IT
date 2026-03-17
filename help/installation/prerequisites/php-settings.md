---
title: Impostazioni PHP
description: Segui questi passaggi per installare le estensioni PHP richieste e configurare le impostazioni PHP richieste per le installazioni locali di Adobe Commerce.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 766226dc998aafe54bc84d77cabee6fb0a969e6c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%

---


# Impostazioni PHP

Questo argomento illustra come impostare le opzioni PHP richieste.

>[!NOTE]
>
>Le versioni PHP supportate variano a seconda della versione di Adobe Commerce. Consulta [requisiti di sistema](../system-requirements.md) per le versioni PHP supportate dalla versione che stai installando.

Per informazioni sulla configurazione cloud, consulta [Impostazioni PHP](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/app/php-settings) nella guida _Commerce su infrastruttura cloud_.

## Controllo processo PHP

{{php-process-control}}

## Verificare che PHP sia installato

PHP è installato per impostazione predefinita sulla maggior parte delle distribuzioni Linux. In questo argomento si presuppone che sia già stato installato PHP. Per verificare se PHP è installato, immetti quanto segue sulla riga di comando:

```bash
php -v
```

Se PHP è installato, viene visualizzato un messaggio simile al seguente:

```
PHP <supported-version> (cli) (built: <build-date>) (NTS)
Copyright (c) The PHP Group
Zend Engine v<matching-version>, Copyright (c) Zend Technologies
    with Zend OPcache v<matching-version>, Copyright (c), by Zend Technologies
```

Se PHP non è installato (o richiede un aggiornamento), installarlo seguendo le istruzioni per la distribuzione Linux.

## Verificare le estensioni installate

Adobe Commerce richiede alcune estensioni PHP. Negli elenchi seguenti vengono specificate le estensioni richieste per ogni edizione di Commerce. Gli elenchi vengono generati automaticamente da una distribuzione che esegue la versione più recente di ogni edizione.

{{$include /help/_includes/templated/php-extensions.md}}

Per verificare le estensioni installate:

1. Elencare i moduli installati.

   ```bash
   php -m
   ```

1. Verifica che siano installate tutte le estensioni richieste.
1. Aggiungi eventuali moduli mancanti utilizzando lo stesso flusso di lavoro utilizzato per l&#39;installazione di PHP.

## Verifica impostazioni PHP

>[!WARNING]
>
>Se stai cercando di risolvere un ambiente legacy interessato dal bug PHP [81101](https://bugs.php.net/bug.php?id=81101), imposta `pcre.jit=0` nel file `php.ini` per risolvere il problema in cui non viene caricato CSS.

- Impostare il fuso orario di sistema per PHP; in caso contrario, errori come il seguente display durante l&#39;installazione e operazioni correlate al tempo come cron potrebbero non funzionare:

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Impostare il limite della memoria PHP.

  Adobe consiglia quanto segue:

   - Compilazione del codice o distribuzione delle risorse statiche, `1G`
   - Debug, `2G`
   - Test, `~3-4G`

- Aumentare i valori per PHP `realpath_cache_size` e `realpath_cache_ttl` alle impostazioni consigliate:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Queste impostazioni consentono ai processi PHP di memorizzare nella cache i percorsi dei file invece di cercarli al caricamento della pagina. Vedi [Ottimizzazione delle prestazioni](https://www.php.net/manual/en/ini.core.php) nella documentazione di PHP.

- Abilita [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), richiesto per Adobe Commerce 2.1 e versioni successive.

  Adobe consiglia di abilitare [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP.

  Adobe Commerce 2.1 e versioni successive utilizzano i commenti del codice PHP per la generazione del codice.

>[!NOTE]
>
>Per evitare problemi durante l&#39;installazione e l&#39;aggiornamento, Adobe consiglia vivamente di applicare le stesse impostazioni PHP sia alla configurazione della riga di comando PHP che alla configurazione del plug-in del server Web PHP. Per ulteriori informazioni, vedere la sezione successiva.

## Trova file di configurazione PHP

Questa sezione illustra come trovare i file di configurazione necessari per aggiornare le impostazioni richieste.

### Trova il file di configurazione `php.ini`

Per trovare la configurazione del server Web, eseguire un file [`phpinfo.php`](optional-software.md#create-phpinfophp) nel browser Web e cercare `Loaded Configuration File` nel modo seguente:

![Pagina informazioni PHP](../../assets/installation/config_phpini-webserver.png)

Per individuare la configurazione della riga di comando PHP, immettete

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se si dispone di un solo file `php.ini`, modificarlo. Se hai due file `php.ini`, modifica *entrambi*. In caso contrario, le prestazioni potrebbero risultare imprevedibili.

### Trova impostazioni di configurazione OPcache

Le impostazioni PHP OPcache si trovano in genere in `php.ini` o `opcache.ini`. La posizione potrebbe dipendere dal sistema operativo in uso e dalla versione PHP. Il file di configurazione OPcache potrebbe avere una sezione `opcache` o impostazioni come `opcache.enable`.

Utilizza le seguenti linee guida per trovarlo:

- Server web Apache:

  Per Ubuntu con Apache, le impostazioni OPcache si trovano in genere nel file `php.ini`.

  Per CentOS con Apache o nginx, le impostazioni OPcache si trovano in genere in `/etc/php.d/opcache.ini`

  In caso contrario, utilizzare il comando seguente per individuarlo:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Server Web nginx con PHP-FPM: `/etc/php/<supported-php-version>/fpm/php.ini`

Se si dispone di più di un `opcache.ini`, modificarli tutti.

## Come impostare le opzioni PHP

Per impostare le opzioni PHP:

1. Apri `php.ini` in un editor di testo.
1. Individua il fuso orario del server nelle [impostazioni del fuso orario](https://www.php.net/manual/en/timezones.php) disponibili
1. Individua la seguente impostazione e, se necessario, rimuovi il commento:

   ```conf
   date.timezone =
   ```

1. Aggiungere l&#39;impostazione del fuso orario specificata al passaggio 2.

1. Modificare il valore di `memory_limit` in uno dei valori consigliati all&#39;inizio di questa sezione.

   Ad esempio:

   ```conf
   memory_limit=2G
   ```

1. Aggiungi o aggiorna la configurazione `realpath_cache` in modo che corrisponda ai seguenti valori:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Salva le modifiche e esci dall’editor di testo.

1. Apri l&#39;altro `php.ini` (se sono diversi) e apporta le stesse modifiche.

## Impostare le opzioni OPcache

Per impostare `opcache.ini` opzioni:

1. Apri il file di configurazione OPcache in un editor di testo:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/<supported-php-version>/fpm/php.ini` (server Web Inginx (CentOS o Ubuntu))

1. Individuare `opcache.save_comments` e rimuoverlo dal commento, se necessario.
1. Assicurarsi che il relativo valore sia impostato su `1`.
1. Salva le modifiche e esci dall’editor di testo.
1. Riavviare il server Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Risoluzione dei problemi

Consulta i seguenti articoli di supporto Adobe Commerce per assistenza nella risoluzione dei problemi PHP:

- [Errore di versione PHP o errore 404 durante l&#39;accesso ad Adobe Commerce in un browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Errori impostazioni PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-settings-errors)
- [Estensione PHP mcrypt non installata correttamente](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/php-mcrypt-extension-not-installed-properly)
- [Problemi relativi al controllo della disponibilità della versione PHP](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues)
- [Errori irreversibili PHP comuni e soluzioni](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions)

<!-- Last updated from includes: 2025-04-04 22:27:22 -->

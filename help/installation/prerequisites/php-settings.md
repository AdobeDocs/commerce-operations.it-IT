---
title: Impostazioni PHP
description: Segui questi passaggi per installare le estensioni PHP richieste e configurare le impostazioni PHP richieste per le installazioni on-premise di Adobe Commerce e Magento Open Source.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: aacc4332cecec0cb9b0f5c23d60b7abd1c63feea
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Impostazioni PHP

Questo argomento illustra come impostare le opzioni PHP richieste.

>[!NOTE]
>
>La versione più recente di Adobe Commerce e Magento Open Source richiede almeno PHP 8.1. Consulta [requisiti di sistema](../system-requirements.md) per tutte le versioni supportate di PHP.

## Verificare che PHP sia installato

PHP è installato per impostazione predefinita sulla maggior parte delle distribuzioni Linux. In questo argomento si presuppone che sia già stato installato PHP. Per verificare se PHP è installato, immetti quanto segue sulla riga di comando:

```bash
php -v
```

Se PHP è installato, viene visualizzato un messaggio simile al seguente:

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Se PHP non è installato (o richiede un aggiornamento), installarlo seguendo le istruzioni per la distribuzione Linux.

## Verificare le estensioni installate

Adobe Commerce e Magento Open Source richiedono alcune estensioni PHP. Negli elenchi seguenti sono specificate le estensioni richieste per ogni edizione di Commerce. Gli elenchi vengono generati automaticamente da una distribuzione che esegue la versione più recente di ogni edizione.

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
>Se si utilizza PHP 7.4.20, impostare `pcre.jit=0` nel tuo `php.ini` file. Questo aggira un PHP [bug](https://bugs.php.net/bug.php?id=81101) che impedisce il caricamento di file CSS.

- Impostare il fuso orario di sistema per PHP; in caso contrario, errori come il seguente display durante l&#39;installazione e operazioni correlate al tempo come cron potrebbero non funzionare:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Impostare il limite della memoria PHP.

  L’Adobe consiglia quanto segue:

   - compilazione del codice o distribuzione di risorse statiche, `1G`
   - Debug, `2G`
   - Test, `~3-4G`

- Aumentare i valori per PHP `realpath_cache_size` e `realpath_cache_ttl` alle impostazioni consigliate:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Queste impostazioni consentono ai processi PHP di memorizzare nella cache i percorsi dei file invece di cercarli al caricamento della pagina. Consulta [Ottimizzazione delle prestazioni](https://www.php.net/manual/en/ini.core.php) nella documentazione PHP.

- Abilita [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), richiesto per Adobe Commerce e Magento Open Source 2.1 e versioni successive.

  L’Adobe consiglia di abilitare [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP.

  Adobe Commerce e Magento Open Source 2.1 e versioni successive utilizzano i commenti del codice PHP per la generazione del codice.

>[!NOTE]
>
>Per evitare problemi durante l&#39;installazione e l&#39;aggiornamento, Adobe consiglia vivamente di applicare le stesse impostazioni PHP sia alla configurazione della riga di comando PHP che alla configurazione del plug-in del server Web PHP. Per ulteriori informazioni, vedere la sezione successiva.

## Trova file di configurazione PHP

Questa sezione illustra come trovare i file di configurazione necessari per aggiornare le impostazioni richieste.

### Trova `php.ini` file di configurazione

Per trovare la configurazione del server web, esegui una [`phpinfo.php` file](optional-software.md#create-phpinfophp) nel browser web e cercare il `Loaded Configuration File` come segue:

![Pagina informazioni PHP](../../assets/installation/config_phpini-webserver.png)

Per individuare la configurazione della riga di comando PHP, immettete

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se ne hai solo uno `php.ini` file, modifica il file. Se ne hai due `php.ini` file, modifica *entrambi* file. In caso contrario, le prestazioni potrebbero risultare imprevedibili.

### Trova impostazioni di configurazione OPcache

Le impostazioni PHP OPcache si trovano in genere in `php.ini` o `opcache.ini`. La posizione potrebbe dipendere dal sistema operativo in uso e dalla versione PHP. Il file di configurazione OPcache potrebbe avere `opcache` sezione o impostazioni come `opcache.enable`.

Utilizza le seguenti linee guida per trovarlo:

- Server web Apache:

  Per Ubuntu con Apache, le impostazioni OPcache si trovano in genere nel `php.ini` file.

  Per CentOS con Apache o nginx, le impostazioni OPcache si trovano in genere in `/etc/php.d/opcache.ini`

  In caso contrario, utilizzare il comando seguente per individuarlo:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Server web nginx con PHP-FPM: `/etc/php/8.1/fpm/php.ini`

Se ne hai più di uno `opcache.ini`, modificale tutte.

## Come impostare le opzioni PHP

Per impostare le opzioni PHP:

1. Apri un `php.ini` in un editor di testo.
1. Individuare il fuso orario del server in [impostazioni del fuso orario](https://www.php.net/manual/en/timezones.php)
1. Individua la seguente impostazione e, se necessario, rimuovi il commento:

   ```conf
   date.timezone =
   ```

1. Aggiungere l&#39;impostazione del fuso orario specificata al passaggio 2.

1. Modifica il valore di `memory_limit` a uno dei valori consigliati all&#39;inizio di questa sezione.

   Ad esempio:

   ```conf
   memory_limit=2G
   ```

1. Aggiungi o aggiorna il `realpath_cache` affinché corrisponda ai seguenti valori:

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

1. Apri l’altro `php.ini` (se sono diversi) e apporta le stesse modifiche.

## Impostare le opzioni OPcache

Per impostare `opcache.ini` opzioni:

1. Apri il file di configurazione OPcache in un editor di testo:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (server web nginx (CentOS o Ubuntu))

1. Individua `opcache.save_comments` e, se necessario, rimuovi il commento.
1. Assicurati che il relativo valore sia impostato su `1`.
1. Salva le modifiche e esci dall’editor di testo.
1. Riavviare il server Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Risoluzione dei problemi

Consulta i seguenti articoli di supporto Adobe Commerce per assistenza nella risoluzione dei problemi PHP:

- [Errore di versione PHP o errore 404 durante l’accesso ad Adobe Commerce in un browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Errori impostazioni PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [Estensione PHP Mcrypt non installata correttamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemi relativi al controllo della disponibilità della versione PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Errori irreversibili PHP comuni e soluzioni](https://support.magento.com/hc/en-us/articles/360030568432)

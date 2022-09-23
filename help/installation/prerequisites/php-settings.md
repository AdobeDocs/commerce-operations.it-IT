---
title: Impostazioni PHP
description: Segui questi passaggi per installare le estensioni PHP richieste e configurare le impostazioni PHP richieste per le installazioni on-premise di Adobe Commerce e Magento Open Source.
source-git-commit: df8240b71efe992bc1c0655aa30c32778297a3c6
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# Impostazioni PHP

In questo argomento viene illustrato come impostare il valore obbligatorio [PHP](https://glossary.magento.com/php) opzioni.

>[!NOTE]
>
>Vedi [requisiti di sistema](../system-requirements.md) per le versioni supportate di PHP.

## Verifica che PHP sia installato

La maggior parte dei sapori di Linux hanno installato PHP per impostazione predefinita. Questo argomento presuppone che sia già stato installato PHP. Per verificare se PHP è già installato, digitare nella riga di comando:

```bash
php -v
```

Se [PHP](https://glossary.magento.com/php) è installato, viene visualizzato un messaggio simile al seguente:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce e Magenti Open Source 2.4 sono compatibili con PHP 7.3, ma si consiglia di testare e utilizzare PHP 7.4.

Se PHP non è installato, o è necessario un aggiornamento della versione, installalo seguendo le istruzioni per il tuo particolare gusto Linux.
Su CentOS, [potrebbero essere necessarie ulteriori misure](https://wiki.centos.org/HowTos/php7).

## Verificare le estensioni installate

Adobe Commerce e Magenti Open Source richiedono l’installazione di un set di estensioni.

{{$include /help/_includes/templated/php-extensions.md}}

Per verificare le estensioni installate:

1. Elenca i moduli installati.

   ```bash
   php -m
   ```

1. Verifica che siano installate tutte le estensioni richieste.
1. Aggiungi tutti i moduli mancanti utilizzando lo stesso flusso di lavoro utilizzato per installare PHP. Ad esempio, se utilizzi `yum` per installare PHP, i moduli PHP 7.4 possono essere aggiunti con:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## Controlla le impostazioni PHP

>[!WARNING]
>
>Se utilizzi PHP 7.4.20, imposta `pcre.jit=0` nel tuo `php.ini` file. Questo aggira un PHP [bug](https://bugs.php.net/bug.php?id=81101) che impedisce il caricamento di CSS.

- Impostare il fuso orario del sistema per PHP; in caso contrario, potrebbero non funzionare errori come la seguente visualizzazione durante l&#39;installazione e operazioni relative all&#39;ora come cron:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Imposta il limite di memoria PHP.

   Le nostre raccomandazioni dettagliate sono:

   - Compilazione del codice o distribuzione di risorse statiche, `1G`
   - Eseguire il debug, `2G`
   - test, `~3-4G`

- Aumenta i valori per il PHP `realpath_cache_size` e `realpath_cache_ttl` alle impostazioni consigliate:

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   Queste impostazioni consentono ai processi PHP di memorizzare in cache i percorsi dei file invece di cercarli ogni volta che una pagina viene caricata. Vedi [Ottimizzazione delle prestazioni](https://www.php.net/manual/en/ini.core.php) nella documentazione PHP.

- Abilita [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), richiesto per Adobe Commerce e Magenti Open Source 2.1 e versioni successive.

   Si consiglia di abilitare [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) per motivi di prestazioni. OPcache è abilitata in molte distribuzioni PHP.

   Adobe Commerce e Magenti Open Source 2.1 e versioni successive utilizzano i commenti del codice PHP per la generazione del codice.

>[!NOTE]
>
>Per evitare problemi durante l&#39;installazione e l&#39;aggiornamento, si consiglia vivamente di applicare le stesse impostazioni PHP sia alla configurazione della riga di comando PHP che alla configurazione del plug-in del server web PHP. Per ulteriori informazioni, consulta la sezione successiva.

## Trova i file di configurazione PHP

Questa sezione illustra come trovare i file di configurazione necessari per aggiornare le impostazioni richieste.

### Trova `php.ini` file di configurazione

Per trovare la configurazione del server web, esegui una [`phpinfo.php` file](optional-software.md#create-phpinfophp) nel browser web e cerca `Loaded Configuration File` come segue:

![Pagina di informazioni PHP](../../assets/installation/config_phpini-webserver.png)

Per individuare la configurazione della riga di comando PHP, immettere

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Se ne hai solo uno `php.ini` file, apporta le modifiche in quel file. Se ne hai due `php.ini` file, apporta le modifiche *tutto* file. In caso contrario, le prestazioni potrebbero essere imprevedibili.

### Trova impostazioni di configurazione OPcache

Le impostazioni PHP OPcache si trovano in genere in `php.ini` o `opcache.ini`. La posizione potrebbe dipendere dal sistema operativo e dalla versione PHP. Il file di configurazione OPcache potrebbe avere un `opcache` sezione o impostazioni come `opcache.enable`.

Utilizza le seguenti linee guida per trovarlo:

- Server web Apache:

   Per Ubuntu con Apache, le impostazioni OPcache si trovano in genere nel `php.ini` file.

   Per CentOS con Apache o nginx, le impostazioni OPcache si trovano in genere in `/etc/php.d/opcache.ini`

   In caso contrario, utilizzare il comando seguente per individuarlo:

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- server web nginx con PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Se ne hai più di uno `opcache.ini`, modificateli tutti.

## Come impostare le opzioni PHP

Per impostare le opzioni PHP:

1. Apri un `php.ini` in un editor di testo.
1. Individua il fuso orario del server nella [impostazioni del fuso orario](https://www.php.net/manual/en/timezones.php)
1. Individua la seguente impostazione e rimuovi il commento se necessario:

   ```conf
   date.timezone =
   ```

1. Aggiungi l&#39;impostazione del fuso orario trovata al passaggio 2.

1. Modifica il valore di `memory_limit` a uno dei valori consigliati all&#39;inizio di questa sezione.

   Ad esempio:

   ```conf
   memory_limit=2G
   ```

1. Aggiungi o aggiorna il `realpath_cache` configurazione per corrispondere ai seguenti valori:

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

## Imposta le opzioni OPcache

Per impostare `opcache.ini` opzioni:

1. Apri il file di configurazione OPcache in un editor di testo:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (server web nginx (CentOS o Ubuntu)

1. Individua `opcache.save_comments` e, se necessario, rimuovilo dal commento.
1. Assicurati che il relativo valore sia impostato su `1`.
1. Salva le modifiche e esci dall’editor di testo.
1. Riavvia il server Web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu e CentOS: `service nginx restart`

## Risoluzione dei problemi

Per assistenza nella risoluzione dei problemi PHP, consulta i seguenti articoli del supporto Adobe Commerce:

- [Errore di versione PHP o errore 404 quando si accede ad Adobe Commerce nel browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Errori delle impostazioni PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [Estensione PHP mcrypt non installata correttamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemi relativi al controllo di preparazione della versione PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Errori e soluzioni comuni PHP Fatal](https://support.magento.com/hc/en-us/articles/360030568432)

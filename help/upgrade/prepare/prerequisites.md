---
title: Prerequisiti completi
description: Prepara il progetto Adobe Commerce o Magenti Open Source per un aggiornamento completando questi passaggi preliminari.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prerequisiti per l’aggiornamento completi

È importante comprendere cosa è necessario per eseguire Adobe Commerce o Magenti Open Source. È innanzitutto necessario esaminare le [requisiti di sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) per la versione a cui si prevede di eseguire l’aggiornamento.

Dopo aver esaminato i requisiti di sistema, è necessario completare i seguenti prerequisiti prima di aggiornare il sistema:

- Aggiorna tutto il software
- Verifica che Elasticsearch sia installato
- Imposta il limite dei file aperti
- Verifica che i lavori cron siano in esecuzione
- Imposta `DATA_CONVERTER_BATCH_SIZE`
- Verifica delle autorizzazioni del file system
- Imposta la `pub/` directory root
- Installa il plugin di aggiornamento del Compositore

## Aggiorna tutto il software

La [requisiti di sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) descrivere esattamente quali versioni di software di terze parti sono state testate con Adobe Commerce e versioni di Magento Open Source.

Assicurati di aver aggiornato tutti i requisiti e le dipendenze di sistema nel tuo ambiente. Vedi PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php)e [impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## Verifica che l&#39;Elasticsearch sia installato

Adobe Commerce e Magenti Open Source richiedono l&#39;installazione di Elasticsearch per poter utilizzare il software. Prima di eseguire l&#39;aggiornamento da 2.3.x a 2.4, è necessario verificare se si utilizza MySQL, Elasticsearch o un&#39;estensione di terze parti come motore di ricerca del catalogo nell&#39;istanza 2.3.x. Il risultato determina le operazioni da eseguire _prima_ aggiornamento a 2.4.

Puoi utilizzare la riga di comando o l’amministratore per determinare il motore di ricerca del catalogo:

- Inserisci il `bin/magento config:show catalog/search/engine` comando. Il comando restituisce un valore di `mysql`, `elasticsearch` (che indica che è configurato l’Elasticsearch 2), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`o un valore personalizzato che indica che è stato installato un motore di ricerca di terze parti.

- Dall’amministratore, controlla il valore del **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** campo .

Le sezioni seguenti descrivono le azioni da eseguire prima di eseguire l’aggiornamento alla versione 2.4.0.

### MySQL

A partire dalla versione 2.4, MySQL non è più un motore di ricerca del catalogo supportato. È necessario installare e configurare Elasticsearch prima dell’aggiornamento. Utilizza le risorse seguenti per guidarti in questo processo:

- [Installare e configurare Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [Installazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configurare Elasticsearch con cui lavorare [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) o [Apache](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [Configurare Commerce per utilizzare Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) e reindicizza

Alcuni motori di ricerca di catalogo di terze parti vengono eseguiti sul motore di ricerca Adobe Commerce. Contatta il fornitore per determinare se devi aggiornare l&#39;estensione.

### Elasticsearch

È necessario installare e configurare Elasticsearch prima di eseguire l’aggiornamento alla versione 2.4.0. Adobe non supporta più Elasticsearch 2.x, 5.x e 6.x.

Fai riferimento a [Aggiornamento dell’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete su come eseguire il backup dei dati, rilevare potenziali problemi di migrazione e testare gli aggiornamenti prima dell’implementazione in produzione. A seconda della versione corrente dell&#39;Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

Elasticsearch richiede JDK 1.8 o versione successiva. Vedi [Installare il Java Software Development Kit (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) per verificare quale versione di JDK è installata.

[Configurare il Magento da utilizzare come Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) descrive le attività da eseguire dopo l’aggiornamento dell’Elasticsearch 2 a una versione supportata.

### Estensioni di terze parti

Contatta il fornitore del motore di ricerca per determinare se l’estensione è completamente compatibile con la versione 2.4.

## Imposta il limite dei file aperti

L&#39;impostazione del limite dei file aperti (ulimit) può aiutare a evitare errori da più chiamate ricorsive di stringhe di query lunghe o problemi con l&#39;utilizzo del `bin/magento setup:rollback` comando. Questo comando è diverso per i diversi gusci UNIX. Consulta il tuo gusto individuale per informazioni specifiche sul `ulimit` comando.

Adobe consiglia di impostare i file aperti [ulimit](http://ss64.com/bash/ulimit.html) a un valore di `65536` o più, ma puoi utilizzare un valore più grande se necessario. È possibile impostare l&#39;opzione di limitazione sulla riga di comando oppure impostarla come impostazione permanente per la shell dell&#39;utente.

Per impostare l&#39;ultimo dalla riga di comando:

1. Passa alla [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Imposta l&#39;ultimo su 65536.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > La sintassi per l&#39;eliminazione dei file aperti dipende dalla shell UNIX utilizzata. L’impostazione precedente deve funzionare con CentOS e Ubuntu con la shell Bash. Tuttavia, per il sistema operativo Mac, l&#39;impostazione corretta è ulimit -S 65532. Per ulteriori informazioni, consultare una pagina man o un riferimento al sistema operativo.

Per impostare il valore nella shell Bash:

1. Passa alla [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Apri `/home/<username>/.bashrc` in un editor di testo.
1. Aggiungi la riga seguente:

   ```bash
   ulimit -s 65536
   ```

1. Salva le modifiche apportate al `.bashrc` e esci dall’editor di testo.

>[!IMPORTANT]
>
>È consigliabile evitare di impostare un valore per `pcre.recursion_limit` nella `php.ini` file perché può causare ripristini incompleti senza preavviso di errore.

## Verifica che i lavori cron siano in esecuzione

Utilità di pianificazione UNIX `cron` è fondamentale per le operazioni quotidiane Adobe Commerce e Magenti Open Source. Pianifica cose come reindicizzazione, newsletter, e-mail, mappe del sito e così via. Diverse funzionalità richiedono almeno un processo cron in esecuzione come proprietario del file system.

Per verificare che il lavoro cron sia configurato correttamente, controlla la crontab immettendo il seguente comando come proprietario del file system:

>[!NOTE]
>
>Il crontab è il file di configurazione responsabile dell&#39;esecuzione dei lavori cron.

```bash
crontab -l
```

Devono essere visualizzati i risultati simili a quelli riportati di seguito:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Un altro sintomo di cron non in esecuzione è il seguente errore nell&#39;amministratore:

![](../../assets/upgrade-guide/cron-not-running.png)

Per visualizzare l’errore, fai clic su **Messaggi di sistema** nella parte superiore della finestra, come segue:

![](../../assets/upgrade-guide/system-messages.png)

Vedi [Configurare ed eseguire cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) per ulteriori informazioni.

## Imposta DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 include miglioramenti a livello di sicurezza che richiedono la conversione di alcuni dati da serializzato a JSON. Questa conversione si verifica durante l&#39;aggiornamento e può richiedere molto tempo, a seconda della quantità di dati presenti nel database.

Le tabelle seguenti sono maggiormente interessate:

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

Se disponi di una grande quantità di dati, puoi migliorare le prestazioni impostando il valore di una variabile di ambiente, `DATA_CONVERTER_BATCH_SIZE`. Per impostazione predefinita, il valore è impostato su `50,000`.

Per impostare la variabile di ambiente:

1. Passa alla [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Imposta la variabile :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` richiede memoria; evita di impostarlo su un valore elevato (circa 1 GB) senza prima testarlo.

1. Al termine dell’aggiornamento, puoi annullare l’impostazione della variabile :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verifica delle autorizzazioni del file system

Per motivi di sicurezza, Adobe Commerce e Magenti Open Source richiedono determinate autorizzazioni sul file system. Le autorizzazioni sono diverse da _[proprietà](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. La proprietà determina chi può eseguire azioni sul file system; le autorizzazioni determinano le operazioni che l&#39;utente può eseguire.

Le directory nel file system devono essere scrivibili dal [del proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) gruppo.

Per verificare che le autorizzazioni del file system siano impostate correttamente, accedi al server dell&#39;applicazione o utilizza l&#39;applicazione file manager del provider di hosting.

Ad esempio, immettere il comando seguente se l&#39;applicazione è installata in `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Output campione:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Per una spiegazione dell&#39;output del campione, vedere quanto segue:

- La maggior parte dei file sono `-rw-rw----`, che è `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- Il proprietario del file system è `magento_user`

Per ottenere informazioni più dettagliate, è possibile immettere il seguente comando:

```bash
ls -la /var/www/html/magento2/pub
```

Poiché Adobe Commerce e Magenti Open Source distribuiscono risorse di file statici nelle sottodirectory di `pub`, è consigliabile verificare anche i permessi e la proprietà in quel luogo.

Per ulteriori informazioni, consulta [Autorizzazioni e proprietà del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## Imposta la `pub/` directory root

Vedi [Modificare il docroot per migliorare la sicurezza](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) per ulteriori dettagli.

## Installa il plugin di aggiornamento del Compositore

La [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Il plug-in Composer risolve le modifiche da apportare al progetto principale `composer.json` prima di eseguire l’aggiornamento a un nuovo requisito del prodotto.

Il plug-in automatizza parzialmente l&#39;aggiornamento manuale identificando e aiutando a risolvere i conflitti di dipendenza invece di richiedere di identificarli e correggerli manualmente.

Per installare il plug-in:

1. Aggiungi il pacchetto al tuo `composer.json` file.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Aggiorna le dipendenze:

   ```bash
   composer update
   ```

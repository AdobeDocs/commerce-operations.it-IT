---
title: Prerequisiti completi
description: Prepara il tuo progetto Adobe Commerce per un aggiornamento completando questi passaggi preliminari.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Completare i prerequisiti per l’aggiornamento

È importante comprendere cosa è necessario per eseguire Adobe Commerce. È innanzitutto necessario esaminare i [requisiti di sistema](../../installation/system-requirements.md) per la versione che si desidera aggiornare.

Dopo aver esaminato i requisiti di sistema, è necessario completare i seguenti prerequisiti prima di aggiornare il sistema:

* Aggiorna tutto il software
* Verificare che sia installato un motore di ricerca supportato
* Converti formato tabella database
* Imposta il limite di file aperti
* Verificare che i processi cron siano in esecuzione
* Imposta `DATA_CONVERTER_BATCH_SIZE`
* Verificare le autorizzazioni del file system
* Imposta la directory principale `pub/`
* Installare il plug-in di aggiornamento Composer

## Aggiorna tutto il software

I [requisiti di sistema](../../installation/system-requirements.md) descrivono esattamente quali versioni di software di terze parti sono state testate con le versioni di Adobe Commerce.

Assicurati di aver aggiornato tutti i requisiti di sistema e le dipendenze nell’ambiente. Vedere PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php) e [impostazioni PHP richieste](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Per i progetti Adobe Commerce su infrastruttura cloud Pro, è necessario creare un ticket [Supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket) per installare o aggiornare i servizi negli ambienti di staging e produzione. Indicare le modifiche necessarie al servizio e includere nel ticket i file `.magento.app.yaml` e `services.yaml` aggiornati e la versione PHP. L’aggiornamento del progetto da parte del team di infrastruttura Cloud può richiedere fino a 48 ore. Consulta [Software e servizi supportati](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html?lang=it#supported-software-and-services).

## Verificare che sia installato un motore di ricerca supportato

Adobe Commerce richiede l’installazione di Elasticsearch o OpenSearch per poter utilizzare il software.

**Se si esegue l&#39;aggiornamento da 2.3.x a 2.4**, è necessario verificare se si utilizza MySQL, Elasticsearch o un&#39;estensione di terze parti come motore di ricerca del catalogo nell&#39;istanza 2.3.x. Il risultato determina cosa devi fare _prima_ dell&#39;aggiornamento a 2.4.

**Se si stanno aggiornando le versioni patch nelle righe della versione 2.3.x o 2.4.x**, se Elasticsearch 7.x è già installato, è possibile [migrare a OpenSearch](opensearch-migration.md).

Puoi utilizzare la riga di comando o l’amministratore per determinare il motore di ricerca del catalogo:

* Immettere il comando `bin/magento config:show catalog/search/engine`. Il comando restituisce un valore di `mysql`, `elasticsearch` (che indica che Elasticsearch 2 è configurato), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` o un valore personalizzato, che indica che è stato installato un motore di ricerca di terze parti. Per le versioni precedenti alla 2.4.6, utilizzare il valore `elasticsearch7` per il motore di Elasticsearch 7 o OpenSearch. Per le versioni 2.4.6 e successive, utilizzare il valore `opensearch` per il motore OpenSearch.

* Dall&#39;amministratore, controllare il valore del campo **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]**.

Le sezioni seguenti descrivono le azioni da intraprendere prima di eseguire l’aggiornamento alla versione 2.4.0.

### MySQL

A partire dalla versione 2.4, MySQL non è più un motore di ricerca catalogo supportato. È necessario installare e configurare Elasticsearch o OpenSearch prima dell&#39;aggiornamento. Utilizza le risorse seguenti per aiutarti a seguire questo processo:

* [Installare e configurare Elasticsearch](../../configuration/search/overview-search.md)
* [Installazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configura [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) o [Apache](../../installation/prerequisites/search-engine/configure-apache.md) per il tuo motore di ricerca
* [Configura Commerce per l&#39;utilizzo di Elasticsearch](../../configuration/search/configure-search-engine.md) e reindicizza

Alcuni motori di ricerca di cataloghi di terze parti vengono eseguiti sul motore di ricerca di Adobe Commerce. Contatta il fornitore per determinare se è necessario aggiornare l’estensione.

### Modifiche a MySQL 8.4

Adobe ha aggiunto il supporto per MySQL 8.4 nella versione 2.4.8.
In questa sezione vengono descritte le principali modifiche apportate a MySQL 8.4 di cui gli sviluppatori devono essere a conoscenza.

#### Chiave non standard obsoleta

L&#39;utilizzo di chiavi non univoche o parziali come chiavi esterne non è standard ed è obsoleto in MySQL 8.4. A partire da MySQL 8.4.0, è necessario abilitare esplicitamente tali chiavi impostando [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) su `OFF` oppure avviando il server con l&#39;opzione `--skip-restrict-fk-on-non-standard-key`.

#### Aggiornamento da MySQL 8.0 ( o versioni precedenti ) a MySQL 8.4

Per aggiornare correttamente MySQL dalla versione 8.0 alla versione 8.4, è necessario seguire i passaggi seguenti nell&#39;ordine in cui si desidera eseguire:

1. Abilita modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

1. Eseguire un backup del database:

   ```bash
   bin/magento setup:backup --db
   ```

1. Aggiornare MySQL alla versione 8.4.
1. Imposta `restrict_fk_on_non_standard_key` su `OFF` in `[mysqld]` nel file `my.cnf`.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Se non si modifica il valore di `restrict_fk_on_non_standard_key` in `OFF`, verrà visualizzato il seguente errore durante l&#39;importazione:
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Riavviare il server MySQL.
1. Importare i dati di backup in MySQL.
1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Disattiva modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Motore di ricerca

Prima di eseguire l’aggiornamento a 2.4.0, è necessario installare e configurare Elasticsearch 7.6 o versione successiva o OpenSearch 1.2. Adobe non supporta più Elasticsearch 2.x, 5.x e 6.x. [Configurazione del motore di ricerca](../../configuration/search/configure-search-engine.md) nella _Guida alla configurazione_ descrive le attività da eseguire dopo l&#39;aggiornamento di Elasticsearch a una versione supportata.

Consulta [Aggiornamento di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete sul backup dei dati, l&#39;individuazione di potenziali problemi di migrazione e il test degli aggiornamenti prima della distribuzione in produzione. A seconda della versione corrente di Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

Elasticsearch richiede Java Development Kit (JDK) 1.8 o versione successiva. Consulta [Installare Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) per verificare quale versione di JDK è installata.

#### OpenSearch

OpenSearch è un fork open-source di Elasticsearch 7.10.2, a seguito della modifica delle licenze di Elasticsearch. Nelle seguenti versioni di Adobe Commerce è stato introdotto il supporto per OpenSearch:

* 2.4.6 (OpenSearch ha un modulo e impostazioni separati)
* 2.4.5.
* 2.4.4.
* 2.4.3-p2
* 2.3.7-p3

Puoi [migrare da Elasticsearch a OpenSearch](opensearch-migration.md) solo se esegui l&#39;aggiornamento a una versione di Adobe Commerce elencata sopra (o successiva).

OpenSearch richiede JDK 1.8 o versione successiva. Consulta [Installare Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) per verificare quale versione di JDK è installata.

[Configurazione del motore di ricerca](../../configuration/search/configure-search-engine.md) descrive le attività da eseguire dopo la modifica dei motori di ricerca.

#### Aggiornare Elasticsearch

Il supporto per Elasticsearch 8.x è stato introdotto in Adobe Commerce 2.4.6. Le istruzioni seguenti mostrano un esempio di aggiornamento di Elasticsearch da 7.x a 8.x:

>[!NOTE]
>
>Nella prossima versione di 2.4.8, questi passaggi non saranno necessari perché il modulo Elasticsearch 8 è incluso per impostazione predefinita e non sarà necessario installarlo separatamente.

1. Aggiorna il server Elasticsearch 7.x a 8.x e assicurati che sia operativo. Consulta la [documentazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Abilita il campo `id_field_data` aggiungendo la seguente configurazione al file `elasticsearch.yml` e riavviando il servizio Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Per supportare Elasticsearch 8.x, Adobe Commerce 2.4.6 non consente la proprietà `indices.id_field_data` per impostazione predefinita e utilizza il campo `_id` nella proprietà `docvalue_fields`.

1. Nella directory principale del progetto Adobe Commerce, aggiorna le dipendenze del Compositore per rimuovere il modulo `Magento_Elasticsearch7` e installare il modulo `Magento_Elasticsearch8`.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Se si verifica un errore di dipendenza per `psr/http-message`, fare clic per espandere la seguente sezione di risoluzione dei problemi:

   +++Risoluzione dei problemi

   Se si verificano conflitti di dipendenza durante l&#39;installazione di Elasticsearch 8, in particolare con `psr/http-message`, è possibile risolvere il problema seguendo la procedura riportata di seguito:

   1. Innanzitutto, devi richiedere il modulo Elasticsearch 8 senza aggiornare altre dipendenze:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. Quindi aggiorna il modulo Elasticsearch 8 e `aws/aws-sdk-php` pacchetti:

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Questo approccio funziona per 2,4,7-p4 con PHP 8,3. Il problema si verifica perché `aws/aws-sdk-php` richiede `psr/http-message >= 2.0`, che può causare conflitti. I passaggi precedenti aiutano a risolvere questi problemi di dipendenza.

   +++

1. Aggiorna i componenti del progetto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configura Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in [!DNL Admin].

1. Reindicizza l’indice del catalogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Elimina tutti gli elementi dai tipi di cache abilitati.

   ```bash
   bin/magento cache:clean
   ```

#### Downgrade di Elasticsearch

Se aggiorni inavvertitamente la versione di Elasticsearch sul server o stabilisci che è necessario effettuare il downgrade per qualsiasi altro motivo, devi aggiornare anche le dipendenze dei progetti Adobe Commerce. Ad esempio, per effettuare il downgrade da Elasticsearch 8.x a 7.x

1. Esegui il downgrade del server Elasticsearch 8.x alla versione 7.x e accertati che sia funzionante. Consulta la [documentazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Nella directory principale del progetto Adobe Commerce, aggiornare le dipendenze del Compositore per rimuovere il modulo `Magento_Elasticsearch8` e le relative dipendenze del Compositore e installare il modulo `Magento_Elasticsearch7`.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Aggiorna i componenti del progetto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configura Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in [!DNL Admin].

1. Reindicizza l’indice del catalogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Elimina tutti gli elementi dai tipi di cache abilitati.

   ```bash
   bin/magento cache:clean
   ```

### Estensioni di terze parti

Contatta il fornitore del motore di ricerca per determinare se l’estensione è completamente compatibile con una versione di Adobe Commerce.

## Converti formato tabella database

È necessario convertire il formato di tutte le tabelle di database da `COMPACT` a `DYNAMIC`. È inoltre necessario convertire il tipo di motore di archiviazione da `MyISAM` a `InnoDB`. Consulta [best practice](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Imposta il limite di file aperti

L&#39;impostazione del limite dei file aperti (ulimit) consente di evitare errori dovuti a più chiamate ricorsive di stringhe di query lunghe o problemi con l&#39;utilizzo del comando `bin/magento setup:rollback`. Questo comando è diverso per le diverse shell UNIX. Per informazioni specifiche sul comando `ulimit`, consultare la versione personalizzata.

Adobe consiglia di impostare i file aperti [ulimit](https://ss64.com/bash/ulimit.html) su un valore pari o superiore a `65536`, ma se necessario è possibile utilizzare un valore maggiore. È possibile impostare il limite massimo sulla riga di comando oppure impostarlo come impostazione permanente per la shell dell&#39;utente.

Per impostare il limite dalla riga di comando:

1. Passa al [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Impostare il limite su `65536`.

   ```bash
   ulimit -n 65536
   ```

Per impostare il valore nella shell Bash:

1. Passa al [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Apri `/home/<username>/.bashrc` in un editor di testo.
1. Aggiungi la seguente riga:

   ```bash
   ulimit -n 65536
   ```

1. Salvare le modifiche apportate al file `.bashrc` e uscire dall&#39;editor di testo.

>[!IMPORTANT]
>
>È consigliabile evitare di impostare un valore per la proprietà `pcre.recursion_limit` nel file `php.ini`, in quanto potrebbe causare rollback incompleti senza alcun avviso di errore.

## Verificare che i processi cron siano in esecuzione

L&#39;Utilità di pianificazione UNIX `cron` è fondamentale per le operazioni quotidiane di Adobe Commerce. Pianifica elementi come reindicizzazione, newsletter, e-mail e sitemap. Diverse funzionalità richiedono almeno un processo cron in esecuzione come proprietario del file system.

Per verificare che il processo cron sia configurato correttamente, controllare la scheda cronica immettendo il comando seguente come proprietario del file system:

>[!NOTE]
>
>Crontab è il file di configurazione responsabile dell&#39;esecuzione dei processi cron.

```bash
crontab -l
```

Dovrebbero essere visualizzati risultati simili ai seguenti:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Un altro sintomo di cron non in esecuzione è il seguente errore in Admin:

![Messaggi di sistema - cron non in esecuzione](../../assets/upgrade-guide/cron-not-running.png)

Per visualizzare l&#39;errore, fare clic su **Messaggi di sistema** nella parte superiore della finestra nel modo seguente:

![Notifica messaggi di sistema](../../assets/upgrade-guide/system-messages.png)

Per ulteriori informazioni, vedere [Configurare ed eseguire cron](../../configuration/cli/configure-cron-jobs.md).

## Imposta DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 include miglioramenti della sicurezza che richiedono la conversione di alcuni dati da serializzati a JSON. Questa conversione si verifica durante l’aggiornamento e può richiedere molto tempo, a seconda della quantità di dati presenti nel database.

Le tabelle seguenti sono quelle maggiormente interessate:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Se la quantità di dati è elevata, è possibile migliorare le prestazioni impostando il valore di una variabile di ambiente, `DATA_CONVERTER_BATCH_SIZE`. Per impostazione predefinita, il valore è impostato su `50,000`.

Per impostare la variabile di ambiente:

1. Passa al [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Imposta la variabile:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` richiede memoria; evitare di impostarla su un valore elevato (circa 1 GB) senza prima testarla.

1. Al termine dell’aggiornamento, puoi annullare l’impostazione della variabile:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Verificare le autorizzazioni del file system

Per motivi di sicurezza, Adobe Commerce richiede determinate autorizzazioni sul file system. Le autorizzazioni sono diverse da _[proprietà](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. La proprietà determina chi può eseguire azioni sul file system; le autorizzazioni determinano ciò che l’utente può fare.

Le directory nel file system devono essere scrivibili dal gruppo [&#x200B; del proprietario del file system &#x200B;](../../installation/prerequisites/file-system/overview.md).

Per verificare che le autorizzazioni del file system siano impostate correttamente, accedere al server applicazioni o utilizzare l&#39;applicazione di gestione file del provider di hosting.

Ad esempio, immettere il seguente comando se l&#39;applicazione è installata in `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Output di esempio:

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

Per una spiegazione dell&#39;output di esempio, vedere quanto segue:

* La maggior parte dei file sono `-rw-rw----`, ovvero `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* Il proprietario del file system è `magento_user`

Per ottenere informazioni più dettagliate, è possibile immettere il seguente comando:

```bash
ls -la /var/www/html/magento2/pub
```

Poiché Adobe Commerce distribuisce risorse di file statici nelle sottodirectory di `pub`, è consigliabile verificare anche le autorizzazioni e la proprietà in tali sottodirectory.

Per ulteriori informazioni, vedere [Autorizzazioni e proprietà del file system](../../installation/prerequisites/file-system/overview.md).

## Imposta la directory principale `pub/`

Per ulteriori dettagli, vedere [Modificare la directory principale dei documenti per migliorare la protezione](../../installation/tutorials/docroot.md).

## Installare il plug-in di aggiornamento Composer

Il plug-in [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer risolve le modifiche che devono essere apportate al file di progetto principale `composer.json` prima di eseguire l&#39;aggiornamento a un nuovo requisito di prodotto.

Il plug-in automatizza parzialmente l’aggiornamento manuale identificando e aiutandoti a risolvere i conflitti di dipendenza invece di richiedere di identificarli e correggerli manualmente.

Per installare il plug-in:

1. Aggiungi il pacchetto al file `composer.json`.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Aggiornare le dipendenze:

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2024-02-12 09:51:27 -->

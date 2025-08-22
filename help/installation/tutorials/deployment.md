---
title: Creare o aggiornare la configurazione della distribuzione
description: Per gestire la configurazione dell’implementazione di Adobe Commerce, segui la procedura riportata di seguito.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Creare o aggiornare la configurazione della distribuzione

Non esistono prerequisiti per l&#39;utilizzo di questo comando.

## Creare o aggiornare la configurazione della distribuzione

[La configurazione della distribuzione](../../configuration/reference/deployment-files.md) fornisce le informazioni necessarie per l&#39;inizializzazione e l&#39;avvio dell&#39;applicazione.

È possibile utilizzare questo comando se:

* L&#39;applicazione è stata installata in precedenza e si desidera modificare la configurazione della distribuzione
* Desideri creare solo la configurazione di distribuzione e continuare l’installazione in un altro modo
* Per aggiornare la configurazione di distribuzione senza influire su altri elementi

Opzioni comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

Nella tabella seguente vengono illustrati i significati dei parametri e dei valori di installazione.

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `--backend-frontname` | Identificatore di risorsa uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) per accedere all&#39;amministratore.<br><br>Per evitare gli exploit, si consiglia di non utilizzare una parola comune come admin, backend. L&#39;URI amministratore può contenere solo valori alfanumerici e il carattere di sottolineatura (`_`). | No |
| `--db-host` | Utilizzare uno dei seguenti elementi:<br><br>- Nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (impostazione predefinita) o `127.0.0.1` se il server di database si trova sullo stesso host del server Web. localhost indica che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa in modo che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, consulta la [documentazione PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** è possibile specificare la porta del server di database nel nome host, ad esempio `www.example.com:9000` | No |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle di database.<br><br>Il valore predefinito è `magento2`. | No |
| `--db-user` | Nome utente del proprietario dell&#39;istanza di database.<br><br>Il valore predefinito è `root`. | No |
| `--db-password` | Password del proprietario dell&#39;istanza di database. | No |
| `--db-prefix` | Da utilizzare solo se si installano le tabelle di database in un&#39;istanza di database in cui sono già presenti tabelle Adobe Commerce.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione. Alcuni clienti hanno più di un’istanza di Adobe Commerce in esecuzione su un server con tutte le tabelle nello stesso database.<br><br>La lunghezza del prefisso non può superare i cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più installazioni di Adobe Commerce. | No |
| `--session-save` | Utilizzare uno dei seguenti elementi:<br><br>- `db` per archiviare i dati della sessione nel [database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Se si dispone di un database in cluster, scegliere l&#39;archiviazione del database. In caso contrario, l&#39;archiviazione basata su file potrebbe non offrire molti vantaggi.<br><br>- `files` per archiviare i dati della sessione nel file system. L&#39;archiviazione delle sessioni basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o che si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per archiviare i dati della sessione in [Utilizzare Redis per l&#39;archiviazione della sessione](../../configuration/cache/config-redis.md). Se utilizzi Redis per il caching predefinito o delle pagine, Redis deve essere già installato. | No |
| `--key` | Se ne hai uno, specifica una chiave per crittografare [dati sensibili](#sensitive-data) nel database. Se non ne hai uno, l’applicazione ne genera uno per te. | No |
| `--db-init-statements` | Parametro di configurazione MySQL avanzato. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL.<br><br>Il valore predefinito è `SET NAMES utf8;`.<br><br>Consulta un riferimento simile a [questo](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) prima di impostare qualsiasi valore. | No |
| `--http-cache-hosts` | Elenco separato da virgole di host gateway cache HTTP a cui inviare richieste di eliminazione. Ad esempio, i server di vernice. Utilizza questo parametro per specificare l’host o gli host da eliminare nella stessa richiesta. (Non importa se si dispone solo di uno o più host).<br><br>Il formato deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80. Ad esempio, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Non separare gli host con uno spazio. | No |

## Importare dati di configurazione

Durante la configurazione di un sistema di produzione, è consigliabile importare le impostazioni di configurazione da `config.php` e `env.php` nel database.
Queste impostazioni includono percorsi e valori di configurazione, siti web, store, visualizzazioni store e temi.

Dopo aver importato siti Web, store, visualizzazioni di store e temi, puoi creare attributi di prodotto e applicarli a siti Web, store e visualizzazioni di store nel sistema di produzione.

Nel sistema di produzione eseguire il comando seguente per importare i dati dai file di configurazione (`config.php` e `env.php`) nel database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Il flag opzionale `[-n, --no-interaction]` consente l&#39;esecuzione del comando senza ulteriori conferme.

Per ulteriori informazioni, controllare [Importa dati dai file di configurazione](../../configuration/cli/import-configuration.md)

### Dati sensibili

{{$include /help/_includes/sensitive-data.md}}

<!-- Last updated from includes: 2024-04-16 09:42:31 -->

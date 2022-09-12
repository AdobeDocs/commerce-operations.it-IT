---
title: Creare o aggiornare la configurazione della distribuzione
description: Segui questi passaggi per gestire la configurazione di distribuzione di Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Creare o aggiornare la configurazione della distribuzione

Non esistono prerequisiti per l&#39;utilizzo di questo comando.

## Creare o aggiornare la configurazione della distribuzione

[Configurazione della distribuzione](../../configuration/reference/deployment-files.md) fornisce le informazioni necessarie per inizializzare e avviare l&#39;applicazione.

Puoi usare questo comando se:

* Hai installato l’applicazione in precedenza e desideri modificare la configurazione della distribuzione
* Creare solo la configurazione di distribuzione e continuare l&#39;installazione in un altro modo
* Aggiornare la configurazione di distribuzione senza influire su nessun altro elemento

Opzioni di comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

La tabella seguente illustra il significato dei parametri e dei valori di installazione.

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `--backend-frontname` | Identificatore risorsa uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) per accedere all’amministratore.<br><br>Per evitare le esplosioni, si consiglia di non utilizzare una parola comune come admin, backend. L’URI amministratore può contenere valori alfanumerici e il carattere di sottolineatura (`_`). | No |
| `--db-host` | Utilizza una delle seguenti opzioni:<br><br>- Nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (predefinito) o `127.0.0.1` se il server di database si trova sullo stesso host del server Web. localhost indica che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa sì che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, consulta la sezione [Documentazione PHP DOP_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Facoltativamente, puoi specificare la porta del server di database nel nome host come `www.example.com:9000` | No |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle del database.<br><br>Il valore predefinito è `magento2`. | No |
| `--db-user` | Nome utente del proprietario dell&#39;istanza del database.<br><br>Il valore predefinito è `root`. | No |
| `--db-password` | Password del proprietario dell&#39;istanza del database. | No |
| `--db-prefix` | Utilizzare solo se si stanno installando le tabelle di database in un&#39;istanza di database che contiene già Adobe Commerce e tabelle di Magento Open Source.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione corrente. Alcuni clienti hanno più di un&#39;istanza Adobe Commerce o Magento Open Source in esecuzione su un server con tutte le tabelle nello stesso database.<br><br>Il prefisso può contenere al massimo cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più di un’installazione Adobe Commerce o Magenti Open Source. | No |
| `--session-save` | Utilizza una delle seguenti opzioni:<br><br>- `db` per memorizzare i dati della sessione in [database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Scegliere l&#39;archiviazione del database se si dispone di un database cluster; in caso contrario, potrebbe non esservi un grande vantaggio rispetto allo storage basato su file.<br><br>- `files` per memorizzare i dati della sessione nel file system. L&#39;archiviazione della sessione basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per memorizzare i dati della sessione in [Utilizzare Redis per l&#39;archiviazione delle sessioni](../../configuration/cache/config-redis.md). Se si utilizza Redis per il caching predefinito o della pagina, Redis deve essere già installato. | No |
| `--key` | Se disponibile, specifica una chiave da crittografare [dati sensibili](#sensitive-data) nel database. Se non ne hai uno, l&#39;applicazione ne genera uno per te. | No |
| `--db-init-statements` | Parametro di configurazione avanzato di MySQL. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL.<br><br>Il valore predefinito è `SET NAMES utf8;`.<br><br>Consultare un riferimento simile a [questo](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) prima di impostare qualsiasi valore. | No |
| `--http-cache-hosts` | Elenco separato da virgole degli host del gateway della cache HTTP a cui inviare le richieste di eliminazione. (Ad esempio, server Varnish). Usa questo parametro per specificare l’host da eliminare nella stessa richiesta. (Non importa se hai un solo host o molti host.)<br><br>Il formato deve essere `<hostname or ip>:<listen port>`, in cui è possibile omettere `<listen port>` se è la porta 80. Ad esempio, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Non separare gli host con un carattere spazio. | No |

## Importare dati di configurazione

Quando si configura un sistema di produzione, è buona prassi importare le impostazioni di configurazione da `config.php` e `env.php` nel database.
Queste impostazioni includono percorsi e valori di configurazione, siti web, store, viste store e temi.

Dopo aver importato siti web, store, viste store e temi, puoi creare attributi di prodotto e applicarli a siti web, negozi e viste store sul sistema di produzione.

Sul sistema di produzione, esegui il seguente comando per importare dati dai file di configurazione (`config.php` e `env.php`) nel database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

L&#39;opzione `[-n, --no-interaction]` Il flag consente l’esecuzione del comando senza ulteriori conferme.

Per ulteriori informazioni, controlla il [Importare dati dai file di configurazione](../../configuration/cli/import-configuration.md)

### Dati sensibili

{{$include /help/_includes/sensitive-data.md}}

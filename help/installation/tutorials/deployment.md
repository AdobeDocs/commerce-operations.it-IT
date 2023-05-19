---
title: Creare o aggiornare la configurazione della distribuzione
description: Per gestire la configurazione della distribuzione di Adobe Commerce o di Magento Open Source, segui la procedura riportata di seguito.
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Creare o aggiornare la configurazione della distribuzione

Non esistono prerequisiti per l&#39;utilizzo di questo comando.

## Creare o aggiornare la configurazione della distribuzione

[Configurazione della distribuzione](../../configuration/reference/deployment-files.md) fornisce le informazioni necessarie per l&#39;inizializzazione e l&#39;avvio dell&#39;applicazione.

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
| `--backend-frontname` | Identificatore risorsa uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) per accedere all&#39;Admin.<br><br>Per evitare attacchi, ti consigliamo di non utilizzare una parola comune come admin, backend. L’URI amministratore può contenere valori alfanumerici e il carattere di sottolineatura (`_`) solo. | No |
| `--db-host` | Usare una delle seguenti opzioni:<br><br>: nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (impostazione predefinita) oppure `127.0.0.1` se il server di database si trova sullo stesso host del server web. localhost indica che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa in modo che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, vedere [Documentazione PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Facoltativamente, puoi specificare la porta del server di database nel suo nome host, ad esempio `www.example.com:9000` | No |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle di database.<br><br>Il valore predefinito è `magento2`. | No |
| `--db-user` | Nome utente del proprietario dell&#39;istanza di database.<br><br>Il valore predefinito è `root`. | No |
| `--db-password` | Password del proprietario dell&#39;istanza di database. | No |
| `--db-prefix` | Da utilizzare solo se si installano le tabelle di database in un&#39;istanza di database in cui sono già presenti tabelle Adobe Commerce e Magenti Open Source.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione. Alcuni clienti dispongono di più istanze di Adobe Commerce o di Magento Open Source in esecuzione su un server con tutte le tabelle nello stesso database.<br><br>La lunghezza del prefisso non può superare i cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più installazioni di Adobe Commerce o di Magento Open Source. | No |
| `--session-save` | Usare una delle seguenti opzioni:<br><br>- `db` per memorizzare i dati della sessione in [database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Se si dispone di un database in cluster, scegliere l&#39;archiviazione del database. In caso contrario, l&#39;archiviazione basata su file potrebbe non offrire molti vantaggi.<br><br>- `files` per memorizzare i dati della sessione nel file system. L&#39;archiviazione delle sessioni basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o che si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per memorizzare i dati della sessione in [Usa Redis per l’archiviazione della sessione](../../configuration/cache/config-redis.md). Se utilizzi Redis per il caching predefinito o delle pagine, Redis deve essere già installato. | No |
| `--key` | Se ne hai una, specifica una chiave da crittografare [dati sensibili](#sensitive-data) nel database. Se non ne hai uno, l’applicazione ne genera uno per te. | No |
| `--db-init-statements` | Parametro di configurazione MySQL avanzato. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL.<br><br>Il valore predefinito è `SET NAMES utf8;`.<br><br>Consulta un riferimento simile a [questo](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) prima di impostare qualsiasi valore. | No |
| `--http-cache-hosts` | Elenco separato da virgole di host gateway cache HTTP a cui inviare richieste di eliminazione. Ad esempio, i server di vernice. Utilizza questo parametro per specificare l’host o gli host da eliminare nella stessa richiesta. (Non importa se si dispone solo di uno o più host).<br><br>Il formato deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se è la porta 80. Ad esempio: `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Non separare gli host con uno spazio. | No |

## Importare dati di configurazione

Durante la configurazione di un sistema di produzione, è buona norma importare le impostazioni di configurazione da `config.php` e `env.php` nel database.
Queste impostazioni includono percorsi e valori di configurazione, siti web, store, visualizzazioni store e temi.

Dopo aver importato siti Web, store, visualizzazioni di store e temi, puoi creare attributi di prodotto e applicarli a siti Web, store e visualizzazioni di store nel sistema di produzione.

Nel sistema di produzione, eseguire il comando seguente per importare i dati dai file di configurazione (`config.php` e `env.php`) al database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

L&#39;opzione `[-n, --no-interaction]` Il flag consente l’esecuzione del comando senza ulteriori conferme.

Per ulteriori informazioni, vedere [Importare dati dai file di configurazione](../../configuration/cli/import-configuration.md)

### Dati sensibili

{{$include /help/_includes/sensitive-data.md}}

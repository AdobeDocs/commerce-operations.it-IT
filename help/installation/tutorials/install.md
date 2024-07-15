---
title: Installare Adobe Commerce
description: Per installare Adobe Commerce nell’infrastruttura di tua proprietà, segui la procedura riportata di seguito.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '2094'
ht-degree: 0%

---

# Installare Adobe Commerce

Prima di iniziare, completa i passaggi seguenti:

* Verifica che il tuo sistema soddisfi i requisiti descritti in [requisiti di sistema](../system-requirements.md).

* Completa tutte le [attività prerequisite](../prerequisites/overview.md).

* Completare i primi passaggi di installazione. Vedi [Percorso di installazione o aggiornamento](../overview.md).

* Dopo aver effettuato l&#39;accesso al server applicazioni, [passare al proprietario del file system](../prerequisites/file-system/overview.md).

* Rivedi la panoramica di [Introduzione all&#39;installazione della riga di comando](../composer.md).

>[!NOTE]
>
>È necessario installare l&#39;applicazione dalla relativa sottodirectory `bin`.

È possibile eseguire il programma di installazione più volte con diverse opzioni per completare attività di installazione come le seguenti:

* Eseguire l&#39;installazione in più fasi: ad esempio, dopo aver configurato il server Web per Secure Sockets Layer (SSL), è possibile eseguire di nuovo il programma di installazione per impostare le opzioni SSL.

* Correggere gli errori nelle installazioni precedenti.

* Installare l&#39;applicazione in un&#39;istanza di database diversa.

>[!NOTE]
>
>Per impostazione predefinita, il programma di installazione non sovrascrive il database se si installa il software Commerce nella stessa istanza di database. È possibile utilizzare il parametro facoltativo `cleanup-database` per modificare questo comportamento.

Vedere anche [Aggiorna, reinstalla, disinstalla](uninstall.md).

## Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Comandi della Guida del programma di installazione

È possibile eseguire i seguenti comandi per trovare i valori per alcuni argomenti obbligatori:

| Argomento del programma di installazione | Comando |
| ------------------ | ------------------------------- |
| Lingua | `magento info:language:list` |
| Valuta | `magento info:currency:list` |
| Fuso orario | `magento info:timezone:list` |

>[!NOTE]
>
>Se durante l&#39;esecuzione di questi comandi viene visualizzato un errore, verificare di aver aggiornato le dipendenze di installazione come descritto in [Aggiorna dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installa dalla riga di comando

Il comando install utilizza il seguente formato:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

Nelle tabelle seguenti vengono descritti i nomi e i valori delle opzioni di installazione, ad esempio i comandi di installazione. Vedi [Esempi di installazioni localhost](#sample-localhost-installations).

>[!NOTE]
>
>Le opzioni contenenti spazi o caratteri speciali devono essere racchiuse tra virgolette singole o doppie.

**Credenziali amministratore:**

Le opzioni seguenti specificano le informazioni utente e le credenziali per l’utente amministratore.

In Adobe Commerce versione 2.2.8 e successive, puoi creare l’utente amministratore durante o dopo l’installazione. Se crei l’utente durante l’installazione, sono necessarie tutte le variabili delle credenziali amministratore. Vedi [Esempi di installazioni localhost](#sample-localhost-installations).

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--admin-firstname` | Nome dell&#39;utente amministratore. | Sì |
| `--admin-lastname` | Cognome dell&#39;utente amministratore. | Sì |
| `--admin-email` | Indirizzo di posta elettronica dell&#39;utente amministratore. | Sì |
| `--admin-user` | Nome utente amministratore. | Sì |
| `--admin-password` | Password utente amministratore. La password deve contenere almeno 7 caratteri e includere almeno un carattere alfabetico e almeno un carattere numerico. Consigliamo una password più lunga e complessa. Racchiudere l&#39;intera stringa della password tra virgolette singole. Ad esempio: `--admin-password='A0b9%t3g'` | Sì |

**Opzioni di configurazione del sito e del database:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--base-url` | URL di base da utilizzare per accedere all&#39;amministratore e alla vetrina in uno dei seguenti formati:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** lo schema (http:// o https://) e una barra finale sono entrambi obbligatori.<br><br>`<your install dir>` è il percorso relativo alla directory principale dei documenti in cui installare l&#39;applicazione. A seconda della configurazione del server web e degli host virtuali, il percorso potrebbe essere magento2 o vuoto.<br><br>Per accedere all&#39;applicazione su localhost, è possibile utilizzare `http://127.0.0.1/<your install dir>/` o `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` che rappresenta un URL di base definito da un&#39;impostazione host virtuale o da un ambiente di virtualizzazione come Docker. Ad esempio, se imposti un host virtuale con il nome host commerce.example.com, puoi installare l&#39;applicazione con `--base-url={{base_url}}` e accedere all&#39;amministratore con un URL come `http://commerce.example.com/admin`. | Sì |
| `--backend-frontname` | URI (Uniform Resource Identifier) per accedere all&#39;amministratore. È possibile omettere questo parametro per consentire all&#39;applicazione di generare un URI casuale con il seguente pattern <code>admin_jkhgdfq</code>.<br><br>È consigliabile utilizzare un URI casuale per motivi di sicurezza. Un URI casuale è più difficile da sfruttare per gli hacker o per il software dannoso.<br><br>L&#39;URI viene visualizzato alla fine dell&#39;installazione. È possibile visualizzarlo in un secondo momento utilizzando il comando `magento info:adminuri`.<br><br>Se scegli di immettere un valore, ti consigliamo di non usare una parola comune come admin, backend. L&#39;URI amministratore può contenere solo valori alfanumerici e il carattere di sottolineatura (`_`). | No |
| `--db-host` | Utilizzare uno dei seguenti elementi:<br><br>- Nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (impostazione predefinita) o `127.0.0.1` se il server di database si trova sullo stesso host del server Web.localhost significa che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa in modo che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, consulta la [documentazione PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** è possibile specificare la porta del server di database nel nome host, ad esempio www.example.com:9000 | Sì |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle di database.<br><br>Il valore predefinito è `magento2`. | Sì |
| `--db-user` | Nome utente del proprietario dell&#39;istanza di database.<br><br>Il valore predefinito è `root`. | Sì |
| `--db-password` | Password del proprietario dell&#39;istanza di database. | Sì |
| `--db-prefix` | Da utilizzare solo se si installano le tabelle di database in un&#39;istanza di database in cui sono già presenti tabelle Adobe Commerce.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione. Alcuni clienti hanno più di un’istanza di Adobe Commerce in esecuzione su un server con tutte le tabelle nello stesso database.<br><br>La lunghezza del prefisso non può superare i cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più installazioni. | No |
| `--db-ssl-key` | Percorso della chiave client. | No |
| `--db-ssl-cert` | Percorso del certificato client. | No |
| `--db-ssl-ca` | Percorso del certificato del server. | No |
| `--language` | Codice lingua da utilizzare nell’amministrazione e nella vetrina. Se non lo hai già fatto, puoi visualizzare l&#39;elenco dei codici di lingua immettendo `magento info:language:list` dalla directory bin. | No |
| `--currency` | Valuta predefinita da utilizzare nella vetrina. Se non lo hai già fatto, puoi visualizzare l&#39;elenco delle valute immettendo `magento info:currency:list` dalla directory bin. | No |
| `--timezone` | Fuso orario predefinito da utilizzare in Admin e storefront. Se non lo hai già fatto, puoi visualizzare l&#39;elenco dei fusi orari immettendo `magento info:timezone:list` dalla directory bin. | No |
| `--use-rewrites` | `1` significa che si utilizza il server Web per riscrivere i collegamenti generati nella vetrina e in Amministrazione.<br><br>`0` disabilita l&#39;utilizzo delle riscritture del server Web. Questa è l&#39;impostazione predefinita. | No |
| `--use-secure` | `1` consente l&#39;utilizzo di Secure Sockets Layer (SSL) negli URL della vetrina. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` disabilita l&#39;utilizzo di SSL. In questo caso, anche tutte le altre opzioni URL protetto sono impostate su 0. Questa è l&#39;impostazione predefinita. | No |
| `--base-url-secure` | URL di base sicuro da utilizzare per accedere all&#39;amministratore e alla vetrina nel seguente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa che si utilizza SSL per accedere all&#39;amministratore. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` significa che non utilizzi SSL con l&#39;amministratore. Questa è l&#39;impostazione predefinita. | No |
| `--admin-use-security-key` | 1 fa in modo che l’applicazione utilizzi un valore chiave generato in modo casuale per accedere alle pagine in Admin e nei moduli. Questi valori chiave aiutano a prevenire attacchi di tipo cross-site script forgery. Questa è l&#39;impostazione predefinita.<br><br>`0` disabilita l&#39;utilizzo della chiave. | No |
| `--session-save` | Utilizzare uno dei seguenti elementi:<br><br>- `db` per archiviare i dati della sessione nel database. Se si dispone di un database in cluster, scegliere l&#39;archiviazione del database. In caso contrario, l&#39;archiviazione basata su file potrebbe non offrire molti vantaggi.<br><br>- `files` per archiviare i dati della sessione nel file system. L&#39;archiviazione delle sessioni basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o che si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per archiviare i dati della sessione in Redis. Se utilizzi Redis per il caching predefinito o delle pagine, Redis deve essere già installato. Per ulteriori informazioni sulla configurazione del supporto per Redis, consulta Utilizzare Redis per l’archiviazione delle sessioni. | No |
| `--key` | Se disponibile, specificare una chiave per crittografare i dati sensibili nel database. Se non ne hai uno, l’applicazione ne genera uno per te. | Sì |
| `--cleanup-database` | Per eliminare le tabelle di database prima di installare l&#39;applicazione, specificare questo parametro senza un valore. In caso contrario, il database viene lasciato intatto. | No |
| `--db-init-statements` | Parametro di configurazione MySQL avanzato. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL. Consultate un riferimento simile a questo prima di impostare qualsiasi valore.<br><br>Il valore predefinito è `SET NAMES utf8;`. | No |
| `--sales-order-increment-prefix` | Specificare un valore stringa da utilizzare come prefisso per gli ordini cliente. In genere, viene utilizzato per garantire numeri di ordine univoci per gli elaboratori dei pagamenti. | No |

>[!TIP]
>
>Per abilitare i servizi di archiviazione remota durante l&#39;installazione, vedere [Configurare Archiviazione remota](../../configuration/remote-storage/remote-storage.md) nella _Guida alla configurazione_.

**Opzioni di configurazione del motore di ricerca:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--search-engine` | Versione del motore di ricerca. I valori possibili sono `elasticsearch7`, `elasticsearch6` e `elasticsearch5`. Il valore predefinito è `elasticsearch7`. Se OpenSearch è stato installato come motore di ricerca, specificare il valore `elasticsearch7`. L&#39;Elasticsearch 5 è stato dichiarato obsoleto e non è consigliato. | No |
| `--elasticsearch-host` | Il nome host o l’indirizzo IP in cui è in esecuzione il motore di ricerca. Il valore predefinito è `localhost`. | No |
| `--elasticsearch-port` | Porta per le richieste HTTP in ingresso. Il valore predefinito è `9200`. | No |
| `--elasticsearch-index-prefix` | Prefisso che identifica l&#39;indice di ricerca. Il valore predefinito è `magento2`. | No |
| `--elasticsearch-timeout` | Il numero di secondi prima del timeout del sistema. Il valore predefinito è `15`. | No |
| `--elasticsearch-enable-auth` | Abilita l&#39;autenticazione sul server del motore di ricerca. Il valore predefinito è `false`. | No |
| `--elasticsearch-username` | ID utente da autenticare | No, a meno che l&#39;autenticazione non sia abilitata |
| `--elasticsearch-password` | Password per l&#39;autenticazione | No, a meno che l&#39;autenticazione non sia abilitata |

**[!DNL RabbitMQ]opzioni di configurazione:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--amqp-host` | Non utilizzare le opzioni `--amqp` a meno che non sia già stata impostata un&#39;installazione di [!DNL RabbitMQ]. Per ulteriori informazioni sull&#39;installazione e la configurazione di [!DNL RabbitMQ], vedere Installazione di [!DNL RabbitMQ].<br><br>Il nome host in cui è installato [!DNL RabbitMQ]. | No |
| `--amqp-port` | Porta da utilizzare per la connessione a [!DNL RabbitMQ]. Il valore predefinito è 5672. | No |
| `--amqp-user` | Nome utente per la connessione a [!DNL RabbitMQ]. Non utilizzare l&#39;utente predefinito `guest`. | No |
| `--amqp-password` | Password per la connessione a [!DNL RabbitMQ]. Non utilizzare la password predefinita `guest`. | No |
| `--amqp-virtualhost` | Host virtuale per la connessione a [!DNL RabbitMQ]. Il valore predefinito è `/`. | No |
| `--amqp-ssl` | Indica se connettersi a [!DNL RabbitMQ]. Il valore predefinito è `false`. Per informazioni sulla configurazione di SSL per [!DNL RabbitMQ], vedere [!DNL RabbitMQ]. | No |
| `--consumers-wait-for-messages` | I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No | No |

**Opzioni di archiviazione remota:**

| Nome | Descrizione | Obbligatorio |
|--- |--- |--- |
| `remote-storage-driver` | Nome scheda<br>Valori possibili:<br>**file**: disabilita l&#39;archiviazione remota e utilizza il file system locale <br>**aws-s3**: utilizza il [servizio Amazon Simple Storage (Amazon S3)](https://aws.amazon.com/s3/) | No |
| `remote-storage-bucket` | Archiviazione oggetto o nome contenitore | No |
| `remote-storage-prefix` | Prefisso facoltativo (posizione all&#39;interno dell&#39;archivio oggetti) | No |
| `remote-storage-region` | Nome regione | No |
| `remote-storage-key` | Chiave di accesso opzionale | No |
| `remote-storage-secret` | Chiave segreta opzionale | No |

**Blocca opzioni di configurazione:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--lock-provider` | Blocca nome provider.<br><br>Provider di blocchi disponibili: `db`, `zookeeper`, `file`.<br><br>Provider di blocchi predefinito: `db` | No |
| `--lock-db-prefix` | Prefisso db specifico per evitare conflitti di blocco quando si utilizza il provider di blocchi `db`.<br><br>Valore predefinito: `NULL` | No |
| `--lock-zookeeper-host` | Host e porta per la connessione al cluster Zookeeper quando si utilizza il provider di blocchi `zookeeper`.<br><br>Esempio: `127.0.0.1:2181` | Sì, se si imposta `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Percorso in cui Zookeeper salva i blocchi.<br><br>Percorso predefinito: `/magento/locks` | No |
| `--lock-file-path` | Percorso in cui vengono salvati i blocchi di file. | Sì, se si imposta `--lock-provider=file` |

**Opzioni di configurazione consumer:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Per attivare o disattivare i moduli dopo l&#39;installazione dell&#39;applicazione, vedere [Attivare e disattivare i moduli](manage-modules.md).

**Dati sensibili:**

{{$include /help/_includes/sensitive-data.md}}

### Esempi di installazioni localhost

Gli esempi seguenti mostrano i comandi per installare Adobe Commerce localmente con varie opzioni.

#### Esempio 1: installazione di base con account utente amministratore

L&#39;esempio seguente installa l&#39;applicazione con le opzioni seguenti:

* L&#39;applicazione è installata nella directory `magento2` relativa alla directory principale dei documenti del server Web in `localhost` e il percorso dell&#39;amministratore è `admin`. Pertanto:

  L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

  Il nome del database è `magento` e il nome utente e la password sono entrambi `magento`

* Utilizza le riscritture del server

* L’amministratore dispone delle seguenti proprietà:

   * Il nome e il cognome sono `Commerce User`
   * Nome utente: `admin`, password: `admin123`
   * Indirizzo di posta elettronica: `user@example.com`

* La lingua predefinita è `en_US` (inglese americano)
* La valuta predefinita è il dollaro statunitense
* Il fuso orario predefinito è Stati Uniti centrali (America/Chicago)
* L&#39;Elasticsearch 7 è installato su `es-host.example.com` e si connette alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Messaggi simili alla seguente visualizzazione per indicare un&#39;installazione riuscita:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Esempio 2: installazione di base senza account utente amministratore

È possibile installare l&#39;applicazione senza creare l&#39;utente amministratore, come illustrato nell&#39;esempio seguente.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Se l’installazione ha esito positivo, vengono visualizzati messaggi come i seguenti:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Dopo l&#39;installazione è possibile creare un utente amministratore utilizzando il comando `admin:user:create`:
[Creare o modificare un amministratore](admin.md#create-or-edit-an-administrator)

#### Esempio 3 - Installazione con opzioni aggiuntive

L&#39;esempio seguente installa l&#39;applicazione con le opzioni seguenti:

* Magapplication è installato nella directory `magento2` relativa alla directory principale dei documenti del server Web in `localhost` e il percorso dell&#39;amministratore è `admin`. Pertanto:

  L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

  Il nome del database è `magento` e il nome utente e la password sono entrambi `magento`

* L’amministratore dispone delle seguenti proprietà:

   * Il nome e il cognome sono `Commerce User`
   * Nome utente: `admin`, password: `admin123`
   * Indirizzo di posta elettronica: `user@example.com`

* La lingua predefinita è `en_US` (inglese americano)
* La valuta predefinita è il dollaro statunitense
* Il fuso orario predefinito è Stati Uniti centrali (America/Chicago)
* Il programma di installazione pulisce il database prima di installare le tabelle e lo schema
* Si utilizza un prefisso di incremento dell&#39;ordine cliente `ORD$` (poiché contiene un carattere speciale [`$`], il valore deve essere racchiuso tra virgolette)
* I dati della sessione vengono salvati nel database
* Utilizza le riscritture del server
* L&#39;Elasticsearch 7 è installato su `es-host.example.com` e si connette alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>È necessario immettere il comando su una sola riga oppure, come nell&#39;esempio precedente, con un carattere `\` alla fine di ogni riga.

Se l’installazione ha esito positivo, vengono visualizzati messaggi come i seguenti:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>Se disponi di un account utente per accedere al server applicazioni, vedi [impostare un umask](../next-steps/set-umask.md). Questo tipo di configurazione è tipico per l&#39;hosting condiviso.

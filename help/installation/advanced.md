---
title: Installazione on-premise avanzata
description: Scopri gli scenari di installazione avanzata per le distribuzioni Adobe Commerce on-premise. Scopri configurazioni complesse e opzioni di configurazione personalizzate.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 937db2209ec4122c611a857796f043523a0acb29
workflow-type: tm+mt
source-wordcount: '2485'
ht-degree: 0%

---

# Installazione on-premise avanzata

>[!TIP]
>
>Perso? Hai bisogno di aiuto? Prova le [guide all&#39;installazione rapida](composer.md) o [all&#39;installazione collaboratore](https://developer.adobe.com/commerce/contributor/guides/install/).

>[!NOTE]
>
>Se hai scelto di abilitare SELinux, consulta [SELinux e iptables](prerequisites/security.md).

## Interfaccia della riga di comando (CLI)

Adobe Commerce dispone di un&#39;unica interfaccia della riga di comando per le attività di installazione e configurazione: `<magento_root>/bin/magento`. L’interfaccia esegue più attività, tra cui:

* Installazione (e attività correlate, come la creazione o l’aggiornamento dello schema del database e la creazione della configurazione di distribuzione).
* Cancellazione della cache.
* Gestione degli indici, inclusa la reindicizzazione.
* Creazione di dizionari e pacchetti di traduzione.
* Generazione di classi inesistenti, ad esempio factory e intercettori per i plug-in, che generano la configurazione dell&#39;iniezione di dipendenza per il gestore di oggetti.
* Distribuzione di file di visualizzazione statica.
* Creazione di CSS da Less.

Altre prestazioni:

* Un singolo comando (`<magento_root>/bin/magento list`) elenca tutti i comandi di installazione e configurazione disponibili.
* Interfaccia utente coerente basata su Symfony.
* La CLI è estensibile in modo che sviluppatori di terze parti possano collegarla. Questo ha il vantaggio aggiuntivo di eliminare la curva di apprendimento degli utenti.
* I comandi per i moduli disattivati non vengono visualizzati.

In questo argomento viene illustrata l&#39;installazione del software Adobe Commerce mediante CLI. Per informazioni sulla configurazione, vedere la [Guida alla configurazione](../configuration/overview.md).

Il programma di installazione può essere eseguito più volte, se necessario, in modo da:

* Immetti valori diversi

  Ad esempio, dopo aver configurato il server Web per Secure Sockets Layer (SSL), è possibile eseguire il programma di installazione per impostare le opzioni SSL.

* Correggere gli errori nelle installazioni precedenti
* Installare Adobe Commerce in un’istanza di database diversa

## Prima di avviare l’installazione

Prima di iniziare, completa i passaggi seguenti:

* Verificare che il sistema soddisfi i requisiti descritti in [requisiti di sistema](system-requirements.md).

* Completa tutte le [attività prerequisite](prerequisites/overview.md).

* Completare i primi passaggi di installazione. Vedi [il tuo percorso di installazione o aggiornamento](overview.md).

* Dopo aver effettuato l&#39;accesso al server applicazioni, [passare al proprietario del file system](prerequisites/file-system/overview.md).

* Rivedi la panoramica di [installazione rapida](composer.md).

>[!NOTE]
>
>È necessario installare Adobe Commerce dalla sottodirectory `bin`.

È possibile eseguire il programma di installazione più volte con diverse opzioni per completare attività di installazione come le seguenti:

* Eseguire l&#39;installazione in più fasi: ad esempio, dopo aver configurato il server Web per Secure Sockets Layer (SSL), è possibile eseguire di nuovo il programma di installazione per impostare le opzioni SSL.

* Correggere gli errori nelle installazioni precedenti.

* Installa Adobe Commerce in un’istanza di database diversa.

>[!NOTE]
>
>Per impostazione predefinita, il programma di installazione non sovrascrive il database se si installa il software nella stessa istanza di database. È possibile utilizzare il parametro facoltativo `cleanup-database` per modificare questo comportamento.

Vedere anche [Aggiorna, reinstalla, disinstalla](tutorials/uninstall.md).

### Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Comandi della Guida del programma di installazione

È possibile eseguire i seguenti comandi per trovare i valori per alcuni argomenti obbligatori:

| Argomento del programma di installazione | Comando |
| ------------------ | ------------------------------- |
| Lingua | `bin/magento info:language:list` |
| Valuta | `bin/magento info:currency:list` |
| Fuso orario | `bin/magento info:timezone:list` |

>[!NOTE]
>
>Se durante l&#39;esecuzione di questi comandi viene visualizzato un errore, verificare di aver aggiornato le dipendenze di installazione come descritto in [Aggiorna dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## Installa dalla riga di comando

Il comando install utilizza il seguente formato:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

Nelle tabelle seguenti vengono descritti i nomi e i valori delle opzioni di installazione. Per i comandi di installazione, vedere [Esempi di installazioni localhost](#sample-localhost-installations).

>[!NOTE]
>
>Le opzioni contenenti spazi o caratteri speciali devono essere racchiuse tra virgolette singole o doppie.

**Credenziali amministratore:**

Le opzioni seguenti specificano le informazioni utente e le credenziali per l’utente amministratore.

Puoi creare l’utente amministratore durante o dopo l’installazione. Se crei l’utente durante l’installazione, sono necessarie tutte le variabili delle credenziali amministratore. Vedi [Esempi di installazioni localhost](#sample-localhost-installations).

Nelle tabelle seguenti sono disponibili molti parametri di installazione, ma non tutti. Per un elenco completo, vedere [Riferimento agli strumenti della riga di comando](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/cli-reference/commerce-on-premises).

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
| `--base-url` | URL di base da utilizzare per accedere all&#39;amministratore e alla vetrina in uno dei seguenti formati:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** lo schema (http:// o https://) e una barra finale sono entrambi obbligatori.<br><br>`<your install dir>` è il percorso relativo alla directory principale dei documenti in cui installare il software Adobe Commerce. A seconda della configurazione del server web e degli host virtuali, il percorso potrebbe essere magento2 o vuoto.<br><br>Per accedere ad Adobe Commerce o MagenAdobe Commerceutilizzare `http://127.0.0.1/<your install dir>/` o `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` che rappresenta un URL di base definito da un&#39;impostazione host virtuale o da un ambiente di virtualizzazione come Docker. Se ad esempio si configura un host virtuale con il nome host `magento.example.com`, è possibile installare il software con `--base-url={{base_url}}` e accedere all&#39;amministratore con un URL come `http://magento.example.com/admin`. | Sì |
| `--backend-frontname` | URI (Uniform Resource Identifier) per accedere all&#39;amministratore. È possibile omettere questo parametro per consentire all&#39;applicazione di generare un URI casuale con il seguente pattern <code>admin_jkhgdfq</code>.<br><br>È consigliabile utilizzare un URI casuale per motivi di sicurezza. Un URI casuale è più difficile da sfruttare per gli hacker o per il software dannoso.<br><br>L&#39;URI viene visualizzato alla fine dell&#39;installazione. È possibile visualizzarlo in un secondo momento utilizzando il comando `bin/magento info:adminuri`.<br><br>Se scegli di immettere un valore, ti consigliamo di non usare una parola comune come admin, backend. L&#39;URI amministratore può contenere solo valori alfanumerici e il carattere di sottolineatura (`_`). | No |
| `--db-host` | Utilizzare uno dei seguenti elementi:<br><br>- Nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (impostazione predefinita) o `127.0.0.1` se il server di database si trova sullo stesso host del server Web.localhost significa che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa in modo che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, consulta la [documentazione PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** è possibile specificare facoltativamente la porta del server di database nel relativo nome host, ad esempio www.example.com:9000 | Sì |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle di database.<br><br>Il valore predefinito è `magento2`. | Sì |
| `--db-user` | Nome utente del proprietario dell&#39;istanza di database.<br><br>Il valore predefinito è `root`. | Sì |
| `--db-password` | Password del proprietario dell&#39;istanza di database. | Sì |
| `--db-prefix` | Da utilizzare solo se si installano le tabelle di database in un&#39;istanza di database in cui sono già presenti tabelle Adobe Commerce.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione. Alcuni clienti hanno più di un Adobe Commerce Commerceserver o MagenAdobe Commerceserver con tutte le tabelle nello stesso database.<br><br>La lunghezza del prefisso non può superare i cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più installazioni di Adobe Commerce |
| `--db-ssl-key` | Percorso della chiave client. | No |
| `--db-ssl-cert` | Percorso del certificato client. | No |
| `--db-ssl-ca` | Percorso del certificato del server. | No |
| `--language` | Codice lingua da utilizzare nell’amministrazione e nella vetrina. Se non lo hai già fatto, puoi visualizzare l&#39;elenco dei codici di lingua immettendo `bin/magento info:language:list` dalla directory bin. | No |
| `--currency` | Valuta predefinita da utilizzare nella vetrina. Se non lo hai già fatto, puoi visualizzare l&#39;elenco delle valute immettendo `bin/magento info:currency:list` dalla directory bin. | No |
| `--timezone` | Fuso orario predefinito da utilizzare in Admin e storefront. Se non lo hai già fatto, puoi visualizzare l&#39;elenco dei fusi orari immettendo `bin/magento info:timezone:list` dalla directory `bin/`. | No |
| `--use-rewrites` | `1` significa che si utilizza il server Web per riscrivere i collegamenti generati nella vetrina e in Amministrazione.<br><br>`0` disabilita l&#39;utilizzo delle riscritture del server Web. Questa è l&#39;impostazione predefinita. | No |
| `--use-secure` | `1` consente l&#39;utilizzo di Secure Sockets Layer (SSL) negli URL della vetrina. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` disabilita l&#39;utilizzo di SSL. In questo caso, anche tutte le altre opzioni URL protetto sono impostate su 0. Questa è l&#39;impostazione predefinita. | No |
| `--base-url-secure` | URL di base sicuro da utilizzare per accedere all&#39;amministratore e alla vetrina nel seguente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa che si utilizza SSL per accedere all&#39;amministratore. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` significa che non utilizzi SSL con l&#39;amministratore. Questa è l&#39;impostazione predefinita. | No |
| `--admin-use-security-key` | 1 fa in modo che l’applicazione utilizzi un valore chiave generato in modo casuale per accedere alle pagine in Admin e nei moduli. Questi valori chiave aiutano a prevenire attacchi di tipo cross-site script forgery. Questa è l&#39;impostazione predefinita.<br><br>`0` disabilita l&#39;utilizzo della chiave. | No |
| `--session-save` | Utilizzare uno dei seguenti elementi:<br><br>- `db` per archiviare i dati della sessione nel database. Se si dispone di un database in cluster, scegliere l&#39;archiviazione del database. In caso contrario, l&#39;archiviazione basata su file potrebbe non offrire molti vantaggi.<br><br>- `files` per archiviare i dati della sessione nel file system. L&#39;archiviazione delle sessioni basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o che si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per archiviare i dati della sessione in Redis. Se utilizzi Redis per il caching predefinito o delle pagine, Redis deve essere già installato. Per ulteriori informazioni sulla configurazione del supporto per Redis, consulta Utilizzare Redis per l’archiviazione delle sessioni. | No |
| `--key` | Se disponibile, specificare una chiave per crittografare i dati sensibili nel database. Se non ne hai uno, l’applicazione ne genera uno per te. | Sì |
| `--cleanup-database` | Per eliminare le tabelle di database prima di installare Adobe Commerce, specifica questo parametro senza un valore. In caso contrario, il database viene lasciato intatto. | No |
| `--db-init-statements` | Parametro di configurazione MySQL avanzato. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL. Consultate un riferimento simile a questo prima di impostare qualsiasi valore.<br><br>Il valore predefinito è `SET NAMES utf8;`. | No |
| `--sales-order-increment-prefix` | Specificare un valore stringa da utilizzare come prefisso per gli ordini cliente. In genere, viene utilizzato per garantire numeri di ordine univoci per gli elaboratori dei pagamenti. | No |

**Opzioni di configurazione del motore di ricerca:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--search-engine` | Versione di Elasticsearch o OpenSearch da utilizzare come motore di ricerca. Il valore predefinito è `elasticsearch7`. Elasticsearch 5 è stato dichiarato obsoleto e non è consigliato. | No |
| `--elasticsearch-host` | Il nome host o l’indirizzo IP in cui Elasticsearch è in esecuzione. Il valore predefinito è `localhost`. | No |
| `--elasticsearch-port` | Porta Elasticsearch per le richieste HTTP in ingresso. Il valore predefinito è `9200`. | No |
| `--elasticsearch-index-prefix` | Prefisso che identifica l’indice di ricerca di Elasticsearch. Il valore predefinito è `magento2`. | No |
| `--elasticsearch-timeout` | Il numero di secondi prima del timeout del sistema. Il valore predefinito è `15`. | No |
| `--elasticsearch-enable-auth` | Abilita l’autenticazione sul server Elasticsearch. Il valore predefinito è `false`. | No |
| `--elasticsearch-username` | ID utente per l’autenticazione al server Elasticsearch. | No, a meno che l&#39;autenticazione non sia abilitata |
| `--elasticsearch-password` | Password per l&#39;autenticazione in Elasticsearchserver. | No, a meno che l&#39;autenticazione non sia abilitata |
| `--opensearch-host` | Nome host o indirizzo IP in cui è in esecuzione OpenSearch. Il valore predefinito è `localhost`. | No |
| `--opensearch-port` | La porta OpenSearch per le richieste HTTP in ingresso. Il valore predefinito è `9200`. | No |
| `--opensearch-index-prefix` | Prefisso che identifica l&#39;indice di ricerca OpenSearch. Il valore predefinito è `magento2`. | No |
| `--opensearch-timeout` | Il numero di secondi prima del timeout del sistema. Il valore predefinito è `15`. | No |
| `--opensearch-enable-auth` | Abilita l&#39;autenticazione sul server OpenSearch. Il valore predefinito è `false`. | No |
| `--opensearch-username` | ID utente da autenticare nel server OpenSearch. | No, a meno che l&#39;autenticazione non sia abilitata |
| `--opensearch-password` | Password per l&#39;autenticazione nel server OpenSearch. | No, a meno che l&#39;autenticazione non sia abilitata |

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

**Opzioni di configurazione di ActiveMQ Artemis:**

>[!NOTE]
>
>ActiveMQ Artemis è stato introdotto in Adobe Commerce 2.4.6 e versioni successive.

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--stomp-host` | Non utilizzare le opzioni `--stomp` a meno che non sia già stata impostata un&#39;installazione di ActiveMQ Artemis. Per ulteriori informazioni sull&#39;installazione e la configurazione di ActiveMQ Artemis, vedere Installazione di ActiveMQ Artemis.<br><br>Il nome host in cui è installato ActiveMQ Artemis. | No |
| `--stomp-port` | Porta da utilizzare per la connessione ad ActiveMQ Artemis. Il valore predefinito è 61613. | No |
| `--stomp-user` | Nome utente per la connessione ad ActiveMQ Artemis. Non utilizzare l&#39;utente predefinito `artemis`. | No |
| `--stomp-password` | Password per la connessione ad ActiveMQ Artemis. Non utilizzare la password predefinita `artemis`. | No |
| `--stomp-ssl` | Indica se connettersi ad ActiveMQ Artemis utilizzando SSL. Il valore predefinito è `false`. Vedere ActiveMQ Artemis per informazioni sulla configurazione di SSL per ActiveMQ Artemis. | No |
| `--consumers-wait-for-messages` | I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No | No |

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
>Per attivare o disattivare i moduli dopo l&#39;installazione di Adobe Commerce, vedere [Attivare e disattivare i moduli](tutorials/manage-modules.md).

**Dati sensibili:**

{{$include /help/_includes/sensitive-data.md}}

### Esempi di installazioni localhost

Gli esempi seguenti mostrano i comandi per installare Adobe Commerce localmente con varie opzioni.

#### Esempio 1: installazione di base con account utente amministratore

L’esempio seguente installa Adobe Commerce con le seguenti opzioni:

* L&#39;applicazione è installata nella directory `magento2` relativa alla directory principale dei documenti del server Web in `localhost` e il percorso dell&#39;amministratore è `admin`. Pertanto:

  L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

  Il nome del database è `magento` e il nome utente e la password sono entrambi `magento`

* Utilizza le riscritture del server

* L’amministratore dispone delle seguenti proprietà:

   * Il nome e il cognome sono `Magento User`
   * Nome utente: `admin`, password: `admin123`
   * Indirizzo di posta elettronica: `user@example.com`

* La lingua predefinita è `en_US` (inglese americano)
* La valuta predefinita è il dollaro statunitense
* Il fuso orario predefinito è Stati Uniti centrali (America/Chicago)
* OpenSearch 1.2 è installato su `os-host.example.com` e si connette alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Messaggi simili alla seguente visualizzazione per indicare un&#39;installazione riuscita:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Esempio 2: installazione di base senza account utente amministratore

È possibile installare Adobe Commerce senza creare l’utente amministratore, come illustrato nell’esempio seguente.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Se l’installazione ha esito positivo, vengono visualizzati messaggi come i seguenti:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Dopo l&#39;installazione è possibile creare un utente amministratore utilizzando il comando `admin:user:create`:
[Creare o modificare un amministratore](tutorials/admin.md#create-or-edit-an-administrator)

#### Esempio 3 - Installazione con opzioni aggiuntive

L’esempio seguente installa Adobe Commerce con le seguenti opzioni:

* L&#39;applicazione è installata nella directory `magento2` relativa alla directory principale dei documenti del server Web in `localhost` e il percorso dell&#39;amministratore è `admin`. Pertanto:

  L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

  Il nome del database è `magento` e il nome utente e la password sono entrambi `magento`

* L’amministratore dispone delle seguenti proprietà:

   * Il nome e il cognome sono `Magento User`
   * Nome utente: `admin`, password: `admin123`
   * Indirizzo di posta elettronica: `user@example.com`

* La lingua predefinita è `en_US` (inglese americano)
* La valuta predefinita è il dollaro statunitense
* Il fuso orario predefinito è Stati Uniti centrali (America/Chicago)
* Il programma di installazione pulisce il database prima di installare le tabelle e lo schema
* È possibile utilizzare il prefisso di incremento dell&#39;ordine cliente `ORD$` (poiché contiene un carattere speciale [`$`], il valore deve essere racchiuso tra virgolette doppie)
* I dati della sessione vengono salvati nel database
* Utilizza le riscritture del server
* OpenSearch è installato su `os-host.example.com` e si connette alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>È necessario immettere il comando su una sola riga oppure, come nell&#39;esempio precedente, con un carattere `\` alla fine di ogni riga.

Se l’installazione ha esito positivo, vengono visualizzati messaggi come i seguenti:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Esempio 4: installazione con ActiveMQ Artemis

Nell&#39;esempio seguente viene illustrato come installare Adobe Commerce con ActiveMQ Artemis come gestore di messaggi:

```bash
bin/magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>L&#39;installazione di ActiveMQ Artemis richiede Adobe Commerce 2.4.6 o versione successiva.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->

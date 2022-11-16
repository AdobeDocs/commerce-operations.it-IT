---
title: Installazione on-premise avanzata
description: Scopri gli scenari di installazione avanzati per Adobe Commerce o Magento Open Source sull’infrastruttura di tua proprietà.
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '2327'
ht-degree: 0%

---


# Installazione on-premise avanzata

>[!TIP]
>
>Perso? Ti serve una mano? Prova la nostra [Installazione rapida](composer.md) o [Installazione collaboratore](https://developer.adobe.com/commerce/contributor/guides/install/) guide.

>[!NOTE]
>
>Se hai scelto di abilitare SELinux, vedi [SELinux e tabelle](prerequisites/security.md).

## Interfaccia della riga di comando (CLI)

Adobe Commerce e Magenti Open Source dispongono di un&#39;unica interfaccia a riga di comando per le attività di installazione e configurazione: `<magento_root>/bin/magento`. L’interfaccia esegue più attività, tra cui:

* Installazione (e attività correlate, ad esempio creazione o aggiornamento dello schema del database, creazione della configurazione di distribuzione).
* Cancellazione della cache.
* Gestione degli indici, inclusa la reindicizzazione.
* Creazione di dizionari di traduzione e pacchetti di traduzione.
* Generazione di classi inesistenti, ad esempio fabbriche e intercettori per i plug-in, generando la configurazione dell&#39;iniezione di dipendenza per il gestore oggetti.
* Distribuzione di file di visualizzazione statici.
* Creazione di CSS da Less.

Altri vantaggi:

* Un singolo comando (`<magento_root>/bin/magento list`) elenca tutti i comandi di installazione e configurazione disponibili.
* Interfaccia utente coerente basata su Symfony.
* La CLI è estensibile in modo che gli sviluppatori di terze parti possano &quot;plug-in&quot; ad essa. Questo ha il vantaggio aggiuntivo di eliminare la curva di apprendimento degli utenti.
* I comandi per i moduli disabilitati non vengono visualizzati.

Questo argomento illustra l’installazione del software Adobe Commerce o Magenti Open Source tramite CLI. Per informazioni sulla configurazione, consulta la sezione [Guida alla configurazione](../configuration/overview.md).

Il programma di installazione può essere eseguito più volte, se necessario, in modo da:

* Fornire valori diversi

   Ad esempio, dopo aver configurato il server web per Secure Sockets Layer (SSL), puoi eseguire il programma di installazione per impostare le opzioni SSL.

* Errori corretti nelle installazioni precedenti
* Installare Adobe Commerce o Magento Open Source in un’altra istanza di database

## Prima di avviare l&#39;installazione

Prima di iniziare, completa i seguenti passaggi:

* Verifica che il sistema soddisfi i requisiti descritti in [requisiti di sistema](system-requirements.md).

* Completa tutte [prerequisito](prerequisites/overview.md) compiti.

* Completa i primi passaggi di installazione. Vedi [percorso di installazione o aggiornamento](overview.md).

* Dopo aver effettuato l&#39;accesso al server dell&#39;applicazione, [passa al proprietario del file system](prerequisites/file-system/overview.md).

* Consulta la sezione [avvio rapido installazione](composer.md) panoramica.

>[!NOTE]
>
>È necessario installare Adobe Commerce o Magenti Open Source dal `bin` sottodirectory.

È possibile eseguire il programma di installazione più volte con diverse opzioni per completare le attività di installazione come indicato di seguito:

* Installazione in fasi: ad esempio, dopo aver configurato il server web per Secure Sockets Layer (SSL), puoi eseguire nuovamente il programma di installazione per impostare le opzioni SSL.

* Correggere gli errori nelle installazioni precedenti.

* Installa Adobe Commerce o Magento Open Source in un&#39;altra istanza di database.

>[!NOTE]
>
>Per impostazione predefinita, il programma di installazione non sovrascrive il database se si installa il software nella stessa istanza di database. È possibile utilizzare l&#39;opzione `cleanup-database` per modificare questo comportamento.

Vedi anche [Aggiorna, reinstalla, disinstalla](tutorials/uninstall.md).

### Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Comandi dell&#39;Aiuto del programma di installazione

È possibile eseguire i seguenti comandi per trovare i valori per alcuni argomenti obbligatori:

| Argomento del programma di installazione | Comando |
| ------------------ | ------------------------------- |
| Lingua | informazioni bin/magento:language:elenco |
| Valuta | informazioni bin/magento:currency:elenco |
| Fuso orario | informazioni bin/magento:timezone:elenco |

>[!NOTE]
>
>Se durante l&#39;esecuzione di questi comandi viene visualizzato un errore, verificare di aver aggiornato le dipendenze di installazione come descritto in [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installa dalla riga di comando

Il comando di installazione utilizza il formato seguente:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

Le tabelle seguenti descrivono i nomi e i valori delle opzioni di installazione. Ad esempio, i comandi di installazione, vedere [Esempi di installazioni localhost](#sample-localhost-installations).

>[!NOTE]
>
>Tutte le opzioni che contengono spazi o caratteri speciali devono essere racchiuse tra virgolette singole o doppie.

**Credenziali amministratore:**

Le opzioni seguenti specificano le informazioni utente e le credenziali per l&#39;utente amministratore.

Puoi creare l’utente amministratore durante o dopo l’installazione. Se crei l’utente durante l’installazione, sono necessarie tutte le variabili delle credenziali amministratore. Vedi [Esempi di installazioni localhost](#sample-localhost-installations).

Le tabelle seguenti forniscono molti ma non tutti i parametri di installazione disponibili. Per un elenco completo, vedi [Riferimento strumenti riga di comando](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--admin-firstname` | Nome utente amministratore. | Sì |
| `--admin-lastname` | Cognome utente amministratore. | Sì |
| `--admin-email` | Indirizzo e-mail dell&#39;utente amministratore. | Sì |
| `--admin-user` | Nome utente amministratore. | Sì |
| `--admin-password` | Password utente amministratore. La password deve contenere almeno 7 caratteri e deve contenere almeno un carattere alfabetico e almeno un carattere numerico. È consigliabile impostare una password più lunga e complessa. Racchiudere l’intera stringa di password tra virgolette singole. Ad esempio: `--admin-password='A0b9%t3g'` | Sì |

**Opzioni di configurazione del sito e del database:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--base-url` | URL di base da utilizzare per accedere all’amministratore e alla vetrina in uno dei seguenti formati:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** Il sistema (http:// o https://) e una barra finale sono entrambi necessari.<br><br>`<your install dir>` è il percorso relativo al docroot in cui installare il software Adobe Commerce o Magenti Open Source. A seconda della configurazione del server web e degli host virtuali, il percorso potrebbe essere magento2 o vuoto.<br><br>Per accedere ad Adobe Commerce o Magento Open Source su localhost, puoi utilizzare `http://127.0.0.1/<your install dir>/` o `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` che rappresenta un URL di base definito da un&#39;impostazione host virtuale o da un ambiente di virtualizzazione come Docker. Ad esempio, se imposti un host virtuale con il nome host `magento.example.com`, è possibile installare il software con `--base-url={{base_url}}` e accedi all’amministratore con un URL come `http://magento.example.com/admin`. | Sì |
| `--backend-frontname` | URI (Uniform Resource Identifier) per accedere all&#39;amministratore. È possibile omettere questo parametro per consentire all&#39;applicazione di generare un URI casuale con il seguente pattern admin_jkhgdfq</code>.<br><br>Consigliamo un URI casuale a scopo di sicurezza. Un URI casuale è più difficile da sfruttare per gli hacker o software dannoso.<br><br>L’URI viene visualizzato alla fine dell’installazione. Puoi visualizzarlo in un secondo momento utilizzando la `bin/magento info:adminuri` comando.<br><br>Se scegli di immettere un valore, ti consigliamo di non utilizzare una parola comune come admin, backend. L’URI amministratore può contenere valori alfanumerici e il carattere di sottolineatura (`_`). | No |
| `--db-host` | Utilizza una delle seguenti opzioni:<br><br>- Nome host o indirizzo IP completo del server di database.<br><br>- `localhost` (predefinito) o `127.0.0.1` se il server di database si trova sullo stesso host del server web.localhost significa che la libreria client MySQL utilizza socket UNIX per connettersi al database. `127.0.0.1` fa sì che la libreria client utilizzi il protocollo TCP. Per ulteriori informazioni sui socket, consulta la sezione [Documentazione PHP DOP_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Facoltativamente, puoi specificare la porta del server di database nel nome host come www.example.com:9000 | Sì |
| `--db-name` | Nome dell&#39;istanza di database in cui si desidera installare le tabelle del database.<br><br>Il valore predefinito è `magento2`. | Sì |
| `--db-user` | Nome utente del proprietario dell&#39;istanza del database.<br><br>Il valore predefinito è `root`. | Sì |
| `--db-password` | Password del proprietario dell&#39;istanza del database. | Sì |
| `--db-prefix` | Utilizzare solo se si stanno installando le tabelle di database in un&#39;istanza di database che contiene già tabelle di Adobe Commerce o di Magento Open Source.<br><br>In tal caso, utilizzare un prefisso per identificare le tabelle per l&#39;installazione corrente. Alcuni clienti hanno più di un&#39;istanza Adobe Commerce o Magento Open Source in esecuzione su un server con tutte le tabelle nello stesso database.<br><br>Il prefisso può contenere al massimo cinque caratteri. Deve iniziare con una lettera e può includere solo lettere, numeri e caratteri di sottolineatura.<br><br>Questa opzione consente ai clienti di condividere il server di database con più di un’installazione Adobe Commerce o Magenti Open Source. | No |
| `--db-ssl-key` | Percorso della chiave client. | No |
| `--db-ssl-cert` | Percorso del certificato client. | No |
| `--db-ssl-ca` | Percorso del certificato server. | No |
| `--language` | Codice lingua da utilizzare nell’amministrazione e nella vetrina. Se non lo hai già fatto, puoi visualizzare l’elenco dei codici della lingua immettendo `bin/magento info:language:list` dalla directory bin.) | No |
| `--currency` | Valuta predefinita da utilizzare nella vetrina. (Se non lo hai già fatto, puoi visualizzare l&#39;elenco delle valute immettendo `bin/magento info:currency:list` dalla directory bin.) | No |
| `--timezone` | Fuso orario predefinito da utilizzare in Admin e nella vetrina. Se non lo hai già fatto, puoi visualizzare l’elenco dei fusi orari immettendo `bin/magento info:timezone:list` dal `bin/` ). | No |
| `--use-rewrites` | `1` significa che utilizzi le riscritture del server web per i collegamenti generati nella vetrina e nell’amministrazione.<br><br>`0` disabilita l&#39;utilizzo delle riscritture del server web. Questa è l’impostazione predefinita. | No |
| `--use-secure` | `1` abilita l&#39;utilizzo di Secure Sockets Layer (SSL) negli URL di vetrina. Assicurati che il server web supporti SSL prima di selezionare questa opzione.<br><br>`0` disabilita l’utilizzo di SSL. In questo caso, anche tutte le altre opzioni URL sicure vengono considerate pari a 0. Questa è l’impostazione predefinita. | No |
| `--base-url-secure` | URL di base sicuro da utilizzare per accedere all&#39;amministratore e alla vetrina nel seguente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa che utilizzi SSL per accedere all’amministratore. Assicurati che il server web supporti SSL prima di selezionare questa opzione.<br><br>`0` significa che non utilizzi SSL con l’amministratore. Questa è l’impostazione predefinita. | No |
| `--admin-use-security-key` | 1 fa sì che l’applicazione utilizzi un valore chiave generato in modo casuale per accedere alle pagine nell’amministratore e nei moduli. Questi valori chiave consentono di evitare attacchi di falsificazione di script tra siti diversi. Questa è l’impostazione predefinita.<br><br>`0` disabilita l’utilizzo della chiave. | No |
| `--session-save` | Utilizza una delle seguenti opzioni:<br><br>- `db` per memorizzare i dati della sessione nel database. Scegliere l&#39;archiviazione del database se si dispone di un database cluster; in caso contrario, potrebbe non esservi un grande vantaggio rispetto allo storage basato su file.<br><br>- `files` per memorizzare i dati della sessione nel file system. L&#39;archiviazione della sessione basata su file è appropriata a meno che l&#39;accesso al file system non sia lento, che si disponga di un database cluster o si desideri archiviare i dati della sessione in Redis.<br><br>- `redis` per memorizzare i dati della sessione in Redis. Se si utilizza Redis per il caching predefinito o della pagina, Redis deve essere già installato. Per ulteriori informazioni sulla configurazione del supporto per Redis, consulta Utilizzare Redis per l’archiviazione delle sessioni . | No |
| `--key` | Se disponibile, specifica una chiave per crittografare i dati sensibili nel database. Se non ne hai uno, l&#39;applicazione ne genera uno per te. | Sì |
| `--cleanup-database` | Per eliminare le tabelle del database prima di installare Adobe Commerce o Magenti Open Source, specifica questo parametro senza un valore. In caso contrario, il database viene lasciato intatto. | No |
| `--db-init-statements` | Parametro di configurazione avanzato di MySQL. Utilizza le istruzioni di inizializzazione del database da eseguire durante la connessione al database MySQL. Prima di impostare qualsiasi valore, consultare un riferimento simile a questo.<br><br>Il valore predefinito è `SET NAMES utf8;`. | No |
| `--sales-order-increment-prefix` | Specificare un valore stringa da utilizzare come prefisso per gli ordini di vendita. In genere, questo viene utilizzato per garantire numeri di ordine univoci per i processori di pagamento. | No |

**Opzioni di configurazione del motore di ricerca:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--search-engine` | Versione di Elasticsearch o OpenSearch da utilizzare come motore di ricerca. I valori possibili sono `elasticsearch7`, `elasticsearch6`e `elasticsearch5`. Il valore predefinito è `elasticsearch7`. Per utilizzare OpenSearch, specificare `elasticsearch7`. L’Elasticsearch 5 è stato dichiarato obsoleto e non è consigliato. | No |
| `--elasticsearch-host` | Nome host o indirizzo IP in cui è in esecuzione il motore di ricerca. Il valore predefinito è `localhost`. | No |
| `--elasticsearch-port` | La porta per le richieste HTTP in arrivo. Il valore predefinito è `9200`. | No |
| `--elasticsearch-index-prefix` | Prefisso che identifica l&#39;indice del motore di ricerca. Il valore predefinito è `magento2`. | No |
| `--elasticsearch-timeout` | Il numero di secondi prima dell&#39;timeout del sistema. Il valore predefinito è `15`. | No |
| `--elasticsearch-enable-auth` | Abilita l’autenticazione sul server del motore di ricerca. Il valore predefinito è `false`. | No |
| `--elasticsearch-username` | ID utente per l’autenticazione del motore di ricerca | No, a meno che l&#39;autenticazione non sia abilitata |
| `--elasticsearch-password` | Password per l’autenticazione del motore di ricerca | No, a meno che l&#39;autenticazione non sia abilitata |

**[!DNL RabbitMQ]opzioni di configurazione:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--amqp-host` | Non utilizzare il `--amqp` a meno che non sia già stata impostata un&#39;installazione di [!DNL RabbitMQ]. Vedi [!DNL RabbitMQ] installazione per ulteriori informazioni sull&#39;installazione e la configurazione [!DNL RabbitMQ].<br><br>Nome host in cui [!DNL RabbitMQ] è installato. | No |
| `--amqp-port` | Porta a cui connettersi [!DNL RabbitMQ]. Il valore predefinito è 5672. | No |
| `--amqp-user` | Nome utente per la connessione a [!DNL RabbitMQ]. Non utilizzare l&#39;utente predefinito `guest`. | No |
| `--amqp-password` | Password per la connessione a [!DNL RabbitMQ]. Non utilizzare la password predefinita `guest`. | No |
| `--amqp-virtualhost` | Host virtuale per la connessione a [!DNL RabbitMQ]. Il valore predefinito è `/`. | No |
| `--amqp-ssl` | Indica se connettersi a [!DNL RabbitMQ]. Il valore predefinito è `false`. Vedi [!DNL RabbitMQ] per informazioni sulla configurazione di SSL per [!DNL RabbitMQ]. | No |
| `--consumers-wait-for-messages` | I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No | No |

**Blocca opzioni di configurazione:**

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--lock-provider` | Blocca nome provider.<br><br>Provider di blocchi disponibili: `db`, `zookeeper`, `file`.<br><br>Provider di blocco predefinito: `db` | No |
| `--lock-db-prefix` | Prefisso del database specifico per evitare conflitti di blocco quando si utilizza `db` provider di blocco.<br><br>Il valore predefinito: `NULL` | No |
| `--lock-zookeeper-host` | Host e porta per connettersi al cluster Zookeeper quando si utilizza `zookeeper` provider di blocco.<br><br>Ad esempio: `127.0.0.1:2181` | Sì, se si imposta `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Il percorso in cui Zookeeper salva le serrature.<br><br>Il percorso predefinito è: `/magento/locks` | No |
| `--lock-file-path` | Percorso in cui vengono salvati i blocchi di file. | Sì, se si imposta `--lock-provider=file` |

**Opzioni di configurazione dei consumatori:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Per abilitare o disabilitare i moduli dopo aver installato Adobe Commerce o Magenti Open Source, vedi [Abilitare e disabilitare i moduli](tutorials/manage-modules.md).

**Dati sensibili:**

{{$include /help/_includes/sensitive-data.md}}

### Esempi di installazioni localhost

Gli esempi seguenti mostrano i comandi per installare Adobe Commerce localmente con varie opzioni.

#### Esempio 1 - Installazione di base con l&#39;account utente amministratore

L’esempio seguente installa Adobe Commerce o Magenti Open Source con le seguenti opzioni:

* L&#39;applicazione è installata nel `magento2` directory relativa al docroot del server web su `localhost` e il percorso dell&#39;amministratore è `admin`; pertanto:

   L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

   Il nome del database è `magento`e il nome utente e la password sono entrambi `magento`

* Utilizza le riscritture del server

* L&#39;amministratore dispone delle seguenti proprietà:

   * Nome e cognome `Magento User`
   * Nome utente `admin` e la password è `admin123`
   * L&#39;indirizzo e-mail è `user@example.com`

* La lingua predefinita è `en_US` (Inglese USA)
* La valuta predefinita è in dollari statunitensi
* Il fuso orario predefinito è U.S. Central (America/Chicago)
* OpenSearch 1.2 è installato in `es-host.example.com` e si collega alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Messaggi simili alla seguente visualizzazione per indicare che l’installazione è riuscita:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Esempio 2: installazione di base senza account utente amministratore

È possibile installare Adobe Commerce o Magento Open Source senza creare l’utente amministratore, come illustrato nell’esempio seguente.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Se l&#39;installazione ha esito positivo, vengono visualizzati messaggi come il seguente:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Dopo l&#39;installazione è possibile creare un utente amministratore utilizzando `admin:user:create` comando:
[Creare o modificare un amministratore](tutorials/admin.md#create-or-edit-an-administrator)

#### Esempio 3: installazione con opzioni aggiuntive

L’esempio seguente installa Adobe Commerce o Magenti Open Source con le seguenti opzioni:

* L&#39;applicazione è installata nel `magento2` directory relativa al docroot del server web su `localhost` e il percorso dell&#39;amministratore è `admin`; pertanto:

   L&#39;URL della vetrina è `http://127.0.0.1`

* Il server di database si trova sullo stesso host del server Web.

   Il nome del database è `magento`e il nome utente e la password sono entrambi `magento`

* L&#39;amministratore dispone delle seguenti proprietà:

   * Nome e cognome `Magento User`
   * Nome utente `admin` e la password è `admin123`
   * L&#39;indirizzo e-mail è `user@example.com`

* La lingua predefinita è `en_US` (Inglese USA)
* La valuta predefinita è in dollari statunitensi
* Il fuso orario predefinito è U.S. Central (America/Chicago)
* Il programma di installazione pulisce prima il database prima di installare le tabelle e lo schema
* È possibile utilizzare il prefisso dell&#39;incremento dell&#39;ordine di vendita `ORD$` (poiché contiene un carattere speciale [`$`], il valore deve essere racchiuso tra virgolette doppie)
* I dati della sessione vengono salvati nel database
* Utilizza le riscritture del server
* L&#39;Elasticsearch 7 è installato in `es-host.example.com` e si collega alla porta 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>È necessario immettere il comando su una singola riga o, come nell&#39;esempio precedente, con un `\` alla fine di ogni riga.

Se l&#39;installazione ha esito positivo, vengono visualizzati messaggi come il seguente:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

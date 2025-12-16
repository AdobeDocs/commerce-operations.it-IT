---
title: Gestore messaggi (ActiveMQ Artemis)
description: Segui questi passaggi per installare e configurare Apache ActiveMQ Artemis message broker per le installazioni locali di Adobe Commerce.
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Gestore messaggi (ActiveMQ Artemis)

Adobe Commerce supporta anche il broker di messaggi open source ActiveMQ Artemis tramite il protocollo STOMP (Simple Text Oriented Messaging Protocol). Fornisce un sistema di messaggistica affidabile e scalabile, offrendo flessibilità per le integrazioni basate su STOMP.


>[!NOTE]
>
>ActiveMQ Artemis è stato introdotto in Adobe Commerce 2.4.5 e versioni successive. Per informazioni dettagliate sull&#39;installazione di ActiveMQ Artemis in Adobe Commerce su progetti di infrastruttura cloud, vedere [Configurazione del servizio ActiveMQ](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/service/activemq) nella *Guida di Commerce su Cloud*.

Le code di messaggi forniscono un meccanismo di comunicazione asincrona in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. Non è necessario che comunichino con la coda di messaggi contemporaneamente. Quando un mittente inserisce un messaggio in una coda, questo viene memorizzato fino a quando il destinatario non lo riceve.

Prima di installare Adobe Commerce, è necessario stabilire il sistema della coda di messaggi. La sequenza di base è:

1. Installa Apache ActiveMQ Artemis ed eventuali prerequisiti.
1. Connettere ActiveMQ ad Adobe Commerce.

>[!NOTE]
>
>È possibile utilizzare MySQL, ActiveMQ o [!DNL RabbitMQ] per l&#39;elaborazione della coda di messaggi. Per informazioni dettagliate sulla configurazione del sistema di code di messaggi, vedere [Panoramica delle code di messaggi](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se utilizzi l&#39;API in blocco con Adobe Commerce, per impostazione predefinita la configurazione del sistema della coda di messaggi utilizza [!DNL RabbitMQ] come gestore di messaggi. Per ulteriori informazioni, vedere [Avvia consumer della coda messaggi](../../configuration/cli/start-message-queues.md).

>[!TIP]
>
>Prima dell&#39;installazione, controlla sempre la [pagina di download di Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/) per l&#39;ultima versione stabile. Gli esempi in questo documento utilizzano la versione 2.42.0, che era l’ultima versione stabile a settembre 2025.


## Installare Apache ActiveMQ Artemis

È possibile installare ActiveMQ Artemis utilizzando Docker (consigliato per lo sviluppo) o l&#39;installazione manuale (consigliato per la produzione).

### Opzione 1: installazione Docker (consigliata per lo sviluppo)

#### Prerequisiti

Verificare che Docker sia installato e in esecuzione nel sistema.

>[!TIP]
>
>Per ulteriori informazioni sull&#39;immagine ufficiale di ActiveMQ Artemis Docker, vedere la [pagina di Apache ActiveMQ Artemis Docker Hub](https://hub.docker.com/r/apache/activemq-artemis).

#### Passaggi per l’installazione

1. Esegui ActiveMQ Artemis utilizzando l&#39;immagine Docker ufficiale:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Esegui con credenziali personalizzate:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Comandi di gestione Docker

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Accesso ai servizi

Una volta che il contenitore Docker è in esecuzione, puoi accedere a:

- **Console Web**: http://localhost:8161/console (credenziali predefinite: artemis/artemis)
- **Porta STOMP**: localhost:61613 (per la connessione Adobe Commerce)

>[!NOTE]
>
>L’installazione Docker è consigliata per lo sviluppo e il test. Per la produzione, è consigliabile utilizzare l&#39;installazione manuale con le configurazioni di sicurezza appropriate.

### Opzione 2: installazione manuale su Ubuntu/CentOS

#### Prerequisiti

Verificare che sia installato Java 17 o versione successiva (richiesto per ActiveMQ Artemis 2.42.0+).

### Passaggi per l’installazione

1. Scarica e installa la versione più recente dal sito Web [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/). A settembre 2025, la versione stabile più recente è la 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Creare l&#39;utente `artemis` e impostare la proprietà:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Crea un&#39;istanza di broker:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Avvia broker:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Configura ActiveMQ Artemis

Consulta la documentazione ufficiale di ActiveMQ Artemis per configurare e gestire il broker. Presta attenzione ai seguenti elementi:

- Variabili di ambiente
- Accesso alla porta (protocollo STOMP)
- Account utente e credenziali predefiniti
- Avvio e arresto del broker
- Limiti di sistema e ottimizzazione delle risorse

### File di configurazione chiave

- `/var/lib/artemis-instance/etc/broker.xml` - Configurazione broker principale
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Autenticazione utente
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Ruoli utente
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Configurazione Bootstrap

### Abilita protocollo STOMP

Controllare `/var/lib/artemis-instance/etc/broker.xml` per verificare che l&#39;accettore STOMP sia configurato:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Per abilitare SSL su STOMP è necessario aggiungere esplicitamente l&#39;accettore `stomp-ssl`.

## Installazione con ActiveMQ Artemis e connessione

Se si installa Adobe Commerce _dopo_ l&#39;installazione di ActiveMQ Artemis, aggiungere i seguenti parametri della riga di comando durante l&#39;installazione:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Dove:

| Parametro | Descrizione |
|--- |--- |
| `--stomp-host` | Il nome host in cui è installato ActiveMQ. |
| `--stomp-port` | Porta da utilizzare per la connessione ad ActiveMQ. Il valore predefinito è `61613`. |
| `--stomp-user` | Nome utente per la connessione ad ActiveMQ. Non utilizzare l&#39;utente predefinito `artemis`. |
| `--stomp-password` | Password per la connessione ad ActiveMQ. Non utilizzare la password predefinita `artemis`. |
| `--stomp-ssl` | Indica se connettersi ad ActiveMQ. Il valore predefinito è `false`. Se imposti il valore su true, consulta Configurare SSL per ulteriori informazioni. |

## Connetti ActiveMQ Artemis

Se nel file `<install_directory>/app/etc/env.php` è già presente un&#39;istanza di Adobe Commerce con configurazione RabbitMQ (AMQP) e si desidera connetterla ad ActiveMQ, sostituire la sezione `queue` con STOMP in modo che sia simile alla seguente:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

È inoltre possibile impostare i valori di configurazione ActiveMQ utilizzando il comando `bin/magento setup:config:set` (rimuovere la configurazione AMQP se esiste nel file `app/etc/env.php`):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Dopo aver eseguito il comando o aggiornato il file `<install_directory>/app/etc/env.php` con i valori di configurazione STOMP, eseguire `bin/magento setup:upgrade` per applicare le modifiche e creare le code richieste in ActiveMQ.

## Configurare SSL

Per configurare il supporto per SSL, modificare i parametri `ssl` e `ssl_options` nel file `<install_directory>/app/etc/env.php` in modo che siano simili ai seguenti:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### Opzioni di configurazione SSL

| Opzione | Descrizione | Predefinito |
|--- |--- |--- |
| `verify_peer` | Verifica il certificato SSL del broker | `true` |
| `verify_peer_name` | Verifica che il nome host del broker corrisponda al certificato | `true` |
| `allow_self_signed` | Consenti certificati autofirmati | `false` |
| `cafile` | Percorso del file del certificato CA per la verifica del broker | Obbligatorio per SSL |
| `certfile` | Percorso del file di certificato client (per SSL reciproco) | Facoltativo |
| `keyfile` | Percorso del file della chiave privata del client (per SSL reciproco) | Facoltativo |
| `passphrase` | Passphrase per chiave privata client | Facoltativo |

### Configurazione SSL di sviluppo

Per gli ambienti di sviluppo, puoi utilizzare impostazioni SSL flessibili:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Ottimizzazione delle prestazioni

ActiveMQ Artemis offre diverse opzioni di ottimizzazione delle prestazioni:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Monitoraggio e gestione

### Console web

ActiveMQ Artemis fornisce una console di gestione basata su Web accessibile da:
- URL: `http://localhost:8161/console`
- Credenziali predefinite: `artemis/artemis`

## Risoluzione dei problemi

### Problemi comuni

1. **Connessione rifiutata**: verificare che ActiveMQ Artemis sia in esecuzione e che l&#39;accettore STOMP sia configurato.
1. **Autenticazione non riuscita**: controllare nome utente/password sia nella configurazione del broker che nel file `env.php`.
1. **Handshake SSL non riuscito**: verificare i certificati e la configurazione SSL.




### Verifica connessione STOMP

Verifica connessione STOMP tramite telnet:

```bash
telnet localhost 61613
```

Dovresti vedere una connessione stabilita. Per eseguire il test con un comando STOMP:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

L’output previsto deve mostrare la connessione stabilita e la risposta del protocollo STOMP.

## Avvia i consumer della coda di messaggi

Dopo aver connesso Adobe Commerce e ActiveMQ Artemis, è necessario avviare i consumer della coda messaggi. Per ulteriori informazioni, vedere [Configurare le code dei messaggi](../../configuration/cli/start-message-queues.md).


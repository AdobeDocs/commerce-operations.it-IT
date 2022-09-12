---
title: Gestore messaggi
description: Segui questi passaggi per installare e configurare il software richiesto per la gestione dei messaggi (come RabbitMQ) per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Gestore messaggi

Adobe Commerce utilizza il broker di messaggi open-source RabbitMQ. Offre un sistema di messaggistica affidabile, altamente disponibile, scalabile e portatile.

Le code dei messaggi forniscono un meccanismo di comunicazione asincrono in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. Né devono comunicare contemporaneamente con la coda dei messaggi. Quando un mittente mette un messaggio in coda, viene memorizzato fino a quando il destinatario non lo riceve.

È necessario stabilire il sistema di coda dei messaggi prima di installare Adobe Commerce o Magenti Open Source. La sequenza di base è:

1. Installa RabbitMQ e tutti i prerequisiti.
1. Collega RabbitMQ ad Adobe Commerce o Magento Open Source.

>[!NOTE]
>
>È possibile utilizzare MySQL o RabbitMQ per l&#39;elaborazione della coda dei messaggi. Per informazioni dettagliate sulla configurazione del sistema di coda dei messaggi, vedi [Panoramica delle code di messaggio](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se utilizzi l’API di massa con Adobe Commerce, per impostazione predefinita la configurazione del sistema della coda dei messaggi utilizza RabbitMQ come gestore dei messaggi. Vedi [Avvia i consumatori della coda dei messaggi](../../configuration/cli/start-message-queues.md) per ulteriori informazioni.

## Installa RabbitMQ su Ubuntu

Per installare RabbitMQ su Ubuntu 16, immetti il seguente comando:

```bash
sudo apt install -y rabbitmq-server
```

Questo comando installa anche i pacchetti Erlang richiesti.

Se si dispone di una versione precedente di Ubuntu, RabbitMQ consiglia di installare il pacchetto dal loro sito web.

1. Scarica il pacchetto .deb da [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installa il pacchetto con `dpkg`.

Fai riferimento a [Installazione su Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) per ulteriori informazioni.

## Installa RabbitMQ su CentOS

### Installa Erlang

RabbitMQ è stato scritto utilizzando il linguaggio di programmazione Erlang, che deve essere installato sullo stesso sistema di RabbitMQ.

Vedi [Installazione manuale](https://www.erlang-solutions.com/downloads/) per ulteriori informazioni.

Fai riferimento a [Matrice di versione RabbitMQ/Erlang](https://www.rabbitmq.com/which-erlang.html) per installare la versione corretta.

### Installa RabbitMQ

Il server RabbitMQ è incluso in CentOS, ma la versione è spesso vecchia. RabbitMQ consiglia di installare il pacchetto dal proprio sito web.

Per ottenere la versione più recente supportata, consulta la pagina di installazione di RabbitMQ . Adobe Commerce e Magenti Open Source 2.3 e 2.4 supportano RabbitMQ 3.8.x.

Fai riferimento a [Installazione su Linux basato su RPM](https://www.rabbitmq.com/install-rpm.html) per ulteriori informazioni.

## Configura RabbitMQ

Consulta la documentazione ufficiale RabbitMQ per configurare e gestire RabbitMQ. Presta attenzione ai seguenti elementi:

* Variabili di ambiente
* Accesso alla porta
* Account utente predefiniti
* Avvio e arresto del broker
* Limiti del sistema

## Installa con RabbitMQ e connetti

Se installi Adobe Commerce o Magenti Open Source _dopo_ installare RabbitMQ, aggiungere i seguenti parametri della riga di comando durante l&#39;installazione:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dove:

| Parametro | Descrizione |
|--- |--- |
| `--amqp-host` | Il nome host in cui è installato RabbitMQ. |
| `--amqp-port` | La porta da utilizzare per la connessione a RabbitMQ. Il valore predefinito è `5672`. |
| `--amqp-user` | Nome utente per la connessione a RabbitMQ. Non utilizzare l&#39;utente predefinito `guest`. |
| `--amqp-password` | Password per la connessione a RabbitMQ. Non utilizzare la password predefinita `guest`. |
| `--amqp-virtualhost` | Host virtuale per la connessione a RabbitMQ. Il valore predefinito è `/`. |
| `--amqp-ssl` | Indica se connettersi a RabbitMQ. Il valore predefinito è `false`. Se imposti il valore su true, consulta Configurare SSL per ulteriori informazioni. |

## Connetti RabbitMQ

Se hai già installato Adobe Commerce o Magento Open Source e desideri connetterlo a RabbitMQ, aggiungi una `queue` nella sezione `<install_directory>/app/etc/env.php` in modo che sia simile al seguente:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

Puoi anche impostare i valori di configurazione RabbitMQ utilizzando `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Dopo l&#39;esecuzione del comando o l&#39;aggiornamento del `<install_directory>/app/etc/env.php` file con valori di configurazione AMQP, esegui `bin/magento setup:upgrade` per applicare le modifiche e creare le code e gli scambi richiesti in RabbitMQ.

## Configurare SSL

Per configurare il supporto per SSL, modifica il `ssl` e `ssl_options` dei parametri `<install_directory>/app/etc/env.php` in modo che siano simili ai seguenti:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Avvia i consumatori della coda messaggi

Dopo aver connesso Adobe Commerce e RabbitMQ, devi avviare la coda messaggi per i consumatori. Vedi [Configurare le code di messaggio](../../configuration/cli/start-message-queues.md) per i dettagli.

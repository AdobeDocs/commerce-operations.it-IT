---
title: Gestore messaggi
description: Segui questi passaggi per installare e configurare il software Message Broker richiesto (ad esempio [!DNL RabbitMQ]) per le installazioni locali di Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Gestore messaggi

Adobe Commerce utilizza [!DNL RabbitMQ] broker di messaggi open-source. Offre un sistema di messaggistica affidabile, ad alta disponibilità, scalabile e portatile.

Le code di messaggi forniscono un meccanismo di comunicazione asincrona in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. Non è necessario che comunichino con la coda di messaggi contemporaneamente. Quando un mittente inserisce un messaggio in una coda, questo viene memorizzato fino a quando il destinatario non lo riceve.

Prima di installare Adobe Commerce, è necessario stabilire il sistema della coda di messaggi. La sequenza di base è:

1. Installa [!DNL RabbitMQ] ed eventuali prerequisiti.
1. Connetti [!DNL RabbitMQ] ad Adobe Commerce.

>[!NOTE]
>
>È possibile utilizzare MySQL oppure [!DNL RabbitMQ] per l’elaborazione della coda di messaggi. Per informazioni dettagliate sulla configurazione del sistema di coda dei messaggi, vedi [Panoramica delle code di messaggi](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se utilizzi l’API Bulk con Adobe Commerce, per impostazione predefinita la configurazione del sistema della coda di messaggi utilizza [!DNL RabbitMQ] come broker di messaggi. Consulta [Avvia consumer coda messaggi](../../configuration/cli/start-message-queues.md) per ulteriori informazioni.

## Installa [!DNL RabbitMQ] su Ubuntu

Per installare [!DNL RabbitMQ] su Ubuntu 16, immetti il seguente comando:

```bash
sudo apt install -y rabbitmq-server
```

Questo comando installa anche i pacchetti Erlang richiesti.

Se avete una versione precedente di Ubuntu, [!DNL RabbitMQ] consiglia di installare il pacchetto dal proprio sito web.

1. Scarica il pacchetto .deb da [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installare il pacchetto con `dpkg`.

Fai riferimento a [Installazione su Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) per ulteriori informazioni.

## Installa [!DNL RabbitMQ] su CentOS

### Installa Erlang

[!DNL RabbitMQ] è stato scritto utilizzando il linguaggio di programmazione Erlang, che deve essere installato sullo stesso sistema di [!DNL RabbitMQ].

Consulta [Installazione manuale](https://www.erlang-solutions.com/downloads/) per ulteriori informazioni.

Consulta la sezione [[!DNL RabbitMQ]Matrice di versione /Erlang](https://www.rabbitmq.com/which-erlang.html) per installare la versione corretta.

### Installa [!DNL RabbitMQ]

Il [!DNL RabbitMQ] Il server è incluso in CentOS, ma la versione è spesso precedente. [!DNL RabbitMQ] consiglia di installare il pacchetto dal proprio sito web.

Consulta la sezione [!DNL RabbitMQ] per ottenere la versione più recente supportata. Supporto di Adobe Commerce 2.3 e 2.4 [!DNL RabbitMQ] 3.8.x.

Fai riferimento a [Installazione su Linux basato su RPM](https://www.rabbitmq.com/install-rpm.html) per ulteriori informazioni.

## Configura [!DNL RabbitMQ]

Rivedi il funzionario [!DNL RabbitMQ] documentazione per configurare e gestire [!DNL RabbitMQ]. Presta attenzione ai seguenti elementi:

* Variabili di ambiente
* Accesso alla porta
* Account utente predefiniti
* Avvio e arresto del broker
* Limiti di sistema

## Installa con [!DNL RabbitMQ] e connetti

Se installi Adobe Commerce _dopo_ installazione [!DNL RabbitMQ], aggiungere i seguenti parametri della riga di comando durante l&#39;installazione:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dove:

| Parametro | Descrizione |
|--- |--- |
| `--amqp-host` | Il nome host in cui [!DNL RabbitMQ] è installato. |
| `--amqp-port` | Porta a cui connettersi [!DNL RabbitMQ]. Il valore predefinito è `5672`. |
| `--amqp-user` | Nome utente per la connessione a [!DNL RabbitMQ]. Non utilizzare l&#39;utente predefinito `guest`. |
| `--amqp-password` | Password per la connessione a [!DNL RabbitMQ]. Non utilizzare la password predefinita `guest`. |
| `--amqp-virtualhost` | Host virtuale per la connessione a [!DNL RabbitMQ]. Il valore predefinito è `/`. |
| `--amqp-ssl` | Indica se connettersi a [!DNL RabbitMQ]. Il valore predefinito è `false`. Se imposti il valore su true, consulta Configurare SSL per ulteriori informazioni. |

## Connetti [!DNL RabbitMQ]

Se Adobe Commerce era già installato e desideri connetterlo a [!DNL RabbitMQ], aggiungi un `queue` sezione nella sezione `<install_directory>/app/etc/env.php` in modo che sia simile al seguente:

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

È inoltre possibile impostare [!DNL RabbitMQ] valori di configurazione utilizzando `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Dopo aver eseguito il comando o aggiornato `<install_directory>/app/etc/env.php` file con valori di configurazione AMQP, esegui `bin/magento setup:upgrade` per applicare le modifiche e creare le code e gli scambi necessari in [!DNL RabbitMQ].

## Configurare SSL

Per configurare il supporto per SSL, modifica il `ssl` e `ssl_options` parametri in `<install_directory>/app/etc/env.php` in modo che siano simili ai seguenti:

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

## Avvia i consumer della coda di messaggi

Dopo aver connesso Adobe Commerce e [!DNL RabbitMQ], è necessario avviare i consumer della coda di messaggi. Consulta [Configurare le code di messaggi](../../configuration/cli/start-message-queues.md) per i dettagli.

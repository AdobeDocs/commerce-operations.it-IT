---
title: Gestore messaggi (RabbitMQ)
description: Segui questi passaggi per installare e configurare il software Message Broker richiesto (ad esempio  [!DNL RabbitMQ]) per le installazioni locali di Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 73faaa2a3b9ce773e9a381d103735403966f568b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Gestore messaggi (RabbitMQ)

Adobe Commerce utilizza il broker di messaggi open-source [!DNL RabbitMQ]. Offre un sistema di messaggistica affidabile, ad alta disponibilità, scalabile e portatile.

Le code di messaggi forniscono un meccanismo di comunicazione asincrona in cui il mittente e il destinatario di un messaggio non si contattano a vicenda. Non è necessario che comunichino con la coda di messaggi contemporaneamente. Quando un mittente inserisce un messaggio in una coda, questo viene memorizzato fino a quando il destinatario non lo riceve.

Prima di installare Adobe Commerce, è necessario stabilire il sistema della coda di messaggi. La sequenza di base è:

1. Installa [!DNL RabbitMQ] ed eventuali prerequisiti.
1. Connetti [!DNL RabbitMQ] ad Adobe Commerce.

>[!NOTE]
>
>È possibile utilizzare MySQL o [!DNL RabbitMQ] per l&#39;elaborazione della coda di messaggi. Per informazioni dettagliate sulla configurazione del sistema di code di messaggi, vedere [Panoramica delle code di messaggi](https://developer.adobe.com/commerce/php/development/components/message-queues/). Se utilizzi l&#39;API in blocco con Adobe Commerce, per impostazione predefinita la configurazione del sistema della coda di messaggi utilizza [!DNL RabbitMQ] come gestore di messaggi. Per ulteriori informazioni, vedere [Avvia consumer della coda messaggi](../../configuration/cli/start-message-queues.md).

## Installa [!DNL RabbitMQ] su Ubuntu

Per installare [!DNL RabbitMQ] su Ubuntu 16, immettere il comando seguente:

```bash
sudo apt install -y rabbitmq-server
```

Questo comando installa anche i pacchetti Erlang richiesti.

Se si dispone di una versione precedente di Ubuntu, [!DNL RabbitMQ] consiglia di installare il pacchetto dal sito Web.

1. Scarica il pacchetto .deb da [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Installa il pacchetto con `dpkg`.

Per ulteriori informazioni, vedere [Installazione su Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html).

## Installa [!DNL RabbitMQ] su CentOS

### Installa Erlang

[!DNL RabbitMQ] è stato scritto utilizzando il linguaggio di programmazione Erlang, che deve essere installato nello stesso sistema di [!DNL RabbitMQ].

Per ulteriori informazioni, vedere [Installazione manuale](https://www.erlang-solutions.com/downloads/).

Per installare la versione corretta, consultare la [[!DNL RabbitMQ]/Erlang versione ](https://www.rabbitmq.com/which-erlang.html).

### Installa [!DNL RabbitMQ]

Il server [!DNL RabbitMQ] è incluso in CentOS, ma la versione è spesso precedente. [!DNL RabbitMQ] consiglia di installare il pacchetto dal proprio sito Web.

Per ottenere la versione supportata più recente, fare riferimento alla pagina di installazione di [!DNL RabbitMQ]. Adobe Commerce 2.3 e 2.4 supportano [!DNL RabbitMQ] 3.8.x.

Per ulteriori informazioni, vedere [Installazione su Linux](https://www.rabbitmq.com/install-rpm.html) basato su RPM.

## Configura [!DNL RabbitMQ]

Consulta la documentazione ufficiale di [!DNL RabbitMQ] per configurare e gestire [!DNL RabbitMQ]. Presta attenzione ai seguenti elementi:

* Variabili di ambiente
* Accesso alla porta
* Account utente predefiniti
* Avvio e arresto del broker
* Limiti di sistema

## Installa con [!DNL RabbitMQ] e connetti

Se installi Adobe Commerce _dopo_ installi [!DNL RabbitMQ], aggiungi i seguenti parametri della riga di comando durante l&#39;installazione:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Dove:

| Parametro | Descrizione |
|--- |--- |
| `--amqp-host` | Il nome host in cui è installato [!DNL RabbitMQ]. |
| `--amqp-port` | Porta da utilizzare per la connessione a [!DNL RabbitMQ]. Il valore predefinito è `5672`. |
| `--amqp-user` | Nome utente per la connessione a [!DNL RabbitMQ]. Non utilizzare l&#39;utente predefinito `guest`. |
| `--amqp-password` | Password per la connessione a [!DNL RabbitMQ]. Non utilizzare la password predefinita `guest`. |
| `--amqp-virtualhost` | Host virtuale per la connessione a [!DNL RabbitMQ]. Il valore predefinito è `/`. |
| `--amqp-ssl` | Indica se connettersi a [!DNL RabbitMQ]. Il valore predefinito è `false`. Se imposti il valore su true, consulta Configurare SSL per ulteriori informazioni. |

## Connetti [!DNL RabbitMQ]

Se Adobe Commerce è già installato e si desidera connetterlo a [!DNL RabbitMQ], aggiungere una sezione `queue` nel file `<install_directory>/app/etc/env.php` in modo che sia simile alla seguente:

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

È inoltre possibile impostare [!DNL RabbitMQ] valori di configurazione utilizzando il comando `bin/magento setup:config:set`:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Dopo aver eseguito il comando o aggiornato il file `<install_directory>/app/etc/env.php` con i valori di configurazione AMQP, eseguire `bin/magento setup:upgrade` per applicare le modifiche e creare le code e gli scambi necessari in [!DNL RabbitMQ].

## Configurare SSL

Per configurare il supporto per SSL, modificare i parametri `ssl` e `ssl_options` nel file `<install_directory>/app/etc/env.php` in modo che siano simili ai seguenti:

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

Dopo aver connesso Adobe Commerce e [!DNL RabbitMQ], è necessario avviare i consumer della coda messaggi. Per ulteriori informazioni, vedere [Configurare le code dei messaggi](../../configuration/cli/start-message-queues.md).

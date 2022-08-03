---
title: Configurare la coda messaggi di Amazon
description: Scopri come configurare Commerce per l’utilizzo del servizio AWS MQ.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Configurare la coda messaggi di Amazon

A partire da Commerce 2.4.3, la coda messaggi di Amazon (MQ) è disponibile come sostituzione pronta per il cloud per le istanze della coda messaggi in locale.

Per creare una coda di messaggi su AWS, vedi [Configurazione di Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in _Documentazione di AWS_.

## Configurare Commerce per AWS MQ

Per connettersi al servizio AWS MQ, configura il `queue.amqp` nell&#39;oggetto `env.php` file.
La coda messaggi di AWS richiede una connessione SSL/TLS.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Dove:

- `host`- l&#39;url dell&#39;endpoint AMQP; disponibile facendo clic sul nome del broker in AWS (rimuovi &quot;https://&quot; e il numero di porta finale)
- `user`- Il valore del nome utente immesso durante la creazione del broker AWS MQ
- `password`- Il valore della password immesso durante la creazione del broker AWS MQ

>[!INFO]
>
>Amazon MQ supporta solo le connessioni TLS. Verifica peer non supportata.

Dopo aver modificato le `env.php` esegui il seguente comando per completare la configurazione:

```bash
bin/magento setup:upgrade
```

## Utilizzo del servizio MQ di AWS da parte di Commerce

La `async.operations.all` il consumatore della coda messaggi utilizza la connessione AMQP.

Questo consumatore indirizza qualsiasi nome argomento con prefisso `async` tramite la connessione AWS MQ.

Ad esempio, in `InventoryCatalog` esistono:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configurazione predefinita per `InventoryCatalog` non pubblica messaggi su RabbitMQ; il comportamento predefinito consiste nell’eseguire l’azione nello stesso thread utente. Per dire `InventoryCatalog` per pubblicare i messaggi, abilita `cataloginventory/bulk_operations/async`. Dall’amministratore, vai a **Negozi** > Configurazione > **Catalogo** > **Inventario** > Operazioni in blocco dell&#39;amministratore e set  `Run asynchronously`a **Sì**.

## Verifica della coda dei messaggi

Per testare l’invio di un messaggio da Commerce a RabbitMQ:

1. Accedi alla console web RabbitMQ in AWS per monitorare le code.
1. In Amministratore, crea un prodotto.
1. Crea un&#39;origine Inventory.
1. Abilita **Negozi** > Configurazione > **Catalogo** > **Inventario** > Operazioni in blocco dell’amministratore > Esegui in modo asincrono.
1. Vai a **Catalogo** > Prodotti. Dalla griglia, seleziona il prodotto creato sopra e fai clic su **Assegna origine magazzino**.
1. Fai clic su **Salva e chiudi** per completare il processo.

   Ora dovresti vedere i messaggi visualizzati nella console web RabbitMQ.

1. Avvia la `async.operations.all` consumer della coda messaggi.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Ora dovresti vedere il messaggio in coda che viene elaborato nella console web RabbitMQ.
Verifica che le origini di inventario siano cambiate nel prodotto in Admin.

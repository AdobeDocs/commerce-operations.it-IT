---
title: Configurare la coda di messaggi di Amazon
description: Scopri come configurare Commerce per l’utilizzo del servizio AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Configurare la coda di messaggi di Amazon

A partire dalla versione 2.4.3 di Commerce, Amazon Message Queue (MQ) è disponibile come sostituzione pronta per il cloud per le istanze della coda di messaggi on-premise.

Per creare una coda di messaggi su AWS, vedi [Configurazione di Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) nel _Documentazione di AWS_.

## Configurare Commerce per AWS MQ

Per connettersi al servizio AWS MQ, configura il `queue.amqp` oggetto in `env.php` file.
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

- `host`: URL dell’endpoint AMQP, disponibile facendo clic sul nome del broker in AWS (rimuovere &quot;https://&quot; e il numero della porta finale)
- `user`- Il valore del nome utente immesso durante la creazione del broker MQ di AWS
- `password`- Il valore della password immesso durante la creazione del broker MQ di AWS

>[!INFO]
>
>Amazon MQ supporta solo le connessioni TLS. La verifica tra pari non è supportata.

Dopo aver modificato `env.php` , eseguire il comando seguente per completare l&#39;installazione:

```bash
bin/magento setup:upgrade
```

## Utilizzo del servizio AWS MQ in Commerce

Il `async.operations.all` Il consumatore della coda di messaggi utilizza la connessione AMQP.

Questo consumatore indirizza qualsiasi nome di argomento con il prefisso `async` tramite la connessione AWS MQ.

Ad esempio, in `InventoryCatalog` sono disponibili:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

Configurazione predefinita per `InventoryCatalog` non pubblica i messaggi in [!DNL RabbitMQ]; il comportamento predefinito consiste nell&#39;eseguire l&#39;azione nello stesso thread utente. Da raccontare `InventoryCatalog` per pubblicare i messaggi, abilita `cataloginventory/bulk_operations/async`. Dall’amministratore, vai a **Negozi** > Configurazione > **Catalogo** > **Inventario** > Operazioni di massa e impostazione dell&#39;amministratore  `Run asynchronously`a **Sì**.

## Verifica della coda dei messaggi

Per verificare l’invio di messaggi da Commerce a [!DNL RabbitMQ]:

1. Accedi a [!DNL RabbitMQ] console web in AWS per monitorare le code.
1. In Amministratore, crea un prodotto.
1. Crea un&#39;origine magazzino.
1. Abilita **Negozi** > Configurazione > **Catalogo** > **Inventario** > Operazioni di massa amministrazione > Esegui in modo asincrono.
1. Vai a **Catalogo** > Prodotti. Dalla griglia, seleziona il prodotto creato in precedenza e fai clic su **Assegna origine magazzino**.
1. Clic **Salva e chiudi** per completare il processo.

   Ora dovresti vedere i messaggi visualizzati nel [!DNL RabbitMQ] console web.

1. Avvia il `async.operations.all` consumer coda messaggi.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Ora dovresti vedere che il messaggio in coda viene elaborato in [!DNL RabbitMQ] console web.
Verifica che le origini dell’inventario siano state modificate sul prodotto nell’amministratore.

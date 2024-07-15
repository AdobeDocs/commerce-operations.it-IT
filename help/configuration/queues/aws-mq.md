---
title: Configurare la coda di messaggi di Amazon
description: Scopri come configurare Commerce per l’utilizzo del servizio AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Configurare la coda di messaggi di Amazon

A partire dalla versione 2.4.3 di Commerce, Amazon Message Queue (MQ) è disponibile come sostituzione pronta per il cloud per le istanze di code di messaggi locali.

Per creare una coda di messaggi in AWS, vedi [Configurazione di Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) nella _documentazione di AWS_.

## Configurare Commerce per AWS MQ

Per connettersi al servizio AWS MQ, configurare l&#39;oggetto `queue.amqp` nel file `env.php`.
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

- `host`—URL dell&#39;endpoint AMQP; disponibile facendo clic sul nome del broker in AWS (rimuovere &quot;https://&quot; e il numero di porta finale)
- `user`: valore del nome utente immesso durante la creazione del broker MQ di AWS
- `password` - Valore password immesso durante la creazione del broker MQ di AWS

>[!INFO]
>
>Amazon MQ supporta solo le connessioni TLS. La verifica tra pari non è supportata.

Dopo aver modificato il file `env.php`, eseguire il comando seguente per completare l&#39;installazione:

```bash
bin/magento setup:upgrade
```

## Utilizzo del servizio AWS MQ da parte di Commerce

Il consumer della coda di messaggi `async.operations.all` utilizza la connessione AMQP.

Questo consumatore indirizza qualsiasi nome di argomento con prefisso `async` tramite la connessione AWS MQ.

Ad esempio, in `InventoryCatalog` sono presenti:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configurazione predefinita per `InventoryCatalog` non pubblica i messaggi in [!DNL RabbitMQ]. Il comportamento predefinito consiste nell&#39;eseguire l&#39;azione nello stesso thread utente. Per indicare a `InventoryCatalog` di pubblicare i messaggi, abilitare `cataloginventory/bulk_operations/async`. Dall&#39;amministratore, vai a **Archivi** > Configurazione > **Catalogo** > **Inventario** > Operazioni in blocco dall&#39;amministratore e imposta `Run asynchronously`su **Sì**.

## Verifica della coda dei messaggi

Per verificare l&#39;invio di messaggi da Commerce a [!DNL RabbitMQ]:

1. Accedere alla console Web [!DNL RabbitMQ] in AWS per monitorare le code.
1. In Amministratore, crea un prodotto.
1. Crea un&#39;origine magazzino.
1. Abilita **Archivi** > Configurazione > **Catalogo** > **Inventario** > Operazioni in blocco amministratore > Esegui in modo asincrono.
1. Vai a **Catalogo** > Prodotti. Dalla griglia, selezionare il prodotto creato in precedenza e fare clic su **Assegna Source di magazzino**.
1. Fai clic su **Salva e chiudi** per completare il processo.

   I messaggi dovrebbero essere visualizzati nella console Web [!DNL RabbitMQ].

1. Avvia il consumer della coda di messaggi `async.operations.all`.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Il messaggio in coda dovrebbe essere elaborato nella console Web [!DNL RabbitMQ].
Verifica che le origini dell’inventario siano state modificate sul prodotto nell’amministratore.

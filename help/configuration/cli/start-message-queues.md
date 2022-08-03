---
title: Avvia i consumatori della coda dei messaggi
description: Scopri come avviare un consumer della coda di messaggi.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Avvia i consumatori della coda dei messaggi

{{file-system-owner}}

Devi avviare un consumer della coda di messaggi per abilitare operazioni asincrone come azioni di massa di Inventory management e REST bulk e endpoint asincroni. Per abilitare la funzionalità B2B, devi avviare più consumatori. Nei moduli di terze parti potrebbe essere necessario avviare un consumatore personalizzato.

Per visualizzare un elenco di tutti i consumatori:

```bash
bin/magento queue:consumers:list
```

Per avviare i consumatori della coda dei messaggi:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Dopo aver utilizzato tutti i messaggi disponibili, il comando termina. Puoi eseguire nuovamente il comando manualmente o con un cron job. È inoltre possibile eseguire più istanze del `magento queue:consumers:start` per elaborare code di messaggi di grandi dimensioni. Ad esempio, puoi aggiungere `&` al comando per eseguirlo in background, tornare a un prompt e continuare ad eseguire i comandi:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Vedi [coda:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) nella sezione Commercio del _Riferimento per gli strumenti della riga di comando_ per informazioni dettagliate sulle opzioni dei comandi, sui parametri e sui valori.

>[!INFO]
>
>La `--multi-process` è presente in `queue:consumers:start` ma per eseguire i consumatori con processi paralleli, configura la [`multiple_processes`](../queues/manage-message-queues.md#configuration) opzione in `/app/etc/env.php`. In caso contrario, se `queue:consumers:start` viene chiamato con `--multi-process` funziona solo su un singolo thread.

---
title: Avvia consumer coda messaggi
description: Scopri come avviare i consumer di code di messaggi per le operazioni asincrone di Adobe Commerce. Scopri la gestione dei consumatori e la configurazione delle funzionalità B2B.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Avvia consumer coda messaggi

{{file-system-owner}}

È necessario avviare un consumer [coda messaggi](../queues/consumers.md) per abilitare operazioni asincrone come le azioni di massa di Inventory management e gli endpoint REST in blocco e asincroni. Per abilitare la funzionalità B2B, è necessario avviare più consumer. Per i moduli di terze parti potrebbe essere necessario anche avviare un consumer personalizzato.

Per visualizzare un elenco di tutti i consumatori:

```bash
bin/magento queue:consumers:list
```

Per avviare i consumer della coda messaggi:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Dopo aver utilizzato tutti i messaggi disponibili, il comando termina. È possibile eseguire nuovamente il comando manualmente o con un processo cron. È inoltre possibile eseguire più istanze del comando `magento queue:consumers:start` per elaborare code di messaggi di grandi dimensioni. È ad esempio possibile aggiungere `&` al comando per eseguirlo in background, tornare a un prompt e continuare a eseguire i comandi:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Per informazioni dettagliate sulle opzioni, i parametri e i valori del comando, vedere [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) nella sezione Commerce del _Riferimento agli strumenti della riga di comando_.

>[!INFO]
>
>L&#39;opzione `--multi-process` è presente nel comando `queue:consumers:start`, ma per eseguire i consumer con processi paralleli, configurare l&#39;opzione [`multiple_processes`](../queues/manage-message-queues.md#configuration) in `/app/etc/env.php`. In caso contrario, se `queue:consumers:start` viene chiamato con l&#39;opzione `--multi-process`, funziona solo su un singolo thread.

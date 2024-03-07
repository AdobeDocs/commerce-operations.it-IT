---
title: Avvia consumer coda messaggi
description: Scopri come avviare un consumer di code di messaggi.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: c9e7a8926c7003d34a62d2defb62c09d58919ddd
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Avvia consumer coda messaggi

{{file-system-owner}}

Devi avviare un [consumer coda messaggi](../queues/consumers.md) per abilitare operazioni asincrone come le azioni di massa di Inventory management ed endpoint REST bulk e asincroni. Per abilitare la funzionalità B2B, è necessario avviare più consumer. Per i moduli di terze parti potrebbe essere necessario anche avviare un consumer personalizzato.

Per visualizzare un elenco di tutti i consumatori:

```bash
bin/magento queue:consumers:list
```

Per avviare i consumer della coda messaggi:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Dopo aver utilizzato tutti i messaggi disponibili, il comando termina. È possibile eseguire nuovamente il comando manualmente o con un processo cron. È inoltre possibile eseguire più istanze di `magento queue:consumers:start` comando per elaborare code di messaggi di grandi dimensioni. Ad esempio, puoi aggiungere `&` per eseguire il comando in background, tornare a un prompt e continuare a eseguire i comandi:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulta [`queue:consumers:start`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) nella sezione Commerce del _Riferimento per gli strumenti della riga di comando_ per informazioni dettagliate sulle opzioni, i parametri e i valori del comando.

>[!INFO]
>
>Il `--multi-process` è presente in `queue:consumers:start` ma per eseguire i consumer con processi paralleli, configurare il [`multiple_processes`](../queues/manage-message-queues.md#configuration) opzione in `/app/etc/env.php`. Altrimenti, se `queue:consumers:start` viene chiamato con `--multi-process` , funziona solo su un singolo thread.

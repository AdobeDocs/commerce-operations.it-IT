---
title: Gestire le code dei messaggi
description: Scopri come gestire le code di messaggi dalla riga di comando per Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Gestire le code dei messaggi

È possibile gestire le code di messaggi dalla riga di comando utilizzando i processi cron o un gestore di processi esterno per garantire che i consumatori recuperino i messaggi.

## Gestione dei processi

I processi Cron sono il meccanismo predefinito per il riavvio dei consumatori. I processi avviati da `cron` utilizzano il numero di messaggi specificato e quindi terminano. `cron` riavvia il consumer.

Nell&#39;esempio seguente viene illustrata la configurazione `crontab` per i consumer in esecuzione:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>La frequenza dei controlli delle code di messaggi dipende dalla logica di business e dalle risorse di sistema disponibili. In generale, potrebbe essere utile cercare nuovi clienti e inviare e-mail di benvenuto con maggiore frequenza rispetto a un processo che richiede un uso intensivo delle risorse, ad esempio l’aggiornamento del catalogo. È necessario definire `cron` pianificazioni in base alle proprie esigenze aziendali.
>
>Può essere configurato in Admin Stores (Archivi amministratori) > Settings (Impostazioni) > Configuration (Configurazione) > Advanced (Avanzate) > System (Sistema) > Cron configuration options (Opzioni di configurazione Cron) per group: users (Gruppo: consumatori).
>
>Per ulteriori informazioni sull&#39;utilizzo di [ con Commerce, vedere ](../cli/configure-cron-jobs.md)Configurare ed eseguire cron`cron`.

È inoltre possibile utilizzare un gestore processi come [Supervisore](https://supervisord.readthedocs.io/en/latest/) per monitorare lo stato dei processi. Il manager può utilizzare la riga di comando per riavviare i processi in base alle esigenze.

## Configurazione

### Comportamento predefinito

- Il processo Cron `consumers_runner` è abilitato
- Il processo Cron `consumers_runner` esegue tutti i consumer definiti
- Ogni consumatore elabora 10000 messaggi e quindi termina

>[!INFO]
>
>Se il tuo archivio Adobe Commerce è ospitato sulla piattaforma Cloud, usa [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#cron_consumers_runner) per configurare il processo cron `consumers_runner`.

### Configurazione specifica

Modificare il file `/app/etc/env.php` per configurare il processo cron `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Valore booleano che abilita o disabilita il processo cron `consumers_runner` (impostazione predefinita = `true`).
- `max_messages` - Numero massimo di messaggi che ogni consumer deve elaborare prima di terminare (impostazione predefinita = `10000`). Sebbene non sia consigliato, è possibile utilizzare 0 per impedire al consumatore di terminare l’operazione. Vedere [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) per configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi.
- `consumers` - Matrice di stringhe che specifica quali consumer eseguire. Un array vuoto esegue *tutti* i consumer.
- `multiple_processes` - Matrice di coppie chiave-valore che specifica il consumer da eseguire nel numero di processi. Supportato in Commerce 2.4.4 o versione successiva.

  >[!INFO]
  >
  >Non è consigliabile eseguire più consumer in una coda gestita da MySQL. Per ulteriori informazioni, vedere [Cambiare la coda dei messaggi da MySQL a AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp).

  >[!INFO]
  >
  >Se il tuo archivio Adobe Commerce è ospitato sulla piattaforma Cloud, usa [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#consumers_wait_for_max_messages) per configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi.

Vedi [Avvia consumer coda messaggi](../cli/start-message-queues.md).

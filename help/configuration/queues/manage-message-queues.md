---
title: Gestire le code dei messaggi
description: Scopri come gestire le code di messaggi dalla riga di comando per Adobe Commerce.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Gestire le code dei messaggi

Puoi gestire le code di messaggi dalla riga di comando utilizzando cron jobs o un gestore di processi esterno per garantire che i consumatori recuperino i messaggi.

## Gestione dei processi

I lavori Cron sono il meccanismo predefinito per riavviare i consumatori. Processi avviati da `cron` consumare il numero specificato di messaggi e quindi terminare. Ripristino `cron` riavvia il consumer.

L’esempio seguente mostra le `crontab` configurazione per utenti in esecuzione:

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
>La frequenza con cui controlli le code dei messaggi dipende dalla logica di business e dalle risorse di sistema disponibili. In generale, potresti voler verificare la presenza di nuovi clienti e inviare e-mail di benvenuto con maggiore frequenza rispetto a un processo che richiede molte risorse, ad esempio l’aggiornamento del catalogo. È necessario definire `cron` programmazioni in base alle esigenze aziendali.
>
>Può essere configurato in Admin Store > Impostazioni > Configurazione > Avanzate > Sistema > Opzioni di configurazione Cron per il gruppo: consumatori.
>
>Vedi [Configurare ed eseguire cron](../cli/configure-cron-jobs.md) per ulteriori informazioni sull&#39;utilizzo di `cron` con Commerce.

È inoltre possibile utilizzare un manager del processo come [Supervisore](http://supervisord.org/index.html) per monitorare lo stato dei processi. Il manager può utilizzare la riga di comando per riavviare i processi in base alle esigenze.

## Configurazione

### Comportamento per impostazione predefinita

- Lavoro cron `consumers_runner` è abilitato
- Lavoro cron `consumers_runner` esegue tutti i consumatori definiti
- Ogni consumatore elabora 10000 messaggi e quindi termina

>[!INFO]
>
>Se il tuo store Adobe Commerce è ospitato sulla piattaforma Cloud, utilizza [`CRON_CONSUMERS_RUNNER`](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) per configurare `consumers_runner` cron job.

### Configurazione specifica

Modifica le `/app/etc/env.php` file per configurare il lavoro cron `consumers_runner`.

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

- `cron_run` - Un valore booleano che abilita o disabilita il `consumers_runner` cron job (predefinito = `true`).
- `max_messages` - Il numero massimo di messaggi che ogni consumatore deve elaborare prima di terminare (impostazione predefinita = `10000`). Anche se non è consigliato, puoi utilizzare 0 per impedire al consumatore di terminare. Vedi [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) per configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi.
- `consumers` - Un array di stringhe che specifica quali consumatori eseguire. Viene eseguita una matrice vuota *tutto* consumatori.
- `multiple_processes` - Matrice di coppie chiave-valore che specifica quale consumatore eseguire in quanti processi.

   >[!INFO]
   >
   >Si sconsiglia di eseguire più consumatori su una coda gestita da MySQL. Vedi [Cambia la coda dei messaggi da MySQL ad AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) per ulteriori informazioni.

   >[!INFO]
   >
   >Se il tuo store Adobe Commerce è ospitato sulla piattaforma Cloud, utilizza [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://devdocs.magento.com/cloud/env/variables-deploy.html#consumers_wait_for_max_messages) per configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi.

Vedi [Avvia i consumatori della coda dei messaggi](../cli/start-message-queues.md).

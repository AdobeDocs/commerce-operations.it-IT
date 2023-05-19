---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Opzioni CLI per i consumer della coda di messaggi

| Nome | Descrizione | Valore | Obbligatorio |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina se i consumatori attenderanno un messaggio dalla coda. | 1 - Sì, 0 - No | No |

* `0`: i consumatori elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono messaggi aggiuntivi per entrare nella coda, anche se il numero di messaggi elaborati è inferiore al `--max_messages` valore specificato durante l&#39;avvio dei consumatori.

* `1`: i consumatori continuano a elaborare i messaggi dalla coda dei messaggi fino a raggiungere il numero massimo di messaggi (il valore specificato per `--max_messages` il `queue:consumers:start` prima di chiudere la connessione TCP e terminare il processo consumer. Se la coda si svuota prima di raggiungere `--max_messages` il consumatore attende che arrivino più messaggi. Se si utilizzano i processi di lavoro per eseguire i consumer anziché un processo cron, impostare questa variabile su `1`.

>[!WARNING]
>
>Il `--consumers-wait-for-messages` è un’opzione globale e non può essere configurata separatamente per ogni consumatore.

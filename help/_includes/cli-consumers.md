---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# Opzioni CLI per i consumer della coda di messaggi

| Nome | Descrizione | Valore | Obbligatorio |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina se i consumatori attenderanno un messaggio dalla coda. | 1 - Sì, 0 - No | No |

* `0`: i consumer elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono messaggi aggiuntivi per entrare nella coda, anche se il numero di messaggi elaborati è inferiore al valore `--max_messages` specificato durante l&#39;avvio dei consumatori.

* `1`: i consumer continuano a elaborare i messaggi dalla coda dei messaggi fino a raggiungere il numero massimo di messaggi (valore specificato per `--max_messages` nel comando `queue:consumers:start`) prima di chiudere la connessione TCP e terminare il processo consumer. Se la coda si svuota prima di raggiungere `--max_messages`, il consumatore attende l&#39;arrivo di altri messaggi. Se si utilizzano i processi di lavoro per eseguire i consumer anziché un processo cron, impostare questa variabile su `1`.

>[!WARNING]
>
>L&#39;opzione `--consumers-wait-for-messages` è globale e non può essere configurata separatamente per ogni consumatore.

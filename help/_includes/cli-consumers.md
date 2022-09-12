---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Opzioni CLI per i consumatori in coda di messaggio

| Nome | Descrizione | Valore | Obbligatorio |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Determina se i consumatori dovranno attendere un messaggio dalla coda. | 1 - Sì, 0 - No | No |

* `0`: I consumatori elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono che altri messaggi entrino nella coda, anche se il numero di messaggi elaborati è inferiore al `--max_messages` valore specificato durante l&#39;avvio dei consumatori.

* `1`: I consumatori continuano a elaborare i messaggi dalla coda dei messaggi fino a raggiungere il numero massimo di messaggi (il valore specificato per `--max_messages` sulla `queue:consumers:start` prima di chiudere la connessione TCP e interrompere il processo consumer. Se la coda si svuota prima di raggiungere `--max_messages` il consumatore attende ulteriori messaggi. Se utilizzi i lavoratori per eseguire i consumatori invece di utilizzare un lavoro cron, imposta questa variabile su `1`.

>[!WARNING]
>
>La `--consumers-wait-for-messages` è un’opzione globale e non può essere configurata separatamente per ogni consumatore.

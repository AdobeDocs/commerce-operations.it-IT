---
title: Metodologia di implementazione del progetto
description: Acquisisci familiarità con il funzionamento della distribuzione del software Adobe Commerce.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metodologia di implementazione del progetto

Ora che hai una migliore idea degli strumenti coinvolti, suddivideremo i nostri processi di consegna e test.

## Integrazione continua (CI)

I processi di integrazione continua eseguono automaticamente le azioni seguenti:

- Genera il codice sorgente per verificare gli errori di compilazione.
- Esegui i test quando viene creata/aggiornata una richiesta di pull. Attualmente, vengono eseguiti i test delle unità PHP.

Il processo inserisce il proprio stato di esecuzione nella richiesta di pull. Gli sviluppatori possono visualizzare i dettagli dell’esecuzione del processo in modo da poter correggere o migliorare il codice esistente.

## Consegna continua (CD)

La distribuzione continua (CD) distribuisce immediatamente il codice sorgente al server dopo che tutti i test sono stati superati. Gli sviluppatori possono controllare le loro funzioni rapidamente e quindi assegnare l’attività al team di controllo qualità per la revisione.

Durante l&#39;esecuzione della build sul sistema di compilazione, non solo riduce i tempi di inattività dell&#39;implementazione, ma riduce anche il carico sul server. Di conseguenza, le attività di controllo qualità, che si verificano sul server, sono influenzate meno.

![Infografica continua di consegna](../../assets/playbooks/cicd.svg)

Il processo CI/CD nel diagramma precedente può essere descritto brevemente come segue:

- Bitbucket ospita l’archivio Git.
- Le immagini Docker vengono replicate dalle configurazioni dello stack della tecnologia di produzione.
- I contenitori Docker vengono utilizzati per tutti gli ambienti di sviluppo e test. Se necessario, altri ambienti potrebbero utilizzare queste configurazioni.
- Gli sviluppatori eseguono un checkout del ramo di codice pertinente per ogni nuova attività/ticket.
- Per tutti i rami di commit, automaticamente:
   - Esegui una scansione del codice standard.
   - Esegui un codice durante la compilazione del test.
   - Esegui una scansione del codice statico (ad esempio, SonarQube).
- Tutti i commit di scansione che passano vengono uniti con il ramo di destinazione.
- Un nuovo tag rilasciato viene inviato ad AWS S3 per il pacchetto di preparazione alla distribuzione.
- La nuova distribuzione viene attivata dal team di progettazione della distribuzione.
   - Un processo di distribuzione distribuisce il nuovo pacchetto all’ambiente di destinazione.
   - Gli aggiornamenti della struttura del database richiedono una pausa per accettare nuove richieste dal cliente.
- Il processo di distribuzione termina con una notifica e-mail/Slack/team, inviata automaticamente dal server al team di progettazione della distribuzione.

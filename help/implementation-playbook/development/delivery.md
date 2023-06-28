---
title: Metodologia di implementazione del progetto
description: Acquisisci familiarità con il funzionamento della distribuzione del software Adobe Commerce.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
feature: Build, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metodologia di attuazione del progetto

Ora che hai un’idea migliore degli strumenti coinvolti, suddivideremo i nostri processi di consegna e test.

## Integrazione continua (CI)

I processi di integrazione continua eseguono automaticamente le azioni seguenti:

- Genera il codice sorgente per verificare gli errori di compilazione.
- Esegui i test quando viene creata/aggiornata una richiesta di pull. Attualmente vengono eseguiti gli unit test PHP.

Il processo invia il proprio stato di esecuzione alla richiesta di pull. Gli sviluppatori possono visualizzare i dettagli dell’esecuzione del processo in modo da correggere o migliorare il codice esistente.

## Consegna continua (CD)

Continuous Delivery (CD) distribuisce immediatamente il codice sorgente al server dopo il completamento di tutti i test. Gli sviluppatori possono verificare rapidamente le proprie funzioni e quindi assegnare l’attività al team di controllo qualità per la revisione.

Quando la build viene eseguita sul sistema di build, non solo riduce al minimo i tempi di inattività dell’implementazione, ma riduce anche il carico sul server. Di conseguenza, le attività di controllo qualità che si verificano sul server sono meno interessate.

![Infografica della consegna continua](../../assets/playbooks/cicd.svg)

Il processo CI/CD nel diagramma precedente può essere descritto brevemente come segue:

- Bitbucket ospita l’archivio Git.
- Le immagini Docker vengono replicate dalle configurazioni dello stack della tecnologia di produzione.
- I contenitori Docker vengono utilizzati per tutti gli ambienti di sviluppo e test. Se necessario, altri ambienti possono sfruttare queste configurazioni.
- Gli sviluppatori eseguono un checkout del ramo di codice pertinente per ogni nuova attività/ticket.
- Per tutti i rami di commit, automaticamente:
   - Esegui una scansione del codice standard.
   - Eseguire un test di compilazione del codice.
   - Esegui una scansione del codice statico (ad esempio, SonarQube).
- Tutti i commit di scansione che passano vengono uniti al ramo di destinazione.
- Un nuovo tag rilasciato viene inviato ad AWS S3 per il pacchetto di preparazione all’implementazione.
- La nuova distribuzione viene attivata dal team di progettazione della distribuzione.
   - Un processo di distribuzione distribuisce il nuovo pacchetto nell’ambiente di destinazione.
   - Gli aggiornamenti della struttura del database richiedono una pausa per accettare nuove richieste dal cliente.
- Il processo di distribuzione termina con una notifica e-mail/Slack/team, inviata automaticamente dal server al team di progettazione della distribuzione.

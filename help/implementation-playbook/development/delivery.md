---
title: Metodologia di implementazione del progetto
description: Acquisisci familiarità con il funzionamento della distribuzione del software Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Metodologia di implementazione del progetto

Now that you have a better idea of the tools that are involved, we will now break down our delivery and testing processes.

## Continuous Integration (CI)

I processi di integrazione continua eseguono automaticamente le azioni seguenti:

- Genera il codice sorgente per verificare gli errori di compilazione.
- Esegui i test quando viene creata/aggiornata una richiesta di pull. At present, PHP unit tests are executed.

Il processo inserisce il proprio stato di esecuzione nella richiesta di pull. Gli sviluppatori possono visualizzare i dettagli dell’esecuzione del processo in modo da poter correggere o migliorare il codice esistente.

## Continuous Delivery (CD)

La distribuzione continua (CD) distribuisce immediatamente il codice sorgente al server dopo che tutti i test sono stati superati. Developers can check their functions quickly and then assign the task to the QA team for review.

As the build executes on the build system, it not only minimizes the deployment downtime, but also reduces the load on the server. Di conseguenza, le attività di controllo qualità, che si verificano sul server, sono influenzate meno.

![Infografica continua di consegna](../../assets/playbooks/cicd.svg)

Il processo CI/CD nel diagramma precedente può essere descritto brevemente come segue:

- Bitbucket hosts the Git repository.
- Docker images are replicated from production technology stack configurations.
- Docker containers are used for all development and testing environments. Other environments could leverage these configurations if needed.
- Developers perform a checkout of the relevant code branch for every new task/ticket.
- For all commit branches, automatically:
   - Esegui una scansione del codice standard.
   - Execute a code compiling test.
   - Esegui una scansione del codice statico (ad esempio, SonarQube).
- All scan commits that pass are merged with the target branch.
- A new released tag is pushed to AWS S3 for the deployment readiness package.
- La nuova distribuzione viene attivata dal team di progettazione della distribuzione.
   - Un processo di distribuzione distribuisce il nuovo pacchetto all’ambiente di destinazione.
   - Database structure updates require a pause to take on new requests from the customer.
- Il processo di distribuzione termina con una notifica e-mail/Slack/team, inviata automaticamente dal server al team di progettazione della distribuzione.

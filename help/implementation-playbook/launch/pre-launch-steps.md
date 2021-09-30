---
title: Passaggi pre-lancio
description: Utilizza le nostre liste di controllo pre-lancio per garantire un’implementazione fluida del sito Commerce di Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Pre-launch steps

Dopo aver completato la distribuzione e il test negli ambienti di staging, puoi iniziare la preparazione all’avvio del sito. Lo staging è un ambiente di quasi produzione in esecuzione su hardware, configurazioni, architettura e servizi simili. Consente di ridurre i tempi di inattività e di eseguire l&#39;estensione, il servizio, le configurazioni personalizzate e il test di accettazione da parte degli utenti commerciali dei componenti essenziali per il rilascio di siti e negozi.

La checklist pre-lancio è necessaria per verificare lo stato prima del lancio, che include le seguenti verifiche principali:

- Blocco del codice per la distribuzione
- Assicurati che il downtime sia stato comunicato in anticipo almeno un giorno per la release di manutenzione e una settimana per il primo avvio
- Deployment scripts are set up/configured completely for Production/Staging/Integration environments
- I database sono tutti configurati e identici tra gli ambienti di staging e produzione
- I certificati SSL (TLS) vengono convalidati per ambienti di staging/produzione
- Mail services are well-configured and functioning for transactional emails
- CDN è configurato per ambienti di staging/produzione
- Configurare la scansione di sicurezza per gli ambienti di staging/produzione
   - Analisi della sicurezza di Adobe Commerce
- Perform performance assessment by
   - JMeter
   - Assedio
   - Test pagina web
   - Velocità della pagina Google
- Convalida tutte le integrazioni di terze parti che funzioneranno in applicazione (OMS, CRM)
- Abilita strumento di monitoraggio delle prestazioni (nuove relazioni)
- Data migration activities in rehearsal (if any)

![Diagramma che mostra la fase 1 del processo di lancio](../../assets/playbooks/launch-steps-1.svg)

Le principali differenze tra le implementazioni on-premise di Adobe Commerce sono gli script e gli strumenti di distribuzione, nonché la configurazione per SSL, servizio Mail e CDN. Tuttavia, il processo resta lo stesso.

For SSL(TLS) certificate, Adobe Commerce on cloud infrastructure provides a Fastly wildcard certificate. Per iniziare a utilizzarlo, è necessario trasmettere la convalida: aggiungi il record TXT finale al nome di dominio apex nelle impostazioni DNS. Il record TXT finale può essere trovato nel foglio di calcolo on-boarding, altrimenti è necessario inviare un ticket di supporto per ottenerlo. Sostituisci questo testo con le tue domande/commenti qui. Se utilizzi un certificato SSL (TLS) personale invece di un certificato jolly Flast, invia un ticket di supporto con il certificato allegato alla configurazione.

Adobe Commerce sull’infrastruttura cloud fornisce la funzionalità SendGrid Mail per le e-mail transazionali. Per i piani Pro, è necessario aggiungere record SendGrid alle impostazioni DNS. SendGrid records can be found in the on-boarding spreadsheet, otherwise SI or merchant should submit support tickets to obtain them. Per iniziare, non è necessario apportare alcuna modifica al DNS; SendGrid è preconfigurato.

## Elenco di controllo completo pre-avvio

The complete pre-launch checklist shows all major activities whose completeness is necessary for moving to the launch state.

- Go-live risk mitigation plans updated
- Nomi di dominio corretti forniti
- Outgoing emails have been tested
- Provisioning e configurazione del certificato SSL
- La configurazione completa dell’applicazione Adobe Commerce viene aggiornata correttamente
- Gli URL di base e gli URL amministratore di base sono impostati correttamente sul nome host finale
- Le password amministratore vengono modificate
- Vengono rimossi tutti gli utenti con accesso all’applicazione che non richiedono più l’accesso
- Payment configuration for production environment (for some, payment is using sandbox mode for testing)
- Test data (customer, wishlist, reviews, orders, and related data) from Production database is cleared

![Diagram showing phase 2 of the launch process](../../assets/playbooks/launch-steps-2.svg)

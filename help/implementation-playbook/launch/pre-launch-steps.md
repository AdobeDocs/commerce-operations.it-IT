---
title: Passaggi pre-lancio
description: Utilizza le nostre liste di controllo pre-lancio per garantire un’implementazione fluida del sito Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Passaggi pre-lancio

Dopo aver completato la distribuzione e il test negli ambienti di staging, puoi iniziare la preparazione all’avvio del sito. Lo staging è un ambiente di quasi produzione in esecuzione su hardware, configurazioni, architettura e servizi simili. Consente di ridurre i tempi di inattività e di eseguire l&#39;estensione, il servizio, le configurazioni personalizzate e il test di accettazione da parte degli utenti commerciali dei componenti essenziali per il rilascio di siti e negozi.

La checklist pre-lancio è necessaria per verificare lo stato prima del lancio, che include le seguenti verifiche principali:

- Blocco del codice per la distribuzione
- Assicurati che il downtime sia stato comunicato in anticipo almeno un giorno per la release di manutenzione e una settimana per il primo avvio
- Gli script di distribuzione sono configurati o configurati completamente per gli ambienti di produzione, staging, integrazione
- I database sono tutti configurati e identici tra gli ambienti di staging e produzione
- I certificati SSL (TLS) vengono convalidati per ambienti di staging/produzione
- I servizi di posta elettronica sono ben configurati e funzionano per le e-mail transazionali
- CDN è configurato per ambienti di staging/produzione
- Configurare la scansione di sicurezza per gli ambienti di staging/produzione
   - Analisi della sicurezza Adobe Commerce
- Eseguire la valutazione delle prestazioni tramite
   - JMeter
   - Assedio
   - Test pagina web
   - Velocità della pagina Google
- Convalida tutte le integrazioni di terze parti che funzioneranno in applicazione (OMS, CRM)
- Abilita strumento di monitoraggio delle prestazioni (nuove relazioni)
- Attività di migrazione dei dati a prova generale (se presenti)

![Diagramma che mostra la fase 1 del processo di lancio](../../assets/playbooks/launch-steps-1.svg)

Le principali differenze tra le implementazioni on-premise cloud di Adobe Commerce sono gli script e gli strumenti di distribuzione, nonché la configurazione per SSL, servizio di posta e CDN. Tuttavia, il processo resta lo stesso.

Per il certificato SSL (TLS), Adobe Commerce sull’infrastruttura cloud fornisce un certificato con caratteri jolly Flast. Per iniziare a utilizzarlo, è necessario trasmettere la convalida: aggiungi il record TXT finale al nome di dominio apex nelle impostazioni DNS. Il record TXT finale può essere trovato nel foglio di calcolo on-boarding, altrimenti è necessario inviare un ticket di supporto per ottenerlo. Sostituisci questo testo con le tue domande/commenti qui. Se utilizzi un certificato SSL (TLS) personale invece di un certificato jolly Flast, invia un ticket di supporto con il certificato allegato alla configurazione.

L’infrastruttura Adobe Commerce su cloud fornisce la funzionalità SendGrid Mail per le e-mail transazionali. Per i piani Pro, è necessario aggiungere record SendGrid alle impostazioni DNS. I record SendGrid si trovano nel foglio di calcolo on-boarding, altrimenti SI o commerciante devono inviare i ticket di supporto per ottenerli. Per iniziare, non è necessario apportare alcuna modifica al DNS; SendGrid è preconfigurato.

## Elenco di controllo completo pre-avvio

La lista di controllo completa pre-lancio mostra tutte le attività principali la cui completezza è necessaria per passare allo stato di lancio.

- Aggiornamento dei piani di mitigazione dei rischi in diretta
- Nomi di dominio corretti forniti
- Le e-mail in uscita sono state testate
- Provisioning e configurazione del certificato SSL
- La configurazione completa dell’applicazione Adobe Commerce viene aggiornata correttamente
- Gli URL di base e gli URL amministratore di base sono impostati correttamente sul nome host finale
- Le password amministratore vengono modificate
- Vengono rimossi tutti gli utenti con accesso all’applicazione che non richiedono più l’accesso
- Configurazione del pagamento per l&#39;ambiente di produzione (per alcuni, il pagamento utilizza la modalità sandbox per il test)
- I dati di test (cliente, lista dei desideri, recensioni, ordini e dati correlati) dal database Production sono stati cancellati

![Diagramma che mostra la fase 2 del processo di lancio](../../assets/playbooks/launch-steps-2.svg)

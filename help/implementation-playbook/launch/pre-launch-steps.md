---
title: Passaggi precedenti al lancio
description: Utilizza le nostre liste di controllo precedenti al lancio per garantire un’implementazione fluida del sito Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Passaggi precedenti all’avvio

Dopo aver completato la distribuzione e il test negli ambienti di staging, puoi iniziare la preparazione dell’avvio del sito. La gestione temporanea è un ambiente di produzione in esecuzione su hardware, configurazioni, architettura e servizi simili. Consente di ridurre i tempi di inattività e di rendere vitali i componenti di test di estensione, servizio, configurazioni personalizzate e accettazione da parte degli utenti commerciali per il rilascio di siti e store.

La checklist pre-lancio deve essere verificata prima dello stato di lancio, che include le seguenti verifiche principali:

- Blocco del codice per la distribuzione
- Assicurati che i tempi di inattività siano stati comunicati in anticipo di almeno un giorno per la versione di manutenzione e una settimana per il primo avvio
- Gli script di implementazione vengono configurati completamente per gli ambienti di produzione, staging e integrazione
- I database sono tutti configurati e identici tra gli ambienti di staging e di produzione
- I certificati SSL (TLS) vengono convalidati per gli ambienti di staging/produzione
- I servizi di posta sono ben configurati e funzionano per le e-mail transazionali
- CDN è configurato per gli ambienti di staging/produzione
- Configurare l’analisi della sicurezza per gli ambienti di staging/produzione
   - analisi della sicurezza di Adobe Commerce
- Esecuzione della valutazione delle prestazioni tramite
   - JMeter
   - Assedio
   - Test pagina Web
   - Velocità pagina Google
- Convalidare tutte le integrazioni di terze parti che funzioneranno nell&#39;applicazione (OMS, CRM)
- Abilita strumento di monitoraggio delle prestazioni (New Relics)
- Attività di migrazione dei dati in prova (se presenti)

![Diagramma che mostra la fase 1 del processo di avvio](../../assets/playbooks/launch-steps-1.svg)

Le principali differenze tra le implementazioni on-premise e cloud di Adobe Commerce sono gli script e gli strumenti di distribuzione, nonché la configurazione per SSL, servizio di posta e CDN. Tuttavia, il processo è ancora lo stesso.

Per il certificato SSL (TLS), Adobe Commerce sull’infrastruttura cloud fornisce un certificato con caratteri jolly Fastly. Per iniziare a utilizzarlo, devi passare la convalida: aggiungi il record TXT rapido al nome di dominio apex nelle impostazioni DNS. Il record Fastly TXT si trova nel foglio di calcolo di onboarding, altrimenti è necessario inviare un ticket di supporto per ottenerlo. Sostituisci questo testo con le tue domande/commenti qui. Se utilizzi un tuo certificato SSL(TLS) invece di un certificato con caratteri jolly Fastly, invia un ticket di supporto allegando il certificato alla configurazione.

Adobe Commerce su infrastruttura cloud fornisce la funzionalità SendGrid Mail per le e-mail transazionali. Per i piani Pro, è necessario aggiungere record SendGrid alle impostazioni DNS. I record SendGrid si trovano nel foglio di calcolo on-boarding, altrimenti SI o l’esercente devono inviare i ticket di supporto per ottenerli. Per iniziare, non è necessario apportare alcuna modifica al DNS; SendGrid è preconfigurato per te.

## Completa elenco di controllo pre-avvio

L’elenco di controllo completo per il pre-lancio mostra tutte le principali attività la cui completezza è necessaria per passare allo stato di lancio.

- Aggiornamento dei piani di attenuazione dei rischi di lancio
- Sono stati forniti i nomi di dominio corretti
- Le e-mail in uscita sono state testate
- Il certificato SSL è stato fornito e configurato
- La configurazione importante dell’applicazione Adobe Commerce viene aggiornata correttamente
- Gli URL di base e l’URL amministratore di base sono impostati correttamente sul nome host finale
- Le password amministratore vengono modificate
- Tutti gli utenti con accesso all’applicazione che non richiedono più l’accesso vengono rimossi
- Configurazione del pagamento per l’ambiente di produzione (per alcuni, il pagamento utilizza la modalità sandbox per i test)
- I dati di test (cliente, lista dei desideri, recensioni, ordini e dati correlati) dal database di produzione vengono cancellati

![Diagramma che mostra la fase 2 del processo di avvio](../../assets/playbooks/launch-steps-2.svg)

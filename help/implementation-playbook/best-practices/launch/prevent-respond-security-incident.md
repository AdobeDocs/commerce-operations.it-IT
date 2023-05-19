---
title: Prevenire e rispondere a un problema di sicurezza
description: Scopri le best practice per evitare incidenti di sicurezza e rispondere a tali problemi nel progetto Adobe Commerce on cloud infrastructure.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Best practice per prevenire e rispondere a un problema di sicurezza

La sicurezza di Adobe Commerce funziona in un [Responsabilità condivisa](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modello. È fondamentale capire di cosa sono responsabili gli Adobi e i team tecnici. Di seguito riepiloghiamo [Best practice per la sicurezza](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) per garantire che il progetto disponga dei migliori controlli di sicurezza e come rispondere al meglio a un problema di sicurezza.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud

## Rispondere a un incidente

Quando si risponde a un problema di sicurezza, è necessario tenere presenti diverse considerazioni. Se pensi di aver riscontrato un recente problema di sicurezza per il progetto di infrastruttura cloud di Adobe Commerce, è importante controllare l’accesso a tutti gli account utente amministratore, abilitare controlli avanzati di autenticazione a più fattori (MFA), conservare i registri critici e rivedere gli aggiornamenti di sicurezza per la tua versione di Adobe Commerce.

Ulteriori raccomandazioni sono descritte di seguito. Possono contribuire a prevenire l&#39;accesso non autorizzato e avviare il processo per ulteriori analisi dei problemi.

## Come prevenire gli incidenti di sicurezza

Segui queste best practice sulla sicurezza per prevenire in modo proattivo incidenti di sicurezza che interessano i siti e gli store front di Adobe Commerce:

- [Abilita 2FA per l&#39;accesso amministratore](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
L’autenticazione a due fattori è ampiamente utilizzata ed è comune generare codici di accesso per siti web diversi sulla stessa app. In questo modo solo l&#39;utente può accedere al proprio account utente. Se si perde la password o se un bot la indovina, l&#39;autenticazione a due fattori aggiunge un livello di protezione.
- [Abilita MFA per accesso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Quando MFA è abilitato in un progetto, tutti gli account Adobe Commerce su infrastrutture cloud con accesso SSH devono seguire un flusso di lavoro di autenticazione che richiede un codice di autenticazione a due fattori (2FA) o un token API e un certificato SSH per accedere all’ambiente.
- Effettua l’aggiornamento all’ultima versione di Adobe Commerce.
Adobe rilascia patch funzionali e di sicurezza per ogni versione supportata di Adobe Commerce.
- Configurazione e utilizzo di un [URL amministratore non predefinito](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
L’Adobe consiglia di utilizzare un URL amministratore univoco e personalizzato invece del predefinito `admin` o un termine comune come *backend*. Anche se questa modifica alla configurazione non protegge direttamente il sito da un determinato attore non valido, può ridurre l’esposizione agli script che tentano di ottenere accesso non autorizzato.
- Impedisci la modifica o l&#39;aggiornamento dei valori di configurazione nell&#39;amministratore utilizzando  [`bin/magento config:set` Comando CLI con `lock env` opzione di configurazione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Questa opzione blocca il valore di configurazione in modo che non possa essere modificato nell’amministratore o impedisce le modifiche a un’impostazione già bloccata. Quando si utilizza questa opzione, le modifiche alla configurazione vengono scritte nel `<Commerce base dir>/app/etc/env.php` file.
- Imposta ed esegui il [Strumento Adobe Commerce Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html).
L&#39;analisi avanzata della sicurezza consente di monitorare tutti i siti Adobe Commerce, incluso PWA, per individuare rischi noti per la sicurezza e malware, nonché di ricevere aggiornamenti delle patch e notifiche di sicurezza.
- [Rivedere e aggiornare l’accesso utente amministratore](https://docs.magento.com/user-guide/system/permissions-users-all.html) e [impostazioni di protezione](https://docs.magento.com/user-guide/stores/security-admin.html).
   - È consigliabile rimuovere eventuali account vecchi, inutilizzati o sospetti e ruotare le password per tutti gli utenti Admin.
   - Rivedi e aggiorna le Impostazioni avanzate di sicurezza&lt; per il progetto. La configurazione della sicurezza Admin consente di aggiungere una chiave segreta agli URL, richiedere che le password distinguano tra maiuscole e minuscole e limitare la durata delle sessioni di amministrazione, inclusa la durata delle password e il numero di tentativi di accesso che possono essere effettuati prima che l’account utente Admin sia bloccato. Per una maggiore sicurezza, è possibile configurare la durata dell&#39;inattività della tastiera prima della scadenza della sessione corrente e richiedere che il nome utente e la password siano sensibili all&#39;uso di maiuscole e minuscole.
- Controlla Adobe Commerce su [utenti progetto cloud](https://devdocs.magento.com/cloud/project/user-admin.html).
È consigliabile rimuovere tutti gli account vecchi, inutilizzati o sospetti e richiedere agli utenti di modificare le password.
- Audit [Chiavi SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) per Adobe Commerce su infrastruttura cloud.
È consigliabile rivedere, eliminare e ruotare le chiavi SSH.
- Implementa l’elenco di controllo di accesso (ACL) per l’amministratore.
È possibile utilizzare un elenco ACL di Fastly Edge in combinazione con un [Frammento di codice VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) per filtrare le richieste in ingresso e consentire l’accesso all’amministratore per indirizzo IP.

## Analizzare un problema

Il primo passo dell&#39;analisi degli incidenti consiste nel raccogliere il maggior numero possibile di dati, il più rapidamente possibile. Raccogliere informazioni sull&#39;incidente può essere utile per determinare la causa potenziale dell&#39;incidente. Adobe Commerce fornisce gli strumenti indicati di seguito per l’analisi dei problemi.

- [Registri azioni amministrazione di controllo](https://docs.magento.com/user-guide/system/action-log-report.html).
Nel rapporto Registri azioni viene visualizzato un record dettagliato di tutte le azioni di amministrazione abilitate per la registrazione. Ogni record ha la marca temporale e registra l’indirizzo IP e il nome dell’utente. I dettagli del registro includono i dati utente amministratore e le relative modifiche apportate durante l’azione.
- Analizzare gli eventi con [Strumento Osservazione per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Lo strumento di osservazione per Adobe Commerce consente di analizzare problemi complessi per identificare le cause principali. Invece di tenere traccia di dati diversi, puoi dedicare più tempo alla correlazione di eventi ed errori per ottenere informazioni più approfondite sulle cause dei colli di bottiglia delle prestazioni.
Lo strumento ha lo scopo di fornire una visione chiara di alcuni dei potenziali problemi del sito per aiutarti a identificare la causa principale e mantenere le prestazioni dei siti ottimali. Per accedere alla documentazione dello strumento, fai clic sul collegamento alla documentazione Osservazione per Adobe Commerce. Nella documentazione è presente una sezione che descrive tutte le informazioni disponibili sul **Sicurezza** scheda.
- Analizzare i registri con [Registri New Relic](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). I progetti Pro di Adobe Commerce su infrastruttura cloud includono [Registri New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) servizio. Il servizio è preconfigurato per aggregare tutti i dati di registro dagli ambienti di staging e produzione per visualizzarli in un dashboard di gestione dei registri centralizzato.
Puoi utilizzare il servizio Registri di New Relic per completare le seguenti attività:
   - Utilizzare [Query New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) per cercare dati di registro aggregati.
   - Visualizzare i dati di registro tramite l’applicazione Registri di New Relic.

## Informazioni aggiuntive

- [Framework di analisi della causa principale](https://sansec.io/kb/incident-response/magento-root-cause-analysis).

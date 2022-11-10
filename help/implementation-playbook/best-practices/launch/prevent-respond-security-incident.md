---
title: Prevenire e rispondere a un incidente di sicurezza
description: Scopri le best practice per evitare e rispondere a incidenti di sicurezza nel progetto Adobe Commerce on cloud Infrastructure.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---


# Best practice per prevenire e rispondere a un problema di sicurezza

La sicurezza Adobe Commerce funziona sotto un [Responsabilità condivisa](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modello. È fondamentale comprendere le responsabilità di Adobe e team tecnici. Di seguito riassunto [Tecniche consigliate per la sicurezza](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) per garantire che il tuo progetto disponga dei migliori controlli di sicurezza e del modo migliore per rispondere a un incidente di sicurezza.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud

## Risposta a un incidente

Ci sono molte considerazioni quando si risponde a un incidente di sicurezza. Se pensi di aver riscontrato un problema di sicurezza recente per il progetto di infrastruttura cloud di Adobe Commerce, è importante controllare l’accesso a tutti gli account utente amministratore, abilitare i controlli avanzati di autenticazione a più fattori (MFA), mantenere i registri critici e rivedere gli aggiornamenti di sicurezza per la tua versione di Adobe Commerce.

Di seguito sono riportati ulteriori consigli. Possono contribuire a prevenire l&#39;accesso non autorizzato e iniziare il processo per ulteriori analisi degli incidenti.

## Come prevenire incidenti di sicurezza

Segui queste best practice di sicurezza per evitare in modo proattivo incidenti di sicurezza che influiscono sui siti e sulle vetrine Adobe Commerce:

- [Abilita 2FA per l&#39;accesso dell&#39;amministratore](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
L’autenticazione a due fattori è ampiamente utilizzata ed è comune generare codici di accesso per siti web diversi nella stessa app. In questo modo potrai accedere solo al tuo account utente. Se si perde la password o un bot indovina, l&#39;autenticazione a due fattori aggiunge un livello di protezione.
- [Abilitare MFA per l’accesso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Quando MFA è abilitato su un progetto, tutti gli account Adobe Commerce su infrastrutture cloud con accesso SSH devono seguire un flusso di lavoro di autenticazione che richiede un codice di autenticazione a due fattori (2FA) o un token API e un certificato SSH per accedere all’ambiente.
- Effettua l’aggiornamento alla versione più recente di Adobe Commerce.
Adobe rilascia patch di sicurezza e funzionali per ogni versione supportata di Adobe Commerce.
- Imposta e utilizza un [URL amministratore non predefinito](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
L’Adobe consiglia di utilizzare un URL amministratore univoco e personalizzato anziché il valore predefinito `admin` o un termine comune come *backend*. Anche se questa modifica della configurazione non protegge direttamente il sito da un determinato attore danneggiato, può ridurre l&#39;esposizione a script che tentano di ottenere l&#39;accesso non autorizzato.
- Impedisci la modifica o l&#39;aggiornamento dei valori di configurazione nell&#39;amministratore utilizzando  [`bin/magento config:set` Comando CLI con `lock env` opzione di configurazione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Questa opzione blocca il valore di configurazione in modo che non possa essere modificato nell’amministratore o impedisce le modifiche a un’impostazione già bloccata. Quando utilizzi questa opzione, le modifiche di configurazione vengono scritte nel `<Commerce base dir>/app/etc/env.php` file.
- Imposta ed esegui [Strumento di scansione della sicurezza Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html).
La scansione della sicurezza avanzata consente di monitorare ogni sito Adobe Commerce, incluso PWA, per individuare rischi noti per la sicurezza e il malware, e di ricevere aggiornamenti sulle patch e notifiche di sicurezza.
- [Rivedi e aggiorna l’accesso utente amministratore](https://docs.magento.com/user-guide/system/permissions-users-all.html) e [impostazioni di protezione](https://docs.magento.com/user-guide/stores/security-admin.html).
   - È consigliabile rimuovere tutti gli account obsoleti, inutilizzati o sospetti e ruotare le password per tutti gli utenti Admin.
   - Rivedi e aggiorna le Impostazioni avanzate di sicurezza&lt; per il tuo progetto. La configurazione di sicurezza Amministratore consente di aggiungere una chiave segreta agli URL, richiedere che le password siano sensibili a maiuscole e minuscole e di limitare la durata delle sessioni di amministrazione, inclusa la durata delle password, e il numero di tentativi di accesso che possono essere effettuati prima che l’account utente amministratore sia bloccato. Per una maggiore sicurezza, è possibile configurare la lunghezza dell’inattività della tastiera prima della scadenza della sessione corrente e richiedere la distinzione tra maiuscole e minuscole per nome utente e password.
- Controlla Adobe Commerce su [utenti di progetti cloud](https://devdocs.magento.com/cloud/project/user-admin.html).
È consigliabile rimuovere account vecchi, non utilizzati o sospetti e richiedere agli utenti di modificare le proprie password.
- Audit [Tasti SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) per Adobe Commerce sull&#39;infrastruttura cloud.
Consigliamo di rivedere, eliminare e ruotare le chiavi SSH.
- Implementa l&#39;elenco di controllo accessi (ACL) per l&#39;amministratore.
È possibile utilizzare un elenco ACL Flast Edge in combinazione con un [Frammento di codice VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) filtrare le richieste in arrivo e consentire l’accesso per indirizzo IP all’amministratore.

## Analizzare un incidente

Il primo passo dell&#39;analisi degli incidenti è quello di raccogliere il maggior numero possibile di fatti, il più rapidamente possibile. La raccolta delle informazioni relative all&#39;incidente può aiutarti a determinare la potenziale causa dell&#39;incidente. Adobe Commerce fornisce gli strumenti seguenti per assistere nell’analisi degli incidenti.

- [Registri delle azioni dell’amministratore di controllo](https://docs.magento.com/user-guide/system/action-log-report.html).
Il rapporto Registri azioni azioni visualizza un record dettagliato di tutte le azioni di amministrazione abilitate per la registrazione. Ogni record è contrassegnato con marca temporale e registra l&#39;indirizzo IP e il nome dell&#39;utente. I dettagli del registro includono i dati utente amministratore e le relative modifiche apportate durante l’azione.
- Analizzare gli eventi con il [Osservazione per lo strumento Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Lo strumento Osservazione per Adobe Commerce consente di analizzare problemi complessi per identificare le cause principali. Invece di tracciare dati diversi, puoi dedicare più tempo a correlare eventi ed errori per ottenere informazioni più approfondite sulle cause dei colli di bottiglia delle prestazioni.
Lo strumento ha lo scopo di fornire una visione chiara di alcuni dei potenziali problemi del sito per aiutare a identificare la causa principale e mantenere le prestazioni dei siti in modo ottimale. Fai clic sul collegamento alla documentazione dello strumento Osservazione per Adobe Commerce qui sopra per accedere alla documentazione dello strumento. Nella documentazione è presente una sezione che descrive tutte le informazioni disponibili nella sezione **Sicurezza** scheda .
- Analizzare i registri con [Nuovi registri delle relazioni](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). I progetti Adobe Commerce su infrastruttura cloud Pro includono [Nuovi registri delle relazioni](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) servizio. Il servizio è preconfigurato per aggregare tutti i dati di registro dagli ambienti di staging e produzione in modo da visualizzarli in un dashboard di gestione del registro centralizzato.
Puoi utilizzare il servizio Nuovi registri relazionali per completare le seguenti attività:
   - Utilizzo [Nuove query relé](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) per cercare i dati di log aggregati.
   - Visualizza i dati di log attraverso la nuova applicazione Relic Logs.

## Informazioni aggiuntive

- [Framework di analisi delle cause principali](https://sansec.io/kb/incident-response/magento-root-cause-analysis).

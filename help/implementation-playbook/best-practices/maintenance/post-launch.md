---
title: Supporto e manutenzione post-lancio
description: Garantisci prestazioni e sicurezza ottimali per il tuo store Adobe Commerce con il supporto post-lancio e le best practice per la manutenzione.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Supporto e manutenzione post-lancio per Adobe Commerce

Il supporto e la manutenzione successivi al lancio sono fondamentali per garantire il corretto funzionamento del tuo negozio Adobe Commerce, il suo buon funzionamento, la sua sicurezza e la sua capacità di continuare a soddisfare gli obiettivi aziendali. Questa fase prevede monitoraggio continuo, ottimizzazione, correzione di bug, aggiornamenti e supporto utente. Nelle sezioni seguenti viene suddiviso il supporto **post-avvio** in categorie chiave:

## Monitoraggio regolare del sito e ottimizzazione delle prestazioni

### Monitoraggio delle prestazioni

- **Test della velocità del sito e del carico**: Adobe Commerce può richiedere molte risorse, pertanto è fondamentale un monitoraggio regolare delle prestazioni.

   - **Strumenti da utilizzare**: tutti i progetti di infrastruttura cloud di Adobe Commerce includono l&#39;accesso a New Relic, che consente di monitorare le prestazioni e analizzare gli eventi all&#39;interno dell&#39;applicazione Commerce e dell&#39;infrastruttura cloud. Altri strumenti includono Google PageSpeed Insights e GTMetrix.

   - **Cosa monitorare**: ecco gli elementi principali da monitorare per Adobe Commerce sull&#39;infrastruttura cloud:

      - **Notifiche di integrità**: avvisi relativi allo spazio su disco e all&#39;integrità dell&#39;ambiente.

      - **Osservazione**: monitoraggio completo che combina dati di registro provenienti da più origini per una gestione efficace del sito.

      - **Servizio New Relic**: monitora le prestazioni in staging e produzione, concentrandosi sulle metriche chiave.

      - **Criteri avvisi gestiti**: tiene traccia delle metriche con soglie predefinite per attivare notifiche per problemi di infrastruttura o applicazioni che influiscono sulle prestazioni.

  >[!TIP]
  >
  >Consulta [monitoraggio delle prestazioni](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) nella _Guida cloud_.


- **Ottimizzazione delle prestazioni del database**: per ottimizzare le prestazioni del database in Adobe Commerce Cloud, implementare quanto segue:

   - **Monitorare e ottimizzare le query MySQL**: identificare e risolvere le query con esecuzione lenta, operazione che può essere eseguita utilizzando i comandi SHOW FULL PROCESSLIST e EXPLAIN di MySQL. Per configurazioni più complesse, gli utenti dell’architettura Pro possono utilizzare Percona Toolkit per analizzare i registri delle query per individuare eventuali problemi di prestazioni.

   - **Gestione degli indici**: verificare che ogni tabella disponga di una chiave primaria e rimuovere eventuali indici duplicati, in quanto questi possono ridurre l&#39;efficienza e causare conflitti durante le scritture simultanee.

   - **Ottimizzazione del processo Cron**: i processi Cron devono essere pianificati nelle ore di minore utilizzo per ridurre al minimo l&#39;impatto sulle prestazioni, soprattutto se sono frequenti attività in background come l&#39;indicizzazione.

  >[!TIP]
  >
  >Consulta [best practice per la risoluzione dei problemi di prestazioni del database](resolve-database-performance-issues.md).

- **Monitora CDN**: per monitorare le prestazioni della rete CDN Fastly in Adobe Commerce Cloud, è possibile effettuare le seguenti operazioni:

   - **Sfrutta New Relic per il monitoraggio**: Adobe Commerce offre New Relic per monitorare le prestazioni Fastly e altre metriche negli ambienti di staging e produzione. Questo strumento fornisce informazioni approfondite sull’integrità del server, sulla memorizzazione nella cache della rete CDN e sulle richieste di rete nel tempo, consentendo di identificare i modelli e di ottimizzare le impostazioni della rete CDN.

   - **Analisi dei registri recenti**: per i progetti Adobe Commerce Cloud Pro, è possibile utilizzare i registri di New Relic per esaminare e analizzare i dati dei registri Fastly CDN e WAF per tenere traccia delle tendenze delle prestazioni, degli eventi di sicurezza e per diagnosticare errori o problemi di latenza.

   - **Utilizza i comandi cURL**: esegui comandi cURL con intestazioni Fastly specifiche per controllare lo stato della cache del sito. Le intestazioni di risposta chiave includono `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` e `Cache-Control` per verificare lo stato del caching e del modulo. Adobe fornisce comandi cURL di esempio sia per gli ambienti di staging che per quelli di produzione.

   - **Controlla le informazioni di intestazione**: le intestazioni di Inspect come `Cache-Control`, `Pragma` e `X-Magento-Tags` consentono di confermare il comportamento di caching e la gestione dei tag appropriati nei contenuti memorizzati nella cache. I valori di intestazione corretti indicano se le configurazioni di memorizzazione in cache vengono applicate in modo efficace nella rete CDN.

   - **Debug e test rapidi**: utilizza la funzione di debug di Fastly per identificare e risolvere i problemi relativi alle percentuali di riscontri e mancati riscontri nella cache, alla logica di memorizzazione nella cache o alle risposte di intestazione non corrette, che possono indicare problemi di configurazione o un disallineamento con le regole di memorizzazione nella cache previste.

Questi passaggi di monitoraggio consentono di mantenere prestazioni CDN ottimali e di risolvere i problemi che influiscono sulla velocità e sull’affidabilità del sito.

>[!TIP]
>
>Consulta [Panoramica dei servizi Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) nella _Guida cloud_.

#### Monitoraggio regolare della sicurezza

Per mantenere un monitoraggio regolare della sicurezza in Adobe Commerce Cloud, Adobe consiglia un approccio multidimensionale che prevede l’analisi continua, la registrazione e pratiche di sicurezza proattive. Di seguito sono riportate alcune azioni principali per garantire la sicurezza continua:

- **Analisi della sicurezza**: utilizza lo strumento di analisi della sicurezza di Adobe per monitorare le vulnerabilità note e il malware nei siti Commerce. Questo strumento fornisce avvisi per potenziali rischi per la sicurezza e problemi di conformità.

- **Manutenzione regolare delle patch e degli aggiornamenti**: applica le patch e gli aggiornamenti di sicurezza di Adobe non appena diventano disponibili. L’aggiornamento alla versione più recente di Adobe Commerce garantisce le più recenti difese contro le minacce.

- **Controllo e monitoraggio dei registri**: utilizza strumenti come Registri di New Relic (disponibili per progetti Pro) per centralizzare e analizzare i registri di sicurezza dagli ambienti di staging e produzione, migliorando la visibilità di potenziali problemi e violazioni di sicurezza.

- **Gestione degli account e degli accessi**: controlla regolarmente gli account utente e amministratore per rimuovere eventuali account non autorizzati o obsoleti. Rafforzare i controlli di accesso con l’autenticazione a più fattori (MFA) per gli utenti amministratori.

- **Firewall applicazione Web (WAF)**: utilizza Fastly WAF integrato per rilevare e attenuare le minacce derivanti da modelli di traffico dannosi, ad esempio i tentativi di estrazione di dati non autorizzati.

- **Codice personalizzato e sicurezza delle estensioni**: proteggi eventuali codici personalizzati o estensioni di terze parti eseguendo controlli regolari del codice e limitando le estensioni a quelle esaminate da Adobe.

>[!TIP]
>
>Vedi [Sicurezza](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) nella _Guida dell&#39;amministratore_.

#### Registrazione e monitoraggio degli errori

Per monitorare la registrazione degli errori in Adobe Commerce Cloud, Adobe fornisce diversi strumenti e procedure per una risoluzione efficace dei problemi e una gestione efficace delle prestazioni:

- **Aggregazione dei registri con New Relic**: New Relic raccoglie e centralizza i registri dalle applicazioni Adobe Commerce, inclusi quelli relativi all&#39;infrastruttura, alla rete CDN e a WAF. Questa configurazione consente un tracciamento degli errori semplificato, la creazione di dashboard e l’esecuzione di query sui registri per ottenere informazioni più approfondite sulle prestazioni e sui problemi delle applicazioni. L’accesso ai registri di New Relic consente di cercare e filtrare i registri in base a vari attributi per diagnosticare rapidamente i problemi.

- **Tipi di log degli errori**: i log degli errori chiave in Adobe Commerce Cloud includono `cloud.log`, che contiene il feedback sulla distribuzione, e `cloud.error.log`, che registra gli avvisi e gli errori di distribuzione. Altri registri specifici per il debug includono `debug.log`, `system.log` e `exception.log`, ciascuno dei quali svolge ruoli distinti nel tracciamento degli errori e degli eventi nella piattaforma Commerce.

- **Registrazione personalizzata con Monolog**: Adobe Commerce supporta la registrazione personalizzata tramite Monolog, che consente agli sviluppatori di indirizzare i messaggi di registro a varie destinazioni, ad esempio file, database e persino avvisi. Questa flessibilità è utile per creare strategie di registrazione avanzate che soddisfino le diverse esigenze di monitoraggio negli ambienti di sviluppo e produzione.

- **Monitoraggio delle eccezioni con lo strumento di analisi a livello di sito**: lo strumento di analisi a livello di sito consente di monitorare e gestire i registri delle eccezioni, identificando i problemi ricorrenti tra gli eventi di distribuzione e applicazione. Questo strumento evidenzia i problemi frequenti, semplificando la definizione delle priorità e la risoluzione dei problemi critici che influiscono sulle prestazioni.

>[!TIP]
>
>Per ulteriori dettagli sulle procedure di registrazione e di rilevamento degli errori in Adobe Commerce Cloud, vedere [Gestione registro New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) e [Monitoraggio eccezioni](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Sicurezza e aggiornamenti

#### Patch e aggiornamenti di sicurezza

Per rimanere aggiornati e garantire la sicurezza del sistema Adobe Commerce Cloud, ecco alcune procedure chiave per il monitoraggio delle patch e degli aggiornamenti di sicurezza:

- **Iscriviti agli avvisi di sicurezza di Adobe Commerce**: resta informato sulle vulnerabilità di sicurezza [registrandoti per le notifiche da Adobe](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **Controlla le note sulla versione**: controlla regolarmente [le note sulla versione della patch di sicurezza](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), contrassegnate con &quot;-pN&quot; per le versioni (ad esempio, 2.3.5-p1), e contengono correzioni e miglioramenti critici.

- **Applica le patch di sicurezza immediatamente**: Applica le patch di sicurezza non appena sono disponibili. Ciò include l’aggiornamento alle versioni più recenti o l’applicazione di file patch specifici.

- **Usa patch cloud**: per Adobe Commerce Cloud, le patch di sicurezza possono essere raggruppate nella suite di strumenti cloud. Aggiorna la suite o la versione Commerce per ricevere queste correzioni.

- **Gestione automatizzata delle patch**: è consigliabile utilizzare strumenti come la patch centralizzata per [gestire e applicare automaticamente le patch in più archivi](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Per ulteriori dettagli e istruzioni dettagliate sull&#39;applicazione delle patch e sulla gestione della sicurezza, vedere [note sulla versione delle patch di sicurezza](../../../release/release-notes/security/overview.md) e [Come applicare le patch di sicurezza](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). È inoltre necessario esaminare i [report dello strumento di analisi a livello di sito](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access).

#### Conformità PCI

Per garantire la conformità PCI in Adobe Commerce Cloud, attenersi alle seguenti procedure chiave:

- **Dati titolare carta di credito Protect**: non memorizzare mai dati titolare carta in Adobe Commerce. Se è necessario lo storage, utilizza metodi crittografati e tokenizzati per proteggerlo.

- **Utilizza protocolli di trasmissione sicuri**: trasmette sempre i dati di pagamento tramite protocolli sicuri come TLS, con crittografia e corretta gestione delle chiavi.

- **Utilizzo di Web Application Firewall (WAF)**: il servizio WAF con tecnologia Fastly consente di soddisfare i requisiti PCI DSS 6.6 e di proteggere da vulnerabilità comuni bloccando il traffico dannoso prima che raggiunga il sito. Ulteriori informazioni [qui](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) e [qui](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Limita l&#39;accesso**: assicurati che solo il personale autorizzato abbia accesso ai dati di pagamento sensibili e [applica il controllo dell&#39;accesso per ridurre il rischio di esposizione](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Analisi della sicurezza regolare**: esegui analisi ASV PCI regolari e [monitora l&#39;ambiente](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) per risolvere potenziali vulnerabilità.

>[!TIP]
>
>Per istruzioni più dettagliate su come mantenere la conformità PCI con Adobe Commerce, consulta [best practice per l&#39;elaborazione e l&#39;archiviazione dei pagamenti](../planning/payment-processing-storage.md).

### Assistenza clienti e utenti

#### Configurazione

- **Canali di supporto**: implementare i canali di supporto clienti, ad esempio:

   - **Chat in tempo reale**: offri supporto chat in tempo reale per assistenza immediata. Le soluzioni più diffuse sono Zendesk, Intercom e Tidio.

   - **Supporto e-mail**: utilizza un sistema di ticket di supporto come Freshdesk o Zoho Desk per gestire in modo efficace le richieste dei clienti.

   - **Supporto telefonico**: se hai una base clienti ampia, puoi offrire supporto telefonico durante l&#39;orario di lavoro.

#### Admin User Training

- **Formazione interna**: forma il tuo personale su come utilizzare l&#39;amministratore Adobe Commerce, elaborare gli ordini, gestire i prodotti e gestire i problemi del servizio clienti.

- **Documentazione**: gestire una knowledge base interna o un manuale utente per le domande frequenti, la risoluzione dei problemi e le attività comuni.

#### Ottimizzazione della customer experience

- **Sondaggi e feedback**: utilizza i sondaggi per raccogliere il feedback dei clienti e ottimizzare l&#39;esperienza del cliente. Adobe Commerce supporta le integrazioni con strumenti come SurveyMonkey o Google Forms.

- **Gestione recensioni**: gestisci le recensioni e le valutazioni dei clienti sui tuoi prodotti. Incoraggiare i clienti soddisfatti a lasciare recensioni mentre rispondono alle recensioni negative in modo appropriato.

- **Personalization**: implementa funzionalità di personalizzazione, ad esempio consigli di prodotti personalizzati o promozioni mirate.

### Manutenzione e ottimizzazione continue dei negozi

#### Ottimizzazione dei motori di ricerca (SEO)

- **Ottimizzazione dei contenuti**: aggiorna regolarmente le descrizioni dei prodotti, i post di blog e le pagine di categorie per mantenere nuovi contenuti e rilevanti per i motori di ricerca.

- **Audit SEO**: esegui controlli SEO regolari utilizzando strumenti come Google Search Console o Screaming Frog per identificare i problemi SEO (ad esempio collegamenti interrotti, metadati mancanti, contenuti duplicati).

- **Struttura URL**: mantiene una struttura URL logica e pulita e assicurati che non vi siano collegamenti interrotti o reindirizzamenti.

#### Ottimizzazione del tasso di conversione (CRO)

- **Test A/B**: esegui test A/B su diversi elementi della pagina, ad esempio pagine di prodotti o processo di pagamento, per migliorare i tassi di conversione.

- **Abbandono carrello**: implementa campagne e-mail di abbandono carrello o pop-up con intento di uscita per recuperare le vendite perse.

- **Ottimizzazione dell&#39;estrazione**: semplifica il processo di estrazione riducendo il numero di passaggi e offrendo l&#39;estrazione guest per migliorare le conversioni.

#### Integrazione marketing

- **Campagne e-mail**: imposta flussi di e-mail marketing automatizzati per e-mail di benvenuto, e-mail del carrello abbandonate e follow-up post-acquisto. Adobe Piattaforme come Marketo, Mailchimp o Klaviyo si integrano bene con Adobe Commerce.

- **Integrazione di social media e annunci**: puoi integrarli con piattaforme quali Facebook, Instagram e Google Ads per eseguire campagne mirate e tenere traccia delle prestazioni.

#### Ottimizzazione per dispositivi mobili

- **Velocità di risposta mobile**: verifica regolarmente la capacità di risposta e l&#39;usabilità mobile del sito. Dato che il commercio mobile è in crescita, un approccio mobile-first è essenziale per un successo continuo.

- **Prestazioni mobili**: utilizza gli strumenti di test e prestazioni per dispositivi mobili di Google per ottimizzare l&#39;esperienza di archiviazione mobile.

### Scalabilità e sviluppo di nuove funzioni

- **Ridimensionamento automatico per la gestione del traffico**:

   - Adobe Commerce Cloud supporta il ridimensionamento automatico per regolare dinamicamente le risorse del server (ad esempio, i nodi web) in base alle esigenze di traffico in tempo reale, garantendo che il tuo store possa gestire elevati volumi di visitatori senza alcun intervento manuale. Vedi [scalabilità automatica](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) nella _Guida cloud_.

   - I livelli web e di servizio possono essere scalati in modo indipendente, aggiungendo più nodi web per aumentare il traffico e scalando i nodi di database o di servizio per le prestazioni di back-end durante i periodi di picco. Vedi [architettura ridimensionata](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) nella _Guida cloud_.

- **Monitoraggio delle prestazioni**:

   - Utilizza **New Relic** per monitorare le metriche delle prestazioni in tempo reale (ad esempio, utilizzo della CPU, livelli di traffico) e apportare le modifiche necessarie.

   - Test delle prestazioni negli ambienti di staging prima della scalabilità per evitare problemi in produzione.

- **Sviluppo di nuove funzionalità**:

   - Integra funzionalità avanzate come **Personalizzazione basata sull&#39;intelligenza artificiale**, **gestione abbonamenti** e soluzioni personalizzate.

   - Test e ottimizzazione continui delle funzionalità negli ambienti di staging prima dell’implementazione in produzione per ridurre al minimo i tempi di inattività.

- **Manutenzione in corso del sito**:

   - Esamina regolarmente i registri di sistema e le metriche delle prestazioni per identificare le aree da migliorare.

   - Garantire la scalabilità e l&#39;adattabilità dell&#39;infrastruttura ai nuovi requisiti aziendali e alla crescita.

>[!TIP]
>
>Per istruzioni dettagliate, consulta [best practice di manutenzione](overview.md), [personalizzazione](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) e [sviluppo funzionalità](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Reporting e analisi

- **Adobe Commerce Intelligence:** Commerce Intelligence, una funzionalità di base di Adobe Commerce, fornisce informazioni sulle best practice per più origini dati, consentendo agli esercenti di prendere decisioni scientifiche basate su dati e di intraprendere azioni chiare e informate. Consulta la [_Guida utente di Commerce Intelligence_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics offre una soluzione potente per monitorare, analizzare e ottimizzare le prestazioni del tuo negozio online. Adobe Analytics consente alle aziende del settore eCommerce di ottenere informazioni più approfondite sul comportamento dei clienti, sulle prestazioni dei prodotti, sui tassi di conversione e su altre metriche chiave, consentendo processi decisionali basati sui dati.

- **Google Analytics:** utilizza le Google Analytics per tenere traccia del comportamento del cliente, delle origini del traffico e dei tassi di conversione.

- **Strumenti Commerce Intelligence aggiuntivi:** Adobe Commerce include la generazione di rapporti avanzati. Questa funzione ti permette di accedere a una suite di rapporti dinamici basati sui tuoi dati relativi a prodotti, ordini e clienti, con una dashboard personalizzata in base alle tue esigenze aziendali. Per ulteriori informazioni, consulta la [creazione di rapporti avanzati](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) nella _Guida utente per amministratori_.

### Conclusione

Il supporto e la manutenzione post-lancio sono attività che richiedono un&#39;attenzione costante per garantire che il tuo negozio Adobe Commerce continui a funzionare bene, rimanga sicuro e si adatti alle esigenze della tua azienda. L’implementazione di un approccio strutturato al monitoraggio del sito, all’assistenza clienti, all’ottimizzazione e agli aggiornamenti è fondamentale per il successo a lungo termine.

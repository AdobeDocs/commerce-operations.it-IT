---
title: Sicurezza dell'infrastruttura cloud
description: 'Scopri come mantenere Adobe Commerce sulla sicurezza dell’infrastruttura cloud. '
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Sicurezza

L’architettura del piano Adobe Commerce Pro è progettata per fornire un ambiente altamente sicuro. Each customer is deployed into their own isolated server environment, separated from other customers. I dettagli di sicurezza dell&#39;ambiente di produzione sono descritti di seguito.

## Browser web

La maggior parte del traffico in entrata e in uscita dall’ambiente cloud proviene dai browser web dei consumatori. Il traffico del consumatore può essere protetto tramite HTTPS per tutte le pagine del sito web (utilizzando una certificazione SSL condivisa o il certificato SSL del cliente per un costo aggiuntivo). Checkout and account pages are always served using HTTPS. The best practice is to serve all pages under HTTPS.

## Rete per la distribuzione dei contenuti (CDN)

Offre infine una protezione CDN e DDoS (Distributed Denial of Service). La rete CDN avanzata consente di isolare l’accesso diretto ai server di origine. The public DNS only points to the Fastly Network. La soluzione DDoS di ultima generazione protegge da attacchi Layer 3 e Layer 4 altamente disturbanti e da attacchi Layer 7 più complessi. Gli attacchi Layer 7 possono essere bloccati utilizzando regole personalizzate basate sull&#39;intera richiesta HTTP/HTTPS e basate su criteri client e di richiesta, tra cui intestazioni, cookie, percorso di richiesta e IP client o indicatori come la geolocalizzazione.

## Web application firewall (WAF)

Il firewall per applicazioni Web (WAF) viene utilizzato per fornire ulteriore protezione. Fastly’s cloud-based WAF uses third-party rules from commercial and open-source sources such as the OWASP Core Ruleset. Inoltre, vengono utilizzate regole specifiche per il commercio di Adobe. I clienti sono protetti da attacchi chiave a livello di applicazione, inclusi attacchi di iniezione e input dannosi, script tra siti diversi, filtrazione dei dati, violazioni del protocollo HTTP e altre minacce OWASP Top 10.

Le regole WAF vengono aggiornate da Adobe Commerce nel caso in cui vengano rilevate nuove vulnerabilità, consentendo a Managed Services di &quot;correggere virtualmente&quot; i problemi di sicurezza prima delle patch software. Il Flast WAF non fornisce servizi di limitazione delle tariffe o di rilevamento di bot. If desired, customers can license a third-party bot-detection service compatible with Fastly.

## Virtual Private Cloud (VPC)

L’ambiente di produzione del piano Adobe Commerce Pro è configurato come Virtual Private Cloud (VPC) in modo che i server di produzione siano isolati e abbiano una capacità limitata di connettersi all’ambiente cloud e di connettersi al suo esterno. Only secure connections to the cloud servers are allowed. Secure protocols like SFTP or rsync can be used for file transfers.

I clienti possono utilizzare i tunnel SSH per proteggere le comunicazioni con l&#39;applicazione. L&#39;accesso ad AWS PrivateLink può essere fornito a pagamento. All connections to these servers are controlled using AWS Security Groups, a virtual firewall that limits connections to the environment. Le risorse tecniche dei clienti possono accedere a questi server utilizzando SSH.

## Encryption

Amazon Elastic Block Store (EBS) viene utilizzato per l&#39;archiviazione. Tutti i volumi EBS vengono crittografati utilizzando l&#39;algoritmo AES-265. Ciò significa che i dati saranno crittografati a riposo. Il sistema inoltre crittografa i dati in transito tra la CDN e l’origine e tra i server di origine. Le password del cliente vengono memorizzate come hash. Le credenziali sensibili, incluse quelle per il gateway dei pagamenti, vengono crittografate utilizzando l&#39;algoritmo SHA-256.

L’applicazione Commerce di Adobe non supporta la crittografia o la crittografia a livello di colonna o riga quando i dati non sono a riposo o non sono in transito tra i server. Il cliente può gestire le chiavi di crittografia dall&#39;interno dell&#39;applicazione. Keys used by the system are stored in AWS Key Management System and must be managed by Managed Services in order to provide parts of the service.

## Penetration testing

Managed Services esegue regolari test di penetrazione del sistema Adobe Commerce cloud con l’applicazione standard. I clienti sono responsabili di qualsiasi test di penetrazione della loro applicazione personalizzata.

## Gateway di pagamento

Adobe Commerce richiede integrazioni del gateway dei pagamenti quando i dati della carta di credito vengono trasmessi direttamente dal browser del consumatore al gateway dei pagamenti. I dati della scheda non sono mai disponibili in nessuno degli ambienti Managed Services della pianificazione Adobe Commerce Pro. Actions on the transactions by the ecommerce application are completed using a reference to the transaction from the gateway.

## applicazione Commerce di Adobe

Adobe verifica regolarmente il codice dell’applicazione di base per individuare eventuali vulnerabilità relative alla sicurezza. Patches for defects and security issues are provided to customers. Il team di sicurezza dei prodotti convalida i prodotti Commerce di Adobe seguendo le linee guida per la sicurezza delle applicazioni OWASP. Diversi strumenti di valutazione della vulnerabilità della sicurezza e fornitori esterni sono utilizzati per testare e verificare la conformità. Gli strumenti di sicurezza includono:

- Veracode Static and Dynamic Scanning
- RIPS source code scanning
- Servizi di scansione delle vulnerabilità di Trustwave e Alert Logic
- Burp Suite Pro
- OWASPZAP
- eSqlMap

L&#39;intera base di codice viene analizzata con questi strumenti su base bisettimanale. Ai clienti vengono comunicate le patch di sicurezza tramite e-mail dirette, notifiche nell&#39;applicazione e nel [Centro sicurezza](https://magento.com/security).

Customers must ensure that these patches are applied to their customized application within 30 days of release, according to the PCI guidelines. L&#39;Adobe fornisce anche uno [strumento di scansione della sicurezza](https://docs.magento.com/user-guide/magento/security-scan.html) che consente ai commercianti di monitorare regolarmente i propri siti e ricevere aggiornamenti sui rischi noti per la sicurezza, il malware e l&#39;accesso non autorizzato. Lo strumento di scansione della sicurezza è un servizio gratuito e può essere eseguito su qualsiasi versione di Adobe Commerce.

To encourage security researchers to identify and report vulnerabilities, Adobe Commerce has a [bug-bounty program](https://hackerone.com/magento) in addition to internal testing. Inoltre, il cliente viene fornito il codice sorgente completo della domanda per la propria recensione, se lo desidera.

## Read-only file system

Tutto il codice eseguibile viene distribuito in un&#39;immagine di file system di sola lettura, che riduce drasticamente le superfici disponibili per gli attacchi. Il processo di distribuzione crea un&#39;immagine Squash-FS. This approach dramatically reduces opportunities to inject PHP or JavaScript code into the system or modify the Adobe Commerce application files.

## Remote deployment

L&#39;unico modo per ottenere il codice eseguibile nell&#39;ambiente di produzione Managed Services è eseguirlo attraverso un processo di provisioning. Ciò comporta l’invio del codice sorgente dall’archivio sorgente in un archivio remoto che avvia un processo di distribuzione. Access to that deployment target is controlled, so you have complete control over who can access the deployment target. Tutte le distribuzioni del codice dell&#39;applicazione nell&#39;ambiente non di produzione sono controllate dal cliente.

## Logging

Tutte le attività AWS sono registrate in AWS CloudTrail. Linux, application server, and database logs are stored on the production servers and stored in backups. All source code changes are recorded in a Git repository. La cronologia della distribuzione è disponibile in Adobe Commerce [Project Web Interface](https://devdocs.magento.com/cloud/project/projects.html#login). All support access is logged and support sessions are recorded.

## Dati sensibili

I dati sensibili possono riguardare sia le informazioni personali dei consumatori sia i dati riservati dei clienti Managed Services. La protezione di dati sensibili relativi a clienti e consumatori è un obbligo fondamentale per Adobe Commerce Managed Services. Sia Managed Services che i nostri clienti hanno obblighi legali in relazione a informazioni personali identificabili. Oltre alle funzioni di sicurezza dell’architettura, esistono altri controlli per limitare la distribuzione e l’accesso ai dati sensibili.

Customers own their data and have control over where that data will be located. The customer specifies the location where their production and development instances reside. Specifica inoltre quale posizione verrà utilizzata per l’ambiente Magenti Business Intelligence (MBI) in combinazione con Commerce e se tale applicazione MBI ha accesso o meno a informazioni personali identificabili. Le istanze di produzione possono essere localizzate nella maggior parte delle aree AWS, mentre gli ambienti di sviluppo e MBI possono essere trovati attualmente negli Stati Uniti o nell&#39;Unione europea.

I dati sensibili possono passare attraverso la rete del server Flast CDN ma non vengono memorizzati nella rete Flast. All partners included in the Adobe Commerce Managed Services offering have contractual obligations to ensure the protection of sensitive data. Managed Services will not move sensitive customer or consumer data from the locations specified by the customer.

Per fornire i servizi inclusi nell’offerta Adobe Commerce Managed Services, lo staff Managed Services richiede l’accesso a sistemi di produzione che contengono dati sensibili. Questi dipendenti vengono addestrati in merito ai loro obblighi per proteggere i dati sensibili dei clienti e dei consumatori. L&#39;accesso a questi sistemi è limitato ai dipendenti che richiedono l&#39;accesso. Questi dipendenti hanno accesso solo per il tempo necessario per fornire questi servizi.

## Regolamento generale sulla protezione dei dati (RGPD)

Il RGPD è un quadro giuridico che stabilisce le linee guida per la raccolta e il trattamento di informazioni personali per gli individui nell’Unione europea (UE). Queste normative si applicano indipendentemente da dove si trova il sito e i visitatori dell&#39;UE hanno accesso ad esso.

In sostanza, i visitatori devono essere informati dei dati che il sito raccoglie da loro e acconsentire esplicitamente alla raccolta di informazioni. Sites must notify visitors if personal data held by the site is breached.

The merchant or company operating the site must also have a dedicated Data Protection Officer who oversees the site’s data security, and this individual (or website management team) should be available for contact should a visitor request that their data be erased.

Il RGPD richiede inoltre che qualsiasi informazione personale (come nomi, razza e data di nascita) raccolta sia anonima o pseudonimizzata.

>[!NOTE]
>
> Questa pagina è semplicemente intesa come panoramica generale di ciò che occorre considerare per il RGPD. For more information, please consult with your legal counsel or refer to the[official text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backup

I backup vengono eseguiti ogni ora per le ultime 24 ore di funzionamento. Dopo il periodo di 24 ore, i backup vengono conservati secondo la seguente pianificazione, utilizzando il servizio AWS EBS Snapshot:

| Periodo di tempo | Backup retention policy |
|----------------|-------------------------|
| Giorni da 1 a 3 | Ogni backup |
| Giorni da 4 a 6 | Un backup al giorno |
| Weeks 2 to 6 | Un backup alla settimana |
| Settimane da 8 a 12 | One biweekly backup |
| Weeks 12 to 22 | Un backup al mese |

Questo crea un backup indipendente sullo storage ridondante. Poiché i volumi EBS sono crittografati, anche i backup vengono crittografati. Additionally, Managed Services performs on-demand backups on a customer-requested basis.

L&#39;approccio di backup e ripristino di Adobe Commerce Managed Services utilizza un&#39;architettura ad alta disponibilità combinata con backup completi del sistema. Ogni progetto viene replicato, tutti i dati, il codice e le risorse, in tre aree di disponibilità AWS separate; ogni zona con un centro dati separato.

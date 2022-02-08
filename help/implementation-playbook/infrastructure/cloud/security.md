---
title: Sicurezza dell'infrastruttura cloud
description: Scopri come proteggere Adobe Commerce dall’infrastruttura cloud.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Sicurezza

L&#39;architettura della pianificazione Adobe Commerce Pro è progettata per fornire un ambiente altamente sicuro. Ogni cliente viene distribuito nel proprio ambiente server isolato, separato da altri clienti. I dettagli di sicurezza dell&#39;ambiente di produzione sono descritti di seguito.

## Browser web

La maggior parte del traffico in entrata e in uscita dall’ambiente cloud proviene dai browser web dei consumatori. Il traffico del consumatore può essere protetto tramite HTTPS per tutte le pagine del sito web (utilizzando una certificazione SSL condivisa o il certificato SSL del cliente per un costo aggiuntivo). Le pagine di estrazione e account vengono sempre servite tramite HTTPS. La best practice prevede l’utilizzo di tutte le pagine sotto HTTPS.

## Rete per la distribuzione dei contenuti (CDN)

Offre infine una protezione CDN e DDoS (Distributed Denial of Service). La rete CDN avanzata consente di isolare l’accesso diretto ai server di origine. Il DNS pubblico punta solo alla rete Flast. La soluzione DDoS di ultima generazione protegge da attacchi Layer 3 e Layer 4 altamente disturbanti e da attacchi Layer 7 più complessi. Gli attacchi Layer 7 possono essere bloccati utilizzando regole personalizzate basate sull&#39;intera richiesta HTTP/HTTPS e basate su criteri client e di richiesta, tra cui intestazioni, cookie, percorso di richiesta e IP client o indicatori come la geolocalizzazione.

## firewall per applicazioni web (WAF)

Il firewall per applicazioni Web (WAF) viene utilizzato per fornire ulteriore protezione. Il WAF basato sul cloud di Flast utilizza regole di terze parti provenienti da fonti commerciali e open source come il set di regole di base OWASP. Inoltre, vengono utilizzate regole specifiche per Adobe Commerce. I clienti sono protetti da attacchi chiave a livello di applicazione, inclusi attacchi di iniezione e input dannosi, script tra siti diversi, filtrazione dei dati, violazioni del protocollo HTTP e altre minacce OWASP Top 10.

Le regole WAF vengono aggiornate da Adobe Commerce nel caso in cui vengano rilevate nuove vulnerabilità, consentendo a Managed Services di &quot;applicare virtualmente patch&quot; ai problemi di sicurezza prima delle patch software. Il Flast WAF non fornisce servizi di limitazione delle tariffe o di rilevamento di bot. Se lo desideri, i clienti possono concedere la licenza per un servizio di rilevamento di bot di terze parti compatibile con Flast.

## Virtual Private Cloud (VPC)

L’ambiente di produzione del piano Adobe Commerce Pro è configurato come Virtual Private Cloud (VPC) in modo che i server di produzione siano isolati e abbiano una capacità limitata di connettersi all’ambiente cloud e di connettersi ad esso. Sono consentite solo connessioni sicure ai server cloud. I protocolli protetti come SFTP o rsync possono essere utilizzati per i trasferimenti di file.

I clienti possono utilizzare i tunnel SSH per proteggere le comunicazioni con l&#39;applicazione. L’accesso ad AWS PrivateLink può essere fornito a pagamento. Tutte le connessioni a questi server sono controllate utilizzando AWS Security Groups, un firewall virtuale che limita le connessioni all&#39;ambiente. Le risorse tecniche dei clienti possono accedere a questi server utilizzando SSH.

## Crittografia

Amazon Elastic Block Store (EBS) viene utilizzato per l&#39;archiviazione. Tutti i volumi EBS vengono crittografati utilizzando l&#39;algoritmo AES-265. Ciò significa che i dati saranno crittografati a riposo. Il sistema inoltre crittografa i dati in transito tra la CDN e l’origine e tra i server di origine. Le password del cliente vengono memorizzate come hash. Le credenziali sensibili, incluse quelle per il gateway dei pagamenti, vengono crittografate utilizzando l&#39;algoritmo SHA-256.

L&#39;applicazione Adobe Commerce non supporta la crittografia o la crittografia a livello di colonna o riga quando i dati non sono in stato di riposo o non sono in transito tra i server. Il cliente può gestire le chiavi di crittografia dall&#39;interno dell&#39;applicazione. Le chiavi utilizzate dal sistema sono memorizzate in AWS Key Management System e devono essere gestite da Managed Services per fornire parti del servizio.

## Prova di penetrazione

Managed Services esegue regolari test di penetrazione del sistema cloud Adobe Commerce con l’applicazione standard. I clienti sono responsabili di qualsiasi test di penetrazione della loro applicazione personalizzata.

## Gateway di pagamento

Adobe Commerce richiede integrazioni del gateway dei pagamenti quando i dati della carta di credito vengono trasmessi direttamente dal browser del consumatore al gateway dei pagamenti. I dati della scheda non sono mai disponibili in nessuno degli ambienti Managed Services pianificati da Adobe Commerce Pro. Le azioni sulle transazioni eseguite dall&#39;applicazione e-commerce vengono completate utilizzando un riferimento alla transazione dal gateway.

## applicazione Adobe Commerce

Adobe verifica regolarmente il codice dell’applicazione di base per individuare eventuali vulnerabilità relative alla sicurezza. I clienti possono accedere a patch per difetti e problemi di sicurezza. Il team di sicurezza dei prodotti convalida i prodotti Adobe Commerce seguendo le linee guida per la sicurezza delle applicazioni OWASP. Diversi strumenti di valutazione della vulnerabilità della sicurezza e fornitori esterni sono utilizzati per testare e verificare la conformità. Gli strumenti di sicurezza includono:

- Scansione statica e dinamica dei codici a barre
- Scansione del codice sorgente RIPS
- Servizi di scansione delle vulnerabilità di Trustwave e Alert Logic
- Burp Suite Pro
- OWASPZAP
- eSqlMap

L&#39;intera base di codice viene analizzata con questi strumenti su base bisettimanale. I clienti ricevono notifiche sulle patch di sicurezza tramite e-mail dirette, notifiche nell’applicazione e nella [Centro sicurezza PC](https://magento.com/security).

I clienti devono assicurarsi che queste patch siano applicate alla loro applicazione personalizzata entro 30 giorni dal rilascio, in conformità alle linee guida PCI. L’Adobe fornisce inoltre un [Strumento di scansione della sicurezza](https://docs.magento.com/user-guide/magento/security-scan.html) che consente ai commercianti di monitorare regolarmente i propri siti e ricevere aggiornamenti sui rischi noti per la sicurezza, il malware e l&#39;accesso non autorizzato. Lo strumento di scansione della sicurezza è un servizio gratuito e può essere eseguito su qualsiasi versione di Adobe Commerce.

Per incoraggiare i ricercatori sulla sicurezza a identificare e segnalare le vulnerabilità, Adobe Commerce ha un [programma bug-bounty](https://hackerone.com/magento) oltre ai test interni. Inoltre, il cliente viene fornito il codice sorgente completo della domanda per la propria recensione, se lo desidera.

## File system di sola lettura

Tutto il codice eseguibile viene distribuito in un&#39;immagine di file system di sola lettura, che riduce drasticamente le superfici disponibili per gli attacchi. Il processo di distribuzione crea un&#39;immagine Squash-FS. Questo approccio riduce notevolmente le opportunità di inserire codice PHP o JavaScript nel sistema o modificare i file dell&#39;applicazione Adobe Commerce.

## Distribuzione remota

L&#39;unico modo per ottenere il codice eseguibile nell&#39;ambiente di produzione Managed Services è eseguirlo attraverso un processo di provisioning. Ciò comporta l’invio del codice sorgente dall’archivio sorgente in un archivio remoto che avvia un processo di distribuzione. L&#39;accesso a tale destinazione di distribuzione è controllato, quindi hai il controllo completo su chi può accedere al target di distribuzione. Tutte le distribuzioni del codice dell&#39;applicazione nell&#39;ambiente non di produzione sono controllate dal cliente.

## Registrazione

Tutte le attività di AWS sono registrate in AWS Cloud Trail. I registri di Linux, di application server e di database vengono memorizzati sui server di produzione e memorizzati nei backup. Tutte le modifiche al codice sorgente vengono registrate in un archivio Git. La cronologia della distribuzione è disponibile in Adobe Commerce [Interfaccia Web progetto](https://devdocs.magento.com/cloud/project/projects.html#login). Tutte le sessioni di supporto vengono registrate e registrate.

## Dati sensibili

I dati sensibili possono riguardare sia le informazioni personali dei consumatori sia i dati riservati dei clienti Managed Services. La protezione di dati sensibili relativi a clienti e consumatori è un obbligo fondamentale per Adobe Commerce Managed Services. Sia Managed Services che i nostri clienti hanno obblighi legali in relazione a informazioni personali identificabili. Oltre alle funzioni di sicurezza dell’architettura, esistono altri controlli per limitare la distribuzione e l’accesso ai dati sensibili.

I clienti possiedono i propri dati e hanno il controllo sulla posizione in cui tali dati saranno localizzati. Il cliente specifica la posizione in cui risiedono le istanze di produzione e sviluppo. Specifica inoltre quale posizione verrà utilizzata per l’ambiente Magenti Business Intelligence (MBI) in combinazione con Commerce e se tale applicazione MBI ha accesso o meno a informazioni personali identificabili. Le istanze di produzione possono essere situate nella maggior parte delle aree geografiche di AWS, mentre gli ambienti di sviluppo e MBI possono essere trovati attualmente negli Stati Uniti o nell’Unione europea.

I dati sensibili possono passare attraverso la rete del server Flast CDN ma non vengono memorizzati nella rete Flast. Tutti i partner inclusi nell’offerta Adobe Commerce Managed Services hanno l’obbligo contrattuale di garantire la protezione dei dati sensibili. Managed Services non sposterà i dati sensibili dei clienti o dei consumatori dalle posizioni specificate dal cliente.

Per fornire i servizi inclusi nell’offerta Adobe Commerce Managed Services, lo staff Managed Services richiede l’accesso a sistemi di produzione che contengono dati sensibili. Questi dipendenti vengono addestrati in merito ai loro obblighi per proteggere i dati sensibili dei clienti e dei consumatori. L&#39;accesso a questi sistemi è limitato ai dipendenti che richiedono l&#39;accesso. Questi dipendenti hanno accesso solo per il tempo necessario per fornire questi servizi.

## Regolamento generale sulla protezione dei dati (RGPD)

Il RGPD è un quadro giuridico che stabilisce le linee guida per la raccolta e il trattamento di informazioni personali per gli individui nell’Unione europea (UE). Queste normative si applicano indipendentemente da dove si trova il sito e i visitatori dell&#39;UE hanno accesso ad esso.

In sostanza, i visitatori devono essere informati dei dati che il sito raccoglie da loro e acconsentire esplicitamente alla raccolta di informazioni. I siti devono informare i visitatori in caso di violazione dei dati personali in possesso del sito.

Il commerciante o la società che gestisce il sito deve inoltre disporre di un responsabile della protezione dei dati incaricato di sorvegliare la sicurezza dei dati del sito e tale persona (o gruppo di gestione del sito web) dovrebbe essere disponibile per il contatto qualora un visitatore richieda la cancellazione dei propri dati.

Il RGPD richiede inoltre che qualsiasi informazione personale (come nomi, razza e data di nascita) raccolta sia anonima o pseudonimizzata.

>[!NOTE]
>
> Questa pagina è semplicemente intesa come panoramica generale di ciò che occorre considerare per il RGPD. Per ulteriori informazioni, consulta il tuo consulente legale o fai riferimento al[testo ufficiale](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backup

I backup vengono eseguiti ogni ora per le ultime 24 ore di funzionamento. Dopo il periodo di 24 ore, i backup vengono conservati secondo la seguente pianificazione, utilizzando il servizio AWS EBS Snapshot:

| Periodo di tempo | Criteri di conservazione backup |
|----------------|-------------------------|
| Giorni da 1 a 3 | Ogni backup |
| Giorni da 4 a 6 | Un backup al giorno |
| Settimane da 2 a 6 | Un backup alla settimana |
| Settimane da 8 a 12 | Backup bisettimanale |
| Settimane da 12 a 22 | Un backup al mese |

Questo crea un backup indipendente sullo storage ridondante. Poiché i volumi EBS sono crittografati, anche i backup vengono crittografati. Inoltre, Managed Services esegue backup su richiesta del cliente.

L&#39;approccio di backup e ripristino di Adobe Commerce Managed Services utilizza un&#39;architettura ad alta disponibilità combinata con backup a sistema completo. Ogni progetto viene replicato, tutti i dati, il codice e le risorse, in tre aree di disponibilità AWS separate; ogni zona con un centro dati separato.

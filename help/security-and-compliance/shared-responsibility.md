---
title: Responsabilità condivisa
description: Scopri le responsabilità di sicurezza di ogni parte coinvolta nel progetto di infrastruttura cloud di Adobe Commerce.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Modello di sicurezza con responsabilità condivisa

Adobe Commerce sull’infrastruttura cloud è un’offerta PaaS (Platform-as-a-Service) che si basa su un modello di sicurezza con responsabilità condivisa. Ad Adobe, l’esercente, il fornitore di servizi cloud e il fornitore di rete di distribuzione di contenuti (CDN) hanno la responsabilità distinta di mantenere la sicurezza dell’applicazione Adobe Commerce sull’infrastruttura cloud e del codice e delle estensioni specifici dell’esercente.

Questo approccio consente ai commercianti di progettare e implementare una soluzione altamente flessibile, personalizzabile e scalabile che soddisfi al meglio le loro esigenze aziendali, riducendo al contempo le responsabilità e i costi operativi.

In generale, Adobe è responsabile dello sviluppo e della manutenzione del codice dell&#39;applicazione di base sicuro, della manutenzione della sicurezza della piattaforma, della conformità SOC 2 e PCI della piattaforma e della sua compatibilità con i componenti tecnologici compatibili con PCI (ad esempio, PHP, Redis) e della risposta ai problemi di sicurezza relativi alla piattaforma di base. Adobe è anche responsabile della collaborazione con i provider di servizi cloud e i partner CDN per risolvere eventuali problemi.

I commercianti sono responsabili della gestione di codice personalizzato sicuro e delle integrazioni con applicazioni di terze parti, della garanzia di sviluppo sicuro delle applicazioni, dell&#39;ottenimento della certificazione PCI se richiesto dal processore dei pagamenti del commerciante e della reazione e risposta agli incidenti di sicurezza.

## Adobe di responsabilità

Adobe è responsabile della sicurezza e della disponibilità dell’ambiente Adobe Commerce sull’infrastruttura cloud e del codice della soluzione principale Adobe Commerce sull’infrastruttura cloud. Inoltre, Adobe è responsabile delle attività e dei meccanismi necessari per mantenere la sicurezza della soluzione Adobe Commerce sull’infrastruttura cloud, tra cui:

- Applicazione di patch e sicurezza a livello di server per le applicazioni supportate da Adobe Commerce sull&#39;infrastruttura cloud, ad esempio l&#39;archiviazione dei dati cloud e le funzionalità di ricerca
- Esecuzione di test di penetrazione e scansione del codice principale dell’infrastruttura Adobe Commerce su cloud
- Esecuzione di revisioni/audit semestrali della soluzione di gestione dell&#39;identità e degli accessi (IAM) dei provider di servizi cloud pubblici e gestione delle autorizzazioni (requisiti di conformità PCI)
- Effettuare revisioni/audit semestrali degli utenti autorizzati, compresi i dipendenti Adobi e i contraenti (requisito di conformità PCI)
- Esecuzione di test annuali e documentazione delle funzionalità di backup e ripristino
- Configurazione dei firewall server e perimetrali
- Connessione e configurazione dell’archivio dell’infrastruttura cloud di Adobe Commerce
- Definizione, test, implementazione e documentazione dei piani di disaster recovery (DR) per le aree che rientrano nell&#39;ambito di responsabilità dell&#39;Adobe
- Definizione delle regole WAF (Global Platform Web Application Firewall)
- Protezione avanzata del sistema operativo
- Implementazione e manutenzione dell’integrazione delle soluzioni CDN (Content Distribution Network) e APM (Application Performance Management) con Adobe Commerce sull’infrastruttura cloud
- Rilascio periodico di aggiornamenti di sicurezza e di altro tipo per il codice principale dell’infrastruttura cloud di Adobe Commerce (l’applicazione di patch è responsabilità del commerciante)
- Gestione del supporto per gli esercenti e dei controlli di accesso al supporto (ad esempio, Zendesk)
- Monitoraggio, registrazione e risoluzione degli incidenti di sicurezza relativi all’infrastruttura della piattaforma Adobe Commerce su infrastruttura cloud
- Monitoraggio delle operazioni della piattaforma e fornitura di supporto 24 ore su 24, 7 giorni su 7 per Adobe Commerce sui commercianti di infrastrutture cloud
- Provisioning degli ambienti di produzione e staging
- Valutazione delle potenziali minacce per la sicurezza delle operazioni e dell&#39;infrastruttura della piattaforma
- Scalabilità di risorse informatiche, di storage, di grid computing e di altro tipo, come descritto nell&#39;accordo sui livelli di servizio (SLA) con l&#39;esercente
- Configurazione del DNS (solo Adobe Commerce su infrastruttura cloud e infrastruttura di piattaforma)
- Test della piattaforma per individuare vulnerabilità di sicurezza

Mentre Adobe mantiene la certificazione PCI per l’infrastruttura e i servizi utilizzati nel funzionamento della soluzione Adobe Commerce su infrastruttura cloud, gli esercenti sono responsabili della conformità del codice personalizzato, dei processi di sistema e di rete e dell’organizzazione.

L&#39;Adobe garantisce inoltre la disponibilità dell&#39;infrastruttura dell&#39;esercente come concordato nello SLA applicabile.

## Responsabilità del commerciante

L’esercente è responsabile del rispetto delle best practice in materia di sicurezza per la propria istanza specifica e personalizzata di Adobe Commerce sulla soluzione di infrastruttura cloud e di:

- Aggiunta all’archivio dei file di configurazione dell’infrastruttura cloud di Adobe Commerce on
- Applicazione di patch di sicurezza e di altro tipo alla soluzione personalizzata Adobe Commerce on cloud infrastructure subito dopo il rilascio per Adobe
- Applicazione di patch di sicurezza e di altro tipo a tutte le estensioni personalizzate e al codice, subito dopo il rilascio da parte del fornitore
- Creazione, distribuzione e test di file VCL di vernice personalizzati
- Progettazione, definizione di temi, installazione, integrazione e protezione della soluzione personalizzata Adobe Commerce on cloud infrastructure, incluse tutte le estensioni e il codice personalizzati
- Concessione e revoca dell’accesso utente all’istanza dell’esercente di Adobe Commerce su configurazione, applicazione e piattaforma dell’infrastruttura cloud
- Gestione dei problemi di sicurezza relativi alla rete interna del commerciante, ai server, all’infrastruttura e a qualsiasi applicazione personalizzata basata su Adobe Commerce sulla piattaforma di infrastruttura cloud
- Installazione dello strumento di integrazione della riga di comando (CLI) di Adobe Commerce su infrastruttura cloud
- Mantenimento del livello richiesto di conformità PCI dell&#39;applicazione personalizzata e di altri processi interni, come definito dalle linee guida PCI-DSS

  >[!NOTE]
  >
  >La conformità PCI dell’esercente si basa sulle certificazioni PCI di Adobe Commerce sull’infrastruttura cloud e sul provider di hosting cloud per ridurre al minimo le aree da rivedere.

- Esecuzione di analisi ASV PCI e risoluzione dei problemi nel codice e nella piattaforma principali di Adobe Commerce su infrastruttura cloud
- Monitoraggio di tutte le attività dell’applicazione che potrebbero rivelare una potenziale minaccia per la sicurezza, inclusi test di penetrazione, scansioni di vulnerabilità e registri
- Monitoraggio e risposta agli incidenti di sicurezza, inclusi analisi legali, monitoraggio e reporting relativi alla soluzione Adobe Commerce on Cloud Infrastructure e agli account utente del commerciante
- Ottenere un provider DNS e configurare e gestire tutti i record DNS specifici del commerciante
- Esecuzione dei test delle prestazioni sull&#39;applicazione personalizzata
- Protezione dell’accesso agli account della piattaforma, dell’accesso alle istanze e alle applicazioni
- Test e controllo qualità dell’applicazione personalizzata
- Mantenere la sicurezza di tutti i sistemi o reti che l’esercente si connette all’applicazione Adobe Commerce su infrastruttura cloud

## Responsabilità del fornitore di servizi cloud

Adobe si avvale di provider di servizi cloud consolidati per ospitare l’infrastruttura del server cloud per Adobe Commerce sull’infrastruttura cloud. Questi provider sono responsabili della sicurezza della rete, inclusi routing, switching e sicurezza della rete perimetrale tramite sistemi firewall e sistemi di rilevamento delle intrusioni (IDS). I fornitori di servizi cloud sono anche responsabili della sicurezza fisica dei centri dati che ospitano la soluzione Adobe Commerce su infrastruttura cloud e della sicurezza ambientale dei centri dati.

I fornitori di servizi cloud sono anche responsabili di:

- Mantenimento delle certificazioni PCI DSS, SOC 2 e ISO 27001 per i servizi cloud
- Protezione dell&#39;hypervisor
- Protezione del centro dati, compreso l&#39;accesso fisico e di rete

## Responsabilità del provider CDN

La soluzione Adobe Commerce per l’infrastruttura cloud utilizza i provider CDN per velocizzare il caricamento delle pagine, memorizzare in cache i contenuti ed eliminare immediatamente quelli obsoleti. Questi provider sono anche responsabili dei problemi di sicurezza direttamente correlati o che influiscono sulla propria rete CDN e della definizione e manutenzione delle regole WAF della rete CDN.

## Grafico delle responsabilità di sicurezza

Il seguente grafico utilizza il modello RACI (R — Responsabile, A — Responsabile, C — Consultato, I — Informato) per rappresentare visivamente ogni parte nelle responsabilità di sicurezza dell&#39;ecosistema per quanto riguarda il modello di responsabilità condivisa di Adobe Commerce sull&#39;infrastruttura cloud:

<table>
<thead>
  <tr>
    <th>Attività</th>
    <th>Adobe</th>
    <th>Commerciante</th>
    <th>Provider di servizi cloud</th>
    <th>Provider CDN</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Applicazione di Adobe Commerce sulle patch dell’infrastruttura cloud</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Applicazione di patch ai servizi di supporto<br>(ad esempio, Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definizione delle regole WAF di origine</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definizione delle regole WAF CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Distribuzione delle regole WAF della piattaforma</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuzione delle regole WAF CDN</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Correzione dei bug principali nel codice dell’infrastruttura cloud di Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Rilascio di patch per l’infrastruttura cloud di Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Scalabilità (elaborazione e archiviazione)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ridimensionamento (PaaS/grid)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Garanzia di accesso al codice sorgente, incluso repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installazione di Adobe Commerce sullo strumento CLI dell’infrastruttura cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aggiunta dei file di configurazione dell’infrastruttura cloud di Adobe Commerce all’archivio</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Creazione di un progetto per l’esercente (interfaccia utente di onboarding)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Connessione degli archivi ad Adobe Commerce sull’infrastruttura cloud</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configurazione dell’archivio di origine<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Creazione di un utente per il Release Manager (interfaccia utente di onboarding)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuzione del codice in produzione</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Distribuzione del codice nell’area di gestione temporanea</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Integrazione di applicazioni ed estensioni esterne</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installazione delle estensioni</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Personalizzazione di Adobe Commerce sull’infrastruttura cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test delle prestazioni di Adobe Commerce personalizzato sull’infrastruttura cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verifica dell’applicazione personalizzata</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Tema e progettazione dell’applicazione personalizzata</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Creazione, distribuzione e test di VCL vernicianti personalizzati</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configurazione di DNS (solo infrastruttura della piattaforma)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Sviluppo dell’estensione CDN e correzione di bug</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>CDN di onboarding</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN di supporto<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Configurazione di New Relic APM/infrastruttura</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installazione di New Relic APM/infrastruttura</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Supporto di New Relic APM/infrastruttura</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configurazione di Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Ottenimento del provider DNS (solo Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Protezione avanzata del sistema operativo</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Provisioning degli ambienti di produzione e staging</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Accesso a Zendesk per Adobe Commerce sull’infrastruttura cloud</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Risoluzione dei problemi di sicurezza degli esercenti</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Risoluzione dei problemi di sicurezza dell’infrastruttura cloud in Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Risoluzione dei problemi di sicurezza CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Risoluzione dei problemi di sicurezza APM</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Assistere gli Adobi nella ricerca sulla sicurezza (software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Assistere gli Adobi nella ricerca sulla sicurezza (scansioni/audit)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Esecuzione di scansioni PCI ASV</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correzione delle scansioni PCI di Adobe Commerce sull’infrastruttura cloud<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correzione delle scansioni PCI PaaS</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestione dei segreti del sistema operativo e della piattaforma</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestione delle chiavi di crittografia dell’infrastruttura cloud di Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Scansione di Adobe Commerce personalizzato sulle istanze dell’infrastruttura cloud</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Monitoraggio dei registri di sicurezza</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestione di IAM e autorizzazioni per Adobe Commerce sull’infrastruttura cloud</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gestione dei controlli di accesso al supporto (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Controllo del supporto e dell'accesso per gli esercenti</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test e documentazione annuali del piano di ripristino di emergenza Adobe e backup e ripristino</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Test annuali e documentazione del piano di ripristino di emergenza</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Solo se come archivio principale viene utilizzato l’archivio dell’infrastruttura cloud di Adobe Commerce. L’utilizzo di altri archivi esterni è di esclusiva responsabilità dell’esercente.</p>
      <p><sup><strong>2</strong></sup> L’Adobe fornisce supporto di livello 1 per i problemi con i provider CDN.</p>
      <p><sup><strong>3</strong></sup> Alcuni controlli Ngnix sono configurati dal commerciante per le loro applicazioni e sono di loro responsabilità.</p>
      <p><sup><strong>4</strong></sup> Per il PCI, i requisiti dei test di penetrazione sono condivisi tra Adobe e il commerciante.</p>
    </td>
  </tr>
</tfoot>
</table>

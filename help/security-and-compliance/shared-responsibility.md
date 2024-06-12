---
title: Responsabilità condivisa sicurezza e modello operativo
description: Scopri le responsabilità di sicurezza di ogni parte coinvolta nel progetto di infrastruttura cloud di Adobe Commerce.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 76aafb88855f7f41db8e57b06cf0e82370b57302
workflow-type: tm+mt
source-wordcount: '2802'
ht-degree: 0%

---

# Responsabilità condivisa sicurezza e modello operativo

Adobe Commerce sull’infrastruttura cloud è un’offerta PaaS (Platform-as-a-Service) che si basa su un modello operativo e di sicurezza con responsabilità condivisa. Queste responsabilità sono condivise tra Adobe, l’esercente, il provider di servizi cloud e il provider di rete per la distribuzione di contenuti (CDN, Content Delivery Network). Ciascuna parte ha la responsabilità distinta di proteggere e gestire l’applicazione Adobe Commerce e il codice specifico del commerciante e le estensioni implementate sull’infrastruttura cloud.

Questo modello condiviso consente ai commercianti di progettare e implementare una soluzione altamente flessibile, personalizzabile e scalabile per soddisfare i requisiti aziendali, riducendo al contempo le responsabilità e i costi operativi.

In generale, Adobe è responsabile di quanto segue:

- Sviluppo e manutenzione del codice dell&#39;applicazione di base protetto
- Mantenimento della sicurezza della piattaforma
- Garanzia che la piattaforma sia compatibile con SOC 2 e PCI e compatibile con i componenti della tecnologia PCI (ad esempio, PHP, Redis)
- Risposta alle questioni di sicurezza relative alla piattaforma principale
- Collaborazione con i provider di servizi cloud e i partner CDN per risolvere eventuali problemi

I commercianti sono responsabili di quanto segue:

- Mantenimento della sicurezza per codice personalizzato e integrazioni con applicazioni di terze parti
- Garanzia di uno sviluppo sicuro delle applicazioni
- Ottenimento della certificazione PCI se richiesto dal servizio di elaborazione dei pagamenti dell&#39;esercente
- Reazione e risposta agli incidenti di sicurezza

## Adobe di responsabilità

Adobe è responsabile della sicurezza e della disponibilità dell’ambiente Adobe Commerce sull’infrastruttura cloud e del codice della soluzione di base. Inoltre, Adobe è responsabile delle attività e dei meccanismi necessari per mantenere la sicurezza della soluzione Adobe Commerce sull’infrastruttura cloud, tra cui:

- Applicazione di patch e sicurezza a livello di server per le applicazioni supportate da Adobe Commerce sull&#39;infrastruttura cloud, ad esempio l&#39;archiviazione dei dati cloud e le funzionalità di ricerca
- Esecuzione di test di penetrazione e scansione del codice principale dell’infrastruttura Adobe Commerce su cloud
- Effettuare revisioni e audit semestrali delle soluzioni di gestione dell&#39;identità e degli accessi (IAM) dei fornitori di servizi cloud pubblici e della gestione delle autorizzazioni (requisiti di conformità PCI)
- Effettuare revisioni e audit semestrali degli utenti autorizzati, compresi i dipendenti Adobi e i contraenti (requisito di conformità PCI)
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

Adobe mantiene la certificazione PCI per l’infrastruttura e i servizi utilizzati per la soluzione Adobe Commerce.  Gli esercenti sono responsabili della conformità del codice personalizzato, dei processi di sistema e di rete e dell’organizzazione.

L&#39;Adobe garantisce inoltre la disponibilità dell&#39;infrastruttura dell&#39;esercente come concordato nello SLA applicabile.

## Responsabilità del commerciante

L’esercente è responsabile del rispetto delle best practice di sicurezza per la propria istanza specifica e personalizzata di Adobe Commerce sulla soluzione di infrastruttura cloud:

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
  >Per ridurre al minimo le aree da rivedere, la conformità PCI per l’esercente si basa sulle certificazioni PCI di Adobe Commerce e del provider di hosting cloud.

- Esecuzione di analisi ASV PCI e risoluzione dei problemi nel codice e nella piattaforma principali di Adobe Commerce su infrastruttura cloud
- Monitoraggio di tutte le attività dell’applicazione che potrebbero rivelare una potenziale minaccia per la sicurezza, inclusi test di penetrazione, scansioni di vulnerabilità e registri
- Monitoraggio e risposta agli incidenti di sicurezza, inclusi analisi legali, monitoraggio e reporting relativi alla soluzione Adobe Commerce on Cloud Infrastructure e agli account utente del commerciante
- Ottenere un provider DNS e configurare e gestire tutti i record DNS specifici del commerciante
- Esecuzione dei test delle prestazioni sull&#39;applicazione personalizzata
- Protezione dell’accesso agli account della piattaforma, dell’accesso alle istanze e alle applicazioni
- Test e controllo qualità dell’applicazione personalizzata
- Mantenere la sicurezza di tutti i sistemi o reti che l’esercente si connette all’applicazione Adobe Commerce su infrastruttura cloud

## Responsabilità del fornitore del Cloud Service

Adobe si avvale di provider di servizi cloud consolidati per ospitare l’infrastruttura del server cloud per Adobe Commerce sull’infrastruttura cloud. Questi provider sono responsabili della sicurezza della rete, inclusi routing, switching e sicurezza della rete perimetrale tramite sistemi firewall e sistemi di rilevamento delle intrusioni (IDS). I fornitori di servizi cloud sono anche responsabili della sicurezza fisica dei centri dati che ospitano la soluzione Adobe Commerce su infrastruttura cloud e della sicurezza ambientale dei centri dati.

I fornitori di servizi cloud sono anche responsabili di:

- Mantenimento delle certificazioni PCI DSS, SOC 2 e ISO 27001 per i servizi cloud
- Protezione dell&#39;hypervisor
- Protezione del centro dati, compreso l&#39;accesso fisico e di rete

## Responsabilità del provider CDN

La soluzione Adobe Commerce per l’infrastruttura cloud utilizza i provider CDN per velocizzare il caricamento delle pagine, memorizzare in cache i contenuti ed eliminare immediatamente quelli obsoleti. Questi provider sono anche responsabili dei problemi di sicurezza direttamente correlati o che influiscono sulla propria rete CDN e della definizione e manutenzione delle regole WAF della rete CDN.

## Riepilogo responsabilità di sicurezza

>[!BEGINSHADEBOX]

La tabella di riepilogo seguente utilizza il modello RACI per mostrare le responsabilità di sicurezza condivise tra Adobe, l’esercente e il provider di servizi Cloud:

**R** — Responsabile
**A** — Responsabile
**C** — Consultato
**I** — Informato

>[!ENDSHADEBOX]

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
    <td>Applicazione di patch ai servizi di supporto<br>Ad esempio, Nginx o MySQL.</td>
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
    <td>Ridimensionamento (PaaS e griglia)</td>
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
    <td>Collegamento degli archivi ad Adobe Commerce sull’infrastruttura cloud</td>
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
    <td>Configurazione delle applicazioni New Relic APM e Infrastructure</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installazione delle applicazioni New Relic APM e Infrastructure</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Supporto delle applicazioni New Relic APM e Infrastructure</td>
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
    <td>Ottenimento di un provider DNS (solo Pro)</td>
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
      <p><sup><strong>3</strong></sup> Il commerciante è responsabile di tutti i controlli Ngnix che configura per le loro applicazioni.</p>
      <p><sup><strong>4</strong></sup> Per il PCI, i requisiti dei test di penetrazione sono condivisi tra Adobe e il commerciante.</p>
    </td>
  </tr>
</tfoot>
</table>

## Riepilogo delle responsabilità operative

>[!BEGINSHADEBOX]

Le tabelle di riepilogo seguenti illustrano le responsabilità operative di Adobe e Merchants per lo sviluppo, la distribuzione, la manutenzione e la protezione di Adobe Commerce sull’infrastruttura cloud.

>[!ENDSHADEBOX]

### Codifica e sviluppo

#### Codice core di Adobe Commerce

|     | Adobe | Commerciante |
| --- | --- | --- |
| Pubblicazione di aggiornamenti e patch nella versione di base di Adobe Commerce | R |     |
| Disponibilità e applicazione di patch al file system | R |  |
| Pubblicazione di aggiornamenti e patch in ECE-Tools | R |     |
| Qualità applicazione Adobe Commerce di base | R |     |

{style="table-layout:auto"}

#### Archivio del codice

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di repo.magento.com | R |     |
| Disponibilità di Adobe Commerce sul server Git cloud | R |     |
| Altri archivi di codice selezionati dal commerciante (GitHub, Bitbucket, server Git ospitato) |     | R |

{style="table-layout:auto"}

#### Docker cloud

|     | Adobe | Commerciante |
| --- | --- | --- |
| Come rendere disponibili per il download i contenitori Docker Cloud | R |   |
| Distribuzione e configurazione di Cloud Docker (facoltativo) |     | R |
| Qualsiasi altra configurazione di sviluppo locale |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Commerciante |
| --- | --- | --- |
| Qualità costante e aggiornamento degli strumenti ECE | R |   |
| Installazione della versione più recente degli strumenti ECE |     | R |

{style="table-layout:auto"}

#### Personalizzazioni

|  | Adobe | Commerciante |
| --- | --- | --- |
| Moduli e codice personalizzati di Adobe Commerce |     | R |
| Estensioni |     | R |
| Integrazioni personalizzate |     | R |

{style="table-layout:auto"}

#### Distribuzioni

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità dell&#39;infrastruttura per la generazione e l&#39;implementazione del codice | R |   |
| Qualità continua della pipeline di configurazione per la creazione e l&#39;implementazione dell&#39;infrastruttura | R |   |
| Configurazione della distribuzione di build e contenuti statici |     | R |
| Creazione ed esecuzione del processo di governance della distribuzione: criteri e gestione delle modifiche |     | R |
| Implementazione nell’ambiente di staging |     | R |
| Implementazione nell’ambiente di produzione |     | R |
| Rollback di produzione |     | R |

{style="table-layout:auto"}

#### Sincronizzazione degli ambienti

I commercianti sono responsabili della sincronizzazione dei dati tra ambienti diversi.

#### Applicazione di patch

|     | Adobe | Commerciante |
| --- | --- | --- |
| Installazione di aggiornamenti e patch in ECE-Tools |     | R |
| Installazione di aggiornamenti e patch per Adobe Commerce Core |     | R |

#### Disponibilità del sito web

|  | Adobe | Commerciante |
| --- | --- | --- |
| Applicazione Adobe Commerce personalizzata e siti web associati |     | R |

#### Prestazioni

|     | Adobe | Commerciante |
| --- | --- | --- |
| Ottimizzazione e tuning delle applicazioni di base | R |   |
| Ottimizzazione e tuning del codice personalizzato |     | R |
| Codice Adobe Commerce personalizzato |     | R |
| Test di carico |     | R |
| Test delle prestazioni |     | R |

{style="table-layout:auto"}


#### Registri e monitoraggio

|     | Adobe | Commerciante |
| --- | --- | --- |
| Rotazione dei registri | R |   |
| Applicazione Adobe Commerce personalizzata | | R |
| Disponibilità dei servizi New Relic:<br>Integrazione di applicazioni e agenti APM, applicazione di infrastruttura,<br>Registrazione e integrazione | R |   |
| Configurazione degli avvisi di New Relic |     | R |
| Distribuzione dell&#39;agente New Relic sui server PaaS |     | R |

{style="table-layout:auto"}

#### Debug e isolamento dei problemi

|     | Adobe | Commerciante |
| --- | --- | --- |
| Debug e isolamento dei problemi | R | R |
| Supporto tempestivo del processo di debug e isolamento dei problemi |     | R |

{style="table-layout:auto"}

### Configurazione di applicazioni e servizi

#### applicazione Commerce

|     | Adobe | Commerciante |
| --- | --- | --- |
| Configurazione dell’applicazione |     | R |
| Aggiunta di domini all’applicazione Adobe Commerce (URL di base) |     | R |
| Configurazione di PaaS per l’utilizzo delle versioni dei servizi supportate dalla versione di Adobe Commerce implementata<br><br>Ad esempio, versioni diverse di Commerce sono compatibili con versioni specifiche di PHP, Redis e così via. |     | R |

{style="table-layout:auto"}

#### Pianificazione attività con processi cron

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità dei processi cron predefiniti | R | |
| Qualità continua dei processi cron personalizzati |  | R |

{style="table-layout:auto"}

#### Gestore messaggi per il framework della coda messaggi

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità del servizio RabbitMQ | R |   |
| Configurazione delle impostazioni predefinite di RabbitMQ | R |   |
| Qualità continua e applicazione di patch di RabbitMQ | R |   |
| Invia una richiesta di servizio per installare una versione di RabbitMQ compatibile con la versione di Adobe Commerce installata |   | R |

{style="table-layout:auto"}

#### servizio PHP

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di PHP | R |   |
| Configurazione delle impostazioni PHP predefinite | R |     |
| Configurazione delle impostazioni PHP personalizzate |     | R |
| Configurazione del file YAML per allineare le versioni PHP compatibili con la versione di Adobe Commerce installata |    | R |

{style="table-layout:auto"}

#### Servizi di database

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità dei servizi Galera e MariaDB | R | |
| Manutenzione continua delle impostazioni predefinite del database<br><br>(indicizzazione e ottimizzazione delle tabelle principali, ottimizzazione delle impostazioni sys-admin predefinite) | R |   |
| Manutenzione continua dei dati degli esercenti e delle impostazioni modificate<br><br>(configurazione di tabelle normalizzate e flat, indicizzazione e ottimizzazione di tabelle personalizzate e di terze parti, archiviazione o rimozione di dati, configurazione delle impostazioni di amministrazione del sistema) |     | R |
| Configurazione di Galera e MySQL | R |   |
| Qualità costante e patch di Galera e MariaDB | R |   |
| Ottimizzazione continua dell&#39;infrastruttura | R |   |
| Identificazione e correzione di query lente |     | R |
| Inviare una richiesta di servizio per installare una versione di MariaDB compatibile con la versione di Adobe Commerce installata |     | R |
| Impostazione e gestione di criteri di conservazione dei dati specifici del commerciante (i criteri di conservazione dei dati Adobe sono definiti nell’accordo per il commerciante) |     | R |

{style="table-layout:auto"}

#### Servizio CDN

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità e qualità della rete CDN | R |   |
| Configurazione rapida del servizio (tramite estensione/API) |     | R |
| Qualità dell’estensione veloce | R |   |
| Qualità dei frammenti VCL di integrazione rapida (forniti con l&#39;estensione Fastly) | R |   |
| Ottimizzazione della cache delle pagine |     | R |
| Aggiunta di domini ai servizi, alla rete CDN e all’infrastruttura | R |   |
| Snippet VCL personalizzati |     | R |
| Regole WAF e WAF | R |   |

{style="table-layout:auto"}

#### Servizio cache

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità del servizio Redis | R |   |
| Configurazione delle impostazioni predefinite di Redis | R |   |
| Qualità continua e applicazione di patch di Redis | R |   |
| Inviare una richiesta di servizio per installare una versione di Redis compatibile con la versione di Adobe Commerce installata |     | R |

{style="table-layout:auto"}

#### Servizio di ricerca

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di Elasticsearch | R |   |
| Configurazione delle impostazioni di Elasticsearch predefinite | R |   |
| Invia una richiesta di servizio per installare una versione di Elasticsearch compatibile con la versione di Adobe Commerce installata |  | R |

{style="table-layout:auto"}

#### Servizio e-mail

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità del servizio e-mail SendGrid e relativa integrazione | R |   |
| Monitorare l’utilizzo di SendGrid da parte del commerciante rispetto ai limiti | R |   |
| L’esercente è responsabile dell’utilizzo del servizio solo per le e-mail transazionali in uscita<br>Il servizio non supporta l’invio di e-mail di marketing. |     | R |
| Configurazione dei servizi e-mail di terze parti facoltativi |     | R |

{style="table-layout:auto"}

#### Servizi di terze parti

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità e qualità dei servizi forniti da terzi |     | R |

{style="table-layout:auto"}

### Estensioni di Commerce Services

#### Servizio di reporting anticipato

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di Advanced Reporting Service | R |   |
| La configurazione di Advanced Reporting è conforme ai Termini e Condizioni di Advanced Reporting |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità dei servizi di Business Intelligence Adobe Commerce | R |   |
| Processi di sincronizzazione dati MBI | R |   |
| Rilevamento problemi di sincronizzazione MBI | R |   |
| Configurazione della sincronizzazione dei dati MBI con Adobe Commerce Cloud Pro, Starter, On-Premises o non Adobe Commerce<br>(API, qualità e formattazione dei dati, rete commerciale,<br>Connessioni DB sia all&#39;interno che all&#39;esterno di Adobe Commerce Cloud DB, oltre le soglie dati) |     | R |
| Configurazione della sincronizzazione dei dati MBI con Adobe Commerce Cloud Pro<br>(configurazione del database di Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

#### Recommendations del prodotto

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità del servizio Recommendations del prodotto | R |   |

{style="table-layout:auto"}

### Servizi di rete

#### Ottimizzazione immagine

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità e qualità dell&#39;ottimizzazione delle immagini | R |  |
| Configurazione dell’ottimizzazione immagine |     | R |

{style="table-layout:auto"}

#### Certificati SSL

|     | Adobe | Commerciante |
| --- | --- | --- |
| Certificato dedicato SSL - scadenza | R |  |
| Provisioning dei certificati SSL | R |  |
| Acquisto e manutenzione di certificati SSL EV/specifici (diversi dai valori predefiniti forniti) e fornitura all&#39;Adobe |     | R |

{style="table-layout:auto"}

#### Firewall applicazione Web (WAF)

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità e configurazione di WAF | R |  |
| Risoluzione dei falsi positivi della regola WAF | R | |
| Segnalazione dei falsi positivi della regola WAF |     | R |
| Ottimizzazione regole WAF (NON SUPPORTATA) |     |     |
| Registri WAF/CDN |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Commerciante |
| --- | --- | --- |
| Blocco IP proattivo |     | R |
| Protezione bot |     | R |
| Rilevamento DDOS - Livello 3-4 | R |   |
| Rilevamento DDOS - livello 7 |     | R |
| Risposta DDOS | R |   |
| Configurazione di Fastly Extension Rate Limiting e Bot Protection (Limited) |     | R |

{style="table-layout:auto"}

#### Collegamento privato

|     | Adobe | Commerciante |
| --- | --- | --- |
| Configurazione e manutenzione delle connessioni PrivateLink (se utilizzate) con un VPC di proprietà dell&#39;Adobe | R |   |
| Configurazione e manutenzione delle connessioni PrivateLink (se utilizzate) con un VPC di proprietà del commerciante |     | R |
| Disponibilità di SSH (collegamento non privato) | R |   |
| Configurazione di PrivateLink in entrata nell’endpoint del servizio Adobe Commerce Cloud | R |   |
| Accettazione di PrivateLink in entrata all’endpoint del servizio Adobe Commerce Cloud |     | R |
| Configurazione di PrivateLink in entrata nell’endpoint del servizio VPC dell’esercente |     | R |
| Accettazione di PrivateLink in entrata all&#39;endpoint del servizio VPC del commerciante | R |   |
| Configurazione delle integrazioni PrivateLink (da endpoint a account) |     | R |
| Configurazione del VPC di proprietà del commerciante per l’endpoint PrivateLink<br><br> (comprese eventuali connessioni VPN) |     | R |

{style="table-layout:auto"}

### Sistema e infrastruttura

#### Server app

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di Nginx | R |   |
| Configurazione di Nginx | R |   |
| Qualità costante e applicazione di patch di Nginx | R |   |

{style="table-layout:auto"}

#### Sistema operativo

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità del sistema operativo | R |   |
| Qualità costante e applicazione di patch al sistema operativo | R |   |

{style="table-layout:auto"}

#### Backup, elevata disponibilità e failover

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di copie istantanee e processo di backup | R |   |
| Pianificazione dei backup per gli ambienti di staging e produzione di Cloud Pro | R |   |
| Pianificazione dei backup per gli ambienti di integrazione di Cloud Starter e Pro |     | R |
| Disponibilità di HA/Failover | R |   |

{style="table-layout:auto"}

#### Server cloud e scalabilità

|     | Adobe | Commerciante |
| --- | --- | --- |
| Disponibilità di risorse CPU, data center e spazio su disco | R |   |
| Disponibilità ed esecuzione di capacità di sovratensione o di sovradimensionamento di emergenza | R |   |
| Richiesta della capacità di sovratensione |     | R |
| Monitoraggio dell’utilizzo di vCPU rispetto ai limiti | R |   |

{style="table-layout:auto"}

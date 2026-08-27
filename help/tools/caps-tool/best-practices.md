---
title: Guida alle best practice di [!DNL Adobe Commerce Patching Automation]
description: Scopri come utilizzare  [!DNL Adobe Commerce Patching Automation]  per pianificare, convalidare e applicare le patch in modo sicuro, riducendo al minimo i rischi di distribuzione e le interruzioni dei servizi.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Guida alle best practice di [!DNL Adobe Commerce Patching Automation]

Le procedure consigliate seguenti sono essenziali per il corretto funzionamento e la sicurezza delle operazioni di patch con [!DNL Adobe Commerce Patching Automation]. Questa guida fornisce procedure ottimali complete per operazioni patch efficaci, gestione dell&#39;ambiente ed eccellenza operativa.

## Best practice pre-patch

### Preparazione all’ambiente

**Best practice:** Prepara sempre accuratamente l&#39;ambiente prima di applicare le patch per garantire il successo delle operazioni e ridurre al minimo i rischi.

Prima di applicare le patch, verificare che l&#39;ambiente sia preparato correttamente:

* **Account Adobe Commerce Cloud**
  * Abbonamento Adobe Commerce Cloud attivo
  * Licenza Adobe Commerce valida
  * [Chiavi di autenticazione compositore](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/authentication-keys) configurate per accedere all&#39;archivio Adobe Commerce
  * Autorizzazioni per progetti e ambienti

* **Risorse di ambiente**
  * Il progetto è in grado di creare un ambiente di integrazione attivo aggiuntivo per l&#39;operazione patch. Per informazioni sui limiti dell&#39;ambiente attivo, vedere [Gestione dei rami con Cloud Console](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/project/console-branches).
  * Risorse di storage, CPU e memoria sufficienti
  * Accesso di rete agli archivi di Adobe
  * Ambiente padre stabile per la sincronizzazione

* **Preparazione dell&#39;ambiente di produzione** (per l&#39;applicazione di patch di produzione)
  * Abilita modalità di manutenzione
  * Disabilita processi Cron
  * Stabilire le procedure della finestra di manutenzione
  * Procedure di ripristino documenti
  * Preparare il piano di comunicazione per le parti interessate

## Best practice per l’applicazione delle patch

### Tempistica e programmazione

**Best practice:** pianifica le operazioni patch durante i periodi a traffico ridotto e coordina con le parti interessate per ridurre al minimo l&#39;impatto aziendale.

**Scegliere l&#39;ora corretta per l&#39;applicazione patch:**

* **Periodi a traffico ridotto**
  * Programmare le patch nelle ore di minore utilizzo
  * Evitare di applicare patch durante eventi con traffico elevato
  * Pianifica i potenziali tempi di inattività durante la convalida

* **Considerazioni sull&#39;ambiente di produzione**
  * **Intervalli di manutenzione** - Pianificazione delle patch di produzione durante gli intervalli di manutenzione pianificati
  * **Comunicazione ai clienti** - Notifica ai clienti la modalità di manutenzione e i tempi di inattività previsti
  * **Coordinamento team** - Assicurarsi che tutti i membri del team siano a conoscenza della pianificazione della manutenzione
  * **Preparazione rollback** - Disponi membri del team per il rollback immediato, se necessario

### Monitoraggio e convalida

**Durante le operazioni patch:**

* **Monitorare l&#39;avanzamento**
  * Controllo dello stato operativo in tempo reale
  * Presta attenzione a eventuali avvisi o errori
  * Non interrompere il processo una volta avviato

* **Convalida risultati**
  * Test delle funzionalità critiche dopo il completamento dell&#39;applicazione
  * Controllare le metriche delle prestazioni per verificare eventuali peggioramenti
  * Verificare che le misure di sicurezza rimangano intatte

## Best practice per la post-patch

### Verifica e prove

**Best practice:** verifica sempre il successo dell&#39;applicazione patch tramite test e monitoraggio completi per garantire la stabilità e la funzionalità del sistema.

**Dopo il completamento dell&#39;applicazione patch:**

* **Test funzionali**
  * Test di tutti i processi aziendali critici
  * Verifica dei flussi di pagamento e di pagamento
  * Verifica funzionalità del pannello di amministrazione

* **Monitoraggio delle prestazioni**
  * Monitorare i tempi di caricamento delle pagine
  * Verifica prestazioni del database
  * Monitora eventuali picchi di utilizzo delle risorse

* **Convalida sicurezza**
  * Verificare che le funzioni di sicurezza funzionino
  * Verifica la presenza di nuove vulnerabilità di sicurezza
  * Test di autenticazione e autorizzazione

## Best practice per l’ambiente di produzione

### Test di pre-produzione

**Best practice:** non applicare mai le patch direttamente alla produzione senza eseguire test approfonditi in ambienti di pre-produzione che rispecchiano la configurazione di produzione.

**Verifica sempre le patch prima della distribuzione di produzione:**

* **Configurazione ambiente di prova**
  * Utilizzare gli ambienti di staging o integrazione per i test
  * Garantire il mirroring della configurazione di produzione nell&#39;ambiente di test
  * Se possibile, esegui test con dati di tipo produzione

* **Test completi**
  * Test di tutti i processi aziendali critici
  * Verifica dei flussi di pagamento e di pagamento
  * Verifica funzionalità del pannello di amministrazione
  * Testare eventuali integrazioni personalizzate

* **Test delle prestazioni**
  * Monitorare l&#39;impatto delle patch sulle prestazioni
  * Controllare eventuali peggioramenti delle prestazioni
  * Verificare che l&#39;utilizzo delle risorse rimanga accettabile

### Attenuazione dei rischi

**Riduci al minimo i rischi durante l&#39;applicazione della patch di produzione:**

* **Piano di comunicazione**
  * Notifica ai clienti le finestre di manutenzione
  * Tieni informati le parti interessate dei progressi
  * Disponi procedure di riassegnazione pronte

* **Strategia di rollback**
  * Come ripristinare rapidamente le patch, se necessario
  * Disponibilità dei membri del team per una risposta immediata
  * Procedure di ripristino documenti

* **Monitoraggio e avvisi**
  * Imposta monitoraggio per problemi post-patch
  * Avvisi per errori critici
  * Monitorare attentamente le metriche delle prestazioni

## Riepilogo delle best practice chiave

### Best practice critiche per il successo di [!DNL Patching Automation]

* Esegui sempre il test in pre-produzione prima di applicare patch agli ambienti di produzione
* Attiva la modalità di manutenzione e disattiva i processi cron per le operazioni patch di produzione
* Monitora attentamente le operazioni e dispone di procedure di ripristino pronte
* Documentare tutte le operazioni di patch e conservare record completi
* Seguire le procedure di gestione delle modifiche appropriate e ottenere le approvazioni appropriate
* Mantieni gli ambienti sincronizzati e mantieni la corretta allocazione delle risorse
* Stabilire procedure di supporto chiare e mantenere la formazione del team
* Analisi e miglioramento periodici dei processi di gestione delle patch

## Argomenti correlati

* [Introduzione all’automazione dell’applicazione di patch](intro.md)
* [Come accedere](access.md)
* [Panoramica del flusso di lavoro](workflow.md)
* [Integrazione GitHub](github-integration.md)
* [Risoluzione dei problemi](troubleshooting.md)

---
title: '[!DNL Adobe Commerce Patching Automation]'
description: Scopri  [!DNL Adobe Commerce Patching Automation], i suoi utilizzi, come accedervi e le best practice per l'applicazione automatica delle patch
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation] è uno strumento che automatizza il processo di applicazione e ripristino delle patch per gli ambienti Adobe Commerce on Cloud. Offre agli amministratori di progetti Commerce un flusso di lavoro semplificato per applicare e ripristinare le patch. La convalida e i controlli di integrità integrati contribuiscono a garantire la stabilità e la sicurezza degli ambienti Cloud.

Questa guida è stata progettata per i commercianti e i partner di Adobe Commerce Cloud che desiderano semplificare il processo di applicazione delle patch, ridurre il rischio di problemi correlati alle patch, migliorare la sicurezza e la stabilità dell’ambiente e automatizzare le operazioni di routine delle patch.

## [!DNL Patching Automation] argomenti

* **[Come accedere](access.md)**
* **[Panoramica del flusso di lavoro](workflow.md)**
* **[Integrazione GitHub](github-integration.md)**
* **[Best practice](best-practices.md)**
* **[Risoluzione dei problemi](troubleshooting.md)**

## Panoramica dello strumento

* **Interfaccia interfaccia utente**
  * Disponibilità e visualizzazione dello stato delle patch in tempo reale per combinazioni specifiche di progetto e ambiente
  * Informazioni complete sullo stato dell&#39;applicazione delle patch, con informazioni sullo stato di avanzamento, sugli errori e su qualsiasi altro messaggio rilevante
  * [!UICONTROL Patch Management Dashboard] per:
    * Visualizzazione delle patch disponibili
    * Applicazione delle patch con un solo clic
    * Ripristino delle patch applicate in precedenza
    * Monitoraggio dello stato e dei risultati dell’operazione patch

* **Servizio di applicazione automatica delle patch con flusso di lavoro strutturato**
  * **Verifica preliminare** - Convalida la compatibilità della patch e la preparazione all&#39;ambiente
  * **Applicazione di patch** - Applica o ripristina automaticamente le patch negli ambienti di integrazione
  * **Convalida** - Esegue un controllo di integrità per confermare l&#39;avvio dell&#39;applicazione e che le connessioni al database e alla cache sono raggiungibili

* **Funzioni di sicurezza**
  * Convalida la compatibilità della patch prima dell&#39;applicazione
  * Applica prima la patch in un ambiente di integrazione temporaneo, confermando che viene distribuita correttamente e superando un controllo di integrità, prima di unirla nell’ambiente di destinazione, quindi esegue un controllo di integrità finale subito dopo la distribuzione.
  * Applica le patch alla cartella `m2-hotfixes` con rimozione automatica durante la reversione

## Integrazioni con Adobe Commerce Cloud

[!DNL Patching Automation] è completamente integrato con l&#39;infrastruttura Adobe Commerce Cloud e funziona perfettamente con gli ambienti cloud esistenti. Sfrutta le funzioni native per il cloud per prestazioni ottimali, fornisce funzioni dettagliate di registrazione e monitoraggio e si integra con gli strumenti di supporto di Adobe Commerce Cloud.

## Tutorial video

Scopri [!DNL Adobe Commerce Patching Automation] e come questo strumento consente agli utenti di trovare e applicare rapidamente le patch di sicurezza. Il video seguente illustra come accedervi tramite il dashboard dello strumento di analisi a livello di sito (SWAT), scegliere il progetto e l’ambiente e applicare le patch con un clic.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Casi d’uso comuni

* **Patch di sicurezza** - Applicazione rapida degli aggiornamenti di sicurezza critici
* **Rollback delle patch** - Ripristino sicuro delle patch problematiche applicate tramite il servizio
* **Conformità in materia di sicurezza** - Mantenimento degli standard di sicurezza con l&#39;applicazione automatica delle patch
* **Stabilità operativa** - Conferma l&#39;avvio dell&#39;applicazione e supera un controllo di integrità dopo ogni operazione patch

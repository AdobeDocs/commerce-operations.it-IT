---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Scopri  [!DNL Cloud Automation Patching Service (CAPS)], i suoi utilizzi, come accedervi e le best practice per l'applicazione automatica delle patch
hide: true
hidefromtoc: true
source-git-commit: 4bb2d597e93379dbe81bae100ccc0b94b39acf26
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

[!DNL Cloud Automation Patching Service] ([!DNL CAPS]) è uno strumento che automatizza il processo di applicazione e ripristino delle patch per gli ambienti Adobe Commerce on Cloud. Offre agli amministratori di progetti Commerce un flusso di lavoro semplificato per applicare e ripristinare le patch, che include verifiche di integrità e convalida integrate per garantire la stabilità e la sicurezza degli ambienti Cloud.

Questa guida è stata progettata per i commercianti e i partner di Adobe Commerce Cloud che desiderano semplificare il processo di applicazione delle patch, ridurre il rischio di problemi correlati alle patch, migliorare la sicurezza e la stabilità dell’ambiente e automatizzare le operazioni di routine delle patch.

## [!DNL CAPS] argomenti

* **[Come accedere](access.md)**
* **[Flusso di lavoro](workflow.md)**
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
   * **Convalida** - Esegue controlli di integrità e assicura che le funzionalità critiche non siano interessate

* **Funzioni di sicurezza**
   * Crea ambienti di integrazione temporanei per il test
   * Convalida la compatibilità della patch prima dell&#39;applicazione
   * Fornisce il rollback automatico in caso di errori di convalida
   * Applica le patch alla cartella `m2-hotfixes` con rimozione automatica durante la reversione

## Integrazioni con Adobe Commerce Cloud

[!DNL CAPS] è completamente integrato con l&#39;infrastruttura Adobe Commerce Cloud e funziona perfettamente con gli ambienti cloud esistenti. Sfrutta le funzioni native per il cloud per prestazioni ottimali, fornisce funzioni dettagliate di registrazione e monitoraggio e si integra con gli strumenti di supporto di Adobe Commerce Cloud.

## Tutorial video

Scopri Adobe Cloud Automated Patching Service e come questo strumento aiuta gli utenti a trovare e applicare rapidamente le patch di sicurezza. Il video seguente illustra come accedervi tramite la dashboard SWAT, scegliere il progetto e l’ambiente e applicare le patch con un clic.

>[!VIDEO](https://video.tv.adobe.com/v/3476255/?captions=ita&learn=on&enablevpops)

## Casi d’uso comuni

* **Patch di sicurezza** - Applicazione rapida degli aggiornamenti di sicurezza critici
* **Rollback delle patch** - Ripristino sicuro delle patch problematiche applicate tramite [!DNL CAPS]
* **Conformità in materia di sicurezza** - Mantenimento degli standard di sicurezza con l&#39;applicazione automatica delle patch
* **Stabilità operativa** - Garantire la stabilità dell&#39;ambiente tramite la convalida automatica

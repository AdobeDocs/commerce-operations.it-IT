---
title: Panoramica del flusso di lavoro [!DNL Adobe Commerce Patching Automation]
description: Scopri il processo del flusso di lavoro  [!DNL Adobe Commerce Patching Automation] , inclusa la terminologia, le fasi del flusso di lavoro e le operazioni per la gestione automatizzata delle patch.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Panoramica del flusso di lavoro [!DNL Adobe Commerce Patching Automation]

In questo argomento viene fornita una panoramica di alto livello sul funzionamento delle operazioni patch con [!DNL Adobe Commerce Patching Automation].

## Terminologia

* **Operazioni** - le azioni principali eseguite dal servizio:
  * Applica
  * Ripristina
* **Fasi** - le tre fasi del flusso di lavoro:
  * Verifica preliminare
  * Applicazione di patch
  * Convalida
* **Ambiente**: l&#39;ambiente Adobe Commerce Cloud in cui vengono applicate le patch.

## Operazioni

[!DNL Patching Automation] supporta due *operazioni* principali per la gestione delle patch nell&#39;ambiente Adobe Commerce Cloud:

* **Operazione Apply** - aggiunge modifiche patch alla base di codice tramite un processo sicuro e convalidato. Le patch vengono applicate inserendo i file patch nella cartella `m2-hotfixes`.

* **Operazione Ripristina**: rimuove le patch applicate in precedenza dal codebase rimuovendo i file di patch dalla cartella `m2-hotfixes`.

>[!IMPORTANT]
>
>Le operazioni di ripristino sono disponibili solo per le patch originariamente applicate tramite [!DNL Patching Automation]. Le patch applicate manualmente o tramite altri metodi non possono essere ripristinate con questo servizio.

## Fasi

Il flusso di lavoro [!DNL Patching Automation] utilizza tre *fasi* che vengono sempre eseguite in questo ordine per garantire che le patch vengano applicate in modo sicuro e affidabile:

* **Verifica preliminare** - convalida la compatibilità della patch e l&#39;idoneità dell&#39;ambiente.
* **Applicazione della patch** - applica o ripristina la patch in un ambiente di integrazione.
* **Convalida**: convalida l&#39;applicazione patch ed esegue i controlli di integrità.

## Dettagli fase

### Fase 1: Controllo preliminare

La fase di verifica preliminare verifica che la patch possa essere applicata in modo sicuro all’ambiente.

**Cosa succede:**

* **Protezione dell&#39;ambiente di produzione** (solo ambienti di produzione):
  * Controlla se l’archivio è in modalità di manutenzione
  * Verifica che i processi cron siano disabilitati
  * Blocca l’applicazione della patch se non vengono soddisfatte le condizioni
  * Visualizza la finestra di dialogo di conferma se vengono soddisfatte le condizioni
* **Convalida patch** - verifica che il file di patch sia valido e compatibile
* **Valutazione dell&#39;ambiente** - verifica la fattibilità dell&#39;ambiente e le risorse
* **Rilevamento conflitti** - identifica potenziali conflitti con il codice esistente
* **Verifica dipendenze** - convalida la compatibilità della versione di Adobe Commerce

### Fase 2: applicazione di patch

La fase di applicazione delle patch applica o ripristina la patch in un ambiente di integrazione temporaneo. Durante questa fase, il servizio crea un ambiente di integrazione temporaneo per applicare in modo sicuro la patch, confermarne la corretta distribuzione e verificare che superi un controllo di integrità, prima di apportare qualsiasi modifica all’ambiente effettivo.

Questo approccio fornisce:

* **Sicurezza** - mantiene l&#39;ambiente di destinazione intatto fino a quando l&#39;ambiente di integrazione non viene distribuito correttamente e non supera il controllo di integrità
* **Funzionalità di rollback** - se vengono rilevati problemi
* **Isolamento** - per ogni operazione patch

#### Fase 2a: creazione di un ambiente di integrazione

**Creazione ramo** - [!DNL Patching Automation] crea un ramo dell&#39;ambiente di integrazione temporaneo denominato `{target-environment}-CAPS-{patch-id}`

**Configurazione dell&#39;ambiente** - L&#39;ambiente di integrazione viene creato come elemento secondario dell&#39;ambiente di destinazione

**Sincronizzazione del codice** - L&#39;ambiente di integrazione eredita lo stato esatto del codice dell&#39;ambiente di destinazione (stessa base di codice)

**Nessuna clonazione dei dati** - L&#39;ambiente di integrazione non riceve una copia dei dati dell&#39;ambiente di destinazione (database, supporto o altro contenuto archiviato). Per applicare e verificare la patch viene utilizzata solo la base di codice

**Fabbisogni di risorse** - La capacità di archiviazione totale del progetto Cloud è definita nel contratto. (Controllare tramite la pagina dell&#39;account o `magento-cloud subscription:info`). L&#39;allocazione del disco di ogni ambiente è configurata separatamente tramite la proprietà `disk` in `.magento.app.yaml`/`.magento/services.yaml`. Per ulteriori dettagli, vedere [Gestione spazio su disco](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space). Se un&#39;operazione di patch non riesce a causa di limiti di archiviazione, controllare l&#39;utilizzo del disco (`magento-cloud db:size` / `magento-cloud mount:size`) dell&#39;ambiente di integrazione rispetto all&#39;allocazione configurata.

#### Fase 2b: applicazione patch nell’ambiente di integrazione

**Test di sicurezza** - La patch viene applicata all&#39;ambiente di integrazione, non direttamente all&#39;ambiente di destinazione

**Gestione file** - I file di patch vengono inseriti nella cartella `m2-hotfixes`

**Operazioni Git** - Le modifiche vengono applicate e inviate al ramo dell&#39;ambiente di integrazione

**Attivazione ambiente** - L&#39;ambiente di integrazione è attivato per distribuire il codice con patch

**Verifica stato** - Dopo l&#39;attivazione, [!DNL Patching Automation] conferma quanto segue prima di procedere all&#39;unione: l&#39;ambiente di integrazione è stato distribuito correttamente ed è integro, l&#39;applicazione viene avviata e le connessioni al database e alla cache sono raggiungibili.

>[!NOTE]
>
>Se il progetto utilizza un archivio GitHub esterno, il servizio gestisce automaticamente l&#39;autenticazione utilizzando l&#39;[[!DNL Patching Automation] app GitHub](github-integration.md). Non sono necessarie credenziali aggiuntive oltre all’installazione dell’app.

#### Fase 2c: unione dell’ambiente di destinazione

**Controllo sincronizzazione** - Prima dell&#39;unione, il servizio conferma che l&#39;ambiente di integrazione è ancora attivo, sincronizzato con l&#39;ambiente di destinazione e integro. Se la destinazione è stata modificata durante l&#39;applicazione della patch, l&#39;operazione si arresta qui anziché unire

**Estrazione dell&#39;ambiente** - Il servizio estrae l&#39;ambiente di destinazione localmente

**Operazione di unione** - Il ramo dell&#39;ambiente di integrazione è unito all&#39;ambiente di destinazione

**Gestione dei conflitti** - Se si verifica un conflitto di unione, l&#39;operazione non riesce e viene segnalata come errore. L&#39;operazione non viene risolta automaticamente

**Distribuzione** - Le modifiche unite vengono distribuite nell&#39;ambiente di destinazione

**Verifica** - Il servizio verifica che l&#39;unione sia avvenuta correttamente e che gli ambienti siano sincronizzati

### Ciclo di vita dell’ambiente di integrazione

Gli ambienti di integrazione hanno un ciclo di vita specifico durante la fase di applicazione delle patch:

* **Creazione** - Creato all&#39;inizio della fase di applicazione della patch
* **Periodo attivo** - Rimane attivo durante l&#39;applicazione della patch e il test
* **Pulizia** - Eliminato immediatamente se l&#39;operazione non riesce durante la fase di esecuzione delle patch, prima dell&#39;unione. Altrimenti eliminato durante la fase di convalida, dopo l’unione, indipendentemente dal fatto che la convalida venga superata o meno

### Fase 3: Convalida

La fase Convalida conferma che l&#39;applicazione aggiornata viene avviata correttamente e supera un controllo di integrità.

**Cosa succede:**

* **Verifica stato dell&#39;applicazione** - verifica che l&#39;applicazione venga avviata e eseguita correttamente e che le connessioni al database e alla cache siano raggiungibili
* **Pulizia** - rimuove l&#39;ambiente di integrazione temporaneo e aggiorna lo stato del processo in base al completamento. L’attività dell’ambiente rimane visibile nel feed Attività del progetto.

>[!IMPORTANT]
>
>A differenza delle fasi 1 e 2, questo controllo di integrità viene eseguito *dopo* che la patch è già stata unita all&#39;ambiente di destinazione. Se l&#39;operazione ha esito negativo, non viene eseguito automaticamente il rollback dell&#39;unione. L’ambiente di destinazione può essere lasciato in uno stato di interruzione ed è necessario un intervento manuale (ad esempio il ripristino della patch) per ripristinarla. Per ulteriori informazioni su come risolvere i problemi, vedere [Risoluzione problemi](troubleshooting.md).

## Indicatori di successo

**Applica operazione:**

* &quot;Processo completato correttamente&quot; - Patch applicata senza problemi
* &quot;La patch è stata applicata&quot; - La patch era già presente (non è necessaria alcuna azione)
* File patch inserito correttamente nella cartella `m2-hotfixes`
* Tutti i controlli di convalida superano
* Controlli di integrità dell&#39;applicazione completati

**Operazione di ripristino:**

* &quot;Processo completato correttamente&quot; - Patch ripristinata senza problemi
* &quot;La patch è stata ripristinata&quot; - La patch era già stata ripristinata (nessuna azione necessaria)
* File patch rimosso dalla cartella `m2-hotfixes`
* Tutti i controlli di convalida superano
* Controlli di integrità dell&#39;applicazione completati

## Salvaguardie dell’ambiente di produzione

L&#39;applicazione o il ripristino delle patch in un ambiente di produzione comporta maggiori rischi rispetto ad altri ambienti, pertanto [!DNL Patching Automation] include due misure di protezione specifiche per la produzione.

### Conferma prima dell’avvio

Prima di avviare qualsiasi operazione di applicazione o ripristino in un ambiente di produzione, viene richiesto di confermare l’operazione in una finestra di dialogo. Questo passaggio di conferma protegge dall’avvio accidentale di un processo in produzione.

### Condizioni preliminari consigliate

Adobe consiglia di abilitare la modalità di manutenzione e disabilitare i processi cron prima di applicare le patch a un ambiente di produzione. Per impostazione predefinita, [!DNL Patching Automation] verifica che entrambe le condizioni siano soddisfatte e blocca l&#39;operazione con una notifica se una delle due condizioni non è soddisfatta. Se comprendi i rischi di procedere senza modalità di manutenzione o con i processi cron abilitati, seleziona la casella di controllo Sostituisci nell’interfaccia utente per ignorare questa verifica.

* **Modalità manutenzione** - Si consiglia di abilitare
* **Processi Cron** - Consigliato per essere disabilitato

## Argomenti correlati

* [Introduzione all’automazione dell’applicazione di patch](intro.md)
* [Come accedere](access.md)
* [Integrazione GitHub](github-integration.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)

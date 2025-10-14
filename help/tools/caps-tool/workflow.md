---
title: Come funziona  [!DNL Cloud Automation Patching Service (CAPS)]  flusso di lavoro
description: Scopri il processo del flusso di lavoro  [!DNL Cloud Automation Patching Service (CAPS)] , inclusa la terminologia, le fasi del flusso di lavoro e le operazioni per la gestione automatizzata delle patch.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Funzionamento del flusso di lavoro [!DNL Cloud Automation Patching Service (CAPS)]

In questo argomento viene fornita una panoramica di alto livello sul funzionamento delle operazioni patch con [!DNL CAPS (Cloud Automation Patching Service)].

## Terminologia

* **Operazioni** - le azioni principali eseguite da [!DNL CAPS]:
   * Applica
   * Ripristina
* **Fasi** - le tre fasi del flusso di lavoro:
   * Verifica preliminare
   * Applicazione di patch
   * Convalida
* **Ambiente**: l&#39;ambiente Adobe Commerce Cloud in cui vengono applicate le patch.

## Operazioni

[!DNL CAPS] supporta due *operazioni* principali per la gestione delle patch nell&#39;ambiente Adobe Commerce Cloud:

* **Operazione Apply** - aggiunge modifiche patch alla base di codice tramite un processo sicuro e convalidato. Le patch vengono applicate inserendo i file di patch nella cartella &quot;m2-hotfixes&quot;.

* **Operazione Ripristina**: rimuove le patch applicate in precedenza dal codebase rimuovendo i file di patch dalla cartella &#39;m2-hotfixes&#39;.

>[!IMPORTANT]
>
>Le operazioni di ripristino sono disponibili solo per le patch originariamente applicate tramite [!DNL CAPS]. Le patch applicate manualmente o tramite altri metodi non possono essere ripristinate con questo servizio.

## Fasi

Il flusso di lavoro [!DNL CAPS] utilizza tre *fasi* che vengono sempre eseguite in questo ordine per garantire che le patch vengano applicate in modo sicuro e affidabile:

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

La fase di applicazione delle patch applica o ripristina la patch in un ambiente di integrazione temporaneo per il test. Durante questa fase, [!DNL CAPS] crea un ambiente di test temporaneo per applicare e testare la patch in modo sicuro prima di apportare modifiche all&#39;ambiente effettivo.

Questo approccio fornisce:

* **Sicurezza** - mantiene l&#39;ambiente di destinazione intatto fino alla convalida della patch
* **Test** - in un ambiente reale prima di influire sulla produzione
* **Funzionalità di rollback** - se vengono rilevati problemi
* **Isolamento** - per ogni operazione patch

#### Fase 2a: creazione di un ambiente di integrazione

**Creazione ramo** - [!DNL CAPS] crea un ramo dell&#39;ambiente di integrazione temporaneo denominato `{target-environment}-CAPS-{patch-id}`

**Configurazione dell&#39;ambiente** - L&#39;ambiente di integrazione viene creato come elemento secondario dell&#39;ambiente di destinazione

**Sincronizzazione del codice** - L&#39;ambiente di integrazione eredita lo stato esatto dell&#39;ambiente di destinazione

**Requisiti delle risorse** - [!DNL CAPS] crea un ambiente temporaneo utilizzando la base di codice dell&#39;ambiente di destinazione. In base alla documentazione di Adobe Commerce Cloud, ogni ambiente (inclusi gli ambienti di integrazione) dispone di un’allocazione di storage separata in base al piano di storage contrattuale. La quantità di storage contrattuale rappresenta lo storage totale per ciascun ambiente. Nella maggior parte dei casi, non si verificano problemi con le limitazioni delle risorse. In caso di errori con limitazioni delle risorse, controlla le dimensioni dell’applicazione e lo spazio di archiviazione contrattuale nel piano.

#### Fase 2b: applicazione patch nell’ambiente di integrazione

**Test di sicurezza** - La patch viene applicata all&#39;ambiente di integrazione, non direttamente all&#39;ambiente di destinazione

**Gestione file** - I file di patch vengono inseriti nella directory `m2-hotfixes/`

**Operazioni Git** - Le modifiche vengono applicate e inviate al ramo dell&#39;ambiente di integrazione

**Attivazione ambiente** - L&#39;ambiente di integrazione è attivato per distribuire il codice con patch

#### Fase 2c: unione dell’ambiente di destinazione

**Estrazione dell&#39;ambiente** - [!DNL CAPS] estrae l&#39;ambiente di destinazione localmente

**Operazione di unione** - Il ramo dell&#39;ambiente di integrazione è unito all&#39;ambiente di destinazione

**Risoluzione dei conflitti** - Se si verificano conflitti, questi vengono risolti automaticamente quando possibile

**Distribuzione** - Le modifiche unite vengono distribuite nell&#39;ambiente di destinazione

**Verifica** - [!DNL CAPS] verifica che l&#39;unione sia stata eseguita correttamente e che gli ambienti siano sincronizzati

**Pulizia ambiente** - L&#39;ambiente di integrazione temporaneo è stato eliminato per liberare risorse

## Ciclo di vita dell’ambiente di integrazione

Gli ambienti di integrazione hanno un ciclo di vita specifico durante la fase di applicazione delle patch:

* **Creazione** - Creato all&#39;inizio della fase di applicazione della patch
* **Periodo attivo** - Rimane attivo durante l&#39;applicazione della patch e il test
* **Pulizia** - Eliminato automaticamente dopo l&#39;unione completata o se l&#39;operazione non riesce

### Fase 3: Convalida

La fase di convalida garantisce il corretto funzionamento dell&#39;applicazione aggiornata e l&#39;esecuzione dei controlli di integrità.

**Cosa succede:**

* **Verifica stato applicazione** - verifica che l&#39;applicazione sia avviata e eseguita correttamente
* **Pulizia** - rimuove l&#39;ambiente temporaneo, aggiorna i registri, notifica il completamento

## Indicatori di successo

**Applica operazione:**

* &quot;Processo completato correttamente&quot; - Patch applicata senza problemi
* &quot;La patch è stata applicata&quot; - La patch era già presente (non è necessaria alcuna azione)
* File patch inserito correttamente nella cartella &#39;m2-hotfixes&#39;
* Tutti i controlli di convalida superano
* Controlli di integrità dell&#39;applicazione completati

**Operazione di ripristino:**

* &quot;Processo completato correttamente&quot; - Patch ripristinata senza problemi
* &quot;La patch è stata ripristinata&quot; - La patch era già stata ripristinata (nessuna azione necessaria)
* File patch rimosso correttamente dalla cartella &quot;m2-hotfixes&quot;
* Tutti i controlli di convalida superano
* Controlli di integrità dell&#39;applicazione completati

## Salvaguardie dell’ambiente di produzione

[!DNL CAPS] include misure di protezione specifiche per gli ambienti di produzione per evitare interruzioni accidentali e garantire che le patch vengano convalidate in modo sicuro in anticipo.

### Condizioni preliminari per l&#39;applicazione di patch di produzione

Prima di applicare le patch agli ambienti di produzione, [!DNL CAPS] verifica la presenza di due condizioni critiche:

* **Modalità manutenzione** - L&#39;archivio deve essere in modalità manutenzione
* **Processi Cron disabilitati** - I processi Cron devono essere disabilitati

Se una delle due condizioni non viene soddisfatta, l&#39;applicazione patch viene bloccata e l&#39;utente riceve una notifica.

## Argomenti correlati

* [Introduzione CAPS](intro.md)
* [Come accedere](access.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)

---
title: Guida alla risoluzione dei problemi di [!DNL Cloud Automation Patching Service (CAPS)]
description: Risoluzione dei problemi comuni e dei messaggi di errore in [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# Guida alla risoluzione dei problemi di [!DNL Cloud Automation Patching Service (CAPS)]

Quando si utilizza [!DNL CAPS] per operazioni patch, è possibile che vengano visualizzati messaggi di errore e problemi che impediscono il corretto completamento dell&#39;applicazione o il ripristino della patch. Questa guida fornisce soluzioni per i problemi più comuni.

## Passaggi per la risoluzione rapida dei problemi

### Se l’operazione patch non riesce

* Controllare lo stato dell&#39;operazione per capire quale fase non è riuscita
* Esaminare i messaggi di errore per motivi di errore specifici
* Esamina i registri di errore per dettagli tecnici
* Segui le soluzioni fornite in questa guida

### Durata delle operazioni patch

Per la maggior parte degli ambienti, la seguente timeline descrive quanto tempo devono richiedere le operazioni patch, ma potrebbe richiedere più tempo a seconda delle dimensioni e della complessità dell’ambiente:

* **Pre-elaborazione:** 2-5 minuti
* **Applicazione della patch:** 5-15 minuti
* **Post-elaborazione:** 10-40 minuti
* **Totale:** 15-60 minuti

### Annullamento di una patch in corso

>[!WARNING]
>
>Una volta iniziata l’operazione patch, questa deve poter essere completata. Il sistema include procedure di pulizia che vengono eseguite anche in caso di errore delle operazioni. L’interruzione del processo potrebbe lasciare l’ambiente in uno stato incoerente.

## Messaggi di successo comuni

* **&quot;Processo completato correttamente&quot;** - La patch è stata applicata/ripristinata correttamente senza problemi.

* **&quot;La patch è stata applicata&quot;** - Si sta tentando di applicare una patch già applicata. Il sistema ha rilevato che la patch è già presente nell&#39;ambiente. Non è necessaria alcuna azione.

* **&quot;Patch ripristinata&quot;** - Si sta tentando di ripristinare una patch già ripristinata. Il sistema ha rilevato che la patch non è applicata. Non è necessaria alcuna azione.

## Messaggi di errore e soluzioni comuni

### Errori di applicazione patch

#### &quot;Impossibile applicare la patch perché [!DNL CAPS] ha rilevato questi problemi con il codebase o con il file di patch&quot;

**Quando si verifica:** Durante il controllo preliminare

**Causa:** la patch è in conflitto con il codebase corrente OPPURE si è verificato un problema con la patch stessa

**Soluzioni:**

* Controlla i registri di errore dettagliati forniti per identificare se si tratta di un problema di base di codice o di patch
* Verifica la presenza di personalizzazioni in conflitto nel codice
* Verifica che la patch sia compatibile con la versione di Adobe Commerce in uso
* Valuta se risolvere i conflitti manualmente o contatta l’assistenza

#### &quot;La patch non è stata gestita da [!DNL CAPS]. Impossibile ripristinare&quot;

**Quando si verifica:** Durante le operazioni di ripristino

**Causa:** Si sta tentando di ripristinare una patch non applicata tramite [!DNL CAPS]

**Soluzione:** Utilizzare lo stesso metodo utilizzato per applicare la patch in origine oppure contattare il supporto tecnico per assistenza manuale

### Errori di ambiente e convalida

#### &quot;L’ambiente non è sincronizzato con l’elemento principale&quot;

**Quando si verifica:** Durante la convalida

**Causa:** l&#39;ambiente di integrazione è diverso dall&#39;ambiente padre

**Soluzioni:**

* Sincronizzare l’ambiente con il ramo principale
* Riprovare l&#39;operazione patch
* Contatta l&#39;assistenza se i problemi di sincronizzazione persistono

#### &quot;Non sono state rispettate le misure di salvaguardia dell’ambiente di produzione&quot;

**Quando si verifica:** Durante la verifica preliminare degli ambienti di produzione

**Causa:** l&#39;ambiente di produzione non soddisfa le condizioni di sicurezza richieste

**Soluzioni:**

* Abilita modalità di manutenzione per l’archivio di produzione
* Disabilita i processi cron nell’ambiente di produzione
* Verifica che entrambe le condizioni siano soddisfatte prima di riprovare

>[!IMPORTANT]
>
> [!DNL CAPS] non abilita automaticamente la modalità di manutenzione o disabilita i processi cron, che devono essere eseguiti esternamente da te

#### &quot;La patch è stata applicata, ma il controllo dello stato non è riuscito. Prendi in considerazione la possibilità di ripristinare&quot;

**Quando si verifica:** Dopo l&#39;applicazione della patch durante la convalida

**Causa:** La patch è stata applicata correttamente, ma i controlli di integrità non sono riusciti

**Soluzioni:**

* Esaminare i registri delle applicazioni per individuare errori specifici
* Verifica manuale delle funzionalità critiche
* Valuta se ripristinare la patch se i problemi persistono
* Contatta il supporto in caso di bisogno di assistenza

### Errori di autenticazione e accesso

#### &quot;Autenticazione non riuscita per l’archivio Adobe Commerce&quot;

**Quando si verifica:** In qualsiasi fase

**Causa:** credenziali archivio Adobe Commerce non valide o scadute

**Soluzioni:**

Per risolvere il problema sono disponibili due opzioni consigliate:

**Opzione 1: correzione della variabile del livello di ambiente `env:COMPOSER_AUTH` (scelta consigliata)**

* Verificare di aver impostato le credenziali corrette per `env:COMPOSER_AUTH`.
* Accedi alla configurazione globale facendo clic sull&#39;icona a forma di ingranaggio in alto a sinistra nell&#39;interfaccia utente del progetto cloud, quindi seleziona la scheda **Variabili**.
* Accertati di selezionare _Disponibile durante la generazione_ e deselezionare _Disponibile durante il runtime_.

Se l&#39;opzione 1 non risolve il problema, procedere con l&#39;opzione 2.

**Opzione 2: creare e distribuire `auth.json` file manualmente**

* SSH nel server.
* Recupera il contenuto della variabile `env:COMPOSER_AUTH` corrente tramite:\
  `echo $COMPOSER_AUTH`
* Copia tutti i contenuti dal passaggio precedente (in formato JSON).
* Creare un nuovo file denominato `auth.json` con questi contenuti.
* Eseguire il commit del file `auth.json` appena creato nella directory principale dell&#39;archivio.
* Attiva una nuova distribuzione.

#### &quot;Autorizzazioni insufficienti per l’accesso all’ambiente&quot;

**Quando si verifica:** Durante la creazione dell&#39;ambiente o l&#39;accesso

**Causa:** l&#39;account utente non dispone delle autorizzazioni necessarie

**Soluzioni:**

* Verifica il ruolo utente e le autorizzazioni
* Contattare l&#39;amministratore di sistema
* Verifica di disporre delle autorizzazioni per la gestione dell’ambiente
* Assicurati di disporre delle autorizzazioni di distribuzione

### Errori di risorse e quote

#### &quot;Quota ambiente superata&quot;

**Quando si verifica:** durante la creazione dell&#39;ambiente

**Causa:** Hai raggiunto il limite dell&#39;ambiente

**Soluzioni:**

* Disattivare gli ambienti non utilizzati
* Pulizia di rami e distribuzioni obsoleti
* Contatta il supporto per richiedere l’aumento della quota
* Valuta l&#39;aggiornamento del piano

#### &quot;Risorse insufficienti per il funzionamento&quot;

**Quando si verifica:** In qualsiasi fase

**Causa:** l&#39;ambiente non dispone di sufficiente CPU, memoria o spazio di archiviazione

**Soluzioni:**

* Verifica l’utilizzo delle risorse dell’ambiente
* Liberare risorse pulendo i file
* Attendere che le risorse siano disponibili
* Contatta il supporto se i problemi relativi alle risorse persistono

## Ottenere aiuto

**Quando contattare il supporto tecnico:**

Contatta il supporto di Adobe Commerce Cloud quando:

* I messaggi di errore non sono chiari o non contengono dettagli sufficienti
* Le operazioni di patch hanno esito negativo in modo coerente
* Assistenza per la risoluzione manuale dei conflitti
* I controlli di integrità non vanno a buon fine, ma la causa non è chiara
* È necessaria assistenza per i problemi di sincronizzazione dell’ambiente

**Informazioni da fornire:**

Quando contatti il supporto, fornisci:

* **ID progetto** - Identificatore progetto Adobe Commerce Cloud
* **ID ambiente**: l&#39;ambiente specifico in cui si è verificato il problema
* **ID operazione** - Identificatore operazione [!DNL CAPS]
* **Dettagli errore** - Completare i messaggi di errore e i registri
* **Passaggi per riprodurre** - Operazioni da eseguire quando si è verificato l&#39;errore
* **Tentativi precedenti** - Tentativi già effettuati per risolvere il problema

### Risorse aggiuntive

Per informazioni tecniche più dettagliate:

* Esaminare i registri di errore completi forniti con le operazioni non riuscite
* Consultate la documentazione di Adobe Commerce per informazioni specifiche sulle patch
* Contatta il supporto di Adobe Commerce Cloud per problemi specifici dell’ambiente

### Argomenti correlati

* [Documentazione di Adobe Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [Guida all&#39;installazione di Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview)
* [Introduzione CAPS](intro.md)
* [Come accedere](access.md)
* [Flusso di lavoro](workflow.md)
* [Best practice](best-practices.md)

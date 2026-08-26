---
title: Guida alla risoluzione dei problemi di [!DNL Adobe Commerce Patching Automation]
description: Risoluzione dei problemi comuni e dei messaggi di errore in [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Guida alla risoluzione dei problemi di [!DNL Adobe Commerce Patching Automation]

Quando si utilizza [!DNL Patching Automation] per operazioni patch, è possibile che vengano visualizzati messaggi di errore e problemi che impediscono il corretto completamento dell&#39;applicazione o il ripristino della patch. Questa guida fornisce soluzioni per i problemi più comuni.

## Passaggi per la risoluzione rapida dei problemi

### Se l’operazione patch non riesce

* Controllare lo stato dell&#39;operazione per capire quale fase non è riuscita
* Esaminare i messaggi di errore per motivi di errore specifici
* Esamina i registri di errore per dettagli tecnici
* Segui le soluzioni fornite in questa guida

>[!TIP]
>
>Nella Cloud Console, i registri di distribuzione sono disponibili dal feed attività del progetto, anche dopo l’eliminazione di un ambiente di integrazione temporaneo.

### Durata delle operazioni patch

Per la maggior parte degli ambienti, la seguente timeline descrive quanto tempo devono richiedere le operazioni patch, ma potrebbe richiedere più tempo a seconda delle dimensioni e della complessità dell’ambiente:

* **Pre-elaborazione:** 2-5 minuti
* **Applicazione della patch:** 5-15 minuti
* **Post-elaborazione:** 10-40 minuti
* **Totale:** 15-60 minuti

>[!NOTE]
>
>Il tempo di post-elaborazione viene stimato in base alla cronologia di distribuzione dell’ambiente, pertanto potrebbe non rientrare nell’intervallo indicato in precedenza per gli ambienti con distribuzione insolitamente rapida o lenta.

### Annullamento di una patch in corso

>[!WARNING]
>
>Una volta iniziata l’operazione patch, questa deve poter essere completata. Il sistema include procedure di pulizia che vengono eseguite anche in caso di errore delle operazioni. L’interruzione del processo potrebbe lasciare l’ambiente in uno stato incoerente.

## Messaggi di successo comuni

* **&quot;Processo completato correttamente&quot;** - La patch è stata applicata/ripristinata correttamente senza problemi.

* **&quot;La patch è stata applicata&quot;** - Si sta tentando di applicare una patch già applicata. Il sistema ha rilevato che la patch è già presente nell&#39;ambiente. Non è necessaria alcuna azione.

* **&quot;Patch ripristinata&quot;** - Si sta tentando di ripristinare una patch già ripristinata. Il sistema ha rilevato che la patch non è applicata. Non è necessaria alcuna azione.

## Messaggi di errore e soluzioni comuni

>[!NOTE]
>
>Non tutti gli errori possibili sono elencati di seguito. Un errore non elencato durante il controllo preliminare viene visualizzato come il generico &quot;Errore durante il controllo preliminare&quot;; un errore non elencato durante la convalida viene visualizzato come il generico &quot;Errore durante la post-elaborazione&quot; — contatta il supporto con il testo esatto dell’errore in entrambi i modi. Durante l’applicazione della patch, un errore imprevisto mostra il messaggio di errore sottostante non elaborato direttamente anziché un fallback generico.

### Errori di preparazione all’ambiente

#### &quot;L’ultima distribuzione non è riuscita. Assicurarsi che l&#39;ambiente sia stabile prima di applicare o ripristinare le patch.&quot;

**Quando si verifica:** All&#39;inizio del controllo preliminare, prima di qualsiasi convalida specifica della patch

**Causa:** la distribuzione più recente dell&#39;ambiente di destinazione non è stata completata correttamente

**Soluzione:** ridistribuisci l&#39;ambiente di destinazione e verifica che la distribuzione sia stata completata correttamente (controlla il relativo registro di distribuzione nella console cloud) prima di ripetere l&#39;operazione di patch.

### Errori di applicazione patch

#### &quot;Impossibile applicare la patch perché [!DNL Patching Automation] ha rilevato questi problemi con il codebase o con il file di patch&quot;

**Quando si verifica:** Durante il controllo preliminare

**Causa:** la patch è in conflitto con il codebase corrente OPPURE si è verificato un problema con la patch stessa

**Soluzioni:**

* Controlla i registri di errore dettagliati forniti per identificare se si tratta di un problema di base di codice o di patch
* Verifica la presenza di personalizzazioni in conflitto nel codice
* Verifica che la patch sia compatibile con la versione di Adobe Commerce in uso
* Valuta se risolvere i conflitti manualmente o contatta l’assistenza

#### &quot;Stai tentando di ripristinare una patch non applicata tramite [!DNL Patching Automation]. È probabile che la patch sia stata applicata manualmente.&quot;

**Quando si verifica:** Durante le operazioni di ripristino

**Causa:** Si sta tentando di ripristinare una patch non applicata tramite [!DNL Patching Automation]

**Soluzione:** Utilizzare lo stesso metodo utilizzato per applicare la patch in origine oppure contattare il supporto tecnico per assistenza manuale

### Errori di ambiente e convalida

#### &quot;L’ambiente non è sincronizzato con l’elemento principale&quot;

**Quando si verifica:** durante la convalida, nel controllo di sincronizzazione pre-unione, prima che l&#39;ambiente di integrazione venga unito all&#39;ambiente di destinazione

**Causa:** L&#39;ambiente di integrazione è diverso dall&#39;ambiente padre, in genere perché l&#39;ambiente di destinazione è stato modificato durante il test della patch

**Soluzioni:**

* Ripetere l&#39;operazione di patch una volta che l&#39;ambiente di destinazione è stabile
* Evitare di apportare modifiche all&#39;ambiente di destinazione durante un&#39;operazione patch
* Contatta l&#39;assistenza se i problemi di sincronizzazione persistono

#### &quot;Verifica post-unione non riuscita: gli ambienti non sono sincronizzati dopo l’unione.&quot;

**Quando si verifica:** Durante la convalida, dopo l&#39;unione dell&#39;ambiente di integrazione con l&#39;ambiente di destinazione

**Causa:** il codice dei due ambienti non corrisponde dopo l&#39;unione, in genere si tratta di un ritardo temporaneo della propagazione API Platform.sh anziché di un conflitto reale

**Soluzioni:**

* Attendi alcuni minuti e controlla di nuovo lo stato dell’ambiente. Questo problema spesso si risolve da solo
* Se dopo alcuni minuti gli ambienti non corrispondono, contatta il supporto Adobe.

#### &quot;Impossibile creare il processo di patch nell’ambiente di produzione quando cron è abilitato e la modalità di manutenzione è disabilitata. Abilita la modalità di manutenzione e disabilita i processi cron prima di applicare le patch.&quot;

**Quando si verifica:** Durante la verifica preliminare degli ambienti di produzione

**Causa:** l&#39;ambiente di produzione non soddisfa le condizioni di sicurezza richieste

**Soluzioni:**

* Abilita modalità di manutenzione per l’archivio di produzione
* Disabilita i processi cron nell’ambiente di produzione
* Verifica che entrambe le condizioni siano soddisfatte prima di riprovare
* In alternativa, seleziona la casella di controllo Sostituisci nell’interfaccia utente per saltare questi controlli e procedere comunque. Utilizza l’opzione di sostituzione solo se comprendi il rischio di applicare patch alla produzione senza tali protezioni in atto

>[!IMPORTANT]
>
> [!DNL Patching Automation] non abilita automaticamente la modalità di manutenzione o disabilita i processi cron, che devono essere eseguiti esternamente da te

#### &quot;L’operazione di patch è stata completata, ma il controllo dello stato dell’ambiente non è riuscito. Questo indica potenziali problemi relativi alla distribuzione. Controlla lo stato dell’ambiente e prendi in considerazione di ripristinare la modifica.&quot;

**Quando si verifica:** dopo l&#39;applicazione della patch o la reversione, durante la convalida

**Causa:** la patch è stata applicata o ripristinata correttamente, ma il controllo di integrità successivo non è riuscito

**Soluzioni:**

* Test della vetrina e dei flussi di lavoro critici di pagamento e amministrazione per verificare se i clienti sono effettivamente interessati
* Nella console Cloud, controlla lo stato dell&#39;ambiente ed esamina i registri dell&#39;applicazione e della distribuzione nel feed **Attività** dei progetti. Cercare gli errori associati all&#39;operazione o alla distribuzione della patch.
* Attiva una ridistribuzione manuale per determinare se l’errore di verifica dello stato è stato causato da un problema transitorio di distribuzione o infrastruttura.
* Se il problema persiste, ripristinare la patch. Se la patch è gestita da [!DNL Patching Automation] e l&#39;operazione è disponibile, selezionare [!UICONTROL Revert]. Se la patch è una patch personalizzata nella directory `m2-hotfixes`, eliminare il file di patch dall&#39;archivio del progetto. Esegui il commit e invia la modifica, quindi ridistribuisci l’ambiente.
* Se il problema persiste, contatta il supporto Adobe.Includi le seguenti informazioni nella richiesta di supporto: ID progetto di supporto, ID ambiente e questo messaggio esatto: l’ultima operazione non è stata completata correttamente, pertanto potrebbe essere necessario confermare lo stato dell’ambiente.

### Errori di autenticazione e accesso

#### &quot;Accesso negato&quot;

**Quando si verifica:** Quando l&#39;account non dispone delle autorizzazioni necessarie durante la creazione o l&#39;accesso all&#39;ambiente

**Causa:** l&#39;account utente non dispone delle autorizzazioni necessarie

**Soluzioni:**

* Verifica il ruolo utente e le autorizzazioni
* Contattare l&#39;amministratore di sistema
* Verifica di disporre delle autorizzazioni per la gestione dell’ambiente
* Assicurati di disporre delle autorizzazioni di distribuzione

### Errori di integrazione GitHub

#### &quot;Nessuna credenziali Git disponibile per il provider &quot;github&quot;. Installare l’app GitHub di automazione dell’applicazione di patch per questo archivio&quot;

**Quando si verifica:** Durante le operazioni di patch per i progetti connessi a GitHub

**Causa:** l&#39;app GitHub [!DNL Patching Automation] non è installata nel repository

**Soluzione:** Segui i passaggi descritti in [Configurare l&#39;integrazione GitHub per [!DNL Patching Automation]](github-integration.md)

#### &quot;Richiesta API GitHub non riuscita&quot;

**Quando si verifica:** durante le operazioni di patch per i progetti connessi a GitHub

**Causa:** un problema temporaneo ha impedito la connessione del servizio a GitHub

**Soluzione:** attendere alcuni minuti e riprovare. Se l&#39;errore persiste, contattare il [supporto Adobe Commerce Cloud](https://experienceleague.adobe.com/home#support)

#### &quot;Ambiente non creato entro il timeout&quot; (progetto connesso a GitHub)

**Quando si verifica:** Durante la creazione dell&#39;ambiente di integrazione

**Causa:** L&#39;integrazione GitHub del progetto ha l&#39;opzione `fetch-branches` disabilitata. Di conseguenza, i rami temporanei inviati dal servizio non vengono sincronizzati e l’ambiente di integrazione non viene mai creato.

**Soluzione:** Abilitare l&#39;opzione [`fetch-branches` dell&#39;integrazione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration), quindi riprovare. Consulta [Configurare l&#39;integrazione GitHub per  [!DNL Patching Automation]](github-integration.md).

### Errori di attivazione dell’ambiente

#### &quot;Impossibile attivare l’ambiente di integrazione.&quot;

**Quando si verifica:** Quando [!DNL Patching Automation] non è in grado di attivare l&#39;ambiente di integrazione temporaneo necessario per testare la patch in modo sicuro.

**Causa:** dipende dai dettagli aggiuntivi visualizzati insieme all&#39;errore:

**Se i dettagli indicano pacchetti Compositore o Adobe Commerce:**

* Accedi a [https://account.magento.com/](https://account.magento.com/) (o richiedi al proprietario dell&#39;account di farlo) e verifica che il tuo account abbia accesso alla base di codice di Commerce Enterprise.
* Verificare che la coppia di chiavi pubblica/privata del Compositore del progetto sia corretta. Vedere [Chiavi di autenticazione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Accedi a [https://account.magento.com/](https://account.magento.com/) (o chiedi al proprietario dell&#39;account di farlo) e conferma che il tuo account abbia accesso alla base di codice di Commerce Enterprise.
* Verifica che le chiavi di autenticazione pubblica e privata del Compositore del progetto siano corrette. Vedi [Chiavi di autenticazione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Verifica che il pacchetto denominato nel messaggio di errore sia disponibile per la versione di Commerce in uso. Consulta [Pacchetti Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/packages/adobe-commerce).

**Se i dettagli indicano gli slot o le risorse dell&#39;ambiente:**

* Nella console Cloud, apri la panoramica del progetto e controlla gli ambienti e i relativi stati. Disattivare o eliminare eventuali ambienti di integrazione inutilizzati: seleziona l’ambiente. Vai a **[!UICONTROL Settings]>[!UICONTROL General]**. Imposta lo stato dell’ambiente su inattivo.

  In alternativa, utilizzare CLI: `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* Verifica che il progetto disponga di risorse sufficienti, ad esempio spazio su disco.
* Verificare che l&#39;ambiente padre sia stabile (nessuna distribuzione attiva) al momento dell&#39;operazione.
* Se hai la necessità di aumentare il limite dell’ambiente, contatta il supporto Adobe.

**Per qualsiasi altra causa:** esaminare i registri di errore dettagliati nell&#39;interfaccia utente di automazione applicazione patch o contattare il supporto tecnico specificando il testo esatto dell&#39;errore.

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
* **ID operazione** - Identificatore operazione [!DNL Patching Automation]
* **Dettagli errore** - Completare i messaggi di errore e i registri
* **Passaggi per riprodurre** - Operazioni da eseguire quando si è verificato l&#39;errore
* **Tentativi precedenti** - Tentativi già effettuati per risolvere il problema

### Risorse aggiuntive

Per informazioni tecniche più dettagliate:

* Esaminare i registri di errore completi forniti con le operazioni non riuscite
* Consultate la documentazione di Adobe Commerce per informazioni specifiche sulle patch
* Contatta il supporto di Adobe Commerce Cloud per problemi specifici dell’ambiente

### Argomenti correlati

* [Documentazione di Adobe Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)
* [Guida all’installazione di Adobe Commerce](/help/installation/overview.md)
* [Introduzione all’automazione dell’applicazione di patch](intro.md)
* [Come accedere](access.md)
* [Panoramica del flusso di lavoro](workflow.md)
* [Integrazione GitHub](github-integration.md)
* [Best practice](best-practices.md)

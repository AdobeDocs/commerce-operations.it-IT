---
title: Rispondere a un problema di sicurezza
description: Gestire gli incidenti di sicurezza seguendo le best practice per rispondere e risolvere i problemi di sicurezza che influiscono sulla disponibilità e sulle prestazioni del sito.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---

# Best practice per rispondere a un problema di sicurezza

L’articolo seguente riepiloga le best practice per rispondere a un problema di sicurezza e risolvere i problemi che influiscono sulla disponibilità, l’affidabilità e le prestazioni del sito Adobe Commerce.

L’aderenza a queste best practice consente di prevenire gli accessi non autorizzati e gli attacchi di malware. Se si verifica un problema di sicurezza, queste procedure consigliate consentono di prepararsi per una risposta immediata, eseguire un&#39;analisi della causa principale e gestire il processo di correzione per ripristinare le normali operazioni.

>[!TIP]
>
>L’Adobe ha rilevato che la maggior parte degli incidenti di sicurezza si verifica quando gli attori che rappresentano una minaccia sfruttano vulnerabilità esistenti e senza patch, password inadeguate e impostazioni di proprietà e autorizzazioni inadeguate nella configurazione dell’applicazione e dell’infrastruttura Commerce. Riduci al minimo il verificarsi di problemi di sicurezza esaminando e seguendo le best practice di sicurezza di Adobe durante la configurazione e l’aggiornamento delle installazioni di Adobe Commerce. Consulta [Proteggere il sito e l’infrastruttura Commerce](../launch/security-best-practices.md).


## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Rispondere a un incidente

Se sospetti che il progetto Adobe Commerce su infrastruttura cloud sia interessato da un problema di sicurezza, i primi passaggi critici sono i seguenti:

- Controlla l&#39;accesso a tutti gli account utente amministratore
- Abilita controlli avanzati di autenticazione a più fattori (MFA)
- Mantenere i registri critici
- Controlla gli aggiornamenti di sicurezza per la tua versione di Adobe Commerce.

Ulteriori raccomandazioni sono descritte di seguito.

## Intervenire immediatamente in caso di attacco

Nel caso sfortunato di un compromesso tra siti, ecco alcune raccomandazioni chiave da seguire:

- Coinvolgi l’integratore di sistemi e il personale addetto alla sicurezza per condurre indagini e riparare i danni.

- Determinare l&#39;ambito dell&#39;attacco:
   - È stato effettuato l&#39;accesso alle informazioni sulla carta di credito?
   - Quali informazioni sono state rubate?
   - Quanto tempo è trascorso dal compromesso?
   - Le informazioni erano crittografate?

- Cercare di trovare il vettore di attacco per determinare quando e come il sito è stato compromesso, esaminando i file di registro del server e le modifiche ai file.

   - In alcune circostanze, potrebbe essere consigliabile cancellare e reinstallare tutto o, nel caso di hosting virtuale, creare una nuova istanza. I malware potrebbero essere nascosti in una posizione insospettata in attesa di essere ripristinati da soli.

   - Rimuovi tutti i file non necessari. Quindi, reinstallare i file richiesti da un&#39;origine nota e pulita. È ad esempio possibile reinstallare utilizzando i file del sistema di controllo delle versioni oppure i file di distribuzione originali di Adobe.

   - Reimposta tutte le credenziali, inclusi database, accesso ai file, integrazioni di pagamento e spedizione, servizi Web e accesso amministratore. Reimposta inoltre tutte le chiavi e gli account di integrazione e API che potrebbero essere utilizzati per attaccare il sistema.

## Analizzare un problema

Il primo passo dell&#39;analisi degli incidenti consiste nel raccogliere quante più informazioni possibili, il più rapidamente possibile. Raccogliere informazioni sull&#39;incidente può essere utile per determinare la causa potenziale dell&#39;incidente. Adobe Commerce fornisce gli strumenti indicati di seguito per l’analisi dei problemi.

- [Registri azioni amministrazione di controllo](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  Nel rapporto Registri azioni viene visualizzato un record dettagliato di tutte le azioni di amministrazione abilitate per la registrazione. Ogni record ha la marca temporale e registra l’indirizzo IP e il nome dell’utente. I dettagli del registro includono i dati utente amministratore e le relative modifiche apportate durante l’azione.

- Analizzare gli eventi con [Strumento Osservazione per Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  Lo strumento di osservazione per Adobe Commerce consente di analizzare problemi complessi per identificare le cause principali. Invece di tenere traccia di dati diversi, puoi dedicare più tempo alla correlazione di eventi ed errori per ottenere informazioni più approfondite sulle cause dei colli di bottiglia delle prestazioni.

  Utilizza il **Sicurezza** scheda nello strumento per ottenere una chiara visualizzazione dei potenziali problemi di sicurezza per aiutare a identificare le cause principali e mantenere le prestazioni dei siti ottimali.

- Analizzare i registri con [Registri New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  I progetti Pro di Adobe Commerce su infrastruttura cloud includono [Registri New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html) servizio. Il servizio è preconfigurato per aggregare tutti i dati di registro dagli ambienti di staging e produzione per visualizzarli in un dashboard di gestione dei registri centralizzato in cui è possibile cercare e visualizzare i dati aggregati.

  Per altri progetti Commerce, puoi impostare e utilizzare [Registri New Relic](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) servizio per completare le seguenti attività:
   - Utilizzare [Query New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) per cercare dati di registro aggregati.
   - Visualizzare i dati di registro tramite l’applicazione Registri di New Relic.

## Controlla account, codice e database

Esamina gli account amministratore e utente di Commerce, il codice dell’applicazione, la configurazione del database e i registri per identificare e rimuovere il codice sospetto e garantire la sicurezza dell’accesso a account, siti e database. Quindi, ridistribuisci in base alle esigenze.

Continuare a monitorare attentamente il sito dopo l&#39;incidente poiché molti siti vengono compromessi di nuovo in poche ore. Verifica continua del registro e monitoraggio dell&#39;integrità dei file per rilevare rapidamente eventuali segni di nuovi compromessi.

### Controlla account utente amministratore

- [Verifica accesso utente amministratore](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html): rimuovi account vecchi, inutilizzati o sospetti e ruota le password per tutti gli utenti amministratore.

- [Verifica impostazioni di protezione amministratore](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)- Verificare che le impostazioni di protezione dell&#39;amministratore seguano le procedure consigliate per la protezione.

- [Verificare gli account utente per i progetti Adobe Commerce su infrastrutture cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html): rimuovi account vecchi, inutilizzati o sospetti e ruota le password per tutti gli utenti amministratori di progetti cloud. Verifica che le impostazioni di sicurezza dell’account siano configurate correttamente.

- [Controlla chiavi SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) per Adobe Commerce su infrastruttura cloud: revisione, eliminazione e rotazione delle chiavi SSH.

### Codice di audit

- Dall’amministratore, controlla [Configurazione intestazione e piè di pagina HTML](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) a tutti i livelli dell&#39;ambito, compresi `website` e `store view`. Rimuovere eventuali codici JavaScript sconosciuti dagli script e dai fogli di stile e da impostazioni HTML varie. Conserva solo il codice riconosciuto, ad esempio i frammenti di tracciamento.

- Confrontare la base di codice di produzione corrente con la base di codice memorizzata nel sistema di controllo delle versioni (VCS, Version Control System).

- Metti in quarantena qualsiasi codice sospetto.

- Assicurati che non vi siano residui di codice sospetto ridistribuendo la base di codice nell’ambiente di produzione.

### Controlla la configurazione del database e i registri

- Esaminare le stored procedure per le modifiche.

- Verifica che il database sia accessibile solo dall’istanza Commerce.

- Verificare che il malware non sia più presente analizzando il sito con gli strumenti di scansione del malware disponibili pubblicamente.

- Proteggi il pannello di amministrazione modificandone il nome e verificando che il sito `app/etc/local.xml` e `var` Gli URL non sono accessibili al pubblico.

- Continuare a monitorare attentamente il sito dopo l&#39;incidente poiché molti siti vengono compromessi di nuovo in poche ore. Verifica continua del registro e monitoraggio dell&#39;integrità dei file per rilevare rapidamente eventuali segni di nuovi compromessi.

## Rimuovi avvisi di Google

Se il sito è stato contrassegnato da Google come contenente codice dannoso, richiedi una revisione dopo la pulizia del sito. Le recensioni per i siti infetti da malware richiedono alcuni giorni. Quando Google determina che il sito è pulito, gli avvisi provenienti dai risultati della ricerca e dai browser dovrebbero scomparire entro 72 ore. Consulta [Richiedi una revisione](https://web.dev/articles/request-a-review).

## Controlla elenco di controllo risultati malware

Se gli strumenti di scansione del malware disponibili pubblicamente confermano un attacco di malware, indagare l&#39;incidente. Collabora con l’integratore di soluzioni per pulire il sito e seguire il processo di correzione consigliato.

## Condurre ulteriori verifiche

Quando si tratta di attacchi sofisticati, la migliore linea di azione è quella di lavorare con uno sviluppatore esperto, un esperto di terze parti o un integratore di soluzioni per riparare completamente il sito e rivedere le pratiche di sicurezza. Lavorare con professionisti esperti della sicurezza garantisce che vengano prese misure complete e avanzate per garantire la sicurezza della tua azienda e dei suoi clienti.

## Informazioni aggiuntive

- [Framework di analisi della causa principale](https://sansec.io/kb/incident-response/magento-root-cause-analysis).

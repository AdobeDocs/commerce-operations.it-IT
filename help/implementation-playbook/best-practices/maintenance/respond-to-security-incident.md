---
title: Rispondere a un problema di sicurezza
description: Gestire gli incidenti di sicurezza seguendo le best practice per rispondere e risolvere i problemi di sicurezza che influiscono sulla disponibilità e sulle prestazioni del sito.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Best practice per rispondere a un problema di sicurezza

L’articolo seguente riepiloga le best practice per rispondere a un problema di sicurezza e risolvere i problemi che influiscono sulla disponibilità, l’affidabilità e le prestazioni del sito Adobe Commerce.

L’aderenza a queste best practice consente di prevenire gli accessi non autorizzati e gli attacchi di malware. Se si verifica un problema di sicurezza, queste procedure consigliate consentono di prepararsi per una risposta immediata, eseguire un&#39;analisi della causa principale e gestire il processo di correzione per ripristinare le normali operazioni.

>[!TIP]
>
>Adobe ha rilevato che la maggior parte degli incidenti di sicurezza si verifica quando gli attori che rappresentano una minaccia sfruttano le vulnerabilità esistenti e senza patch, le password non corrette e le impostazioni di proprietà e autorizzazioni insufficienti nella configurazione dell’applicazione e dell’infrastruttura Commerce. Riduci al minimo il verificarsi di problemi di sicurezza esaminando e seguendo le best practice di sicurezza di Adobe durante la configurazione e l’aggiornamento delle installazioni di Adobe Commerce. Consulta [Proteggere il sito e l&#39;infrastruttura Commerce](../launch/security-best-practices.md).


## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Systems Commerce su infrastruttura cloud
- Adobe Systems Commerce locale

## Rispondere a un incidente

Se sospetti che il progetto Adobe Commerce su infrastruttura cloud sia interessato da un problema di sicurezza, i primi passaggi critici sono i seguenti:

- Controlla l&#39;accesso a tutti gli account utente amministratore
- Abilitare i controlli avanzati di autenticazione a più fattori (MFA)
- Conserva registri critico
- Esamina gli aggiornamenti di sicurezza per la tua versione di Adobe Systems Commerce.

Ulteriori raccomandazioni sono dettagliate di seguito.

## Intervenire immediatamente in caso di attacco

Nel malaugurato caso di una compromissione del sito, ecco alcuni consigli chiave da seguire:

- Coinvolgi l’integratore di sistemi e il personale addetto alla sicurezza per condurre indagini e riparare i danni.

- Determinare l&#39;ambito dell&#39;attacco:
   - È stato effettuato l&#39;accesso alle informazioni sulla carta di credito?
   - Quali informazioni sono state rubate?
   - Quanto tempo è trascorso dal compromesso?
   - Le informazioni erano crittografate?

- Cercare di trovare il vettore di attacco per determinare quando e come il sito è stato compromesso, esaminando i file di registro del server e le modifiche ai file.

   - In alcune circostanze, potrebbe essere consigliabile cancellare e reinstallare tutto o, nel caso di hosting virtuale, creare una nuova istanza. I malware potrebbero essere nascosti in una posizione insospettata in attesa di essere ripristinati da soli.

   - Rimuovi tutti i file non necessari. Quindi, reinstallare i file richiesti da un&#39;origine nota e pulita. È ad esempio possibile reinstallare utilizzando i file del sistema di controllo delle versioni oppure i file di distribuzione originali di Adobe.

   - Reimposta tutte le credenziali, inclusi database, accesso file, integrazioni di pagamento e spedizione, servizi Web e login amministratore. Ripristina anche tutte le chiavi e gli account API e di integrazione che potrebbero essere utilizzati per attaccare il sistema.

## Analizzare un problema

Il primo passo dell&#39;analisi degli incidenti consiste nel raccogliere quante più informazioni possibili, il più rapidamente possibile. Raccogliere informazioni sull&#39;incidente può essere utile per determinare la causa potenziale dell&#39;incidente. Adobe Commerce fornisce gli strumenti indicati di seguito per l’analisi dei problemi.

- [Registri azioni azioni amministrazione controllo](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  Il rapporto Registri azioni visualizza un record dettagliato di tutte le azioni dell&#39;amministratore abilitate per registrazione. Ogni record ha la marca temporale e registra l’indirizzo IP e il nome dell’utente. I dettagli del registro includono i dati utente amministratore e le relative modifiche apportate durante l’azione.

- Analizzare gli eventi con lo strumento [Osservazione per Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  Lo strumento di osservazione per Adobe Commerce consente di analizzare problemi complessi per identificare le cause principali. Invece di tenere traccia di dati diversi, puoi dedicare più tempo alla correlazione di eventi ed errori per ottenere informazioni più approfondite sulle cause dei colli di bottiglia delle prestazioni.

  Utilizza la scheda **Sicurezza** nello strumento per ottenere una chiara visualizzazione dei potenziali problemi di sicurezza per aiutare a identificare le cause principali e mantenere le prestazioni dei siti ottimali.

- Analizza i registri con [Registri New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  I progetti Adobe Commerce su infrastruttura cloud Pro includono il servizio [Registri New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html). Il servizio è preconfigurato per aggregare tutti i dati di registro dagli ambienti di staging e produzione per visualizzarli in un dashboard di gestione dei registri centralizzato in cui è possibile cercare e visualizzare i dati aggregati.

  Per altri progetti Commerce, puoi impostare e utilizzare il servizio [Registri New Relic](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) per completare le seguenti attività:
   - Utilizza [query New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) per cercare dati di registro aggregati.
   - Visualizzare i dati di registro tramite l’applicazione Registri di New Relic.

## Controllare conti, codice e database

Esaminare gli account utente e di amministrazione di Commerce, il codice dell&#39;applicazione, la configurazione del database e i registri per identificare e rimuovere il codice sospetto e garantire la sicurezza dell&#39;accesso a account, siti e database. Quindi, ridistribuisci se necessario.

Continuare a monitorare attentamente il sito dopo l&#39;incidente poiché molti siti vengono compromessi di nuovo in poche ore. Verifica continua del registro e monitoraggio dell&#39;integrità dei file per rilevare rapidamente eventuali segni di nuovi compromessi.

### Controlla account utente amministratore

- [Controlla accesso utente amministratore](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html): consente di rimuovere account vecchi, inutilizzati o sospetti e di ruotare le password per tutti gli utenti amministratore.

- [Esamina le impostazioni](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) di sicurezza dell&#39;amministratore: verifica che le impostazioni di sicurezza dell&#39;amministratore seguire le best practice per la sicurezza.

- [Esamina gli account utente di Adobe Systems Commerce su infrastruttura cloud progetti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html), Rimuovi account vecchi, inutilizzati o sospetti e ruota le password per tutti gli utenti amministratori cloud progetto. Assicurati che account impostazioni di sicurezza siano configurate correttamente.

- [Controlla le chiavi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) SSH per Adobe Systems Commerce su infrastruttura cloud: rivedi, elimina e ruota le chiavi SSH.

### Codice di controllo

- Dall&#39;amministratore, esamina la configurazione[&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) dell&#39;intestazione HTML e del piè di pagina in tutti i livelli ambito, inclusi `website` e `store view`. Rimuovere eventuali codici JavaScript sconosciuti dagli script e dai fogli di stile e da impostazioni HTML varie. Conserva solo il codice riconosciuto, ad esempio i frammenti di tracciamento.

- Confrontare la base di codice di produzione corrente con la base di codice memorizzata nel sistema di controllo delle versioni (VCS, Version Control System).

- Metti in quarantena qualsiasi codice sospetto.

- Assicurati che non vi siano residui di codice sospetto ridistribuendo la base di codice nell’ambiente di produzione.

### Controlla la configurazione del database e i registri

- Esaminare le stored procedure per le modifiche.

- Verificare che il database sia accessibile solo dall&#39;istanza di Commerce.

- Verificare che il malware non sia più presente analizzando il sito con gli strumenti di scansione del malware disponibili pubblicamente.

- Proteggere il pannello di amministrazione modificandone il nome e verificando che gli URL del sito `app/etc/local.xml` e `var` non siano accessibili al pubblico.

- Continuare a monitorare attentamente il sito dopo l&#39;incidente poiché molti siti vengono compromessi di nuovo in poche ore. Verifica continua del registro e monitoraggio dell&#39;integrità dei file per rilevare rapidamente eventuali segni di nuovi compromessi.

## Rimuovi avvisi di Google

Se il sito è stato contrassegnato da Google come contenente codice dannoso, richiedi una revisione dopo la pulizia del sito. Le recensioni per i siti infetti da malware richiedono alcuni giorni. Quando Google determina che il sito è pulito, gli avvisi provenienti dai risultati della ricerca e dai browser dovrebbero scomparire entro 72 ore. Vedi [Richiedi una revisione](https://web.dev/articles/request-a-review).

## Controlla elenco di controllo risultati malware

Se gli strumenti di scansione del malware disponibili pubblicamente confermano un attacco di malware, indagare l&#39;incidente. Collabora con l’integratore di soluzioni per pulire il sito e seguire il processo di correzione consigliato.

## Condurre ulteriori revisioni

Quando si ha a che fare con attacchi sofisticati, la migliore linea d&#39;azione è lavorare con uno sviluppatore esperto, un esperto di terze parti o un integratore di soluzioni per riparare completamente il sito e rivedere le pratiche di sicurezza. Lavorare con professionisti della sicurezza esperti garantisce che vengano adottate misure complete e avanzate per garantire la sicurezza della tua azienda e dei suoi clienti.

## Informazioni aggiuntive

- [Framework di analisi](https://sansec.io/kb/incident-response/magento-root-cause-analysis) delle cause principali.

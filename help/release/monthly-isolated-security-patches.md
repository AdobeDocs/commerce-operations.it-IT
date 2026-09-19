---
title: Criterio di applicazione patch di sicurezza isolato ogni mese
description: Scopri le patch di sicurezza isolate mensili di Adobe Commerce, distribuite martedì per fornire correzioni CVE mirate tra le versioni delle patch di sicurezza.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
    internal-label: PCI
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 66d7c9fd19785e791635d8e8bdf3d6ff3aa27a20
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%
---
# Criteri di applicazione patch di sicurezza isolati mensili

Per consentire ai clienti di Adobe Commerce di applicare prima correzioni di sicurezza critiche, Adobe Commerce ora distribuisce patch di sicurezza isolate mensili il martedì delle patch (il secondo martedì del mese). Per conoscere le date, consulta la [pianificazione del rilascio di Adobe Commerce](schedule.md). Queste patch sono disponibili per le installazioni di Adobe Commerce on Cloud, Adobe Commerce on-premise e Magento Open Source.

Un file di patch di sicurezza isolato contiene solo il codice necessario per risolvere una o più vulnerabilità di sicurezza specifiche, distribuito come file code-diff con ambito ristretto anziché come pacchetto Composer completo. Poiché le modifiche sono specifiche per le vulnerabilità di sicurezza, possono essere riviste, testate e applicate più rapidamente rispetto a una versione di patch di sicurezza, senza attivare la risoluzione più ampia delle dipendenze e il test di regressione necessari per l’aggiornamento di una versione di patch di sicurezza. Ogni file di patch di sicurezza isolato mensile viene piegato nella successiva versione completa della patch di sicurezza, in modo che i clienti possano ottenere tutti i file di patch isolati rilasciati tramite la successiva versione della patch di sicurezza (`-pN`).

## Come si adattano i cerotti isolati ad altri tipi di cerotti

Le patch di sicurezza isolate sono uno dei diversi tipi di patch fornite da Adobe Commerce per proteggere i clienti e mantenerli aggiornati.

| **Tipo di patch** | **Scopo** | **Comportamento cumulativo** | **Consegna tipica** | **Ruolo** |
| --- | --- | --- | --- | --- |
| Versione patch di sicurezza (-pN) | Aggiornamento della sicurezza e della conformità per una riga di rilascio supportata | Cumulativo: stabilisce la linea di base di sicurezza corrente. | Pacchetto Compositore | Linea di base di sicurezza primaria supportata |
| File patch di sicurezza isolato | Correzione mirata per uno o più CVE | Non cumulativo: applica in sequenza | File di patch autonomo, solitamente un file ZIP. Alcune correzioni potrebbero essere incluse anche nelle patch cloud per Commerce | Correzione intermedia più rapida tra le versioni delle patch di sicurezza |
| Patch cloud per Commerce | Correzioni critiche richieste (incluse correzioni di sicurezza) e modifiche specifiche per il cloud | Dipendente dalla versione del pacchetto | Patch cloud per il pacchetto Commerce gestite tramite gli strumenti ECE | Applicato automaticamente durante l’implementazione cloud |
| Patch Quality Tool (QPT) | Correzione facoltativa e mirata di problemi di qualità o compatibilità per un problema specifico | Dipendente da catena di patch | Pacchetto QPT | Correzioni di qualità mirate |
| Hotfix | Correzione urgente e di portata limitata (ad esempio, un giorno zero) | Specifico per caso | Pacchetto ZIP/diff o autonomo tramite QPT | Problemi urgenti e di forte impatto |

I due tipi di patch di sicurezza svolgono ruoli diversi:

* **Le patch isolate** contengono solo correzioni di vulnerabilità e non sono cumulative. Non raggruppano i file di patch isolati rilasciati in precedenza. I commercianti devono applicare le patch in ordine, in quanto ogni nuova patch presuppone che siano state implementate quelle precedenti. Per applicare una patch di sicurezza isolata, l’installazione deve essere nell’ultima versione della patch di sicurezza per la propria linea supportata, perché le correzioni isolate vengono testate esclusivamente per tale versione.

* **Le patch di sicurezza (`-pN`)** vengono rilasciate ogni anno per tutte le righe di rilascio supportate e distribuite tramite Composer. Includono tutti gli hotfix di sicurezza, conformità e qualità rilasciati in precedenza. Se necessario, Adobe può rilasciare patch di sicurezza aggiuntive.

## Vantaggi mensili delle patch isolate

L&#39;individuazione delle vulnerabilità ha subito un&#39;accelerazione in tutto il settore. Gli strumenti di analisi assistiti dall&#39;intelligenza artificiale possono ora scansionare grandi basi di codice e difetti superficiali molto più rapidamente della revisione manuale, riducendo la finestra tra la divulgazione e lo sfruttamento. Una cadenza mensile di patch isolate colma questo vuoto fornendo correzioni non appena sono pronte, invece di attendere il successivo rilascio pianificato delle patch di sicurezza.

L&#39;obiettivo è la velocità senza sovraccarichi inutili. Una correzione pronta non rimane in coda fino alla prossima versione della patch di sicurezza e gli esercenti non applicano la patch più spesso del necessario. I file di patch di sicurezza isolati risolvono tale tensione: ciascuno è una piccola differenza di sicurezza, molto più semplice da esaminare e applicare rispetto a una versione di patch di sicurezza, perché il suo ambito è deliberatamente limitato.

Questo approccio funziona perché le patch monouso ignorano la risoluzione delle dipendenze e il test di regressione completo richiesti per le versioni del Compositore, consentendo loro di essere create, convalidate rispetto a una linea di base nota e spedite rapidamente. Sull’infrastruttura cloud, queste correzioni sono incluse in Cloud Patches per Commerce, un pacchetto che i commercianti aggiornano come parte del loro flusso di lavoro di composizione e distribuzione. Una volta aggiornata, la correzione si applica automaticamente durante la distribuzione senza alcun file di patch separato da individuare o applicare. Il flusso di lavoro manuale per file di patch descritto nei bollettini sulla sicurezza è destinato alle installazioni locali e Magento Open Source che non eseguono la pipeline cloud.

## Applicare patch isolate mensili

Per applicare il file patch di sicurezza isolato mensile e mantenere aggiornate le ultime correzioni, attenersi alla procedura descritta di seguito:

1. **Verifica la [pianificazione del rilascio](schedule.md).**

   I nuovi file patch isolati mensili vengono spediti in base alla pianificazione del rilascio. Esamina il corrispondente bollettino sulla sicurezza per i componenti e i CVE interessati. Ogni bollettino contiene collegamenti alle note sulla versione con istruzioni dettagliate per l’installazione del file patch isolato del mese in questione.

1. **Verifica lo stato di sicurezza dell&#39;installazione di Commerce utilizzando [Commerce Version Tool](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/commerce-version-tool/intro).**

   Lo strumento segnala quali patch mensili sono attualmente installate, quali mancano e a quali CVE rimane esposta l’installazione. Questo fornisce una valutazione definitiva di quale azione è necessaria, piuttosto che basarsi solo sul numero di versione.

1. **Conferma la versione di base.**

   Le patch isolate vengono testate solo in base all&#39;ultima versione `-p` di sicurezza per la tua linea. Se si è in ritardo rispetto a tale linea di base, applicarla prima.

1. **Applica tutte le patch mancanti nell&#39;ordine.**

   Poiché non sono cumulativi, non è possibile passare al file più recente.

   >[!NOTE]
   >
   >**Clienti cloud:** Controlla prima le patch cloud installate per Commerce [versione](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). La correzione potrebbe essere già inclusa e applicarla manualmente potrebbe creare un conflitto o duplicare la correzione.

1. **Associa i file ai componenti installati.**

   Applica solo il file che corrisponde alla versione del tuo CE, EE, B2B o altro componente.

1. **Rieseguire lo strumento Versione di Commerce per confermare.**

   Verificate che la nuova patch sia installata e che i CVE pertinenti siano ora protetti.

1. **Test, quindi distribuzione.**

   Convalida nella gestione temporanea prima della promozione in produzione, in base al normale processo di modifica.

I clienti Cloud possono inoltre utilizzare [Adobe Commerce Patching Automation](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/caps-tool/intro) per applicare o ripristinare le patch tramite il pannello di amministrazione anziché i passaggi manuali Git e Compositore descritti sopra.

## Azioni patch per tipo di distribuzione

| **Esecuzione in corso...** | **Cosa cambia per te** |
| --- | --- |
| Adobe Commerce su Cloud | Le patch cloud per Commerce, distribuite tramite ECE-Tools, applicano automaticamente le correzioni richieste durante la prossima implementazione. Puoi comunque controllare i passaggi di diramazione, unione e convalida. Prima di applicare manualmente la stessa correzione, controlla le note sulla versione delle patch cloud per Commerce. |
| Adobe Commerce on-premise | Conferma la versione `-p` della linea di base, scarica il file corrispondente a ciascun componente installato, applica in sequenza e verifica con lo strumento Versione di Commerce. |

## Domande frequenti

L’applicazione di patch di sicurezza isolate mensili è una nuova versione dei criteri. Le domande seguenti affrontano problemi comuni.

### È necessario applicare tutte le patch isolate precedenti o solo la versione più recente delle patch di sicurezza?

Vi servono entrambe. Prima di applicare una patch isolata, eseguire l&#39;aggiornamento alla versione di base più recente per la sola protezione `-p`. Ogni cerotto viene testato solo rispetto a tale linea di base. Le patch isolate non sono cumulative, quindi applicare tutte le patch mancanti in sequenza.

Ad esempio, se ti trovi nella linea di base della versione `-p` corrente ma non hai rilevato le patch isolate di luglio e agosto, applica le versioni di luglio, agosto e settembre. La prossima versione completa di `-p` ripristina la sequenza perché include tutte le correzioni isolate emesse in precedenza.

### Perché non spedire solo un pacchetto Compositore invece di file patch separati?

In un&#39;installazione con più componenti (CE, EE, B2B e Page Builder), una versione mensile potrebbe richiedere file patch separati, in quanto ogni file è destinato a una specifica versione del componente installato. La combinazione di tutte le correzioni in un unico pacchetto Compositore reintrodurrebbe i problemi di risoluzione delle dipendenze e richiederebbe un test di regressione a tutta la superficie; i rischi che le patch isolate sono progettate per evitare. I clienti cloud non devono applicare le patch manualmente. Le patch cloud per Commerce forniscono le stesse correzioni tramite la pipeline di distribuzione esistente.

### Con le patch su più livelli, come posso sapere in quale stato di sicurezza si trova la mia installazione?

Con il rilascio delle patch di sicurezza mensili, Adobe Commerce ha introdotto [Commerce Version Tool](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/commerce-version-tool/intro), un&#39;utility autonoma che segnala quali patch sono installate o mancanti e quali CVE sono protette dall&#39;installazione. Invece di affidarsi ai numeri di versione, lo strumento legge i metadati delle patch e fornisce un output leggibile al computer per il reporting e l’integrazione continua (CI).

### Questo significa che Adobe ha fatto un passo indietro rispetto ai rilasci di sicurezza cumulativi e con versioni?

No. La versione annuale di `-p` rimane il punto di controllo di sicurezza primario e cumulativo. I cerotti isolati integrano tale cadenza per i CVE che non possono attenderla in modo sicuro. Non sostituiscono le versioni `-p`. Se applichi ogni anno il rilascio della patch di sicurezza pianificato per la tua linea, rimani su un percorso completamente supportato e ricevi ogni correzione mai rilasciata come file isolato nel mezzo.

### Le correzioni apportate alla spedizione al di fuori di Composer rendono un&#39;installazione predefinita meno sicura?

No. Il meccanismo di consegna non influisce sul risultato di sicurezza della correzione. Una patch isolata applica la stessa modifica al codice successivamente inclusa in una versione completa (`-p`). Che la correzione venga distribuita come pacchetto Compositore o come file standalone non ha alcuna influenza sulla sua efficacia. I commercianti che non applicano la patch rimangono alla linea di base di sicurezza esistente fino alla successiva versione di sicurezza pianificata. L’applicazione di patch isolate può ridurre l’esposizione distribuendo le correzioni più rapidamente, anziché attendere un ciclo di rilascio completo.

## Ulteriori informazioni su questo argomento

>[!MORELIKETHIS]
>
>* [Criteri del ciclo di vita del software](lifecycle-policy.md)
>* [Criteri di rilascio](versioning-policy.md)
>* [Pianificazione rilascio patch](schedule.md)
>* [Strumento Versione Commerce](../tools/commerce-version-tool/intro.md)
>* [Bollettini sulla sicurezza e avvisi di Adobe](https://helpx.adobe.com/it/security/security-bulletin.html)

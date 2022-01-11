---
title: Best practice
description: Utilizza le best practice consigliate per Adobe per gestire il processo di aggiornamento dei progetti Adobe Commerce e Magenti Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per l’aggiornamento

In questo argomento sono elencate le azioni da intraprendere per gestire la complessità dell’aggiornamento dei progetti Adobe Commerce e Magenti Open Source. Il team deve pensare agli aggiornamenti dal momento in cui inizia lo sviluppo del progetto e continuare attraverso ogni versione. Seguendo queste best practice, il processo di aggiornamento sarà molto più semplice, veloce e meno costoso.

>[!TIP]
>
>Tali raccomandazioni si basano sulle migliori pratiche, corroborate da prove dell&#39;impatto e dell&#39;efficacia di queste ultime da parte di partner, commercianti, esperti di Adobe e della Comunità.

## Che impatto ha un aggiornamento?

È importante comprendere le variabili che determinano la complessità di un aggiornamento. Devi considerare queste variabili all&#39;inizio di ciascun progetto, non solo quando è il momento di eseguire l&#39;aggiornamento. Lo sviluppo di un progetto è fondamentale per garantire che gli aggiornamenti futuri siano lisci e che tu sia in grado di controllare lo sforzo necessario per completarli.

Il livello di impegno per l’aggiornamento dell’istanza Adobe Commerce dipende da questi fattori:

- **Come avete costruito il vostro sito?** La quantità di lavoro personalizzato e il numero di moduli di terze parti installati influisce fortemente sulla complessità di un aggiornamento. La qualità del lavoro personalizzato e dei moduli può determinare se un aggiornamento va senza problemi.

- **Stai saltando più versioni?** Saltare le versioni rende il prossimo aggiornamento più complesso, l&#39;aggiornamento da versioni successive rende il processo più semplice e meno costoso.

- **Che tipo di aggiornamento stai eseguendo?** Un aggiornamento a una versione minore (ad esempio da 2.3.x a 2.4.0) è più esteso di un aggiornamento tra le versioni della patch (ad esempio da 2.4.2 a 2.4.3). Gli aggiornamenti di sicurezza sono il tipo più semplice da implementare.

## Best practice per la pianificazione degli aggiornamenti

Se lavori su un progetto già in produzione, gli aggiornamenti ti offrono l’opportunità di migliorare la qualità del codice e delle personalizzazioni e di ottimizzare gli aggiornamenti futuri. Il tempo che investi oggi è risparmiato nel lungo periodo.

Se gestisci più siti per diversi merchants, l’approccio migliore è quello di avere un’istanza di base con le caratteristiche principali e le personalizzazioni normalmente utilizzate. Utilizza questa istanza di base come sito di test per completare un aggiornamento e poi eseguine altre. Questa procedura offre la flessibilità di riutilizzare moduli personalizzati per clienti diversi e di semplificare gli aggiornamenti tra progetti.

Se il progetto è attivo, ti consigliamo di eseguire un controllo di audit per determinarne la qualità e di capire come migliorarlo per renderlo più efficiente.

### Sviluppo con gli aggiornamenti

Dal momento in cui inizi a lavorare su un progetto, dovresti considerare in che modo gli aggiornamenti futuri saranno influenzati dal tuo lavoro attuale. Segui sempre le best practice di sviluppo Adobe Commerce come descritto qui:

- [Best practice di sviluppo](https://devdocs.magento.com/guides/v2.4/ext-best-practices/bk-ext-best-practices.html)
- [Standard di codifica](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)

Se non lo hai già fatto, inizia ad adottare la piattaforma di estensibilità di Adobe Commerce. La piattaforma consente di personalizzare in modo efficiente i processi, integrare i sistemi e implementare nuove funzionalità, mantenendo al tempo stesso la possibilità di aggiornare SaaS. Le sue caratteristiche includono:

- **Estensibilità dell’interfaccia utente**. Estendi ed evolvi la vetrina indipendentemente dal backend e dal middleware che utilizzi [PWA Studi](https://developer.adobe.com/commerce/pwa-studio/).

- **Estensibilità API**. Utilizzo [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) estendere il livello API web evolvendo il modello dati grafico ed eseguendo funzioni lambda direttamente dal livello grafico.

- **Adobe I/O middleware e servizi**. Collega i tuoi sistemi con Adobe Commerce utilizzando il middleware di Adobe e una suite di connessioni app basate su [Adobe I/O](https://www.adobe.io/). Inoltre, puoi estendere le funzionalità di base della piattaforma sovrascrivendo il comportamento predefinito con la tua logica di business che viene eseguita su Adobe I/O.

### Aggiornamento della pianificazione

Man mano che espandiamo continuamente le funzionalità di Adobe Commerce, è fondamentale che tu sviluppi le ultime versioni disponibili e definisca una strategia di aggiornamento nei tuoi piani di progetto. In questo modo potrai essere sicuro, conforme e aggiornato sugli ultimi miglioramenti che ti consentono di incrementare le vendite più rapidamente, operare in modo più efficace e rimanere al passo con la concorrenza attuale e futura.

Per facilitare la pianificazione e il budget degli aggiornamenti, è necessario monitorare il nostro [programma di rilascio](https://devdocs.magento.com/release). Pianifica in anticipo le attività di aggiornamento all’interno del backlog del tuo team. Scopo di completare questo lavoro con GA.

- Per informazioni su ogni nuova versione, utilizza la versione precedente al rilascio. Il pre-rilascio è il codice di disponibilità generale disponibile per gli esercenti Adobe Commerce e tutti i partner due settimane prima della disponibilità generale. Se disponi di più store, utilizza il pre-release sul tuo archivio di base e verifica che i moduli e i temi personalizzati siano compatibili con esso.

- Consulta la sezione [Elenco di controllo piano di aggiornamento](https://support.magento.com/hc/en-us/articles/360057968951) per Adobe Commerce per pianificare l’aggiornamento.

- Pianificare gli aggiornamenti all&#39;inizio dell&#39;anno. È necessario prenotare un budget e risorse per completare ogni aggiornamento. Lo sforzo di aggiornamento può variare notevolmente da un progetto all’altro. Utilizza le tue esperienze e conoscenze per realizzare un piano il più accurato possibile.

- Se gli aggiornamenti richiedono più impegno rispetto a quanto descritto qui, è consigliabile controllare il progetto e apportare modifiche all’ambiente per ridurre la manutenzione a lungo termine.

### Esecuzione degli aggiornamenti

Gli aggiornamenti devono essere effettuati regolarmente e con un budget predefinito. Consigliamo di pianificare aggiornamenti pre-approvati all&#39;inizio dell&#39;anno per garantire che gli aggiornamenti siano pianificati e completati in tempo.

Valutare il lavoro da eseguire per l’aggiornamento:

- Consulta la sezione [note sulla versione](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) per comprendere l’ambito e l’impatto della nuova versione.

- Utilizza la [Strumento di compatibilità per l’aggiornamento](../upgrade-compatibility-tool/overview.md) per identificare potenziali problemi che devono essere risolti nel codice personalizzato prima di tentare di eseguire l&#39;aggiornamento a una versione più recente.

- Se utilizzi estensioni di terze parti, convalidane la compatibilità con la versione di destinazione in cui intendi eseguire l’aggiornamento.

### Test post-aggiornamento

Il test è la fase di un aggiornamento che richiede il maggior tempo. Di conseguenza, tale processo dovrebbe essere il più automatizzato possibile. Puoi sfruttare i vantaggi dell’utilizzo degli strumenti di test di base. La [Guida al test delle applicazioni](https://devdocs.magento.com/guides/v2.4/test/testing.html) fornisce dettagli.

Utilizza un ambiente di staging per testare e convalidare l’aggiornamento prima di passare alla produzione.

Utilizzare un **pagina di manutenzione**. La preparazione anticipata di questa pagina ti consente di comunicare con i tuoi clienti, avvisandoli che il lavoro sta avvenendo in background. Questa pagina deve essere visibile per alcuni minuti, ma in caso di problemi potrebbe essere necessario utilizzarla più a lungo. Disporre del contenuto e della progettazione appropriati per la pagina di manutenzione offre agli utenti una buona esperienza anche quando lo store non è disponibile.

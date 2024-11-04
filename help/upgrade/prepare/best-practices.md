---
title: Best practice
description: Utilizza le best practice consigliate da Adobe per gestire il processo di aggiornamento per i progetti Adobe Commerce.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Best practice per l&#39;aggiornamento

In questo argomento sono elencate le azioni da intraprendere per gestire la complessità dell’aggiornamento dei progetti Adobe Commerce. Il tuo team deve pensare agli aggiornamenti dal momento in cui inizia lo sviluppo del progetto e continuare attraverso ogni versione. Seguendo queste best practice, il processo di aggiornamento sarà molto più semplice, rapido e conveniente.

>[!TIP]
>
>Queste raccomandazioni si basano sulle best practice supportate da dati comprovanti il suo impatto e la sua efficacia da parte di partner, esercenti, Adobe e la community.

## Che impatto ha un aggiornamento?

È importante comprendere le variabili che determinano la complessità di un aggiornamento. Devi considerare queste variabili all&#39;inizio di ogni progetto, non solo quando è il momento di eseguire l&#39;aggiornamento. Lo sviluppo di un progetto è fondamentale per garantire che gli aggiornamenti futuri siano fluidi e che tu sia in grado di controllare lo sforzo necessario per completarli.

Il livello di impegno per aggiornare l’istanza di Adobe Commerce dipende da questi fattori:

- **Come è stato creato il sito?** La quantità di lavoro personalizzato e il numero di moduli di terze parti installati influiscono notevolmente sulla complessità di un aggiornamento. La qualità del lavoro e dei moduli personalizzati può determinare se un aggiornamento procede senza problemi.

- **Verranno ignorate più versioni?** Ignorare le versioni rende il prossimo aggiornamento più complesso. L&#39;aggiornamento dalle versioni successive rende il processo più semplice e meno costoso.

- **Che tipo di aggiornamento si sta eseguendo?** Un aggiornamento a una versione secondaria (ad esempio da 2.3.x a 2.4.0) è più esteso di un aggiornamento tra versioni patch (ad esempio da 2.4.2 a 2.4.3). Gli aggiornamenti di sicurezza sono il tipo più semplice da implementare.

## Best practice per la pianificazione degli aggiornamenti

Se stai lavorando a un progetto che è già in produzione, gli aggiornamenti sono un’opportunità per migliorare la qualità del codice e delle personalizzazioni e per ottimizzare i futuri aggiornamenti. Il tempo che investite oggi è risparmiato a lungo termine.

Se gestisci più siti per diversi commercianti, l’approccio migliore consiste nell’avere un’istanza di base con le funzioni e le personalizzazioni principali che utilizzi normalmente. Utilizza questa istanza di base come sito di test per completare un aggiornamento, quindi eseguilo su altri. Questa procedura offre la flessibilità di riutilizzare i moduli personalizzati per clienti diversi e semplificare gli aggiornamenti tra i progetti.

Se il progetto è live, ti consigliamo di eseguire un controllo di audit per determinarne la qualità e di capire come migliorarlo per rendere gli aggiornamenti più efficienti.

### Sviluppo pensando agli aggiornamenti

Dal momento in cui inizi a lavorare su un progetto, dovresti considerare in che modo i futuri aggiornamenti saranno influenzati dal lavoro corrente. Segui sempre le best practice di sviluppo di Adobe Commerce come descritto qui:

- [Best practice per lo sviluppo](https://developer.adobe.com/commerce/php/best-practices/)
- [Standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/)

Inizia ad adottare la piattaforma Adobe Commerce Extensibility, se non lo hai già fatto. La piattaforma consente di personalizzare in modo efficiente i processi, integrare i sistemi e implementare nuove funzionalità, mantenendo al tempo stesso la possibilità di aggiornamento simile a SaaS. Le sue caratteristiche includono:

- **Estensibilità interfaccia utente**. Estendi ed evolvi la vetrina indipendentemente dal backend e dal middleware utilizzando [PWA Studi](https://developer.adobe.com/commerce/pwa-studio/).

- **Estensibilità API**. Utilizza [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html) per estendere il livello API Web evolvendo il modello dati del grafico ed eseguendo funzioni lambda direttamente dal livello grafico.

- **Servizi e middleware di Adobe I/O**. Connetti i tuoi sistemi con Adobe Commerce utilizzando il middleware di Adobe e una suite di connessioni alle app basate su [Adobe I/O](https://www.adobe.io/). Inoltre, puoi estendere le funzionalità della piattaforma di base sovrascrivendo il comportamento predefinito con la tua logica di business che viene eseguita su Adobe I/O.

### Aggiornamenti di Planning

Man mano che le funzionalità di Adobe Commerce vengono continuamente ampliate, è fondamentale che tu sviluppi l’ultima versione disponibile e definisca una strategia di aggiornamento nei piani dei tuoi progetti. In questo modo potrai rimanere sicuro, conforme e aggiornato sugli ultimi miglioramenti, consentendoti di incrementare le vendite in modo più rapido, di operare in modo più efficace e di restare al passo con la concorrenza attuale e futura.

Per aiutarti a pianificare e pianificare il budget per gli aggiornamenti, devi monitorare la [pianificazione delle versioni](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule). Pianifica in anticipo le attività di aggiornamento nel backlog del team. Completa questo lavoro con GA.

- Utilizza la versione non definitiva per scoprire ogni nuova versione. La versione non definitiva è il codice di disponibilità generale disponibile per i commercianti Adobe Commerce e per tutti i partner due settimane prima della disponibilità generale. Se disponi di più store, utilizza la versione non definitiva sullo store di base e verifica che i moduli e i temi personalizzati siano compatibili con esso.

- Consulta la [Lista di controllo del piano di aggiornamento](https://support.magento.com/hc/en-us/articles/360057968951) per Adobe Commerce per aiutarti a pianificare l&#39;aggiornamento.

- Pianificare gli aggiornamenti all&#39;inizio dell&#39;anno. È necessario registrare un budget e le risorse per completare ogni aggiornamento. Ricorda che lo sforzo di aggiornamento potrebbe variare notevolmente da un progetto all’altro. Utilizza le tue esperienze e conoscenze per creare un piano il più accurato possibile.

- Se gli aggiornamenti richiedono più tempo di quanto qui descritto, ti consigliamo di controllare il progetto e apportare modifiche all’ambiente per ridurre la manutenzione a lungo termine.

### Esecuzione degli aggiornamenti

Gli aggiornamenti devono essere effettuati regolarmente e in base a un budget predefinito. Si consiglia di pianificare gli aggiornamenti preapprovati all&#39;inizio dell&#39;anno per assicurare che vengano pianificati e completati in tempo.

Valutare il lavoro da eseguire per l&#39;aggiornamento:

- Consulta le [note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) per comprendere l&#39;ambito e l&#39;impatto della nuova versione.

- Utilizza [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) per identificare potenziali problemi che devono essere risolti nel codice personalizzato prima di tentare l&#39;aggiornamento a una versione più recente.

- Se utilizzi estensioni di terze parti, verifica la loro compatibilità con la versione di destinazione a cui intendi effettuare l’aggiornamento.

### Test post-aggiornamento

Il test è la fase di un aggiornamento che richiede più tempo. Di conseguenza, questo processo dovrebbe essere il più possibile automatizzato. Puoi trarre vantaggio dall’utilizzo degli strumenti di test di base. La [Guida al test delle applicazioni](https://developer.adobe.com/commerce/testing/guide/) fornisce dettagli.

Utilizza un ambiente di staging per testare e convalidare l’aggiornamento prima di passare alla produzione.

Utilizza una **pagina di manutenzione**. La preparazione anticipata di questa pagina consente di comunicare con i clienti e di avvisarli che il lavoro è in corso in background. Questa pagina dovrebbe essere visibile per alcuni minuti, ma in caso di problemi potrebbe essere necessario usarla più a lungo. La possibilità di disporre del contenuto e della progettazione appropriati per la pagina di manutenzione offre agli utenti una buona esperienza anche quando il negozio non è disponibile.

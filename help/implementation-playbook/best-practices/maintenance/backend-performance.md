---
title: Ottimizzare le prestazioni del back-end
description: Scopri come ottimizzare le prestazioni di back-end dei siti Adobe Commerce.
badge: label="Contribuito da objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: e5df5a7242dbe8ceff548257daeb39f7c9fc5c69
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Best practice per ottimizzare le prestazioni del back-end

Questo argomento illustra le best practice per l’analisi e l’ottimizzazione delle prestazioni back-end dei siti Adobe Commerce, con particolare attenzione all’ottimizzazione e al test dei database. Gli sviluppatori possono utilizzare queste informazioni per analizzare il contesto univoco di ciascun progetto Commerce e identificare le opportunità per ottimizzare la configurazione back-end e le operazioni per migliorare le prestazioni del sito.

>[!NOTE]
>
>Recommendations ed esempi si ispirano ai processi che objectsource segue negli impegni dei clienti reali per fornire siti Adobe Commerce ad alte prestazioni su larga scala.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Ottimizzare il database per migliorare le prestazioni

L&#39;ottimizzazione del database è un modo sicuro per migliorare l&#39;esperienza utente e aumentare le vendite. Quando ottimizzi il database, la spina dorsale di un sito Commerce, puoi evitare rallentamenti nelle prestazioni del sito web ed eliminare i lunghi tempi di caricamento che creano attrito per i clienti.

### Stress testing

Periodi di traffico elevato come il Black Friday richiedono che i siti Commerce gestiscano volumi di traffico elevati. In preparazione a tali eventi, le prove di stress sono essenziali per comprendere come un sito operi con aumenti esponenziali del carico.

Uno strumento che puoi usare per i test di stress è GTmetrix. Misura la preparazione del sito per l’aumento di carico configurando GTmetrix per replicare e moltiplicare il comportamento e le azioni dei visitatori normali. Quindi, esegui test per identificare e risolvere i problemi che potrebbero influire sulle prestazioni e sulla disponibilità del sito durante i principali eventi di acquisto.

Ulteriori informazioni sulla preparazione di progetti Commerce per periodi con traffico elevato:

- [Preparazione alle festività](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [Analisi acquisti per festività](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Aumento capacità di sovratensione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Test di carico

Puoi anche utilizzare GTmetrix o uno strumento simile per caricare i progetti di prova di Commerce. Come precursore delle prove di stress, le prove di carico sono una pratica essenziale per i siti su larga scala e ad alto traffico. Previeni interruzioni impreviste del sito, clienti frustrati e perdite finanziarie anticipando e mitigando i problemi che influiscono sulle prestazioni del sito durante i picchi di carico.

Utilizza GTmetrix per simulare il traffico pesante e analizzare le prestazioni del sito per ottenere informazioni chiare sulla capacità del sito. Questa analisi consente di identificare e risolvere i colli di bottiglia e di identificare le opportunità da ottimizzare, garantendo che i siti Commerce possano funzionare in modo efficace in condizioni di carico maggiore.

Ulteriori informazioni sulla verifica dei progetti Adobe Commerce:

- [Linee guida per i test](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html)  (infrastruttura cloud)
- [Test delle applicazioni](https://developer.adobe.com/commerce/testing/guide/)

### Identificazione e risoluzione dei problemi di prestazioni

Affronta i problemi di prestazioni utilizzando vari strumenti come New Relic e Observation for Adobe Commerce per rilevare i colli di bottiglia e ottimizzare i siti Commerce in modo efficace. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) è incluso in Adobe Commerce sull’infrastruttura cloud e [Osservazione per Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) è incluso per le distribuzioni cloud e on-premise.

Utilizzare questi strumenti per analizzare le prestazioni del sito e identificare i problemi di prestazioni relativi a:

- Funzionalità a uso intensivo di CPU
- Configurazione della gestione della cache per query e operazioni back-end
- Chiamate API di terze parti
- Pianificazione Cron

Ad esempio, puoi esaminare attentamente le transazioni concentrandoti sui dettagli del prodotto e sulle pagine delle categorie. Identificare i processi che richiedono molto tempo e che possono essere ottimizzati per migliorare le prestazioni. In un progetto client, objectsource ha notato un problema di prestazioni in una pagina dei dettagli di un prodotto e ha rilevato una chiamata API che consuma il 3,5% del tempo necessario per le prestazioni. In base a questo risultato, hanno esaminato la gerarchia di esecuzione del codice per individuare e risolvere il problema che causava il collo di bottiglia.

Ulteriori informazioni sulla gestione delle prestazioni del sito:

- [Monitoraggio delle prestazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (infrastruttura cloud)
- [Valutazione dell’ottimizzazione delle prestazioni](/help/implementation-playbook/infrastructure/performance/recommendations.md)
- [Best practice di configurazione](/help/performance/configuration.md)
- [Osservazione per Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Ottimizzare le prestazioni MySQL

Affrontare i problemi di prestazioni di MySQL implementando il clustering del database e l&#39;ottimizzazione delle query è un approccio efficace per migliorare le prestazioni prima e durante periodi di traffico elevato come il Black Friday.

#### Implementazione del clustering del database

I siti web a traffico elevato spesso si trovano a dover affrontare colli di bottiglia del database, principalmente causati dalla dipendenza da un singolo server MySQL. È possibile risolvere questi colli di bottiglia implementando il clustering del database, un&#39;architettura distribuita che migliora le prestazioni e garantisce un&#39;elevata disponibilità.

Il clustering del database riduce al minimo l&#39;impatto dei problemi correlati al database durante i periodi di picco del traffico consentendo a più nodi Web di connettersi a più server MySQL. Utilizza strumenti come Galera Cluster per configurare il clustering del database per i siti Commerce. Il cluster Galera è incluso in [Progetti Adobe Commerce implementati nell’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/cloud/technology.html).

#### Ottimizzazione delle query MySQL

In genere, l&#39;infrastruttura per la maggior parte dei siti Adobe Commerce è costituita da più nodi Web connessi a un unico server MySQL.

In questa configurazione, ogni nodo Web front-end si connette al cluster Galera, che consente più server MySQL. L&#39;aumento del numero di nodi Web front-end può migliorare le prestazioni delle applicazioni, ma il singolo server MySQL rimane un collo di bottiglia.

Per ottimizzare le prestazioni del server MySQL e ridurre al minimo i colli di bottiglia, è essenziale identificare e ridurre le query non necessarie. Ad esempio, se invii 1.000 query al secondo, ma sono necessarie solo 200, l’ottimizzazione e la riduzione del conteggio delle query possono migliorare notevolmente le prestazioni.

Ulteriori informazioni sulla configurazione e l&#39;ottimizzazione di MySQL:

- [Procedure consigliate per la configurazione del database](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Replica lenta per la replica di Galera DB](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Linee guida generali di MySQL](/help/installation/prerequisites/database/mysql.md)
- [Memorizzazione in cache delle query MySQL](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Gestire i processi cron in modo efficace: prestazioni e tempi

I processi Cron svolgono un ruolo fondamentale nell’elaborazione delle attività in background del sito, come la generazione di rapporti e l’indicizzazione dei prodotti. Tuttavia, l’ottimizzazione dei processi cron richiede un’attenta valutazione del loro impatto sulle prestazioni complessive. Gli sviluppatori devono valutare la frequenza di pianificazione e determinare la tempistica ottimale in base a requisiti specifici.

Bilanciando prestazioni e convenienza, è spesso consigliabile pianificare i lavori cron durante i periodi a traffico ridotto. Tuttavia, trattare con clienti in diversi fusi orari può presentare problemi, richiedendo un approccio attento per garantire un’esperienza armoniosa in più aree geografiche.

Se sei responsabile dell’ottimizzazione delle prestazioni e della tempistica dei cron, rivedi la configurazione cron corrente dall’amministratore di Commerce e scopri come impostare e configurare i processi cron per i progetti Commerce.

Inoltre, puoi utilizzare Osservazione per Adobe Commerce per visualizzare gli indicatori di prestazioni relativi ai cron. Questo strumento combina i dati di registro provenienti da più origini per aiutarti a gestire meglio le prestazioni del sito Adobe Commerce e a diagnosticare i problemi.

Ulteriori informazioni sull’implementazione di Adobe Commerce cron:

- [Cron (attività pianificate)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) nel _Guida utente di Commerce Admin Systems_
- [Configurazione dell’applicazione - proprietà crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (infrastruttura cloud)
- [Configurare ed eseguire crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (in loco)
- [Osservazione per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (consultare la [!UICONTROL Cron] e [!UICONTROL MySQL] schede.)

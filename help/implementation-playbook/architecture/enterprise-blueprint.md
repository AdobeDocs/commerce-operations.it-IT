---
title: Architettura di riferimento aziendale
description: Scopri come implementare Adobe Commerce utilizzando la più recente tecnologia di e-commerce componibile di Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
source-git-commit: 96afb0ccf5ea872cb42320babfd04ba51fa7dbf6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---


# Architettura di riferimento aziendale Adobe Commerce

Adobe Commerce è la piattaforma basata sull’esperienza che associa in modo univoco flessibilità tecnica e facilità d’uso, il tutto al servizio della creazione di esperienze eccezionali che producono risultati aziendali.

Commerce si è evoluto per soddisfare i requisiti aziendali in termini di prestazioni, scalabilità e sicurezza. L’adozione di un approccio di implementazione moderno che utilizza le più recenti soluzioni di e-commerce componibili di Adobe è fondamentale per il successo delle aziende. Questa pagina descrive nei dettagli tecnici il moderno approccio di implementazione di Commerce.

Il diagramma seguente illustra il flusso di dati tra Adobe Commerce e tutte le soluzioni Adobe Experience Cloud.

![Diagramma architetturale che mostra il modo in cui Adobe Commerce si connette alle soluzioni Experience Cloud](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>I flussi di dati di alto livello mostrati nel diagramma sono coerenti nella maggior parte delle implementazioni aziendali. Il componente chiave che può rendere univoche le implementazioni è il modo in cui crei il catalogo (in particolare per il B2B). È necessario mappare attentamente l’architettura del catalogo al [API web di Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) è il fondamento dell’implementazione di Commerce. Fornisce un [protetto](../../security-and-compliance/shared-responsibility.md) piattaforma di hosting automatizzata con un approccio self-service per creare, distribuire, monitorare e gestire l’applicazione Commerce in un ambiente nativo per il cloud.

Consulta i seguenti dettagli tecnici di cloud foundation:

- [**Architettura scalata**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)- Capacità regolata automaticamente per mantenere prestazioni stabili e prevedibili
- [**Più ambienti**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture): preinstallato con PHP, MySQL (MariaDB), Redis, RabbitMQ e tecnologie di motori di ricerca supportate per sviluppare, testare e distribuire il sito
- [**Gestione della configurazione**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview): file di configurazione dell&#39;ambiente personalizzabili e interfaccia CLI (Command-Line Interface) per gestire le impostazioni dell&#39;applicazione, le route, le azioni di generazione e distribuzione e le notifiche.
- [**Flusso di lavoro basato su Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): creazione e distribuzione automatiche dopo il push delle modifiche al codice per lo sviluppo rapido e la distribuzione continua
- [**Osservabilità integrata**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)- Strumenti che combinano i dati di registro provenienti da più origini per gestire le prestazioni del sito e diagnosticare i problemi
- [**Copertura API completa**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) e [REST](https://developer.adobe.com/commerce/webapi/rest) API per l’integrazione dell’applicazione Commerce di base con sistemi di terze parti e per l’estensione delle funzionalità Commerce

## Integrazione con Experience Cloud

Adobe Commerce si integra con tutte le soluzioni Experience Cloud per offrire [esperienze di e-commerce personalizzate su larga scala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Connessione dati](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) sblocca informazioni sul comportamento d’acquisto dei tuoi acquirenti, in modo da poter creare esperienze d’acquisto personalizzate su tutti i canali con altri prodotti Adobe Digital Experience.

>[!NOTE]
>
>Consulta [Blueprint di esperienza digitale](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) per maggiori dettagli tecnici.


## Integrazione con sistemi di terze parti

Adobe fornisce agli sviluppatori punti di estensione e strumenti completi per creare applicazioni che estendono le funzionalità Commerce di base e integrano Commerce con sistemi di terze parti (come CRM, ERPS e PIMS). Questi strumenti riducono il costo totale di proprietà della piattaforma nei seguenti modi:

- **Scalabilità**- Le applicazioni possono essere scalate separatamente dal software principale, consentendo una maggiore efficienza e aggiornamenti semplificati.
- **isolamento**-Un ambiente isolato consente agli sviluppatori di aggiornare o modificare le estensioni a loro discrezione senza affidarsi a una versione di base.
- **Indipendenza tecnologica**-Gli sviluppatori possono scegliere quale tecnologia stack e linguaggi di codifica si adattano alle loro esigenze.

L’Adobe fornisce i seguenti strumenti per sviluppatori per creare integrazioni e personalizzazioni:

- [**Mesh API per Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/): coordina e combina più API, GraphQL, REST e altre origini in un unico endpoint GraphQL interrogabile.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): crea e distribuisci applicazioni web sicure e scalabili che estendono le funzionalità di Commerce e si integrano con soluzioni di terze parti.
- [**Eventi**](https://developer.adobe.com/commerce/extensibility/events/)- Utilizza trigger di evento personalizzati per interagire con altri strumenti di sviluppo estensibili.
- [**Webhook**](https://developer.adobe.com/commerce/extensibility/webhooks/): utilizza i webhook per attivare automaticamente le interazioni tra Commerce e i sistemi di terze parti.
- [**SDK interfaccia utente amministratore**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): personalizza e ottimizza l’amministratore di Commerce con nuove pagine e funzioni per i tuoi esercenti.

## Servizi di vetrina

Adobe offre una ricca gamma di servizi di merchandizing intelligenti e componibili per aiutarti a supportare i tuoi obiettivi aziendali chiave. Questi servizi forniscono anche API fondamentali per ottimizzare le prestazioni su larga scala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)- Risultati più intelligenti, rapidi e pertinenti per gli acquirenti grazie a questo strumento di ricerca basato sull&#39;intelligenza artificiale.
- [Recommendations del prodotto](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview): aggiungi consigli basati sull’intelligenza artificiale in base al comportamento degli acquirenti, alle tendenze popolari, alla somiglianza dei prodotti e altro ancora.
- [Servizio catalogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview)—Offrite ai vostri clienti un&#39;esperienza di prodotto ottimizzata migliorando le prestazioni, migliorando la scalabilità e aumentando le conversioni.
- [Servizi di pagamento](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)- Migliora la soddisfazione dei clienti offrendo diversi metodi di pagamento, tra cui rate di pagamento senza interessi e un&#39;unica vista sull&#39;elaborazione dei pagamenti, gli ordini e le fatture.

## Vetrina headless

L’e-commerce headless è l’e-commerce API-first. Adobe Commerce è completamente headless con un’architettura separata che fornisce tutti i servizi e i dati commerce tramite un livello API GraphQL. Questa architettura consente ai team di sviluppare i front-end in modo indipendente dall’applicazione principale, fornendo la flessibilità necessaria per creare e testare rapidamente nuovi punti di contatto con le tecnologie emergenti.

Adobe fornisce una moderna tecnologia di vetrina headless che include gli stessi vantaggi e le stesse funzionalità offerti da [Edge Delivery Services](https://www.aem.live/home) con l’authoring basato su documenti, un’architettura basata sulle prestazioni e una sperimentazione nativa preconfigurata. Sfrutta la scalabilità e le prestazioni di Adobe Commerce [servizi di vetrina](#storefront-services) e la flessibilità e la convenienza di [componenti di rilascio](https://experienceleague.adobe.com/developer/commerce/storefront/) per fornire funzionalità commerce.

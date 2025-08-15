---
title: Architettura di riferimento aziendale
description: Scopri come implementare Adobe Commerce utilizzando la più recente tecnologia di e-commerce componibile di Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Architettura di riferimento aziendale Adobe Commerce

Adobe Commerce è la piattaforma basata sull’esperienza che associa in modo univoco flessibilità tecnica e facilità d’uso, il tutto al servizio della creazione di esperienze eccezionali che producono risultati aziendali.

Commerce si è evoluta per soddisfare i requisiti aziendali in termini di prestazioni, scalabilità e sicurezza. L’adozione di un approccio di implementazione moderno che utilizza le più recenti soluzioni di e-commerce componibili di Adobe è fondamentale per il successo delle aziende. Questa pagina descrive nei dettagli tecnici il moderno approccio di implementazione di Commerce.

Il diagramma seguente illustra il flusso di dati tra Adobe Commerce e tutte le soluzioni Adobe Experience Cloud.

![Diagramma architetturale che mostra il modo in cui Adobe Commerce si connette alle soluzioni Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>I flussi di dati di alto livello mostrati nel diagramma sono coerenti nella maggior parte delle implementazioni aziendali. Il componente chiave che può rendere univoche le implementazioni è il modo in cui crei il catalogo (in particolare per il B2B). Devi mappare attentamente l&#39;architettura del catalogo alle [API Web di Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) è la base dell&#39;implementazione di Commerce. Fornisce una piattaforma di hosting automatizzata [secure](../../security-and-compliance/shared-responsibility.md) con un approccio self-service per la creazione, la distribuzione, il monitoraggio e la gestione dell&#39;applicazione Commerce in un ambiente nativo per il cloud.

Consulta i seguenti dettagli tecnici di cloud foundation:

- [**Architettura scalata**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Capacità regolata automaticamente per mantenere prestazioni stabili e prevedibili
- [**Ambienti multipli**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - È stato eseguito il preprovisioning con PHP, MySQL (MariaDB), Redis, RabbitMQ e tecnologie dei motori di ricerca supportate per sviluppare, testare e distribuire il sito
- [**Gestione della configurazione**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview): file di configurazione dell&#39;ambiente personalizzabili e interfaccia della riga di comando (CLI) per gestire le impostazioni dell&#39;applicazione, le route, le azioni di generazione e distribuzione e le notifiche.
- [**Flusso di lavoro basato su Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): compilazione e distribuzione automatiche dopo il push delle modifiche al codice per lo sviluppo rapido e la distribuzione continua
- [**Osservabilità integrata**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance): strumenti che combinano i dati di registro provenienti da più origini per gestire le prestazioni del sito e diagnosticare i problemi
- [**Copertura API completa**](https://developer.adobe.com/commerce/webapi/get-started/)—[API GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) e [REST](https://developer.adobe.com/commerce/webapi/rest) per l&#39;integrazione dell&#39;applicazione Commerce di base con sistemi di terze parti e l&#39;estensione delle funzionalità di Commerce

## Integrazione con Experience Cloud

Adobe Commerce si integra con tutte le soluzioni Experience Cloud per fornire [esperienze di e-commerce personalizzate su larga scala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Connessione dati](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview) consente di ottenere informazioni sul comportamento d&#39;acquisto dei tuoi acquirenti, in modo da poter creare esperienze d&#39;acquisto personalizzate su tutti i canali con altri prodotti Adobe Digital Experience.

>[!NOTE]
>
>Per ulteriori informazioni, consulta le risorse seguenti:
>
>- [Blueprint per esperienze digitali](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) per ulteriori dettagli tecnici.
>- Consulta [Personalizzazione della customer experience](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integrazione con sistemi di terze parti

Adobe fornisce agli sviluppatori punti di estensione e strumenti completi per creare applicazioni che estendono le funzionalità Commerce di base e integrano Commerce con sistemi di terze parti (come CRM, ERPS e PIMS). Questi strumenti riducono il costo totale di proprietà della piattaforma nei seguenti modi:

- **Scalabilità**: le applicazioni possono essere scalate separatamente dal software principale, consentendo una maggiore efficienza e aggiornamenti semplificati.
- **Isolamento**-Un ambiente isolato significa che gli sviluppatori possono aggiornare o modificare le loro estensioni a loro discrezione senza affidarsi a una versione di base.
- **Indipendenza tecnologica**-Gli sviluppatori possono scegliere qualsiasi tecnologia, stack e linguaggi di codifica che soddisfino le loro esigenze.

Adobe fornisce i seguenti strumenti per sviluppatori per creare integrazioni e personalizzazioni:

- [**Mesh API per Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/): consente di coordinare e combinare più origini API, GraphQL, REST e altre in un unico endpoint GraphQL interrogabile.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): crea e distribuisci applicazioni web sicure e scalabili che estendono le funzionalità di Commerce e si integrano con soluzioni di terze parti.
- [**Eventi**](https://developer.adobe.com/commerce/extensibility/events/)—Utilizza trigger evento personalizzati per interagire con altri strumenti di sviluppo estensibili.
- [**Webhook**](https://developer.adobe.com/commerce/extensibility/webhooks/): utilizza i webhook per attivare automaticamente le interazioni tra Commerce e i sistemi di terze parti.
- [**Interfaccia utente amministratore SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)—Personalizza e ottimizza l&#39;amministratore Commerce con nuove pagine e funzionalità per gli esercenti.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/): accelera le integrazioni di backoffice con integrazioni di riferimento, script di onboarding e architettura standardizzata.

>[!NOTE]
>
>Vedi [L&#39;approccio moderno: estensibilità effettiva in Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Servizi di vetrina

Adobe offre una ricca gamma di servizi di merchandizing intelligenti e componibili per aiutarti a supportare i tuoi obiettivi aziendali chiave. Questi servizi forniscono anche API fondamentali per ottimizzare le prestazioni su larga scala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview) - Fornisci risultati più intelligenti, più veloci e rilevanti per gli acquirenti con questo strumento di ricerca basato sull&#39;intelligenza artificiale.
- [Consigli di prodotto](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview): aggiungi consigli basati sull&#39;intelligenza artificiale in base al comportamento degli acquirenti, alle tendenze popolari, alla somiglianza dei prodotti e altro ancora.
- [Catalog Service](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview) - Offri ai tuoi clienti un&#39;esperienza di prodotto ottimizzata migliorando le prestazioni, la scalabilità e le conversioni.
- [Servizi di pagamento](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview)—Aumenta la soddisfazione dei clienti offrendo diversi metodi di pagamento, incluse le rate di pagamento senza interessi e un&#39;unica vista per l&#39;elaborazione dei pagamenti, gli ordini e le fatture.

## Vetrina headless

L’e-commerce headless è l’e-commerce API-first. Adobe Commerce è completamente headless con un’architettura separata che fornisce tutti i servizi e i dati commerce tramite un livello API GraphQL. Questa architettura consente ai team di sviluppare i front-end in modo indipendente dall’applicazione principale, fornendo la flessibilità necessaria per creare e testare rapidamente nuovi punti di contatto con le tecnologie emergenti.

Adobe fornisce una moderna tecnologia di vetrina headless che include gli stessi vantaggi e le stesse funzionalità offerte da [Edge Delivery Services](https://www.aem.live/home) con authoring basato su documenti, un&#39;architettura basata sulle prestazioni e una sperimentazione nativa preconfigurata. Sfrutta la scalabilità e le prestazioni dei [servizi storefront](#storefront-services) di Adobe Commerce e la flessibilità e la comodità dei [componenti di destinazione](https://experienceleague.adobe.com/developer/commerce/storefront/) per fornire funzionalità di e-commerce.


---
title: Strategia di integrazione Adobe Commerce
description: Esamina le strategie e le opzioni di integrazione per l’implementazione Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Strategia di integrazione Adobe Commerce

La capacità di integrare la piattaforma è &quot;non negoziabile&quot;. Le aziende vogliono che le loro piattaforme di e-commerce siano accessibili da una varietà di punti di contatto e perfettamente integrate nei loro sistemi tecnologici, in particolare nell&#39;ERP. Personalizzazione, scalabilità globale e convenienza giocano un ruolo importante anche nell&#39;acquisto di piattaforme finali.

Un approccio di integrazione olistica sia per i sistemi storefront che per quelli back-end è supportato dalle API GraphQL performanti, dalle API REST complete e dall’importazione di file batch tra Adobe Commerce e altri sistemi o servizi.

L’API GraphQL di Adobe Commerce fornisce una copertura completa per la vetrina che puoi utilizzare per l’integrazione con altri vetrini, tra cui:

- Piattaforme di esperienza digitale (DXP) come Adobe Experience Manager e Bloomreach
- Sistemi di gestione dei contenuti (CMS) come Drupal e WordPress
- Applicazione storefront personalizzata moderna come Adobe Commerce, PWA Studi e Vue Storefront

GraphQL fornisce una risposta efficiente e specifica per il canale, nessun overfetching di dati e una distribuzione agile di nuove funzioni per i punti di contatto. Spesso viene anche scelto di integrarsi con canali di vendita come app native per dispositivi mobili, POS, IoT, canali social e canali di e-commerce livestream come Facebook, Google, Instagram, WeChat e TikTok.

L’API REST di Adobe Commerce fornisce una copertura completa della configurazione del sistema e funzioni di gestione dei dati, inclusi prodotti e catalogo; carrello, preventivo e pagamento; clienti, account e società; e ordini e resi. Le API REST supportano operazioni in blocco, modalità di autenticazione multiple e autorizzazioni granulari, pertanto le API REST vengono spesso scelte per l’integrazione con i sistemi aziendali, tra cui:

- Sistemi ERP (Enterprise Resource Planning) come SAP
- Sistemi di gestione delle informazioni sui prodotti (PIM) come Akeneo
- Sistemi di gestione delle relazioni con i clienti (CRM) come Salesforce
- Sistemi di gestione degli ordini (OMS) come MOM, Manhattan e SAP
- Sistema di gestione del magazzino (WMS) o logistica di terze parti (3PL) come Oracle, NetSuite e SAP WM
- Configura, Prezzo, Preventivo (CPQ) come SalesforceCPQ
- Digital Asset Management (DAM) come Adobe DAM.

Le importazioni di file batch sono anche considerate una buona opzione per integrare sistemi aziendali come ERP e PIM, in quanto tali dati non cambiano molto spesso e spesso si hanno prestazioni migliori con le importazioni di file programmate. Pertanto, le importazioni di file batch vengono solitamente selezionate per la sincronizzazione dati in blocco su base giornaliera/settimanale e per le sincronizzazioni complete dei dati mensili, mentre le API REST vengono scelte per la sincronizzazione incrementale dei cambiamenti dei dati, per prestazioni migliori. Anche questo è considerato solo un lavoro pianificato ma può essere fatto frequentemente, potenzialmente ogni 15 minuti a 1 ora, a seconda delle esigenze aziendali.

## Opzioni di integrazione

Adobe Commerce offre tre opzioni di integrazione flessibili:

- Integrazione diretta tra sistemi con connettori predefiniti. Alcuni sistemi potrebbero già disporre di estensioni Adobe Commerce su Adobe Commerce Marketplace o sul proprio sito web.

- Integrazione da sistema a sistema tramite middleware personalizzato. La soluzione middleware personalizzata distribuita verrà utilizzata per la mappatura, la traduzione e la gestione dei dati del processo.

- Integrazione tra sistemi tramite iPaaS (Integration Platform-as-a-Service), denominata anche EAI (Enterprise Application Integration Platform), come Mulesoft, Boomi e Software AG.

![Opzioni di integrazione di Adobe Commerce](../../assets/playbooks/integration-options.svg)

Anche se di solito sono desiderate integrazioni in tempo reale, non è necessario in alcuni scenari. Adobe Commerce supporta in modo nativo RabbitMQ come bus dei messaggi per abilitare i processi asincroni, il che è consigliato per alcuni dati che non sono necessari per lo scambio in tempo reale, ma piuttosto per l’aggiornamento con l’API di processo di scambio di file batch o di dati batch REST in modo che vengano elaborati in modo asincrono.

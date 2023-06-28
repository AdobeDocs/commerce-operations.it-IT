---
title: Strategia di integrazione di Adobe Commerce
description: Rivedi le strategie e le opzioni di integrazione per l’implementazione di Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Strategia di integrazione di Adobe Commerce

La capacità di integrare la piattaforma è &quot;non negoziabile&quot;. Le aziende vogliono che le loro piattaforme di e-commerce siano accessibili da una varietà di punti di contatto e perfettamente integrate nei loro sistemi tecnologici, in particolare nel loro ERP. Personalizzazione, scalabilità globale e convenienza hanno un ruolo importante anche nell&#39;acquisto finale della piattaforma.

Un approccio olistico all’integrazione sia per i sistemi storefront che per quelli back-end è supportato da API GraphQL performanti, API REST complete e importazione di file batch tra Adobe Commerce e altri sistemi o servizi.

L’API GraphQL di Adobe Commerce fornisce una copertura completa della vetrina che puoi utilizzare per l’integrazione con altre vetrine, tra cui:

- Piattaforme di esperienza digitale (DXP) come Adobe Experience Manager e Bloomreach
- Sistemi di gestione dei contenuti (CMS) come Drupal e WordPress
- Moderna applicazione di vetrina personalizzata come Adobe Commerce, PWA Studi e Vue Storefront

GraphQL fornisce una risposta efficiente e specifica per il canale, nessun recupero eccessivo dei dati e una distribuzione agile di nuove funzioni per i punti di contatto. Viene spesso scelto per integrarsi con canali di vendita come app native per dispositivi mobili, POS, IoT, canali social e canali commerciali in diretta come Facebook, Google, Instagram, WeChat e TikTok.

L’API REST di Adobe Commerce fornisce copertura completa della configurazione del sistema e funzioni di gestione dei dati, tra cui prodotti e cataloghi, carrello, preventivi e pagamento, clienti, account e aziende, ordini e restituzioni. Le API REST supportano operazioni in blocco, più modalità di autenticazione e autorizzazioni granulari, pertanto le API REST vengono spesso scelte per l’integrazione con i sistemi aziendali, tra cui:

- Sistemi ERP (Enterprise Resource Planning) come SAP
- Sistemi di gestione delle informazioni sui prodotti (PIM) come Akeneo
- Sistemi di gestione delle relazioni con i clienti (CRM) come Salesforce
- Sistemi di gestione degli ordini (OMS) come MOM, Manhattan e SAP
- WMS (Warehouse Management System) o logistica di terze parti (3PL) come Oracle, NetSuite e SAP WM
- Configurazione, prezzo, preventivo (CPQ) come SalesforceCPQ
- Digital Asset Management (DAM) come Adobe DAM.

Anche le importazioni di file batch sono considerate una buona opzione per integrare sistemi aziendali come ERP e PIM, in quanto tali dati non cambiano molto spesso e spesso si hanno prestazioni migliori con le importazioni di file pianificate. Pertanto, le importazioni di file batch vengono solitamente scelte per la sincronizzazione di dati in blocco su base giornaliera/settimanale e per le sincronizzazioni di dati complete mensili, mentre le API REST vengono scelte per la sincronizzazione incrementale delle modifiche ai dati, per prestazioni migliori. Anche questo viene considerato solo un lavoro pianificato, ma può essere svolto frequentemente, potenzialmente ogni 15 minuti o 1 ora, a seconda delle esigenze aziendali.

## Opzioni di integrazione

Adobe Commerce offre tre opzioni di integrazione flessibili:

- Integrazione diretta tra sistemi con connettori predefiniti. Alcuni sistemi possono già disporre di estensioni Adobe Commerce su Adobe Commerce Marketplace o sul proprio sito web.

- Integrazione tra sistemi tramite middleware personalizzato. La soluzione middleware personalizzata implementata verrà utilizzata per la mappatura, la traduzione e la gestione dei dati di processo.

- Integrazione tra sistemi tramite iPaaS (Integration Platform-as-a-Service), nota anche come EAI (Enterprise Application Integration Platform), come Mulesoft, Boomi e Software AG.

![Opzioni di integrazione di Adobe Commerce](../../assets/playbooks/integration-options.svg)

Anche se in genere si desiderano integrazioni in tempo reale, per alcuni scenari non è necessario. Supporto nativo di Adobe Commerce [!DNL RabbitMQ] come bus di messaggio per abilitare i processi asincroni, consigliato per alcuni dati che non sono necessari per lo scambio in tempo reale, ma che vengono aggiornati con lo scambio di file batch o con l’API di elaborazione di dati batch REST per l’elaborazione asincrona.

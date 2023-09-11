---
title: Strategia di estensibilità di Adobe Commerce
description: Scopri come il modello di estensibilità di Adobe Commerce ti consente di personalizzare la tua implementazione.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Strategia di estensibilità

La piattaforma di estensibilità di Adobe Commerce consente ai brand di personalizzare in modo efficiente i processi, integrare i sistemi e implementare nuove funzionalità, mantenendo al contempo la possibilità di aggiornamento.

## Panoramica delle strategie di estensione di Commerce

L’estensione delle funzionalità della piattaforma Commerce include i seguenti approcci di alto livello:

* Estensione delle funzionalità native della piattaforma Commerce. Ad esempio, i commercianti possono installare applicazioni Marketplace (spesso create da terze parti) che estendono e perfezionano le funzionalità native della piattaforma, ad esempio un&#39;estensione che può convalidare gli indirizzi di spedizione durante il pagamento e facilitare una rapida integrazione con le API degli indirizzi dei gestori UPS.

* Integrazione di app/estensioni di terze parti con la piattaforma Commerce. Gli sviluppatori possono utilizzare le API REST e GraphQL esistenti e complete di Commerce per integrare direttamente Commerce con soluzioni di terze parti.

Tuttavia, l’architettura della piattaforma determina le strategie migliori per estendere una piattaforma. Commerce fornisce una copertura GQL avanzata e REST API per la distribuzione headless. La base di codice di Commerce di base continua a evolversi verso un’architettura più modulare e un singolo livello di integrazione, che fornisce nuovi e migliorati strumenti di personalizzazione:

* [App Builder per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) è un framework di sviluppo e un set di strumenti basati sull’infrastruttura Adobe. Gli sviluppatori possono utilizzarlo per creare estensioni Commerce che vanno dalle personalizzazioni dell’esperienza utente/vetrina alle estensioni middleware e della logica di business.

* [Mesh API per Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) consente agli sviluppatori di combinare più origini dati in un singolo endpoint API. Questo supporta l’orchestrazione o l’integrazione API di API private e di terze parti e altre interfacce software con le API di Adobe Commerce e altri prodotti Adobe tramite Adobe I/O.

* [Eventi di Adobe I/O per Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) rende disponibili i dati transazionali per le applicazioni sviluppate con App Builder e hook web di terze parti, supportando la creazione di applicazioni guidate da eventi.

Questi strumenti consentono di accedere alla console Adobe Developer e agli strumenti per sviluppatori Adobe per creare API e integrare plug-in e integrazioni personalizzati.

Il diagramma seguente evidenzia i componenti principali della strategia di flessibilità di Commerce.

![Diagramma della strategia di estensibilità di Adobe Commerce](../../assets/playbooks/extensibility-strategy-overview.png)

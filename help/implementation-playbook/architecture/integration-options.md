---
title: Opzioni di integrazione di Adobe Commerce
description: Esplora le opzioni per l’integrazione di altri sistemi con l’implementazione di Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Punti di integrazione e flussi di dati tipici

Esistono due approcci principali alle integrazioni e ai flussi di dati, che sono molto simili, ma presentano una differenza chiave.

## Monolitico

Il diagramma seguente descrive un approccio monolitico che utilizza Adobe Commerce sia come sistema back-end che come applicazione storefront:

![Diagramma monolitico di Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Headless

Il diagramma seguente descrive un approccio headless che utilizza Adobe Commerce come sistema back-end integrato con un’applicazione DXP/CMS/personalizzata come applicazione storefront:

![Diagramma Adobe Commerce headless](../../assets/playbooks/integration-headless.svg)

L’unica differenza tra l’approccio monolitico e headless è l’integrazione in vetrina, che influisce sull’esperienza utente dei clienti. Monolithic utilizza la vetrina Adobe Commerce direttamente per l’integrazione con i servizi di terze parti, mentre headless dipende dalla propria vetrina per personalizzare e integrare con gli stessi servizi. Alcuni servizi, come pagamento e Single Sign-On (SSO), richiedono la personalizzazione sia della vetrina che di Adobe Commerce per finalizzare il flusso di integrazione.

## Sistemi di terze parti

Alcuni servizi popolari dispongono già di estensioni eccezionali per supportare Adobe Commerce o soluzioni di vetrina popolari, come PWA Studi, Adobe Experience Manager e Vue Storefront, reperibili dal marketplace delle estensioni o da siti web di terze parti correlati. Anche se non esiste un’estensione, lo sforzo per implementare l’integrazione tra Adobe Commerce e altre vetrine headless è simile. Tutti i servizi di terze parti in genere dispongono di documenti che spiegano come integrarsi con essi. Questi servizi sono solo alcuni esempi; vari paesi e mercati possono avere scelte diverse.

## Integrazioni Enterprise

Per le integrazioni di sistemi aziendali, solitamente denominate anche integrazioni back-end, si verifica un impatto sul flusso di dati aziendali. In base a esigenze e tipi di business diversi, può utilizzare tre diverse opzioni di integrazione, che abbiamo già introdotto.

I dati obbligatori per il prodotto come SKU, inventario e prezzi di base di solito provengono dagli ERP, mentre i prezzi di vendita sono solitamente gestiti da ciascun canale di vendita (ad esempio, Adobe Commerce) o CPQ (B2B o vendite private). Poiché i dati obbligatori per il prodotto (ad eccezione dell’inventario) non cambiano molto spesso, è consigliabile utilizzare gli aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco dei file. Per l’inventario, la best practice prevede un aggiornamento completo su base giornaliera per l’inventario dei prodotti condiviso con canali di vendita diversi, in modo da evitare vendite eccessive. Inoltre, sono state pianificate modifiche incrementali da ERP entro 24 ore.

Il catalogo dei prodotti, i metadati e i contenuti di marketing possono essere gestiti separatamente da ciascun canale di vendita (ad esempio, Adobe Commerce) o da un PIM centrale. Poiché anche i metadati non vengono modificati frequentemente, è consigliabile utilizzare gli aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco dei file.

I dati dell&#39;ordine includono i dati relativi a ordini, preventivi (B2B), spedizioni, restituzioni e scambi che vengono in genere gestiti da un sistema OMS e WMS centralizzato. I dati dell’ordine devono essere sincronizzati il prima possibile, pertanto l’API REST è in genere l’opzione migliore. Per prestazioni migliori, valuta la possibilità di ridurre il numero di chiamate API. Per lo stato dell’ordine, le spedizioni, la restituzione e lo scambio dei dati, è consigliabile pianificare le API di aggiornamento batch REST in ore o minuti.

I dati B2B sono solitamente gestiti da un sistema CRM centralizzato. Viene utilizzata un’API in tempo reale per verificare i clienti esistenti e crearne di nuovi. Per il B2B, potrebbe essere necessario introdurre più API per sincronizzare diversi dipendenti, gruppi e listini prezzi aziendali tra Adobe Commerce e il CRM o CPQ.

Esistono altre integrazioni di sistema, come eDM per l’e-mail marketing e business intelligence per l’analisi dei dati aziendali, che in genere vengono eseguite tramite API REST o tramite esportazione/importazione di file, solitamente supportate dalle estensioni esistenti.

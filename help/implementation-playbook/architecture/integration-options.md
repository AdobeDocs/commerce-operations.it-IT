---
title: Opzioni di integrazione di Adobe Commerce
description: Esplora le opzioni per l’integrazione di altri sistemi con l’implementazione Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Punti di integrazione e flussi di dati tipici

Esistono due approcci principali alle integrazioni e ai flussi di dati, molto simili ma con una differenza chiave.

## Monolitico

Il diagramma seguente descrive un approccio monolitico che utilizza Adobe Commerce sia come sistema back-end che come applicazione storefront:

![Diagramma monolitico di Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Senza testa

Il diagramma seguente descrive un approccio headless che utilizza Adobe Commerce come sistema back-end integrato con un&#39;applicazione DXP/CMS/personalizzata come applicazione storefront:

![Diagramma headless di Adobe Commerce](../../assets/playbooks/integration-headless.svg)

L’unica differenza tra l’approccio monolitico e headless è l’integrazione con la vetrina, che influisce sull’esperienza utente per i clienti. Monolitico utilizza la vetrina Adobe Commerce direttamente per integrarsi con servizi di terze parti, mentre headless dipende dalla propria vetrina per personalizzare e integrare con gli stessi servizi. Per completare il flusso di integrazione, alcuni servizi come il pagamento e il single sign-on (SSO) necessitano sia della vetrina che della personalizzazione Adobe Commerce.

## Sistemi di terze parti

Alcuni servizi popolari dispongono già di ottime estensioni per supportare Adobe Commerce o soluzioni popolari per la vetrina, come PWA Studi, Adobe Experience Manager e Vue Storefront, che possono essere trovate dal loro marketplace di estensioni o da siti web di terze parti correlati. Anche se non esiste un&#39;estensione esistente, lo sforzo di implementare l&#39;integrazione tra Adobe Commerce e altri vetrini headless è simile. Tutti i servizi di terze parti di solito hanno documenti che spiegano come integrarsi con loro. Questi servizi sono solo alcuni esempi; vari paesi e mercati possono avere scelte diverse.

## Integrazioni aziendali

Per le integrazioni di sistemi aziendali, che sono solitamente chiamate integrazioni back-end, c&#39;è un impatto sul flusso di dati aziendali. In base a diversi tipi di business e esigenze, può utilizzare tre diverse opzioni di integrazione, che abbiamo già introdotto.

I dati obbligatori sul prodotto come SKU, inventario e prezzi base provengono solitamente da ERP, mentre i prezzi di vendita sono solitamente gestiti da ciascun canale di vendita (ad esempio, Adobe Commerce) o CPQ (B2B o vendite private). Poiché i dati obbligatori del prodotto (ad eccezione dell’inventario) non cambiano molto spesso, la best practice consiste nell’utilizzare aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco di file. Per l’inventario, è consigliabile disporre di un aggiornamento completo su base giornaliera per l’inventario dei prodotti condiviso con diversi canali di vendita al fine di evitare le vendite eccessive. Inoltre, puoi impostare le modifiche incrementali rispetto all’ERP programmate entro 24 ore.

I cataloghi di prodotti, i metadati e i contenuti di marketing possono essere gestiti separatamente da ciascun canale di vendita (ad esempio, Adobe Commerce) o da un sistema PIM centrale. Poiché anche i metadati non vengono modificati frequentemente, la best practice consiste nell’utilizzare aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco di file.

I dati dell&#39;ordine includono i dati relativi all&#39;ordine, al preventivo (B2B), alla spedizione, alla restituzione e allo scambio, solitamente gestiti da un sistema OMS e WMS centralizzato. I dati dell’ordine devono essere sincronizzati il prima possibile, quindi l’API REST di solito è l’opzione migliore. Per prestazioni migliori, considera la riduzione del numero di chiamate API. Per lo stato dell’ordine, le spedizioni, la restituzione e lo scambio dei dati, è consigliabile pianificare le API di aggiornamento batch REST in ore o minuti.

I dati B2B sono solitamente gestiti da un sistema di gestione delle relazioni con i clienti centralizzato. Viene utilizzata un’API in tempo reale per verificare i clienti esistenti e creare nuovi clienti. Per B2B, potrebbe essere necessario introdurre più API per sincronizzare diversi dipendenti aziendali, gruppi e listino prezzi tra Adobe Commerce e il CRM o CPQ.

Esistono altre integrazioni di sistema come eDM per l’e-mail marketing e le informazioni aziendali per l’analisi dei dati aziendali, che di solito vengono eseguite tramite API REST o tramite esportazione/importazione di file, che solitamente sono supportate dalle estensioni esistenti.

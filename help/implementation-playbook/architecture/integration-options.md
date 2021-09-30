---
title: Opzioni di integrazione di Adobe Commerce
description: Esplora le opzioni per l’integrazione di altri sistemi con l’implementazione Commerce di Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Punti di integrazione e flussi di dati tipici

Esistono due approcci principali alle integrazioni e ai flussi di dati, molto simili ma con una differenza chiave.

## Monolithic

Il diagramma seguente descrive un approccio monolitico che utilizza Commerce di Adobe sia come sistema back-end che come applicazione storefront:

![Diagramma del monolite di Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Senza testa

The following diagram describes a headless approach that uses Adobe Commerce as the backend systenm integrated with a DXP/CMS/custom application as the storefront application:

![Diagramma headless di Adobe Commerce](../../assets/playbooks/integration-headless.svg)

L’unica differenza tra l’approccio monolitico e headless è l’integrazione con la vetrina, che influisce sull’esperienza utente per i clienti. Monolithic uses Adobe Commerce storefront directly to integrate with third-party services, while headless depends on its own storefront to customize and integrate with the same services. Alcuni servizi come il pagamento e il single sign-on (SSO) hanno bisogno sia di storefront che di personalizzazione di Adobe Commerce per completare il flusso di integrazione.

## Sistemi di terze parti

Alcuni servizi popolari dispongono già di ottime estensioni per supportare Adobe Commerce o soluzioni di vetrina popolari, come PWA Studi, Adobe Experience Manager e Vue Storefront, che possono essere trovate dal loro marketplace di estensioni o da siti web di terze parti correlati. Anche se non esiste un&#39;estensione esistente, lo sforzo di implementare l&#39;integrazione tra Adobe Commerce e altri vetrine headless è simile. Tutti i servizi di terze parti di solito hanno documenti che spiegano come integrarsi con loro. Questi servizi sono solo alcuni esempi; vari paesi e mercati possono avere scelte diverse.

## Enterprise integrations

Per le integrazioni di sistemi aziendali, che sono solitamente chiamate integrazioni back-end, c&#39;è un impatto sul flusso di dati aziendali. Based on different business type and needs, it can use three different integration options, which we already introduced.

I dati obbligatori sul prodotto come SKU, inventario e prezzi base provengono solitamente da ERP, mentre i prezzi di vendita sono solitamente gestiti da ciascun canale di vendita (ad esempio, Adobe Commerce) o CPQ (B2B o vendite private). Poiché i dati obbligatori del prodotto (ad eccezione dell’inventario) non cambiano molto spesso, la best practice consiste nell’utilizzare aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco di file. Per l’inventario, è consigliabile disporre di un aggiornamento completo su base giornaliera per l’inventario dei prodotti condiviso con diversi canali di vendita al fine di evitare le vendite eccessive. Inoltre, puoi impostare le modifiche incrementali rispetto all’ERP programmate entro 24 ore.

I cataloghi di prodotti, i metadati e i contenuti di marketing possono essere gestiti separatamente da ciascun canale di vendita (ad esempio, Adobe Commerce) o da un sistema PIM centrale. Poiché anche i metadati non vengono modificati frequentemente, la best practice consiste nell’utilizzare aggiornamenti batch pianificati tramite l’API REST o l’importazione in blocco di file.

I dati dell&#39;ordine includono i dati relativi all&#39;ordine, al preventivo (B2B), alla spedizione, alla restituzione e allo scambio, solitamente gestiti da un sistema OMS e WMS centralizzato. I dati dell’ordine devono essere sincronizzati il prima possibile, quindi l’API REST di solito è l’opzione migliore. Per prestazioni migliori, considera la riduzione del numero di chiamate API. For the order status, shipments, return, and exchange data, consider scheduling REST batch update APIs in hours or minutes.

I dati B2B sono solitamente gestiti da un sistema di gestione delle relazioni con i clienti centralizzato. Viene utilizzata un’API in tempo reale per verificare i clienti esistenti e creare nuovi clienti. Per B2B, potrebbe essere necessario introdurre più API per sincronizzare diversi dipendenti aziendali, gruppi e listini prezzi tra Adobe Commerce e il tuo CRM o CPQ.

Esistono altre integrazioni di sistema come eDM per l’e-mail marketing e le informazioni aziendali per l’analisi dei dati aziendali, che di solito vengono eseguite tramite API REST o tramite esportazione/importazione di file, che solitamente sono supportate dalle estensioni esistenti.

---
title: Panoramica dell’hosting autonomo
description: Scopri le best practice per l’hosting autonomo da considerare. Gli argomenti trattati spaziano dagli elementi di sicurezza al disaster recovery e molto altro ancora. Questi argomenti sono destinati ad assistere le aziende che hanno deciso di ospitare la propria versione di Adobe Commerce. Gli elementi presentati non sono tutti inclusivi, ma dovrebbero fornire una buona gamma di concetti per promuovere un sito web sicuro, stabile e resiliente.
landing-page-description: Scopri alcuni concetti e cose da considerare quando ospiti Adobe Commerce da solo.
short-description: Scopri le strategie e i concetti per ospitare te stesso Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Panoramica di Adobe Commerce con hosting autonomo

Quando prendi in considerazione il passaggio a una piattaforma di e-commerce come Adobe Commerce, hai il lusso di opzioni. Tuttavia, con queste opzioni ci sono costi aggiuntivi, rischi e passività da considerare. L’hosting di un sito Commerce può essere eseguito utilizzando una soluzione completa, ad esempio [Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}: infrastruttura, server, e-mail, certificati SSL e molto altro ancora sono preconfigurati e pronti per l’uso. Trovare una buona soluzione di hosting come Adobe Commerce su infrastruttura cloud semplifica l’intero processo, ci sono motivi convincenti per ospitare autonomamente il tuo sito Commerce. All’interno delle pagine di accompagnamento, sono presenti molti argomenti che forniscono informazioni approfondite e indicazioni sui servizi, le tecniche e i concetti offerti dall’hosting autonomo. Le informazioni qui riportate non sono esaustive e non è previsto che tu debba implementare ogni suggerimento. Tuttavia, questi articoli possono aiutarti a comprendere le idee e i concetti che possono rendere l’hosting autonomo di Adobe Commerce il più stabile e sicuro possibile.

Quando non utilizzi Adobe Commerce su un’infrastruttura cloud, i termini utilizzati sono self-hosting o on-premise, oppure on-premise. On-premise non significa solo in un centro dati in un edificio di proprietà di un&#39;azienda. Questo termine rappresenta tutto ciò che non è supportato da Adobe Commerce nell’infrastruttura. Esistono società di hosting che gestiscono Adobe Commerce, ma sono anche considerate come self-hosting o on-premise.

Per quanto riguarda Adobe Commerce e Magento Open-source, la maggior parte dei consigli e dei suggerimenti forniti funziona per entrambe le versioni. Anche se non lo afferma direttamente, l’aspettativa è che sia applicabile a entrambi. In questo argomento sulle opzioni di hosting autonomo per Adobe Commerce, vengono considerate entrambe le versioni. Infine, la maggior parte degli argomenti riguarda [Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} viene selezionato come provider di hosting.

## Livello terminologico impostato

I termini seguenti vengono comunemente utilizzati in tutti gli Experienci League, quando si parla con il team DevOps e si lavora con il supporto aziendale:

* **DevOps** è un termine utilizzato per descrivere i team che gestiscono la configurazione, la gestione, i certificati SSL e tutto il resto relativo ai server e ai servizi effettivi utilizzati per eseguire un sito Adobe Commerce. Questo termine viene utilizzato per indicare quando in genere termina la responsabilità di uno sviluppatore e dove iniziano la valutazione e il supporto da parte di un team di infrastruttura.

* **Concetti di sicurezza** include diversi argomenti e considerazioni per creare la base di codice, i file e il file system di Adobe Commerce sui server e tutte le configurazioni o gli aggiornamenti che riducono la superficie di attacco per molti pattern di exploit noti.

* **Strumenti di monitoraggio** tratta alcuni strumenti e servizi esistenti che monitorano i siti web di Adobe Commerce. Questi strumenti possono a volte fornire suggerimenti su come migliorare le cose, o scoprire problemi e vulnerabilità di sicurezza.

* **Disaster recovery** aiuta a fornire alcuni concetti e considerazioni per l&#39;evento sfortunato di un progetto danneggiato o sfruttato.

* **Suggerimenti sulle prestazioni** fornisci alcuni suggerimenti e indicazioni pro per rendere l’applicazione Adobe Commerce più performante possibile.

* **Attore non valido** è il termine utilizzato per indicare una persona o un team che sta tentando di fare qualcosa di dannoso o non autorizzato. Non si limita all’applicazione commerce, ma si estende anche all’infrastruttura o a qualsiasi componente correlato al sito web.

* **Firewall applicazione Web** (WAF) aiuta guardando ogni intestazione di richiesta nell’applicazione commerce e blocca i pattern e gli exploit noti. Spesso viene utilizzato un WAF insieme a filtri e regole personalizzati per aiutare a gestire gli attacchi DDOS.

* **Denial of Service distribuito** (DDoS) è un metodo di attacco per forzare i server che eseguono il sito web ad essere utilizzati con richieste false con un volume sufficiente da non poter più rispondere a richieste legittime.

## Quali sono le prossime novità?

Questi argomenti non sono in alcun ordine o sequenza speciale. Hanno lo scopo di fornire punti di contatto con un ingegnere DevOps, con l’architetto Commerce e con chiunque sia coinvolto in questa importante decisione su dove e come ospitare Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}

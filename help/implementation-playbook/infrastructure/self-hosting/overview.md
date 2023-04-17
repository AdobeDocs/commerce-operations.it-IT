---
title: Panoramica sull’hosting autonomo
description: Scopri le best practice di hosting autonomo da considerare. Gli argomenti spaziano dagli elementi di sicurezza, al disaster recovery molti altri. Questi argomenti sono qui per assistere un’azienda che ha deciso di ospitare la propria versione di Adobe Commerce. Gli articoli presentati non sono tutti inclusivi ma dovrebbero fornire una buona gamma di concetti per promuovere un sito web sicuro, stabile e resiliente.
landing-page-description: Scopri alcuni concetti e cose da considerare durante l’hosting di Adobe Commerce da solo.
short-description: Scopri strategie e concetti per l’hosting autonomo di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# Panoramica sull’hosting autonomo di Adobe Commerce

Quando consideri il passaggio a una piattaforma di e-commerce come Adobe Commerce, hai il lusso di opzioni. Tuttavia, con queste opzioni ci sono costi, rischi e passività aggiuntivi da considerare. L’hosting di un sito Commerce può essere eseguito utilizzando una soluzione in pacchetto, ad esempio [Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, in cui l’infrastruttura, i server, l’e-mail, i certificati SSL e molto altro sono preconfigurati e pronti per l’uso. Trovare una buona soluzione di hosting come Adobe Commerce su un’infrastruttura cloud semplifica l’intero processo, ci sono motivi impellenti per l’hosting autonomo del tuo sito Commerce. All’interno delle pagine di accompagnamento, sono presenti molti argomenti che forniscono informazioni e indicazioni sui servizi, le tecniche e i concetti forniti dall’hosting autonomo. Le informazioni qui non sono esaustive e non ci si aspetta che tu implementi ogni suggerimento. Tuttavia, questi articoli possono aiutarti a comprendere le idee e i concetti che possono rendere l&#39;hosting autonomo Adobe Commerce il più stabile e sicuro possibile.

Quando non utilizzi l’infrastruttura cloud di Adobe Commerce, vengono utilizzati i termini self-hosting, on-premise o anche on-prem. Non si intende solo in un centro dati di un edificio di proprietà di un&#39;azienda. Questo termine rappresenta tutto ciò che non viene gestito dal supporto di Adobe Commerce sulla propria infrastruttura. Ci sono aziende di hosting che si occupano di Adobe Commerce, sono anche considerate come self-hosting o on-prem.

Per quanto riguarda Adobe Commerce e Magento Open-source, la maggior parte dei consigli e dei suggerimenti forniti funziona per entrambe le versioni. Anche se non lo afferma direttamente, ci si aspetta che sia applicabile per entrambi. In questo argomento delle opzioni di hosting autonomo per Adobe Commerce, vengono considerate entrambe le versioni. Infine, la maggior parte dei temi sono rilevanti per [Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} è selezionato come provider di hosting.

## Livello terminologico impostato

I seguenti termini vengono comunemente utilizzati in tutti gli articoli di Experience League, quando si parla con il team DevOps e si lavora con il supporto aziendale:

* **DevOps** è un termine utilizzato per descrivere i team che gestiscono la configurazione del server, la configurazione, la gestione, i certificati SSL e tutto il resto sui server e i servizi effettivi utilizzati per eseguire un sito Adobe Commerce. Questo termine viene utilizzato per aiutare a definire quando le responsabilità degli sviluppatori generalmente terminano e dove inizia la fase di valutazione e il supporto di un team di infrastruttura.

* **Concetti di sicurezza** Includere diversi argomenti e considerazioni per rendere la base di codice, i file e il file system di Adobe Commerce sui server e qualsiasi configurazione o aggiornamento che riducono la superficie di attacco per molti pattern di exploit noti.

* **Strumenti di monitoraggio** copre alcuni strumenti e servizi esistenti che monitorano i siti web Adobe Commerce. A volte questi strumenti possono fornire suggerimenti su come migliorare le cose, o scoprire problemi e vulnerabilità di sicurezza.

* **Ripristino di emergenza** aiuta a fornire alcuni concetti e considerazioni per lo sfortunato evento di un progetto danneggiato o sfruttato.

* **Suggerimenti sulle prestazioni** fornisce alcuni suggerimenti e indicazioni professionali per rendere l&#39;applicazione Adobe Commerce il più performante possibile.

* **Attore cattivo** è il termine utilizzato per una persona o un team che sta cercando di fare qualcosa di maligno o non autorizzato. Non si limita all&#39;applicazione commerce, ma si estende anche all&#39;infrastruttura o a qualsiasi componente correlato al sito web.

* **Firewall applicazione Web** (WAF) aiuta guardando ogni richiesta indirizzata all&#39;applicazione commerce e blocca i pattern e gli utilizzi noti. Spesso un WAF viene utilizzato insieme a filtri e regole personalizzati per aiutare a gestire gli attacchi DDOS.

* **Denial of Service distribuito** (DDoS) è un metodo di attacco per forzare i server che eseguono il sito web a essere consumati con richieste false con un volume sufficiente a non poter più rispondere a richieste legittime.

## Cosa succede dopo?

Questi argomenti non sono in alcun ordine o sequenza speciale. Hanno lo scopo di fornire punti di discussione con un ingegnere DevOps, l’architetto Commerce e chiunque altro sia coinvolto nel prendere questa importante decisione su dove e come ospitare Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}

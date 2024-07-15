---
title: Panoramica dell’hosting autonomo
description: Scopri le best practice per l’hosting autonomo da considerare. Gli argomenti trattati spaziano dagli elementi di sicurezza al disaster recovery e molto altro ancora. Questi argomenti sono destinati ad assistere le aziende che hanno deciso di ospitare la propria versione di Adobe Commerce. Gli elementi presentati non sono tutti inclusivi, ma dovrebbero fornire una buona gamma di concetti per promuovere un sito web sicuro, stabile e resiliente.
landing-page-description: Scopri alcuni concetti e cose da considerare quando ospiti Adobe Commerce da solo.
short-description: Scopri le strategie e i concetti per ospitare te stesso Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Panoramica di Adobe Commerce per hosting autonomo

Quando prendi in considerazione il passaggio a una piattaforma di e-commerce come Adobe Commerce, hai il lusso di opzioni. Tuttavia, con queste opzioni ci sono costi aggiuntivi, rischi e passività da considerare. L&#39;hosting di un sito Commerce può essere eseguito utilizzando una soluzione in pacchetto, ad esempio [Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, in cui l&#39;infrastruttura, i server, l&#39;e-mail, i certificati SSL e molti altri sono preconfigurati e pronti per l&#39;uso. Trovare una buona soluzione di hosting come Adobe Commerce su infrastruttura cloud semplifica l’intero processo, ci sono motivi convincenti per l’hosting autonomo sul tuo sito Commerce. All’interno delle pagine di accompagnamento, sono presenti molti argomenti che forniscono informazioni approfondite e indicazioni sui servizi, le tecniche e i concetti offerti dall’hosting autonomo. Le informazioni qui riportate non sono esaustive e non è previsto che tu debba implementare ogni suggerimento. Tuttavia, questi articoli possono aiutarti a comprendere le idee e i concetti che possono rendere l’hosting autonomo di Adobe Commerce il più stabile e sicuro possibile.

Quando non utilizzi Adobe Commerce su un’infrastruttura cloud, i termini utilizzati sono self-hosting o on-premise, oppure on-premise. On-premise non significa solo in un centro dati in un edificio di proprietà di un&#39;azienda. Questo termine rappresenta tutto ciò che non è supportato da Adobe Commerce nell’infrastruttura. Esistono società di hosting che gestiscono Adobe Commerce, ma sono anche considerate come self-hosting o on-premise.

Per quanto riguarda Adobe Commerce e Magento Open-source, la maggior parte dei consigli e dei suggerimenti forniti funziona per entrambe le versioni. Anche se non lo afferma direttamente, l’aspettativa è che sia applicabile a entrambi. In questo argomento sulle opzioni di hosting autonomo per Adobe Commerce, vengono considerate entrambe le versioni. Infine, la maggior parte degli argomenti è pertinente per [Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} selezionato come provider di hosting.

## Livello terminologico impostato

I termini seguenti vengono comunemente utilizzati in tutti gli Experienci League, quando si parla con il team DevOps e si lavora con il supporto aziendale:

* **DevOps** è un termine utilizzato per descrivere i team che gestiscono la configurazione, la gestione, i certificati SSL e tutto il resto relativo ai server e ai servizi utilizzati per eseguire un sito Adobe Commerce. Questo termine viene utilizzato per indicare quando in genere termina la responsabilità di uno sviluppatore e dove iniziano la valutazione e il supporto da parte di un team di infrastruttura.

* **Concetti sulla sicurezza** includono diversi argomenti e considerazioni per rendere Adobe Commerce codebase, file e file system sui server e qualsiasi configurazione o aggiornamento che riduca la superficie di attacco per molti pattern di exploit noti.

* **Strumenti di monitoraggio** include alcuni strumenti e servizi esistenti che monitorano i siti Web di Adobe Commerce. Questi strumenti possono a volte fornire suggerimenti su come migliorare le cose, o scoprire problemi e vulnerabilità di sicurezza.

* **Disaster Recovery** consente di fornire alcuni concetti e considerazioni per l&#39;evento negativo di un progetto danneggiato o sfruttato.

* **Suggerimenti sulle prestazioni** fornisci alcuni suggerimenti e indicazioni utili per rendere l&#39;applicazione Adobe Commerce il più performante possibile.

* **Attore non valido** è il termine utilizzato per indicare una persona o un team che sta tentando di eseguire un&#39;operazione dannosa o non autorizzata. Non si limita all’applicazione commerce, ma si estende anche all’infrastruttura o a qualsiasi componente correlato al sito web.

* **Web Application Firewall** (WAF) aiuta guardando ogni intestazione di richiesta nell&#39;applicazione commerce e blocca i pattern e gli exploit noti. Spesso viene utilizzato un WAF insieme a filtri e regole personalizzati per aiutare a gestire gli attacchi DDOS.

* **Distributed Denial of Service** (DDoS) è un metodo di attacco per forzare i server che eseguono il sito Web a essere utilizzati con richieste false con un volume sufficiente da non poter più rispondere a richieste legittime.

## Quali sono le prossime novità?

Questi argomenti non sono in alcun ordine o sequenza speciale. Hanno lo scopo di fornire punti di contatto con un ingegnere DevOps, con l’architetto Commerce e con chiunque sia coinvolto in questa importante decisione su dove e come ospitare Adobe Commerce.

{{$include /help/_includes/hosting-related-links.md}}

---
title: Versioni beta
description: Scopri le versioni beta di Adobe Commerce e come partecipare.
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Versioni beta di Adobe Commerce

A partire da giugno 2023, Adobe rilascerà beta pubbliche per le versioni patch (&quot;versioni beta&quot;). Le versioni beta sono disponibili per tutti i clienti e i partner Adobe Commerce prima della disponibilità generale (GA) e includono correzioni di sicurezza, conformità, prestazioni e qualità ad alta priorità.

>[!IMPORTANT]
>
>I rilasci beta possono contenere difetti e sono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia di alcun tipo. Adobe non avrà alcun obbligo di mantenere, correggere, aggiornare, modificare, modificare o supportare in altro modo (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Contenuti della versione

Ogni versione beta di Adobe Commerce include tutte le modifiche consegnate al codice core di Adobe Commerce entro la data di rilascio pianificata, incluse, a titolo esemplificativo, le seguenti aree funzionali:

- Correzioni di sicurezza più recenti
- Miglioramenti delle prestazioni
- Miglioramenti GraphQL
- Correzioni di bug di qualità generale
- Contributi comunitari
- Modifiche necessarie per supportare la compatibilità con [Servizi Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## Convenzione di denominazione e pianificazione

Adobe rilascerà patch beta due volte all’anno. La prima patch beta viene in genere rilasciata tre mesi dopo la disponibilità generale di una nuova patch dell’applicazione core.

I pacchetti versione beta presentano `-betaX` suffisso. Ad esempio, i pacchetti della versione beta di Adobe Commerce 2.4.7 utilizzano la seguente convenzione di denominazione:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulta la [pianificazione delle versioni](schedule.md) per l’elenco delle prossime date di rilascio della versione beta pubblica.

## Vantaggi della partecipazione

Quanto prima viene visualizzato il codice che stiamo sviluppando, tanto prima sarà possibile preparare la tecnologia e i commercianti per il prossimo aggiornamento.

Anche se le cose possono cambiare, utilizzare le versioni beta ti consentirà di iniziare a capire dove si verificano le modifiche della base di codice e iniziare la preparazione prima della data di rilascio della versione GA.

## Accesso alla versione beta

Le versioni beta di Adobe Commerce sono distribuite come qualsiasi altra versione patch di Adobe Commerce: come metapacchetti Compositore su `https://repo.magento.com`. Il codice sorgente è disponibile su [GitHub](https://github.com/magento/magento2).

Consulta [Guida introduttiva all&#39;installazione del Compositore](../installation/composer.md) per ulteriori dettagli.

## Segnalazione problemi

Adobe non fornisce il servizio standard di supporto Adobe per le versioni beta.

Per inviare feedback relativi alle versioni beta, segui la nostra [flusso regolare di reporting sui problemi](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) il [GitHub](https://github.com/magento/magento2).

I nostri team interni monitoreranno tutti i problemi critici segnalati in base all’ultima versione beta e assegneranno loro un ordine di priorità per la risoluzione prima della data di rilascio della versione GA.

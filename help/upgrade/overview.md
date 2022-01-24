---
title: Panoramica del processo di aggiornamento
description: Scopri come l’aggiornamento di Adobe Commerce e il progetto Magenti Open Source consente di proteggere la vetrina e di funzionare in modo efficiente.
source-git-commit: 8f983e6791da852350fa061fd3119abcdaa03cbf
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---


# Panoramica del processo di aggiornamento

L&#39;aggiornamento del progetto Adobe Commerce o di Magento Open Source è fondamentale per garantire che lo store rimanga sicuro, conforme allo standard PCI e che funzioni con la massima efficienza. Questa guida è stata sviluppata per illustrarvi le considerazioni principali durante la preparazione di un aggiornamento.

La guida fornisce una panoramica del tipico percorso di aggiornamento Adobe Commerce/Magento Open Source e delle best practice da seguire lungo quel percorso. Descrive inoltre i dettagli tecnici del processo di aggiornamento con un esempio tempestivo e istruzioni passo per passo per l’aggiornamento alla versione 2.4.4 di Adobe Commerce/Magenti Open Source. Il rilascio delle patch 2.4.4 sarà generalmente disponibile l’8 marzo 2022, pertanto è importante iniziare a prepararsi all’aggiornamento in anticipo perché il [Fine del ciclo di vita (EOL)](https://devdocs.magento.com/release/lifecycle-policy.html) le date si avvicinano sia per la linea 2.3 che per le versioni da 2.4.0 a 2.4.3 nel 2022. Infine, forniamo risorse di pianificazione e strumenti di aggiornamento che rendono il processo di aggiornamento più efficiente.

## Per chi è questa guida?

Il pubblico di destinazione per questa guida include:

### Manager e direttori tecnici di e-commerce

Questa guida aiuta i clienti di questi ruoli a comprendere il percorso di aggiornamento, l’importanza di un aggiornamento regolare e come pianificare e preparare al meglio un aggiornamento.

### Team operativi e di sviluppo

Questa guida aiuta questi team a scoprire i passaggi tecnici necessari per effettuare l’aggiornamento alla versione 2.4.4 (o a qualsiasi versione di Adobe Commerce/Magento Open Source) e gli strumenti che possono utilizzare per rendere il processo più semplice, veloce e conveniente.

## Informazioni sul processo di aggiornamento

Uno dei motivi per cui hai scelto Adobe Commerce/Magento Open Source probabilmente include:

- Ampio set di funzioni pronto all’uso
- Funzioni SaaS offerte separate dal codice di base
- Offerta affidabile di estensioni Marketplace
- Possibilità unica di offrire una flessibilità infinita per personalizzare il sito in base alle esigenze aziendali e dei clienti.

Il vantaggio di essere un prodotto altamente estensibile e personalizzabile, tuttavia, può stimolare potenziali problemi di aggiornamento quando le personalizzazioni non sono codificate secondo le best practice, portando a costi di aggiornamento più elevati del previsto.

_Allora... perché fare l&#39;upgrade?_

L&#39;aggiornamento consente alle aziende di rimanere agili nel settore eCommerce, in rapida evoluzione e in continua evoluzione, e consente alla piattaforma di essere sempre compatibile con le funzioni più recenti che contribuiscono a massimizzare le vendite e le conversioni. L&#39;inclusione degli aggiornamenti nei normali piani di manutenzione è fondamentale per garantire la sicurezza dello store, la conformità PCI e il funzionamento a un&#39;efficienza massima.

### Sicurezza

La sicurezza è uno dei motivi principali per l&#39;aggiornamento, in quanto l&#39;83% degli incidenti di sicurezza si verifica con software obsoleto. Secondo [IBM](https://www.ibm.com/security/data-breach), il costo medio di una violazione dei dati è di 3,86 milioni di dollari—molto più di quanto costi attenuare questo rischio attraverso l&#39;aggiornamento. L&#39;Adobe offre due modi per proteggere il tuo negozio durante tutto l&#39;anno:

- **Rilasci di patch**- Include correzioni di bug ad alta priorità, tra cui sicurezza, prestazioni, qualità.
- **Versioni delle patch di sicurezza**- Include correzioni e miglioramenti per proteggere il sito e sono più facili da implementare.

### Prestazioni

Le prestazioni sono un altro motivo principale per l’aggiornamento. Secondo [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), i primi cinque secondi di tempo di caricamento hanno un effetto significativo sui tassi di conversione e, in seguito, ogni secondo di latenza ha un impatto del -4,4%. Questo, insieme al fatto che la velocità della pagina è un fattore di classificazione SEO leader, dimostra perché le prestazioni del sito sono un elemento fondamentale del sito da mantenere e migliorare regolarmente. Ogni rilascio di patch include miglioramenti a livello di prestazioni, per cui sfruttare i nuovi rilasci supporta i tuoi piani di crescita e mantiene la tua azienda competitiva.

### Costo del ritardo

Il ritardo o il differimento degli aggiornamenti della piattaforma spesso si riduce al costo immediato. Tuttavia, il costo reale dell&#39;esecuzione di una versione obsoleta di qualsiasi software è molto più grande e può avere un impatto duraturo su un&#39;azienda.

Può sembrare controintuitivo, ma l&#39;esecuzione di regolari aggiornamenti della piattaforma richiede uno sforzo complessivo inferiore rispetto all&#39;esecuzione di aggiornamenti non frequenti a causa della quantità di debito tecnico accumulato che risulta dal ritardo. Recentemente abbiamo lavorato con un partner che ha un commerciante al dettaglio che ha condotto gli aggiornamenti in modo poco frequente e incoerente (ogni anno o più). Trasformando il modo in cui si approcciano agli aggiornamenti e seguendo un percorso di aggiornamento regolare consigliato in Adobe nel corso di 12 mesi, il partner è stato in grado di risparmiare al cliente quattro settimane di tempo di sviluppo cumulativo, impegno e costi associati, tutti reindirizzati a iniziative che guidano la crescita aziendale.

Quando gli aggiornamenti vengono eseguiti regolarmente, le modifiche sono incrementali e lo sforzo di aggiornamento corrispondente riflette questo aspetto. Quando gli aggiornamenti della piattaforma vengono differiti per un periodo prolungato, possono diventare un processo molto più complesso. Inoltre, le estensioni utilizzate dalla [Marketplace](https://marketplace.magento.com/) e possono essere interessate anche altre integrazioni di terze parti. Infine, il tempo necessario per indagare, pianificare ed eseguire un aggiornamento ritardato viene esteso, il che aggiunge sforzi e costi evitabili.

Alcuni dei fattori generali che influiscono sul livello di impegno per l’aggiornamento del progetto includono, tra l’altro:

| Complessità tecnica | Pianificazione e strategia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Ampiezza delle personalizzazioni | Chiarezza dei requisiti, decisioni vacillanti e ambiguità dell&#39;ambito |
| Numero di estensioni | Frequenza di aggiornamento |
| Numero di integrazioni con terzi (OMS, ERP) | Strategia di test |
| Codifica delle best practice |  |

La crescita continua dello spazio commerciale digitale ha esercitato una maggiore pressione sulle aziende affinché evolvano più rapidamente, più spesso e in modo imprevedibile. La mancata tenuta e anticipazione del comportamento di acquisto dei clienti ha livellato le condizioni di gioco anche per i marchi più grandi e consolidati. Devi essere in grado di fornire esperienze solide e personalizzate su tutti i punti di contatto, senza interruzioni nelle prestazioni e nei tempi di attività. Devi essere in grado di innovare più velocemente, senza limiti, per stare al passo con i concorrenti globali. Con l’aggiornamento, potrai eseguire in futuro le prove della tua attività e configurarti per soddisfare le esigenze dei clienti più dinamici.

## Pianificazione del rilascio 2022

Adobe pubblica un [programma di rilascio](https://devdocs.magento.com/release/) ogni anno per facilitare il processo di pianificazione dei commercianti e consiglia di aggiornare ogni ciclo di rilascio delle patch. Per mantenere la conformità PCI, i merchants devono trovarsi nella patch o nella patch di sicurezza più recente. La seguente cronologia mostra le versioni principali e gli eventi EOL del 2022.

![](../assets/upgrade-guide/2022-release-timeline.jpg)

Gli eventi importanti da notare includono:

- La linea 2.3.x raggiunge la fine del supporto (EOS) a settembre 2022
- Da 2.4.0 a 2.4.3 (basato su PHP 7.4) raggiunge EOS nel novembre 2022, quando PHP 7.4 raggiunge la fine del ciclo di vita (EOL)
- In base a questi due eventi EOS, **è importante effettuare l’aggiornamento alla versione 2.4.4 o successiva entro novembre 2022**
- In linea con Adobe Commerce [politica del ciclo di vita](https://devdocs.magento.com/release/lifecycle-policy.html), le versioni 2.4.4 e 2.4.5 riceveranno supporto qualità e patch di sicurezza fino a novembre 2024

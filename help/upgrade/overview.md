---
title: Panoramica del processo di aggiornamento
description: Scopri come l’aggiornamento del progetto Adobe Commerce contribuisce a proteggere la vetrina e a garantire un funzionamento efficiente.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Panoramica del processo di aggiornamento

L’aggiornamento del progetto Adobe Commerce è fondamentale per garantire la sicurezza, la conformità PCI e l’efficienza massima del tuo archivio. Questa guida illustra le considerazioni chiave per la preparazione a un aggiornamento.

La guida fornisce una panoramica del tipico percorso di aggiornamento di Adobe Commerce e delle best practice da seguire lungo tale percorso. Descrive inoltre i dettagli tecnici del processo di aggiornamento con un esempio tempestivo e istruzioni dettagliate per l’aggiornamento alla versione più recente di Adobe Commerce. È importante rivedere l’Adobe Commerce [pianificazione delle versioni](../release/schedule.md) e iniziare a prepararsi per gli aggiornamenti in anticipo. Adobe pubblica annualmente la pianificazione del rilascio per facilitare il processo di pianificazione degli esercenti e consiglia di aggiornare ogni ciclo di rilascio delle patch. Per essere conformi allo standard PCI, gli esercenti devono utilizzare la patch o la patch di sicurezza più recente.

## A chi serve questa guida?

Il pubblico di destinazione di questa guida include:

- **Dirigenti e direttori tecnici di e-commerce**—Comprendere il percorso di aggiornamento, l&#39;importanza dell&#39;aggiornamento regolare e come pianificare e preparare al meglio un aggiornamento.
- **Team operativi e di sviluppo**: scopri i passaggi tecnici necessari per effettuare l’aggiornamento alla versione più recente di Adobe Commerce e gli strumenti disponibili che rendono il processo più semplice, rapido ed economico.

## Spiegazione del processo di aggiornamento

Uno dei motivi per cui hai scelto Adobe Commerce probabilmente include:

- Ampia gamma di funzioni pronte all’uso
- Funzioni SaaS offerte separatamente dal codice core
- Solida offerta di estensioni Marketplace
- Possibilità unica di offrire una flessibilità infinita per personalizzare il sito in base alle esigenze aziendali e dei clienti

Il vantaggio di essere un prodotto altamente estensibile e personalizzabile, tuttavia, può stimolare potenziali problemi di aggiornamento quando le personalizzazioni non sono codificate in best practice, con conseguenti costi di aggiornamento più elevati del previsto.

_Quindi... perché effettuare l&#39;aggiornamento?_

L’aggiornamento consente alla tua azienda di rimanere agile nel settore dell’e-commerce, in continua evoluzione e in rapida evoluzione, e consente alla tua piattaforma di essere compatibile con le funzioni Adobe Commerce più recenti che consentono di massimizzare le vendite e le conversioni. L&#39;inclusione degli aggiornamenti nei piani di manutenzione ordinari è fondamentale per garantire la sicurezza, la conformità PCI e l&#39;efficienza massima del negozio.

### Sicurezza

La sicurezza è uno dei motivi principali per l&#39;aggiornamento, in quanto l&#39;83% degli incidenti di sicurezza si verifica su software obsoleto. Secondo [IBM](https://www.ibm.com/reports/data-breach)Tuttavia, il costo medio di una violazione dei dati è di 3,86 milioni di dollari, molto superiore al costo necessario per mitigare questo rischio con l&#39;aggiornamento. Adobe offre due modi per proteggere il tuo negozio durante l&#39;anno:

- **Versioni patch**- Include correzioni di bug relativi a sicurezza, prestazioni, qualità e priorità alta.
- **Versioni delle patch di sicurezza**- Include correzioni e miglioramenti per proteggere il sito e semplificarne l&#39;implementazione.

### Prestazioni

Le prestazioni sono un altro motivo fondamentale per l&#39;aggiornamento. Secondo [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), i primi cinque secondi di tempo di caricamento hanno un effetto significativo sui tassi di conversione e successivamente ogni secondo di latenza ha un impatto pari a -4,4%. Questo, insieme al fatto che la velocità della pagina è un fattore di classificazione SEO leader, dimostra perché le prestazioni del sito sono un elemento critico del sito da mantenere e migliorare regolarmente. Ogni versione di patch include miglioramenti delle prestazioni, pertanto l&#39;utilizzo delle nuove versioni supporta i piani di crescita e mantiene la competitività aziendale.

### Costo del ritardo

Spesso il ritardo o il differimento degli aggiornamenti della piattaforma si riduce al costo immediato. Tuttavia, il costo reale dell&#39;esecuzione di una versione obsoleta di qualsiasi software è molto maggiore e può avere un impatto duraturo su un&#39;azienda.

Può sembrare inaspettato, ma eseguire aggiornamenti regolari della piattaforma richiede uno sforzo complessivo inferiore rispetto all’esecuzione di aggiornamenti non frequenti a causa dell’entità del debito tecnico accumulato derivante dal ritardo. Adobe ha recentemente lavorato con un partner che ha un commerciante al dettaglio che eseguiva aggiornamenti con scarsa frequenza e incoerenza (annualmente o più a lungo). Trasformando il loro approccio agli aggiornamenti e seguendo un percorso di aggiornamento regolare consigliato dall&#39;Adobe nel corso di 12 mesi, il partner è stato in grado di risparmiare al cliente quattro settimane di tempo di sviluppo cumulativo, impegno e costi associati. Questi costi potrebbero quindi essere riorientati verso iniziative che stimolino la crescita aziendale.

Quando gli aggiornamenti vengono eseguiti regolarmente, le modifiche sono incrementali e il corrispondente sforzo di aggiornamento riflette questo aspetto. Quando gli aggiornamenti della piattaforma vengono differiti per un periodo prolungato, possono diventare un processo molto più coinvolto. Inoltre, le estensioni utilizzate da [Adobe Commerce Marketplace](https://marketplace.magento.com/) e anche altre integrazioni di terze parti potrebbero essere interessate. Infine, il tempo necessario per analizzare, pianificare ed eseguire un aggiornamento ritardato viene esteso, il che aggiunge sforzi e costi evitabili.

Alcuni dei fattori generali che influiscono sul livello di impegno necessario per aggiornare il progetto includono, tra gli altri:

| Complessità tecnica | Pianificazione e strategia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Estensione delle personalizzazioni | Chiarezza dei requisiti, decisioni errate e slittamento dell&#39;ambito |
| Numero di estensioni | Frequenza di aggiornamento |
| Numero di integrazioni con terze parti (OMS, ERP) | La tua strategia di test |
| Codifica in base alle best practice |  |

La crescita continua nello spazio del commercio digitale ha esercitato una maggiore pressione sulle imprese affinché si evolvessero più rapidamente, più spesso e in modo imprevedibile. La mancata capacità di tenere il passo con il comportamento di acquisto dei clienti ha spianato la strada anche ai marchi più grandi e affermati. Devi essere in grado di fornire esperienze solide e personalizzate in tutti i punti di contatto, senza interruzioni di prestazioni e tempo di attività. Devi essere in grado di innovare più rapidamente, senza limiti, per stare al passo con la concorrenza globale. Con l&#39;upgrade, potrai garantire il futuro della tua azienda e configurarti per soddisfare le esigenze dinamiche dei clienti.

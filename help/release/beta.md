---
title: Versioni beta
description: Scopri le versioni beta di Adobe Commerce e come partecipare.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 0e2dfc376a049a47348a7a913bd5181436227cc2
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Versioni beta di Adobe Commerce

I programmi beta di Adobe Commerce consentono ai commercianti di accedere alle funzioni e al codice prerelease, fornire feedback e guidare il futuro di Adobe Commerce. Esistono due tipi di programmi beta:

- Beta pubblica: un programma beta pubblico è disponibile per tutti i clienti e i partner di Adobe Commerce
- Beta privata: per partecipare a un programma beta privato potrebbe essere necessaria un’approvazione basata su criteri di qualificazione

>[!IMPORTANT]
>
>I rilasci beta possono contenere difetti e sono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia di alcun tipo. Adobe non avrà alcun obbligo di mantenere, correggere, aggiornare, modificare, modificare o supportare in altro modo (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Le funzioni e le API in versione beta sono soggette a modifiche senza preavviso. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Vantaggi della partecipazione

L&#39;accesso anticipato alle funzioni sviluppate da Adobe offre a clienti e partner la possibilità di fornire feedback, definire lo sviluppo dei prodotti e prepararsi ad adottare nuove funzionalità prima della disponibilità generale.

## Programmi beta correnti

Per un elenco dei programmi beta attivi, consulta le sezioni seguenti.

### Integrazione di Experience Manager Assets per Commerce (versione beta privata)

L&#39;integrazione di Experience Manager Assets per Commerce consente la gestione e la distribuzione efficienti di un grande volume di immagini di prodotti da Experience Manager Assets ad Adobe Commerce con un minimo sforzo operativo.

Funzioni principali:

- Integrazione Plug and Play: un Adobe di integrazione preconfigurata tra Experience Manager Assets e Adobe Commerce per consentire ai commercianti di concentrarsi su ciò che conta di più, con costi operativi ridotti e maggiore efficienza.

- Personalizzare le immagini dei prodotti su larga scala-Utilizza Experience Manager Assets per generare milioni di varianti di prodotto per esperienze Commerce personalizzate con semplici strumenti di modifica basati sull’interfaccia utente, creazione di contenuti generativa tramite Adobe Firefly e flussi di lavoro di risorse assegnati per garantire la coerenza del marchio. Una volta soddisfatte le risorse, distribuirle direttamente ai punti vendita Commerce utilizzando l’integrazione di Experience Manager Assets.

- Onboarding semplificato: l’onboarding degli esercenti è semplificato con un processo di sincronizzazione configurabile che consente la sincronizzazione completa tra l’archivio Experience Manager Assets e il catalogo Commerce.

- Strategia di corrispondenza flessibile: l’integrazione include algoritmi di corrispondenza delle risorse predefiniti basati su SKU di prodotto che sincronizzano le immagini tra AEM Assets e Commerce ed è estensibile utilizzando Adobe Developer App Builder. Collabora con il tuo partner di soluzioni per creare una strategia di corrispondenza delle risorse personalizzata oltre all’integrazione per adattarsi a qualsiasi struttura dell’archivio di gestione delle risorse.

Per partecipare alla versione beta, invia una richiesta e-mail a [Shaun McCran](mailto:mccran@adobe.com).

### Integrazione del sistema IBM Sterling Order Management (versione beta privata)

Questo acceleratore di integrazione per IBM Sterling Order Management consente ai clienti Adobe Commerce di iniziare con funzionalità avanzate di gestione degli ordini basate su IBM Sterling OMS. Con questa integrazione i commercianti ottengono:
- Visibilità in tempo reale dei livelli di inventario e date di consegna precise per i clienti.
- Acquisizione automatizzata degli ordini in base a regole configurabili, per ottimizzare la rete di evasione e l&#39;inventario.
- Una visione universale degli ordini tra canali da un singolo dashboard in modo che i team di supporto possano fornire un servizio eccezionale e identificare e gestire rapidamente le eccezioni.
- Un flusso di gestione dei resi basato su modelli per semplificare la gestione dei resi.

Per partecipare a questa versione beta, invia una richiesta e-mail a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Connessione dati e Audience Activation (versione beta pubblica)

È stata ampliata la condivisione di dati tra Adobe Commerce e Adobe Experience Platform per promuovere esperienze personalizzate più potenti. Questa funzionalità consente agli esercenti di:
- Condividere i profili cliente di Commerce
- Creare attributi personalizzati
- Ottieni informazioni Commerce in Real-Time CDP e Adobe Journey Optimizer
- Supporto di più set di dati e flussi di dati

Per partecipare a questa versione beta, invia una richiesta e-mail a [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (versione beta pubblica)

Ogni versione beta di Adobe Commerce Foundation include tutte le modifiche consegnate al codice core di Adobe Commerce entro la data di rilascio pianificata, incluse, a titolo esemplificativo, le seguenti aree funzionali:

- Correzioni di sicurezza più recenti
- Miglioramenti delle prestazioni
- Miglioramenti GraphQL
- Correzioni di bug di qualità generale
- Contributi comunitari
- Modifiche necessarie per supportare la compatibilità con [Servizi Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convenzione di denominazione e pianificazione

Adobe in genere rilascia patch beta due volte all’anno.

I pacchetti versione beta presentano `-betaX` suffisso. Ad esempio, i pacchetti della versione beta di Adobe Commerce 2.4.7 utilizzano la seguente convenzione di denominazione:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulta la [pianificazione delle versioni](schedule.md) per l’elenco delle prossime date di rilascio della versione beta pubblica.


#### Accesso alla versione beta

Le versioni beta di Adobe Commerce sono distribuite come qualsiasi altra versione patch di Adobe Commerce: come metapacchetti Compositore su `https://repo.magento.com`. Il codice sorgente è disponibile su [GitHub](https://github.com/magento/magento2).

Consulta [Guida introduttiva all&#39;installazione del Compositore](../installation/composer.md) per ulteriori dettagli.

#### Segnalazione problemi

Adobe non fornisce il servizio standard di supporto Adobe per le versioni beta.

Per inviare feedback relativi alle versioni beta, segui la nostra [flusso regolare di reporting sui problemi](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) il [GitHub](https://github.com/magento/magento2).

I nostri team interni monitoreranno tutti i problemi critici segnalati in base all’ultima versione beta e assegneranno loro un ordine di priorità per la risoluzione prima della data di rilascio della versione GA.

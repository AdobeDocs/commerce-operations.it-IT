---
title: Versioni di Beta
description: Scopri le versioni beta di Adobe Commerce e come partecipare.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Versioni beta di Adobe Commerce

I programmi beta di Adobe Commerce consentono ai commercianti di accedere alle funzioni e al codice prerelease, fornire feedback e guidare il futuro di Adobe Commerce. Esistono due tipi di programmi beta:

- Beta pubblico: un programma beta pubblico è disponibile per tutti i clienti e i partner Adobe Commerce
- Private Beta: per partecipare a un programma beta privato potrebbe essere necessaria un’approvazione basata su criteri di qualificazione

>[!IMPORTANT]
>
>I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Le funzioni e le API in versione beta sono soggette a modifiche senza preavviso. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Vantaggi della partecipazione

L’accesso anticipato alle funzioni sviluppate da Adobe offre a clienti e partner la possibilità di fornire feedback, definire lo sviluppo dei prodotti e prepararsi ad adottare nuove funzionalità prima della disponibilità generale.

## Programmi Beta correnti

Per un elenco dei programmi beta attivi, consulta le sezioni seguenti.

### Ricerca semantica: esperienze di acquisto più intelligenti e basate sul contesto (versione beta privata)

La ricerca semantica è una tecnologia di ricerca e-commerce che comprende il *significato* dietro una query di un acquirente, non solo le parole esatte. A differenza della ricerca tradizionale basata su parole chiave, che spesso ha esito negativo quando le query includono termini non familiari o errati, questo approccio basato sull’intelligenza artificiale interpreta l’intento utilizzando l’elaborazione del linguaggio naturale (NLP) e il contesto per fornire risultati più rilevanti.

Questa tecnologia risolve un importante limite della ricerca tradizionale: pagine a zero risultati che si verificano quando gli acquirenti usano parole che non esistono nel catalogo. Utilizzando tecniche basate sull’intelligenza artificiale, mappa le query utente e i dati dei prodotti in uno spazio semantico condiviso. Ad esempio, il sistema riconosce che &quot;scarpe da corsa&quot; e &quot;scarpe da jogging&quot; si riferiscono allo stesso tipo di prodotto, consentendo:

- Riconoscimento sinonimi
- Rilevanza contestuale
- Gestione intelligente di query vaghe, errate o composte
- Comprensione del linguaggio naturale e conversazionale

Per richiedere un invito al programma beta, invia un&#39;e-mail a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). Il team Adobe risponderà con i passaggi successivi e i requisiti di idoneità.

### Servizio di applicazione di patch per l&#39;automazione cloud (Private Beta)

Il [Cloud Automation Patching Service](../tools/caps-tool/intro.md) automatizza il processo di applicazione di patch di sicurezza isolate agli ambienti [Adobe Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview).

A ottobre 2025, la versione beta del Cloud Automation Patching Service verrà aggiunta alla [dashboard dello strumento di analisi a livello di sito](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Questo servizio supporta gli amministratori di progetto Commerce con un flusso di lavoro di applicazione delle patch semplificato che include:

- Installazione automatica delle patch
- Ripristino rollback
- Verifica post-distribuzione.

Il servizio garantisce la sicurezza, la stabilità e l&#39;aggiornamento degli ambienti con il minimo sforzo e rischio manuale.

La versione beta include le seguenti funzionalità:

- **Installazione automatica delle patch**: semplificazione e automazione del processo di applicazione delle patch a vulnerabilità critiche in ambienti diversi.
- **Riduci al minimo il rischio**: impedisce interruzioni del sito con funzionalità di verifica dello stato e rollback post-distribuzione.

>[!NOTE]
>
>Poiché il servizio di esecuzione patch di automazione cloud applica automaticamente le patch di sicurezza isolate, è necessario disporre del ruolo [Collaboratore o amministratore progetto](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) per utilizzarlo.

Per partecipare a questa versione beta, completa e invia il [Servizio di applicazione di patch per l&#39;automazione cloud - Modulo registrazione Beta](https://forms.office.com/r/3Wfxj5nPdB).

### Integrazione dei sistemi IBM Sterling Order Management (Private Beta)

Questo acceleratore di integrazione per IBM Sterling Order Management consente ai clienti Adobe Commerce di iniziare con funzionalità avanzate di gestione degli ordini basate su IBM Sterling OMS. Con questa integrazione i commercianti ottengono:

- Visibilità in tempo reale dei livelli di inventario e date di consegna precise per i clienti.
- Acquisizione automatizzata degli ordini in base a regole configurabili, per ottimizzare la rete di evasione e l&#39;inventario.
- Una visione universale degli ordini tra canali da un singolo dashboard in modo che i team di supporto possano fornire un servizio eccezionale e identificare e gestire rapidamente le eccezioni.
- Un flusso di gestione dei resi basato su modelli per semplificare la gestione dei resi.

Per partecipare a questa versione beta, invia una richiesta e-mail a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Alpha/Beta pubblico)

Ogni versione alfa e beta di Adobe Commerce Foundation include tutte le modifiche consegnate al codice core di Adobe Commerce entro la data di rilascio pianificata, incluse, a titolo esemplificativo, le seguenti aree funzionali:

- Correzioni di sicurezza più recenti
- Miglioramenti delle prestazioni
- Miglioramenti GraphQL
- Correzioni di bug di qualità generale
- Contributi comunitari
- Modifiche necessarie per supportare la compatibilità con [i servizi Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### Convenzione di denominazione e pianificazione

Adobe rilascia generalmente patch alfa e beta diverse volte all’anno.

I pacchetti di rilascio di Alpha hanno un suffisso `-alphaX`. Ad esempio, i pacchetti di rilascio alfa di Adobe Commerce 2.4.7 utilizzano la seguente convenzione di denominazione:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

I pacchetti di rilascio di Beta hanno un suffisso `-betaX`. Ad esempio, i pacchetti della versione beta di Adobe Commerce 2.4.7 utilizzano la seguente convenzione di denominazione:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulta la [pianificazione delle versioni](schedule.md) per un elenco delle prossime date pubbliche di rilascio delle versioni alfa e beta.

#### Accesso al rilascio

Le versioni alfa e beta di Adobe Commerce sono distribuite come qualsiasi altra versione patch di Adobe Commerce: come metapacchetti Compositore in `https://repo.magento.com`. Il codice sorgente è disponibile su [GitHub](https://github.com/magento/magento2).

Per ulteriori dettagli, vedere [Avvio rapido dell&#39;installazione del Compositore](../installation/composer.md).

#### Segnalazione problemi

Adobe non fornisce il servizio di supporto Adobe standard per le versioni alfa e beta.

Per inviare feedback relativi alle versioni alfa e beta, segui il [flusso regolare di segnalazione dei problemi](https://developer.adobe.com/commerce/contributor/guides/code-contributions) su [GitHub](https://github.com/magento/magento2).

Adobe monitora tutti i problemi critici segnalati in base all’ultima versione alfa o beta e assegna loro un ordine di priorità per la risoluzione prima della data di rilascio GA.

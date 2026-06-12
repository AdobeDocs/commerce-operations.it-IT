---
title: Versioni di Beta
description: Scopri le versioni beta di Adobe Commerce e come partecipare.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud (infrastruttura PaaS gestita da Adobe) e ai progetti on-premise."
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce as a Cloud Service e Adobe Commerce Optimizer (infrastruttura SaaS gestita da Adobe)."
source-git-commit: 41e4aa725848fd7fa4910eaea09a802326fa3995
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Versioni beta di Adobe Commerce

I programmi Beta per [soluzioni dei prodotti Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions) consentono ai commercianti di accedere alle funzioni e al codice prerelease, fornire feedback e guidare il futuro di Adobe Commerce. Esistono due tipi di programmi beta:

- Beta pubblico: un programma beta pubblico è disponibile per tutti i clienti e i partner Adobe Commerce
- Private Beta: per partecipare a un programma beta privato potrebbe essere necessaria un’approvazione basata su criteri di qualificazione

>[!IMPORTANT]
>
>**Dichiarazione di non responsabilità**<br/>
>I rilasci di Beta includono funzioni prerelease e codice che possono contenere difetti e vengono forniti &quot;COSÌ COM&#39;È&quot; senza alcuna garanzia. Adobe ha la sola discrezione di decidere se rendere le versioni beta generalmente disponibili. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare, modificare, supportare (tramite i servizi di supporto Adobe o in altro modo) o di fornire tali versioni beta entro una data specifica. Se una versione beta diventa generalmente disponibile, può essere soggetta a termini e condizioni aggiuntivi, comprese le tariffe applicabili. Le versioni Beta sono soggette a modifiche senza preavviso, inclusa la loro interruzione. Si consiglia ai clienti di prestare attenzione e di non fare affidamento in alcun modo sul funzionamento o sulle prestazioni ininterrotti o privi di errori delle versioni beta.  Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Vantaggi della partecipazione

L’accesso anticipato alle funzioni sviluppate da Adobe offre a clienti e partner la possibilità di fornire feedback, definire lo sviluppo dei prodotti e prepararsi ad adottare nuove funzionalità prima della disponibilità generale.

## Programmi Beta correnti

Per un elenco dei programmi beta attivi, consulta le sezioni seguenti.

### Corrispondenza ricerca e classificazione (Private Beta)

[!BADGE Solo SaaS]{type=Positive url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce as a Cloud Service e Adobe Commerce Optimizer (infrastruttura SaaS gestita da Adobe)."}

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud (infrastruttura PaaS gestita da Adobe) e ai progetti on-premise."}

Adobe sta migliorando il modo in cui l&#39;individuazione del prodotto classifica i risultati della ricerca per [!DNL Live Search] in [!DNL Adobe Commerce] e per [!DNL Adobe Commerce Optimizer]. L&#39;aggiornamento assegna priorità a **corrispondenze esatte e simili a frasi**, quindi a **tutti i termini di query vengono visualizzati nello stesso attributo ricercabile** e infine a **corrispondenze tra campi diversi** (incluso il comportamento che supporta suggerimenti di tipo completamento automatico). Questo modello su più livelli consente alle query ad alto intento di far emergere per prime i prodotti più rilevanti, restituendo al contempo alternative utili.

Lo stesso modello di rilevanza interagisce con **pesi di ricerca**, **classificazione intelligente**, **sinonimi** e **regole merchandising** (pin, boost, bury). Gli storefront tedeschi possono utilizzare **decomponunding** per le parole composte, con lo stesso approccio di priorità generale.

**Vantaggi chiave**

- Incrementi più forti per corrispondenza di frasi esatte e vicine (comprese forme normalizzate come singolare e plurale).
- Classificazione più alta quando tutte le parole della query vengono visualizzate insieme in un campo ricercabile.
- Aspettative più chiare sul modo in cui i pesi, la classificazione intelligente e le regole manuali si combinano al momento della query.
- Linee guida per la convalida di query di alto valore e l’ottimizzazione delle regole di incremento dopo la modifica.

Ulteriori informazioni sulla strategia di corrispondenza e classificazione delle ricerche in [Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/en/docs/commerce/optimizer/search-relevance-matching) e [Live Search (PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/search-relevance-matching).

Per richiedere un invito per questa versione beta privata, invia un&#39;e-mail a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). Il team Adobe risponderà con i passaggi successivi e i requisiti di idoneità.

### Filtri prezzi consigli (Public Beta) {#recommendation-price-filters-public-beta}

[!BADGE Solo SaaS]{type=Positive url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce as a Cloud Service e Adobe Commerce Optimizer (infrastruttura SaaS gestita da Adobe)."}

[!DNL Adobe Commerce Optimizer] aggiunge **filtri prezzo** ai consigli di prodotto in modo da poter includere o escludere i prodotti consigliati in base al prezzo al momento della creazione o della modifica di un&#39;unità di consigli. I filtri utilizzano il **prezzo calcolato finale** di ogni prodotto dal **listino prezzi attivo** dello storefront, inclusi sconti e promozioni da quel listino prezzi (non solo listino prezzi). Le regole di prezzo consentono di perfezionare il set di candidati e non di riclassificare i prodotti.

Puoi definire **intervalli statici** con valori minimi e massimi fissi nella valuta di base del tuo store, oppure **regole dinamiche** nelle pagine dei dettagli del prodotto che confrontano i prodotti consigliati con il **prodotto attualmente visualizzato** utilizzando operatori come minore o uguale a, maggiore o uguale a, o all&#39;interno di un valore o intervallo percentuale del prezzo di ancoraggio. I filtri dinamici sono disponibili per i tipi di consigli relativi a SKU eseguiti nel contesto del prodotto (ad esempio, *Ha visualizzato questo/a, ha visualizzato quello* e *Altri elementi simili*).

**Vantaggi chiave**

- Includi o escludi i candidati per i consigli in base al prezzo utilizzando le regole di inclusione ed esclusione nel passaggio **Filtra prodotti**.
- Utilizza fasce di prezzo statiche per obiettivi di merchandising fissi (ad esempio, componenti aggiuntivi per il budget o articoli premium).
- Utilizza le regole di prezzo dinamiche nella pagina dei dettagli del prodotto per mostrare alternative all’interno di una fascia di prezzo comparabile rispetto al prodotto visualizzato.
- Allinea il filtro con il prezzo visualizzato dagli acquirenti, che è lo stesso prezzo finale del listino prezzi attivo utilizzato per il filtro e la visualizzazione.

Per ulteriori informazioni, consulta [Filtri per consigli: prezzo](https://experienceleague.adobe.com/it/docs/commerce/optimizer/merchandising/recommendations/filters#price) nella guida per i commercianti e [Configurazione per consigli di prodotto](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/?lang=it) nella guida per l&#39;accesso a Storefront.

Per condividere il tuo feedback durante l&#39;utilizzo di questa funzione beta, invia un&#39;e-mail a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Servizio di applicazione di patch per l&#39;automazione cloud (Private Beta)

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud (infrastruttura PaaS gestita da Adobe) e ai progetti on-premise."}

Il [Cloud Automation Patching Service](../tools/caps-tool/intro.md) automatizza il processo di applicazione di patch di sicurezza isolate agli ambienti [Adobe Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/overview).

A ottobre 2025, la versione beta del Cloud Automation Patching Service verrà aggiunta alla [dashboard dello strumento di analisi a livello di sito](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Questo servizio supporta gli amministratori di progetto Commerce con un flusso di lavoro di applicazione delle patch semplificato che include:

- Installazione automatica delle patch
- Ripristino rollback
- Verifica post-distribuzione.

Il servizio garantisce la sicurezza, la stabilità e l&#39;aggiornamento degli ambienti con il minimo sforzo e rischio manuale.

La versione beta include le seguenti funzionalità:

- **Installazione automatica delle patch**: semplificazione e automazione del processo di applicazione delle patch a vulnerabilità critiche in ambienti diversi.
- **Riduci al minimo il rischio**: impedisce interruzioni del sito con funzionalità di verifica dello stato e rollback post-distribuzione.

>[!NOTE]
>
>Poiché il servizio di esecuzione patch di automazione cloud applica automaticamente le patch di sicurezza isolate, è necessario disporre del ruolo [Collaboratore o amministratore progetto](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/project/user-access) per utilizzarlo.

Per partecipare a questa versione beta, completa e invia il [Servizio di applicazione di patch per l&#39;automazione cloud - Modulo registrazione Beta](https://forms.office.com/r/3Wfxj5nPdB).

### Assistente di IA per l’analisi della produttività dei commercianti (Beta pubblico)

L’Assistente per l’intelligenza artificiale per la produttività dei commercianti è un’interfaccia di conversazione incorporata nell’amministratore di Adobe Commerce che consente ai commercianti di completare le attività di routine e di accedere a informazioni aziendali su richiesta utilizzando un linguaggio naturale. Consente ai commercianti di gestire le promozioni, aggiornare le informazioni sul catalogo dei prodotti e recuperare i dati operativi, come ordini recenti o promozioni attive, direttamente all&#39;interno dei flussi di lavoro esistenti. L’assistente fornisce anche indicazioni contestuali per consentire ai commercianti di navigare e utilizzare l’amministratore in modo più efficiente.

**Vantaggi chiave**

- Automatizza le attività di merchandising più comuni, tra cui la creazione di promozioni e gli aggiornamenti dei metadati del catalogo, utilizzando le istruzioni per il linguaggio naturale.
- Accedi all’assistenza e alle indicazioni contestuali direttamente all’interno del flusso di lavoro di amministrazione.
- Eseguire query sui dati del negozio live su richiesta, ad esempio recuperare gli ultimi 10 ordini, visualizzare le promozioni attualmente attive o controllare lo stato del magazzino.
- Riduci il tempo dedicato ad attività di amministrazione ripetitive, consentendo ai commercianti di concentrarsi sulla strategia e sulla crescita.

Per partecipare a questa versione beta, invia un&#39;e-mail a [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Adobe Commerce Foundation (Alpha/Beta pubblico)

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud (infrastruttura PaaS gestita da Adobe) e ai progetti on-premise."}

Ogni versione alfa e beta di Adobe Commerce Foundation include tutte le modifiche consegnate al codice core di Adobe Commerce entro la data di rilascio pianificata, incluse, a titolo esemplificativo, le seguenti aree funzionali:

- Correzioni di sicurezza più recenti
- Miglioramenti delle prestazioni
- Miglioramenti GraphQL
- Correzioni di bug di qualità generale
- Contributi comunitari
- Modifiche necessarie per supportare la compatibilità con [i servizi Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce/user-guides/home)

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

Per inviare feedback relativi alle versioni alfa e beta, segui il [flusso regolare di segnalazione dei problemi](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) su [GitHub](https://github.com/magento/magento2).

Adobe monitora tutti i problemi critici segnalati in base all’ultima versione alfa o beta e assegna loro un ordine di priorità per la risoluzione prima della data di rilascio GA.

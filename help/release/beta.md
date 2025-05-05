---
title: Versioni di Beta
description: Scopri le versioni beta di Adobe Commerce e come partecipare.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: ea4f340540e57b282657a44502d80f1d5c409c6a
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# Versioni beta di Adobe Commerce

I programmi beta di Adobe Commerce consentono ai commercianti di accedere alle funzioni e al codice prerelease, fornire feedback e guidare il futuro di Adobe Commerce. Esistono due tipi di programmi beta:

- Beta pubblico: un programma beta pubblico è disponibile per tutti i clienti e i partner Adobe Commerce
- Private Beta: per partecipare a un programma beta privato potrebbe essere necessaria un’approvazione basata su criteri di qualificazione

>[!IMPORTANT]
>
>I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non avrà alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Le funzioni e le API in versione beta sono soggette a modifiche senza preavviso. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Vantaggi della partecipazione

L’accesso anticipato alle funzioni sviluppate da Adobe offre a clienti e partner la possibilità di fornire feedback, definire lo sviluppo dei prodotti e prepararsi ad adottare nuove funzionalità prima della disponibilità generale.

## Programmi Beta correnti

Per un elenco dei programmi beta attivi, consulta le sezioni seguenti.

### Adobe Commerce Optimizer

Adobe Commerce Optimizer migliora la tua esperienza di e-commerce con una vetrina ad alte prestazioni, aumentando il traffico organico, il coinvolgimento dei clienti e i ricavi.

Con Adobe Commerce Optimizer è possibile:

- Aumenta e ridimensiona il catalogo senza riorganizzare l’intero stack commerce.
- Acquisisci i dati del catalogo da qualsiasi origine.
- Definire i canali e i criteri aziendali.
- Crea ricerche e consigli personalizzati utilizzando IA e ML.
- Visualizzare i dati fondamentali sulla disponibilità dei prodotti, compresi lo stato di sincronizzazione e i dati degli eventi storefront, per un&#39;implementazione e una risoluzione dei problemi accurate.

[Ulteriori informazioni](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html?lang=it) su Adobe Commerce Optimizer. Per ulteriori informazioni sul programma di accesso anticipato [!DNL Adobe Commerce Optimizer], compilare il [modulo di richiesta di accesso anticipato](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5UMlhTMTYzVDhPQVFNTUFYUjJHNlRKTE5TWS4u).

### Funzionalità di ricerca avanzate per Live Search (Beta pubblico)

Questa versione beta supporta tre nuove funzionalità nella query [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Ricerca a livelli** - Ricerca in un altro contesto di ricerca - Con questa funzionalità è possibile eseguire fino a due livelli di ricerca per le query di ricerca. Ad esempio:

   - **Ricerca livello 1** - Ricerca &quot;motor&quot; in &quot;product_attribute_1&quot;.
   - **Ricerca livello 2** - Cercare &quot;numero parte 123&quot; in &quot;product_attribute_2&quot;. In questo esempio viene cercata la voce &quot;part number 123&quot; all&#39;interno dei risultati per &quot;motor&quot;.

  La ricerca con livelli è disponibile sia per l&#39;indicizzazione di ricerca `startsWith` che per quella `contains` come descritto di seguito:

- **startsWith indicizzazione ricerca** - Effettua la ricerca utilizzando l&#39;indicizzazione `startsWith`. Questa nuova funzionalità consente di:

   - Ricerca di prodotti in cui il valore dell&#39;attributo inizia con una stringa specifica.
   - La configurazione di una ricerca &quot;termina con&quot; consente agli acquirenti di cercare prodotti in cui il valore dell’attributo termina con una stringa specifica. Per abilitare una ricerca &quot;termina con&quot;, l’attributo del prodotto deve essere acquisito in ordine inverso e anche la chiamata API deve essere una stringa inversa.

- **contiene l&#39;indicizzazione della ricerca** -Cercare un attributo utilizzando l&#39;indicizzazione contains. Questa nuova funzionalità consente di:

   - Ricerca di una query all&#39;interno di una stringa più grande. Ad esempio, se un acquirente cerca il numero di prodotto &quot;PE-123&quot; nella stringa &quot;HAPE-123&quot;.

      - Nota: questo tipo di ricerca è diverso dalla [ricerca frase](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) esistente, che esegue una ricerca di completamento automatico. Ad esempio, se il valore dell’attributo del prodotto è &quot;pantaloni da esterni&quot;, la ricerca di una frase restituisce una risposta per &quot;out pan&quot;, ma non restituisce una risposta per &quot;o formiche&quot;. Una ricerca contiene, tuttavia, restituisce una risposta per &quot;o formiche&quot;.

Queste nuove condizioni migliorano il meccanismo di filtro delle query di ricerca per perfezionare i risultati della ricerca. Queste nuove condizioni non influiscono sulla query di ricerca principale. Per partecipare alla versione beta, invia una richiesta e-mail a [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Per installare la versione beta di Live Search, consulta la [guida di Live Search](https://experienceleague.adobe.com/it/docs/commerce/live-search/install#install-the-live-search-beta).

### Integrazione dei sistemi IBM Sterling Order Management (Private Beta)

Questo acceleratore di integrazione per IBM Sterling Order Management consente ai clienti Adobe Commerce di iniziare con funzionalità avanzate di gestione degli ordini basate su IBM Sterling OMS. Con questa integrazione i commercianti ottengono:

- Visibilità in tempo reale dei livelli di inventario e date di consegna precise per i clienti.
- Acquisizione automatizzata degli ordini in base a regole configurabili, per ottimizzare la rete di evasione e l&#39;inventario.
- Una visione universale degli ordini tra canali da un singolo dashboard in modo che i team di supporto possano fornire un servizio eccezionale e identificare e gestire rapidamente le eccezioni.
- Un flusso di gestione dei resi basato su modelli per semplificare la gestione dei resi.

Per partecipare a questa versione beta, invia una richiesta e-mail a [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Beta pubblica)

Ogni versione beta di Adobe Commerce Foundation include tutte le modifiche consegnate al codice core di Adobe Commerce entro la data di rilascio pianificata, incluse, a titolo esemplificativo, le seguenti aree funzionali:

- Correzioni di sicurezza più recenti
- Miglioramenti delle prestazioni
- Miglioramenti GraphQL
- Correzioni di bug di qualità generale
- Contributi comunitari
- Modifiche necessarie per supportare la compatibilità con [i servizi Adobe Commerce](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html?lang=it)

#### Convenzione di denominazione e pianificazione

Adobe in genere rilascia patch beta due volte all’anno.

I pacchetti di rilascio di Beta hanno un suffisso `-betaX`. Ad esempio, i pacchetti della versione beta di Adobe Commerce 2.4.7 utilizzano la seguente convenzione di denominazione:

- `2.4.7-beta1`
- `2.4.7-beta2`

Per un elenco delle prossime date di rilascio della versione beta pubblica, consulta la [pianificazione del rilascio](schedule.md).

#### Accesso alla versione di Beta

Le versioni beta di Adobe Commerce vengono distribuite come qualsiasi altra versione patch di Adobe Commerce: come metapacchetti Compositore in `https://repo.magento.com`. Il codice sorgente è disponibile su [GitHub](https://github.com/magento/magento2).

Per ulteriori dettagli, vedere [Avvio rapido dell&#39;installazione del Compositore](../installation/composer.md).

#### Segnalazione problemi

Adobe non fornisce il servizio di supporto Adobe standard per le versioni beta.

Per inviare feedback relativi alle versioni beta, segui il [flusso regolare di segnalazione dei problemi](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) in [GitHub](https://github.com/magento/magento2).

I nostri team interni monitoreranno tutti i problemi critici segnalati in base all’ultima versione beta e assegneranno loro un ordine di priorità per la risoluzione prima della data di rilascio della versione GA.

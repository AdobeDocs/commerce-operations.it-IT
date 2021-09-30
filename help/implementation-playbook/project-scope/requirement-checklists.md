---
title: Elenchi di controllo dei requisiti
description: Utilizza questo elenco di domande complete per prepararti a un’implementazione Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# Elenchi di controllo dei requisiti

Le seguenti domande possono fungere da punto di partenza per vedere quali informazioni devono essere documentate per confermare la preparazione organizzativa. Possono inoltre essere di aiuto quando si sviluppa un PQR.

## Business

- What are the business goals for the new ecommerce platform?

- What are the reasons for changing your current ecommerce platform?

- Quali sono gli obiettivi dell&#39;infrastruttura web?

- What is your timeframe to deliver the new ecommerce platform?

- Quanti project manager IT verranno assegnati a questo progetto?

- How many of your business analysts will be assigned to this project?

- Quanti dei vostri analisti tecnici saranno assegnati a questo progetto?

- How many of your HTML developers will be assigned to this project?

- Quale documentazione esiste per i processi aziendali correnti?

- What documentation exists for current system integrations?

- Quale documentazione esiste per i flussi di processo correnti?

- Quale documentazione esiste per i flussi di dati correnti?

- Chi fornirà la formazione?

- Quale formazione sarà completata prima del live?

- Quale formazione sarà completata dopo l&#39;entrata in servizio?

- What Adobe Commerce support will be required after go-live?

- Questo progetto dipende da altri progetti di sviluppo del sistema?

- Come vede l&#39;aumento delle vendite nei prossimi 12-24 mesi?

- Chi sono i suoi principali concorrenti? Fornisci i collegamenti ai loro siti. How do you want to differentiate your online experience from your competitors?

- Where do you see future growth coming from in your business?

- Qual è il ruolo del commercio digitale nella tua strategia commerciale? Quali sono i vostri obiettivi principali per la creazione di questa piattaforma commerciale?

- Hai marchi/aziende che prendi come riferimento su come crescere il tuo business omnichannel?

- Quali team o individui stanno guidando la strategia commerciale? Descrivere le posizioni pertinenti.

## Current platform

- In che modo è ospitata la piattaforma corrente: Interno, provider di hosting, server cloud privati o server cloud ospitati?

- Quali ambienti dispone della piattaforma corrente: sviluppo, QA, pre-produzione, produzione?

- How many web and database servers are in the development environment?

- How many web and database servers are in the QA environment?

- Quanti server web e database si trovano nell’ambiente di staging (pre-produzione)?

- Quanti server web e database si trovano nell&#39;ambiente di produzione?

- Si tratta di un’architettura multi-server con bilanciamento del carico?

- Is it a high-availability system architecture?

- What problems are you experiencing with your current websites?

- Dimensione attuale del catalogo (numero di SKU)?

- Visitatori medi al giorno?

- Average concurrent sessions per hour?

- Visualizzazioni di pagina medie al giorno?

- Ordini medi all&#39;ora e al giorno?

## Requisiti della piattaforma previsti

- Which Adobe Commerce version will you use?

- Come sarà ospitata la futura piattaforma: Interno, provider di hosting, server cloud privati o server cloud ospitati?

- Quali ambienti avranno la piattaforma futura: sviluppo, QA, pre-produzione, produzione?

- How many web and database servers will be in the development environment?

- Will it be a high-availability system architecture?

- How manyAdobe Commerceadministrators will you have?

- Expected catalog size (number of SKUs)?

- Expected average visitors per day?

- Expected average concurrent sessions per hour?

- Expected average page views per day?

- What data should be imported from the old site to the new site? (Esempio: prodotto, cliente, cronologia ordini)

## Websites

- How many domestic websites will be implemented?

- Which languages will be implemented?

- How many international websites will be implemented?

- Quali regioni saranno supportate dai siti web?

- Which languages will be implemented?

- Quali valute saranno attuate?

- Hai accordi a livello di servizio di consegna per ogni paese?

- Chi sono i vostri fornitori di consegne per ogni paese?

- Chi sono i suoi fornitori di contabilità fiscale per ogni paese?

- Richiederai un tema personalizzato del sito web internazionale?

- Si tratta principalmente di un sito B2C o B2B? Esiste un elemento B2B2B o B2B2C?

- Is there an existing design that is adapted,or will the platform be designed from scratch?

- Is there a requirement for headless commerce (separate frontend and backend layers)?

- What are the break points (tablet/mobile) for the responsive design?

- Esiste un requisito per un’app mobile? PWA dovrebbe essere sfruttato per i dispositivi mobili front-end?

- Alcuni browser specifici da testare (ad eccezione dei browser standard IE9+, Firefox, Chrome, Safari)?

- What are the language(s) for eachfront end? Is the translated content available or is support needed?

- Are there multiple websites? If so,cancustomers use their credentials across all sites?

- Is product data shared across all sites?

- Sono presenti modifiche nella progettazione da sito a sito?

- Are there subscription options and how are subscribers managed?

- Esistono requisiti specifici in materia di SEO? Come viene gestito il marketing basato su motori di ricerca?

## Integrazioni

- Quale sistema CMS verrà integrato con Adobe Commerce? (Examples: WordPress, Drupal, Concrete5)

Are there existing APIs that can be used?

- La gestione degli errori di sistema è stata progettata e sviluppata per questa integrazione di sistemi di terze parti?

- Quale sistema ERP verrà integrato con Adobe Commerce? (Esempi: SAP, MS Dynamics NAV)

- Quale sistema di vettori di spedizione sarà integrato con Adobe Commerce?

- Quale sistema software fiscale sarà integrato con Adobe Commerce? (Example:Taxware)

- From which system will product data be imported intoAdobe Commerce?

- Frequency of imported product data loads?

- In quale sistema verranno esportati i dati dei prodotti Adobe Commerce?

- Frequenza dei carichi di dati di prodotto esportati?

- Da quale sistema verranno importati i dati dell’ordine in Adobe Commerce?

- Frequenza dei carichi di dati dell&#39;ordine importati?

- Into which system willAdobe Commerceexport order data?

- Frequenza dei carichi di dati dell&#39;ordine esportati?

- Which analytics platform is used? (Examples: Adobe Analytics, Google Analytics)

- Ci sarà un single sign on e condivisione dei social network? In caso affermativo, quali reti sociali?

- Is there any rewards or loyalty programs in place? Esiste un&#39;integrazione con i sistemi POS per i premi?

- Come vengono gestiti i rendimenti dei prodotti? Il cliente deve registrare una richiesta di ritorno online?

- È necessario uno strumento di chat online? Is a chatbot needed?

- Quale gateway di pagamento vuoi che abbia il tuo sito?

- Which order management system will be integrated withAdobe Commerce? (Examples: Microsoft Dynamics, SAP, Retail Pro)

- Quale sistema di gestione dell’inventario dei prodotti sarà integrato con Adobe Commerce? (Esempi: Akeneo, InRiver, Bluestone)

- Which customer relationship management system will be integrated withAdobe Commerce? (Esempi: Hubspot, Salesforce, Klaviyo)

## Funzioni specifiche di Adobe Commerce

- Richiederai un qualsiasi tipo di test A/B?

- Quanti amministratori simultanei possono lavorare nel sistema?

- Permetterai a un cliente di ritirare gli articoli acquistati sul sito web in un negozio?

- Avrà delle pagine promozionali?

- Will you have marketing banners?

- Vuoi far riprodurre i video in una pagina CMS?

- Quale sarà la frequenza di modifica o aggiornamento del contenuto?

- Quale tipo di contenuto verrà caricato?

- Gli aggiornamenti dei contenuti saranno pianificati?

- Will you require a content staging website?

- Deve essere consentito ai clienti di creare un account sito web?

- Utilizzerai buoni sconto univoci per le promozioni?

- Will you have promotional pricing?

- Will you have flexible coupons (ability to set per website, customer group, time, categories, or products)?

- Saranno offerti sconti percentuali per singoli articoli?

- What type of gift functionality will be required?

- Sarà necessaria la funzionalità del programma di premi?

- Will newsletter functionality be required?

- Allow a customer to view past orders and select items to be exchanged?

- Permetterai a un cliente di avviare l&#39;annullamento di un ordine dal sito web?

- Will you allow a customer to initiate the exchange of items from the website?

- Will you require real-time address validation?

- Permetterai a un cliente di avviare la restituzione degli articoli dal sito web?

- Adobe Commerce emetterà un RMA di ritorno?

- Acquisire informazioni sul rimborso in Adobe Commerce?

- Richiederai il tracciamento degli ordini online per un cliente registrato?

- Will you require online order tracking for a guest customer?

- Esegui l&#39;autorizzazione online e acquisisci durante il posizionamento dell&#39;ordine?

- Autorizzazione con filtro per frode durante il posizionamento dell&#39;ordine con recupero ritardato

- Numero di giorni per ricevere il pagamento completo (non autorizzazione)?

- Cattura ed esegui in caso di scadenza dell&#39;autorizzazione?

- Authorize.net

- Braintree

- PayPal Express

- Store credit

- Plastic gift cards

- Punti di premio

- &quot;Bill Me Later”– more commonly knownas“Buy Now, Pay Later”as it&#39;s immediately billed but not paid yet

- Will there be different product pricing on different websites?

- Sarà necessaria una funzionalità per confrontare prodotti diversi?

- Che tipi di prodotti venderai?

- What will be the frequency of adding new products?

- Quale sarà la frequenza di aggiornamento dei prodotti?

- What will be the frequency of creating new categories or sub-categories?

- Will &quot;Ratings and Reviews&quot; functionality be required?

- Permetterai ai clienti di consigliare un prodotto?

- Vendite: Ordini, imposte, fatturati, spedizione, rimborsi, coupon, report di regolamento PayPal

- Shopping cart: Products in carts, abandoned arts

- Prodotti: Bestseller, prodotti ordinati, più visti, basso, download

- Clienti: Newaccount, clienti per totale ordini, clienti per numero di ordini, segmenti di clienti, recensioni dei clienti

- Recensioni sui prodotti

- Tag: Clienti, prodotti, popolari

- Termini di ricerca

- Inviti: Generale, clienti, tasso di conversione ordine

- Sarà necessario Adobe Commerce per generare rapporti basati sui dati di utilizzo dei coupon?

- Sarà necessario Adobe Commerce per generare rapporti basati sui dati di vendita?

- Will you need custom Adobe Commercere ports?

- What is your current SEO strategy?

- Quale sarà la tua nuova strategia SEO?

- Quali sono i requisiti per la migrazione SEO?

- Memorizzare le tariffe fisse in Adobe Commerce?

- Consentire la spedizione parziale?

- Le informazioni di tracciamento delle spedizioni devono essere memorizzate in Adobe Commerce?

- Richiederai regole di calcolo delle imposte per le tue regioni nazionali?

- Richiederai regole di calcolo delle imposte per le tue regioni internazionali?

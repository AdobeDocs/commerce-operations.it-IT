---
title: Elenchi di controllo requisiti
description: Utilizza questo elenco di domande complete per aiutarti a prepararti per un’implementazione Adobe Commerce.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
feature: Best Practices
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Elenchi di controllo requisiti

Le seguenti domande possono fungere da punto di partenza per vedere quali informazioni devono essere documentate per confermare la preparazione organizzativa. Possono anche essere utili per sviluppare un RFP.

## Aziende

- Quali sono gli obiettivi aziendali per la nuova piattaforma di e-commerce?

- Quali sono le ragioni per cambiare la tua attuale piattaforma di e-commerce?

- Quali sono gli obiettivi per l’infrastruttura del sito web?

- Qual è il tuo periodo di tempo per distribuire la nuova piattaforma di e-commerce?

- Quanti project manager IT saranno assegnati a questo progetto?

- Quanti analisti aziendali saranno assegnati a questo progetto?

- Quanti analisti tecnici saranno assegnati a questo progetto?

- Quanti dei tuoi sviluppatori HTML saranno assegnati a questo progetto?

- Quale documentazione è disponibile per i processi aziendali correnti?

- Qual è la documentazione disponibile per le integrazioni di sistema correnti?

- Qual è la documentazione relativa ai flussi di processo correnti?

- Qual è la documentazione dei flussi di dati correnti?

- Chi fornirà la formazione?

- Quale corso di formazione verrà completato prima del lancio?

- Quale corso di formazione sarà completato dopo il lancio?

- Quale supporto Adobe Commerce sarà richiesto dopo il lancio?

- Il progetto dipende da altri progetti di sviluppo del sistema?

- Come pensi che aumenteranno le tue vendite nei prossimi 12-24 mesi?

- Chi sono i tuoi principali concorrenti? Inserisci i collegamenti ai loro siti. Come vuoi differenziare la tua esperienza online dalla concorrenza?

- Quali sono le prospettive di crescita per il tuo business?

- Quale ruolo svolge il commercio digitale nella tua strategia aziendale? Quali sono i tuoi obiettivi principali per la configurazione di questa piattaforma di e-commerce?

- Hai marchi/aziende da utilizzare come riferimento per la crescita del tuo business omnicanale?

- Quali team o singoli utenti guidano la strategia di e-commerce? Descrivere le posizioni pertinenti.

## Piattaforma corrente

- In che modo viene ospitata la piattaforma corrente: interna, del provider di hosting, dei server cloud privati o dei server cloud ospitati?

- Quali ambienti dispone la piattaforma corrente: sviluppo, controllo qualità, preproduzione, produzione?

- Quanti server web e di database sono presenti nell&#39;ambiente di sviluppo?

- Quanti server web e di database sono presenti nell&#39;ambiente di controllo qualità?

- Quanti server web e di database sono presenti nell&#39;ambiente di staging (pre-produzione)?

- Quanti server web e di database sono presenti nell&#39;ambiente di produzione?

- Si tratta di un&#39;architettura multiserver con bilanciamento del carico?

- Si tratta di un&#39;architettura di sistema ad alta disponibilità?

- Quali problemi si verificano con i siti Web correnti?

- Dimensione catalogo corrente (numero di SKU)?

- Visitatori medi al giorno?

- Numero medio di sessioni simultanee all&#39;ora?

- Visualizzazioni di pagina medie al giorno?

- Ordini medi all&#39;ora e al giorno?

## Requisiti previsti per la piattaforma

- Quale versione di Adobe Commerce utilizzerai?

- In che modo verrà ospitata la futura piattaforma: interna, del provider di hosting, dei server cloud privati o dei server cloud ospitati?

- Quali ambienti disporrà la futura piattaforma: sviluppo, controllo qualità, preproduzione, produzione?

- Quanti server web e di database saranno presenti nell&#39;ambiente di sviluppo?

- Sarà un&#39;architettura di sistema ad alta disponibilità?

- Quanti amministratori Adobe Commerce avrai?

- Dimensione prevista del catalogo (numero di SKU)?

- Visitatori medi previsti al giorno?

- Media prevista sessioni simultanee all&#39;ora?

- Media giornaliera prevista delle visualizzazioni di pagina?

- Quali dati devono essere importati dal sito precedente al nuovo? (Esempio: prodotto, cliente, cronologia ordini)

## Siti Web

- Quanti siti web nazionali saranno implementati?

- Quali lingue verranno implementate?

- Quanti siti web internazionali saranno implementati?

- Quali aree geografiche saranno supportate dai siti Web?

- Quali lingue verranno implementate?

- Quali valute verranno implementate?

- Sono disponibili accordi sui livelli di servizio di consegna per ciascun paese?

- Chi sono i fornitori di servizi di consegna per ciascun paese?

- Chi sono i fornitori di contabilità fiscale per ogni paese?

- Sarà necessario un tema del sito Web internazionale personalizzato?

- È principalmente un sito B2C o B2B? Esiste un elemento B2B2B o B2B2C?

- Esiste un progetto esistente adattato o la piattaforma sarà progettata da zero?

- Esiste un requisito per l’e-commerce headless (livelli front-end e back-end separati)?

- Quali sono i punti di interruzione (tablet/mobile) per il design reattivo?

- Esiste un requisito per un’app mobile? PWA dovrebbe essere utilizzato per il front-end mobile?

- Browser specifici da testare (eccetto i browser standard IE9+, Firefox, Chrome, Safari)?

- Quali sono le lingue per ogni front-end? Il contenuto tradotto è disponibile o è necessario supporto?

- Esistono più siti Web? In caso affermativo, i clienti possono utilizzare le credenziali in tutti i siti?

- I dati dei prodotti sono condivisi tra tutti i siti?

- La progettazione viene modificata da un sito all&#39;altro?

- Esistono opzioni di abbonamento e come vengono gestiti gli abbonati?

- Esistono requisiti SEO specifici? Come viene gestito il marketing dei motori di ricerca?

## Integrazioni

- Quale sistema CMS sarà integrato con Adobe Commerce? (Esempi: WordPress, Drupal, Concrete5)

È possibile utilizzare delle API esistenti?

- La gestione degli errori di sistema è stata progettata e sviluppata per questa integrazione di sistema di terze parti?

- Quale sistema ERP sarà integrato con Adobe Commerce? (Esempi: SAP, MS Dynamics NAV)

- Quale sistema di corriere sarà integrato con Adobe Commerce?

- Quale software fiscale sarà integrato con Adobe Commerce? (Esempio: Taxware)

- Da quale sistema verranno importati i dati dei prodotti in Adobe Commerce?

- Frequenza dei caricamenti dei dati dei prodotti importati?

- In quale sistema Adobe Commerce esporterà i dati dei prodotti?

- Frequenza dei caricamenti dei dati dei prodotti esportati?

- Da quale sistema verranno importati i dati in Adobe Commerce?

- Frequenza dei caricamenti dei dati dell’ordine importati?

- In quale sistema Adobe Commerce esporterà i dati degli ordini?

- Frequenza dei caricamenti dei dati dell’ordine esportati?

- Quale piattaforma di analisi viene utilizzata? (Esempi: Adobe Analytics, Google Analytics)

- Ci sarà il single sign-on e la condivisione sui social network? In caso affermativo, quali sono i social network?

- Esistono premi o programmi di fidelizzazione? C&#39;è qualche integrazione con i sistemi POS per i premi?

- Come vengono gestiti i resi dei prodotti? Il cliente deve registrare una richiesta di reso online?

- È necessario uno strumento di chat online? Serve un chatbot?

- Specificare il gateway di pagamento da utilizzare per il sito.

- Quale sistema di gestione degli ordini verrà integrato con Adobe Commerce? (Esempi: Microsoft Dynamics, SAP, Retail Pro)

- Quale sistema di gestione delle informazioni sui prodotti sarà integrato con Adobe Commerce? (Esempi: Akeneo, InRiver, Bluestone)

- Quale sistema di gestione delle relazioni con i clienti sarà integrato con Adobe Commerce? (Esempi: Hubspot, Salesforce, Klaviyo)

## Funzioni specifiche di Adobe Commerce

- Avrai bisogno di qualche tipo di test A/B?

- Quanti amministratori simultanei possono lavorare nel sistema?

- Permetterai a un cliente di ritirare gli articoli acquistati sul sito web in un negozio?

- Avrai pagine promozionali?

- Avrai dei banner di marketing?

- Riprodurre i video in una pagina CMS?

- Con quale frequenza verranno modificati o aggiornati i contenuti?

- Quale tipo di contenuto verrà caricato?

- Gli aggiornamenti dei contenuti verranno pianificati?

- Sarà necessario un sito Web di gestione temporanea dei contenuti?

- I clienti devono essere autorizzati a creare un account per il sito Web?

- Utilizzerai coupon di sconto univoci per le promozioni?

- Hai dei prezzi promozionali?

- Avrai coupon flessibili (possibilità di impostare per sito web, gruppo di clienti, tempo, categorie o prodotti)?

- Gli sconti in percentuale verranno offerti per singoli articoli?

- Quale tipo di funzionalità regalo sarà necessaria?

- Sarà necessaria la funzionalità dei programmi per i premi?

- Sarà richiesta la funzionalità della newsletter?

- Consentire a un cliente di visualizzare gli ordini passati e selezionare gli articoli da scambiare?

- Permetterai a un cliente di avviare l’annullamento di un ordine dal sito web?

- Permetterai a un cliente di avviare lo scambio di articoli dal sito Web?

- Sarà necessaria la convalida degli indirizzi in tempo reale?

- Consentirai a un cliente di avviare la restituzione degli articoli dal sito Web?

- Adobe Commerce emetterà una RMA di ritorno?

- Acquisire informazioni sul rimborso in Adobe Commerce?

- Richiedi il tracciamento degli ordini online per un cliente registrato?

- Richiedi il tracciamento degli ordini online per un cliente ospite?

- Eseguire l&#39;autorizzazione online e l&#39;acquisizione durante il posizionamento dell&#39;ordine?

- Autorizzazione con filtro antifrode durante il posizionamento dell’ordine con acquisizione ritardata

- Numero di giorni per ricevere il pagamento completo (non l&#39;autorizzazione)?

- Acquisire ed eseguire in caso di scadenza dell’autorizzazione?

- Authorize.net

- Braintree

- PayPal Express

- Credito store

- Biglietti regalo in plastica

- Punti premio

- &quot;Bill Me Later&quot; - più comunemente noto come &quot;Buy Now, Pay Later&quot; in quanto è immediatamente fatturato ma non ancora pagato

- Ci saranno prezzi di prodotto diversi su diversi siti web?

- Sarà necessaria la funzionalità per confrontare prodotti diversi?

- Quali tipi di prodotti venderai?

- Con quale frequenza verranno aggiunti nuovi prodotti?

- Con quale frequenza verranno aggiornati i prodotti?

- Con quale frequenza verranno create nuove categorie o sottocategorie?

- Sarà necessaria la funzionalità &quot;Classificazioni e recensioni&quot;?

- Permetterai ai clienti di consigliare un prodotto?

- Vendite: ordini, imposte, fatturati, spedizione, rimborsi, coupon, rapporti di liquidazione PayPal

- Carrello: Prodotti in carrelli, arti abbandonate

- Prodotti: Bestseller, prodotti ordinati, più visti, scorte basse, download

- Clienti: nuovi account, clienti per totale ordini, clienti per numero di ordini, segmenti di clienti, recensioni dei clienti

- Recensioni prodotti

- Tag: Clienti, prodotti, popolari

- Termini di ricerca

- Inviti: Generale, clienti, tasso di conversione ordini

- Sarà necessario Adobe Commerce per generare rapporti basati sui dati di utilizzo dei coupon?

- Sarà necessario Adobe Commerce per generare rapporti basati sui dati delle vendite?

- Saranno necessari rapporti Adobe Commerce personalizzati?

- Qual è la tua attuale strategia SEO (Search Engine Optimization)?

- Quale sarà la vostra nuova strategia SEO (Search Engine Optimization)?

- Quali sono i requisiti per la migrazione SEO (Search Engine Optimization)?

- Memorizzare i tassi fissi in Adobe Commerce?

- Consentire la spedizione parziale?

- Archiviare le informazioni di tracciabilità della spedizione in Adobe Commerce?

- Saranno necessarie regole di calcolo delle imposte per le aree geografiche nazionali?

- Saranno necessarie regole di calcolo delle imposte per le regioni internazionali?

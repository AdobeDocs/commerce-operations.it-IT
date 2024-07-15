---
title: Best practice per la gestione del catalogo
description: Scopri i consigli per la configurazione dei limiti del carrello e degli attributi del prodotto, l’impaginazione degli elenchi, le opzioni, le promozioni e le varianti.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Best practice per la gestione del catalogo

Le best practice per la gestione dei cataloghi qui descritte riguardano una serie di problemi, tra cui (ma non sono limitate a):

- Limiti del carrello
- Limiti delle categorie
- Attributi del prodotto
- Paginazione elenco prodotti
- Opzioni prodotto
- Varianti prodotto
- Promozioni

## Limiti del carrello

Per ottenere prestazioni ottimali, utilizza le seguenti linee guida per gestire i limiti del carrello per Adobe Commerce.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Riduci il numero di elementi nel carrello

Utilizza le seguenti strategie per gestire il numero di articoli del carrello

- Suddividere gli ordini in più ordini più piccoli con un numero di righe inferiore utilizzando la funzione [!UICONTROL Add Item by SKU].
- Aggiungi solo la logica personalizzata e la personalizzazione del carrello richieste per caricare un elenco di elementi.

## Limiti delle categorie

La configurazione di un numero elevato di categorie può influire sulle prestazioni.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Ridurre il numero di prodotti

Utilizza le seguenti strategie per ridurre il numero di categorie:

- Gestire funzioni univoche del prodotto tramite attributi e opzioni personalizzate
- Rimuovi categorie inattive
- Ottimizzare la profondità del catalogo nella navigazione

## Attributi del prodotto

La configurazione di troppi attributi di prodotto o di opzioni di attributi di prodotto può influire sulle prestazioni.

>[!NOTE]
>
>Gli attributi del prodotto specificano le funzioni che si applicano a livello globale a tutti i prodotti. Le opzioni dell’attributo del prodotto sono personalizzazioni per specificare le funzioni applicabili a prodotti specifici.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Riduci il numero di attributi

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati di prodotto nella vetrina:

- Utilizzare diversi modelli di prodotto (set di attributi) per prodotti diversi.
- Sfruttare opzioni personalizzate e prodotti complessi per la gestione delle varianti
- Riduci al minimo il numero di attributi ricercabili.
- Rimuovi le proprietà del prodotto non utilizzate.
- Archivia e gestisci attributi non correlati all’e-commerce in sistemi esterni di gestione dei prodotti (PMS).

### Riduci il numero di opzioni attributo

Per ottenere le migliori prestazioni durante la gestione dei prodotti dall’amministratore e il recupero dei dati di prodotto nella vetrina:

- Utilizza diversi meccanismi di variante per creare prodotti: prodotti complessi, opzioni personalizzate come origine di varianti di prodotto.
- Crea modelli di prodotto specifici con attributi di targeting e opzioni per evitare modelli di prodotto e contenitori di opzioni generalizzati.
- Gestisce un elenco delle opzioni di attributo effettive.
- Gestire le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

### Riduci il numero di set di attributi

Rimuovere i set di attributi di prodotto inutilizzati utilizzando MySQL.

#### Verifica la configurazione del set di attributi

1. [Connessione al database del sito](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Trovare il numero di set di attributi utilizzando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Rimuovere tutti i set di attributi inutilizzati.

### Potenziale impatto sulle prestazioni

La configurazione di molti **attributi di prodotto** aumenta le dimensioni del modello di prodotto per ciascun prodotto (struttura EAV) e la quantità di dati da recuperare. Questo aumento influisce sulle operazioni nei seguenti modi:

- Aumento del traffico delle query SQL correlate al recupero dei dati EAV e della quantità di dati elaborati, con conseguente riduzione della velocità effettiva del database
- Aumento significativo della dimensione degli indici Adobe Commerce e dell’indice di ricerca full-text
- Raggiungimento dei limiti rigidi di MySQL durante la creazione di un indice FLAT per modelli di prodotto di dimensioni eccessive e impossibilità di utilizzarlo

L’aumento dei dati di prodotto e delle dimensioni dell’indice può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più elevati per la maggior parte degli scenari di vetrina relativi alla navigazione del catalogo, alla ricerca (rapida e avanzata) e alla navigazione su più livelli.
- Le operazioni di gestione dei prodotti nell’amministratore subiscono un rallentamento significativo, che può causare timeout.
- È possibile bloccare la funzionalità Azioni di massa prodotto.
- I tempi di ricreazione degli indici per i cataloghi di medie e grandi dimensioni non possono essere eseguiti su base giornaliera a causa dei lunghi tempi di esecuzione.

La configurazione di molte **opzioni attributo** può influire sulle prestazioni del sito nei seguenti modi:

- Lunghi tempi di richiesta e rendering sui dettagli prodotto (PDP) e sulle pagine di categorie contenenti prodotti complessi.
- Il tempo di risposta per le operazioni di salvataggio dei prodotti dell’amministratore aumenta oltre gli obiettivi di prestazioni ottimali.
- Aumento del tempo di rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Opzioni prodotto

La configurazione di un numero eccessivo di opzioni prodotto per prodotto può influire sulle prestazioni.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Riduci il numero di opzioni

Utilizza le seguenti strategie per ridurre il numero di opzioni di prodotto per prodotto:

- Configura prodotti complessi e opzioni personalizzate come origine di varianti di prodotto.
- Invece di creare modelli di prodotto globali e contenitori di opzioni applicabili a tutti i prodotti, utilizza i set di attributi per creare modelli di prodotto specifici con attributi e opzioni di destinazione.
- Gestire le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

### Potenziale impatto sulle prestazioni

La configurazione di molte opzioni di prodotto aumenta la quantità di dati recuperati per ciascun prodotto su tutte le operazioni di lettura e scrittura, con conseguente:

- L&#39;aumento del traffico delle query SQL e le operazioni `JOIN` più pesanti aumentano la velocità effettiva del database.
- Sono state aumentate le dimensioni per gli indici Adobe Commerce e l’indice di ricerca full-text.

Gli aumenti elencati sopra possono influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più lunghi per la maggior parte degli scenari di vetrina relativi a prodotti contenenti molte opzioni negli attributi.
- Aumenti significativi del tempo necessario per completare le operazioni di gestione dei prodotti in Admin che possono causare timeout, in particolare per scenari relativi all’elenco degli attributi e al recupero della struttura, inclusa la gestione delle regole di promozione.
- Può bloccare azioni in blocco che completano operazioni di massa asincrone come l’importazione e l’esportazione e assegnare prezzi personalizzati a più prodotti in un catalogo condiviso.

## Paginazione elenco prodotti

La visualizzazione di un numero eccessivo di prodotti per pagina può influire sulle prestazioni.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Aggiornare la configurazione dell’elenco dei prodotti

Se hai troppi prodotti in una categoria, aggiorna la configurazione del catalogo della vetrina per disabilitare l&#39;opzione su **Consenti tutti i prodotti per pagina**.

Dopo aver disabilitato questa opzione, Adobe Commerce utilizza i controlli di paginazione della vetrina per gestire il numero di prodotti visualizzati nei componenti della vetrina. Per istruzioni, vedere [Configurare i controlli di impaginazione](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Limiti SKU prodotto

Configurare troppi SKU di prodotto può influire sulle prestazioni rallentando il recupero dei dati di prodotto e aumentando il tempo necessario per completare le operazioni o le indicizzazioni dell’amministratore.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Ridurre il numero di prodotti

Per ridurre il numero di prodotti (SKU), utilizza le seguenti strategie:

- Riduci al minimo i moltiplicatori:
   - Il consolidamento dei siti web riduce il moltiplicatore.
   - Utilizza funzioni di prodotto alternative per i prezzi personalizzati al posto dei moltiplicatori di cataloghi e gruppi di clienti condivisi.
   - Sia i gruppi di clienti che il catalogo condiviso fungono da moltiplicatori per il numero di SKU effettivi in un negozio.
- Ristrutturare il catalogo:
   - Riduci il numero di prodotti assegnati alle categorie.
   - Diminuisci il numero di SKU diminuendo il numero di siti web, gruppi di clienti, cataloghi condivisi, numero di prodotti o numero di opzioni di prodotto configurabili
- Puoi fornire più varianti di prodotto utilizzando opzioni personalizzate anziché creare prodotti separati.
- Tenendo conto del fatto che una SKU effettiva potrebbe includere una serie di potenziali permutazioni dei prezzi, poiché i prezzi possono essere specificati in modo diverso per ogni negozio o gruppo di clienti.
- Disattiva o rimuovi i componenti di sistema inutilizzati come i moduli. Consulta [Disinstallare i moduli](../../../installation/tutorials/uninstall-modules.md).
- Gestione dei prodotti in un sistema di gestione della piattaforma (PMS) esterno.

## Varianti prodotto

La configurazione di un numero eccessivo di varianti per prodotto può influire sulle prestazioni.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Riduci il numero di varianti

Per migliorare le prestazioni del sito, utilizza le seguenti strategie per ridurre il numero di varianti di prodotto:

- Ristruttura il catalogo distribuendo il numero di varianti tra i diversi prodotti.
- Rimuovere le opzioni di attributo configurabili non disponibili.
- Gestisci le varianti tramite funzionalità alternative come opzioni personalizzate, categorie, prodotti correlati, raggruppati e bundle.

### Potenziale impatto sulle prestazioni

Il superamento del numero consigliato di varianti di prodotto può influire sulle prestazioni del sito nei seguenti modi:

- Tempi lunghi di richiesta e rendering dei dettagli di prodotto e delle pagine di categorie contenenti prodotti complessi.
- È stato aumentato il tempo di risposta per completare le operazioni di salvataggio nell’amministratore.
- È stato aumentato il tempo per il rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Promozioni

Segui queste best practice per configurare vendite e promozioni per gli articoli in un carrello:

- **Regole di vendita (regole prezzo carrello)**
   - Gestisci e rimuovi le regole non utilizzate.
   - Aggiungi condizioni di regola rigide (come un filtro di attributi o categorie) per ottenere la corrispondenza più efficiente.
- **Coupon**
   - Rimuovere i coupon inutilizzati e scaduti.
   - Genera solo il numero di coupon necessari per soddisfare i requisiti della campagna.

### Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

### Potenziale impatto sulle prestazioni

Avere un numero di regole di prezzo del carrello superiore a quello massimo consigliato può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più rapidi quando i prodotti vengono aggiunti al carrello.
- È stato aumentato il tempo necessario per caricare ed eseguire il rendering del minicart.
- È stato aumentato il tempo per il rendering della pagina del carrello.
- È stato aumentato il tempo per il rendering del blocco **Totali** nella pagina Pagine di pagamento.

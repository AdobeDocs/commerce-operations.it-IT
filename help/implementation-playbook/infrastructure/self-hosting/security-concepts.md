---
title: Concetti di sicurezza di Adobe Commerce per l’hosting autonomo
description: Scopri le idee e i concetti di sicurezza e le best practice di self-hosting da considerare. Scopri concetti quali file system di sola lettura, scansione malware e molti altri argomenti da considerare durante l'hosting di adobe commerce.
landing-page-description: Scopri alcuni concetti e cose di sicurezza da considerare quando ospita Adobe Commerce da solo.
short-description: Scopri strategie e concetti di sicurezza per l’hosting autonomo di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 0d5c2d3ae44008142797c7ac91530a9df98ae004
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# Concetti di sicurezza

La sicurezza dovrebbe sempre essere una considerazione importante per qualsiasi cosa riguardi un progetto di e-commerce. Senza una forte posizione di sicurezza, la superficie che può essere attaccata è esponenzialmente più grande. I concetti e le idee presentati forniscono metodi comprovati per ridurre le vulnerabilità comuni tipicamente sfruttate.

I seguenti concetti non sono in alcun ordine particolare. Hanno lo scopo di fornire alcune idee e concetti da considerare. Molti sono gratuiti o richiederebbero una configurazione e una configurazione minime e un successivo monitoraggio. Ricercare questi argomenti al di fuori di questo tutorial per assicurarti di avere una conoscenza sufficientemente approfondita dei concetti presentati qui.

## File system di sola lettura

Il concetto di file system di sola lettura è stato preso in prestito da [Adobe Commerce su un’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Questo rimuove completamente un&#39;area importante utilizzata da un attore cattivo. Molti sfruttatori hanno approfittato della modifica di un file che si prevede si trovi nell’applicazione Commerce per evitare il rilevamento. Invece di crearne uno, l’attore errato modifica il contenuto di un file esistente per eseguire un’azione imprevista. Rendere il file system di sola lettura riduce notevolmente questo vettore di attacco.

## Utilizzare l’autenticazione a due fattori e i gestori di password

Non condividere mai le password. Ogni utente amministratore deve avere il proprio account con ACL appropriato. Assicurati che l’identificazione a due fattori non sia mai disabilitata o rimossa. Se fornisci l&#39;accesso dell&#39;amministratore a terze parti, assicurati che la password sia generata da un gestore di password e non sia mai riutilizzata.

## Scansioni malware

Le scansioni malware si trovano in genere da un provider di hosting che cerca di specializzarsi in Adobe Commerce. Questa libreria di malware e sfruttamenti noti è una lista sempre crescente man mano che vengono scoperte, testate e diagnosticate nuove minacce. Richiedi se il provider di hosting dispone di tale servizio e se può essere eseguito automaticamente o solo su richiesta. Ci sono anche servizi a cui puoi abbonarti che possono utilizzare la loro libreria di exploit noti per controllare costantemente la tua applicazione commerciale per gli utilizzi. Alcuni di questi sono solo esterni, alcuni possono essere aggiunti all&#39;infrastruttura per fornire una scansione profonda interna di tutte le cartelle, i file e persino il database. Ci sono alcuni fornitori con anni di esperienza in questo ambito, da Sansec.io a Sucuri e naturalmente MageReport. Alcuni sono gratuiti e altri sono accompagnati da un costo associato. Sapere che questo è disponibile e avere una conversazione attenta con il tuo architetto Adobe Commerce e il team DevOps ti garantirà la soluzione giusta.

## Strumento di analisi a livello di sito per Commerce

La [Strumento di analisi a livello di sito](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} è uno strumento proattivo self-service e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l’operabilità dell’installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24 per identificare potenziali problemi e migliorare la visibilità sulle configurazioni di sicurezza, salute e applicazioni del sito. Consente di ridurre i tempi di risoluzione e migliorare la stabilità e le prestazioni del sito.

## Abilita e verifica le impostazioni per Registrazione azioni amministratore

Questo si può trovare dopo aver effettuato l’accesso all’amministratore Adobe Commerce e aver navigato in Stores > Configuration > Advanced > Admin > Admin Actions Logging (Archivia > Configurazione > Amministratore > Registrazione azioni). Questo fornisce un elenco degli eventi monitorati e registrati. È utile quando si esegue un&#39;analisi forense su un sito sfruttato, se il sospetto è che hanno avuto accesso all&#39;amministratore Commerce. La registrazione e il report possono essere utili per vedere quali eventi ha eseguito il cattivo attore. Se una registrazione di azioni di amministrazione è disabilitata, significa che qualcuno potrebbe averle disattivate per la copertura, rimuovi la registrazione quando esegui determinate azioni.

## Server Bastion per l&#39;accesso ssh

Questo è più difficile da spiegare che la maggior parte degli argomenti del tutorial Security Concepts. L&#39;idea di base è quella di fornire un server che funga da intermediario per l&#39;accesso ssh. In questo modo, i server di produzione non consentono mai connessioni ssh esterne. Puoi creare questo server bastion e utilizzare una maschera IP locale per garantire che solo i server designati siano autorizzati a utilizzare SSH.

## Esamina ruoli e autorizzazioni ACL

A ogni utente amministratore di Adobe Commerce viene assegnato un ruolo ACL. Questo ruolo deve essere creato per fornire solo la funzionalità necessaria per eseguire il processo. I ruoli ACL devono essere valutati spesso, per garantire che non forniscano più autorità del necessario. Se necessario, crea molti ruoli ACL con responsabilità. Se l&#39;accesso è concesso a terzi per qualche motivo, è opportuno disattivarlo il prima possibile. Chiedi loro per quanto tempo hanno assolutamente bisogno di accedere e impostare una data di scadenza automatica quando crei il loro utente amministratore.

## Controllare frequentemente gli utenti amministratori e l’accesso degli utenti SSH

Per rilevare la creazione di utenti amministratori indesiderati o non autorizzati, l&#39;elenco degli utenti amministratori deve essere controllato frequentemente. Una buona regola è quella di verificare chi ha accesso mensile SSH e amministratore all&#39;applicazione Adobe Commerce. Se vengono rilevati nuovi utenti, disattiva il loro account e segui le politiche e le procedure aziendali relative a tale incidente. È più facile ripristinare l&#39;accesso di un utente che di recuperare da un exploit.

## Pulizia del database

Limitare l’accesso ai dati di produzione. Questi membri del gruppo dovrebbero avere la possibilità di estrarre le basi di dati di produzione e pulirle di dati reali. Se la rimozione dei dati è un’opzione, tronca le tabelle appropriate come ordini, preventivi e clienti. Tuttavia, a volte si desidera l&#39;insieme completo di dati, ma i valori possono essere resi anonimi. Ciò è in genere vero in un ambiente di staging. È utile anche prima degli aggiornamenti. Grazie al volume reale di dati, ma con l’anonimizzazione è possibile testare e convalidare il tempo necessario per eseguire correttamente un’implementazione per l’aggiornamento. Se hai un set limitato di dati, puoi sottovalutare il processo di aggiornamento e la tempistica.

+++Esempio casuale di informazioni sul cliente Ecco un esempio per come modificare l’indirizzo e-mail del cliente con una stringa casuale e tutti i campi nome e ultimo mane in alcune tabelle standard in cui Adobe Commerce memorizza i dati. **Ricordare di controllare tutte le tabelle per i dati sensibili, questo elenco non è tutto incluso nelle tabelle che possono memorizzare i dati dei clienti**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++È anche possibile troncare le tabelle invece di cercare di anonimizzare

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Rimuovi completamente le informazioni Esempio: qui è un esempio per rimuovere tutti gli ordini, le quotazioni, le note di credito e altro ancora prima del lancio o per un ambiente di sviluppo inferiore

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Usa variabili di ambiente

[!BADGE Solo Adobe Commerce su cloud]{type=Informative}

L’utilizzo delle variabili di ambiente consente di impostare alcuni valori che possono e devono essere modificati per ogni ambiente. Ad esempio, potresti voler avere un URL amministratore diverso per ogni ambiente. Impostando questo valore come variabile di ambiente, puoi configurarlo e anche fare riferimento rapido a tale valore dall’interfaccia utente di Cloud quando necessario.

Per ulteriori informazioni su questo argomento, consulta l’Experience League [Variabili dell’ambiente dell’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Strumenti di scansione della vulnerabilità del software

La pipeline CI/CD può essere uno strumento potente e consente di automatizzare alcune attività. In particolare, l&#39;opportunità per uno sviluppatore di eseguire il commit del codice che può essere sfruttabile è sempre una possibilità reale. Le revisioni del codice peer normalmente catturano tali elementi, ma siccome è un umano, gli errori capitano. La scansione automatica del codice aiuta a ridurre le opportunità di vulnerabilità impreviste in una nuova funzione introdotta. Questi strumenti possono anche essere implementati per bloccare l&#39;unione del codice nella codebase live. Ci sono molti modi e strumenti per offrire sicurezza del codice automatizzata e scansioni di qualità. Possono esistere solidi strumenti di sviluppo personalizzati, ma richiedono aggiornamenti e regolazioni costanti. Un&#39;alternativa è quella di applicare strumenti proattivamente aggiornati come synk.io e la finestra di ispezione del codice di Amazon.

## Firewall applicazione Web

Un firewall per applicazioni web o un WAF utilizzato spesso quando si parla con DevOps o un provider di hosting.

I firewall per applicazioni web (WAF) impediscono l’accesso a siti e reti da parte di traffico dannoso filtrando il traffico in base a un insieme di regole di sicurezza. Il traffico che attiva una delle regole viene bloccato prima che possa danneggiare i siti o la rete.

Adobe Commerce cloud WAF fornisce una policy WAF con un set di regole progettato per proteggere le applicazioni web Adobe Commerce da una vasta gamma di attacchi. Se scegli un’opzione di self-hosting, trova un WAF e configura le regole, sei tu responsabile. Alcuni provider di hosting e WAF hanno un set generico di regole che sono un buon inizio, tuttavia aspettarsi qualche lavoro per ottenere cose funzionanti per il tuo progetto.

Il WAF esamina il traffico web e amministrativo per identificare qualsiasi attività sospetta. Valuta il traffico GET e POST (chiamate API HTTP) e applica il set di regole per determinare quale traffico bloccare. Il WAF può bloccare un&#39;ampia varietà di attacchi, tra cui attacchi di iniezione SQL, attacchi di scripting tra siti, attacchi di filtrazione dei dati e violazioni del protocollo HTTP.

Come servizio basato su cloud, il WAF non richiede hardware o software per l&#39;installazione o la manutenzione. Infine, un partner tecnologico esistente, fornisce il software e le competenze necessarie. Il WAF ad alte prestazioni, sempre attivo, risiede in ogni nodo di cache attraverso la rete di consegna globale di Flast.

Per ulteriori informazioni sul WAF su Adobe Commerce on cloud fornite da Flast, leggere il [Domande frequenti sulla Knowledge Base di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}

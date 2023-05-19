---
title: Concetti di sicurezza di Adobe Commerce per hosting autonomo
description: Scopri le idee e i concetti di sicurezza di self-hosting e le best practice da considerare. Scopri concetti come il file system di sola lettura, la scansione del malware e molti altri argomenti da considerare durante l’hosting di adobe commerce.
landing-page-description: Scopri alcuni concetti e aspetti di sicurezza da considerare quando ospiti Adobe Commerce da solo.
short-description: Scopri le strategie e i concetti di sicurezza per ospitare te stesso Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# Concetti di sicurezza

La sicurezza deve sempre essere una considerazione forte per qualsiasi cosa relativa a un progetto di e-commerce. Senza una forte posizione di sicurezza, la superficie che può essere attaccata è esponenzialmente più grande. I concetti e le idee presentati forniscono metodi collaudati per ridurre le vulnerabilità comuni tipicamente sfruttate.

I concetti seguenti non sono in alcun ordine particolare. Hanno lo scopo di fornire alcune idee e concetti da considerare. Molte sono gratuite o richiedono un minimo di configurazione e monitoraggio. Esci da questa esercitazione per approfondire la conoscenza dei concetti presentati qui.

## File system di sola lettura

Il concetto di file system di sola lettura è stato preso in prestito da [Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Questo rimuove completamente un&#39;area importante utilizzata da un attore cattivo. Molti exploit hanno approfittato dell’alterazione di un file che dovrebbe trovarsi nell’applicazione Commerce per evitare il rilevamento. Invece di crearne uno, l’attore danneggiato modifica il contenuto di un file esistente per eseguire un’azione imprevista. Rendendo il file system di sola lettura si riduce notevolmente questo vettore di attacco.

## Utilizzare l&#39;autenticazione a DUE fattori e i gestori di password

Non condividere mai le password. Ogni utente amministratore deve disporre di un proprio account con l’ACL corretto. Assicurarsi che l&#39;identificazione dei due fattori non venga mai disattivata o rimossa. Se fornisci all’amministratore l’accesso a una terza parte, assicurati che la password sia generata da un gestore di password e non venga mai riutilizzata.

## Scansioni malware

Le scansioni malware si trovano in genere da un provider di hosting che tenta di specializzarsi in Adobe Commerce. Questa libreria di malware e exploit noti è un elenco in continua crescita, in quanto vengono scoperte, sperimentate e diagnosticate nuove minacce. Chiedi se il provider di hosting dispone di tale servizio e se può essere eseguito automaticamente o solo su richiesta. Ci sono anche servizi a cui puoi abbonarti che possono utilizzare la loro libreria di exploit noti per controllare costantemente la tua applicazione commerce per gli exploit. Alcuni sono solo esterni, altri possono essere aggiunti all’infrastruttura per fornire una scansione approfondita interna di tutte le cartelle, i file e persino il database. Ci sono alcuni fornitori con anni di esperienza in questo settore, da Sansec.io a Sucuri e naturalmente MageReport. Alcune sono gratuite, altre hanno un costo associato. Sapere che è disponibile e parlare con il tuo architetto Adobe Commerce e il team DevOps ti garantiranno la soluzione giusta.

## Strumento di analisi a livello di sito per Commerce

Il [Strumento di analisi a livello di sito](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} è uno strumento self-service proattivo e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l’operabilità dell’installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24, 7 giorni su 7 per identificare potenziali problemi e migliorare la visibilità delle configurazioni di salute, sicurezza e applicazioni del sito. Consente di ridurre i tempi di risoluzione e di migliorare la stabilità e le prestazioni del sito.

## Abilita e verifica le impostazioni per la registrazione delle azioni amministratore

Puoi accedere a questa pagina dopo aver effettuato l’accesso all’amministrazione di Adobe Commerce e aver selezionato Archivi > Configurazione > Avanzate > Amministratore > Registrazione azioni amministratore. Fornisce un elenco di eventi che vengono monitorati e registrati. È utile quando si eseguono analisi forensi su un sito sfruttato, se il sospetto è che abbiano ottenuto l’accesso all’amministratore di Commerce. Questa registrazione e questo rapporto possono essere utili per vedere quali eventi ha eseguito l’attore errato. Se la registrazione di eventuali azioni dell’amministratore è disabilitata, ciò indica che qualcuno potrebbe averla disabilitata per la copertura, rimuovi la registrazione quando esegui determinate azioni.

## Bastion Server per accesso ssh

È difficile spiegare che la maggior parte degli argomenti dell’esercitazione sui concetti di sicurezza. L’idea di base è fornire un server che funga da intermediario per l’accesso a ssh. In questo modo, i server di produzione non consentono mai connessioni ssh esterne. Puoi creare questo bastion server e utilizzare una maschera IP locale per garantire che solo i server designati siano autorizzati a usare SSH in tali server.

## Rivedi ruoli e autorizzazioni ACL

A ogni utente amministratore di Adobe Commerce viene assegnato un ruolo ACL. Questo ruolo deve essere creato per fornire solo la funzionalità che deve eseguire il processo. I ruoli ACL devono essere valutati spesso, per garantire che non forniscano più autorità del necessario. Se necessario, crea molti ruoli ACL con responsabilità. Se per qualche motivo l’accesso è concesso a terzi, questi dovrebbero essere disattivati il prima possibile. Chiedi loro per quanto tempo hanno bisogno di accedere e imposta una data di scadenza automatica durante la creazione del loro utente amministratore.

## Controlla frequentemente gli utenti amministratori e l’accesso degli utenti SSH

Per rilevare la creazione di utenti amministratori indesiderati o non autorizzati, è necessario controllare frequentemente l’elenco degli utenti amministratori. Una buona regola è verificare chi dispone di accesso mensile SSH e amministratore all’applicazione Adobe Commerce. Se vengono rilevati nuovi utenti, disabilita il tuo account e segui la politica e le procedure aziendali relative a tali incidenti. È più facile ripristinare l’accesso di un utente che ripristinarlo da un exploit.

## Pulizia del database

Limita l’accesso ai dati di produzione. Questi team devono avere la capacità di estrarre i database di produzione e ripulirli dai dati reali. Se è possibile rimuovere i dati, troncare le tabelle appropriate, ad esempio ordini, preventivi e clienti. Tuttavia, a volte può essere utile il set completo di dati, ma i valori possono essere resi anonimi. In genere, ciò si verifica in un ambiente di staging. È utile anche prima degli aggiornamenti. Grazie alla disponibilità del volume reale di dati, ma con anonimizzazione, è possibile testare e convalidare il tempo necessario per eseguire correttamente una distribuzione per l’aggiornamento. Se si dispone di un set limitato di dati, è possibile sottostimare il processo di aggiornamento e la tempistica.

+++Esempio di casualizzazione delle informazioni sul cliente Ecco un esempio per cambiare l’indirizzo e-mail del cliente con una stringa casuale e tutti i campi nome e cognome in alcune tabelle standard in cui Adobe Commerce memorizza i dati. **Ricorda di controllare la presenza di dati sensibili in tutte le tabelle; questo elenco non include tutte le tabelle che possono memorizzare i dati dei clienti**

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


+++È anche possibile troncare le tabelle invece di cercare di rendere anonime

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

+++Rimuovi completamente le informazioni di esempio Di seguito è riportato un esempio per la rimozione di tutti gli ordini, preventivi, note di credito e altro ancora prima del lancio o per un ambiente di sviluppo inferiore.

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

## Utilizzare le variabili di ambiente

[!BADGE Adobe Commerce solo su cloud]{type=Informative}

L’utilizzo delle variabili di ambiente consente di impostare alcuni valori che possono e devono essere modificati per ogni ambiente. Ad esempio, potrebbe essere utile disporre di un URL amministratore diverso per ogni ambiente. Impostando questo valore come variabile di ambiente, puoi configurarlo e, se necessario, anche fare riferimento rapidamente a tale valore dall’interfaccia utente di Cloud.

Per ulteriori informazioni su questo argomento, consulta l’Experience League [Variabili di ambiente di Commerce su infrastruttura Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Strumenti di scansione delle vulnerabilità software

La pipeline CI/CD può essere uno strumento utile per automatizzare alcune attività. In particolare, la possibilità per uno sviluppatore di eseguire il commit di codice che potrebbe essere sfruttabile è sempre una possibilità reale. Le revisioni dei codici tra pari normalmente rilevano tali elementi, ma poiché si tratta di un elemento umano, possono verificarsi errori. La scansione automatica del codice aiuta a ridurre le opportunità di vulnerabilità impreviste in una funzione appena introdotta. Questi strumenti possono anche essere implementati per bloccare l’unione di codice nella base di codice live. Esistono molti modi e strumenti per offrire sicurezza automatica del codice e controlli di qualità. Possono essere disponibili solidi strumenti personalizzati, ma richiedono aggiornamenti e regolazioni costanti. In alternativa, puoi applicare strumenti aggiornati in modo proattivo, come synk.io e l’ispettore del codice di Amazon.

## Firewall applicazione Web

Un web application firewall o WAF, come viene spesso utilizzato quando si parla con DevOps o un provider di hosting.

I Web Application Firewall (WAF) impediscono al traffico dannoso di entrare in siti e reti filtrando il traffico in base a una serie di regole di sicurezza. Il traffico che attiva una qualsiasi delle regole viene bloccato prima che possa danneggiare i siti o la rete.

Adobe Commerce Cloud WAF fornisce una policy WAF con un set di regole progettato per proteggere le applicazioni web Adobe Commerce da un’ampia gamma di attacchi. Se scegli un’opzione di hosting autonomo, puoi trovare un WAF e configurare le regole. Alcuni provider di hosting e provider WAF dispongono di un set generico di regole che rappresentano un buon punto di partenza, tuttavia si aspetta un po’ di lavoro per far funzionare le cose per il progetto.

Il WAF esamina il traffico web e di amministrazione per identificare eventuali attività sospette. Valuta il traffico GET e POST (chiamate API HTTP) e applica il set di regole per determinare quale traffico bloccare. La WAF può bloccare un&#39;ampia varietà di attacchi, tra cui attacchi SQL injection, attacchi cross-site scripting, attacchi di exfiltrazione dei dati e violazioni del protocollo HTTP.

In quanto servizio basato su cloud, WAF non richiede hardware o software per l&#39;installazione o la manutenzione. Fastly, un partner tecnologico esistente, fornisce il software e le competenze necessarie. Le loro prestazioni elevate, WAF sempre attivo, risiedono in ogni nodo di cache all’interno della rete di distribuzione globale di Fastly.

Per ulteriori informazioni sulla WAF in Adobe Commerce on cloud fornite da Fastly, consulta la sezione [Domande frequenti sulla Knowledge Base di Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}

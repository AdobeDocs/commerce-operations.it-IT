---
title: Ripristina database diviso
description: Ripristino dell'implementazione di un database diviso obsoleta in un'unica implementazione di database.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Ripristina da database diviso

{{ee-only}}

Per i clienti Adobe Commerce che hanno implementato [Database diviso](multi-master.md), l&#39;argomento seguente descrive come ripristinare o eseguire la migrazione a un singolo database. Consigliamo agli esercenti Adobe Commerce che attualmente utilizzano il database diviso e di pianificare l’aggiornamento alla versione 2.4.2 e successive di rivedere questi passaggi, nonché la nostra [annuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sull&#39;eliminazione pianificata del database diviso.

Il ripristino da un database diviso a un singolo database comporta la creazione di backup `magento_quote` e `magento_sales` database prima di caricarli nel singolo `magento_main` database.

In questo esempio, effettuiamo l&#39;accesso a tutti e tre i database installati sullo stesso host (`magento2-mysql`) come utente &quot;root&quot;. È necessario sostituire questi valori con i valori appropriati per i database.

1. Crea un backup del `magento_quote` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Crea un backup del `magento_sales` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Carica il `magento_quote` nel database `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Carica il `magento_sales` nel database `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Rilascia `magento_sales` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Rilascia `magento_quote` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Rimuovi la configurazione di distribuzione per `checkout` e `sales` in `connections` e `resources` sezioni `env.php` file.
1. Ripristina chiavi esterne:

   ```bash
   bin/magento setup:upgrade
   ```

## Verificare il lavoro

Per verificare che l’implementazione del database singolo funzioni correttamente, esegui le seguenti attività e verifica che i dati vengano aggiunti al `magento_main` tabelle di database utilizzando uno strumento di database come [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Verifica che le chiavi esterne siano state ripristinate. Ad esempio, il `QUOTE_STORE_ID_STORE_STORE_ID` nella `quote` tabella del database.
1. Verifica che i clienti possano effettuare ordini dalla vetrina.
1. Verificare che gli ordini creati prima di ripristinare il database suddiviso in un singolo database siano disponibili in Amministratore.

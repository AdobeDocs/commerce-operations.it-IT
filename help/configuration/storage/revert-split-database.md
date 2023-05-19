---
title: Ripristina database diviso
description: Ripristino da un’implementazione di database suddiviso obsoleta a un’implementazione di database singola.
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Ripristina da database suddiviso

{{ee-only}}

Per i clienti Adobe Commerce che hanno implementato [Dividi database](multi-master.md), nell&#39;argomento seguente viene descritto come ripristinare o eseguire la migrazione a un singolo database. Consigliamo ai commercianti di Adobe Commerce che attualmente utilizzano il database suddiviso di pianificare l’aggiornamento alla versione 2.4.2 e di rivedere questi passaggi, nonché i [annuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sulla deprecazione pianificata di Dividi database.

Il ripristino da un database diviso a un singolo database comporta la creazione di backup del `magento_quote` e `magento_sales` prima di caricarli nel singolo `magento_main` database.

In questo esempio, effettuiamo l&#39;accesso a tutti e tre i database, installati sullo stesso host (`magento2-mysql`) come utente &quot;root&quot;. È necessario sostituire questi valori con i valori appropriati per i database.

1. Crea un backup del `magento_quote` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Crea un backup del `magento_sales` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Carica `magento_quote` database in `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Carica `magento_sales` database in `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Rilascia il `magento_sales` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Rilascia il `magento_quote` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Rimuovi la configurazione di distribuzione per `checkout` e `sales` nel `connections` e `resources` sezioni del `env.php` file.
1. Ripristina chiavi esterne:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifica il tuo lavoro

Per verificare il corretto funzionamento dell’implementazione di un singolo database, esegui le seguenti attività e verifica che i dati vengano aggiunti al `magento_main` tabelle di database utilizzando uno strumento di database come [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Verificare che le chiavi esterne siano state ripristinate. Ad esempio, il `QUOTE_STORE_ID_STORE_STORE_ID` chiave nella `quote` tabella di database.
1. Verifica che i clienti possano effettuare ordini dalla vetrina.
1. Verificare che gli ordini creati prima di ripristinare il database suddiviso in un singolo database siano disponibili in Amministrazione.

---
title: Ripristina database diviso
description: Ripristino da un’implementazione di database suddiviso obsoleta a un’implementazione di database singola.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Ripristina da database suddiviso

{{ee-only}}

Per i clienti Adobe Commerce che hanno implementato [Dividi database](multi-master.md), il seguente argomento descrive come ripristinare o eseguire la migrazione a un singolo database. È consigliabile che i commercianti di Adobe Commerce che attualmente utilizzano il database suddiviso pianifichino l&#39;aggiornamento alla versione 2.4.2 e versioni successive rivedano questi passaggi, nonché il nostro [annuncio](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sulla prevista rimozione di Split Database.

Il ripristino da un database diviso a un singolo database comporta la creazione di backup dei database `magento_quote` e `magento_sales` prima di caricarli nel singolo database `magento_main`.

In questo esempio, si accede a tutti e tre i database, installati sullo stesso host (`magento2-mysql`) dell&#39;utente &quot;root&quot;. È necessario sostituire questi valori con i valori appropriati per i database.

1. Creare un backup del database `magento_quote`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Creare un backup del database `magento_sales`:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Caricare il database `magento_quote` nel database `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Caricare il database `magento_sales` nel database `magento_main`:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Eliminare il database `magento_sales`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Eliminare il database `magento_quote`:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Rimuovere la configurazione di distribuzione per `checkout` e `sales` nelle sezioni `connections` e `resources` del file `env.php`.
1. Ripristina chiavi esterne:

   ```bash
   bin/magento setup:upgrade
   ```

## Verifica il tuo lavoro

Per verificare che l&#39;implementazione di un singolo database funzioni correttamente, eseguire le attività seguenti e verificare che i dati vengano aggiunti alle tabelle del database `magento_main` utilizzando uno strumento di database come [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Verificare che le chiavi esterne siano state ripristinate. Ad esempio, la chiave `QUOTE_STORE_ID_STORE_STORE_ID` nella tabella del database `quote`.
1. Verifica che i clienti possano effettuare ordini dalla vetrina.
1. Verificare che gli ordini creati prima di ripristinare il database suddiviso in un singolo database siano disponibili in Amministrazione.

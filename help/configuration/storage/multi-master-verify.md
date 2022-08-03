---
title: Verificare il database diviso
description: Scopri come verificare il corretto funzionamento di una configurazione di database con suddivisione Commerce.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Verificare il database diviso

{{ee-only}}

{{deprecate-split-db}}

Dopo la configurazione, i database master sono configurati come segue:

- Database Commerce principale: 369 tabelle
- Commerce [preventivo](https://glossary.magento.com/quote) database: 11 tabelle
- Database vendite Commerce: 55 tabelle

Per verificare che i database suddivisi funzionino correttamente, eseguire le operazioni seguenti e verificare che i dati vengano aggiunti alle tabelle del database utilizzando uno strumento di database come [phpmyadmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

| Cosa verificare | Come verificare |
| -------------- | ------------- |
| database delle virgolette in corso | Aggiungi elementi a un carrello. Verifica che le righe siano state aggiunte al database delle offerte `quote`, `quote_address`e `quote_item` tabelle. |
| database di vendita in corso | Completare un ordine (qualsiasi metodo di pagamento, incluso assegno/ordine monetario). Verifica che le righe siano state aggiunte al database di vendita `sales_order_address`, `sales_order_item`e `sales_order_payment` tabelle. |

>[!WARNING]
>
>È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell’istanza di database principale. La [`magento setup:backup --db`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html) Le opzioni di comando e amministratore non consentono di eseguire il backup delle tabelle aggiuntive.

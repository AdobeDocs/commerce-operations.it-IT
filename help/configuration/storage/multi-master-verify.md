---
title: Verificare il database diviso
description: Scopri come verificare il corretto funzionamento di una configurazione di database con suddivisione Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Verificare il database diviso

{{ee-only}}

{{deprecate-split-db}}

Dopo la configurazione, i database master sono configurati come segue:

- Database Commerce principale: 369 tabelle
- Database delle virgolette commerciali: 11 tabelle
- Database vendite Commerce: 55 tabelle

Per verificare che i database suddivisi funzionino correttamente, eseguire le operazioni seguenti e verificare che i dati vengano aggiunti alle tabelle del database utilizzando uno strumento di database come [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Cosa verificare | Come verificare |
| -------------- | ------------- |
| database delle virgolette in corso | Aggiungi elementi a un carrello. Verifica che le righe siano state aggiunte al database delle offerte `quote`, `quote_address`e `quote_item` tabelle. |
| database di vendita in corso | Completare un ordine (qualsiasi metodo di pagamento, incluso assegno/ordine monetario). Verifica che le righe siano state aggiunte al database di vendita `sales_order_address`, `sales_order_item`e `sales_order_payment` tabelle. |

>[!WARNING]
>
>È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell’istanza di database principale. La [`magento setup:backup --db`](../../installation/tutorials/backup.md) Le opzioni di comando e amministratore non consentono di eseguire il backup delle tabelle aggiuntive.

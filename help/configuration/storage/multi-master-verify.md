---
title: Verifica database diviso
description: Scopri come verificare il corretto funzionamento di una configurazione di database diviso di Commerce.
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verifica database diviso

{{ee-only}}

{{deprecate-split-db}}

Dopo la configurazione, i database master vengono configurati come segue:

- Database Commerce principale: 369 tabelle
- Database delle offerte Commerce: 11 tabelle
- Database vendite Commerce: 55 tabelle

Per verificare che i database suddivisi funzionino correttamente, eseguire le operazioni seguenti e verificare che i dati vengano aggiunti alle tabelle del database utilizzando uno strumento di database come [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Cosa verificare | Come verificare |
| -------------- | ------------- |
| il database delle offerte funziona | Aggiungi articoli al carrello. Verificare che le righe siano state aggiunte al database delle offerte `quote`, `quote_address`, e `quote_item` tabelle. |
| il database delle vendite funziona | Completa un ordine (qualsiasi metodo di pagamento, compresi assegni/vaglia postale). Verificare che le righe siano state aggiunte al database delle vendite `sales_order_address`, `sales_order_item`, e `sales_order_payment` tabelle. |

>[!WARNING]
>
>È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell’istanza di database principale. Il [`magento setup:backup --db`](../../installation/tutorials/backup.md) nelle opzioni Command e Admin non viene eseguito il backup delle tabelle aggiuntive.

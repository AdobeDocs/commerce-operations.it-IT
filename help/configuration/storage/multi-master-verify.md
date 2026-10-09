---
title: Verifica database diviso
description: Scopri come verificare il corretto funzionamento di una configurazione di database diviso Commerce.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%
---
# Verifica database diviso

{{ee-only}}

{{deprecate-split-db}}

Dopo la configurazione, i database master vengono configurati come segue:

- Database principale di Commerce: 369 tabelle
- Database delle offerte Commerce: 11 tabelle
- Database vendite Commerce: 55 tabelle

Per verificare che i database suddivisi funzionino correttamente, eseguire le attività seguenti e verificare che i dati vengano aggiunti alle tabelle del database utilizzando uno strumento di database come [phpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Cosa verificare | Come verificare |
| -------------- | ------------- |
| il database delle offerte funziona | Aggiungi articoli al carrello. Verificare che siano state aggiunte righe alle tabelle `quote`, `quote_address` e `quote_item` del database delle offerte. |
| il database delle vendite funziona | Completa un ordine (qualsiasi metodo di pagamento, compresi assegni/vaglia postale). Verificare che siano state aggiunte righe alle tabelle `sales_order_address`, `sales_order_item` e `sales_order_payment` del database delle vendite. |

>[!WARNING]
>
>È necessario eseguire manualmente il backup delle due istanze di database aggiuntive. Commerce esegue il backup solo dell&#39;istanza di database principale. Il comando [`magento setup:backup --db`](../../installation/tutorials/backup.md) e le opzioni Admin non eseguono il backup delle tabelle aggiuntive.

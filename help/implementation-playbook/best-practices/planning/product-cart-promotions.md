---
title: Best practice per la configurazione delle promozioni
description: Scopri le best practice per configurare le regole di vendita e i codici coupon per ottimizzare le prestazioni di Commerce Store.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione delle promozioni

Per ottenere le migliori prestazioni, segui queste best practice per configurare vendite e promozioni per gli articoli nel carrello:

- **Regole di vendita (regole del prezzo del carrello)**- Configura non più di 1000 regole di prezzo del carrello per tutti i siti web
   - Gestione e rimozione delle regole non utilizzate.
   - Aggiungi condizioni di regole rigide (come filtro di attributi o categorie) per la corrispondenza più efficiente.
- **Coupon**—
   - Verifica che il numero totale di coupon nel database sia inferiore a 250.000.
   - Rimuovere i coupon inutilizzati e scaduti.
   - Genera solo il numero di coupon necessari per soddisfare i requisiti della campagna.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Effetti potenziali sulle prestazioni

Avere più del numero massimo consigliato di regole di prezzo del carrello o coupon può influenzare le prestazioni del sito nei seguenti modi:

- Tempo di risposta aumentato quando i prodotti vengono aggiunti al carrello.
- Maggiore tempo per caricare ed eseguire il rendering del minicart.
- Maggiore tempo per il rendering della pagina del carrello.
- Maggiore tempo di rendering del **Totali** nella pagina Pagamento.
- L&#39;applicazione dei coupon può richiedere più di 2 secondi.

## Informazioni aggiuntive

- [Informazioni su campagne e promozioni di marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Regole del prezzo del carrello](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Esercitazione: Creare una regola del prezzo del carrello](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Codici coupon](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce sull’infrastruttura cloud: Best practice per la configurazione dell’archivio](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)

---
title: Best practice per la configurazione delle promozioni
description: Scopri le best practice per configurare regole di vendita e codici coupon per ottimizzare le prestazioni di Commerce Store.
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Best practice per la configurazione delle promozioni

Per ottenere prestazioni ottimali, segui queste best practice per configurare vendite e promozioni per gli articoli in un carrello:

- **Regole di vendita (regole prezzo carrello)**-Configurare non più di 1000 regole di prezzo del carrello per tutti i siti Web
   - Gestisci e rimuovi le regole non utilizzate.
   - Aggiungi condizioni di regola rigide (come un filtro di attributi o categorie) per ottenere la corrispondenza più efficiente.
- **Coupon**—
   - Verificare che il numero totale di coupon nel database sia inferiore a 250.000.
   - Rimuovere i coupon inutilizzati e scaduti.
   - Genera solo il numero di coupon necessari per soddisfare i requisiti della campagna.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Potenziali impatti sulle prestazioni

Avere un numero di regole di prezzo del carrello superiore a quello massimo consigliato può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più rapidi quando i prodotti vengono aggiunti al carrello.
- È stato aumentato il tempo necessario per caricare ed eseguire il rendering del minicart.
- È stato aumentato il tempo per il rendering della pagina del carrello.
- È stato aumentato il tempo di rendering del **Totali** nella pagina Pagamento.
- L’applicazione dei coupon può richiedere più di 2 secondi.

## Informazioni aggiuntive

- [Informazioni sulle campagne e le promozioni di marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Regole prezzo carrello](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: creare una regola per il prezzo del carrello](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Codici coupon](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce sull’infrastruttura cloud: best practice per la configurazione dello store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)

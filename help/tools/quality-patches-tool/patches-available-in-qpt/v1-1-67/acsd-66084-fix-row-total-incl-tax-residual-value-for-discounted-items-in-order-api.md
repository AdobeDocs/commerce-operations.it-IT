---
title: 'ACSD-66084: "row_total_incl_tax" restituisce quasi zero invece di 0,00 per gli elementi completamente scontati nell’API dell’ordine'
description: Applica la patch ACSD-66084 per risolvere il problema Adobe Commerce per cui "row_total_incl_tax" restituiva un valore residuo vicino a zero invece di 0,00 per gli elementi completamente scontati nella risposta API dell’ordine.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 951738a4c671ed6fcc47b2a928d2110c78763d26
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-66084: `row_total_incl_tax` restituisce quasi zero invece di 0,00 per gli elementi completamente scontati nell&#39;API dell&#39;ordine

La patch ACSD-66084 risolve il problema per cui `row_total_incl_tax` viene restituito come valore residuo vicino a zero nella risposta API dell&#39;ordine anziché 0,00 per gli elementi completamente scontati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66084. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`row_total_incl_tax` viene restituito come valore residuo vicino a zero nella risposta API dell&#39;ordine anziché 0,00 per gli elementi completamente scontati.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con un prezzo e un prezzo speciale. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Fai clic su **[!UICONTROL Add Product]** > imposta **[!UICONTROL Price]** su $25 e **[!UICONTROL Special Price]** su $16,99 in **[!UICONTROL Advanced Pricing]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** e aggiungi una percentuale del 20%. Quindi vai a **[!UICONTROL Tax Rules]**, crea una regola e assegna
   **[!UICONTROL Taxable Goods]** come classe di imposta prodotto.
1. Crea una regola di vendita con uno sconto del 100% e un coupon. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** e aggiungi una regola con uno sconto del 100%, quindi utilizza **[!UICONTROL Specific Coupon]** e immetti il codice.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > e configura le impostazioni delle imposte.
1. Abilita spedizione gratuita. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. Imposta **[!UICONTROL Enabled]** su **[!UICONTROL Yes]** e regola le impostazioni.
1. Andare alla pagina del prodotto e selezionare **[!UICONTROL Add to Cart]**. Vai al carrello e applica il codice del coupon.
1. Inserire l&#39;ordine con l&#39;area fiscale applicabile.
1. Genera un token di amministrazione (API) tramite API REST.
1. Recupera i dettagli dell’ordine tramite API REST.
1. Controlla `row_total_incl_tax` nella risposta.

<u>Risultati previsti</u>:

`row_total_incl_tax` deve restituire un valore appropriato per la valuta come `0.00` quando l&#39;elemento viene completamente scontato.

<u>Risultati effettivi</u>:

`row_total_incl_tax` restituisce un valore a virgola mobile vicino a zero come `3.5527136788005e-15`, che non è appropriato per la visualizzazione della valuta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

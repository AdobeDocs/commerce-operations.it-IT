---
title: 'ACSD-61200: Corregge la compensazione dell''imposta sugli sconti nei calcoli del totale delle vendite'
description: Applicare la patch ACSD-61200 per risolvere il problema Adobe Commerce per cui *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* mancano dai calcoli del totale vendite, causando discrepanze tra i dati dell'ordine cliente e i dati del rapporto coupon.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Corregge la compensazione dell&#39;imposta sugli sconti nei calcoli del totale delle vendite

La patch ACSD-61200 risolve il problema relativo a *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* mancanti nei calcoli *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]*, causando discrepanze tra i dati dell&#39;ordine di vendita e i dati del rapporto coupon. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61200. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

- Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

- Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Imprecisioni nei dati del report ordini cliente e cedole a causa di *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* mancanti nei calcoli del totale vendite.

<u>Passaggi da riprodurre</u>:

1. Creare [!UICONTROL Tax Zone] e [!UICONTROL Tax Rule].
1. Imposta le seguenti configurazioni di imposta:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Aggiornare le seguenti impostazioni di visualizzazione per Ordini, Fatture e Note di accredito:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Crea un [!UICONTROL Cart Price Rule] con un coupon per uno sconto del 10%.
1. Completa un ordine utilizzando il coupon e genera una fattura e una spedizione.
1. Vai a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** e genera un rapporto.
1. Confrontare i dati nel riepilogo dell&#39;ordine con quelli del report.

<u>Risultati previsti</u>:

I calcoli *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* includono sia *[!UICONTROL Discount Tax Compensation Amount]* che *[!UICONTROL Shipping Discount Tax Compensation Amount]*, che corrispondono al riepilogo dell&#39;ordine con i dati del report.

<u>Risultati effettivi</u>:

I dati dell&#39;ordine cliente e i dati del rapporto coupon non corrispondono perché *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]* non sono presenti nei calcoli.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

- Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
- Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella guida Strumenti.

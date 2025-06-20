---
title: 'ACP2E-3841: le regole di prezzo del carrello per i prodotti di spedizione multipla non vengono applicate correttamente quando vengono utilizzate le condizioni di sottoselezione e la spedizione gratuita è abilitata'
description: Applicare la patch ACP2E-3841 per risolvere il problema Adobe Commerce in cui le regole del prezzo del carrello per i prodotti di spedizione multipla non vengono applicate correttamente quando vengono utilizzate condizioni di selezione secondaria e la spedizione gratuita è abilitata.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACP2E-3841: le regole di prezzo del carrello per i prodotti di spedizione multipla non vengono applicate correttamente quando vengono utilizzate le condizioni di sottoselezione e la spedizione gratuita è abilitata

La patch ACP2E-3841 risolve il problema in cui le regole del prezzo del carrello per i prodotti di spedizione multipla non vengono applicate correttamente quando vengono utilizzate le condizioni di sottoselezione e viene abilitata la spedizione gratuita. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACP2E-3841. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p9

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le regole del prezzo del carrello per i prodotti di spedizione multipla non si applicano correttamente quando vengono utilizzate le condizioni di selezione secondaria e la spedizione gratuita è abilitata.

<u>Prerequisiti</u>:

**Impostazioni:**
1. **[!UICONTROL Free Shipping]** = *Abilitato*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Categorie necessarie:**
1. Prova di categoria 1
1. Prova di categoria 2

**Prodotti necessari:**
1. Test prodotto 1:
   1. Categorie: prova di categoria 1
   1. Prezzo: $ 45
1. Test prodotto 2:
   1. Categorie: prova di categoria 2
   1. Prezzo: $ 56,25 
      **(I prezzi devono essere uguali a quelli mostrati qui per garantire il corretto funzionamento del test.)**

**Regola prezzo carrello:**

Accedi come amministratore e passa a **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Utilizza questi valori:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: verifica spedizione gratuita
1. **[!UICONTROL Active]**: *Sì*
1. **[!UICONTROL Websites]**: *Sito Web principale*
1. **[!UICONTROL Customer Groups]**: *NESSUN ACCESSO, Generale, Commercio all&#39;ingrosso, Retailer*
1. **[!UICONTROL Coupon]**: *Nessun coupon*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

Azioni:

**[!UICONTROL Percent of product price discount]** = *10*

<u>Passaggi da riprodurre</u>:

1. Accedi alla vetrina.
2. Aggiungi test prodotto 1.
3. Aggiungere due quantità di Product Test 2.
4. Visita il carrello.
5. Selezionare **[!UICONTROL Check Out with Multiple Addresses]**.

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

*Errore 500*

*Messaggio: funzionalità obsoleta: la conversione implicita da float 112.5 a int perde precisione in /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php alla riga 214*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

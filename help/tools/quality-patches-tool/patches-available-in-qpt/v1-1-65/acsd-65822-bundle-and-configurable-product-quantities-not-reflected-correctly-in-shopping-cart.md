---
title: 'ACSD-65822: quantità di prodotti configurabili e in bundle non riportate correttamente nel carrello'
description: Applica la patch ACSD-65822 per risolvere il problema di Adobe Commerce, dove la quantità appariva come 0 nella sezione carrello clienti nel pannello di amministrazione quando si aggiungevano bundle di prodotti.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822: le quantità del bundle e dei prodotti configurabili non vengono riportate correttamente in [!UICONTROL Shopping Cart]

La patch ACSD-65822 risolve il problema che causa la visualizzazione non corretta del bundle e delle quantità di prodotti configurabili nella sezione **[!UICONTROL Shopping Cart]** in *[!UICONTROL Customer's Activities]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-65822. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il bundle e le quantità di prodotti configurabili non vengono visualizzati correttamente nella sezione **[!UICONTROL Shopping Cart]** in *[!UICONTROL Customer's Activities]*.

<u>Passaggi da riprodurre</u>:

1. Crea un utente nella vetrina.
2. Crea un **[!UICONTROL Bundle product]** nel pannello di amministrazione.
3. Nella vetrina, come utente connesso, aggiungi il prodotto del bundle al carrello con una quantità specificata.
4. Nel pannello *Amministratore*, passa a **[!UICONTROL Customers]** e fai clic su **[!UICONTROL Edit]** per il cliente creato nel passaggio 1.
5. Fare clic su **[!UICONTROL Create Order]**.
6. Sul lato sinistro, in *[!UICONTROL Customer's Activities]*, controllare la sezione **[!UICONTROL Shopping Cart]**. Dovresti visualizzare il prodotto del bundle insieme alla quantità selezionata.

<u>Risultati previsti</u>:

La quantità dell&#39;articolo del bundle deve corrispondere alla quantità visualizzata nella vetrina.

<u>Risultati effettivi</u>:

La quantità dell&#39;articolo del bundle viene visualizzata come 0.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

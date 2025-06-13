---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* stato non applicato per *[!UICONTROL Related Product Rules]*'
description: Applica la patch ACSD-54739 per risolvere il problema Adobe Commerce per il quale lo stato *[!UICONTROL Product Stock]* non è applicato per *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739: stato *[!UICONTROL Product stock]* non applicato per *[!UICONTROL Related Product Rules]*

La patch ACSD-54739 risolve il problema se lo stato *[!UICONTROL Product stock]* non viene applicato per *[!UICONTROL Related Product Rules]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. L’ID della patch è ACSD-54739. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Stato *[!UICONTROL Product stock]* non applicato per *[!UICONTROL Related Product Rules]*.

<u>Passaggi da riprodurre</u>:

1. Impostare la configurazione **[!UICONTROL Display Out of Stock Products]** su *Sì*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** e imposta *Sì* per la condizione della regola promozionale.
1. Crea la regola prodotto correlata. Vai a **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Aggiungi una condizione con quantità attributo (selezionare in magazzino/esaurito).
1. Controlla i prodotti nel front-end.

<u>Risultati previsti</u>:

Il prodotto in magazzino/esaurito corrisponde a *[!UICONTROL Related Product Rules]*.

<u>Risultati effettivi</u>:

Il prodotto in magazzino/esaurito non corrisponde a *[!UICONTROL Related Product Rules]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

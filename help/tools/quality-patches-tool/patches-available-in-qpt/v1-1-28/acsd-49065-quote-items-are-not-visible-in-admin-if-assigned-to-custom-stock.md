---
title: 'ACSD-49065: gli elementi del preventivo non sono visibili in admin'
description: Applica la patch ACSD-49065 per risolvere il problema Adobe Commerce, se gli elementi del preventivo non sono visibili nell’amministratore se sono assegnati solo al titolo personalizzato.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: gli elementi del preventivo non sono visibili in admin

La patch ACSD-49065 risolve il problema per cui gli elementi dell&#39;offerta non sono visibili nell&#39;amministratore se sono assegnati solo all&#39;azione personalizzata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-49065. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi del preventivo non sono visibili nell&#39;amministratore se sono assegnati solo al titolo personalizzato.

Prerequisiti:

È necessario installare **[!UICONTROL B2B]** e **[!UICONTROL Inventory]** moduli.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Company]** e **[!UICONTROL B2B Quote]** in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Creare un **[!UICONTROL Inventory Source]** secondario e assegnarlo a un **[!UICONTROL Inventory Stock]** secondario.
1. Creare un nuovo prodotto assegnando solo il **[!UICONTROL Inventory Source]** secondario (non predefinito).
1. Vai alla vetrina e crea un nuovo account aziendale. Accedi come **[!UICONTROL Company Admin]** e aggiungi il prodotto creato al carrello.
1. Passare al carrello e *[!UICONTROL Request a Quote]*.
1. Rivolgersi all&#39;amministratore e visualizzare il preventivo richiesto in **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Risultati previsti</u>:

Gli elementi sono visibili nel nuovo preventivo creato con i nuovi prodotti senza dover salvare nuovamente i prodotti.

<u>Risultati effettivi</u>:

La sezione *[!UICONTROL Items Quoted]* è vuota. Se salvi nuovamente il prodotto appena creato, gli elementi vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

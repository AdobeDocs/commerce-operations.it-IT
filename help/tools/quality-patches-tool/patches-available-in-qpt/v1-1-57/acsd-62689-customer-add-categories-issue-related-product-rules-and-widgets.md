---
title: 'ACSD-62689: impossibile aggiungere categorie in [!UICONTROL Related Product Rules] e widget dopo la profondità 4'
description: Applicare la patch ACSD-62689 per risolvere il problema di Adobe Commerce che impedisce al cliente di aggiungere categorie in [!UICONTROL Related Product Rules] e widget dopo la nidificazione della profondità quattro.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
source-git-commit: 7aefd4f20580529a9da14776368bf2c3bbb3ff3c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: impossibile aggiungere categorie in *[!UICONTROL Related Product Rules]* e widget dopo la profondità 4

>[!NOTE]
>
>Questa patch è sostituita da [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md).

La patch ACSD-62689 risolve il problema che impediva al cliente di aggiungere categorie in *[!UICONTROL Related Product Rules]* e widget dopo la nidificazione di livello quattro. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62689. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un cliente non è in grado di aggiungere categorie in *[!UICONTROL Related Product Rules]* e widget dopo la nidificazione di profondità quattro.

<u>Passaggi da riprodurre</u>:

1. Creare due categorie denominate *[!UICONTROL Anchor]* e *[!UICONTROL Non-Anchor]* nella categoria principale predefinita.
   * Verificare che il flag *[!UICONTROL Is Anchor]* sia disabilitato per la categoria *[!UICONTROL Non-Anchor]*.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Widgets]** e crea un widget.
1. In *[!UICONTROL Layout Updates]*, selezionare **[!UICONTROL Non-Anchor Categories]** nel campo *[!UICONTROL Display on]*.
1. Fare clic su **[!UICONTROL Specific Categories]**.
1. Fai clic sull’icona di selezione della categoria.
1. Espandere la categoria radice.
1. Controlla le categorie. Entrambi devono essere disabilitati e non selezionabili.
1. In *[!UICONTROL Layout Updates]*, selezionare **[!UICONTROL Anchor Categories]** nel campo *[!UICONTROL Display on]*. Quindi seguire i punti 5 e 6.
1. Controlla le categorie. Entrambi devono essere attivati e selezionabili.

<u>Risultati previsti</u>:

Nel passaggio 7, deve essere selezionabile solo la categoria *[!UICONTROL Non-Anchor]*. Nel passaggio 9, la categoria *[!UICONTROL Anchor]* deve essere selezionabile.

<u>Risultati effettivi</u>:

Nel passaggio 7, non è possibile selezionare entrambe le categorie. Nel passaggio 9, è possibile selezionare entrambe le categorie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.


---
title: 'ACSD-64111: corregge l''errore *InvalidArgumentException: Class does not exist* durante l''impostazione di condizioni nidificate per un componente Product in [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: corregge l&#39;errore *InvalidArgumentException: La classe non esiste* durante l&#39;impostazione delle condizioni nidificate per un componente prodotto in [!DNL Page Builder]

La patch ACSD-64111 risolve il problema in cui *InvalidArgumentException: la classe non esiste* si verifica in `vendor/magento/module-rule/Model/ConditionFactory.php:50` quando si impostano condizioni nidificate per un componente prodotto in [!DNL Page Builder]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. L’ID della patch è ACSD-64111. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione)  2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore *InvalidArgumentException: la classe non esiste in /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php* viene generata quando si aggiunge un *[!UICONTROL Conditions Combination]* nella condizione [!DNL Page Builder] del widget Prodotti.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Adobe Commerce.
1. Vai a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Aggiungere una nuova pagina o modificare una pagina esistente.
1. Espandere la sezione **[!UICONTROL Content]** e fare clic su **[!UICONTROL Edit with Page Builder]**.
1. Aggiungere una nuova riga e quindi il widget **[!UICONTROL Products]**.
1. Configurare il widget **[!UICONTROL Products]**.
1. Selezionare **[!UICONTROL Condition]** in **[!UICONTROL Select Products By]**.
1. Aggiungi una nuova condizione e seleziona **[!UICONTROL Conditions Combination]** dal menu a discesa.

<u>Risultati previsti</u>:

Nessun errore nei registri.

<u>Risultati effettivi</u>:

Nei registri viene registrata la seguente eccezione:

*report.CRITICAL: InvalidArgumentException: la classe non esiste in vendor/magento/module-rule/Model/ConditionFactory.php:50*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'ACSD-62670: errore durante l''esportazione di [!UICONTROL Ordered Products Report] in CSV e XML'
description: Applicare la patch ACSD-62670 per risolvere il problema di Adobe Commerce, a causa del quale l'esportazione di [!UICONTROL Ordered Products Report] in formato CSV e XML genera un errore.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
source-git-commit: 0f26c762ee0cce3a415689b5196bfa564516e766
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# ACSD-62670: errore durante l&#39;esportazione di *[!UICONTROL Ordered Products Report]* in CSV e XML

La patch ACSD-62670 risolve il problema che causava la generazione di un errore durante l&#39;esportazione di *[!UICONTROL Ordered Products Report]* in CSV e XML. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) 1.1.56. L’ID della patch è ACSD-62670. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;esportazione di *[!UICONTROL Ordered Products Report]* in formato CSV e XML genera un errore.

<u>Passaggi da riprodurre</u>:

1. Vai al pannello *Amministratore* e passa a **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Prova a esportare file CSV o Excel.

<u>Risultati previsti</u>:

I report vengono esportati senza errori.

<u>Risultati effettivi</u>:

L&#39;esportazione di *[!UICONTROL Ordered Products Report]* genera l&#39;errore 404.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

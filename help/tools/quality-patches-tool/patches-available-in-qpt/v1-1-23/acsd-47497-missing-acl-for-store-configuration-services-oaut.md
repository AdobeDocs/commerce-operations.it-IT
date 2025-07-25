---
title: 'ACSD-47497: ACL mancante per l''archivio/configurazione/servizi [!UICONTROL OAuth]'
description: Applica la patch ACSD-47497 per risolvere il problema di Adobe Commerce quando vengono impostate le autorizzazioni per un particolare ruolo e non puoi definire l’accesso alla sezione di configurazione.
feature: Configuration, Identity Management, Services
role: Admin
exl-id: 4dbbd7df-f34b-4db8-a207-3de40fb39c6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-47497: ACL mancante per l&#39;archivio/configurazione/servizi [!UICONTROL OAuth]

La patch ACSD-47497 risolve il problema per cui la scheda **[!UICONTROL Services]** non è visibile nella sezione **[!UICONTROL Configuration]** dell&#39;amministrazione di Adobe Commerce. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23. L’ID della patch è ACSD-47497. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si impostano le autorizzazioni per un ruolo particolare, non è possibile definire l&#39;accesso a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Adobe Commerce Admin. Vai a **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Selezionare **[!UICONTROL Role Resources]** nel ruolo Amministratori e impostare **[!UICONTROL Resource Access]** in **[!UICONTROL Roles Resources]** su _Personalizzato_, quindi selezionare tutte le caselle di controllo. Selezionare **[!UICONTROL Save Role]**.
1. Selezionare **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**. Sezione di configurazione **[!UICONTROL OAuth]** non disponibile.

<u>Risultati previsti</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, la sezione di configurazione è visibile.

<u>Risultati effettivi</u>:

In **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**, la sezione di configurazione è mancante.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

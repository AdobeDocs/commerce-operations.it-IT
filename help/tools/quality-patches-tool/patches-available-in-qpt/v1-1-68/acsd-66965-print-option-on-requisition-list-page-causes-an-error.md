---
title: 'ACSD-66965: l''opzione [!UICONTROL Print] nella pagina [!UICONTROL Requisition List] causa un errore'
description: Applicare la patch ACSD-66965 per risolvere un problema in Adobe Commerce in cui l'opzione [!UICONTROL Print] nella pagina [!UICONTROL Requisition List] causa un errore.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: ccd0920a-074c-4851-a45a-09c43b04fe64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-66965: l&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** causa un errore

La patch ACSD-66965 risolve il problema che causa un errore nell&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66965. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** causa un errore a causa di un riferimento a un oggetto null in `Grid.php`.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Impostare **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** e **[!UICONTROL Enable Requisition List]** su `Yes`.
1. Crea due prodotti semplici.
1. Accedi alla vetrina e apri la pagina **[!UICONTROL My Account]**.
1. Creare un elenco di richieste.
1. Assegnare entrambi i prodotti all&#39;elenco delle richieste.
1. Accedere all&#39;elenco delle richieste di acquisto ed elencare i prodotti.
1. Fare clic su **[!UICONTROL Print]**.

<u>Risultati previsti</u>:

L&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** visualizza l&#39;anteprima di stampa senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Si è verificato un errore durante l&#39;esecuzione dell&#39;applicazione. Vedere il registro eccezioni per i dettagli.*

```text
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

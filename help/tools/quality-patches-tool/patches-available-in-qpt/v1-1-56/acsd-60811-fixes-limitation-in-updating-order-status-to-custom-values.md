---
title: 'ACSD-60811: Corregge la limitazione nell’aggiornamento dello stato dell’ordine ai valori personalizzati'
description: Applica la patch ACSD-60811 per risolvere il problema di Adobe Commerce, dove l’aggiornamento dello stato dell’ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è "elaborazione" o "frode".
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-60811: Corregge la limitazione nell’aggiornamento dello stato dell’ordine ai valori personalizzati

La patch ACSD-60811 risolve il problema per cui l&#39;aggiornamento dello stato dell&#39;ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è &#39;[!UICONTROL Processing]&#39; o &#39;[!UICONTROL Suspected Fraud]&#39;. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-60811. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento dello stato dell&#39;ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è *elaborazione* o *frode*. Lo stato dell&#39;ordine rimane invariato quando si seleziona e si invia un nuovo stato.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** per creare uno stato di ordine personalizzato nel pannello di amministrazione.
1. Fare clic su **[!UICONTROL Assign Status to State]** per assegnare lo stato personalizzato allo stato dell&#39;ordine.
1. Modificate lo stato dell&#39;ordine dalla pagina di visualizzazione dell&#39;ordine nel pannello di amministrazione.

<u>Risultati previsti</u>:

L’utente amministratore deve essere in grado di modificare lo stato dell’ordine impostandolo sullo stato personalizzato nel pannello di amministrazione.

<u>Risultati effettivi</u>:

Lo stato dell&#39;ordine rimane invariato quando si seleziona e si invia un nuovo stato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

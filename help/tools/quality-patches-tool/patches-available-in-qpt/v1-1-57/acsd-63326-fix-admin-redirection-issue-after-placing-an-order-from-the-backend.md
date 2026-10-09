---
title: 'ACSD-63326: risolvere il problema di reindirizzamento dell’amministratore dopo aver effettuato un ordine dal backend'
description: Applica la patch ACSD-63326 per risolvere il problema di Adobe Commerce, in cui l’amministratore viene reindirizzato a una pagina interrotta dopo aver effettuato un ordine dal backend.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
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
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-63326: risolvere il problema di reindirizzamento dell’amministratore dopo aver effettuato un ordine dal backend

La patch ACSD-63326 risolve il problema relativo al reindirizzamento dell’amministratore a una pagina interrotta dopo aver effettuato un ordine dal back-end. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-63326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli amministratori vengono reindirizzati a una pagina con un layout non funzionante dopo aver completato correttamente un ordine per un cliente dal backend.

<u>Passaggi da riprodurre</u>:

1. Passare alla sezione **[!UICONTROL Customers]** nel pannello di amministrazione.
1. Selezionare un cliente e fare clic su **[!UICONTROL Edit]**.
1. Nella pagina dei dettagli del cliente, fare clic su **[!UICONTROL Create Order]** dal menu principale.
1. Selezionare l&#39;archivio [!UICONTROL FR French] e aggiungere qualsiasi prodotto disponibile all&#39;ordine.
1. Compila i dettagli richiesti al momento del pagamento e fai clic su **[!UICONTROL Get shipping methods and rates]**.
1. Fai clic su **[Invia ordine]** per inoltrare l&#39;ordine.

<u>Risultati previsti</u>:

L’amministratore viene reindirizzato alla pagina di conferma dell’ordine o di ringraziamento con il layout corretto.

<u>Risultati effettivi</u>:

L’amministratore viene reindirizzato a una pagina con un layout non funzionante. Il layout viene corretto solo dopo l’aggiornamento della pagina.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

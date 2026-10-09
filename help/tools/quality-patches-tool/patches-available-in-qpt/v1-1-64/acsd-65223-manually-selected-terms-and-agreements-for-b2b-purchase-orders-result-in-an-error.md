---
title: 'ACSD-65223: i termini e gli accordi selezionati manualmente per gli ordini fornitore B2B generano un errore'
description: Applicare la patch ACSD-65223 per risolvere il problema di Adobe Commerce, per cui gli ordini creati con [!UICONTROL Purchase Orders] non possono essere completati con metodi di pagamento online come le carte di credito quando sono richiesti termini e condizioni per il pagamento.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '457'
ht-degree: 0%
---
# ACSD-65223: i termini e gli accordi selezionati manualmente per gli ordini fornitore B2B generano un errore

La patch ACSD-65223 risolve il problema che impedisce il completamento degli ordini creati con **[!UICONTROL Purchase Orders]** con metodi di pagamento online come le carte di credito quando sono richiesti termini e condizioni per il pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65223.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) B2B 1.5.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) B2B 1.5.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se sono necessari termini e condizioni per effettuare un ordine e si sta tentando di finalizzare un ordine creato utilizzando [!UICONTROL Purchase Orders], l&#39;ordine non può essere effettuato utilizzando metodi di pagamento online come le carte di credito.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** e scegli **[!UICONTROL B2B Features]**.
1. Impostare **[!UICONTROL Enable Company]** e **[!UICONTROL Enable Purchase Orders]** su *Sì*.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** e crea una nuova condizione. Imposta **[!UICONTROL Applied]** su *[!UICONTROL Manually]*.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** e imposta **[!UICONTROL Enable Terms and Conditions]** su *Sì*.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** e configura [!DNL Braintree].
1. Nella vetrina, crea un’azienda.
1. Nell&#39;amministratore, vai a **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.
1. Approva la società e consenti **[!UICONTROL Purchase Orders]**.
1. Sul front-end, accedi all’account.
1. Aggiungi un articolo al carrello.
1. Effettuare un ordine utilizzando **[!UICONTROL Purchase Order]**.
1. Nel dashboard del cliente, fare clic sulla scheda **[!UICONTROL Purchase Orders]**.
1. Crea un ordine dal nuovo ordine fornitore. Quindi seleziona la carta di credito come metodo di pagamento.
1. Accettare i termini e le condizioni.
1. Effettua l’ordine.

<u>Risultati previsti</u>:

Puoi effettuare un ordine utilizzando un metodo di pagamento online su ordini di acquisto approvati quando sono necessari termini e condizioni per il pagamento.

<u>Risultati effettivi</u>:

Non puoi effettuare un ordine utilizzando un metodo di pagamento online su ordini di acquisto approvati quando sono richiesti termini e condizioni per il pagamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

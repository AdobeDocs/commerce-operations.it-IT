---
title: 'ACSD-61134: deselezione automatica del metodo di pagamento [!UICONTROL Braintree Vault] nel flusso di lavoro di pagamento'
description: Applica la patch ACSD-61134 per risolvere il problema di Adobe Commerce in cui il metodo di pagamento *[!UICONTROL Braintree Vault]* viene deselezionato automaticamente nel flusso di lavoro di pagamento quando un acquirente aggiorna il proprio indirizzo di fatturazione deselezionando la casella di controllo *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '347'
ht-degree: 0%
---
# ACSD-61134: deselezione automatica del metodo di pagamento *[!UICONTROL Braintree Vault]* nel flusso di lavoro di pagamento

La patch ACSD-61134 risolve il problema che comporta la deselezione automatica del metodo di pagamento *[!UICONTROL Braintree Vault]* nel flusso di lavoro di pagamento quando un acquirente aggiorna il proprio indirizzo di fatturazione deselezionando la casella di controllo *[!UICONTROL My billing and shipping address are the same]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61134. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.7-beta1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il metodo di pagamento *[!UICONTROL Braintree Vault]* viene deselezionato automaticamente nel flusso di lavoro di pagamento dell&#39;estrazione.

<u>Passaggi da riprodurre</u>:

1. Configurare il metodo di pagamento *[!DNL Braintree]* con *[!UICONTROL Vault]* abilitato.
1. Estrarre e salvare una scheda in *[!UICONTROL Vault]*.
1. Estrai un altro prodotto.
1. Nella pagina *[!UICONTROL Shipping]*, aggiungi un nuovo indirizzo di spedizione in modo da avere due indirizzi da selezionare.
1. Nella pagina *[!UICONTROL Payment]*, seleziona il metodo di pagamento e fai clic su **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Risultati previsti</u>:

Il metodo di pagamento selezionato rimane selezionato.

<u>Risultati effettivi</u>:

Il metodo di pagamento selezionato non è selezionato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'ACSD-62118: tabella "sales_order_tax_item" non completamente aggiornata per gli ordini B2B effettuati utilizzando il metodo [!UICONTROL Purchase Order]'
description: Applica la patch ACSD-62118 per risolvere il problema di Adobe Commerce in cui la tabella "sales_order_tax_item" non viene completamente aggiornata quando si inseriscono ordini B2B utilizzando il metodo [!UICONTROL Purchase Order].
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-62118: tabella `sales_order_tax_item` non completamente aggiornata per gli ordini B2B effettuati utilizzando il metodo [!UICONTROL Purchase Order]

La patch ACSD-62118 risolve il problema che causa l&#39;aggiornamento completo della tabella `sales_order_tax_item` quando viene effettuato un ordine B2B utilizzando il metodo *[!UICONTROL Purchase Order]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-62118. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si inseriscono ordini B2B utilizzando il metodo *[!UICONTROL Purchase Order]*, la tabella `sales_order_tax_item` non viene aggiornata completamente. Questo problema influisce sui calcoli delle imposte e sull’elaborazione degli ordini. In particolare, l&#39;array `applied_taxes` è vuoto quando si esegue una query sull&#39;ordine tramite l&#39;API e sia `tax_item_amount` che `tax_item_percent` sono NULL.

<u>Passaggi da riprodurre</u>:

1. Aggiungere regole fiscali sia per **[!UICONTROL Product]** che per **[!UICONTROL Shipping]**.
1. Abilita il metodo **[!UICONTROL Purchase Order]** nelle impostazioni aziendali.
1. Accedi come utente amministratore della società.
1. Inserire un **[!UICONTROL Purchase Order]** utilizzando un metodo di pagamento offline.
1. Dopo l&#39;approvazione automatica di [!UICONTROL Purchase Order] e la conversione in un ordine, controllare i dati fiscali nella tabella `sales_order_tax_item` e tramite l&#39;API REST.

<u>Risultati previsti</u>:

* La tabella `sales_order_tax_item` deve contenere `tax_item` dati.
* L&#39;array `applied_taxes` deve visualizzare le informazioni fiscali corrette nella risposta API per gli ordini fornitore, in modo analogo ad altri metodi di pagamento (ad esempio, Assegno/vaglia postale).

<u>Risultati effettivi</u>:

* La tabella `sales_order_tax_item` non contiene dati `tax_item`.
* Gli array `applied_taxes` e `item_applied_taxes` sono vuoti nella risposta API per *[!UICONTROL Purchase Order]*.
* Nessun dato fiscale visualizzato quando si utilizza il metodo di pagamento *[!UICONTROL Purchase Order]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

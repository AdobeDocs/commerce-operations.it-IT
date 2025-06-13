---
title: 'ACSD-44938: VAT_ID non può essere applicato nella  [!DNL GraphQL] richiesta per l''utente ospite'
description: La patch ACSD-44938 risolve il problema per cui il "VAT_ID" non può essere applicato in una  [!DNL GraphQL] richiesta per un utente ospite. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-44938. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938: VAT_ID non può essere applicato nella richiesta [!DNL GraphQL] per l&#39;utente guest

La patch ACSD-44938 risolve il problema che impedisce l&#39;applicazione di `VAT_ID` in una richiesta [!DNL GraphQL] per un utente guest. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-44938. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile applicare `VAT_ID` a una richiesta [!DNL GraphQL] per un utente guest.

<u>Passaggi da riprodurre</u>:

1. Segui i passaggi indicati nell&#39;[[!DNL GraphQL] esercitazione](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) nella documentazione per sviluppatori per creare un carrello guest.
1. Provare ad applicare `VAT_ID` per l&#39;utente guest utilizzando [!DNL GraphQL].

<u>Risultati previsti</u>:

`VAT_ID` può essere applicato nello stesso modo di un cliente registrato. Consulta l&#39;articolo sulla mutazione [`createCustomerAddress`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/) nella documentazione per gli sviluppatori.

<u>Risultati effettivi</u>:

Impossibile applicare `VAT_ID` a un utente guest che utilizza [!DNL GraphQL].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

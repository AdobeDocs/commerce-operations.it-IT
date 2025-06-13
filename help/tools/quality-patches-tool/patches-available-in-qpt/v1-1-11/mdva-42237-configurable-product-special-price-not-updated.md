---
title: 'MDVA-42237: prezzo speciale del prodotto configurabile non aggiornato'
description: La patch MDVA-42237 risolve il problema che impedisce l'aggiornamento del prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del sottoprodotto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. L'ID della patch è MDVA-42237. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
exl-id: 1bae9a14-d6c1-4ee3-85aa-5d80ef479385
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42237: prezzo speciale del prodotto configurabile non aggiornato

La patch MDVA-42237 risolve il problema che impedisce l&#39;aggiornamento del prezzo speciale del prodotto configurabile in seguito alle modifiche del prezzo del sottoprodotto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. L&#39;ID della patch è MDVA-42237. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo speciale del prodotto configurabile non viene aggiornato in seguito alle modifiche apportate al prezzo del sottoprodotto.

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministrazione** > **Sistema** > **Gestione indice** e imposta **Modalità indice** su **Aggiorna in base alla pianificazione** per tutti gli indici.
1. Crea un prodotto configurabile con un prodotto semplice e imposta un prezzo speciale per il sottoprodotto.
1. Verifica che il prezzo speciale si rifletta sullo Storefront.
1. Rimuovere il prezzo speciale utilizzando GraphQL e ricontrollare il prezzo del prodotto sul Negozio.

<u>Risultati previsti</u>:

Il prezzo speciale non viene più visualizzato sullo Store.

<u>Risultati effettivi</u>:

Il prezzo non viene aggiornato sullo Store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

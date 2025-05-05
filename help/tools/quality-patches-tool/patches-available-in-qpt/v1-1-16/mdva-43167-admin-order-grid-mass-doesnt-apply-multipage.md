---
title: 'MDVA-43167: l''azione di massa Admin Order Grid non è applicabile a più pagine'
description: La patch MDVA-43167 risolve il problema per cui l'azione di massa Admin order grid non è applicabile per più pagine quando l'utente admin seleziona tutti gli ordini. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16. L'ID della patch è MDVA-43167. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Admin Workspace, Orders
role: Admin
exl-id: 992f8a90-300e-41aa-b03d-b8a647dddd51
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-43167: l&#39;azione di massa Admin Order Grid non è applicabile a più pagine

La patch MDVA-43167 risolve il problema per cui l&#39;azione di massa Admin order grid non è applicabile per più pagine quando l&#39;utente admin seleziona tutti gli ordini. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16. L&#39;ID della patch è MDVA-43167. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’azione di massa della griglia dell’ordine amministratore non si applica a più pagine quando l’utente amministratore seleziona tutti gli ordini.

<u>Passaggi da riprodurre</u>:

1. Acquista un prodotto tre volte per creare tre ordini.
1. Passare a **Griglia ordini di vendita**.
1. Modifica l’impaginazione impostando il valore personalizzato 2.
1. Seleziona tutto.
1. Selezionare **Azione di massa blocco**.

<u>Risultati previsti</u>:

Tutti e tre gli ordini sono bloccati.

<u>Risultati effettivi</u>:

Solo i due ordini visibili vengono bloccati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

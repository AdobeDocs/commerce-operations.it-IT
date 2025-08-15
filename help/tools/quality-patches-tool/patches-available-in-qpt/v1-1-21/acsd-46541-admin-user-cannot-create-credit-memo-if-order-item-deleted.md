---
title: 'ACSD-46541: un utente amministratore non può creare una nota di credito se viene eliminato un articolo dell''ordine'
description: Applica la patch ACSD-46541 per risolvere il problema di Adobe Commerce, per cui una volta eliminato un prodotto non è più possibile creare una nota di credito nell’amministratore Adobe Commerce.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541: un utente amministratore non può creare una nota di credito se viene eliminato un articolo dell&#39;ordine

La patch ACSD-46541 risolve il problema che impediva a un utente amministratore di creare una nota di credito in caso di eliminazione di una voce dell&#39;ordine. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21. L’ID della patch è ACSD-46541. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una volta eliminato un prodotto, non è più possibile creare una nota di credito in Commerce Admin.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Crea un ordine.
1. Fattura l&#39;ordine.
1. Elimina il prodotto dall’ordine.
1. Fare clic sul collegamento **[!UICONTROL Credit Memo]** nella pagina di modifica dell&#39;ordine.
1. Fare clic su **[!UICONTROL Refund Offline]** per creare una nota di credito.

<u>Risultati previsti</u>:

Creazione della nota di credito completata.

<u>Risultati effettivi</u>:

Impossibile trovare i _prodotti seguenti con SKU richiesti: viene visualizzato l&#39;errore SKU001_.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-47336: errore [!UICONTROL Something went wrong] durante la rimozione delle notifiche in Adobe Commerce Admin'
description: Applica la patch ACSD-47336 per risolvere il problema di Adobe Commerce, in cui l'utente visualizza l'errore [!UICONTROL Something went wrong], quando ignora le notifiche in  [!DNL Commerce] Admin.
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336: errore _[!UICONTROL Something went wrong]_&#x200B;durante la rimozione delle notifiche in Adobe Commerce Admin

La patch ACSD-47336 risolve il problema per cui l&#39;utente visualizza l&#39;errore _[!UICONTROL Something went wrong]_&#x200B;durante l&#39;eliminazione delle notifiche nell&#39;amministratore [!DNL Commerce]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-47336. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente visualizza l&#39;errore _[!UICONTROL Something went wrong]_&#x200B;quando ignora le notifiche nell&#39;amministratore [!DNL Commerce].

<u>Passaggi da riprodurre</u>:

1. Eseguire un’operazione in blocco (ad esempio, aggiornamento in blocco degli attributi del prodotto dalla griglia del prodotto).
1. Completare l&#39;operazione, ad esempio eseguire `bin/magento queue:consumer:start product_action_attribute.update`.
1. Aggiorna la pagina di amministrazione [!DNL Commerce], espandi la sezione di notifica amministratore e fai clic sul collegamento **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Risultati previsti</u>:

L&#39;errore _[!UICONTROL Something went wrong]_&#x200B;non deve essere visualizzato quando si cancellano le attività completate.

<u>Risultati effettivi</u>:

Viene visualizzato l&#39;errore _[!UICONTROL Something went wrong]_.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

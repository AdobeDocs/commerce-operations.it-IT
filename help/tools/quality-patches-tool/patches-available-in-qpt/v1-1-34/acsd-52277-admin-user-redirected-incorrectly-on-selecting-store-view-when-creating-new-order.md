---
title: 'ACSD-52277: l’utente amministratore non è stato reindirizzato correttamente quando ha selezionato la vista store durante la creazione di un nuovo ordine'
description: Applica la patch ACSD-52277 per risolvere il problema di Adobe Commerce, se un utente amministratore non viene reindirizzato correttamente, dopo aver selezionato la vista Store durante la creazione di un nuovo ordine in Admin.
exl-id: 61ef59a9-7a31-441f-a763-2d8016498fa7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277: l’utente amministratore non è stato reindirizzato correttamente quando ha selezionato la vista store durante la creazione di un nuovo ordine

La patch ACSD-52277 risolve il problema relativo a un utente amministratore che non viene reindirizzato correttamente dopo aver selezionato la vista Store durante la creazione di un nuovo ordine in Admin. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34. L’ID della patch è ACSD-52277. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore non viene reindirizzato correttamente dopo aver selezionato la vista store durante la creazione di un nuovo ordine.

<u>Passaggi da riprodurre</u>

1. Installa un’istanza pulita.
1. Crea un prodotto.
1. Crea un sito web aggiuntivo, uno store e due visualizzazioni store.
1. Creare un ordine dall&#39;amministratore selezionando *visualizzazione archivio 1*.

<u>Risultati previsti</u>:

L’utente viene reindirizzato alla pagina dell’ordine.

<u>Risultati effettivi</u>:

L’utente non viene reindirizzato alla pagina dell’ordine dopo aver selezionato la vista Store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

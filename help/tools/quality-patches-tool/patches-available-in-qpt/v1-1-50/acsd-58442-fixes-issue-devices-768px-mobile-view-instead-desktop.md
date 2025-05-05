---
title: 'ACSD-58442: risolve il problema per cui i dispositivi con larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento di menu e intestazioni nella visualizzazione per dispositivi mobili non desktop'
description: Applica la patch ACSD-58442 per risolvere il problema Adobe Commerce, in cui i dispositivi con una larghezza di 768 px vengono trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile anziché desktop.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442: risolve il problema per cui i dispositivi con larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento di menu e intestazioni nella visualizzazione per dispositivi mobili non desktop

La patch ACSD-58442 risolve il problema di Adobe Commerce, in cui i dispositivi con una larghezza di 768 px vengono trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile anziché desktop. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-58442. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il sistema ora tratta i dispositivi con una larghezza di 768 px come desktop, garantendo che il menu e l&#39;intestazione vengano caricati correttamente. In precedenza, i dispositivi con una larghezza di 768 px venivano trattati come dispositivi mobili, causando il caricamento del menu e dell’intestazione in una visualizzazione mobile.

<u>Passaggi da riprodurre</u>:

1. Carica la home page in un iPad Mini o utilizza lo strumento di ispezione di un browser per ridimensionare il browser a una larghezza di *768px*.
1. Apri il menu principale.

<u>Risultati previsti</u>:

Il menu e l’intestazione vengono caricati come vista desktop.

<u>Risultati effettivi</u>:

Il menu e l’intestazione vengono caricati come visualizzazione mobile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

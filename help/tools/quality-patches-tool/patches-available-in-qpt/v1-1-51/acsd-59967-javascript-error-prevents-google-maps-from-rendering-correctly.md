---
title: 'ACSD-59967: l''errore JavaScript impedisce il corretto rendering di  [!DNL Google Maps] '
description: Applica la patch ACSD-59967 per risolvere il problema di Adobe Commerce, in cui l'errore JavaScript impedisce il corretto rendering di  [!DNL Google Maps] .
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967: l&#39;errore JavaScript impedisce il corretto rendering di [!DNL Google Maps]

La patch ACSD-59967 risolve il problema che impedisce il corretto rendering di [!DNL Google Maps] a causa dell&#39;errore di JavaScript. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-59967. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;errore di JavaScript impedisce il corretto rendering di [!DNL Google Maps].

<u>Passaggi da riprodurre</u>:

1. Generare una chiave [!DNL Google Maps] valida.
1. Configurare la chiave API [!DNL Google Maps] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**.
1. Aggiungi [!DNL Google API Key] al campo **[!UICONTROL Google Maps API Key]** e salva la configurazione.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**.
1. Aggiungere un elemento **[!UICONTROL Row]** e un elemento **[!UICONTROL Maps]**.

<u>Risultati previsti</u>:

Nessun errore JavaScript presente nella console e la mappa viene riprodotta correttamente in *Storefront* e *Admin*.

<u>Risultati effettivi</u>:

Gli errori JavaScript vengono visualizzati nella console e la mappa non viene riprodotta correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

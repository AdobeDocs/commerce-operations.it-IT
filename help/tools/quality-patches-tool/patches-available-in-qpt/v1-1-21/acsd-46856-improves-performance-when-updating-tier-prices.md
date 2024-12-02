---
title: 'ACSD-46856: migliora le prestazioni quando si aggiornano i prezzi dei livelli'
description: Applicare la patch ACSD-46856 per migliorare le prestazioni quando si aggiornano i prezzi dei livelli tramite System &gt; Configuration &gt; Import &gt; Advanced Pricing.
feature: Orders
role: Admin
exl-id: 5c954f2c-a55c-43ba-919f-406f4b173d30
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-46856: l&#39;aggiornamento dei prezzi di livello tramite Sistema > Configurazione > Importazione > Advanced Pricing è lento

La patch ACSD-46856 migliora le prestazioni quando si aggiornano i prezzi dei livelli tramite **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21. L’ID della patch è ACSD-46856. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento dei prezzi dei livelli tramite **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Import]** > **[!UICONTROL Advanced Pricing]** è lento.

<u>Passaggi da riprodurre</u>:

* Importa un numero elevato di prodotti (ad esempio: 10k+ o 200k+) tramite **Sistema** > **Configurazione** > **Importazione** > **Determinazione prezzi avanzata**.

<u>Risultati previsti</u>:

Con la patch, il tempo di elaborazione è di circa 1:00 minuti per più di 200k prodotti.

<u>Risultati effettivi</u>:

Senza la patch, il tempo di elaborazione è di circa 10:00 minuti per i prodotti 10k+.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

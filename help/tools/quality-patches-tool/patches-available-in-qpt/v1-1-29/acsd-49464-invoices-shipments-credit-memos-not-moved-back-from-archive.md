---
title: 'ACSD-49464: Fatture, spedizioni e note di accredito non spostate dall''archivio'
description: Applicare la patch ACSD-49464 per risolvere il problema Adobe Commerce, in cui fatture, spedizioni e note di accredito non vengono spostate dall'archivio quando l'ID ordine è diverso.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464: Fatture, spedizioni e note di accredito non spostate dall&#39;archivio

La patch di ACSD-49464 risolve il problema che impedisce lo spostamento di fatture, spedizioni e note di credito dall&#39;archivio quando l&#39;ID ordine è diverso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-49464. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le fatture, le spedizioni e le note di accredito non vengono spostate dall&#39;archivio quando l&#39;ID ordine è diverso.

<u>Passaggi da riprodurre</u>:

1. Abilita l&#39;archiviazione di ordini, fatture, spedizioni e note di accredito.
1. Crea e completa un ordine, incluse spedizione, fattura e nota di accredito.
1. Verificare che gli ID di spedizione, fattura e nota di accredito non corrispondano al numero dell&#39;ordine.
1. Sposta l’ordine nell’archivio.
1. Ripristinare l&#39;ordine archiviato in Order Management.
1. Controllare i dettagli della fattura, della spedizione e della nota di accredito nelle rispettive pagine di griglia [!UICONTROL Invoice], [!UICONTROL Shipping] e [!UICONTROL Credit Memo].

<u>Risultati previsti</u>:

I record correlati originali vengono ripristinati quando l&#39;ordine viene spostato dall&#39;elenco di archiviazione alla gestione degli ordini.

<u>Risultati effettivi</u>:

* Nessun record per le note di spedizione, fattura e credito se tutti gli ID sono diversi.
* Se l&#39;ordine e i record correlati hanno lo stesso ID, i record vengono restituiti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

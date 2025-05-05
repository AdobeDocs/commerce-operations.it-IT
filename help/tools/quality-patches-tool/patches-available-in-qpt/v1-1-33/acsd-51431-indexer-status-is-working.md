---
title: "ACSD-51431: lo stato dell'indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog"
description: Applicare la patch ACSD-51431 per risolvere il problema Adobe Commerce in cui lo stato dell'indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog.
feature: Logs, Price Indexer
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431: lo stato dell&#39;indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog

La patch ACSD-51431 risolve il problema di prestazioni in cui lo stato dell&#39;indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51431. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell&#39;indicizzatore è *[!UICONTROL Working]* anche se non sono presenti voci nel changelog.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL indexers]** su [!UICONTROL Update on Schedule].
1. Configura il processo cron in modo che venga eseguito ogni minuto.
1. Salva le modifiche apportate a prodotti diversi simultaneamente.
1. Esegui `bin/magento indexer:status` in pochi minuti.

<u>Risultati previsti</u>:

Le modifiche vengono elaborate e gli indicizzatori sono nello stato *[!UICONTROL Ready]*. Lo stato *[!UICONTROL Schedule]* è *[!UICONTROL idle (0 in the backlog)]*.

<u>Risultati effettivi</u>:

Le modifiche vengono elaborate e gli indicizzatori sono nello stato *[!UICONTROL Ready]*. Tuttavia, lo stato *[!UICONTROL Schedule]* visualizza *[!UICONTROL working (0 in the backlog)]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

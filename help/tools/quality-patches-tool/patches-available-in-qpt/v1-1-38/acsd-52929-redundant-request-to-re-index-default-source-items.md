---
title: 'ACSD-52929: richiesta ridondante per reindicizzare gli elementi di origine predefiniti'
description: Applica la patch ACSD-52929 per risolvere il problema di Adobe Commerce in presenza di una richiesta ridondante di reindicizzazione degli elementi di origine predefiniti quando l’indicizzatore inventario è configurato in modalità asincrona.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: richiesta ridondante per reindicizzare gli elementi di origine predefiniti

La patch ACSD-52929 risolve il problema della ridondanza delle richieste di reindicizzazione degli elementi di origine predefiniti quando l’indicizzatore di inventario è configurato in modalità asincrona. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-52929. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l’indicizzatore inventario è configurato in modalità asincrona, vi è una ridondanza di richieste per reindicizzare gli articoli di origine predefiniti.

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL RabbitMQ].
1. Abilitare la strategia di reindicizzazione asincrona scegliendo **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** e impostando **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crea un’origine inventario personalizzata.
1. Accedere al dashboard [!DNL RabbitMQ] e passare alla scheda code.
1. Controllare la coda di `inventory.indexer.sourceItem` e assicurarsi che non contenga messaggi.
1. Aprire un prodotto semplice dal backend e aggiungere *[!UICONTROL stock only]* all&#39;origine personalizzata e salvare il prodotto.
1. Caricare la coda `inventory.indexer.sourceItem` nel dashboard [!DNL RabbitMQ] e quindi controllare i messaggi.

<u>Risultati previsti</u>:

Nella coda è presente un solo messaggio per l&#39;origine personalizzata.

<u>Risultati effettivi</u>:

Nella coda vengono visualizzati due messaggi: uno per l’origine predefinita e l’altro per l’origine personalizzata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-62591: il tema non viene cambiato quando **[!UICONTROL User Agent Rules]** è configurato'
description: Applicare la patch ACSD-62591 per risolvere il problema Adobe Commerce in cui il tema non viene cambiato correttamente quando **[!UICONTROL User Agent Rules]** sono configurati.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591: il tema non viene cambiato correttamente quando [!UICONTROL User Agent Rules] è configurato

La patch ACSD-62591 risolve il problema che causa il cambiamento non corretto del tema quando **[!UICONTROL User Agent Rules]** è configurato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-62591. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il tema non viene cambiato correttamente quando **[!UICONTROL User Agent Rules]** è configurato.

<u>Passaggi da riprodurre</u>:

1. Aprire Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Modifica un tema di visualizzazione store.
1. Imposta `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` in **[!UICONTROL User Agent Rules]** e scegli un tema diverso.
1. Salva le modifiche e cancella le cache.
1. Apri una pagina Storefront su un dispositivo mobile.
1. Apri la stessa pagina da un browser desktop.

<u>Risultati previsti</u>:

Il browser desktop e il dispositivo mobile visualizzano le pagine utilizzando i rispettivi temi.

<u>Risultati effettivi</u>:

Il browser desktop visualizza la pagina memorizzata in cache con il tema mobile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.


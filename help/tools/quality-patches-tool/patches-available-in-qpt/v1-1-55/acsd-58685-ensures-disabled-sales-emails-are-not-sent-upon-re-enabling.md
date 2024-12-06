---
title: 'ACSD-58685: le e-mail di vendita disabilitate vengono inviate al momento della riabilitazione'
description: Applica la patch ACSD-58685 per risolvere il problema Adobe Commerce, a causa del quale le e-mail di vendita avviate mentre la comunicazione e-mail è disabilitata vengono inviate dopo la riattivazione della comunicazione e-mail.
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: le e-mail di vendita disabilitate vengono inviate al momento della riabilitazione

La patch di ACSD-58685 risolve il problema per cui le e-mail di vendita avviate mentre la comunicazione e-mail è disattivata vengono inviate dopo la riattivazione della comunicazione e-mail. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58685. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di vendita avviate mentre la comunicazione e-mail è disabilitata vengono inviate una volta riabilitata la comunicazione e-mail.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** e imposta **[!UICONTROL Disable Email Communications]** su *[!UICONTROL No]*.
1. Passare a **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** e impostare **[!UICONTROL Asynchronous Sending]** su *[!UICONTROL Yes]*.
1. Cancella la cache di configurazione.
1. Effettua un ordine.
1. Abilita la comunicazione e-mail.
1. Effettua un altro ordine.
1. Esegui il cron.

<u>Risultati previsti</u>:

Viene inviata solo l’e-mail per il secondo ordine.

<u>Risultati effettivi</u>:

Le e-mail del primo e del secondo ordine vengono inviate.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

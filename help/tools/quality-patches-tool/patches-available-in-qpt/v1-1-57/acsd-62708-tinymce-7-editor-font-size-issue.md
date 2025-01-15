---
title: 'ACSD-62708: [!DNL TinyMCE] 7 dimensione font editor nel pannello di amministrazione mostra PT'
description: Applica la patch ACSD-62708 per risolvere il problema di Adobe Commerce in cui la dimensione font dell'editor  [!DNL TinyMCE] 7 nell'amministratore mostra PT e non PX. Ora è anche possibile impostare la dimensione del carattere in PX anziché in PT.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708: le dimensioni del font dell&#39;editor [!DNL TinyMCE] 7 nel pannello di amministrazione mostrano PT

La patch ACSD-62708 risolve il problema relativo alla visualizzazione della dimensione del font dell&#39;editor [!DNL TinyMCE] 7 nel pannello di amministrazione in PT anziché in PX. Questa patch consente di impostare la dimensione del carattere in PX. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62708. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;editor di [!DNL TinyMCE] 7 nel pannello di amministrazione visualizza la dimensione del font in PT invece che in PX.

<u>Passaggi da riprodurre</u>:

1. Apri la pagina di modifica del prodotto nel pannello di amministrazione.
1. Espandere la sezione [!UICONTROL Content].
1. Controllare i controlli dei caratteri nell&#39;editor [!DNL TinyMCE].

<u>Risultati previsti</u>:

La dimensione font deve essere in PX.

<u>Risultati effettivi</u>:

La dimensione del carattere è in PT.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

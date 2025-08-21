---
title: 'ACSD-62415: il backend di Adobe Commerce carica [!UICONTROL Categories] molto lentamente'
description: Applicare la patch ACSD-62415 per risolvere il problema di Adobe Commerce, in cui le prestazioni della pagina [!UICONTROL Categories] nel pannello [!UICONTROL Admin] vengono caricate molto lentamente quando è presente un numero elevato di categorie di ancoraggio.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: il backend di Adobe Commerce carica **[!UICONTROL Categories]** molto lentamente quando sono presenti categorie di ancoraggio

La patch ACSD-62415 risolve il problema relativo al caricamento molto lento delle prestazioni della pagina **[!UICONTROL Categories]** nel pannello **[!UICONTROL Admin]** quando sono presenti numerose categorie di ancoraggio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-62415. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La pagina **[!UICONTROL Categories]** nel pannello **[!UICONTROL Admin]** viene caricata molto lentamente quando è presente un numero elevato di categorie di ancoraggio.

<u>Passaggi da riprodurre</u>:

1. Genera categorie di ancoraggio 3K.
1. Aprire la pagina **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** nel pannello **[!UICONTROL Admin]**.

<u>Risultati previsti</u>:

La pagina **[!UICONTROL Categories]** viene caricata rapidamente e la query non deve essere ripetuta 1.000 volte.

<u>Risultati effettivi</u>:

Il caricamento richiede da 7 a 20 secondi e la query viene eseguita più di 1K volte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

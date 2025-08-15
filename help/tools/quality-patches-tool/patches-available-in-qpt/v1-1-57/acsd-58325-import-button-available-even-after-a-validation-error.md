---
title: 'ACSD-58325: pulsante [!UICONTROL Import] disponibile anche dopo un errore di convalida'
description: Applicare la patch ACSD-58325 per risolvere il problema di Adobe Commerce per cui il pulsante [!UICONTROL Import] è disponibile anche dopo un errore di convalida.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: pulsante [!UICONTROL Import] disponibile anche dopo un errore di convalida

La patch ACSD-58325 risolve il problema per cui il pulsante **[!UICONTROL Import]** è disponibile anche dopo un errore di convalida. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-58325. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pulsante [!UICONTROL Import] è disponibile anche dopo un errore di convalida.

<u>Passaggi da riprodurre</u>:

1. Crea il file CSV per l’importazione del prodotto con un nome immagine errato nel file.
1. Crea un’importazione di prodotto pianificata utilizzando il file CSV creato.
1. Attendi l’esecuzione dell’importazione pianificata.
1. Controllare [!UICONTROL Last outcome] nella griglia **[!UICONTROL Scheduled Imports/Exports]**.

<u>Risultati previsti</u>:

[!UICONTROL Last outcome] deve essere [!UICONTROL Failed].

<u>Risultati effettivi</u>:

[!UICONTROL Last outcome] è [!UICONTROL Successful].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

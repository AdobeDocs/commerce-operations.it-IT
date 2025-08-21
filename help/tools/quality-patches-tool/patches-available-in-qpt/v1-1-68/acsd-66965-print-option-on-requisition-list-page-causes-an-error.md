---
title: 'ACSD-66965: l''opzione [!UICONTROL Print] nella pagina [!UICONTROL Requisition List] causa un errore'
description: Applicare la patch ACSD-66965 per risolvere un problema in Adobe Commerce in cui l'opzione [!UICONTROL Print] nella pagina [!UICONTROL Requisition List] causa un errore.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: l&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** causa un errore

La patch ACSD-66965 risolve il problema che causa un errore nell&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66965. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** causa un errore a causa di un riferimento a un oggetto null in `Grid.php`.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Impostare **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** e **[!UICONTROL Enable Requisition List]** su `Yes`.
1. Crea due prodotti semplici.
1. Accedi alla vetrina e apri la pagina **[!UICONTROL My Account]**.
1. Creare un elenco di richieste.
1. Assegnare entrambi i prodotti all&#39;elenco delle richieste.
1. Accedere all&#39;elenco delle richieste di acquisto ed elencare i prodotti.
1. Fare clic su **[!UICONTROL Print]**.

<u>Risultati previsti</u>:

L&#39;opzione **[!UICONTROL Print]** nella pagina **[!UICONTROL Requisition List]** visualizza l&#39;anteprima di stampa senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Si è verificato un errore durante l&#39;esecuzione dell&#39;applicazione. Vedere il registro eccezioni per i dettagli.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

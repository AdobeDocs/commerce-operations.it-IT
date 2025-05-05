---
title: 'ACSD-60811: Corregge la limitazione nell’aggiornamento dello stato dell’ordine ai valori personalizzati'
description: Applica la patch ACSD-60811 per risolvere il problema di Adobe Commerce, dove l’aggiornamento dello stato dell’ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è "elaborazione" o "frode".
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 099c4d25978aebe1eefbdcd4c3317b804da456b8
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# ACSD-60811: Corregge la limitazione nell’aggiornamento dello stato dell’ordine ai valori personalizzati

La patch ACSD-60811 risolve il problema per cui l&#39;aggiornamento dello stato dell&#39;ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è &#39;[!UICONTROL Processing]&#39; o &#39;[!UICONTROL Suspected Fraud]&#39;. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-60811. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento dello stato dell&#39;ordine con un valore o un commento personalizzato è possibile solo se lo stato corrente è *elaborazione* o *frode*. Lo stato dell&#39;ordine rimane invariato quando si seleziona e si invia un nuovo stato.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** per creare uno stato di ordine personalizzato nel pannello di amministrazione.
1. Fare clic su **[!UICONTROL Assign Status to State]** per assegnare lo stato personalizzato allo stato dell&#39;ordine.
1. Modificate lo stato dell&#39;ordine dalla pagina di visualizzazione dell&#39;ordine nel pannello di amministrazione.

<u>Risultati previsti</u>:

L’utente amministratore deve essere in grado di modificare lo stato dell’ordine impostandolo sullo stato personalizzato nel pannello di amministrazione.

<u>Risultati effettivi</u>:

Lo stato dell&#39;ordine rimane invariato quando si seleziona e si invia un nuovo stato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

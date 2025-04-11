---
title: 'ACSD-64209: il modulo di pianificazione Cron recupera i preventivi negoziabili senza escludere [!UICONTROL Ordered] preventivi'
description: Applicare la patch ACSD-64209 per risolvere il problema di Adobe Commerce in cui il modulo di pianificazione cron recupera tutti i preventivi negoziabili senza escludere quelli con lo stato [!UICONTROL Ordered], causando l'attivazione di un messaggio e-mail o di messaggi e-mail.
feature:  B2B, Communications
role: Admin, Developer
source-git-commit: 6fbe987dca81065071b611bfe0bfd0cb7baf1938
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: il modulo di pianificazione Cron recupera i preventivi negoziabili senza escludere [!UICONTROL Ordered] preventivi

La patch ACSD-64209 risolve il problema che comporta il recupero da parte del modulo di pianificazione cron di tutti i preventivi negoziabili senza escludere quelli con lo stato **[!UICONTROL Ordered]**, causando l&#39;attivazione di un messaggio e-mail o di messaggi e-mail. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64209. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il modulo di pianificazione cron recupera tutti i preventivi negoziabili senza escludere quelli con lo stato **[!UICONTROL Ordered]**, causando l&#39;attivazione di un messaggio e-mail o di messaggi e-mail.

<u>Passaggi da riprodurre</u>:


1. Nella barra laterale *Amministratore*, vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e abilita Azienda e preventivo B2B.
1. Imposta **[!UICONTROL Default Expiration Period]** su *1* in *Amministratore* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Crea una società, attivala e accedi come amministratore della società.
1. Aggiungi un prodotto al carrello.
1. Richiedi un preventivo.
1. Nella barra laterale *Admin*, passa a **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Selezionare il preventivo creato e fare clic su **[!UICONTROL Send]** per inviare nuovamente il preventivo all&#39;acquirente.
1. Accedi come amministratore aziendale sulla vetrina.
1. Selezionare il preventivo e fare clic su **[!UICONTROL Proceed to checkout]** per completare l&#39;acquisto.
1. Verificare che lo stato del preventivo sia **[!UICONTROL Ordered]** e che non siano possibili altre azioni nella vetrina.
1. Attiva il processo cron `negotiable_quote_send_emails`.


<u>Risultati previsti</u>:

Poiché il preventivo è stato ordinato e non è possibile eseguire ulteriori azioni, non è necessario inviare alcuna e-mail relativa alla scadenza del preventivo.

<u>Risultati effettivi</u>:

Verrà inviata un&#39;e-mail con *scadenza del preventivo*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

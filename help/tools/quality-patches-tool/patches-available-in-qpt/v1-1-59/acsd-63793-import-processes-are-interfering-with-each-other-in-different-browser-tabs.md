---
title: 'ACSD-63793: i processi di importazione interferiscono tra loro in diverse schede del browser'
description: Applica la patch ACSD-63793 per risolvere il problema di Adobe Commerce, in cui i processi di importazione interferiscono tra loro in diverse schede del browser.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 60ad8dff5a3f26d0eab536d8824cb6579cb88a5a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-63793: i processi di importazione interferiscono tra loro in diverse schede del browser

La patch ACSD-63793 risolve il problema relativo alle interferenze tra i processi di importazione nelle diverse schede del browser. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-63793. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione di dati tramite l’interfaccia di amministrazione interferisce con un’altra importazione, consentendo l’elaborazione dei dati di un’importazione in un’altra.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Imposta **[!UICONTROL Entity Type]** su *[!UICONTROL Customers and Addresses] (file singolo)*.
1. Imposta **[!UICONTROL Import Behavior]** su *[!UICONTROL Add/Update]*.
1. Seleziona un file valido da importare.
1. Fare clic sul pulsante **[!UICONTROL Check Data]**.
1. Tieni aperta questa scheda.
1. Apri una nuova scheda e ripeti i passaggi con un file contenente dati non validi (ad esempio, due e-mail identiche per clienti diversi).
1. Torna alla prima scheda.
1. Fare clic sul pulsante **[!UICONTROL Import]** in basso.

<u>Risultati previsti</u>:

Il processo di importazione non deve interferire tra di loro.

<u>Risultati effettivi</u>:

Il processo di importazione viene completato e il file del report è disponibile per il download. Indica un errore nella seconda riga e i dati di un’altra importazione vengono elaborati, anche se la convalida iniziale è passata senza errori.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

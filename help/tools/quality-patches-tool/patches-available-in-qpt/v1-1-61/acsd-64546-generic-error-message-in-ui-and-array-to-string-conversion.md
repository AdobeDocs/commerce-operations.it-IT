---
title: 'ACSD-64546: messaggio di errore generico nell’interfaccia utente e eccezione di conversione da array a stringa durante la creazione dell’etichetta UPS'
description: Applica la patch ACSD-64546 per risolvere il problema di Adobe Commerce, in cui viene visualizzato un messaggio di errore generico nell’interfaccia utente e l’eccezione Array to String conversion viene registrata durante la creazione dell’etichetta UPS. La patch fa sì che l’errore corretto venga visualizzato nell’interfaccia utente e nei registri.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: messaggio di errore generico nell&#39;interfaccia utente e eccezione *Array to string conversion* durante la creazione dell&#39;etichetta UPS

La patch ACSD-64546 risolve il problema che causava la visualizzazione di un messaggio di errore generico nell&#39;interfaccia utente e la registrazione dell&#39;eccezione *Conversione da array a stringa* durante la creazione dell&#39;etichetta UPS, garantendo la visualizzazione dell&#39;errore corretto nell&#39;interfaccia utente e nei registri. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64546. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nell&#39;interfaccia utente viene visualizzato un messaggio di errore generico e l&#39;eccezione *Array to string conversion* si verifica durante la creazione dell&#39;etichetta UPS.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente con un indirizzo valido.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** e aggiungi un indirizzo valido.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** e aggiungi un indirizzo valido.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** e configura UPS.
1. Effettuare un ordine utilizzando [!UICONTROL UPS].
1. Rimuovere l&#39;ID utente e la password UPS da `core_config_data` nel database.
1. Pulizia cache di configurazione.
1. Aprire l&#39;ordine creato in **[!UICONTROL Admin]**.
1. Crea una nuova spedizione.
   1. Selezionare la casella di controllo **[!UICONTROL Create Shipping Label]**.
   1. Fare clic su **[!UICONTROL Submit shipment]**.
   1. Aggiungi il prodotto a un pacchetto. Specifica la dimensione del pacchetto (Lunghezza, Larghezza e Altezza).
   1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Il messaggio di errore effettivo viene visualizzato nell’interfaccia utente e nei registri.

<u>Risultati effettivi</u>:

* Nell’interfaccia utente viene visualizzato il seguente errore:
  *Errore durante la creazione dell&#39;etichetta di spedizione.*
* L&#39;eccezione *Array to string conversion* impedisce la visualizzazione o l&#39;archiviazione del messaggio di errore effettivo nei registri.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:
* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:
* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

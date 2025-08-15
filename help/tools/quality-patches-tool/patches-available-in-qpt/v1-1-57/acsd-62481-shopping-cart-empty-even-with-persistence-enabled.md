---
title: 'ACSD-62481: il carrello rimane vuoto anche con [!UICONTROL Persistence] abilitato'
description: Applica la patch ACSD-62481 per risolvere il problema di Adobe Commerce in cui la funzione del carrello persistente non riesce quando utilizzi il pop-up di accesso durante il pagamento.
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-62481: il carrello rimane vuoto anche con *[!UICONTROL Persistence]* abilitato

La patch ACSD-62481 risolve il problema relativo al mancato funzionamento della funzione del carrello persistente quando si utilizza il pop-up di accesso durante l&#39;estrazione perché manca la casella di controllo *[!UICONTROL Remember Me]*, causando la scomparsa dei prodotti dal carrello dopo la disconnessione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62481. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La funzionalità del carrello persistente non riesce quando si utilizza la finestra a comparsa di accesso durante l&#39;estrazione perché manca la casella di controllo *[!UICONTROL Remember Me]*. In questo modo i prodotti scompaiono dal carrello dopo la disconnessione.

<u>Passaggi da riprodurre</u>:

1. Nell’amministratore, configura l’account guest e le impostazioni del carrello permanente come segue:

   * Passa a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** e imposta *[!UICONTROL Allow Guest Checkout]* su *No*.

      * Fare clic su **[!UICONTROL Save Config]**.

   * Passa a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** e imposta *[!UICONTROL Enable Persistence]* su *Sì*.
   * Lascia tutte le altre impostazioni predefinite, ma cambia *[!UICONTROL Clear Persistence on Sign Out]* in *No*.

      * Fare clic su **[!UICONTROL Save Config]**.

1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** per aggiungere un prodotto semplice al catalogo.

   * Compila i dettagli minimi richiesti e assicurati che siano in magazzino.

1. Sul front-end creare un account cliente utilizzando il modulo principale `(../customer/account/create/)` e disconnettersi.
1. Aggiungi il prodotto al carrello come ospite.
1. Apri il mini-carrello con l&#39;icona in alto a destra, quindi fai clic su **[!UICONTROL View and Edit Cart]**.
1. Procedi con il pagamento.
1. Accedi al nuovo account cliente tramite la finestra di dialogo a comparsa visualizzata ed esci.

<u>Risultati previsti</u>:

Il carrello conserva i prodotti dell’utente connesso in precedenza.

<u>Risultati effettivi</u>:

* Il carrello è vuoto.
* La finestra di dialogo di accesso popup non mostra l&#39;opzione *[!UICONTROL Remember Me]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

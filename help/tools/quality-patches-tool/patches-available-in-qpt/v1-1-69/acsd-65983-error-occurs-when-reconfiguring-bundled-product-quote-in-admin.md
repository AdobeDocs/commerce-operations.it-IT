---
title: 'ACSD-65983: si verifica un errore durante la riconfigurazione dell’offerta di prodotto in bundle in Admin'
description: Applicare la patch ACSD-65983 per risolvere il problema di Adobe Commerce che si verifica quando si tenta di configurare un prodotto bundle nella schermata [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] sul backend.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: si verifica un errore durante la riconfigurazione dell’offerta di prodotto in bundle in Admin

La patch ACSD-65983 risolve il problema se la riconfigurazione di un preventivo di prodotto in bundle nel backend di amministrazione restituisce un errore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-65983. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La riconfigurazione di un preventivo di prodotto in bundle nel backend di amministrazione restituisce un errore.

<u>Passaggi da riprodurre</u>:

1. Vai al pannello di amministrazione e abilita **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Crea un prodotto bundle con importo fisso (ad esempio: *$10*) e aggiungi tre o più prodotti semplici con importo *0*, *2* in **Opzione 1** e *altri* in **Opzione 2**.
1. Crea un account aziendale dal front-end.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e assegna la società e i prodotti creati al catalogo condiviso nuovo/personalizzato.
1. Accedi come **Utente aziendale** sul front-end e aggiungi un prodotto semplice al carrello dal bundle.
1. Apri la pagina del carrello e invia come **Richiedi un preventivo**.
1. Passare al backend e modificare l&#39;offerta creata.
1. Nella sezione **Elemento preventivo** fare clic sul pulsante **Configura**.
1. Selezionare un altro prodotto semplice dall&#39;**opzione 2**.
1. Fare clic sul pulsante **OK** per visualizzare il messaggio di errore.

<u>Risultati previsti</u>:

È possibile configurare correttamente gli elementi dell&#39;offerta richiesta dall&#39;amministratore, senza visualizzare alcun messaggio di errore.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di errore:

*Un problema tecnico con il server ha creato un errore. Riprova a continuare quello che stavi facendo. Se il problema persiste, riprovare più tardi.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti

---
title: 'ACSD-58828: l’indirizzo *lato server è obbligatorio* viene visualizzato per qualsiasi campo obbligatorio vuoto, insieme alla convalida lato client'
description: Applica la patch ACSD-58828 per risolvere il problema Adobe Commerce, se viene lasciato vuoto un campo obbligatorio contenente il messaggio di convalida lato server *address*, insieme al messaggio di convalida lato client.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
source-git-commit: 3b47046d31a6f71f8c366fb468f435633832c039
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# ACSD-58828: l&#39;indirizzo *lato server è obbligatorio* viene visualizzato per qualsiasi campo obbligatorio vuoto, insieme alla convalida lato client

La patch ACSD-58828 risolve il problema relativo all&#39;eventuale visualizzazione del messaggio di convalida lato server *indirizzo* se un campo obbligatorio viene lasciato vuoto, insieme al messaggio di convalida lato client. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58828. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se un campo obbligatorio viene lasciato vuoto, viene visualizzato il messaggio di convalida lato server *indirizzo* insieme al messaggio di convalida lato client.

Passaggi da riprodurre:

1. Accedi come cliente.
1. Aggiungi un prodotto al carrello.
1. Procedi con il pagamento.
1. Lascia l’indirizzo di spedizione immutato.
1. Selezionare **[!UICONTROL Flat rate]** e selezionare **[!UICONTROL Next]**.
1. Deseleziona **[!UICONTROL My billing and shipping address are the same]**.
1. Aggiungi un nuovo indirizzo dal menu a discesa.
1. Lascia vuoto qualsiasi campo obbligatorio e seleziona **[!UICONTROL Update]**.

Risultati previsti:

Il messaggio di errore descrive informazioni mancanti o errate necessarie per l&#39;estrazione.

Risultati effettivi:

L&#39;indirizzo *dell&#39;errore è obbligatorio. Inserisci e riprova.* viene visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'ACSD-66179: l''annullamento di una fattura con il tipo di pagamento [!UICONTROL Not Capture] genera una pagina di errore 404'
description: Applicare la patch ACSD-66179 per risolvere il problema di Adobe Commerce in cui l'annullamento di una fattura con il tipo di pagamento [!UICONTROL Not Capture] causava una pagina di errore 404.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
source-git-commit: 02a446114be0f9c1ff8d4532cb13a94f1ef64ed2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-66179: l&#39;annullamento di una fattura con il tipo di pagamento [!UICONTROL Not Capture] genera una pagina di errore 404

La patch ACSD-66179 risolve il problema che causava la pagina di errore 404 in seguito all&#39;annullamento di una fattura creata con il tipo di pagamento *[!UICONTROL Not Capture]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66179. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;annullamento di una fattura creata con il tipo di pagamento *[!UICONTROL Not Capture]* genera una pagina di errore 404.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine utilizzando un metodo di pagamento come PayPal Express Checkout.
1. Creare una fattura. Impostare **[!UICONTROL Amount]** su *[!UICONTROL Not Capture]* e inviare la fattura.
1. Aprire la fattura creata e selezionare **[!UICONTROL Cancel]**.

<u>Risultati previsti</u>:

1. La fattura è stata annullata.
1. Viene visualizzato un messaggio di operazione riuscita: *Hai annullato la fattura.*

<u>Risultati effettivi</u>:

Viene visualizzata una pagina di errore 404: *Pagina non trovata.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

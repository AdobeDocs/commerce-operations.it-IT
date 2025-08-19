---
title: 'ACSD-65938: e-mail con gift card inviate anche quando la creazione della fattura non è riuscita'
description: Applicare la patch ACSD-65938 per risolvere il problema Adobe Commerce in cui le e-mail gift card sono state inviate prima del salvataggio e del commit della fattura, garantendo che le e-mail vengano attivate dopo il salvataggio corretto della fattura.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938: e-mail con gift card inviate anche quando la creazione della fattura non è riuscita

La patch ACSD-65938 risolve un problema in cui le e-mail gift card venivano inviate prima del salvataggio e del commit della fattura. Con questa correzione, le e-mail ora vengono attivate solo dopo che la fattura è stata salvata correttamente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-65938. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail delle gift card sono state inviate prima di confermare che la fattura è stata creata e salvata correttamente, con conseguente invio di e-mail anche quando la creazione della fattura non è riuscita.

<u>Passaggi da riprodurre</u>:

1. Accedere al pannello **[!UICONTROL Admin]**.
2. Passare a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]** e impostare **[!UICONTROL Generate Gift Card Account when Order Item is]** su *Fatturato*.
3. Crea un nuovo prodotto gift card.
4. Aggiungi il prodotto del carrello regalo al carrello e procedi a **[!UICONTROL checkout]**. È possibile utilizzare **[!UICONTROL Check/Money Order]** come metodo di pagamento.
5. Effettua l’ordine.
6. Modificare `OrderRepository` per simulare un&#39;eccezione durante il posizionamento dell&#39;ordine.
7. Invia una richiesta POST a `rest/default/V1/order/<ORDER_ID>/invoice` con il seguente payload:

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Risultati previsti</u>:

Se la creazione della fattura non riesce, non deve essere inviata alcuna e-mail di gift card.

<u>Risultati effettivi</u>:

L&#39;e-mail della gift card viene inviata anche se la creazione della fattura non è riuscita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

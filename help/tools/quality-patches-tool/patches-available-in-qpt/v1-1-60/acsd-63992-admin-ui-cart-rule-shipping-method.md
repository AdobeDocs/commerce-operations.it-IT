---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] con coupon e errore di condizione del metodo di spedizione nell''interfaccia utente di amministrazione'
description: Applica la patch ACSD-63992 per risolvere il problema di Adobe Commerce per cui [!UICONTROL Cart Price Rule] con un coupon e una condizione basata su un metodo di spedizione non possono essere applicati correttamente tramite l'interfaccia utente di amministrazione.
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-63992: [!UICONTROL Cart Price Rule] con coupon e errore di condizione del metodo di spedizione nell&#39;interfaccia utente di amministrazione

La patch ACSD-63992 risolve il problema per cui [!UICONTROL Cart Price Rule] con un coupon e una condizione basata su un metodo di spedizione non possono essere applicati correttamente tramite l&#39;interfaccia utente di amministrazione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. L’ID della patch è ACSD-63992. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando una regola del carrello include una condizione per il metodo di spedizione nella sezione **[!UICONTROL Conditions]**, il codice coupon associato non viene applicato durante la creazione di un ordine tramite il pannello di amministrazione. Viene invece visualizzato il seguente errore:

_Il codice coupon &lt;> non è valido. Verificare il codice e riprovare._

<u>Passaggi da riprodurre</u>:

1. Crea una regola di prezzo del carrello e descrivine le condizioni:
   * In *[!UICONTROL Conditions]*: aggiungere una condizione per includere il metodo di spedizione, ad esempio *[!UICONTROL Flat Rate]*.
   * In *[!UICONTROL Rule Information]*: impostare **[!UICONTROL Coupon]** su *[!UICONTROL Specific Coupon]*, quindi immettere **[!UICONTROL Coupon Code]** come *TEST*.
1. Creare un nuovo ordine dal pannello di amministrazione e immettere il codice coupon *TEST* nel campo **[!UICONTROL Apply Coupon]**.

<u>Risultati previsti</u>:

Il coupon viene applicato correttamente.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

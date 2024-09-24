---
title: "ACSD-49389: messaggio e-mail pronto per il prelievo inviato dall’API quando non è pronto per il prelievo"
description: Applica la patch ACSD-49389 per risolvere il problema di Adobe Commerce, a causa del quale l’API invia un’e-mail pronta per il prelievo quando l’ordine non è pronto per il prelievo.
feature: REST, Communications
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: e-mail pronta per il prelievo inviata dall’API quando non è pronta per il prelievo

La patch ACSD-49389 risolve il problema per cui un’e-mail pronta per il prelievo viene inviata dall’API quando l’ordine non è pronto per il prelievo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-49389. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [pagina di destinazione QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l’ordine non è pronto per il prelievo, l’API invia un’e-mail pronta per il prelievo.

<u>Passaggi da riprodurre</u>:

1. Abilita il metodo *[!UICONTROL In-Store Delivery]*.
1. Creare un&#39;origine di magazzino con l&#39;ubicazione di prelievo abilitata.
1. Crea nuovo stock utilizzando il sito Web principale con l&#39;origine creata in precedenza.
1. Crea un prodotto assegnando la stessa origine.
1. Imposta qtà magazzino = 1.
1. Controllare il prodotto creato al passaggio 4 utilizzando il metodo *[!UICONTROL In-Store Delivery]* dalla vetrina.
1. Creare una fattura per l&#39;ordine.
1. Impostare la quantità del prodotto su *0* e renderlo esaurito.
1. Pubblica la seguente richiesta API:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Risultati previsti</u>:

L’e-mail pronta per il prelievo non viene inviata.

<u>Risultati effettivi</u>:

L&#39;API ha restituito *L&#39;ordine non è pronto per il prelievo*, ma l&#39;e-mail pronta per il prelievo è stata inviata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, consultare [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

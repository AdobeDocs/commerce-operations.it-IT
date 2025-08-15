---
title: 'ACSD-54966: Correzione per il riutilizzo dei codici coupon dopo ordini non riusciti'
description: Applica la patch ACSD-54966 per risolvere il problema di Adobe Commerce che impedisce il riutilizzo dei codici coupon limitati per promozioni e carrello a seguito di un ordine precedentemente non riuscito.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-54966: Correzione per il riutilizzo dei codici coupon dopo ordini non riusciti

La patch ACSD-54966 risolve il problema che impedisce il riutilizzo dei codici coupon limitati per cliente a seguito di un ordine precedentemente non riuscito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. L’ID della patch è ACSD-54966. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p10, 2.4.6 - 2.4.6-p8
* Adobe Commerce: 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un codice coupon, limitato all’uso singolo per cliente, non può essere riutilizzato in seguito a un ordine precedente non riuscito.

<u>Passaggi da riprodurre</u>:

1. Imposta una regola prezzo carrello con *[!UICONTROL Uses per Customer]* = *1*.
1. Procedi con un acquisto utilizzando il codice coupon assegnato.
1. Annulla l’ordine dal pannello di amministrazione o eseguilo con un errore di pagamento.
1. Esegui il comando: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Prova a effettuare un ordine successivo utilizzando lo stesso codice coupon per lo stesso cliente.

<u>Risultati previsti</u>:

Dopo aver annullato l’ordine o riscontrato un errore nel pagamento, il cliente può riutilizzare correttamente il codice del coupon per un nuovo acquisto.

<u>Risultati effettivi</u>:

Il cliente non è in grado di riutilizzare il codice coupon.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

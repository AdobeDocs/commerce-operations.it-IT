---
title: 'ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello'
description: La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754: punti premio non aggiunti dopo l’applicazione del coupon al carrello

La patch ACSD-45754 risolve il problema in cui i punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45754. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I punti premio non vengono aggiunti dopo l’applicazione di un coupon al carrello.

<u>Prerequisiti</u>:

Il metodo di pagamento PayPal è configurato.

<u>Passaggi da riprodurre</u>:

1. Crea tassi di cambio punti premio andando in **Store** > **Altre impostazioni** > **Premi tassi di cambio**.
1. Crea una regola di prezzo del carrello con un codice coupon per applicare 100 punti premio ai clienti connessi.
1. Consulta un prodotto come cliente connesso con PayPal e il codice del coupon.
1. Controlla la cronologia dei punti premio nell&#39;account cliente dell&#39;amministratore.

<u>Risultati previsti</u>:

I punti premio vengono aggiunti al cliente in base alla regola del prezzo.

<u>Risultati effettivi</u>:

Al cliente non vengono aggiunti punti premio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

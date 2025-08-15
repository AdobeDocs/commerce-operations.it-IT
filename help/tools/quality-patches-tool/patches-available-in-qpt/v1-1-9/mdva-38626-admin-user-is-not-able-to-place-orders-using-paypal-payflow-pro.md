---
title: 'MDVA-38626: l''utente amministratore non è in grado di effettuare ordini con PayPal Payflow Pro'
description: La patch MDVA-38626 risolve il problema che impediva all'utente amministratore di effettuare un ordine sul backend utilizzando il metodo di pagamento PayPal Payflow Pro. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-38626. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Payments
role: Admin
exl-id: 32d2e5dd-7081-42f2-a074-71e21c870dc2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-38626: l&#39;utente amministratore non è in grado di effettuare ordini con PayPal Payflow Pro

La patch MDVA-38626 risolve il problema che impediva all&#39;utente amministratore di effettuare un ordine sul backend utilizzando il metodo di pagamento PayPal Payflow Pro. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L&#39;ID della patch è MDVA-38626. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente amministratore non è in grado di effettuare ordini sul backend utilizzando il metodo di pagamento PayPal Payflow Pro.

<u>Passaggi da riprodurre</u>:

1. Configurare il metodo di pagamento PayPal Payflow Pro.
1. Vai a **Clienti** > **Tutti i clienti** e crea un account cliente.
1. Fai clic su **Crea ordine**.
1. Aggiungi qualsiasi elemento al carrello.
1. Provare a effettuare l&#39;ordine utilizzando Payflow Pro.

<u>Risultati previsti</u>:

L&#39;ordine viene effettuato.

<u>Risultati effettivi</u>:

L’utente riceve un errore 500. Il registro dei rapporti contiene:

```
{"0":"No such entity with cartId = 0","1":"#1 Magento\\Quote\\Model\\QuoteRepository->loadQuote() called at [app\/code\/Magento\/Quote\/Model\/QuoteRepository.php:136]\n#2 Magento\\Quote\\Model\\QuoteRepository->get() called at [lib\/internal\/Magento\/Framework\/Interception\/Interceptor.php:58]\n#3 Mag
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

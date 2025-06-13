---
title: 'MDVA-29400: ordini duplicati effettuati con PayPal Express Checkout'
description: La patch MDVA-29400 risolve il problema della creazione di ordini duplicati quando i clienti effettuano ordini con PayPal Express Checkout. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-29400. Il problema è stato risolto in Adobe Commerce 2.4.1.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400: ordini duplicati effettuati con PayPal Express Checkout

La patch MDVA-29400 risolve il problema della creazione di ordini duplicati quando i clienti effettuano ordini con PayPal Express Checkout. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L&#39;ID della patch è MDVA-29400. Il problema è stato risolto in Adobe Commerce 2.4.1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini duplicati vengono creati quando gli utenti effettuano ordini con PayPal Express Checkout.

<u>Prerequisiti</u>:

Abilitazione e configurazione di PayPal Express Checkout.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello.
1. Vai alla pagina Pagamento e utilizza PayPal Express come metodo di pagamento.
1. Sarà reindirizzato a paypal/express/review/page.
1. Ordinate. Verrai reindirizzato alla pagina di successo.
1. Torna a PayPal/express/review/page.
1. Fai clic sul pulsante **Inserisci ordine**.

<u>Risultati previsti</u>:

Viene creato un solo ordine.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore: *Il token di pagamento PayPal Express non esiste*, ma il secondo ordine è stato effettuato correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

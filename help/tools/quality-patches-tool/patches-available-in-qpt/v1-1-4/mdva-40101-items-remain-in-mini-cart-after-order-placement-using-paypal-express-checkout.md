---
title: 'MDVA-40101: Gli oggetti rimangono mini-cart dopo il posizionamento dell''ordine PayPal Express Checkout'
description: La patch MDVA-40101 risolve il problema che impedisce la rimozione degli articoli dal mini-carrello dopo il corretto inserimento dell'ordine tramite PayPal Express Checkout. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-40101. Il problema è stato risolto in Adobe Commerce 2.4.0.
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
exl-id: 8d3fa92e-39ed-4d8f-8dbe-9c08f787c6f1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-40101: Gli oggetti rimangono mini-cart dopo il posizionamento dell&#39;ordine PayPal Express Checkout

La patch MDVA-40101 risolve il problema che impedisce la rimozione degli articoli dal mini-carrello dopo il corretto inserimento dell&#39;ordine tramite PayPal Express Checkout. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L&#39;ID della patch è MDVA-40101. Il problema è stato risolto in Adobe Commerce 2.4.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli oggetti rimangono nel mini-carrello anche dopo un ordine effettuato con successo utilizzando PayPal Express Checkout.

<u>Passaggi da riprodurre</u>:

Effettuare un ordine utilizzando PayPal Express Checkout in modalità Incognito in un browser.

<u>Risultati previsti</u>:

Il mini-carrello deve essere vuoto dopo il completamento dell’ordine.

<u>Risultati effettivi</u>:

* La pagina di successo mostra un mini-carrello vuoto.
* Tutte le altre pagine mostrano il mini-carrello con gli articoli acquistati.
* Facendo clic sul collegamento del carrello, si viene reindirizzati a una pagina vuota del carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).

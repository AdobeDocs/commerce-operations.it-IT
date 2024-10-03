---
title: "MDVA-40961: impossibile aggiungere al carrello un elemento aggiuntivo quando la quantità minima di elemento è già nel carrello"
description: La patch MDVA-40961 risolve il problema che impedisce l'aggiunta di un articolo al carrello quando la quantità minima dell'articolo è già nel carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L'ID della patch è MDVA-40961. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961: impossibile aggiungere al carrello un elemento aggiuntivo quando la quantità minima di elemento è già nel carrello

La patch MDVA-40961 risolve il problema che impedisce l&#39;aggiunta di un articolo al carrello quando la quantità minima dell&#39;articolo è già nel carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L&#39;ID della patch è MDVA-40961. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile aggiungere un articolo aggiuntivo al carrello se la quantità minima dell&#39;articolo è già nel carrello.

<u>Passaggi da riprodurre</u>:

1. Impostare un prodotto semplice in modo che nel carrello sia consentita più di una **Quantità minima** (ad esempio, due).
1. Apri il prodotto sullo Storefront e aggiungine due al carrello.
1. Rimani nella pagina del prodotto e aggiungi un altro prodotto al carrello.

<u>Risultati previsti</u>:

Il terzo prodotto può essere aggiunto al carrello in quanto contiene già la quantità minima.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Il minor numero di acquisti è 2*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
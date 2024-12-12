---
title: 'ACSD-50949: il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU'
description: Applica la patch ACSD-50949 per risolvere il problema di Adobe Commerce, in cui il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU.
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949: il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato con il filtro SKU

La patch ACSD-50949 risolve il problema se il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti quando viene utilizzato insieme al filtro SKU. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33. L’ID della patch è ACSD-50949. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Problema

Il filtro del prezzo nella ricerca avanzata non restituisce risultati corretti se utilizzato insieme al filtro SKU.

<u>Passaggi da riprodurre</u>:

1. Crea diversi prodotti, ad esempio:

   | SKU | Nome | Prezzo | Quantità |
   |-----|-----------|-------|----------|
   | MJ1 | Prodotto 1 | $ 10 | 10 |
   | MJ2 | Prodotto 2 | $ 15 | 10 |
   | MJ3 | Prodotto 3 | $ 21 | 10 |
   | MJ4 | Prodotto 4 | $ 32 | 10 |
   | MJ5 | Prodotto 5 | $ 33 | 10 |
   | MJ6 | Prodotto 6 | $ 34 | 10 |
   | MJ7 | Prodotto 7 | $ 44 | 10 |

1. Apri **[!UICONTROL Advanced Search]** nella vetrina e cerca per SKU: &quot;MJ&quot;.
1. Fare clic sul collegamento **[!UICONTROL Modify your search]**.
1. Aggiungere un intervallo di prezzi ai criteri da *1* a *21* e fare clic sul pulsante **[!UICONTROL Search]**.

<u>Risultati previsti</u>:

Vengono restituiti solo i prodotti con prezzi compresi nell&#39;intervallo definito.

<u>Risultati effettivi</u>:

Vengono restituiti prodotti con prezzi superiori a *$21*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].

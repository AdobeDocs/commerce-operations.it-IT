---
title: 'ACSD-63299: il prezzo speciale di un prodotto configurabile non viene visualizzato nella vetrina'
description: Applicare la patch ACSD-63299 per risolvere il problema Adobe Commerce in cui l'attributo prezzo speciale non influisce più sulla visualizzazione dei prezzi speciali per i prodotti configurabili.
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: il prezzo speciale di un prodotto configurabile non viene visualizzato nella vetrina

La patch ACSD-63299 risolve il problema in cui l&#39;attributo prezzo speciale non influisce più sulla visualizzazione dei prezzi speciali per i prodotti configurabili. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63299. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

In [!DNL Adobe Commerce], la modifica del valore *Utilizzato nell&#39;elenco dei prodotti* per l&#39;attributo di prezzo speciale non influisce più sulla visualizzazione dei prezzi speciali per i prodotti configurabili.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Trovare l&#39;attributo ***[!UICONTROL special_price]*** e passare a **[!UICONTROL Storefront Properties]**.
1. Cambia ***[!UICONTROL Used in Product Listing]*** in ***[!UICONTROL No]***.
1. Crea un prodotto configurabile con un elemento figlio:
   * Nome e SKU: Test
   * Prezzo: $159,00
   * Genera l’opzione in base al colore. Aggiungi un nuovo colore: Blu
   * Salva
1. Apri il prodotto secondario e segui questi passaggi:
   * Imposta un prezzo speciale a $99,90 in **[!UICONTROL Advanced Pricing]**
   * Cambia [!UICONTROL Visibility] in **[!UICONTROL Catalog, Search]**.
1. Apri la pagina del prodotto semplice e conferma che il prezzo speciale sia visibile.
1. Apri la pagina del prodotto configurabile.
1. Seleziona il prodotto blu.

<u>Risultati previsti</u>:

Il prezzo speciale è visibile nello stesso modo in cui è per il prodotto semplice.

<u>Risultati effettivi</u>:

1. Il prezzo completo viene visualizzato quando si seleziona un prodotto configurabile.
1. Mancata corrispondenza tra le sezioni *Minima (...* ($99,90) e il prezzo effettivo ($99,90 + $59,10 = $159,00).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

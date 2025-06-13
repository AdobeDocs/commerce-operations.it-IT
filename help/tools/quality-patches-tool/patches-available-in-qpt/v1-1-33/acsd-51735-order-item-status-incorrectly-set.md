---
title: 'ACSD-51735: lo stato dell''articolo dell''ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando lo stock del prodotto è 0'
description: Applicare la patch ACSD-51735 per risolvere il problema Adobe Commerce in cui lo stato dell'articolo dell'ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando la scorta prodotto è 0.
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735: lo stato dell&#39;articolo dell&#39;ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando lo stock di prodotto è 0

La patch ACSD-51735 risolve il problema relativo all&#39;impostazione errata dello stato dell&#39;articolo dell&#39;ordine su *[!UICONTROL Ordered]* quando le scorte di prodotto sono pari a 0. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. L’ID della patch è ACSD-50895. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell&#39;articolo dell&#39;ordine non è impostato correttamente su *[!UICONTROL Ordered]* quando le scorte del prodotto sono pari a 0.

<u>Prerequisiti</u>:

* I moduli Adobe Commerce Inventory management (MSI) sono installati.
* Gli ordini inevasi sono abilitati in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Passaggi da riprodurre</u>:

1. Create un nuovo grezzo.
1. Crea una nuova origine.
1. Assegnate il sito Web predefinito al nuovo materiale e assegnate la nuova origine.
1. Crea un nuovo prodotto.

   * Impostare la Qtà di origine predefinita su 10 e la nuova Qtà di origine su 0.

1. Aggiungi il prodotto al carrello nella vetrina.
1. Osserva l’avviso dell’ordine inevaso al momento del pagamento, che indica che il prodotto proviene da una nuova origine.
1. Effettua l’ordine.
1. Apri l’ordine in Amministratore e controlla lo stato dell’ordine inevaso.

<u>Risultati previsti</u>:

L&#39;ordine mostra che Qtà 1 è in inevaso.

<u>Risultati effettivi</u>:

L&#39;ordine mostra che la Qtà 1 è ordinata, non in inevaso.

>[!MORELIKETHIS]
>
>[Lo stato dell&#39;elemento dell&#39;ordine non è impostato correttamente su *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

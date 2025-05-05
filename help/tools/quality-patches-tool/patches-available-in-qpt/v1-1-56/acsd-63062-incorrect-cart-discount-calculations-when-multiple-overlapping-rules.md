---
title: 'ACSD-63062: calcoli non corretti dello sconto sul carrello con più regole sovrapposte'
description: Applica la patch ACSD-63062 per risolvere il problema di Adobe Commerce, in cui si verificano calcoli non corretti dello sconto sul carrello quando vengono applicate più regole di sovrapposizione.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: calcoli non corretti dello sconto sul carrello con più regole sovrapposte

La patch ACSD-63062 risolve il problema relativo a calcoli non corretti degli sconti del carrello quando vengono applicate più regole di sovrapposizione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-63062. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si applicano più regole di sovrapposizione, si verificano calcoli di sconto sul carrello errati.

<u>Passaggi da riprodurre</u>:

1. Installa una nuova istanza con dati di esempio.
1. Crea tre prodotti semplici:

   * simple1: $1080
   * simple2: $260
   * simple3: $280

1. Creare quattro *[!UICONTROL Cart Price Rules]* come segue:

   * Regola 1:

      * *[!UICONTROL Priority]*: 100
      * Scheda *[!UICONTROL Conditions]*: usa prodotto simple2 ($280) se la quantità totale è uguale o maggiore di 3
      * Scheda *[!UICONTROL Actions]*: SKU semplice2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regola 2:

      * *[!UICONTROL Priority]*: 200
      * Scheda *[!UICONTROL Actions]*: SKU semplice2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * Regola 3:

      * *[!UICONTROL Priority]*: 300
      * Scheda *[!UICONTROL Conditions]*: il subtotale è uguale o maggiore di $1000
      * *[!UICONTROL Fixed Amount Discount]* per l&#39;intero carrello: $100

   * Regola 4:

      * *[!UICONTROL Priority]*: 400
      * Scheda *[!UICONTROL Conditions]*: usa prodotto simple1 ($1080) se la quantità totale è uguale o maggiore di 2
      * Scheda *[!UICONTROL Actions]*: lo SKU è semplice1
      * *[!UICONTROL Fixed Amount Discount]* per l&#39;intero carrello: $960

1. Vai alla vetrina e aggiungi al carrello i seguenti prodotti con la quantità specificata:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Controlla il carrello.

<u>Risultati previsti</u>:

Lo sconto applicato è di $1352.

<u>Risultati effettivi</u>:

Lo sconto applicato è $1525,33.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

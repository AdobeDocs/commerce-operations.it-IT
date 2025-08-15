---
title: 'ACSD-64149: è possibile salvare il segmento del cliente con una condizione [!UICONTROL Date range] quando viene modificata una sola data'
description: Applica la patch ACSD-64149 per risolvere il problema di Adobe Commerce, in cui è possibile salvare il segmento del cliente con una condizione **[!UICONTROL Date range]** quando viene modificata solo una delle date.
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-64149: è possibile salvare il segmento del cliente con una condizione [!UICONTROL Date range] quando viene modificata una sola data

La patch ACSD-64149 risolve il problema che consente di salvare un segmento del cliente con una condizione di intervallo di date quando viene modificata solo una delle date. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. L’ID della patch è ACSD-64149. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si modifica un segmento di clienti esistente con una condizione per i prodotti all&#39;interno del carrello specificato da un intervallo di date, il consumatore `matchCustomerSegmentProcessor` genera un errore SQL.

<u>Passaggi da riprodurre</u>:

1. Verificare che il consumer `matchCustomerSegmentProcessor` sia in esecuzione:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Passare a **[!UICONTROL Magento backend]**.
1. Vai a **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Fai clic su **[!UICONTROL Add Segment]**.
1. Immettere un **[!UICONTROL Segment Name]**, selezionare un sito Web in **[!UICONTROL Assigned to Website]** e assicurarsi che **[!UICONTROL Status]** sia impostato su *Attivo*.
1. Fare clic su **[!UICONTROL Save and Continue Edit]**.
1. Vai alla scheda **[!UICONTROL Conditions]** e aggiungi una nuova condizione: *Prodotti{} > {}Elenco prodotti*{*}*.
1. Aggiungere una sottocondizione per **[!UICONTROL Date range]** e impostare un **[!UICONTROL Date range]** valido.
1. Fare clic sul pulsante verde di conferma accanto a **[!UICONTROL Date range]**.
1. Fai di nuovo clic su **[!UICONTROL Date range]**, seleziona il selettore di date, modifica uno dei valori di data e conferma facendo clic sul pulsante verde.

<u>Risultati previsti</u>:

Il selettore **[!UICONTROL Date range]** non deve aggiungere l&#39;ora alla data durante la modifica.

<u>Risultati effettivi</u>:

* Il selettore **[!UICONTROL Date range]** aggiunge un orario alla data:
   * Una data ha solo la data, mentre l’altra ha sia la data che l’ora specificate.
* Nei registri viene visualizzato il seguente errore:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

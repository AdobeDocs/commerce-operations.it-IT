---
title: 'ACSD-63454: il valore predefinito per gli attributi a discesa e Selezione multipla non viene salvato correttamente nel database'
description: Applica la patch ACSD-63454 per risolvere il problema di Adobe Commerce, in cui il valore predefinito per gli attributi a discesa e Selezione multipla non viene salvato correttamente nel database.
feature: Attributes, Products
role: Admin, Developer
source-git-commit: 1c872ebeff05c0c84756d7abd7f43c4652032d3f
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# ACSD-63454: il valore predefinito per gli attributi [!UICONTROL Dropdown] e [!UICONTROL Multiple Select] non viene salvato correttamente nel database

La patch ACSD-63454 risolve il problema che causa il mancato salvataggio nel database del valore predefinito per gli attributi [!UICONTROL Dropdown] e [!UICONTROL Multiple Select]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-63454. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore predefinito per gli attributi [!UICONTROL Dropdown] e [!UICONTROL Multiple Select] non viene salvato correttamente nel database. Anziché aggiornare il valore predefinito, il nuovo valore viene aggiunto a quello precedente, separato da una virgola.

<u>Passaggi da riprodurre</u>:

1. Accedi al backend, passa a **[!UICONTROL Stores]** > [!UICONTROL Attributes] > **[!UICONTROL Product]**.
1. Fare clic su **[!UICONTROL Add New Attribute]**.
1. Nella scheda **[!UICONTROL Properties]**, impostare quanto segue:
   * [!UICONTROL Default Label] = test
   * [!UICONTROL Catalog Input Type for Store Owner]= [!UICONTROL Multiple Select]
   * [!UICONTROL Manage Options]: aggiungere 2 opzioni senza selezionare **[!UICONTROL Is Default]**.
1. Fare clic su **[!UICONTROL Save Attribute]**.
1. Verificare nel database che la colonna *default_value* sia vuota.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Tornare indietro e impostare una delle due opzioni come **[!UICONTROL Is Default]**.
1. Controlla nuovamente il database per assicurarti che *default_value* ora contenga l&#39;ID opzione selezionato.
1. Tornate indietro e modificate l&#39;opzione di default selezionando l&#39;altra opzione.

<u>Risultati previsti</u>:

Il nuovo valore predefinito deve sostituire il valore precedente nel database.

<u>Risultati effettivi</u>:

Invece di sostituire il valore predefinito con quello nuovo, il nuovo valore viene aggiunto al valore precedente, separato da una virgola.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

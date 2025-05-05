---
title: 'ACSD-63572: le tabelle temporanee dell’indicizzatore "catalogrule" non vengono pulite se il processo di indicizzazione è terminato'
description: Applicare la patch ACSD-63572 per risolvere il problema di Adobe Commerce per cui le tabelle di indicizzazione non vengono pulite quando il processo è stato terminato a causa di un aggiornamento del sistema o di un arresto in [!UICONTROL CLI].
feature: System
Role: Admin, Developers
source-git-commit: 588a543a8c0bfb8067f81e7131d0a53e5cdc340a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-63572: le tabelle temporanee dell&#39;indicizzatore `catalogrule` non vengono pulite se il processo di indicizzazione viene terminato

La patch di ACSD-63572 risolve il problema relativo alla mancata pulizia delle tabelle temporanee dell&#39;indicizzatore quando il processo è stato terminato a causa di un aggiornamento o di un&#39;interruzione del sistema in [!UICONTROL CLI]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63572. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le tabelle temporanee dell&#39;indicizzatore non vengono pulite quando il processo viene terminato a causa di un aggiornamento del sistema o di un arresto in [!UICONTROL CLI].

<u>Passaggi da riprodurre</u>:

1. Apri [!UICONTROL CLI].
1. Esegui comando: `bin/magento indexer:reindex catalogrule_rule`.
1. Annullare il processo prima che sia terminato utilizzando: `^C`.
1. Reimpostare gli indicizzatori utilizzando: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Ripetere più volte i passaggi precedenti.
1. Verificare la presenza delle tabelle temporanee seguenti create nel database:

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Risultati previsti</u>:

Le tabelle temporanee precedenti vengono eliminate quando non sono necessarie.

<u>Risultati effettivi</u>:

Le tabelle temporanee precedenti non vengono rimosse.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

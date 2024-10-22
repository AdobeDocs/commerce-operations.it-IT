---
title: "ACSD-59952: errore durante l’eliminazione del catalogo condiviso con lo stesso ID gruppo di un altro catalogo condiviso"
description: Applica la patch ACSD-59952 per risolvere il problema di Adobe Commerce in cui viene generato un errore durante l’eliminazione di un catalogo condiviso con lo stesso "customer_group_id" di un altro catalogo condiviso.
feature: B2B, REST
role: Admin, Developer
source-git-commit: a67f31aa905b420dcd2a17645734632d3f94520c
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACSD-59952: errore durante l’eliminazione del catalogo condiviso con lo stesso ID gruppo di un altro catalogo condiviso

La patch ACSD-59952 corregge l&#39;errore generato durante l&#39;eliminazione di cataloghi condivisi con lo stesso `customer_group_id` di un altro catalogo condiviso. Inoltre, impedisce agli utenti di creare tali cataloghi condivisi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-59952. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile creare un nuovo catalogo condiviso con lo stesso `customer_group_id` di un altro catalogo condiviso. Tuttavia, se si tenta di eliminare il catalogo condiviso con lo stesso `customer_group_id`, viene generato un errore.

<u>Prerequisiti</u>:

Installa i moduli B2B di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Crea più cataloghi condivisi assegnati allo stesso `customer_group_id` utilizzando la seguente chiamata API REST:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Prova a eliminare i cataloghi condivisi utilizzando la seguente chiamata API REST:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Risultati previsti</u>:

* Impossibile creare più cataloghi condivisi assegnati allo stesso `customer_group_id`.
* Il catalogo condiviso nel caso precedente è stato eliminato correttamente.

<u>Risultati effettivi</u>:

* È possibile creare più cataloghi condivisi assegnati allo stesso `customer_group_id`.
* Durante il tentativo di eliminare il catalogo condiviso con lo stesso `customer_group_id` viene restituito l&#39;errore seguente: *Impossibile eliminare il catalogo condiviso*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

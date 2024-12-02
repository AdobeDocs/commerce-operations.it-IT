---
title: 'MDVA-40550: prodotti mancanti sul fronte dopo la reindicizzazione'
description: La patch MDVA-40550 risolve il problema che causa la reindicizzazione e la mancanza di alcuni o di tutti i prodotti nelle categorie della vetrina. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. L'ID della patch è MDVA-40550. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550: prodotti mancanti sul fronte dopo la reindicizzazione

La patch MDVA-40550 risolve il problema che causa la reindicizzazione e la mancanza di alcuni o di tutti i prodotti nelle categorie della vetrina. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. L&#39;ID della patch è MDVA-40550. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto.
1. Cambia gli indicizzatori in **Aggiorna in base alla pianificazione**.
   * Assegna il prodotto a una categoria.
1. Abilitare xdebug e creare un punto di interruzione xdebug in `\Magento\Indexer\Model\Indexer::reindexAll` e `\Magento\Indexer\Model\IndexMutex::execute`.
1. Esegui una **reindicizzazione completa** di `catalog_category_product` con il comando:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Attendere l&#39;interruzione dell&#39;esecuzione nel punto di interruzione `\Magento\Indexer\Model\Indexer::reindexAll`.

1. In un&#39;altra console, esegui una **reindicizzazione parziale** in parallelo al comando:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Attendere l&#39;interruzione dell&#39;esecuzione nel punto di interruzione `\Magento\Indexer\Model\IndexMutex::execute`. L&#39;indicizzatore `catalog_category_product` verrà bloccato.
1. Riprendere l&#39;esecuzione della reindicizzazione completa di `catalog_category_product` e attendere un timeout di blocco (60 secondi).

<u>Risultati previsti</u>:

Nessun messaggio di errore nella console.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

*Impossibile acquisire il blocco per l&#39;indice: catalog_category_product.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

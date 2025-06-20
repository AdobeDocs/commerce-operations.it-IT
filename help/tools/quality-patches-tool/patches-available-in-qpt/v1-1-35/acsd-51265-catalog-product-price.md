---
title: 'ACSD-51265: Ottimizzare la reindicizzazione per i prodotti in bundle'
description: Applica la patch ACSD-51265 per risolvere il problema Adobe Commerce, in cui le prestazioni di reindicizzazione "catalog_product_price" sono basse quando il sistema contiene troppi prodotti in bundle.
feature: Products, Price Indexer
role: Admin
exl-id: 1a173ca7-f99e-42d8-87d7-81a6b33f2d4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-51265: Ottimizzare la reindicizzazione per i prodotti in bundle

La patch ACSD-51265 risolve il problema relativo alle prestazioni di reindicizzazione di `catalog_product_price` ridotte quando nel sistema sono presenti troppi prodotti in bundle. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-51265. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni di reindicizzazione del prezzo del prodotto del catalogo sono basse quando nel sistema sono presenti troppi prodotti in bundle.

<u>Passaggi da riprodurre</u>:

1. Genera un catalogo con almeno *10.000* prodotti in bundle con opzioni di prezzo dinamiche.
1. Esegui reindicizzazione prezzo prodotto.

<u>Risultati previsti</u>

La reindicizzazione del prezzo del prodotto richiede meno di 15 minuti.

<u>Risultati effettivi</u>

La reindicizzazione del prezzo del prodotto richiede più di un’ora.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

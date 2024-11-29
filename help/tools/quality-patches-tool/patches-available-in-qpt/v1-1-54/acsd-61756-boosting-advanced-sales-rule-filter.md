---
title: 'ACSD-61756: degradazione delle prestazioni dei filtri "AdvancedSalesRule" a causa di indici di database mancanti'
description: Applica la patch ACSD-61756 per risolvere il problema di Adobe Commerce, in cui la query "magento_salesrule_filter" esegue una scansione completa della tabella senza utilizzare gli indici, con conseguente deterioramento delle prestazioni durante la gestione di grandi volumi di record. Questa patch migliora le prestazioni aggiungendo gli indici di database mancanti per i filtri "AdvancedSalesRule".
feature: Price Rules, Price Indexer
role: Admin, Developer
source-git-commit: 42a376d1a791a17d88bea68dfef178a7b2849ce2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: riduzione delle prestazioni di `AdvancedSalesRule` filtri a causa di indici di database mancanti

Applicare la patch ACSD-61756 per migliorare le prestazioni dei filtri `AdvancedSalesRule` aggiungendo indici di database mancanti. In questo modo viene risolto il problema che comporta l&#39;esecuzione di una scansione completa della tabella da parte della query `magento_salesrule_filter` senza utilizzare gli indici, con conseguente deterioramento delle prestazioni in presenza di numerosi record nella tabella. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54. L’ID della patch è ACSD-61756. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p9

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query `magento_salesrule_filter` esegue un&#39;analisi completa della tabella senza utilizzare indici, con conseguente deterioramento delle prestazioni dei filtri `AdvancedSalesRule` quando la tabella contiene molti record.

<u>Passaggi da riprodurre</u>:

1. Estrai con più regole di vendita attive.

<u>Risultati previsti</u>:

Migliori prestazioni delle regole di vendita.

<u>Risultati effettivi</u>:

La query esegue una scansione completa della tabella e non utilizza gli indici, con conseguente deterioramento delle prestazioni quando la tabella contiene molti record.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

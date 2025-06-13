---
title: 'ACSD-55414: Prestazioni non buone quando MariaDB tenta di eseguire il cast di entitys_ids'
description: Applica la patch ACSD-55414 per risolvere il problema di Adobe Commerce quando MariaDB tenta di convertire "entitys_ids" da stringa a numero intero, ostacolando le prestazioni della reindicizzazione.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414: prestazioni non valide quando MariaDB tenta di eseguire il cast di `entitys_ids`

La patch di ACSD-55414 risolve il problema relativo alle prestazioni della reindicizzazione, che vengono ostacolate quando MariaDB tenta di convertire `entitys_ids` da stringa a numero intero. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.41. L’ID della patch è ACSD-55414. Tieni presente che il problema è risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni della reindicizzazione sono ostacolate quando MariaDB tenta di eseguire il cast di `entitys_ids` da stringa a numero intero.

<u>Passaggi da riprodurre</u>:

1. Aggiornare `setup/performance-toolkit/profiles/ce/small.xml` configurando *50000* prodotti semplici.
1. Generare questo profilo eseguendo il comando: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Esegui reindicizzazione: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Risultati previsti</u>:

Il completamento della reindicizzazione richiede un tempo ragionevole.

<u>Risultati effettivi</u>:

La reindicizzazione richiede troppo tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

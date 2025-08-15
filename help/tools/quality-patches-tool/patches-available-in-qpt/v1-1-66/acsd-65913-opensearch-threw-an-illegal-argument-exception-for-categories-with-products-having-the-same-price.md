---
title: 'ACSD-65913: [!DNL OpenSearch] genera un''eccezione_argomento_non valido per le categorie con prodotti aventi lo stesso prezzo'
description: Applica la patch ACSD-65913 per risolvere il problema Adobe Commerce in cui [!DNL Opensearch] genera un'eccezione legal_topic_exception ("[from] parametro non può essere negativa") sulle categorie contenenti tutti i prodotti con lo stesso prezzo.
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch] genera un `illegal_argument_exception` per le categorie con prodotti aventi lo stesso prezzo

La patch ACSD-65913 risolve il problema per cui [!DNL OpenSearch] ha generato un `illegal_argument_exception` per le categorie con prodotti che hanno lo stesso prezzo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-65913. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL OpenSearch] genera un parametro `illegal_argument_exception` (*[from] non può essere negativo*) durante il caricamento di categorie in cui tutti i prodotti hanno condiviso lo stesso prezzo.

<u>Passaggi da riprodurre</u>:

1. Installa [!DNL OpenSearch] versione 2.19.1 e impostalo come motore di ricerca predefinito.
1. Configura l&#39;attributo di prodotto **[!UICONTROL Price]** affinché sia visibile in navigazione a livelli:
   1. **[!UICONTROL Visible in Advanced Search]**: *Sì*
   1. **[!UICONTROL Comparable on Storefront]**: *Sì*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filtrabile (con risultati)*
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Imposta **[!UICONTROL Price Navigation Step Calculation]** su *Automatico (equalizza conteggi prodotti)*.
1. Crea una categoria con sei prodotti che hanno tutti lo stesso prezzo:
   1. SKU: product_super_0-1-1-1, Prezzo: $150
   1. SKU: product_super_0-1-1, Prezzo: $48
   1. SKU: product_super_0-1, Prezzo: $ 48
   1. SKU: product_super_0, Prezzo: $ 48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Prezzo: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1, Prezzo: $48
1. Esegui il comando seguente:
   `bin/magento indexer:reindex`
1. Apri la pagina della categoria. Viene visualizzato un errore:
   Il parametro *[from] non può essere negativo, trovato [-1]*

<u>Risultati previsti</u>:

[!DNL OpenSearch] non deve generare un `illegal_argument_exception` quando tutti i prodotti in una categoria hanno lo stesso prezzo.

<u>Risultati effettivi</u>:

* [!DNL OpenSearch] genera un `illegal_argument_exception` con il messaggio:
  Il parametro *[from] non può essere negativo, trovato [-1]*

* Il file `var/log/exception.log` contiene:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

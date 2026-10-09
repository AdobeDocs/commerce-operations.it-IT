---
title: 'ACSD-53925: impossibile salvare il blocco CMS con [!UICONTROL Product Carousel]'
description: Applica la patch ACSD-53925 per risolvere il problema di Adobe Commerce, in cui l’amministratore non è in grado di salvare un blocco CMS con Product Carousel quando la modalità dimensioni per "catalog_product_price" è impostata su sito web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%
---
# ACSD-53925: impossibile salvare il blocco CMS con *[!UICONTROL Product Carousel]*

La patch ACSD-53925 risolve il problema che impediva all&#39;amministratore di salvare un blocco CMS con *[!UICONTROL Product Carousel]* quando la modalità dimensioni per `catalog_product_price` è impostata su Sito Web. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.43. L’ID della patch è ACSD-53925. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non è in grado di salvare un blocco CMS con *[!UICONTROL Product Carousel]* quando la modalità dimensioni per `catalog_product_price` è impostata su Sito Web.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti semplici:
   * simple1 - $10
   * simple2 - $20
1. Creare un prodotto bundle &#39;*bundle1-dyn*&#39; con due opzioni basate su SKU di prodotto semplici.
1. Imposta modalità dimensioni per l&#39;indicizzatore prezzo prodotto:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** e crea un nuovo blocco CMS.
1. Modifica il contenuto utilizzando [!DNL Page Builder]:
   * Aggiungi un elemento *[!UICONTROL Row]*
   * Aggiungi un elemento *[!UICONTROL Products]*
   * Seleziona *[!UICONTROL Product Carousel]*
   * Immetti SKU prodotto - *bundle1-dyn*
1. Salva il blocco CMS.

<u>Risultati previsti</u>:

L’utente può aggiungere un carosello di prodotto senza errori.

<u>Risultati effettivi</u>:

* Messaggio generato nell&#39;interfaccia utente: *Si è verificato un errore durante la generazione del contenuto*
* `var/log/exception.log` contiene il seguente errore:

  ```text
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

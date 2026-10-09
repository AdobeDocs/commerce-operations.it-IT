---
title: 'ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* impostato su Sì senza l''opzione *[!UICONTROL Use in Search]*'
description: Applicare la patch ACSD-50887 per risolvere il problema di Adobe Commerce per cui la proprietà dell'attributo del prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostata su *Yes* senza che anche l'opzione *[!UICONTROL Use in Search]* sia impostata su *Yes*.
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: 5e797121-c386-4aca-9139-0a02a60be38a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-50887: *[!UICONTROL Use in Search Results Layered Navigation]* impostato su *Sì* senza l&#39;opzione *[!UICONTROL Use in Search]*

La patch ACSD-50887 risolve il problema per cui la proprietà dell&#39;attributo di prodotto *[!UICONTROL Use in Search Results Layered Navigation]* può essere impostata su *Sì* senza che anche l&#39;opzione *[!UICONTROL Use in Search]* sia impostata su *Sì*. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-50887. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile impostare la proprietà dell&#39;attributo di prodotto *[!UICONTROL Use in Search Results Layered Navigation]* su *Yes* senza impostare anche l&#39;opzione *[!UICONTROL Use in Search]* su *Yes*.

Queste impostazioni sono state progettate per essere utilizzate insieme. Con la patch applicata, quando l&#39;opzione *[!UICONTROL Use in Search]* è impostata su *No*, l&#39;opzione *[!UICONTROL Use in Search Results Layered Navigation]* è nascosta e funziona come se fosse impostata anche su *No*.

<u>Passaggi da riprodurre</u>:

1. In Amministrazione, passare a **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** e creare un attributo con il tipo a selezione multipla e impostare quanto segue:

   * *[!UICONTROL Use in Search]= No*
   * *[!UICONTROL Use in Layered Navigation]= (Qualsiasi opzione)*
   * *[!UICONTROL Use in Search Results Layered Navigation]= Sì*
   * *Nome = Test_attribute*
   * *Opzioni*:
     * *Sticker*
     * *Selettore*

1. Aggiungere il nuovo attributo al set di attributi predefinito.
1. Crea due prodotti:

   1. Primo prodotto:
      * Nome = Sticker
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = opzione di selezione *Sticker*

   1. Secondo prodotto:
      * Nome = Selettore
      * Imposta prezzo, QTÀ, Peso su 1
      * Test_attribute = seleziona entrambe le opzioni

1. Esegui reindicizzazione `catalogsearch_fulltext`:

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. Effettua la ricerca in base alla parola *sticker* nella vetrina.

<u>Risultati previsti</u>:

Viene restituito solo il prodotto *Sticker*, perché [!DNL Elasticsearch] non indicizza Test_attribute quando *[!UICONTROL Use in Search]* è stato impostato su *No*.

<u>Risultati effettivi</u>:

Entrambi i prodotti vengono restituiti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-45168: URL descrittivi SEO non generati per prodotti con attributi url_key sostituiti'
description: Applica la patch ACSD-45168 per risolvere il problema di Adobe Commerce, in cui gli URL compatibili con SEO non vengono generati per i prodotti con attributi url_key sostituiti a livello di visualizzazione dello store.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%
---
# ACSD-45168: URL descrittivi SEO non generati per prodotti con attributi url_key sostituiti

La patch ACSD-45168 risolve il problema della mancata generazione di URL compatibili con SEO per i prodotti con attributi url_key sostituiti a livello di visualizzazione store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-45168. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli URL compatibili con SEO non vengono generati per i prodotti con attributi url_key sostituiti a livello di visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Impostare la configurazione come segue passando a **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Sì*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Sì*
1. Pulisci la cache di configurazione.
1. Creare due categorie: [!UICONTROL Category 1] e [!UICONTROL Category 2].
1. Creare due prodotti: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Modificare l&#39;ambito in [!UICONTROL Default Store View] per [!UICONTROL Product 1].
1. Deselezionare l&#39;URL facoltativo [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Salva il prodotto.
1. Torna a [!UICONTROL All Store Views].
1. Aggiungi [!UICONTROL Product 1] a [!UICONTROL Category 2] e aggiungi [!UICONTROL Product 2] a [!UICONTROL Category 2].
1. Controllare la tabella `url_rewrite` o [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Risultati previsti</u>:

L&#39;URL compatibile con SEO per [!UICONTROL Category 2] è stato creato per [!UICONTROL Product 1].

<u>Risultati effettivi</u>:

URL compatibile con SEO per [!UICONTROL Category 2] mancante per [!UICONTROL Product 1] perché l&#39;attributo chiave URL è stato sovrascritto per l&#39;ambito di visualizzazione archivio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud

## Lettura correlata

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

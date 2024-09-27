---
title: "ACSD-56023: il contenuto del widget non viene aggiornato nella pagina CMS"
description: Applica la patch ACSD-56023 per risolvere il problema di Adobe Commerce, se il contenuto del widget non viene aggiornato nella pagina CMS
feature: CMS
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56023: il contenuto del widget non viene aggiornato nella pagina CMS

La patch ACSD-56023 risolve il problema se il contenuto del widget non viene aggiornato nella pagina CMS. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44. L’ID della patch è ACSD-56023. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il contenuto del widget non viene aggiornato nella pagina CMS.

<u>Passaggi da riprodurre</u>:

1. Crea alcuni prodotti.
1. Crea la nuova pagina CMS e aggiungi nuovi widget di prodotti al contenuto:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Apri la pagina creata nella vetrina. Assicurati di memorizzarlo nella cache.
1. Dall&#39;amministratore, aprire **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Selezionare un prodotto da modificare e passare da **[!UICONTROL Set Product as New]** a *Sì*.
1. Vai di nuovo alla *pagina CMS* creata nella vetrina.

<u>Risultati previsti</u>:

La pagina contiene *nuovi widget Prodotti* con i prodotti.

<u>Risultati effettivi</u>:

La pagina non contiene *widget Nuovi prodotti* e i nuovi prodotti non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-54972: l’URL della categoria canonica non viene aggiornato'
description: Applica la patch ACSD-54972 per risolvere il problema di Adobe Commerce per cui l’URL canonico della categoria non viene aggiornato dopo la modifica dell’URL della categoria.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972: l’URL della categoria canonica non viene aggiornato dopo la modifica dell’URL della categoria

La patch ACSD-54972 risolve il problema che impedisce l’aggiornamento dell’URL canonico di una categoria in seguito alla modifica dell’URL della categoria. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43. L’ID della patch è ACSD-54972. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’URL canonico della categoria non viene aggiornato dopo la modifica dell’URL della categoria.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * Imposta *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *SÌ*

2. Crea una categoria (ad esempio, *Nome*: *Categoria 01*, *Chiave URL*: *categoria-01*).
3. Aggiorna la chiave *URL* in un valore diverso da quello originale mantenendo selezionata la casella di controllo **[!UICONTROL Create Permanent Redirect for old URL]**.
4. Pulire la cache.
5. Vai a *[!UICONTROL Category Page]* sul front-end.
6. Controlla l&#39;origine della pagina e cerca il tag *canonical*.

<u>Risultati previsti</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Risultati effettivi</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

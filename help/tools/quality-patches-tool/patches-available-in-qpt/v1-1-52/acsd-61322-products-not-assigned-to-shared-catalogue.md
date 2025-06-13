---
title: 'ACSD-61322: i prodotti non assegnati a [!UICONTROL Shared Catalogue] sono inclusi in XML Sitemap'
description: Applicare la patch ACSD-61322 per risolvere il problema di Adobe Commerce, in cui prodotti/categorie non assegnati al gruppo [!UICONTROL Shared Catalog] per il gruppo predefinito (Generale) sono ancora inclusi in XML Sitemap.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: i prodotti non assegnati a [!UICONTROL Shared Catalogue] sono inclusi in XML Sitemap

La patch ACSD-61322 risolve il problema per cui prodotti/categorie non assegnati al gruppo [!UICONTROL Shared Catalog] per il gruppo predefinito (Generale) sono ancora inclusi in XML Sitemap. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-61322. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Prodotti/categorie non assegnati a [!UICONTROL Shared Catalog] per il gruppo Predefinito (Generale) sono ancora inclusi in XML Sitemap.

<u>Passaggi da riprodurre</u>:

1. Crea alcune categorie e aggiungi prodotti (ad esempio, Categoria 1 con Categoria 2).
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e abilita *[!UICONTROL Company and Shared Catalog]*.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e modifica il catalogo predefinito.
1. Dal menu a discesa **[!UICONTROL Select]**, selezionare **[!UICONTROL Set Pricing and Structure]** e fare clic su **[!UICONTROL Configure]**.
1. Nella categoria *Categoria 1 > Categoria 2*, deselezionare alcuni prodotti che non dovrebbero essere nella categoria [!UICONTROL Shared Catalog].
1. Fare clic su **[!UICONTROL Next]** e generare il catalogo.
1. Nella vetrina, crea un account cliente.
1. Passa alla categoria *Categoria 1 > Categoria 2*. Vengono visualizzati solo i prodotti assegnati a [!UICONTROL Shared Catalog].
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** e genera una nuova sitemap.
1. Apri `sitemap.xml` nella vetrina.
1. Cerca i prodotti che non hai incluso in [!UICONTROL Shared Catalog].

<u>Risultati previsti</u>:

La mappa del sito non contiene collegamenti a prodotti e categorie non assegnati a [!UICONTROL Shared Catalog].

<u>Risultati effettivi</u>:

La mappa del sito contiene collegamenti a prodotti e categorie non assegnati a [!UICONTROL Shared Catalog].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

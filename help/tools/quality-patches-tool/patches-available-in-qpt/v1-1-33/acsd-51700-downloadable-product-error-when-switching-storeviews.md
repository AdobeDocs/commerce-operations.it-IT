---
title: 'ACSD-51700: errore nel cambiare le visualizzazioni dello store nella pagina di modifica del prodotto scaricabile'
description: Applica la patch ACSD-51700 per risolvere il problema di Adobe Commerce in cui si verifica un errore quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile nell’amministratore.
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700: errore nel cambiare le visualizzazioni dello store nella pagina di modifica del prodotto scaricabile

La patch ACSD-51700 risolve il problema relativo a un errore che si verifica quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile dall’amministratore. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51700. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

## Problema

Si verifica un errore quando si passa da una visualizzazione store a una pagina di modifica del prodotto scaricabile nell’amministratore.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto scaricabile con nome, [!DNL SKU] e prezzo. Non aggiungere collegamenti e salva il prodotto.
1. Passa da tutte le visualizzazioni dello store alla visualizzazione predefinita dello store.
1. Crea un collegamento per il prodotto scaricabile e salvalo.
1. Passa dalla visualizzazione predefinita dello store a tutte le visualizzazioni dello store.

<u>Risultati previsti</u>:

I prodotti collegati sono visibili.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

*Funzionalità obsoleta: number_format(): il passaggio del valore null al parametro #1 ($num) di tipo float è stato dichiarato obsoleto in vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php alla riga 228*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

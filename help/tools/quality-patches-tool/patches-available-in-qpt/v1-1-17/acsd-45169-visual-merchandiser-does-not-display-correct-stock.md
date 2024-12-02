---
title: 'ACSD-45169: Visual Merchandiser mostra azioni e prezzi errati per prodotti configurabili'
description: La patch ACSD-45169 risolve il problema che causa la mancata visualizzazione da parte di Visual Merchandiser del prezzo e delle azioni corretti per un prodotto configurabile dopo l'applicazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45169. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
exl-id: 3f1218ee-2fd0-4f3e-80d7-7e6f9342e0fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169: Visual Merchandiser mostra azioni e prezzi errati per prodotti configurabili

La patch ACSD-45169 risolve il problema che causa la mancata visualizzazione da parte di Visual Merchandiser del prezzo e delle azioni corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45169. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

In Visual Merchandiser non vengono visualizzati il prezzo e le azioni corretti per un prodotto configurabile dopo l&#39;applicazione di un aggiornamento di staging.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea qualsiasi aggiornamento pianificato per il prodotto semplice (è sufficiente disporre di ID di riga ed entità diversi).
1. Crea un prodotto configurabile.
1. Assegna il prodotto configurabile a una categoria.
1. Apri la categoria e osserva il prodotto configurabile nella sezione Visual Merchandiser.

<u>Risultati previsti</u>:

In Visual Merchandiser vengono visualizzati il titolo e il prezzo corretti.

<u>Risultati effettivi</u>:

In Visual Merchandiser vengono visualizzati un prezzo e un titolo errati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: "MDVA-27239: i prodotti di cross-selling non vengono visualizzati"
description: La patch MDVA-27239 risolve il problema della mancata visualizzazione dei prodotti di cross-selling. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Il problema è stato risolto in Adobe Commerce 2.3.6.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: i prodotti di cross-selling non vengono visualizzati

La patch MDVA-27239 risolve il problema della mancata visualizzazione dei prodotti di cross-selling. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Il problema è stato risolto in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4, 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti di cross-selling non vengono visualizzati nel blocco di cross-selling nella pagina del carrello.

<u>Prerequisiti</u>:

1. Disattiva il modulo Magento_TargetRule o rimuovi dal blocco di layout Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Crea prodotto 1.
1. Crea un aggiornamento della pianificazione per il prodotto 1, in modo che i prodotti appena creati abbiano row_id diverso da entity_id.
1. Creare i prodotti 2, 3 e 4.
1. Impostare Prodotto 3 come cross-selling per Prodotto 4.
1. Impostare Prodotto 4 come cross-selling per Prodotto 2.

<u>Passaggi da riprodurre</u>:

1. Aggiungi Prodotto 4 e Prodotto 2 al carrello.
1. Controlla la pagina del carrello.

<u>Risultati previsti</u>:

Il prodotto 3 viene visualizzato in un blocco di cross-selling.

<u>Risultati effettivi</u>:

Il blocco di cross-selling è vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

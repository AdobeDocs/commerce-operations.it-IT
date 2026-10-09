---
title: 'MDVA-40488: prodotti configurabili con prodotti secondari esauriti non visualizzati nell''intervallo di prezzo corretto'
description: La patch MDVA-40488 risolve il problema se i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-40488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Configuration, Orders, Products
role: Admin
exl-id: 9a843d1b-88df-4bd7-a358-3aa34c436bdf
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%
---
# MDVA-40488: prodotti configurabili con prodotti secondari esauriti non visualizzati nell&#39;intervallo di prezzo corretto

La patch MDVA-40488 risolve il problema se i prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-40488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti configurabili con prodotti secondari esauriti non vengono visualizzati nella giusta fascia di prezzo.

<u>Prerequisiti</u>:

Vai a Amministrazione Commerce > **store** > **configurazione** > **catalogo** > **Inventario** > **stock options** e imposta la configurazione **Visualizza prodotti esauriti** su *Sì*.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con due prodotti associati. Ad esempio: prodotti semplici Rosso e Marrone.
1. Imposta l&#39;inventario del prodotto semplice rosso e lo stato del magazzino su *In magazzino*, quindi imposta lo stato Abilita prodotto su *No*.
1. Impostare l&#39;inventario del prodotto semplice Brown, quindi impostare lo stato Abilita prodotto su *Sì*.
1. Assicurati che lo stato del magazzino del prodotto configurabile sia *In magazzino*.
1. Modificare l&#39;inventario del prodotto semplice Brown su 0 e impostare lo stato Stock su *esaurito*.
1. A questo punto, lo stato del magazzino del prodotto configurabile è ancora *In magazzino*.
1. Eseguire la reindicizzazione.
1. Controllare `min_price` e `max_price` per il prodotto configurabile nella tabella del database `catalog_product_index_price`. I due valori sono impostati su 0.
1. Ma se impostiamo lo stato del magazzino del prodotto configurabile su *esaurito* ed eseguiamo la reindicizzazione, possiamo vedere valori diversi da zero `min_price` e `max_price` del prodotto configurabile.

<u>Risultati previsti</u>:

Se tutti i prodotti secondari sono *esauriti* e il prodotto configurabile stesso è anche *esaurito*, il prezzo viene calcolato utilizzando tutti i prodotti secondari.

<u>Risultati effettivi</u>:

I valori `min_price` e `max_price` per il prodotto configurabile nella tabella del database `catalog_product_index_price` sono impostati su 0 quando lo stato delle scorte configurabili è *In magazzino*, ma se è *Esaurito* diventano valori diversi da zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

---
title: 'MDVA-39482: il prodotto esaurisce le scorte se viene importato con la quantità ''0'' con ordini inevasi abilitati'
description: MDVA-39482 risolve il problema relativo all'esaurimento delle scorte del prodotto importato con quantità pari a "0" quando MSI e gli ordini inevasi sono attivati e la soglia delle scorte esaurite è impostata su un valore meno. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-39482. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Data Import/Export, Orders, Products
role: Admin
exl-id: 9d705ebf-2372-4e59-b447-cdb5b0db32f4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482: il prodotto esaurisce le scorte se viene importato con la quantità &#39;0&#39; con ordini inevasi abilitati

MDVA-39482 risolve il problema relativo all&#39;esaurimento delle scorte del prodotto importato con quantità pari a &quot;0&quot; quando MSI e gli ordini inevasi sono attivati e la soglia delle scorte esaurite è impostata su un valore meno. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L&#39;ID della patch è MDVA-39482. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se viene importata con una quantità pari a &quot;0&quot;, il prodotto esaurisce le scorte quando MSI e gli ordini inevasi sono abilitati e la soglia delle scorte esaurite è impostata su un valore meno.

<u>Prerequisiti</u>:

1. È necessario installare MSI e i dati di esempio.
1. Vai a **Archivi** > **Configurazioni** > **Catalogo** > **Inventario**:
   * Imposta ordini arretrati su &quot;Consenti quantità inferiore a 0&quot;
   * Imposta soglia esaurita su &quot;-10&quot;

<u>Passaggi da riprodurre</u>:

1. Assicurati che lo SKU sia **In magazzino** e abbia una quantità di **24-MB01**.
1. Importa il file CSV delle origini Stock. Accertatevi di selezionare &quot;Origini magazzino&quot; in Tipo entità:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Controllare lo stato delle scorte del prodotto dopo l&#39;importazione delle origini delle scorte.

<u>Risultati previsti</u>:

24-MB01 è **Disponibile** in Storefront.

<u>Risultati effettivi</u>:

24-MB01 è **esaurito** in Storefront.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).

---
title: 'MDVA-39181: le regole di prodotto correlate mostrano i prodotti della categoria non definiti nella regola'
description: La patch MDVA-39181 risolve il problema che causa la visualizzazione di prodotti di una categoria non definita nella regola da parte di regole di prodotto correlate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-39181. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: le regole di prodotto correlate mostrano i prodotti della categoria non definiti nella regola

La patch MDVA-39181 risolve il problema che causa la visualizzazione di prodotti di una categoria non definita nella regola da parte di regole di prodotto correlate. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-39181. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le regole di prodotto correlate mostrano i prodotti di categorie non definite nella regola.

<u>Prerequisiti</u>:

Installa i dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Creare un marchio di attributi e aggiungerlo al **Set di attributi superiore**.
1. Scegli **Josie**, **Augusta** e **Ingrid** giacche da aggiungere a Brand Kitty da **Women** > **Tops** > **Categoria giacche**.
1. Scegli **giacche Beaumont**, **Hyperion** e **Kenobi** da aggiungere a Brand Kitty da **Uomini** > **Cime** > **Categoria giacche**.
1. Crea un prodotto correlato con:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Prodotti corrispondenti:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Prodotti da visualizzare:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Apri SKU WJ04 dal front-end e controlla i prodotti correlati.
1. Aggiorna l&#39;ID categoria da **Donne** > **Cime** > **Giacche** nel caso sia diverso da questo.

<u>Risultati previsti</u>:

Solo i prodotti della stessa marca e della stessa categoria secondaria sono visualizzati nei prodotti correlati.

<u>Risultati effettivi</u>:

I prodotti correlati sono mostrati dello stesso marchio ma da una categoria padre casuale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

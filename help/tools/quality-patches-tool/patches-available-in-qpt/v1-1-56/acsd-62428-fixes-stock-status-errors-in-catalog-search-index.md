---
title: 'ACSD-62428: errori di stato del magazzino nell’indice di ricerca del catalogo'
description: Applica la patch ACSD-62428 per risolvere il problema in cui il valore "is_out_of_stock" nell’indice di ricerca del catalogo non viene impostato correttamente quando lo SKU non è come attributo ricercabile.
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: errori di stato del magazzino nell’indice di ricerca del catalogo

La patch ACSD-62428 risolve il problema in cui i valori `is_out_of_stock` nell&#39;indice di ricerca del catalogo sono impostati su un valore errato quando l&#39;attributo SKU non è impostato come ricercabile. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62428. Il problema era pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore `is_out_of_stock` nell&#39;indice di ricerca del catalogo è impostato su un valore errato quando lo SKU non è configurato come attributo ricercabile, causando una rappresentazione non accurata delle scorte.

<u>Passaggi da riprodurre</u>:

1. Creare un [!UICONTROL Source] personalizzato e un [!UICONTROL Stock] personalizzato.
1. Creare tre semplici prodotti e assegnare il relativo inventario a [!UICONTROL Source] personalizzato. Assegna questi prodotti a una categoria.
1. Impostare *[!UICONTROL Inventory (MSI) Indexer]* su *[!UICONTROL Update on Save]* per semplificare la replica.
1. Imposta *[!UICONTROL Source Item Status]* su *[!UICONTROL In Stock]* e assegna *[!UICONTROL Quantity]*.
1. Salva il prodotto.
1. Passare a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e aprire l&#39;attributo **[!UICONTROL SKU]**.
1. Imposta *[!UICONTROL Use In]* su *[!UICONTROL No]*.
1. Modificare la quantità di prodotto (assicurarsi che non sia impostata su 0).
1. Salva il prodotto.

<u>Risultati previsti</u>:

Il valore `is_out_of_stock` riflette con precisione lo stato delle scorte del prodotto, anche quando lo SKU non è un attributo ricercabile.

<u>Risultati effettivi</u>:

Il valore `is_out_of_stock` non è impostato correttamente su 1 e l&#39;attributo SKU è assente nei dati indicizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

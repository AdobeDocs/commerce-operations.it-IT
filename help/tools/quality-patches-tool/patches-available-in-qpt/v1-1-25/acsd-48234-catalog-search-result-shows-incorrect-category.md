---
title: 'ACSD-48234: risultato della ricerca catalogo errato nel conteggio degli elementi della categoria quando [!UICONTROL Display Out of Stock Products] è abilitato'
description: Applicare la patch ACSD-48234 per risolvere il problema di Adobe Commerce, in cui il risultato della ricerca nel catalogo mostra un conteggio di elementi di categoria errato quando l'opzione [!UICONTROL Display Out of Stock Products] è abilitata.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: il risultato della ricerca nel catalogo indica che il conteggio degli elementi di categoria **[!UICONTROL Display Out of Stock Products]** è abilitato non corretto

La patch di ACSD-48234 risolve il problema relativo alla visualizzazione di un numero di elementi di categoria non corretto da parte del risultato della ricerca nel catalogo quando l&#39;opzione **[!UICONTROL Display Out of Stock Products]** è abilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-48234. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.


## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il risultato della ricerca nel catalogo mostra un conteggio degli elementi di categoria errato quando l&#39;opzione **[!UICONTROL Display Out of Stock Products]** è abilitata.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e apri l&#39;attributo **[!UICONTROL color]**.
1. Aggiungi due opzioni, ad esempio arancione e verde. Salva l’attributo.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** e aggiungi l&#39;attributo **[!UICONTROL color]** al set di attributi **[!UICONTROL Default]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e imposta **[!UICONTROL Display Out of Stock Products]** su _Sì_.
1. Crea la categoria &quot;cat1&quot;.
1. Crea due prodotti:
   1. Nome: prod1, Colore: arancione, Categorie: cat1.
   1. Nome: prod2, Colore: verde, Categorie: cat1.
1. Apri la categoria cat1 nella vetrina.
1. Selezionare il colore arancione nella navigazione a livelli.

<u>Risultati previsti</u>:

Viene visualizzato solo il prodotto prod1.

<u>Risultati effettivi</u>:

Vengono visualizzati sia i prodotti prod1 che prod2.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-49628: [!DNL Page Builder] Gli errori CORS impediscono il salvataggio del prodotto'
description: Applica la patch ACSD-49628 per risolvere il problema di Adobe Commerce in cui gli errori  [!DNL Page Builder] CORS impediscono il salvataggio del prodotto.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] errori CORS impediscono il salvataggio del prodotto

La patch ACSD-49628 risolve il problema in cui [!DNL Page Builder] errori CORS impediscono a un amministratore di salvare un prodotto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-49628. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL Page Builder] errori CORS impediscono il salvataggio di un prodotto.

<u>Passaggi da riprodurre</u>:

1. Accedi come amministratore.
1. Crea un ruolo utente con le seguenti autorizzazioni:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Non aggiungere autorizzazioni *[!UICONTROL Content]*.
1. Crea un altro utente amministratore e assegna a questo utente i ruoli creati in precedenza.
1. Crea un prodotto e disconnettiti.
1. Accedi come secondo amministratore.
1. Prova a modificare e salvare il prodotto.

<u>Risultati previsti</u>:

Il secondo amministratore è in grado di salvare il prodotto, ma il pulsante **[!UICONTROL Edit with Page Builder]** non viene visualizzato all&#39;amministratore senza alcuna autorizzazione *[!UICONTROL Content]*.

<u>Risultati effettivi</u>:

Il secondo amministratore non è in grado di salvare il prodotto a causa di più errori di [!DNL Page Builder].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

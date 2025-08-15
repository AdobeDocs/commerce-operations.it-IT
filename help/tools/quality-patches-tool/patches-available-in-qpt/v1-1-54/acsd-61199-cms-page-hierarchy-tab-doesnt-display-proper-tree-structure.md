---
title: 'ACSD-61199: la scheda della pagina [!UICONTROL Hierarchy] di CMS non visualizza la struttura ad albero corretta'
description: Applica la patch ACSD-61199 per risolvere il problema Adobe Commerce, se nella scheda *[!UICONTROL Hierarchy]* della pagina CMS non viene visualizzata una struttura ad albero corretta durante la modifica di una pagina CMS con un *[!UICONTROL Hierarchy]* esistente.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: la scheda [!UICONTROL Hierarchy] della pagina CMS non visualizza la struttura ad albero corretta

La patch ACSD-61199 risolve il problema per cui nella scheda *[!UICONTROL Hierarchy]* della pagina CMS non viene visualizzata una struttura ad albero corretta quando si modifica una pagina CMS con un *[!UICONTROL Hierarchy]* esistente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61199. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella scheda *[!UICONTROL Hierarchy]* della pagina CMS non viene visualizzata una struttura ad albero corretta quando si modifica una pagina CMS con un *[!UICONTROL Hierarchy]* esistente.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Crea un nuovo **[!UICONTROL CMS page]**. Viene aggiunto alla directory principale del sito Web in *[!UICONTROL Hierarchy]*.
1. Salva la pagina.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Aggiungere altre pagine esistenti a *[!UICONTROL Hierarchy]*.
1. Salva *[!UICONTROL Hierarchy]*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Modificare le pagine esistenti e aprire *[!UICONTROL Hierarchy]*.

<u>Risultati previsti</u>:

*[!UICONTROL Hierarchy]* viene caricato come previsto.

<u>Risultati effettivi</u>:

*[!UICONTROL Hierarchy]* non è caricato nella scheda.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

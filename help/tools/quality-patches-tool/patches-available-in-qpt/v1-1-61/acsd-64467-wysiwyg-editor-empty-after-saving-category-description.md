---
title: 'ACSD-64467: l’editor WYSIWYG è vuoto dopo il salvataggio della descrizione della categoria a livello di visualizzazione negozio'
description: Applica la patch ACSD-64467 per risolvere il problema di Adobe Commerce, in cui l’editor WYSIWYG appare vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione archivio.
feature: Page Content
role: Admin, Developer
source-git-commit: 4e883b3ec9b790f52dd56206539475e72bdf361d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: l’editor WYSIWYG è vuoto dopo il salvataggio della descrizione della categoria a livello di visualizzazione negozio

The ACSD-64467 patch fixes the issue where the WYSIWYG editor appears empty after saving a category description at the store view level. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. The patch ID is ACSD-64467. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

The WYSIWYG editor appears empty after saving a category description at the store view level.

<u>Passaggi da riprodurre</u>:

1. Edit a category in the Commerce Admin at the store view level.
1. Deselect the *[!UICONTROL Use default value]* checkbox next to the category description.
1. Enter a description in the WYSIWYG editor.
1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

The description is saved and properly displayed.

<u>Risultati effettivi</u>:

La descrizione è vuota dopo il ricaricamento della pagina.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

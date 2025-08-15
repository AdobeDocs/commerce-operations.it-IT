---
title: 'ACSD-64467: l’editor WYSIWYG è vuoto dopo il salvataggio della descrizione della categoria a livello di visualizzazione negozio'
description: Applica la patch ACSD-64467 per risolvere il problema di Adobe Commerce, in cui l’editor WYSIWYG appare vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione archivio.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: l’editor WYSIWYG è vuoto dopo il salvataggio della descrizione della categoria a livello di visualizzazione negozio

La patch ACSD-64467 risolve il problema se l’editor WYSIWYG appare vuoto dopo il salvataggio di una descrizione della categoria a livello di visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64467. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’editor WYSIWYG appare vuoto dopo aver salvato una descrizione della categoria a livello di visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Modifica una categoria in Commerce Admin a livello di visualizzazione store.
1. Deselezionare la casella di controllo *[!UICONTROL Use default value]* accanto alla descrizione della categoria.
1. Immetti una descrizione nell’editor di WYSIWYG.
1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

La descrizione viene salvata e visualizzata correttamente.

<u>Risultati effettivi</u>:

La descrizione è vuota dopo il ricaricamento della pagina.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

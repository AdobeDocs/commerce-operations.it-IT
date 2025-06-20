---
title: 'ACP2E-3689: molteplici problemi con la visualizzazione dell’albero delle categorie a livelli più profondi e che riflettono le relazioni ancoraggio/non ancoraggio'
description: Applicate la patch ACP2E-3689 per risolvere il problema Adobe Commerce relativo alla visualizzazione della struttura delle categorie su una profondità superiore a quattro annidamenti e relazioni di ancoraggio/non di ancoraggio riflettenti.
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689: molteplici problemi con la visualizzazione dell’albero delle categorie a livelli più profondi e che riflettono le relazioni ancoraggio/non ancoraggio

>[!NOTE]
>
>Questa patch sostituisce [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) per le versioni 2.4.7 e successive.

La patch ACP2E-3689 risolve diversi problemi con la visualizzazione dell&#39;albero delle categorie su più di quattro annidamenti di profondità e relazioni di ancoraggio/non di ancoraggio riflettenti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACP2E-3689. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;albero delle categorie su livelli più profondi (4+) non viene visualizzato correttamente e riflette le relazioni di ancoraggio/non di ancoraggio.

<u>Passaggi da riprodurre</u>:

1. Impostare una struttura di categorie con categorie nidificate di più di 4 livelli.
1. Espandi la struttura delle categorie in Amministratore che viene visualizzata in posizioni diverse:
   1. Impostare un [!UICONTROL Related Products Rule] e una condizione in base alle categorie.
   1. Crea un widget e in [!UICONTROL Layout Updates] seleziona [!UICONTROL Anchor categories].

<u>Risultati previsti</u>:

Tutti i livelli dell&#39;albero delle categorie vengono visualizzati correttamente.

<u>Risultati effettivi</u>:

Sono disponibili solo i primi livelli (&lt;4) dell&#39;albero delle categorie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

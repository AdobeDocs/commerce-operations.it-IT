---
title: 'ACSD-63974: corregge il tempo di caricamento lento di [!UICONTROL Requisition List] con la paginazione'
description: Applicare la patch ACSD-63974 per risolvere il problema relativo al caricamento della pagina [!UICONTROL Requisition List] quando sono presenti troppi elementi.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974: corregge il tempo di caricamento lento di [!UICONTROL Requisition List] con la paginazione

La patch ACSD-63974 risolve il problema relativo al tempo di caricamento della pagina **[!UICONTROL Requisition List]** quando sono presenti troppi elementi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-63974. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il caricamento della pagina **[!UICONTROL Requisition List]** richiede molto tempo se gli elementi sono numerosi (oltre 2000). Ciò è dovuto all’assenza di impaginazione, che causa il caricamento di tutti gli elementi contemporaneamente.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Imposta **[!UICONTROL Enable Requisition List]** su *Sì*.
1. Generare più di 2.000 prodotti modificando il nodo `simple_products` in `setup/performance-toolkit/profiles/ce/small.xml`.
1. Esegui il comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Crea un cliente e accedi.
1. Aggiungi tutti i prodotti a **[!UICONTROL Requisition List]**.
1. Visualizza **[!UICONTROL Requisition List]** nella vetrina.


<u>Risultati previsti</u>:

La pagina deve essere caricata entro un tempo ragionevole.


<u>Risultati effettivi</u>:

Il tempo di caricamento della pagina aumenta con il numero di elementi, perché tutti gli elementi vengono caricati contemporaneamente a causa dell’assenza di impaginazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

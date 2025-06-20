---
title: 'ACSD-63323: risolve la funzionalità [!UICONTROL Select All] e migliora l''impaginazione e il conteggio dei record nel popup della categoria di prodotto'
description: Applicare la patch ACSD-63323 per risolvere il problema di Adobe Commerce, in cui l'opzione [!UICONTROL Select All] non funziona quando si aggiungono prodotti a una categoria. Inoltre, assicura che la paginazione e l’etichetta del conteggio dei record funzionino correttamente quando si aggiungono prodotti a una categoria tramite la griglia a comparsa.
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323: risolve la funzionalità [!UICONTROL Select All] e migliora l&#39;impaginazione e il conteggio dei record nel popup della categoria di prodotto

La patch ACSD-63323 risolve il problema relativo al mancato funzionamento dell&#39;opzione **[!UICONTROL Select All]** durante l&#39;aggiunta di prodotti a una categoria. Inoltre, assicura che la paginazione e l’etichetta del conteggio dei record funzionino correttamente quando si aggiungono prodotti a una categoria tramite la griglia a comparsa. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. L’ID della patch è ACSD-63323. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che impediva il funzionamento dell&#39;opzione **[!UICONTROL Select All]** in Amministratore > **[!UICONTROL Categories]** > scegli una categoria > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**. Consente inoltre il corretto funzionamento dell’impaginazione e dell’etichetta del conteggio dei record quando si aggiungono prodotti a una categoria tramite la griglia a comparsa.


<u>Passaggi da riprodurre</u>:

1. Genera *1200* prodotti utilizzando il comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Apri **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e visualizza il numero di prodotti: *1200* record trovati.
1. Apri una categoria predefinita > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Fare clic su **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Modifica il numero di prodotti nella pagina impostando il valore = *5*.


**Risultati previsti**:

*Il messaggio deve essere: trovati 1200 record (selezionati 1200)*

**Risultati effettivi**:

* La paginazione non funziona.
* Viene visualizzato il messaggio errato: *5* record trovati (*20* selezionati)

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

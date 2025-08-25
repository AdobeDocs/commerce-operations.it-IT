---
title: 'ACSD-66506: si verifica un errore di back-end dopo l’eliminazione e la riassegnazione dei prodotti del catalogo condiviso'
description: Applica la patch ACSD-66506 per risolvere il problema di Adobe Commerce che causa l’errore nel backend *Il prodotto richiesto non esiste. Verifica il prodotto e riprova* dopo aver eliminato i prodotti precedentemente assegnati e averne assegnati di nuovi a un catalogo condiviso.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: si verifica un errore di back-end dopo l’eliminazione e la riassegnazione dei prodotti del catalogo condiviso

La patch ACSD-66506 risolve il problema che causa l&#39;errore del backend *Il prodotto richiesto non esiste. Verifica il prodotto e riprova* dopo aver eliminato i prodotti precedentemente assegnati e averne assegnati di nuovi a un catalogo condiviso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66506. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver eliminato i prodotti precedentemente assegnati e averne assegnati di nuovi a **[!UICONTROL Shared Catalog]**, il backend restituisce il seguente errore: *Il prodotto richiesto non esiste. Verifica il prodotto e riprova*

<u>Passaggi da riprodurre</u>:

1. Creare alcuni prodotti utilizzando il toolkit di prestazioni: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Vai alla configurazione **[!UICONTROL [!DNL B2B] Features]** e imposta **[!UICONTROL Enable Company]** e **[!UICONTROL Enable Shared Catalog]** su `Yes`.
1. Crea un nuovo catalogo condiviso.
1. Assegna tutti i prodotti generati al nuovo catalogo condiviso creato.
1. Utilizzare **[!UICONTROL Product Import]** per eliminare un prodotto assegnato al catalogo condiviso.
   1. Esporta un prodotto filtrato per SKU.
   1. Selezionare **[!UICONTROL Import Behavior: Delete]**, quindi importare lo stesso file.
1. Apri **[!UICONTROL Shared Catalog]** e configura i prezzi e la struttura.
   1. Selezionare **[!UICONTROL Set Pricing and Structure]**.
   1. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Generate Catalog]**.
   1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Non si verifica alcun errore e i prodotti rimangono nel catalogo condiviso anche in caso di errore.

<u>Risultati effettivi</u>:

Si è verificato un errore: *Il prodotto richiesto non esiste. Verificare il prodotto e riprovare*. Tutti i prodotti verranno rimossi dal catalogo condiviso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

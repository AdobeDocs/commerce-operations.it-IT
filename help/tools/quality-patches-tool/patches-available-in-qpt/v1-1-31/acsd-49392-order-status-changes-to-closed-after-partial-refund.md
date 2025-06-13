---
title: 'ACSD-49392: lo stato dell''ordine viene modificato in chiuso dopo il rimborso parziale'
description: Applica la patch ACSD-49392 per risolvere il problema Adobe Commerce, in cui lo stato dell’ordine diventa chiuso dopo un rimborso parziale per un prodotto in bundle.
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392: lo stato dell&#39;ordine viene modificato in chiuso dopo il rimborso parziale

>[!NOTE]
>
>La patch ACSD-49392 è stata sostituita con la patch [ACSD-57003](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) per le versioni da 2.4.6-p7 a 2.4.6-p10.

La patch ACSD-49392 risolve il problema relativo alla chiusura dello stato dell&#39;ordine dopo un rimborso parziale per un prodotto in bundle. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.31. L’ID della patch è ACSD-49392. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4 e 2.4.1 - 2.4.6-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato dell&#39;ordine diventa chiuso dopo un rimborso parziale per un prodotto nel pacchetto.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Adobe Commerce e crea qualsiasi prodotto in bundle o utilizza il prodotto in bundle esistente.
1. Effettua un ordine con questo prodotto in bundle con una quantità maggiore di 1.
1. Accedere all&#39;amministratore, aprire l&#39;ordine creato nel passaggio 2 da **[!UICONTROL Sales]** > **[!UICONTROL Order]** e creare una fattura. Osserva lo stato dell’ordine. Sarà in elaborazione.
1. Crea una nota di credito parziale (non rimborsare per tutti i prodotti nel bundle).
1. Controlla lo stato dell’ordine.

<u>Risultati previsti</u>

Dopo aver creato una nota di credito parziale per il prodotto nel pacchetto, lo stato dell&#39;ordine è in elaborazione.

<u>Risultati effettivi</u>

Dopo aver creato una nota di credito parziale per il prodotto nel pacchetto, lo stato dell&#39;ordine è completo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

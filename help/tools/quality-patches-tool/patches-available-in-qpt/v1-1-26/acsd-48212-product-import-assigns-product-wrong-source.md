---
title: 'ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata'
description: Applica la patch ACSD-48212 per risolvere il problema di Adobe Commerce, a causa del quale l’importazione del prodotto assegna il prodotto alla sorgente errata.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata

La patch ACSD-48212 risolve il problema che causa l’importazione del prodotto, il quale viene assegnato all’origine errata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. L’ID della patch è ACSD-48212. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione del prodotto assegna il prodotto all’origine errata.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;origine magazzino secondaria.
1. Crea un prodotto solo con l&#39;origine di magazzino predefinita.
1. Esporta il prodotto.
1. Esegui `bin/magento cron:run`.
1. Apri **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Seleziona il prodotto dalla griglia.
1. Annullare l&#39;assegnazione del titolo utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Assegnare l&#39;origine secondaria utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Eliminare il prodotto utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Importa il prodotto utilizzando il file CSV esportato in precedenza.
1. Controllare l&#39;assegnazione di origine.

<u>Risultati previsti</u>:

Il prodotto viene assegnato solo all&#39;origine predefinita.

<u>Risultati effettivi</u>:

Il prodotto viene assegnato sia all&#39;origine predefinita che a quella secondaria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

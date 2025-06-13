---
title: 'ACSD-48293: prodotti compositi esauriti quando sono esauriti i prodotti per bambini riassortiti'
description: Applicare la patch ACSD-48293 per risolvere il problema Adobe Commerce relativo all'esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: prodotti compositi esauriti quando sono esauriti i prodotti per bambini riassortiti

La patch ACSD-48293 risolve il problema relativo all&#39;esaurimento delle scorte dei prodotti compositi quando i prodotti secondari esauriti vengono restituiti alle scorte. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-48293. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti compositi esauriscono quando i prodotti secondari esauriti vengono restituiti alle scorte.

<u>Passaggi da riprodurre</u>:

1. Crea una visualizzazione secondaria per sito Web, store e store.
1. Crea due origini e due scorte e assegnale a ciascun sito Web.
1. Abilita l&#39;opzione Mostra prodotti esauriti in **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Creare un prodotto configurabile con un prodotto associato utilizzando l&#39;origine di magazzino del sito Web principale (qtà impostata = 1).
1. Ordinare il prodotto configurabile.
1. Esegui il cron.
1. Apri il prodotto configurabile dalla vetrina e conferma che non è disponibile.
1. Aprire il prodotto configurabile da [!UICONTROL Admin] e impostare **[!UICONTROL Manage Stock Option]** su *[!UICONTROL No]*.
1. Esegui il cron.
1. Spedire l&#39;ordine e aggiungere la quantità al prodotto semplice rendendolo disponibile.
1. Esegui il cron.
1. Verifica la disponibilità del prodotto nella vetrina.

<u>Risultati previsti</u>:

Il prodotto configurabile è disponibile.

<u>Risultati effettivi</u>:

Il prodotto configurabile è esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

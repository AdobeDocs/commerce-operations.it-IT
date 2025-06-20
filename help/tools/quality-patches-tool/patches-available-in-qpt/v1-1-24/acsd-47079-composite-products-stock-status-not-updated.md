---
title: 'ACSD-47079: lo stato delle scorte dei prodotti compositi non viene aggiornato quando cambia lo stato delle scorte dei sottoprodotti'
description: Applicare la patch ACSD-47079 per risolvere il problema Adobe Commerce per cui lo stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato delle scorte dei sottoprodotti cambia tramite REST API POST /rest/V1/inventory/source-items.
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079: lo stato delle scorte dei prodotti compositi non viene aggiornato quando cambia lo stato delle scorte dei sottoprodotti

La patch ACSD-47079 risolve il problema che impedisce l&#39;aggiornamento dello stato delle scorte dei prodotti compositi (bundle, raggruppati e configurabili) quando lo stato delle scorte dei sottoprodotti viene modificato tramite REST API POST `/rest/V1/inventory/source-items`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-47079. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato del magazzino dei prodotti compositi (bundle, raggruppati e configurabili) non viene aggiornato quando lo stato del magazzino del sottoprodotto viene modificato tramite REST API POST `/rest/V1/inventory/source-items`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile, in bundle e raggruppato con un semplice prodotto secondario per ciascuno di essi.
1. Impostare ogni stato di prodotto figlio semplice su **[!UICONTROL Out of Stock]** utilizzando la chiamata API `source-items`.
1. Ora controlla lo stato delle scorte del prodotto principale.

<u>Risultati previsti</u>:

Lo stato del prodotto padre è [!UICONTROL Out of Stock].

<u>Risultati effettivi</u>:

Lo stato del prodotto padre è [!UICONTROL In Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

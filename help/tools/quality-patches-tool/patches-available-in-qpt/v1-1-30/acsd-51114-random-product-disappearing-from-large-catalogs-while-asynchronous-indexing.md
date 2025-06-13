---
title: 'ACSD-51114: i prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona'
description: Applica la patch ACSD-51114 per risolvere il problema di Adobe Commerce. I prodotti Random scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51114: i prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona

>[!NOTE]
>
>Questa patch è obsoleta.

La patch ACSD-51114 risolve il problema Prodotti casuali scomparsi da cataloghi di grandi dimensioni quando l’indicizzazione asincrona è abilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. L’ID della patch è ACSD-51114. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]:Cerca patch].Utilizzare l&#39;ID della patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.

<u>Passaggi da riprodurre</u>:

1. Crea un set di 10 prodotti.
1. Imposta tutti gli indicizzatori sulla modalità **[!UICONTROL Update on Save]**.
1. Crea una categoria e assegna a essa tutti i prodotti.
1. Disattiva tutti i prodotti.
1. Apri la categoria e verifica che non vi siano prodotti.
1. Imposta tutti gli indicizzatori sulla modalità **[!UICONTROL Update on Schedule]**.
1. Impostare `DEFAULT_BATCH_SIZE` su 2 in `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Abilitare i prodotti nell&#39;ordine seguente: 1°, 9°, 2°, 5°, 10°, 3°.
1. Esegui il comando cron.
1. Apri nuovamente la categoria.

<u>Risultati previsti</u>:

Vengono visualizzati tutti i prodotti abilitati.

<u>Risultati effettivi</u>:

Tutti i prodotti abilitati non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

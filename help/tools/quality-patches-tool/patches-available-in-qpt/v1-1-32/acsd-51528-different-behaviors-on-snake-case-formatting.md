---
title: 'ACSD-51528: diversi comportamenti nella formattazione di snake_case'
description: Applica la patch ACSD-51528 per risolvere il problema Adobe Commerce, in presenza di comportamenti diversi nella formattazione di snake_case.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: diversi comportamenti nella formattazione di snake_case

La patch ACSD-51528 corregge diversi comportamenti nella formattazione di snake_case. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51528. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I diversi comportamenti sulla formattazione snake_case.

<u>Passaggi da riprodurre</u>:

1. Verificare la funzione `\Magento\Framework\Api\DataObjectHelper::populateWithArray` con diversi nomi di proprietà.
1. Le proprietà con nomi come *NewPName* devono essere trasformate in *new_p_name*, ma verranno trasformate in *new_pname*.
1. Inoltre, quando si utilizza la funzione *getNewPName* nell&#39;oggetto, verrà restituito *null* perché il *modello astratto* trasformerà correttamente la chiamata in *new_p_name* rendendo entrambe le funzioni incompatibili tra loro.

<u>Risultati previsti</u>

La funzione **[!UICONTROL populateWithArray]** deve trasformare correttamente le proprietà dell&#39;oggetto in snake_case, rendendolo compatibile con **[!DNL AbstractModel's]** `Getters` e `Setters`.

<u>Risultati effettivi</u>

Quando si utilizza la funzione **[!UICONTROL populateWithArray]**, qualsiasi proprietà dell&#39;oggetto che contenga due o più lettere maiuscole in una riga del nome causerà l&#39;errata trasformazione di snake_case nell&#39;array di dati finale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

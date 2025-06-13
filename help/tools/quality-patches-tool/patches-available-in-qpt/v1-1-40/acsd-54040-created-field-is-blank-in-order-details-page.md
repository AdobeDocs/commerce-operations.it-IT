---
title: 'ACSD-54040: il campo [!UICONTROL Created] è vuoto nei dettagli dell’ordine quando i moduli B2B sono abilitati'
description: Applica la patch ACSD-54040 per risolvere il problema di Adobe Commerce, in cui il campo [!UICONTROL Created] è vuoto nella pagina dei dettagli dell’ordine quando i moduli B2B sono abilitati.
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040: il campo *[!UICONTROL Created]* è vuoto nei dettagli dell’ordine quando i moduli B2B sono abilitati.

La patch ACSD-54040 risolve il problema se il campo *[!UICONTROL Created]* rimane vuoto nella pagina dei dettagli dell’ordine quando i moduli B2B sono abilitati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. L’ID della patch è ACSD-54040. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando i moduli B2B sono abilitati, il campo *[!UICONTROL Created]* rimane vuoto nella pagina dei dettagli dell&#39;ordine.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con il modulo B2B.
1. Crea un nuovo cliente e effettua un ordine.
1. Vai ai dettagli dell&#39;ordine sul front-end e controlla il campo *[!UICONTROL Created]*.

<u>Risultati previsti</u>:

Nel campo *[!UICONTROL Created]* viene visualizzata la data di creazione dell&#39;ordine.

<u>Risultati effettivi</u>:

Il campo *[!UICONTROL Created]* è vuoto

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

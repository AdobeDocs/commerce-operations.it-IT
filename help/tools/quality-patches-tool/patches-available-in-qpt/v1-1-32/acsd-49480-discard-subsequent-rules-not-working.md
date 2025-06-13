---
title: 'ACSD-49480: le regole successive non funzionano'
description: Applicare la patch ACSD-49480 per risolvere il problema di Adobe Commerce in cui [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto.
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto

La patch ACSD-49480 risolve il problema se [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-49480. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto.

<u>Passaggi da riprodurre</u>:

1. Crea un **[!UICONTROL Cart Price Rule]** con un codice coupon (denominalo *TEST*) che offre uno sconto di $ 10 all&#39;*ID prodotto 1* nella scheda **[!UICONTROL Actions]** con [!UICONTROL Discard Subsequent Rules] impostato su *[!UICONTROL Yes]* e [!UICONTROL Priority] impostato su *1*.
1. Crea un altro **[!UICONTROL Cart Price Rule]** senza un codice coupon che offre uno sconto di $5 a *ID prodotto 2* nella scheda **[!UICONTROL Actions]** con [!UICONTROL Priority] impostato su *2*. In questo caso, si tratta di una vendita globale per *ID prodotto 2*.
1. Vai al sito front-end e aggiungi *ID prodotto 1* e *ID prodotto 2* nel carrello.
1. Applica il codice coupon *TEST*.

<u>Risultati previsti</u>

* *Sconto 1* applicato a *ID prodotto 1*.
* *Sconto 2* applicato a *ID prodotto 2*.

<u>Risultati effettivi</u>

* Solo *Sconto 1* è applicato a *ID prodotto 1*.
* *Sconto 2* non applicato a *ID prodotto 2*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

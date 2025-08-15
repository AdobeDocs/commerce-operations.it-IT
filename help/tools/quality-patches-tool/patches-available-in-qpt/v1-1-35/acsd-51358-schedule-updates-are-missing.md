---
title: 'ACSD-51358: mancano aggiornamenti della pianificazione'
description: Applica la patch ACSD-51358 per risolvere il problema di Adobe Commerce, in cui le modifiche all’aggiornamento pianificato senza data di fine determinano la rimozione di altri aggiornamenti pianificati sulla stessa entità.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: mancano aggiornamenti della pianificazione

La patch ACSD-51358 risolve il problema che causa la rimozione di altri aggiornamenti pianificati sulla stessa entità a causa delle modifiche apportate all’aggiornamento pianificato senza data di fine. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35. L’ID della patch è ACSD-51358. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche apportate all’aggiornamento programmato senza data di fine determinano la rimozione di altri aggiornamenti programmati sulla stessa entità.

<u>Passaggi da riprodurre</u>:

1. Crea un **[!UICONTROL scheduled update]** senza la data di fine (*aggiornamento 1*).
1. Crea nuovo **[!UICONTROL scheduled update]** con la stessa data di inizio del primo aggiornamento, ma aggiungi il giorno successivo e la data di fine (*aggiornamento 2*).
1. Modifica **[!UICONTROL scheduled update]** creata al passaggio 1 (*aggiorna 1*) e le modifiche di salvataggio.

<u>Risultati previsti</u>

(*aggiornamento 2*) deve rimanere nell&#39;elenco **[!UICONTROL schedule update]** quando (*aggiornamento 1*) viene modificato.

<u>Risultati effettivi</u>

(*aggiornamento 2*) è stato rimosso dall&#39;elenco **[!UICONTROL schedule update]** quando (*aggiornamento 1*) è stato modificato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].

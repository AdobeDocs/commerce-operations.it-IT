---
title: 'ACSD-51358: mancano aggiornamenti della pianificazione'
description: Applica la patch ACSD-51358 per risolvere il problema di Adobe Commerce, in cui le modifiche all’aggiornamento pianificato senza data di fine determinano la rimozione di altri aggiornamenti pianificati sulla stessa entità.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---
# ACSD-51358: mancano aggiornamenti della pianificazione

La patch ACSD-51358 risolve il problema che causa la rimozione di altri aggiornamenti pianificati sulla stessa entità a causa delle modifiche apportate all’aggiornamento pianificato senza data di fine. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.35. L’ID della patch è ACSD-51358. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

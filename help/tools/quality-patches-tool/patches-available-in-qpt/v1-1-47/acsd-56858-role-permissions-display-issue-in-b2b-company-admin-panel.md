---
title: 'ACSD-56858: discrepanza nelle autorizzazioni dei ruoli nell’amministratore dell’azienda B2B'
description: Applica la patch ACSD-56858 per risolvere il problema di Adobe Commerce, in cui le autorizzazioni dei ruoli non vengono visualizzate correttamente per un amministratore aziendale con restrizioni nell’ambiente B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '462'
ht-degree: 0%
---
# ACSD-56858: discrepanza nelle autorizzazioni dei ruoli nell’amministratore dell’azienda B2B

La patch ACSD-56858 risolve il problema relativo alla visualizzazione errata delle autorizzazioni dei ruoli per un amministratore aziendale con restrizioni nell’ambiente B2B. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.47. L’ID della patch è ACSD-56858. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le autorizzazioni per il ruolo di amministratore di un’azienda con restrizioni nell’ambiente B2B non vengono visualizzate in modo corretto.

<u>Passaggi da riprodurre</u>:

1. Per prima cosa, imposta una società, aggiungendo un amministratore della società e gli utenti della società.
1. Accedi allo storefront come amministratore aziendale e crea vari ruoli per utenti diversi.
1. Assegna questi ruoli in base alle esigenze, ad esempio limitando l’accesso ad alcune attività e consentendo l’accesso completo ad altre.
1. Assegna questi ruoli con accesso completo a un utente diverso dall’amministratore della società.
1. Accedi a un utente amministratore non aziendale, ad esempio company_manager.
1. Passare a **[!UICONTROL Roles and permission]** e modificare il ruolo.
1. Tieni presente che le autorizzazioni visualizzate non corrispondono alle autorizzazioni impostate nel database dell’azienda per tale ID ruolo.

<u>Risultati previsti</u>:

I ruoli e le autorizzazioni vengono visualizzati correttamente per l’utente amministratore non aziendale.

<u>Risultati effettivi</u>:

I ruoli non vengono visualizzati correttamente per l’utente amministratore non aziendale in base ai record del database nella tabella delle autorizzazioni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud

## Lettura correlata

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-47027: aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] con query lenta'
description: Applicare la patch ACSD-47027 per risolvere il problema Adobe Commerce in caso di aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] lento della query.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
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
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-47027: aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] con query lenta

La patch ACSD-47027 risolve il problema che causa il mancato funzionamento previsto dell&#39;aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] della query lenta. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-47027. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento B2B [!UICONTROL CompanyRole] [!DNL GraphQL] della query lenta non funziona come previsto.

<u>Prerequisiti</u>:

Installa il modulo B2B.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** e imposta **[!UICONTROL Enable Company]** su _Yes_.
1. Vai al front-end e crea un’azienda.
1. Dopo aver effettuato l&#39;accesso come utente aziendale, passare a **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** e aggiungere una nuova mansione.
1. Abilita [!UICONTROL dev] registro query tramite `bin/magento dev:que:enab`.
1. Ora invia la seguente richiesta [!DNL GraphQL] (ID è l&#39;ID ruolo codificato [!UICONTROL base64]):

   ```graphql
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id
   
         name
   
         permissions {
         id
   
         text
   
         children {
            id
   
            text
   
            children {
               id
   
               text
             }
           }
         }
       }
     }
   }
   ```

1. Controlla il registro delle query.
1. Puoi vedere che la query precedente viene eseguita. Questa query viene eseguita in `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Risultati previsti</u>:

È necessario ottimizzare `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` per evitare di caricare tutti i dati disponibili nella tabella del database **[!UICONTROL company_permissions]**.

<u>Risultati effettivi</u>:

Adobe Commerce esegue una query senza alcun filtro. In presenza di un numero elevato di record, la preparazione della raccolta dei dati da parte di Adobe Commerce richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

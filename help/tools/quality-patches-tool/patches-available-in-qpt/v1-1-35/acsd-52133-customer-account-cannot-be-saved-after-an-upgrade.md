---
title: 'ACSD-52133: impossibile salvare l’account del cliente dopo un aggiornamento'
description: Applica la patch ACSD-52133 per risolvere il problema di Adobe Commerce, a causa del quale non è possibile salvare un account cliente dopo un aggiornamento.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%
---
# ACSD-52133: impossibile salvare l’account del cliente dopo un aggiornamento

>[!NOTE]
>
>Questa patch è stata rimossa a causa di un conflitto con la patch di sicurezza [APSB25-08](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-27149).

La patch ACSD-52133 risolve il problema che impediva il salvataggio di un account cliente dopo un aggiornamento. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52133. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;account cliente non può essere salvato dopo un aggiornamento.

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce versione 2.4.4.
1. Crea un cliente.
1. Aggiornare Adobe Commerce alla versione 2.4.6 dalla versione precedente della versione 2.4.4, in cui era già stato creato un cliente.
1. Impostare la chiave di crittografia come indicato di seguito in `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Impostare i valori seguenti nel database per qualsiasi cliente nella tabella `customer_entity`:

   ```text
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifica il cliente per il quale sono stati aggiornati i valori precedenti.
1. Fai clic su **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**

<u>Risultati previsti</u>:

Il cliente viene salvato senza errori.

<u>Risultati effettivi</u>:

* Record cliente non salvato.
* L&#39;amministratore visualizza il seguente messaggio di errore: *Si è verificato un errore durante il salvataggio del cliente.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud

## Lettura correlata

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

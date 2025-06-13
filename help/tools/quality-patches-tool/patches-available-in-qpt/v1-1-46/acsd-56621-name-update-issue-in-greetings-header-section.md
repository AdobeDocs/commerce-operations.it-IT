---
title: 'ACSD-56621: i nomi aggiornati non vengono visualizzati nell’intestazione dei saluti per l’utente amministratore della società'
description: Applica la patch ACSD-56621 per risolvere il problema di Adobe Commerce, per cui il nome e il cognome aggiornati dell’utente amministratore della società non vengono riportati nella sezione dell’intestazione dei saluti.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621: i nomi aggiornati non vengono visualizzati nell’intestazione dei saluti per l’utente amministratore della società

La patch ACSD-56621 risolve il problema per cui il nome e il cognome aggiornati dell’utente amministratore dell’azienda non compaiono nella sezione dell’intestazione dei saluti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46. L’ID della patch è ACSD-56621. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I nomi aggiornati non vengono visualizzati nell’intestazione dei saluti per gli utenti amministratori della società.

<u>Passaggi da riprodurre</u>:

1. Passare al pannello **[!UICONTROL Admin]**.
1. Vai a **[!UICONTROL Stores]** e seleziona **[!UICONTROL Configuration]**.
1. Nella sezione **[!UICONTROL General]**, seleziona **[!UICONTROL B2B]** per abilitare la funzionalità aziendale B2B.
1. Passare a **[!UICONTROL Storefront]** e registrare una nuova società.
1. Accedi come utente amministratore della società.
1. Vai a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** e modifica i campi nome e cognome come richiesto.

<u>Risultati previsti</u>:

Il nome e il cognome dell’utente nella sezione dell’intestazione dei saluti vengono modificati immediatamente.

<u>Risultati effettivi</u>:

Il nome e il cognome dell’utente vengono modificati solo quando l’utente si disconnette e accede di nuovo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

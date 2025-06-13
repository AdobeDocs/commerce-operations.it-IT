---
title: 'ACSD-48773: modello e-mail punti premio ottenuto da un archivio errato'
description: Applica la patch ACSD-48773 per risolvere il problema di Adobe Commerce per cui il modello e-mail dei punti premio viene prelevato dallo store errato.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773: modello e-mail punti premio ottenuto da un archivio errato

La patch ACSD-48773 risolve il problema se il modello e-mail dei punti premio viene prelevato dall’archivio errato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. L’ID della patch è ACSD-48773. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione del prezzo del prodotto non funziona se il prodotto bundle non è assegnato ad alcun sito Web.

<u>Passaggi da riprodurre</u>:

1. Crea 2 siti web, 2 store e 2 visualizzazioni store.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** e abilita **[!UICONTROL Reviews]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Passa a **[!DNL default website scope]** e imposta l&#39;indirizzo **[!UICONTROL Customer Support Sender Email]** (ad esempio: *support_base@example.com*).
Passa a **[!DNL second website scope]** e imposta l&#39;indirizzo **[!UICONTROL Customer Support Sender Email]** su un altro valore (ad esempio: *support_second@example.com*).
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** e imposta **[!UICONTROL Share Customer Accounts]** = *Per sito Web*.
1. In **[!UICONTROL Reward Points]**, impostare quanto segue:
   **[!UICONTROL Enable Reward Points Functionality]** = *Sì*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Sì*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** e **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** e impostato **[!UICONTROL Email Sender]** = *Assistenza clienti*
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e imposta i tassi di cambio per il secondo sito Web sia per **[!UICONTROL Points/Currency]** che per **[!UICONTROL Currency/Points]**.
1. Crea un account cliente sul secondo sito Web.
1. Accedi come cliente al secondo sito Web.
1. Assicurarsi di abilitare **[!UICONTROL Subscribe]** per **[!UICONTROL Balance Updates]**.
1. Invia una recensione prodotto.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Modificare lo stato della nuova revisione in ***[!UICONTROL Approved]*** e **[!UICONTROL Save]**.
1. Attendi che l’e-mail arrivi.

<u>Risultati previsti</u>:

L’e-mail di aggiornamento dei punti premio avrebbe dovuto essere inviata dal mittente dell’e-mail configurato nel secondo ambito del sito web.

<u>Risultati effettivi</u>:

L’e-mail di aggiornamento dei punti premio è stata inviata dal mittente dell’e-mail configurato nell’ambito predefinito del sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

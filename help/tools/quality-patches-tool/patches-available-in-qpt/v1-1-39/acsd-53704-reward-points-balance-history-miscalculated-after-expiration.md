---
title: 'ACSD-53704: storico saldo punti premio non calcolato correttamente dopo la scadenza'
description: Applica la patch ACSD-53704 per risolvere il problema Adobe Commerce per cui la cronologia dei saldi dei punti premio viene calcolata in modo errato dopo la data di scadenza dei punti premio.
feature: Rewards
role: Admin, Developer
exl-id: 8cd297cc-9e9d-4615-b817-283065a79c2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-53704: storico saldo punti premio non calcolato correttamente dopo la scadenza

La patch ACSD-53704 risolve il problema relativo al calcolo errato della cronologia dei saldi dei punti premio dopo la data di scadenza dei punti premio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39. L’ID della patch è ACSD-53704. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La cronologia dei saldi dei punti premio viene calcolata in modo errato dopo la data di scadenza dei punti premio.

<u>Passaggi da riprodurre</u>:

1. Crea un cliente nella vetrina.
1. Aggiungere punti premio per il cliente con date di scadenza diverse.
1. Controllare la tabella `magento_reward_history` e impostare la data di scadenza per l&#39;ultimo record di punti premio su una data passata:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Controllare la griglia della cronologia premi in **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** e **[!UICONTROL Reward Points Balance]**.

<u>Risultati previsti</u>:

Il saldo dei punti premio mostra solo i punti non scaduti.

<u>Risultati effettivi</u>:

Il saldo dei punti premio riflette l&#39;importo che include i punti scaduti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud

## Lettura correlata

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

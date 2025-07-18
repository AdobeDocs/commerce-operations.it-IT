---
title: 'ACSD-47910: ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità'
description: Applicare la patch ACSD-47910 per risolvere il problema Adobe Commerce in presenza di ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità

La patch ACSD-47910 risolve il problema relativo a ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-47910. La versione in cui verrà risolto il problema non è ancora disponibile.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Asynchronous indexing]** in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Effettuare due ordini.
1. Esegui la cron per sincronizzare questi ordini con la griglia.
1. Aprire uno degli ordini e prepararlo per la fatturazione. NON INVIARE ANCORA LA FATTURA.
1. Crea un nuovo ordine pronto per essere inserito sul front-end. NON FARE ANCORA CLIC SUL PULSANTE INSERISCI ORDINE.
1. Aggiungi `sleep(30)` in `foreach` alle `NotSyncedDataProvider::L43`.
1. Esegui `bin/magento cron:run`.
1. Ora inserisci il nuovo ordine.
1. Fattura l&#39;ordine precedente.
1. Esegui di nuovo il cron in attesa della sincronizzazione del nuovo ordine.
1. Vai alla griglia dell’ordine nell’amministratore.

<u>Risultati previsti</u>:

Il nuovo ordine dovrebbe essere visualizzato nella griglia dell&#39;ordine.

<u>Risultati effettivi</u>:

L&#39;aggiornamento dell&#39;ordine precedente è stato sincronizzato nella griglia (**[!UICONTROL status: Processing]**). Il nuovo ordine non viene mai visualizzato sulla griglia.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACP2E-3977: il campo [!UICONTROL Cap Reward Points Balance At] non può essere lasciato vuoto'
description: Applica la patch ACP2E-3977 per risolvere il problema Adobe Commerce per cui il campo **[!UICONTROL Cap Reward Points Balance At]** non poteva essere lasciato vuoto quando è stato impostato **[!UICONTROL Rewards Points Balance Redemption Threshold]** campo, causando un errore di convalida.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977: il campo **[!UICONTROL Cap Reward Points Balance At]** non può essere lasciato vuoto

La patch ACP2E-3977 risolve il problema per cui il campo **[!UICONTROL Cap Reward Points Balance At]** non può essere lasciato vuoto, anche quando dovrebbe essere consentito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACP2E-3977. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se si lascia **[!UICONTROL Cap Reward Points Balance At]** vuoto, viene generato un errore di convalida, anche se si dovrebbe disattivare il limite se lasciato vuoto.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. Imposta **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Lascia **[!UICONTROL Cap Reward Points Balance At]** vuoto.
1. Salva.

<u>Risultati previsti</u>:

È consentito un valore vuoto per **[!UICONTROL Cap Reward Points Balance At]** e disabilita la limitazione.

<u>Risultati effettivi</u>:

*Il saldo dei punti premio del tetto massimo non è valido. Il saldo deve essere un numero positivo o lasciato vuoto. Verifica e riprova.* errore visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

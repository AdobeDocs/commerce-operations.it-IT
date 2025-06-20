---
title: 'MDVA-42269: l''utente Admin non può accedere ad Admin a causa dell''errore "TypeError"'
description: La patch MDVA-42269 risolve il problema che impediva agli utenti Admin di accedere ad Admin a causa di TypeError. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11.  L'ID della patch è MDVA-42269.  L’ultimo aggiornamento della patch è disponibile in QPT 1.1.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Admin Workspace
role: Admin
exl-id: 42ad4bb5-950f-476d-bf55-931b38bcb937
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-42269: l&#39;utente Admin non può accedere ad Admin a causa dell&#39;errore &quot;TypeError&quot;

La patch MDVA-42269 risolve il problema che impediva agli utenti Admin di accedere ad Admin a causa di TypeError. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11.  L&#39;ID della patch è MDVA-42269.  L’ultimo aggiornamento della patch è disponibile in QPT 1.1.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1, 2.3.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti Admin non possono accedere all&#39;Admin a causa del seguente errore: *TypeError: strtotime() prevede che il parametro 1 sia una stringa, dato null.*

<u>Passaggi da riprodurre</u>:

Accedi all’amministratore di Commerce.

<u>Risultati previsti</u>:

L’utente amministratore può effettuare l’accesso con il nome utente e la password corretti.

<u>Risultati effettivi</u>:

L’utente amministratore non può effettuare l’accesso. È stato registrato il seguente errore: *TypeError: strtotime() prevede che il parametro 1 sia una stringa, dato null.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

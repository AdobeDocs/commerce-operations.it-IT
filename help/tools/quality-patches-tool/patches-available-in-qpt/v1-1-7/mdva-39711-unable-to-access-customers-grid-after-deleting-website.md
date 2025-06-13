---
title: 'MDVA-39711: impossibile accedere alla griglia clienti dopo l''eliminazione del sito Web'
description: La patch MDVA-39711 risolve il problema che impediva all'utente amministratore di accedere alla griglia dei clienti dopo l'eliminazione del sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. L'ID della patch è MDVA-39711. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: Configuration
role: Admin
exl-id: 7ddca2e7-86f5-4ffd-9c00-ea4c511ab663
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39711: impossibile accedere alla griglia clienti dopo l&#39;eliminazione del sito Web

La patch MDVA-39711 risolve il problema che impediva all&#39;utente amministratore di accedere alla griglia dei clienti dopo l&#39;eliminazione del sito Web. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. L&#39;ID della patch è MDVA-39711. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7-p2, 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non può accedere alla griglia dei clienti dopo l’eliminazione del sito web.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito Web, store e visualizzazione store.
1. Crea un nuovo cliente nell’amministratore e associalo al sito web creato.
1. Vai a **Archivi** > **Tutti gli archivi** ed elimina il sito Web creato.
1. Vai a **Clienti** > **Tutti i clienti**.

<u>Risultati previsti</u>:

* Nessun messaggio di errore.
* Tutti i clienti sono visibili nella griglia.

<u>Risultati effettivi</u>:

* L&#39;utente riceve un messaggio di errore: *Impossibile trovare il sito Web con ID 2 richiesto. Verifica il sito Web e riprova*
* Tutti i clienti non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

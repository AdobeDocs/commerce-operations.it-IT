---
title: 'MDVA-44703: i totali degli ordini nel rapporto Ordini non vengono calcolati correttamente'
description: La patch MDVA-44703 risolve il problema relativo al calcolo errato dei totali degli ordini nel rapporto Ordini per l'utente amministratore con restrizioni. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L'ID della patch è MDVA-44703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703: i totali degli ordini nel rapporto Ordini non vengono calcolati correttamente

La patch MDVA-44703 risolve il problema relativo al calcolo errato dei totali degli ordini nel rapporto Ordini per l&#39;utente amministratore con restrizioni. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L&#39;ID della patch è MDVA-44703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I totali degli ordini nel rapporto Ordini non vengono calcolati correttamente per l’utente amministratore con restrizioni.

<u>Passaggi da riprodurre</u>:

1. Crea un altro sito web con due store.
1. Crea un utente amministratore con restrizioni con accesso solo al nuovo sito web.
1. Accedi come utente amministratore con restrizioni.
1. Crea due ordini con totali diversi, uno per ogni nuovo negozio.
1. Creare le fatture per gli ordini.
1. Vai a **Report** > **Vendite** e apri **Report ordini**.
1. Aggiorna statistiche.
1. Vedi il rapporto per ogni negozio.

<u>Risultati previsti</u>:

I totali delle vendite corrispondono all&#39;importo dell&#39;ordine di ciascun negozio.

<u>Risultati effettivi</u>:

Il totale aggregato delle vendite per l&#39;intero sito Web viene visualizzato per ogni negozio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

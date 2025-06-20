---
title: 'MDVA-43091: impossibile ordinare il prodotto in bundle dall''amministratore'
description: La patch MDVA-43091 risolve il problema che impediva agli utenti di ordinare il prodotto in bundle dall'amministratore Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-43091. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: d2812f97-107c-4db9-93cc-7004344fcc95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43091: impossibile ordinare il prodotto in bundle dall&#39;amministratore

La patch MDVA-43091 risolve il problema che impediva agli utenti di ordinare il prodotto in bundle dall&#39;amministratore Commerce. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-43091. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si tenta di ordinare il prodotto in bundle dall&#39;amministratore, viene generato il seguente errore: *Impossibile utilizzare la quantità decimale per questo prodotto.*

<u>Passaggi da riprodurre</u>:

1. Installa un Adobe Commerce pulito.
1. Crea due prodotti semplici.
1. Crea un prodotto in bundle con due opzioni.
1. Crea un account cliente sul front-end.
1. Vai a **Amministratore** > **Vendite** > **Ordini** > **Crea nuovo ordine**.
   * Seleziona l’account cliente appena creato.
   * Prova ad aggiungere il prodotto nel carrello.

<u>Risultati previsti</u>:

L’utente amministratore può aggiungere al carrello il prodotto con una quantità.

<u>Risultati effettivi</u>:

L&#39;utente amministratore riceve il seguente errore: *Impossibile utilizzare la quantità decimale per questo prodotto.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'MDVA-44887: errore "SyntaxError non rilevato: const di token imprevisto" nel pannello di amministrazione'
description: 'La patch di MDVA-44887 risolve il problema che impediva all''utente amministratore di fare clic su un''opzione di menu. Nel pannello di amministrazione viene visualizzato l’errore *Uncatch SyntaxError: Unexpected token const* (Sintassi non rilevata: costo token imprevisto*). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15. L''ID della patch è MDVA-44887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.'
feature: Admin Workspace, Orders
role: Admin
exl-id: d8cc03c3-35a0-4f00-8ec3-1ba3e100f7ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887: errore &quot;SyntaxError non rilevato: const di token imprevisto&quot; nel pannello di amministrazione

La patch di MDVA-44887 risolve il problema che impediva all&#39;utente amministratore di fare clic su un&#39;opzione di menu. *Errore di sintassi non rilevato: errore di const* del token imprevisto visualizzato nel pannello di amministrazione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15. L&#39;ID della patch è MDVA-44887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non può fare clic su nessuna opzione di menu. *Errore di sintassi non rilevato: errore di const* del token imprevisto visualizzato nel pannello di amministrazione.

<u>Passaggi da riprodurre</u>:

1. Abilita il bundling JS.
1. Minimizza i file JS.
1. Accedi al pannello di amministrazione di Commerce.

<u>Risultati previsti</u>:

L’utente amministratore non può fare clic su nessuna opzione di menu. Errore nella console del browser: *Sintassi non rilevataErrore: numero di token imprevisto*.

<u>Risultati effettivi</u>:

Il pannello Amministratore è accessibile a un utente amministratore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

---
title: 'MDVA-42283: il formato data-ora per le impostazioni locali francesi non è valido'
description: La patch MDVA-42283 risolve il problema che causa la mancata validità del formato data/ora nella griglia dell'ordine di amministrazione per le impostazioni internazionali in francese. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L'ID della patch è MDVA-42283. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: ed99519d-03e2-444b-9cd1-e5c6e6d2ac2d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42283: il formato data-ora per le impostazioni locali francesi non è valido

La patch MDVA-42283 risolve il problema che causa la mancata validità del formato data/ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali in francese. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L&#39;ID della patch è MDVA-42283. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il formato data/ora nella griglia dell&#39;ordine di amministrazione per le impostazioni internazionali francesi non è valido.

<u>Passaggi da riprodurre</u>:

1. Creare un ordine, un cliente, una pagina CMS o un blocco CMS.
1. Vai a **Amministratore** > **Impostazioni account** e imposta le impostazioni locali dell&#39;interfaccia per l&#39;amministratore su **Français (Canada)**/**Français (Canada)(fr_CA)** o **Portoghese brasiliano (pt_BR)**.
1. Osservare il valore nella colonna della data per qualsiasi griglia di blocchi Ordine, Spedizione, Nota di credito, Cliente, Pagina CMS o CMS.

<u>Risultati previsti</u>:

La data è nel formato visualizzato nella pagina di modifica effettiva per l’entità.

<u>Risultati effettivi</u>:

Il valore data-ora non è corretto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-42807: il simbolo di valuta personalizzato non viene visualizzato nella vetrina'
description: La patch ACSD-42807 risolve il problema se il simbolo di valuta personalizzato non viene visualizzato nella vetrina. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-42807. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Storefront
role: Developer
exl-id: 9aa3dd73-fab8-4a5b-b177-5226a37ee3c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807: il simbolo di valuta personalizzato non viene visualizzato nella vetrina

La patch ACSD-42807 risolve il problema se il simbolo di valuta personalizzato non viene visualizzato nella vetrina. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-42807. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il simbolo di valuta personalizzato non viene visualizzato nella vetrina.

<u>Passaggi da riprodurre</u>:

1. Vai a **Store** > **Impostazioni** > **Configurazioni** > **Generale** > **Impostazione valuta** e seleziona una valuta personalizzata. Ad esempio, **Peso messicano**.
1. Vai a **Store** > **Impostazioni** > **Configurazioni** > **Generale** > **Opzioni internazionali** e seleziona **Spagnolo (Messico)**.
1. Vai a **Store** > **Simboli di valuta** e configura il simbolo di valuta in **MX$**.
1. Controlla il simbolo di valuta sul front-end.

<u>Risultati previsti</u>:

Il simbolo di valuta predefinito è &quot;MX$&quot; con valuta impostata come &quot;Peso messicano&quot; e lingua impostata come &quot;Spagnolo (Messico)&quot;.

<u>Risultati effettivi</u>:

Il simbolo di valuta predefinito è &quot;$&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

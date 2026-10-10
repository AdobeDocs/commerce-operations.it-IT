---
title: 'MDVA-43201: errore durante l''utilizzo di un campo DOB con PT delle impostazioni internazionali'
description: La patch MDVA-43201 risolve il problema relativo all'errore che si verifica quando si utilizza l'attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%
---
# MDVA-43201: errore durante l&#39;utilizzo di un campo DOB con PT delle impostazioni internazionali

La patch MDVA-43201 risolve il problema relativo all&#39;errore che si verifica quando si utilizza l&#39;attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l&#39;attributo del cliente DOB viene aggiunto al modulo di registrazione del cliente per le impostazioni locali portoghesi, il modulo restituisce l&#39;errore *L&#39;argomento 1 passato a iterator_to_array() deve implementare l&#39;interfaccia viaggiabile, null specificato*.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione > **Archivi** > **Configurazione** > **Generale** > **Opzioni internazionali**, imposta la lingua su **Portoghese (Portogallo)** e fai clic su **Salva**.
1. Reindicizzare e cancellare la cache.
1. Vai a **Archivi** > **Attributo** > **Cliente**.
1. Aprire l&#39;attributo del cliente DOB e impostare **Show on Storefront** su **Yes**.
1. Seleziona tutto da **Modulo da utilizzare in**.
1. Salva l’attributo.
1. Vai alla pagina Crea nuovo account nel front-end.

<u>Risultati previsti</u>:

Il modulo di registrazione cliente per l’archivio portoghese non fornisce alcun errore quando si aggiunge l’attributo DOB.

<u>Risultati effettivi</u>:

Il modulo di registrazione cliente per l’archivio portoghese restituisce un errore quando si aggiunge l’attributo DOB.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

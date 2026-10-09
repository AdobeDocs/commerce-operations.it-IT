---
title: 'MDVA-39605: valore TTL della cache Redis (data di scadenza) errato'
description: La patch MDVA-39605 risolve il problema in cui il valore TTL (data di scadenza) della cache Redis è errato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L'ID della patch è MDVA-39605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%
---
# MDVA-39605: valore TTL della cache Redis (data di scadenza) errato

La patch MDVA-39605 risolve il problema in cui il valore TTL (data di scadenza) della cache Redis è errato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-39605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore TTL (data di scadenza) della cache Redis non è corretto.

<u>Passaggi da riprodurre</u>:

Per testare la correzione, svuota la cache e apri un prodotto configurabile nella vetrina. Quindi apri un terminale (console) e segui i passaggi seguenti:

1. Eseguire il comando: `redis-cli`.
1. Esegui `KEYS "*PRICE"` (dovrebbe essere presente una sola chiave nel risultato, ad esempio `zc:ti:e54_PRICE`). Copiate la chiave.
1. Esegui `SMEMBERS` seguito dalla chiave del passaggio precedente (ad esempio, `SMEMBERS zc:ti:e54_PRICE`). Copia qualsiasi chiave dal risultato (ad esempio, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Eseguire `KEYS "*<key>"` con il nome della chiave del passaggio precedente per ottenere il nome completo della chiave, ad esempio `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`. Il risultato deve contenere una sola chiave (ad esempio, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Come si può notare, il nome completo della chiave è semplicemente il nome della chiave con prefisso &quot;`zc:k:`&quot;. Ora copia il nome completo della chiave.
1. Eseguire `HGETALL` seguito dal nome completo della chiave del passaggio 4 per verificare il valore. Il valore deve contenere dati serializzati dei prodotti associati di un prodotto configurabile correlato.
1. Eseguire `TTL` seguito dal nome completo della chiave del passaggio 4 per verificare se la chiave ha una scadenza. Il risultato deve essere diverso da **-1** e **-2** e deve essere approssimativamente 2592000 (30 giorni). Anche se la scadenza impostata nel codice è un anno, la libreria Redis utilizzata in Adobe Commerce ha un limite massimo di scadenza difficile di 2592000.

<u>Risultati previsti</u>:

Il limite di scadenza è 2592000s

<u>Risultati effettivi</u>:

Il limite di scadenza è impostato su **-1** o **-2**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

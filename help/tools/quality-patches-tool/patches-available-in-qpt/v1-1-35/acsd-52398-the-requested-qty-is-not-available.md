---
title: 'ACSD-52398: la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità del prodotto nel pacchetto'
description: Applica la patch ACSD-52398 per risolvere il problema di Adobe Commerce per cui la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-52398: la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità del prodotto nel pacchetto

La patch ACSD-52398 risolve il problema se la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52398. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti semplici con quantità *1* e *10*.
1. Crea un prodotto in bundle utilizzando i prodotti semplici.
1. Aggiungi il prodotto nel carrello.
1. Modifica il prodotto e prova ad aggiornare la quantità a *3* per l&#39;opzione in cui sono disponibili *10* elementi.

<u>Risultati previsti</u>:

Nessun errore. La quantità è stata aggiornata correttamente poiché per questa opzione sono disponibili *10* elementi.

<u>Risultati effettivi</u>:

Viene generato il seguente errore: *La quantità richiesta non è disponibile*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

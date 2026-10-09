---
title: 'ACSD-53643: l’ordine presenta un totale errato al momento del posizionamento di un ordine fornitore'
description: Applicare la patch ACSD-53643 per risolvere il problema Adobe Commerce in cui l'ordine presenta un totale errato quando si effettua un ordine con prodotti disabilitati o esauriti.
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%
---
# ACSD-53643: l’ordine presenta un totale errato al momento del posizionamento di un ordine fornitore

La patch ACSD-53643 risolve il problema relativo a un totale non corretto dell&#39;ordine quando si effettua un ordine di acquisto con prodotti disabilitati o esauriti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-53643. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il totale dell’ordine non è corretto quando si effettua un ordine di acquisto con prodotti disabilitati o esauriti.

<u>Passaggi da riprodurre</u>:

1. Installa *[!UICONTROL B2B]* e *[!UICONTROL Inventory]*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** e imposta **[!UICONTROL Company]** = *Sì* e **[!UICONTROL Purchase Order]** = *Sì*.
1. Cancella la cache di configurazione.
1. Crea una nuova società, attivala e abilita *[!UICONTROL Purchase order]* per la società.
1. Crea un nuovo utente per l’azienda.
1. Crea una *regola di approvazione* per approvare tutti gli ordini superiori a *1 USD* da parte dell&#39;amministratore della società.
1. Crea un’origine aggiuntiva.
1. Accedi come nuovo utente aziendale.
1. Aggiungi due prodotti al carrello e invia un ordine di acquisto.
1. Disattiva il secondo prodotto.
1. Accedi come amministratore della società.
1. Aprire l&#39;ordine di acquisto e verificare che l&#39;ordine di acquisto contenga entrambi i prodotti e che il totale sia relativo a entrambi.
1. Approva l&#39;ordine fornitore.
1. Effettua l’ordine.
1. Apri i dettagli dell’ordine.

<u>Risultati previsti</u>:

* Impossibile effettuare l&#39;ordine anche se un prodotto nell&#39;ordine è *disabilitato* o *esaurito*.
* Il pulsante *[!UICONTROL Place Order]* è nascosto.

<u>Risultati effettivi</u>:

L&#39;ordine inoltrato contiene solo il primo prodotto attivo, ma il totale dell&#39;ordine viene calcolato per entrambi i prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

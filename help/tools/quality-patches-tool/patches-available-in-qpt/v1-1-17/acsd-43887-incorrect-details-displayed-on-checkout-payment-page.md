---
title: 'ACSD-43887: dettagli non corretti visualizzati nella pagina di pagamento per il pagamento dell''assegno'
description: La patch di ACSD-43887 risolve il problema della visualizzazione di dettagli non corretti nella pagina Pagamento di pagamento di pagamento di pagamento quando gli ordini di acquisto per le società sono abilitati. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-43887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%
---
# ACSD-43887: dettagli non corretti visualizzati nella pagina di pagamento per il pagamento dell&#39;assegno

La patch di ACSD-43887 risolve il problema della visualizzazione di dettagli non corretti nella pagina Pagamento di pagamento di pagamento di pagamento quando gli ordini di acquisto per le società sono abilitati. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-43887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dettagli errati vengono visualizzati nella pagina Pagamento di pagamento di pagamento di pagamento quando sono abilitati gli ordini di acquisto per le società.

<u>Prerequisiti</u>:

1. I moduli B2B sono installati.
1. Abilita società è impostato su _Sì_. Vai a **Archivi** > **Configurazioni** > **Generale** > **Caratteristiche B2B** > **Abilita società** > **Sì**.
1. Abilita ordini di acquisto è impostato su _Sì_. Vai a **Configurazione approvazione ordine** > **Abilita ordini di acquisto** > **Sì**.
1. PayPal Express è configurato come metodo di pagamento.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto virtuale.
1. Registra un account aziendale dal front-end con un amministratore società.
1. Approva l&#39;account società dal backend e imposta **Abilita ordini di acquisto** come _Sì_ durante l&#39;approvazione della società.
1. Vai al front-end e accedi utilizzando l&#39;account amministratore della società creato nel passaggio due.
1. Crea un &quot;Utente predefinito&quot; per la società. Vai a **Utente società** > **Aggiungi nuovo utente**.
1. Crea una &quot;Regola di approvazione&quot; per l’azienda. Vai a **Regole di approvazione** > **Aggiungi nuova regola**.

   * Tipo di regola: totale ordine
   * Totale ordine: è maggiore o uguale a 1 $
   * Richiede l&#39;approvazione di: Amministratore società

1. Esci e accedi con l&#39;account &quot;Utente predefinito&quot;.
1. Aggiungi al carrello il prodotto virtuale creato al passaggio 1 e procedi al pagamento.
1. Seleziona PayPal Express come metodo di pagamento e fai clic su **Inserisci ordine di acquisto**.
1. Esci e accedi con l&#39;account amministratore della società.
1. Vai a **I miei ordini di acquisto** e da **Ordini di acquisto società**, fai clic su **Visualizza** per l&#39;ordine creato al passaggio nove.
1. Approva l&#39;ordine fornitore. Lo stato dell&#39;ordine fornitore deve essere &quot;Approvato: Pagamento in sospeso&quot;.
1. Esci e accedi con l’account aziendale &quot;Utente predefinito&quot;.
1. Vai a **I miei ordini di acquisto** > **Visualizza** > **Inserisci ordine**.
1. Controlla il **Riepilogo ordini**.

<u>Risultati previsti</u>:

Nel riepilogo dell&#39;ordine vengono visualizzati valori diversi da zero corretti.

<u>Risultati effettivi</u>:

Il valore totale del riepilogo degli ordini è zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

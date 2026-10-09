---
title: 'ACP2E-3918: errore di checkout per i clienti aziendali che utilizzano il prelievo in-store'
description: Applica la patch ACP2E-3918 per risolvere il problema Adobe Commerce, in cui il check-out non riesce per i clienti della società che hanno effettuato l’accesso utilizzando il ritiro in negozio senza un indirizzo di fatturazione predefinito.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '384'
ht-degree: 0%
---
# ACP2E-3918: errore di checkout per i clienti aziendali che utilizzano il prelievo in-store

La patch ACP2E-3918 risolve il problema se il check-out non riesce per i clienti della società che hanno effettuato il login e che utilizzano il ritiro in-store senza un indirizzo di fatturazione predefinito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACP2E-3918. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il check-out non riesce quando un cliente della società che ha effettuato l’accesso senza un indirizzo predefinito tenta di effettuare un ordine di acquisto utilizzando il ritiro in-store.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Purchase Orders]**.
1. Creare **[!UICONTROL Company]** e abilitare **[!UICONTROL Purchase Orders]**.
1. Crea un **[!UICONTROL Company User]** senza indirizzi salvati.
1. Abilita il metodo di spedizione **[!UICONTROL In-Store Delivery]**.
1. Aggiungi un&#39;origine inventario.
1. Aggiunge un magazzino.
1. Assegna l&#39;inventario a un prodotto.
1. Sul front-end, accedi come utente dell’azienda.
1. Aggiungi prodotti a **[!UICONTROL Cart]**.
1. Procedi con il pagamento.
1. Seleziona **[!UICONTROL In-Store Pick Up]** al passaggio di spedizione.
1. Procedi al pagamento.

<u>Risultati previsti</u>:

Il passaggio di pagamento deve essere caricato correttamente durante l’estrazione e nella console del browser non deve essere visualizzato alcun errore.

<u>Risultati effettivi</u>:

Il passaggio di pagamento non viene caricato e nella console del browser viene visualizzato il seguente errore JavaScript:

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

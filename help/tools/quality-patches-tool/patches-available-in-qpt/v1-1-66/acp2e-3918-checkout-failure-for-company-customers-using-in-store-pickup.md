---
title: 'ACP2E-3918: errore di checkout per i clienti aziendali che utilizzano il prelievo in-store'
description: Applica la patch ACP2E-3918 per risolvere il problema Adobe Commerce, in cui il check-out non riesce per i clienti della società che hanno effettuato l’accesso utilizzando il ritiro in negozio senza un indirizzo di fatturazione predefinito.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1295af44422ffbd67a3666f1a96a75af0a4e3c81
workflow-type: tm+mt
source-wordcount: '359'
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
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

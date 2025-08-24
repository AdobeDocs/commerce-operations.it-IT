---
title: 'ACSD-67347: l’ordine non riesce e viene visualizzato l’errore "Impossibile acquisire un blocco" quando si utilizzano codici coupon'
description: Applica la patch ACSD-67347 al problema Adobe Commerce in cui gli ordini non riescono con un errore "Impossibile acquisire un blocco" quando i codici coupon contengono caratteri speciali (ad esempio, BIT/123456) e il blocco file è abilitato.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: l&#39;ordine non riesce con *Impossibile acquisire un errore di blocco* quando si utilizzano codici coupon

La patch ACSD-67347 risolve il problema che causa il fallimento degli ordini con un errore *Impossibile acquisire un blocco* quando i codici coupon contengono caratteri speciali (ad esempio, BIT/123456) e il blocco file è abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-67347. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p12

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini non riescono con l&#39;errore *Impossibile acquisire un blocco* quando vengono utilizzati coupon con caratteri speciali e il blocco dei file è abilitato.

<u>Passaggi da riprodurre</u>:

1. Installare 2.4-development.
1. Impostare la configurazione del blocco file nel file `env.php`:

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Creare una regola del carrello con un coupon utilizzando il formato di codice coupon: *BIT/123456*.
1. Crea un prodotto semplice.
1. Aggiungi il prodotto al carrello e applica il codice del coupon.
1. Procedi al pagamento e invia l&#39;ordine.

<u>Risultati previsti</u>:

Gli ordini vengono inseriti correttamente perché non vi sono restrizioni alla creazione di codici coupon.

<u>Risultati effettivi</u>:

Impossibile effettuare l&#39;ordine. Viene visualizzato il seguente errore: *Impossibile acquisire il blocco.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

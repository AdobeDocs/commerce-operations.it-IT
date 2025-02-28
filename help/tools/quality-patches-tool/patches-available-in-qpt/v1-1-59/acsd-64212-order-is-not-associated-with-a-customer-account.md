---
title: 'ACSD-64212: ordine non collegato a un account cliente creato tramite [!DNL GraphQL] dopo aver effettuato l''ordine'
description: Applica la patch ACSD-64212 per risolvere il problema di Adobe Commerce per cui un ordine non viene collegato a un account cliente creato tramite [!DNL GraphQL] dopo aver effettuato l'ordine.
feature: GraphQL, Checkout, Customers
role: Admin, Developer
source-git-commit: d1d5214293f3bb38b787f80172aabf9cd0bf808b
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-64212: ordine non collegato a un account cliente creato tramite [!DNL GraphQL] dopo l&#39;ordine

La patch ACSD-64212 risolve il problema che impedisce il collegamento di un ordine a un account cliente creato tramite [!DNL GraphQL] dopo l&#39;ordine. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-64212. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;ordine non è collegato a un account cliente quando l&#39;account viene creato tramite [!DNL GraphQL] dopo l&#39;ordine.

<u>Passaggi da riprodurre</u>:

1. Effettua un ordine per gli ospiti sul front-end.
1. Invia la seguente richiesta per creare l’account:

```
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u>Risultati previsti</u>:

L&#39;ordine ospite viene associato al cliente dopo la creazione dell&#39;account cliente.

<u>Risultati effettivi</u>:

L&#39;account cliente è stato creato, ma l&#39;ordine ospite non è associato al cliente.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'ACSD-65254: notifica e-mail non inviata dopo l’aggiornamento dell’e-mail del cliente tramite updateCustomerEmail [!DNL GraphQL] mutation'
description: Applica la patch ACSD-65254 per risolvere il problema di Adobe Commerce per cui le notifiche e-mail non venivano inviate ai clienti dopo il corretto aggiornamento dei loro indirizzi e-mail sui loro account utilizzando la mutazione updateCustomerEmail [!DNL GraphQL] .
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5f7af7704c53c808298422dc165397dd255480b9
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# ACSD-65254: notifica e-mail non inviata dopo l&#39;aggiornamento dell&#39;e-mail del cliente tramite la mutazione `updateCustomerEmail` [!DNL GraphQL]

La patch ACSD-65254 risolve il problema per cui le notifiche e-mail non venivano inviate ai clienti dopo l&#39;aggiornamento dei loro indirizzi e-mail sui loro account utilizzando la mutazione `updateCustomerEmail` [!DNL GraphQL]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-65254. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le notifiche e-mail non sono state inviate ai clienti dopo l&#39;aggiornamento dei loro indirizzi e-mail utilizzando la mutazione `updateCustomerEmail` [!DNL GraphQL].

<u>Passaggi da riprodurre</u>:

1. Crea utente utilizzando la mutazione seguente:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. Genera un token per l’utente creato in precedenza e utilizzalo come token Bearer:

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Prova ad aggiornare l’e-mail per l’utente creato in precedenza utilizzando l’ultimo token bearer creato:

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>Risultati previsti</u>:

I clienti devono ricevere notifiche e-mail dopo aver aggiornato gli indirizzi e-mail sui loro account.

<u>Risultati effettivi</u>:

Al nuovo indirizzo viene inviato solo un messaggio e-mail di abbonamento; l’e-mail di conferma per la modifica dell’indirizzo e-mail non viene inviata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

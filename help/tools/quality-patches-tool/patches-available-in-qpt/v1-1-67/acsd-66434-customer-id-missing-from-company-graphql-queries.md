---
title: 'ACSD-66434: [!UICONTROL Customer ID] mancante dalla società [!DNL GraphQL] query'
description: Applica la patch ACSD-66434 per risolvere il problema di Adobe Commerce per cui [!UICONTROL Customer ID] non è presente nelle query dell'azienda [!DNL GraphQL] .
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434: [!UICONTROL Customer ID] mancante dalle query [!DNL GraphQL] della società

La patch ACSD-66434 risolve il problema di assenza di **[!UICONTROL Customer ID]** dalle query aziendali [!DNL GraphQL]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66434. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query della società [!DNL GraphQL] restituisce `null` per **[!UICONTROL Customer ID]** nella struttura della società.

<u>Passaggi da riprodurre</u>:

1. Installa lo sviluppo Adobe Commerce 2.4 con moduli B2B e Inventory.
1. Dall’amministratore di Commerce, abilita le funzioni B2B e crea una società di test.
1. Genera un token Bearer per l&#39;amministratore della società utilizzando la seguente mutazione [!DNL GraphQL]:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Utilizza il token generato per recuperare la struttura aziendale del cliente con la seguente query [!DNL GraphQL]:

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Risultati previsti</u>:

**[!UICONTROL Customer ID]** deve essere restituito nella query [!DNL GraphQL] della società.

<u>Risultati effettivi</u>:

**[!UICONTROL Customer ID]** restituisce come `null` nella query [!DNL GraphQL] della società.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

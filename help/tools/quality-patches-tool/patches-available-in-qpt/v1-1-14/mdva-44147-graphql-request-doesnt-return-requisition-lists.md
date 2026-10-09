---
title: 'MDVA-44147: la richiesta [!DNL GraphQL] non restituisce [!UICONTROL Requisition Lists]'
description: La patch MDVA-44147 risolve il problema per cui la richiesta [!DNL GraphQL] non restituisce [!UICONTROL Requisition Lists]. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 è installato. L'ID della patch è MDVA-44147. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%
---
# MDVA-44147: la richiesta [!DNL GraphQL] non restituisce [!UICONTROL Requisition Lists]

La patch MDVA-44147 risolve il problema per cui la richiesta [!DNL GraphQL] non restituisce [!UICONTROL Requisition Lists]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-44147. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta [!DNL GraphQL] non restituisce [!UICONTROL Requisition Lists].

<u>Passaggi da riprodurre</u>:

1. Vai a **Store** > **Impostazioni** > **Configurazione** > **Generale** > **Caratteristiche B2B** e abilita **[!UICONTROL Requisition List]**.
1. Accedi come cliente e aggiungi un prodotto a [[!UICONTROL Requisition List]](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/requisition-lists/requisition-lists).
1. Crea un [[!UICONTROL Customer Token]](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/).

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) &lbrace;
          token
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Utilizzare la query seguente per recuperare tutti i [!UICONTROL Requisition Lists] dal cliente. Utilizza l&#39;intestazione **Authorization** con il valore `Bearer <customer_token>`. Per ulteriori informazioni, consulta l&#39;articolo [Customer Query](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) nella documentazione per gli sviluppatori.

   Richiesta:

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Risposta:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "customer": &lbrace;
          "requisition_lists": &lbrace;
            "items": &lbrack;
            &lbrace;
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": &lbrace;
                "items": &lbrack;
                &lbrace;
                  "uid": "MQ==",
                  "product": &lbrace;
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    &rbrace;,
                    "quantity": 1
                  &rbrace;
                  &rbrack;,
                  "total_pages": 1
                &rbrace;
              &rbrace;
              &rbrack;,
              "total_count": 1
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Copia l’UID di qualsiasi elemento dall’elenco restituito (MQ==) e utilizza la seguente query per ottenere l’elenco filtrato da UID.

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20,
          filter: &lbrace;
            uids: &lbrace;
              eq: "MQ=="
            &rbrace;
          &rbrace;
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

<u>Risultati previsti</u>:

Viene restituito un risultato.

<u>Risultati effettivi</u>:

Vengono restituiti zero risultati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in [!DNL QPT], fare riferimento a [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

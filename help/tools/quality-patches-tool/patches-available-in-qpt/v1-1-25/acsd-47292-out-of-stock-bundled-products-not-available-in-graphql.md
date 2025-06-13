---
title: 'ACSD-47292: i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL'
description: Applica la patch ACSD-47292 per risolvere il problema di Adobe Commerce per cui i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL anche se "show out-of-stock products" (Mostra prodotti esauriti) è impostato su Sì.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292: i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL

La patch ACSD-47292 risolve il problema per cui i prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL anche se [!UICONTROL Display Out-of-Stock Products] è impostato su *[!UICONTROL Yes]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-47292. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti in bundle esauriti non sono disponibili nella risposta di GraphQL anche se [!UICONTROL Display Out-of-Stock Products] è impostato su *[!UICONTROL Yes]*.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Adobe Commerce > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** e imposta [!UICONTROL Display Out-of-Stock Products] su *[!UICONTROL Yes]*.
1. Crea due prodotti semplici, s1 e s2.
1. Rendere s1 esaurito e non visibile singolarmente e s2 in magazzino e non visibile singolarmente, quindi assegnarli a una categoria.
1. Crea un prodotto in bundle con almeno un prodotto opzione e assegna s1 e s2 a questa opzione (tipo di input &quot;RadioButton&quot;).
1. Salva il prodotto in bundle e assegnalo a una categoria.
1. Vai alla vetrina e apri questo prodotto in bundle. L’opzione esaurita s1 è disattivata ma visibile.
1. Invia una richiesta GraphQL:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Risultati previsti</u>:

L&#39;opzione del bundle s1 è elencata nella risposta di GraphQL poiché [!UICONTROL Display Out-of-Stock Products] è impostata su *[!UICONTROL Yes]* ed è visibile nella vetrina.

<u>Risultati effettivi</u>:

l’opzione del bundle s1 non è elencata nella risposta di GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

---
title: 'ACSD-46519: [!UICONTROL product_count] nella query [!DNL GraphQL] di [!UICONTROL categoryList] restituisce 0 per le categorie di ancoraggio'
description: Applicare la patch ACSD-46519 per risolvere il problema Adobe Commerce, in cui quando si utilizza il metodo [!UICONTROL categoryList] [!DNL GraphQL] per ottenere categorie figlio, il valore [!UICONTROL product_count] viene visualizzato come 0 per le categorie padre.
feature: Categories, GraphQL, Products
role: Admin
exl-id: 7becaa4e-421a-4983-ac73-f5b58fc45d8f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '377'
ht-degree: 0%
---
# ACSD-46519: [!UICONTROL product_count] nella query [!DNL GraphQL] di [!UICONTROL categoryList] restituisce 0 per le categorie di ancoraggio

La patch ACSD-46519 risolve il problema per cui la query [!UICONTROL product_count] in [!UICONTROL categoryList] [!DNL GraphQL] restituisce 0 per le categorie di ancoraggio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-46519. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si utilizza il metodo [!UICONTROL categoryList] [!DNL GraphQL] per ottenere categorie figlio, [!UICONTROL product_count] viene visualizzato come 0 per le categorie padre.

<u>Passaggi da riprodurre</u>:

1. Utilizza la seguente richiesta [!DNL GraphQL] per ottenere la gerarchia di categorie con [!UICONTROL product_count]:

<pre><code>
&lbrace;
  categoryList(filters: { ids: { eq: "2" } }) &lbrace;
    id
    name
    product_count
    level
    children &lbrace;
      name
      product_count
      level
      children &lbrace;
        name
        product_count
        level
        children &lbrace;
          name
          product_count
          level
          children &lbrace;
            name
            product_count
            level
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code></pre>

<u>Risultati previsti</u>:

Se la categoria padre è una categoria ancorata, [!UICONTROL product_count] deve mostrare la somma dei conteggi dei prodotti della categoria figlio a ogni livello.

<u>Risultati effettivi</u>:

Se la categoria padre è ancorata, i prodotti vengono visualizzati come 0 per il livello di categoria 2 e verso il basso.

<pre><code>
&lbrace;
    "data": &lbrace;
        "categoryList": &lbrack;
            &lbrace;
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": &lbrack;
                    &lbrace;
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    &rbrace;,
                    &lbrace;
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": &lbrack;
                            &lbrace;
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;,
                            &lbrace;
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;
                        &rbrack;
                    &rbrace;,
                    ...
                &rbrack;
            &rbrace;
        &rbrack;
    &rbrace;
&rbrace;
</code></pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

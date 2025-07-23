---
title: 'ACSD-65750: [!DNL GraphQL]  La query "route" restituisce prodotti fuori ordine nel tipo di contenuto  [!DNL Page Builder] Prodotti'
description: Applica la patch ACSD-65750 per risolvere il problema di Adobe Commerce, in cui la query "route" di GraphQL restituisce prodotti non ordinati nel tipo di contenuto  [!DNL Page Builder] Prodotti.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750: la query &quot;route&quot; [!DNL GraphQL] restituisce prodotti fuori ordine nel tipo di contenuto [!DNL Page Builder] prodotti

La patch ACSD-65750 risolve il problema per cui la query &quot;route&quot; di [!DNL GraphQL] restituisce prodotti non ordinati nel tipo di contenuto [!DNL Page Builder] Products. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-65750. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query &quot;route&quot; di [!DNL GraphQL] non restituisce i prodotti nel tipo di ordinamento corretto quando si utilizza il tipo di contenuto Prodotti [!DNL Page Builder].

<u>Passaggi da riprodurre</u>:

1. Crea una nuova categoria e alcuni prodotti nel catalogo e collega i prodotti a questa categoria.
1. Passare a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, modificare la categoria creata e aprire la scheda **[!UICONTROL Products in Category]**.
1. Imposta **[!UICONTROL Position]** personalizzato per ogni prodotto di questa categoria.
1. Salva la categoria ed esegui la reindicizzazione.
1. Passare a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** e fare clic su **[!UICONTROL Add New Page]**.
1. Espandere la scheda **[!UICONTROL Content]**, quindi fare clic su **[!UICONTROL Edit with Page Builder]**.
1. Trascinare un elemento **[!UICONTROL Row]** nell&#39;area del contenuto, quindi trascinare un elemento **[!UICONTROL Products]** nella riga.
1. Configura l’elemento Products come segue:
   * **[!UICONTROL Select Products By]**: *Categoria*
   * **[!UICONTROL Category]**: *Seleziona la categoria appena creata*
   * **[!UICONTROL Sort By]**: *Posizione*
1. Passare alla scheda **[!UICONTROL Search Engine Optimization]** e impostare **[!UICONTROL URL Key]** su *test-widget*.
1. Salva la pagina.
1. Effettua la seguente richiesta [!DNL GraphQL]:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Risultati previsti</u>:

Il sistema restituisce i prodotti nell&#39;ordine definito dalla relativa posizione della categoria.

<u>Risultati effettivi</u>:

Il sistema restituisce i prodotti in un ordine che non corrisponde alla loro posizione di categoria nella risposta di GraphQL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

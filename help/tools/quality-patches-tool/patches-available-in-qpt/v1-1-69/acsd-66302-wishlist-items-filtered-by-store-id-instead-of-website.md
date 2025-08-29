---
title: 'ACSD-66302: elementi della lista dei desideri filtrati per ID negozio invece che per sito Web'
description: Applica la patch ACSD-66302 per risolvere il problema Adobe Commerce in cui gli elementi della lista dei desideri vengono filtrati per ID archivio invece che per sito Web in [!DNL GraphQL] richieste.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302: elementi della lista dei desideri filtrati per ID negozio invece che per sito Web

La patch ACSD-66302 risolve il problema che causava il filtraggio degli elementi della lista dei desideri in base all&#39;ID archivio invece che al sito Web nelle richieste [!DNL GraphQL]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66302. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi della lista dei desideri vengono filtrati in modo errato in base all&#39;ID store anziché al sito Web.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea un&#39;ulteriore visualizzazione dello store.
1. In Amministrazione, passare a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** e impostare **[!UICONTROL Enable Multiple Wish Lists]** su `Yes`.
1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** e imposta **[!UICONTROL Add Store Code to Urls]** su `Yes`.
1. Crea un account cliente.
1. Utilizza una richiesta [!DNL GraphQL] per recuperare il token di autenticazione del cliente.
1. Accedi come cliente.
1. Selezionare **[!UICONTROL Default Store View]** e aggiungere il prodotto alla lista dei desideri.
1. Passa alla visualizzazione archivio *test*.
1. Conferma che il prodotto sia ancora presente nella lista dei desideri (comportamento corretto).
1. Eseguire la seguente query [!DNL GraphQL]:

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. Esegui la query sull’archivio predefinito: il prodotto viene visualizzato come previsto.
1. Esegui la stessa query sull’archivio dei test: il prodotto non viene visualizzato.

<u>Risultati previsti</u>:

Il prodotto deve essere visibile in tutte le visualizzazioni dello store all&#39;interno dello stesso sito Web tramite [!DNL GraphQL] query.

<u>Risultati effettivi</u>:

Il prodotto scompare dalla lista dei desideri quando si passa da una visualizzazione all’altra dello store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

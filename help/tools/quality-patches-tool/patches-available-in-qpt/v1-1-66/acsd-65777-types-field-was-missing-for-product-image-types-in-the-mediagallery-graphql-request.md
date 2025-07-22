---
title: 'ACSD-65777: campo "types" mancante per i tipi di immagine del prodotto nella richiesta GraphQL "MediaGallery"'
description: Applica la patch ACSD-65777 per risolvere il problema di Adobe Commerce in cui il campo "types" (tipi) era mancante per i tipi di immagini del prodotto nella richiesta GraphQL "MediaGallery".
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777: campo **[!UICONTROL types]** mancante per i tipi di immagine prodotto nella richiesta GraphQL `MediaGallery`

La patch ACSD-65777 risolve il problema relativo all&#39;assenza del campo **[!UICONTROL types]** per i tipi di immagine prodotto nella richiesta GraphQL `MediaGallery`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-65777. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Manca il campo **[!UICONTROL types]** per i tipi di immagine del prodotto durante il recupero dei dati multimediali tramite la richiesta GraphQL `MediaGallery`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto.
1. Carica un’immagine nel prodotto.
1. Recupera i dati multimediali utilizzando il seguente GraphQL.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Risultati previsti</u>:

L&#39;interfaccia GraphQL `media_gallery` deve includere il campo **[!UICONTROL types]**.

<u>Risultati effettivi</u>:

`media_gallery` non contiene il campo **[!UICONTROL types]** del supporto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

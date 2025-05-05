---
title: 'ACSD-59925: ordinamento degli elementi in [!UICONTROL Media Gallery] in base alla posizione in GraphQL'
description: Applicare la patch ACSD-59925 per risolvere il problema di Adobe Commerce per cui gli elementi in [!UICONTROL Media Gallery] non sono ordinati per posizione, causando un ordine di visualizzazione errato.
feature: Media, GraphQL
role: Admin, Developer
exl-id: a4dd840f-44d2-40dc-b0e1-13d55b688204
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925: ordinamento degli elementi in [!UICONTROL Media Gallery] in base alla posizione in GraphQL

La patch ACSD-59925 risolve il problema che impediva l&#39;ordinamento degli elementi in [!UICONTROL Media Gallery] in base alla posizione, causando un ordine di visualizzazione errato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-59925. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi in [!UICONTROL Media Gallery] non sono ordinati in base alla posizione, causando un ordine di visualizzazione errato.

<u>Passaggi da riprodurre</u>:

1. Crea/Modifica il prodotto.
1. Aggiungi due o più immagini e salvala.
1. Modificare lo stesso prodotto, ma questa volta trascinare l&#39;ultima immagine nella prima posizione.
1. Salva il prodotto.
1. Reindicizzare.
1. Vai al client GraphQL.
1. Esegui query GraphQL:

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u>Risultati previsti</u>:

Gli elementi in `media_gallery` sono ordinati per posizione.

<u>Risultati effettivi</u>:

Gli elementi in `media_gallery` non sono ordinati per posizione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

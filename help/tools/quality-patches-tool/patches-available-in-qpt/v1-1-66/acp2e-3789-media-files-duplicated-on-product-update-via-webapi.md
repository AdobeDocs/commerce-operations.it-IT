---
title: 'ACP2E-3789: file multimediali duplicati all’aggiornamento del prodotto tramite WebAPI'
description: Applicare la patch ACP2E-3789 per risolvere il problema Adobe Commerce, in cui vengono aggiornati i prodotti tramite file multimediali duplicati WebAPI quando viene fornito un ID multimediale.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
exl-id: 1eaa8ed0-fde6-47c4-9339-8f5e7bce7b19
source-git-commit: f82dcd6c76ba3512e59275c26815b6bb89e53733
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACP2E-3789: file multimediali duplicati all’aggiornamento del prodotto tramite WebAPI

La patch ACP2E-3789 risolve il problema relativo agli aggiornamenti dei prodotti tramite file multimediali duplicati WebAPI quando viene fornito un ID multimediale. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACP2E-3789. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento di un prodotto tramite WebAPI con un ID file multimediali determina la duplicazione dei file multimediali da parte del sistema anziché la loro sostituzione, creando nuovi file con ogni chiamata API e generando un accumulo di immagini che sovraccarica la directory `/pub/media/catalog/products/cache/`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto e aggiungi un’immagine.
1. Ottenere i dettagli del prodotto utilizzando l&#39;API REST in `base_url/rest/V1/products/<sku>`.
1. Esegui una richiesta PUT per aggiornare il prodotto mantenendo `media_gallery_entrie` invariati (nome immagine e file uguali).
1. Controllare la directory `pub/media/catalog/product/xx/yy` prima e dopo l&#39;aggiornamento.

<u>Risultati previsti</u>:

Il file di immagine viene sostituito quando l’ID del file multimediale viene incluso nella richiesta.

<u>Risultati effettivi</u>:

L’immagine viene duplicata con un nuovo nome (ad esempio, wb04-blue-1.jpg), causando un accumulo di file non necessario.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

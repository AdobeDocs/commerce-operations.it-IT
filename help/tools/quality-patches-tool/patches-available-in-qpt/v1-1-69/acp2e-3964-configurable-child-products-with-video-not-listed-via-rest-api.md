---
title: 'ACP2E-3964: prodotti secondari configurabili con video non elencato tramite API REST'
description: Applicare la patch ACP2E-3964 per risolvere il problema Adobe Commerce, in cui i prodotti secondari di prodotti configurabili con un video in [!UICONTROL Media Gallery] non sono elencati tramite l'API REST.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964: prodotti secondari configurabili con video non elencato tramite API REST

La patch ACP2E-3964 risolve il problema per cui i prodotti secondari di prodotti configurabili con un video in **[!UICONTROL Media Gallery]** non sono elencati tramite l&#39;API REST. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACP2E-3964. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti secondari di prodotti configurabili con un video in **[!UICONTROL Media Gallery]** non possono essere elencati tramite API REST, causando una risposta di errore.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo prodotto configurabile e aggiungi un singolo prodotto secondario.
1. Modificare il prodotto secondario e aggiungere un video in **[!UICONTROL Images and Videos]** (ad esempio, [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Salva il prodotto secondario.
1. Invia una richiesta GET all&#39;endpoint REST API: `rest/v1/configurable-products/%sku%/children` utilizzando un token Bearer amministratore.

<u>Risultati previsti</u>:

L&#39;API REST deve restituire i dati del prodotto secondario senza errori, incluse le informazioni video in **[!UICONTROL Media Gallery]**.

<u>Risultati effettivi</u>:

L’API REST restituisce un errore:

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

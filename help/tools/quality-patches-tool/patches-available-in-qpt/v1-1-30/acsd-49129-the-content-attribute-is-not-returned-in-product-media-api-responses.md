---
title: '"ACSD-49129: attributo "Content" non restituito nelle risposte API dei supporti di prodotto"'
description: Applica la patch ACSD-49129 per risolvere il problema di Adobe Commerce, in cui l’attributo *content* (*base64 image code*) non viene restituito nelle risposte API "rest/V1/products/sku/media" product media.
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-49129: attributo &quot;Content&quot; non restituito nelle risposte API per gli elementi multimediali del prodotto

La patch ACSD-49129 risolve il problema per cui l&#39;attributo *content* (*[!UICONTROL base64 image code]*) non viene restituito nelle risposte API dei supporti di prodotto `rest/V1/products/sku/media`. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.30. L’ID della patch è ACSD-49129. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;attributo *content* (*[!UICONTROL base64 image code]*) non è restituito nelle risposte API dei supporti di prodotto `rest/V1/products/sku/media`.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con un’immagine.
1. GET Invia *richiesta REST API* a `rest/V1/products/<sku>/media` e `rest/V1/products/<sku>/media/<entryId>`.
1. Controlla le risposte API.

<u>Risultati previsti</u>

L&#39;attributo *content* con i dati è disponibile tramite API REST.

<u>Risultati effettivi</u>

L&#39;attributo *content* non è presente nelle risposte API.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

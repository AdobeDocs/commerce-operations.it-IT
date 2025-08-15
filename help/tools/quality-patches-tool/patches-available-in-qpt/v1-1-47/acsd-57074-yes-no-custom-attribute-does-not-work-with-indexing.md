---
title: 'ACSD-57074: *Yes/No* l’attributo personalizzato con il prefisso "price_*" nell’attributo "attribute_code" non funziona con l’indicizzazione'
description: Applica la patch ACSD-57074 per risolvere il problema di Adobe Commerce per cui l’attributo personalizzato *Yes/No* con prefisso "price_*" nell’attributo "attribute_code" non funziona con l’indicizzazione.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: l&#39;attributo personalizzato *Yes/No* con prefisso `price_*` nell&#39;attributo `attribute_code` non funziona con l&#39;indicizzazione

La patch ACSD-57074 risolve il problema che impedisce l&#39;indicizzazione dell&#39;attributo personalizzato *Sì/No* con prefisso `price_*` nell&#39;attributo `attribute_code`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.47. L’ID della patch è ACSD-57074. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;attributo personalizzato *Yes/No* con prefisso `price_*` nell&#39;attributo `attribute_code` non funziona con l&#39;indicizzazione.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo di prodotto personalizzato con le seguenti opzioni:
   * *[!UICONTROL Catalog Input Type]*: *Sì/No*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sì*
1. Assegnare l&#39;attributo al set di attributi predefinito.
1. Crea un prodotto con l’attributo creato.
1. Assegna il prodotto appena creato a una categoria.
1. Esegui reindicizzazione completa.

<u>Risultati previsti</u>:

Il prodotto viene visualizzato nella categoria assegnata.

<u>Risultati effettivi</u>:

Il prodotto non viene visualizzato nella pagina iniziale della categoria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

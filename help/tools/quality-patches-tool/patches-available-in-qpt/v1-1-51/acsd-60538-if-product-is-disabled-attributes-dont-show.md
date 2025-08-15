---
title: 'ACSD-60538: gli attributi non vengono visualizzati correttamente se il prodotto è disabilitato in [!UICONTROL All Store Views]'
description: Applica la patch ACSD-60538 per risolvere il problema di Adobe Commerce, in cui se un prodotto è disabilitato in *Tutte le visualizzazioni store* e abilitato solo in ambiti di visualizzazione store specifici, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: gli attributi non vengono visualizzati correttamente se il prodotto è disabilitato in *[!UICONTROL All Store Views]*

La patch ACSD-60538 risolve il problema per cui se un prodotto è disabilitato in *[!UICONTROL All Store Views]* e abilitato solo in ambiti di visualizzazione specifici dell&#39;archivio, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-60538. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se un prodotto è disabilitato in *[!UICONTROL All Store Views]* e abilitato solo in ambiti di visualizzazione specifici dell&#39;archivio, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando la visualizzazione non corretta del prodotto.

<u>Prerequisiti</u>:

Il modulo Inventario è installato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con l&#39;attributo *color* e tre prodotti secondari (*blue*, *black* e *brown*).
1. Disabilita due prodotti secondari associati (*blue* e *black*) nell&#39;ambito *[!UICONTROL All Store Views]*.
1. Passare all&#39;ambito **[!UICONTROL Store View]**.
1. Abilita i prodotti secondari (*blue* e *black*) nell&#39;ambito *[!UICONTROL Store View]*.
1. Esegui la richiesta GraphQL seguente:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Risultati previsti</u>:

La risposta di GraphQL include i valori dell&#39;attributo per il prodotto associato figlio disabilitato in *[!UICONTROL All Store Views]* e abilitato nell&#39;ambito *[!UICONTROL Store View]*.

<u>Risultati effettivi</u>:

La risposta di GraphQL contiene valori di attributo vuoti per il prodotto associato secondario quando il prodotto è disabilitato su *[!UICONTROL All Store Views]* e abilitato nell&#39;ambito *[!UICONTROL Store View]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

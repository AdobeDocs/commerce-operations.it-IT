---
title: 'ACSD-48210: l’attributo di ambito specifico della vista archivio sostituisce i valori globali'
description: Applicare la patch ACSD-48210 per risolvere il problema Adobe Commerce relativo all'aggiornamento di un attributo *[!UICONTROL Website Scope]* in una visualizzazione archivio specifica sostituisce i valori dell'attributo nell'ambito globale.
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%
---
# ACSD-48210: gli attributi di ambito specifici della vista archivio sovrascrivono i valori globali

La patch ACSD-48210 risolve il problema per cui quando si aggiorna un attributo *[!UICONTROL Website Scope]* all&#39;interno di una visualizzazione archivio specifica, i valori dell&#39;attributo nell&#39;ambito globale vengono ignorati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50. L’ID della patch è ACSD-48210. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si aggiorna un attributo *[!UICONTROL Website Scope]* all&#39;interno di una visualizzazione archivio specifica, i valori dell&#39;attributo nell&#39;ambito globale vengono ignorati.

L&#39;importazione di prezzi di prodotti con più righe che condividono gli stessi `SKU` e `store_view_code` ha causato aggiornamenti non corretti dei prezzi negli ambiti *[!UICONTROL All Store View]* e *[!UICONTROL Default Store]*. La modifica dell&#39;attributo dell&#39;ambito del sito Web in una visualizzazione archivio specifica non esclude più il valore dell&#39;attributo nell&#39;ambito globale.
<u>Passaggi da riprodurre</u>:

1. Configurare *[!UICONTROL Catalog Price Scope]* in *[!UICONTROL Website]*.
1. Creare un prodotto semplice denominato *SP01* e impostare il prezzo su *$84.50*.
1. Importa il prodotto utilizzando il seguente file CSV:

   ```text
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. Controllare il prezzo del prodotto negli ambiti *[!UICONTROL All Store View]* e *[!UICONTROL Default Store]*.

<u>Risultati previsti</u>:

* Il primo valore non vuoto viene utilizzato per l&#39;ambito *[!UICONTROL Default Store]*.
* L&#39;ambito *[!UICONTROL All Store View]* rimane invariato.

<u>Risultati effettivi</u>:

* Il prezzo dell&#39;ambito *[!UICONTROL All Store View]* cambia in *$86.59*.
* Il prezzo dell&#39;ambito *[!UICONTROL Default Store]* cambia in *$86.59*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

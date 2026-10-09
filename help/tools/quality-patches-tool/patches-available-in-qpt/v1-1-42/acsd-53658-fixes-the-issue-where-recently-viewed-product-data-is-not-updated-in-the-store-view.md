---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** dati non aggiornati correttamente nella visualizzazione archivio'
description: Applicare la patch ACSD-53658 per risolvere il problema di Adobe Commerce per cui i dati **[!UICONTROL Recently Viewed Product]** non vengono aggiornati correttamente nella visualizzazione archivio.
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
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
source-wordcount: '397'
ht-degree: 0%
---
# ACSD-53658: i dati **[!UICONTROL Recently Viewed Product]** non vengono aggiornati correttamente nella visualizzazione archivio

La patch ACSD-53658 risolve il problema che causa l&#39;aggiornamento non corretto dei dati di **[!UICONTROL Recently Viewed Product]** nella visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-53658. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati di **[!UICONTROL Recently Viewed Product]** non sono aggiornati correttamente nella visualizzazione archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Crea una seconda visualizzazione store per il sito Web predefinito.
1. Crea un prodotto semplice.
1. Imposta un nome di prodotto diverso per la nuova visualizzazione store.
1. Crea un widget **[!UICONTROL Recently Viewed Product]**.
1. Configura questo widget per visualizzarlo nella home page.
1. Apri la pagina del prodotto sullo Storefront dalla visualizzazione predefinita dello store.
1. Aprire la home page.
1. Utilizzando il commutatore store, passare alla seconda visualizzazione store.

<u>Risultati previsti</u>:

Il nome del prodotto viene aggiornato nel widget.

<u>Risultati effettivi</u>:

Il nome del prodotto non viene aggiornato nel widget.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

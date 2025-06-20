---
title: 'ACSD-58790: corregge la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto in visualizzazione mobile su [!DNL Chrome]'
description: ACSD-58790 risolve il problema di Adobe Commerce, per cui l'immagine nella visualizzazione per dispositivi mobili in  [!DNL Chrome]  non veniva ingrandita come previsto.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790: corregge la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto in visualizzazione mobile su [!DNL Chrome]

La patch ACSD-58790 risolve il problema di Adobe Commerce, per cui l&#39;immagine nella visualizzazione per dispositivi mobili su [!DNL Chrome] non veniva ingrandita come previsto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-58790. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stata corretta la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili in [!DNL Chrome].

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con un’immagine.
1. Aprire il prodotto da un browser [!DNL Chrome].
1. Fai clic sull’immagine e verifica che l’immagine si ingrandisca con il doppio clic.
1. Passare alla visualizzazione per dispositivi mobili utilizzando gli strumenti di sviluppo [!DNL Chrome].
1. Fai clic sull’immagine.
1. Tocca due volte.

<u>Risultati previsti</u>:

L&#39;immagine viene ingrandita quando si fa doppio clic.

<u>Risultati effettivi</u>:

L&#39;immagine non viene ingrandita quando si fa doppio clic. Questo problema è specifico di [!DNL Chrome] nella visualizzazione per dispositivi mobili, in quanto la funzionalità di zoom funziona come previsto in [!DNL Firefox].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

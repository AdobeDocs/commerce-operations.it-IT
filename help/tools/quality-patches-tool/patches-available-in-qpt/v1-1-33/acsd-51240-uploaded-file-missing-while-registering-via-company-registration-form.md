---
title: 'ACSD-51240: file caricato mancante durante la registrazione tramite il modulo di registrazione della società'
description: Applica la patch ACSD-51240 per risolvere il problema di Adobe Commerce relativo alla mancanza del file caricato durante la registrazione tramite il modulo di registrazione della società.
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240: file caricato mancante durante la registrazione tramite il modulo di registrazione della società

>[!NOTE]
>
>Questa patch è sostituita da [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

La patch ACSD-51240 risolve il problema relativo alla mancanza del file caricato durante la registrazione tramite il modulo di registrazione della società. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. L’ID della patch è ACSD-51240. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Problema

Il file caricato risulta mancante durante la registrazione tramite il modulo di registrazione della società.

<u>Passaggi da riprodurre</u>:

1. Imposta **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Sì*.
1. Creare un nuovo attributo cliente di tipo **[!UICONTROL File]**, impostare **[!UICONTROL Show in StoreFront]** = *Sì* e selezionare **[!UICONTROL all forms]**.
1. Crea una nuova società sullo Storefront e carica un&#39;immagine per il nuovo attributo.
Apri l’azienda e l’utente amministratore sullo Storefront.

<u>Risultati previsti</u>:

Viene visualizzato il file caricato.

<u>Risultati effettivi</u>:

Il file caricato non viene visualizzato nella pagina dell&#39;azienda né nella pagina del cliente amministratore in [!UICONTROL Commerce Admin].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

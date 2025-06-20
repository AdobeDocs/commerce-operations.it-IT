---
title: 'ACSD-47137: migliorare la velocità di caricamento della galleria di immagini "pub/media" cartella big'
description: Applica la patch ACSD-47137 per migliorare la velocità di caricamento della galleria di immagini quando la cartella "pub/media" è molto grande.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: migliora la velocità di caricamento della galleria di immagini quando la cartella `pub/media` è grande

La patch ACSD-47137 migliora la velocità di caricamento della raccolta immagini quando la cartella `pub/media` è molto grande. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-47137. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La velocità di caricamento della raccolta immagini è lenta quando la cartella `pub/media` è molto grande.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Adobe Commerce > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** a _No_.
1. Pulisci la cache di configurazione.
1. Esci e accedi di nuovo come utente amministratore.
1. Nella barra laterale di amministrazione, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** e seleziona la categoria principale.
1. Espandere la sezione **[!UICONTROL Content]** e fare clic su **[!UICONTROL Select from Gallery]**.

Durante il caricamento della pagina, Adobe Commerce invia la richiesta `media_gallery/directories/gettree` per caricare la struttura di cartelle multimediali.

<u>Risultati previsti</u>:

La richiesta `media_gallery/directories/gettree` deve caricare il contenuto solo dalle directory necessarie, ad eccezione del ciclo dell&#39;intero elenco di percorsi dalla cartella `pub/media/`.

<u>Risultati effettivi</u>:

Il caricamento della richiesta di `media_gallery/directories/gettree` richiede molto tempo se la cartella `pub/media/` contiene molti contenuti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

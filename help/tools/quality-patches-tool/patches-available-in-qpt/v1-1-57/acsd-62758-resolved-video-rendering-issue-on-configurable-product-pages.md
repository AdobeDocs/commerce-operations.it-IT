---
title: 'ACSD-62758: problema di rendering video risolto nelle pagine di prodotti configurabili'
description: Applica la patch ACSD-62758 per risolvere il problema di Adobe Commerce, a causa del quale i video dei prodotti nelle pagine dei dettagli configurabili del prodotto non vengono riprodotti correttamente se gli URL contengono opzioni di campioni preselezionate.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: problema di rendering video risolto nelle pagine di prodotti configurabili

La patch ACSD-62758 risolve il problema per cui i video dei prodotti nelle pagine dei dettagli configurabili del prodotto non vengono riprodotti correttamente se gli URL contengono opzioni di campioni preselezionate. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62758. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I video sui prodotti non vengono riprodotti correttamente nelle pagine di dettaglio configurabili quando l’URL include opzioni di campione preselezionate, causando la visualizzazione di un’immagine statica al posto del video.

<u>Passaggi da riprodurre</u>:

1. Passa a [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Selezionare l&#39;attributo **[!UICONTROL Color]** e modificarlo.
1. Aggiorna le seguenti impostazioni:
   1. Imposta [!UICONTROL Catalog Input Type for Store Owner] su [!UICONTROL Visual Swatch].
   1. Imposta **[!UICONTROL Update Product Preview Image]** su **[!UICONTROL Yes]**.
1. Crea alcune opzioni per questo attributo.
1. Creare una nuova categoria e aggiungervi un nuovo prodotto configurabile, utilizzando l&#39;attributo **[!UICONTROL Color]**.
1. Aggiungi una singola immagine casuale al prodotto principale.
1. Modifica i prodotti secondari configurabili appena creati e aggiungi un video alla galleria multimediale:
   1. Fare clic su **[!UICONTROL Add Video]** e utilizzare l&#39;URL del video di prova: https://vimeo.com/12860646.
1. Salva il prodotto, cancella la cache e reindicizza l’archivio.
1. Apri il prodotto appena creato nella vetrina, seleziona una delle opzioni dei campioni e verifica che il video venga caricato correttamente con il pulsante del lettore visualizzato.
1. Il video dovrebbe essere caricato come previsto e dovrebbe essere visualizzato il pulsante del lettore.
1. Fare clic con il pulsante destro del mouse su una delle opzioni del campione, selezionare **[!UICONTROL Inspect]** e individuare l&#39;ID attributo e l&#39;ID opzione. Copiare l&#39;URL del prodotto e aggiungere alla fine quanto segue: `www.product-url.com/producit-test#attribute_id=option_id`. In questo modo verrà preselezionata l’opzione campione. Apri l’URL aggiornato in una nuova finestra.

<u>Risultati previsti</u>:

Il video dovrebbe essere caricato correttamente, in modo simile a quando un’opzione campione è selezionata manualmente.

<u>Risultati effettivi</u>:

Al posto del video viene visualizzata un’immagine statica. Gli errori della console vengono registrati e indicano un errore nell’inizializzazione video.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.


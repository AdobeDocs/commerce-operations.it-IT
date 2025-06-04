---
title: 'ACSD-65100: la rimozione dei valori [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] nella configurazione [!UICONTROL Media Gallery Image Optimization] causa un errore'
description: Applicare la patch ACSD-65100 per risolvere il problema di Adobe Commerce per cui la rimozione dei valori [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] nella configurazione [!UICONTROL Media Gallery Image Optimization] causa un errore durante il processo di ottimizzazione dell'immagine.
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100: la rimozione dei valori [!UICONTROL Maximum Width] e [!UICONTROL Maximum Height] nella configurazione [!UICONTROL Media Gallery Image Optimization] causa un errore

La patch ACSD-65100 risolve il problema che causa un errore durante il processo di ottimizzazione dell&#39;immagine se si rimuovono i valori **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** nella configurazione **[!UICONTROL Media Gallery Image Optimization]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65100. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante il processo di ottimizzazione dell&#39;immagine quando i valori per **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]** vengono rimossi nella configurazione **[!UICONTROL Media Gallery Image Optimization]**.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Rimuovere i valori per **[!UICONTROL Maximum Width]** e **[!UICONTROL Maximum Height]**.
1. Pulisci la cache di configurazione.
1. Passa a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Apri qualsiasi pagina per la modifica.
1. Nell&#39;area dei contenuti:
   1. Selezionare **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**.
   1. Selezionare **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**.
   1. Nell&#39;editor di WYSIWYG, fare clic su **[!UICONTROL Add Image]**.
   1. Caricare un&#39;immagine e selezionare **[!UICONTROL Add Selected]**.
1. Controllare il file `var/log/exception.log`.

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

Viene registrato un errore simile al seguente:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

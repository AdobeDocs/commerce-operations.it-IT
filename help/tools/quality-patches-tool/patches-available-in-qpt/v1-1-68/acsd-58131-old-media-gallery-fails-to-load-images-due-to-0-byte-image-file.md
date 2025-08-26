---
title: 'ACSD-58131: la galleria di vecchi supporti non riesce a caricare le immagini a causa di un file di immagine a 0 byte'
description: Applica la patch ACSD-58131 per risolvere il problema di Adobe Commerce, in cui la vecchia raccolta multimediale non riesce a eseguire il rendering delle immagini quando nella directory è presente un’immagine a 0 byte.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: la galleria di vecchi supporti non riesce a caricare le immagini a causa di un file di immagine a 0 byte

La patch ACSD-58131 risolve il problema che impediva il rendering delle immagini della vecchia raccolta multimediale quando nella directory è presente un&#39;immagine a 0 byte. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-58131. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si inserisce un&#39;immagine a 0 byte nella directory della raccolta multimediale, la vecchia raccolta multimediale non riesce a eseguire il rendering delle immagini. Il sistema aggiornato ignora i file a 0 byte non validi, visualizza le immagini valide come previsto e registra un avviso per ogni file non valido.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Imposta **[!UICONTROL Enable Old Media Gallery]** su *Sì*.
1. Inserire alcune immagini nella directory `pub/media/wysiwyg`.
1. Creare un&#39;immagine a 0 byte nella stessa directory utilizzando `touch pub/media/wysiwyg/empty_image.png`.
1. Aggiungere un&#39;immagine dalla directory `wysiwyg` tramite Page Builder in qualsiasi contenuto (ad esempio, un blocco CMS):
   1. Crea un nuovo blocco. Vai a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** e fai clic su **[!UICONTROL Add New Block]**.
   1. Modifica la sezione del contenuto mediante Page Builder.
   1. In **[!UICONTROL Layout]** trascinare un nuovo **[!UICONTROL Row]** nell&#39;area di visualizzazione.
   1. Espandere **[!UICONTROL Media]** e trascinare un segnaposto **[!UICONTROL Image]** nella riga.
   1. Fare clic su **[!UICONTROL Select from Gallery]**.
   1. Selezionare la directory `wysiwyg` se non è selezionata per impostazione predefinita.

<u>Risultati previsti</u>:

La raccolta multimediale rimane funzionante anche se è presente un&#39;immagine a 0 byte (o qualsiasi altro file).

<u>Risultati effettivi</u>:

La raccolta multimediale non riesce a caricare immagini dalla directory `wysiwyg` a causa di un errore critico registrato in `var/log/system.log`:

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

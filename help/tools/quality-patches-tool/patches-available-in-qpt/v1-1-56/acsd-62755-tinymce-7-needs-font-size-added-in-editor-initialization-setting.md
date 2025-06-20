---
title: 'ACSD-62755: [!DNL TinyMCE] 7 è necessario aggiungere la dimensione e il tipo di carattere alle impostazioni di inizializzazione dell''editor'
description: Applica la patch ACSD-62755 per risolvere il problema di Adobe Commerce per cui [!DNL TinyMCE] 7 richiede che *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell'editor.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 richiede che le impostazioni di inizializzazione dell&#39;editor e le dimensioni e il tipo di carattere siano stati aggiunti

La patch ACSD-62755 risolve il problema per cui [!DNL TinyMCE] 7 richiede che i selettori *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell&#39;editor. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installato. L’ID della patch è ACSD-62755. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p10

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL TinyMCE] 7 richiede che i selettori *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell&#39;editor.

<u>Passaggi da riprodurre</u>:

Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** e seleziona *[!UICONTROL Show Editor]*.

<u>Risultati previsti</u>:

I selettori *Dimensione font* e *Famiglia font* sono visibili nell&#39;editor di WYSIWYG.

<u>Risultati effettivi</u>:

Il selettore *Dimensione font* non è presente nell&#39;editor di WYSIWYG.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

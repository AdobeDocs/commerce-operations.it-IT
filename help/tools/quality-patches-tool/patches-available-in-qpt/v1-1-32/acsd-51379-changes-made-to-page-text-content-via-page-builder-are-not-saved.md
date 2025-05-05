---
title: 'ACSD-51379: le modifiche al contenuto di testo della pagina tramite [!DNL Page Builder] non vengono salvate'
description: Applica la patch ACSD-51379 per risolvere il problema Adobe Commerce per cui le modifiche apportate al contenuto di testo di una pagina tramite [!DNL Page Builder] non vengono salvate.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: le modifiche al contenuto di testo della pagina tramite [!DNL Page Builder] non vengono salvate

La patch ACSD-51379 risolve il problema per cui le modifiche apportate al contenuto di testo di una pagina tramite [!DNL Page Builder] non vengono salvate. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32. L’ID della patch è ACSD-51379. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche apportate al contenuto di testo di una pagina tramite [!DNL Page Builder] non vengono salvate.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Creare una pagina di prova con una riga e un elemento di testo nella scheda **[!UICONTROL Content]**.
1. Salvare la pagina e tornare alla scheda **[!UICONTROL Content]**.
1. Modificare il testo selezionandolo e modificandolo.

   **Nota:** il problema è riproducibile solo se il testo viene selezionato e modificato senza attivare l&#39;editor.

1. Fare clic sul pulsante **[!UICONTROL Save and Close]** nella pagina di prova.
1. Aprire nuovamente la pagina di prova e selezionare la scheda **[!UICONTROL Content]**.

<u>Risultati previsti</u>:

Il nuovo testo viene salvato correttamente per gli elementi di testo originali e duplicati.

<u>Risultati effettivi</u>:

L’elemento di testo viene duplicato correttamente, ma il nuovo testo non viene salvato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

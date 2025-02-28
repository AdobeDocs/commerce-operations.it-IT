---
title: 'ACSD-64113: errore in amministratore durante il caricamento di un''immagine con larghezza inferiore all''altezza tramite [!DNL Media Gallery]'
description: Applica la patch ACSD-64113 per risolvere il problema di Adobe Commerce, in cui si verificano errori nell'amministratore durante il caricamento di immagini con una larghezza relativamente piccola rispetto alla loro altezza (o viceversa) tramite  [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
source-git-commit: b9433897d2658ecbe0b8d7f9932c15824f2ecca6
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: errore in amministratore durante il caricamento di un&#39;immagine con larghezza inferiore all&#39;altezza tramite [!DNL Media Gallery]

La patch ACSD-64113 risolve il problema relativo agli errori che si verificano nell&#39;amministratore durante il caricamento di immagini con una larghezza relativamente piccola rispetto alla loro altezza (o viceversa) tramite [!DNL Media Gallery]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-64113. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli errori si verificano nell&#39;amministratore durante il caricamento di immagini con una larghezza relativamente piccola rispetto alla loro altezza (o viceversa) tramite [!DNL Media Gallery].

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** e seleziona la directory **[!UICONTROL wysiwyg]**.
1. Carica l’immagine con una larghezza relativamente piccola rispetto alla sua altezza (o viceversa).

<u>Risultati previsti</u>:

L’immagine viene caricata senza errori.

<u>Risultati effettivi</u>:

1. Viene visualizzato il seguente messaggio di errore:

   *Un problema tecnico con il server ha creato un errore. Riprova a continuare quello che stavi facendo. Se il problema persiste, riprovare più tardi.*
1. `var/log/exception.log` contiene:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   o

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'ACP2E-3838: [!DNL Page Builder] Gli errori CORS impediscono il salvataggio delle modifiche nel pannello di amministrazione in modalità di produzione'
description: Applica la patch ACP2E-3838 per risolvere il problema Adobe Commerce, in cui [!DNL Page Builder] gli errori CORS impediscono il salvataggio delle modifiche nel pannello di amministrazione in modalità di produzione.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
source-git-commit: 1b9c721c8200f38b6ce5d1b4de87b1f10e07e8d2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACP2E-3838: [!DNL Page Builder] errori CORS impediscono il salvataggio delle modifiche nel pannello di amministrazione in modalità di produzione

La patch ACP2E-3838 risolve il problema in cui [!DNL Page Builder] errori CORS impediscono il salvataggio delle modifiche nel pannello di amministrazione in modalità di produzione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACP2E-3838. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL Page Builder] errori CORS impediscono il salvataggio delle modifiche nel pannello di amministrazione in modalità di produzione.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Fare clic su **[!UICONTROL Add New Page]** oppure selezionare una pagina CMS esistente e fare clic su **[!UICONTROL Edit]**.
1. Fare clic su **[!UICONTROL Edit with Page Builder]** per aggiungere un nuovo blocco di contenuto o modificare un blocco esistente.
1. Apportare le modifiche desiderate al contenuto, ad esempio aggiungere testo, immagini o altri elementi.
1. Fare clic sul pulsante **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Il contenuto della pagina deve essere salvato correttamente senza errori.

<u>Risultati effettivi</u>:

1. Impossibile salvare le modifiche di [!DNL Page Builder].
1. La console del browser registra gli errori relativi a CORS.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

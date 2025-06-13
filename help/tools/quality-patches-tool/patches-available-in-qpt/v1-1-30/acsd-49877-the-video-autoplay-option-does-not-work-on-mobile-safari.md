---
title: 'ACSD-49877: la riproduzione automatica video non funziona su dispositivi mobili [!DNL Safari]'
description: Applica la patch ACSD-49877 per risolvere il problema di Adobe Commerce per cui l'opzione di riproduzione automatica video non funziona su dispositivi mobili [!DNL Safari] quando il video è collegato direttamente a un file video remoto.
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877: la riproduzione automatica video non funziona sul dispositivo mobile [!DNL Safari]

L&#39;ACSD-49877 risolve il problema per cui l&#39;opzione di riproduzione automatica sul dispositivo mobile [!DNL Safari] non funziona quando il video è collegato direttamente a un file video remoto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. L’ID della patch è ACSD-49877. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto [ !magento/quality-patches] alla versione più recente e verificare la compatibilità in [[!DNL Quality Patches Tool]: Cerca patch]. Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La riproduzione automatica video non funziona sul dispositivo mobile [!DNL Safari] quando il video è collegato direttamente a un file video remoto e non a un servizio di streaming.

<u>Prerequisiti</u>:
[!DNL Page Builder] moduli sono installati.

<u>Passaggi da riprodurre</u>:

1. Creare una nuova pagina CMS e modificare **[!UICONTROL Content Value]** con [!DNL Page Builder].
1. Aggiungi un elemento *Tab* al contenuto e un elemento *Video* all&#39;interno della *Tab*.
1. Ora fai clic sul pulsante con l&#39;ingranaggio per modificare l&#39;*elemento video*.
1. Aggiungere un collegamento a un file video mp4 nel campo [!UICONTROL Video URL].
1. Contrassegna il campo **[!UICONTROL Autoplay]** come *Sì*.
1. Fare clic su **[!UICONTROL Save]**.
1. Apri la pagina creata di recente in [!DNL Safari] utilizzando un iPhone.

<u>Risultati previsti</u>

L&#39;opzione di riproduzione automatica funziona su [!DNL Safari] utilizzando un iPhone.

<u>Risultati effettivi</u>

L&#39;opzione di riproduzione automatica non funziona su [!DNL Safari] utilizzando un iPhone.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

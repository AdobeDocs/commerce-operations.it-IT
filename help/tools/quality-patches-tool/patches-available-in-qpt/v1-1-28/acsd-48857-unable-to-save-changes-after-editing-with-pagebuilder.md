---
title: 'ACSD-48857: impossibile salvare le modifiche dopo la modifica con [!DNL Page Builder]'
description: Applica la patch ACSD-48857 per risolvere il problema di Adobe Commerce che impediva all'utente di salvare le modifiche dopo la modifica con  [!DNL Page Builder].
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857: impossibile salvare le modifiche dopo la modifica con [!DNL Page Builder]

La patch ACSD-48857 risolve il problema che impediva all&#39;utente di salvare le modifiche dopo averle modificate con [!DNL Page Builder]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-48857. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente non è in grado di salvare le modifiche dopo averle modificate con [!DNL Page Builder].

<u>Passaggi da riprodurre</u>

1. Accedi al sito web dell’amministratore.
1. Passare a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** per creare una pagina CMS vuota.
1. Eseguire questo script SQL per impostare il seguente valore di campo **[!UICONTROL Content]**:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Torna a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** in Amministratore.
1. Modifica la pagina.
1. Passa alla scheda **[!UICONTROL Content]**.
1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>

È stata implementata l’eliminazione dei contenuti HTML. Rimuove gli attributi riservati di HTML [!DNL Page Builder] nei contenuti generati dall&#39;editor di testo.

<u>Risultati effettivi</u>

La pagina non viene salvata e il caricatore continua a ruotare. Nella console viene generato il seguente errore:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

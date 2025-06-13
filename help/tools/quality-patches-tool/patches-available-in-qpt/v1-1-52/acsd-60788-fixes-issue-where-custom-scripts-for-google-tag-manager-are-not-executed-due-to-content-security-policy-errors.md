---
title: 'ACSD-60788: script personalizzati per  [!DNL Google Tag Manager]  non eseguiti a causa di errori CSP'
description: Applica la patch ACSD-60788 per risolvere il problema di Adobe Commerce per cui gli script personalizzati per  [!DNL Google Tag Manager]  non vengono eseguiti a causa di errori CSP (Content Security Policy).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: gli script personalizzati per [!DNL Google Tag Manager] non vengono eseguiti a causa di errori dei criteri di sicurezza del contenuto

La patch ACSD-60788 risolve il problema che impediva l&#39;esecuzione degli script personalizzati per [!DNL Google Tag Manager] a causa di errori di Criteri di sicurezza del contenuto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-60788. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli script personalizzati per [!DNL Google Tag Manager] non vengono eseguiti a causa di errori Content Security Policy (CSP).

<u>Passaggi da riprodurre</u>:

1. Imposta la variabile *[!DNL Google Tag Manager]*.
1. Imposta il tag HTML personalizzato *[!DNL Google Tag Manager]*.
1. Inserisci il seguente codice JavaScript nel primo tag:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Svuota le cache dopo la configurazione di *GTM*.
1. Apri la Developer Console nel browser.
1. Aprire la home page.

<u>Risultati previsti</u>:

Nella console di sviluppo del browser viene visualizzato *Nonce da JS semplice (caratteri casuali)*.

<u>Risultati effettivi</u>:

Nella console di sviluppo del browser viene visualizzato *Nonce da JS semplice non definito*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

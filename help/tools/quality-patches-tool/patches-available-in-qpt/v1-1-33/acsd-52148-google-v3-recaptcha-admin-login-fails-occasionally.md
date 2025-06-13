---
title: 'ACSD-52148: l’accesso amministratore Google v3 reCAPTCHA a volte non riesce'
description: Applica la patch ACSD-52148 per risolvere il problema di Adobe Commerce, a causa del quale l’accesso amministratore Google v3 reCAPTCHA talvolta non riesce.
feature: Admin Workspace
role: Admin
exl-id: a114d39e-0aad-45c8-9e64-2b559373b228
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-52148: l’accesso amministratore Google v3 reCAPTCHA a volte non riesce

La patch ACSD-52148 risolve il problema che occasionalmente causa un errore di accesso dell’amministratore Google v3 reCAPTCHA. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-52148. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’accesso dell’amministratore reCAPTCHA di Google v3 a volte non riesce.

<u>Passaggi da riprodurre</u>:

1. Attiva Google v3 reCAPTCHA per l’accesso come amministratore.
1. Accedi ad Admin passando il captcha.

<u>Risultati previsti</u>

L&#39;amministratore ha effettuato l&#39;accesso.

<u>Risultati effettivi</u>

* *verifica reCAPTCHA non riuscita.* errore viene visualizzato occasionalmente.
* Errore registrato-

  ```
  report.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

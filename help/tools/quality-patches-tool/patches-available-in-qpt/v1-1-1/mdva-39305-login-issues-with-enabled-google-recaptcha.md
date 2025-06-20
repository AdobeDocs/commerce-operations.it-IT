---
title: 'MDVA-39305: problema di accesso con Google reCAPTCHA abilitato'
description: Applicare la patch MDVA-39305 per risolvere il problema di Adobe Commerce che impedisce ai clienti registrati di accedere quando Google reCAPTCHA è abilitato.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305: problema di accesso con Google reCAPTCHA abilitato

>[!NOTE]
>
>La patch è stata aggiornata e l&#39;ID più recente è MDVA-39305-V3. La nuova patch viene creata per Adobe Commerce versioni 2.4.4, 2.4.5-p2 e 2.4.7. Per ulteriori informazioni, fare riferimento all&#39;articolo della patch [MDVA-39305-V3](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha).

La patch MDVA-39305 risolve il problema che impediva ai clienti registrati di accedere quando Google reCAPTCHA è abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. L&#39;ID della patch è MDVA-39305. Il problema è stato risolto nelle versioni 2.4.4 e 2.4.7 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce su infrastruttura cloud 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti registrati non sono in grado di effettuare l’accesso con Google reCAPTCHA abilitato.

<u>Passaggi da riprodurre</u>:

1. Vai a **Store** > **Configurazione** > **Sicurezza** > **Google reCAPTCHA Storefront** e abilita **Google reCAPTCHA**.
1. Vai a **Frontend**.
1. Apri **Console Strumenti per sviluppatori** nel browser.

<u>Risultati previsti</u>:

Nessun avviso CSP nella console.

<u>Risultati effettivi</u>:

Avvisi CSP nella console.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

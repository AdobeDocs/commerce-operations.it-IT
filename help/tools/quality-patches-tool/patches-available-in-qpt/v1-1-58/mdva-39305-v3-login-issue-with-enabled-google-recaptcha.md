---
title: 'MDVA-39305-V3: problema di accesso con abilitato [!DNL Google reCAPTCHA]'
description: Applicare la patch MDVA-39305-V3 per risolvere il problema di Adobe Commerce che impedisce ai clienti registrati di accedere quando  [!DNL Google reCAPTCHA]  è abilitato. Questa patch risolve anche il problema relativo all'invio di un modulo prima del caricamento completo di  [!DNL Google reCAPTCHA] . Inoltre, viene corretto l’errore *Chiamata a una funzione membro isDisabled() su null* quando i blocchi vengono utilizzati in posizioni non predefinite su una pagina CMS.
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: problema di accesso con [!DNL Google reCAPTCHA] abilitato

>[!NOTE]
>
>Questa patch è un aggiornamento della patch [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md).

La patch MDVA-39305-V3 risolve il problema che impediva ai clienti registrati di accedere quando [!DNL Google reCAPTCHA] è abilitato. Questa patch risolve anche il problema relativo all&#39;invio di un modulo prima del caricamento completo di [!DNL Google reCAPTCHA]. Inoltre, viene corretto l&#39;errore *Chiamata a una funzione membro isDisabled() su null* quando i blocchi vengono utilizzati in posizioni non predefinite in una pagina CMS.

Questa patch è stata aggiunta nella versione [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. È stato aggiornato nella versione QPT 1.1.58 per includere le nuove versioni di Adobe Commerce 2.4.7 - 2.4.7-p4. L&#39;ID della patch è MDVA-39305-V3. Il problema è stato risolto nelle versioni 2.4.4, 2.4.5-p2 e 2.4.7 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.5-p2, 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problemi

### Caso I

1. I clienti registrati non sono in grado di effettuare l&#39;accesso con [!DNL Google reCAPTCHA] abilitato.
1. È possibile inviare un modulo prima del caricamento completo di [!DNL Google reCAPTCHA].

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** e abilita ***[!DNL Google reCAPTCHA]***.
1. Vai al front-end.
1. Apri **[!UICONTROL Developer Tool Console]** nel browser.

<u>Risultati previsti</u>:

Nessun avviso CSP nella console.

<u>Risultati effettivi</u>:

Avvisi CSP nella console.

### Caso II

Errore che indica che *La chiamata a una funzione membro èDisabled() su null* viene generata quando i blocchi vengono utilizzati in posizioni non predefinite in una pagina CMS.

<u>Passaggi da riprodurre</u>:

1. Crea un blocco statico con il seguente contenuto:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Aggiungere un blocco statico a una pagina di CMS da **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**.
1. Salva la pagina.

<u>Risultati previsti</u>:

La pagina viene caricata senza errori.

<u>Risultati effettivi</u>:

Sulla pagina della vetrina si verifica un errore 500.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

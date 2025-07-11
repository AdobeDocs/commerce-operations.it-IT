---
title: 'ACSD-46988: la richiesta API della valuta GraphQL restituisce valori null'
description: La patch ACSD-46988 risolve il problema per cui la richiesta API della valuta GraphQL restituisce valori Null per una valuta personalizzata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21. L’ID della patch è ACSD-46988. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988: la richiesta API della valuta GraphQL restituisce valori null

La patch ACSD-46988 risolve il problema per cui la richiesta API della valuta GraphQL restituisce valori Null per una valuta personalizzata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21. L’ID della patch è ACSD-46988. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta API per la valuta GraphQL restituisce valori Null per una valuta personalizzata.

<u>Passaggi da riprodurre</u>:

1. Configurare la valuta personalizzata in Admin. Vai a **Sistema** > **Configurazione** > **Generale** > **Impostazione valuta**.
1. Invia una richiesta GraphQL con il seguente payload:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>Risultati previsti</u>:

La richiesta restituisce valori di valuta invece di valori nulli.

<u>Risultati effettivi</u>:

La richiesta restituisce più valori Null.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Strumenti patch di qualità > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida dello strumento Patch di qualità.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Per gli utenti locali:

* Esecuzione: `composer require symfony/intl:"~5.4.11"`

Per gli utenti di Cloud:

* Esecuzione: `composer require symfony/intl:"~5.4.11"`
* Invia `composer.json` e `composer.lock` file all&#39;archivio Git insieme al file patch.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida dello strumento Patch di qualità.

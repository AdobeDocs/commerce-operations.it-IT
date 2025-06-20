---
title: 'ACSD-60816: [!DNL New Relic] gli script di monitoraggio del browser inseriti dall''agente APM non sono conformi a CSP'
description: Applica la patch ACSD-60816 per risolvere il problema Adobe Commerce per cui gli script di monitoraggio del browser  [!DNL New Relic]  inseriti dall'agente APM non sono conformi ai criteri sulla sicurezza dei contenuti (CSP), impedendone l'esecuzione.
feature: Tools and External Services, Checkout
role: Admin, Developer
exl-id: d03c25e0-ed25-4877-8470-737d3499473f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-60816: gli script di monitoraggio del browser [!DNL New Relic] inseriti dall&#39;agente APM non sono conformi ai CSP

La patch ACSD-60816 risolve il problema per cui gli script di monitoraggio del browser [!DNL New Relic] inseriti dall&#39;agente APM non sono conformi ai criteri CSP (Content Security Policy). Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-60816. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL New Relic] gli script di monitoraggio del browser inseriti dall&#39;agente APM non sono conformi ai CSP.

<u>Passaggi da riprodurre</u>:

1. Aggiungi il prodotto al carrello.
1. Vai al pagamento.

<u>Risultati previsti</u>:

Nessun errore CSP nella console per sviluppatori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

```
Content-Security-Policy: The page's settings blocked an inline script (script-src-elem) from being executed because it violates the following directive: "script-src 
...
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

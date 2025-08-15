---
title: 'ACSD-65127: la minimizzazione del JavaScript in modalità di produzione causa  [!DNL TinyMCE] 6 errori nel browser'
description: Applica la patch ACSD-65127 per risolvere il problema di Adobe Commerce, a causa del quale l'attivazione della minimizzazione di JavaScript in modalità di produzione  [!DNL TinyMCE] 6 ha generato errori nella console del browser, influendo sulla funzionalità e sull'esperienza utente.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127: la minimizzazione del JavaScript in modalità di produzione causa [!DNL TinyMCE] 6 errori nel browser

La patch ACSD-65127 risolve il problema che causava la generazione di errori nella console del browser da parte di [!DNL TinyMCE] 6 a causa dell&#39;abilitazione della minimizzazione di JavaScript in modalità di produzione, con conseguente impatto sulla funzionalità e sull&#39;esperienza utente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65127. Questo problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;attivazione della minimizzazione di JavaScript in modalità di produzione ha causato la generazione di errori da parte di [!DNL TinyMCE] 6 nella console del browser, che hanno influito sulla funzionalità e sull&#39;esperienza utente.

<u>Passaggi da riprodurre</u>:

1. Imposta la configurazione eseguendo i seguenti comandi:

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Abilita la modalità di produzione.

```
bin/magento deploy:mode:set production
```

1. Nella barra laterale di amministrazione, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Fai clic su **[!UICONTROL Edit]** per uno dei prodotti elencati, scorri verso il basso fino a **[!UICONTROL Content]** e seleziona **[!UICONTROL Show Editor]**.

<u>Risultati previsti</u>:

Nessun errore JS nella console del browser.

<u>Risultati effettivi</u>:

*404* errori nella console del browser per js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

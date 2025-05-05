---
title: 'ACSD-61534: la configurazione del progetto non può essere impostata utilizzando bin/magento config:set e i valori bloccati possono essere modificati tramite la manipolazione del modulo'
description: Applica la patch ACSD-61534 per risolvere il problema di Adobe Commerce, in cui la configurazione del progetto non può essere impostata utilizzando il comando "bin/magento config:set", e i valori bloccati possono essere modificati tramite la manipolazione del modulo.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
source-git-commit: bbf7df7fdca4c11f6f268344db00e2c8643b5dce
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: impossibile impostare la configurazione della progettazione utilizzando `bin/magento config:set`. I valori bloccati possono essere modificati tramite la manipolazione del modulo

La patch ACSD-61534 risolve il problema che impediva di impostare la configurazione della progettazione con il comando `bin/magento config:set` e di modificare i valori bloccati tramite la manipolazione del modulo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-61534. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile impostare la configurazione della progettazione utilizzando il comando `bin/magento config:set`. I valori bloccati possono essere modificati tramite la modifica del modulo. Con questa patch non è possibile aggiornare i valori bloccati impostati dallo strumento da riga di comando (CLI) con `--lock-env` o `--lock-conf`.

<u>Passaggi da riprodurre</u>:

1. Blocca un valore di configurazione utilizzando una variabile di ambiente cloud, ad esempio `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Passa al pannello *[!UICONTROL Admin]*.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Fare clic su **[!UICONTROL Edit]** accanto a **[!UICONTROL Global/Main website]** nella seconda riga.
1. Modificare il tema per una visualizzazione store.
1. Apri la testina del HTML.
1. Abilita il campo **[!UICONTROL Scripts and Style Sheets]** disabilitato utilizzando gli strumenti per sviluppatori.
1. Modifica il valore e salvalo.

<u>Risultati previsti</u>:

Impossibile salvare un valore bloccato.

<u>Risultati effettivi</u>:

La tabella `core_config_data` contiene un valore aggiornato per `design/head/includes`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

---
title: 'MDVA-42509: impossibile caricare il file CSV per l’ordine rapido. Errore "Impossibile inviare il cookie"'
description: La patch MDVA-42509 risolve il problema che impediva il caricamento di un file CSV per l'ordine rapido, causando l'errore *Impossibile inviare il cookie*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16. L'ID della patch è MDVA-42509. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: impossibile caricare il file CSV per l’ordine rapido. Errore &quot;Impossibile inviare il cookie&quot;

La patch MDVA-42509 risolve il problema che impediva il caricamento di un file CSV per l&#39;ordine rapido, causando l&#39;errore *Impossibile inviare il cookie*. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16. L&#39;ID della patch è MDVA-42509. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se si crea un ordine rapido con un numero elevato di prodotti utilizzando un file CSV, viene visualizzato un errore di cookie: *Impossibile inviare il cookie*

<u>Passaggi da riprodurre</u>:

1. Abilita Ordine rapido passando a **Archivi** > **Impostazioni** > **Configurazioni** > **Generale** > **Caratteristiche B2B**.
1. Crea un account cliente e passa a **Ordine rapido** dal collegamento superiore.
1. Prova a creare un ordine rapido utilizzando un file CSV con più di 100 SKU.

<u>Risultati previsti</u>:

Puoi creare un ordine rapido con un numero elevato di SKU.

<u>Risultati effettivi</u>:

Viene visualizzato un messaggio di errore relativo alla dimensione del cookie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

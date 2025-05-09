---
title: 'ACSD-63406: le virgolette persistenti scadute non vengono cancellate quando viene eseguito il processo cron persistent_clear_expired'
description: Applica la patch ACSD-63406 per risolvere il problema di Adobe Commerce, in cui le virgolette persistenti scadute non vengono cancellate da alcun processo cron quando viene eseguito il processo cron "persistent_clear_expiry".
feature: Quotes, Shopping Cart
role: Admin, Developer
source-git-commit: b3bb6ae825f4912b19e2d1f88b5d55835d9769ff
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACSD-63406: le virgolette persistenti scadute non vengono cancellate durante l&#39;esecuzione del processo cron `persistent_clear_expired`

La patch ACSD-63406 risolve il problema se le virgolette persistenti scadute non vengono cancellate da alcun processo cron durante l&#39;esecuzione del processo cron `persistent_clear_expired`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. L’ID della patch è ACSD-63406. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le virgolette persistenti scadute non vengono cancellate da alcun processo cron durante l&#39;esecuzione del processo cron `persistent_clear_expired`.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria e un prodotto.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Imposta tutte le opzioni su *Sì*.
   1. Imposta **[!UICONTROL Persistence Lifetime (seconds)]** su *60*.
1. Crea un account cliente nella vetrina e accedi.
1. Aggiungi un prodotto al carrello.
1. Esci, attendi 60 secondi e accedi di nuovo.

<u>Risultati previsti</u>:

Il processo cron `persistent_clear_expired` deve eliminare le virgolette persistenti in base alle impostazioni della durata di persistenza nella configurazione.

<u>Risultati effettivi</u>:

Il valore `is_persistent` per l&#39;offerta cliente rimane *1* nella tabella delle offerte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

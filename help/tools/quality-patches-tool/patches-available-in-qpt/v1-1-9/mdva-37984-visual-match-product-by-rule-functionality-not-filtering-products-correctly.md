---
title: 'MDVA-37984: Visual Merchandiser non funziona correttamente quando vengono applicati aggiornamenti di staging'
description: La patch MDVA-37984 risolve il problema per cui la funzionalità "Match product by rule" di Visual Merchandiser non filtra correttamente i prodotti quando vengono applicati aggiornamenti di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-37984. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser non funziona correttamente quando vengono applicati aggiornamenti di staging

La patch MDVA-37984 risolve il problema per cui la funzionalità &quot;Match product by rule&quot; di Visual Merchandiser non filtra correttamente i prodotti quando vengono applicati aggiornamenti di staging. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. L&#39;ID della patch è MDVA-37984. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La funzionalità &quot;Match product by rule&quot; di Visual Merchandiser non filtra correttamente i prodotti quando vengono applicati aggiornamenti di staging.

<u>Passaggi da riprodurre</u>:

1. Crea un aggiornamento della pianificazione per qualsiasi prodotto esistente.
   * Impostare valori diversi per `entity_id` e `row_id`.
1. Creare un nuovo prodotto configurabile e quindi un prodotto semplice (quindi anche i nuovi prodotti `entity_id` e `row_ids` sono diversi).
   * Per semplificare la replica del problema, impostare un valore di quantità distinguibile per il prodotto semplice, ad esempio 5000.
1. Vai a una categoria > **Prodotti nella categoria** e abilita **Corrispondenza prodotti per regola**.
1. Selezionare &quot;Quantità&quot; come attributo, &quot;Maggiore&quot; come operatore e &quot;4500&quot; come valore.
1. Fai clic su **salva**.

<u>Risultati previsti</u>:

Viene elencato il prodotto configurabile appena creato.

<u>Risultati effettivi</u>:

Il prodotto configurabile appena creato non è elencato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

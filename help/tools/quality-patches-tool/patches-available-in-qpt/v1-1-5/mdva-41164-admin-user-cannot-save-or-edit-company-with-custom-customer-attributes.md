---
title: 'MDVA-41164: impossibile salvare o modificare la società con attributi cliente personalizzati'
description: La patch MDVA-41164 risolve il problema che impediva all'utente amministratore di salvare o modificare un'azienda con attributi cliente personalizzati di file o immagini di qualsiasi tipo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. L'ID della patch è MDVA-41164. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: impossibile salvare o modificare la società con attributi cliente personalizzati

La patch MDVA-41164 risolve il problema che impediva all&#39;utente amministratore di salvare o modificare un&#39;azienda con attributi cliente personalizzati di file o immagini di qualsiasi tipo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. L&#39;ID della patch è MDVA-41164. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non è in grado di salvare o modificare un’azienda con attributi cliente personalizzati di file o immagini di alcun tipo.

<u>Prerequisiti</u>:

Il modulo B2B è installato.

<u>Passaggi da riprodurre</u>:

1. Abilita la società in **Archivi** > **Configurazione** > **Funzionalità B2B**.
1. Crea un attributo cliente in **Archivi** > **Attributi** > **Clienti** > **Aggiungi nuovo attributo**:
   * Tipo di input: File (allegato)
   * Mostra in vetrina: sì
   * Ordinamento: qualsiasi
   * Forms da usare in: Seleziona tutto
1. Crea una nuova società in **Clienti** > **Società** > **Aggiungi nuova società** e carica un file per il nuovo attributo creato in precedenza.

<u>Risultati previsti</u>:

L’utente è in grado di completare la creazione dell’azienda e l’allegato viene caricato senza errori.

<u>Risultati effettivi</u>:

* Viene visualizzato un messaggio di errore: *Si è verificato un errore durante il salvataggio del file.*
* Il registro eccezioni contiene un record simile al seguente:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

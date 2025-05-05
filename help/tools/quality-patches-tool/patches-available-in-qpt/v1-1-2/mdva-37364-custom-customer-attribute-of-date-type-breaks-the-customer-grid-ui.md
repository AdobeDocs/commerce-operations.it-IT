---
title: 'MDVA-37364: l''attributo cliente personalizzato del tipo di data interrompe l''interfaccia utente della griglia'
description: La patch MDVA-37364 risolve il problema relativo all'interruzione dell'interfaccia utente di Customer Grid da parte dell'attributo cliente personalizzato del tipo di data. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-37364. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364: l&#39;attributo cliente personalizzato del tipo di data interrompe l&#39;interfaccia utente della griglia

La patch MDVA-37364 risolve il problema relativo all&#39;interruzione dell&#39;interfaccia utente di Customer Grid da parte dell&#39;attributo cliente personalizzato del tipo di data. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-37364. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0-2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’attributo cliente personalizzato del tipo di data interrompe l’interfaccia utente della griglia clienti.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo personalizzato con tipo di data:
   * Vai a **Archivi** > **Attributi** > **Aggiungi attributo**.
   * Impostare il tipo di input su Data.
   * Impostare Aggiungi a opzioni colonna su Sì.
   * Salva l’attributo.
1. Vai a **Amministratore** > **Clienti** > **Tutti i clienti**.
   * Aggiungi l’attributo personalizzato appena aggiunto alla griglia dall’opzione Colonne.
1. Crea/Modifica un cliente e imposta il valore del campo attributo data personalizzato creato.
1. Salvare, reindicizzare e cancellare la cache.
1. Vai a **Clienti** > **Tutti i clienti**.
   * Controlla la griglia clienti.

<u>Risultati previsti</u>:

La griglia clienti amministratore mostra tutti i dati, incluso il nuovo attributo personalizzato di data, senza interrompere l’interfaccia utente della griglia clienti.

<u>Risultati effettivi</u>:

L’interfaccia utente di Admin Customer Grid non funziona correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento Quality Patches: è stato introdotto un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).

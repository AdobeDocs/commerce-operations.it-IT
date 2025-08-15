---
title: 'MDVA-44940: errore SQL durante il salvataggio della categoria dall''amministratore'
description: La patch MDVA-44940 risolve il problema che si verifica in caso di errore SQL durante il salvataggio di una categoria dall'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L'ID della patch è MDVA-44940. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940: errore SQL durante il salvataggio della categoria dall&#39;amministratore

La patch MDVA-44940 risolve il problema che si verifica in caso di errore SQL durante il salvataggio di una categoria dall&#39;amministratore. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L&#39;ID della patch è MDVA-44940. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore SQL durante il salvataggio di una categoria dall’amministratore.

<u>Passaggi da riprodurre</u>:

1. Installa i dati di esempio.
1. Crea un secondo sito Web con un gruppo di punti vendita assegnato alla categoria predefinita.

   * Crea una visualizzazione dello store assegnata al nuovo gruppo di store.

1. Crea le scorte e un&#39;origine aggiuntiva assegnata a queste scorte e a un canale di vendita assegnato al secondo sito Web.
1. Crea un prodotto di test assegnato al secondo sito Web.
1. Vai a **Amministratore** > **Catalogo** > **Categorie**, seleziona **Ambito** = **Secondo sito Web** e vai a **Prodotti nella categoria** > **Ordinamento automatico** > Sposta prodotti esauriti in basso e fai clic su **Salva**.

<u>Risultati previsti</u>:

La categoria viene salvata.

<u>Risultati effettivi</u>:

Si è verificato il seguente errore: *Si è verificato un errore durante il salvataggio della categoria*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

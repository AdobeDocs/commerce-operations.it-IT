---
title: 'MDVA-42657: impossibile selezionare le categorie nelle condizioni del segmento cliente'
description: La patch MDVA-42657 risolve il problema che impediva all'utente amministratore di selezionare le categorie nelle condizioni del segmento cliente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-42657. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: impossibile selezionare le categorie nelle condizioni del segmento cliente

La patch MDVA-42657 risolve il problema che impediva all&#39;utente amministratore di selezionare le categorie nelle condizioni del segmento cliente. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L&#39;ID della patch è MDVA-42657. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non è in grado di selezionare le categorie nelle condizioni del segmento cliente.

<u>Passaggi da riprodurre</u>:

1. Vai a **Clienti** > **Segmenti**.
1. Crea un nuovo segmento.
1. Vai al segmento appena creato e fai clic su **Condizioni** nella navigazione a sinistra.
1. Fare clic sul segno più verde.
1. Seleziona Cronologia prodotto in Prodotti.
1. Cambia &quot;visualizzato&quot; in &quot;ordinato&quot;.
1. Modificare &quot;ALL&quot; in &quot;ANY&quot;.
1. Fai clic sul segno più verde nidificato e seleziona Categoria.
1. Fare clic sul segno **...** e quindi sull&#39;icona del selettore (a sinistra del segno di spunta).
1. Apri la console di sviluppo del browser.
1. Seleziona le caselle di controllo per una o più categorie e annota l’errore JavaScript generato nella console.
1. Fai clic sul pulsante **Salva**.
1. Torna alla condizione e controlla se le categorie selezionate sono salvate.

<u>Risultati previsti</u>:

Le categorie selezionate vengono salvate e selezionate durante la visualizzazione o la modifica delle condizioni del segmento.

<u>Risultati effettivi</u>:

Le categorie selezionate risultano mancanti e non sono state salvate correttamente. Nella console viene visualizzato il seguente errore:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

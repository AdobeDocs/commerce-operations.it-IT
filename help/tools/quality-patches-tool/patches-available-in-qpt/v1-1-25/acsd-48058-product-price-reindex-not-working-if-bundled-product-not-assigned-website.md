---
title: 'ACSD-48058: la reindicizzazione del prezzo del prodotto non funziona se il prodotto in bundle non è stato assegnato al sito web'
description: Applica la patch ACSD-48058 per risolvere il problema di Adobe Commerce in cui la reindicizzazione del prezzo del prodotto non funziona se il prodotto incluso non è assegnato ad alcun sito Web.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 270e1b5d-75e0-4374-973a-2bb37161ceec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058: la reindicizzazione del prezzo del prodotto non funziona se il prodotto in bundle non è stato assegnato al sito web

La patch ACSD-48058 risolve il problema che causa il mancato funzionamento della reindicizzazione del prezzo del prodotto se il prodotto incluso non è assegnato ad alcun sito Web. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-48058. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione dei prezzi del prodotto non funziona se il prodotto nel pacchetto non è assegnato ad alcun sito Web.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Adobe Commerce > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crea un nuovo prodotto in bundle o modifica un prodotto in bundle esistente.
   * Fare clic sulla scheda **[!UICONTROL Product in Websites]** e deselezionare tutte le caselle di controllo (siti Web)
   * Salvare il prodotto
1. Eseguire la reindicizzazione.

<u>Risultati previsti</u>:

Reindicizzazione eseguita correttamente.

<u>Risultati effettivi</u>:

Durante l’esecuzione dell’indice dei prezzi del prodotto viene generato il seguente errore:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].

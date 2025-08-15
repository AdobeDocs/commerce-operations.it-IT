---
title: 'ACSD-53583: miglioramento delle prestazioni di reindicizzazione parziale per gli indicizzatori [!UICONTROL Category Products] e [!UICONTROL Product Categories]'
description: Applicare la patch ACSD-53585 per migliorare le prestazioni di reindicizzazione parziale per gli indici Categoria prodotti e Categoria prodotti.
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-53583: Migliorare le prestazioni di reindicizzazione parziale per gli indicizzatori di categorie e prodotti

La patch ACSD-53583 migliora le prestazioni di reindicizzazione parziale degli indicizzatori *Category Products* e *Product Categories*. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-53583. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3
* Non compatibile con il modulo [!DNL Live Search]. Per applicare questa patch all&#39;installazione di [!DNL Live Search], richiedere una patch ACSD-55719 aggiuntiva.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione parziale richiede più tempo della reindicizzazione completa.

<u>Passaggi da riprodurre</u>:

1. Imposta tutti gli indicizzatori su *Aggiorna secondo pianificazione*.
1. Genera dati con [!DNL Performance Toolkit] (profilo medio).
1. Apporta modifiche a tutti i prodotti e a tutte le categorie in modo che si trovino nel backlog dell’indice e che tutti gli indici siano inattivi.
1. Eseguire la reindicizzazione parziale per *Prodotti categoria* e *Indicizzatori categorie prodotto*.

<u>Risultati previsti</u>:

La reindicizzazione parziale viene chiamata una volta per prodotto e richiede quasi lo stesso tempo della reindicizzazione completa, perché tutti i prodotti e le categorie sono stati modificati.

<u>Risultati effettivi</u>:

La reindicizzazione parziale viene chiamata molte volte per prodotto e richiede più tempo della reindicizzazione completa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].

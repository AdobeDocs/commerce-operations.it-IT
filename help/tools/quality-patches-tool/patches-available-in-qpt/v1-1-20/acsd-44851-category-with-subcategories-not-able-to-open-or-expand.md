---
title: "ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere"
description: Questo articolo fornisce una soluzione al problema che impedisce all’utente di aprire o espandere una categoria con sottocategorie.
feature: Categories
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere

La patch ACSD-44851 risolve il problema se l’utente non è in grado di aprire o espandere una categoria con sottocategorie. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20. L’ID della patch è ACSD-44851. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente non è in grado di aprire o espandere una categoria con sottocategorie.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, crea una struttura ad albero con due categorie principali e alcune sottocategorie per ciascuna.
1. Apri la visualizzazione/emulatore mobile o riduci la larghezza della finestra finché il layout non diventa mobile.
1. Apri il menu principale del catalogo.
1. Prova ad espandere le categorie principali.
1. Prova ad aprire la categoria.

<u>Risultati previsti</u>:

Il menu è accessibile.

<u>Risultati effettivi</u>:

Il secondo livello del menu mobile non si apre.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Strumenti patch di qualità > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida dello strumento Patch di qualità.

* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida dello strumento Patch di qualità.
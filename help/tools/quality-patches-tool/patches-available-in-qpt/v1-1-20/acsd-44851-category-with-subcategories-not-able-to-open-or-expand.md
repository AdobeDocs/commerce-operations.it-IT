---
title: 'ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere'
description: Questo articolo fornisce una soluzione al problema che impedisce all’utente di aprire o espandere una categoria con sottocategorie.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere

La patch ACSD-44851 risolve il problema se l’utente non è in grado di aprire o espandere una categoria con sottocategorie. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. L’ID della patch è ACSD-44851. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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

* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

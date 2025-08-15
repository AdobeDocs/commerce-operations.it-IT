---
title: 'ACP2E-3753: memorizza le e-mail di avviso che non utilizzano modelli di tema specifici per lo store in una configurazione multi-store'
description: Applica la patch ACP2E-3753 per risolvere il problema Adobe Commerce, in cui le e-mail di avviso del prodotto in una configurazione multi-store vengono sempre inviate utilizzando il tema predefinito, indipendentemente dalla configurazione dello store o del tema.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 2089fed83a207f9d0211273652ea320d2590f8d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACP2E-3753: memorizza le e-mail di avviso che non utilizzano modelli di tema specifici per lo store in una configurazione multi-store

La patch ACP2E-3753 risolve il problema per cui le e-mail di avviso sul prodotto in una configurazione multi-store venivano sempre inviate utilizzando il tema predefinito, indipendentemente dalla configurazione dello store o del tema. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACP2E-3753. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p11

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di avviso sui prodotti in una configurazione con più store vengono sempre inviate utilizzando il tema predefinito, indipendentemente dalla configurazione dello store o del tema.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web, store e visualizzazioni dello store.
1. Crea due temi separati e assegnali a negozi diversi.
1. L’impostazione predefinita per gli avvisi sui prodotti è l’ambito che viene eseguito ogni minuto.
1. Ignora/aggiungi parte del contenuto al file `stock.phtml` per entrambi i temi. Esempio di posizione del file:

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Crea un utente per ogni negozio e abbonati all’avviso sulle scorte dei prodotti.
1. Attiva l’avviso sulle scorte di prodotto per inviare le e-mail.

<u>Risultati previsti</u>:

L’e-mail deve includere le modifiche a livello di tema.

<u>Risultati effettivi</u>:

Le e-mail non includono i modelli impostati nel rispettivo sito web/store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

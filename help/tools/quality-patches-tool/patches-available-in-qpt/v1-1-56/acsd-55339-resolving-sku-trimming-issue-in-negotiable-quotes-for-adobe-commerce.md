---
title: 'ACSD-55339: risoluzione del problema di trimming SKU in preventivi negoziabili per Adobe Commerce'
description: Applica la patch ACSD-55339 per risolvere il problema Adobe Commerce, che comporta il taglio degli SKU dei prodotti con zeri iniziali e la conseguente generazione di errori di negoziazione.
feature: B2B, Quotes
role: Admin, Developer
source-git-commit: 5153eadfe0d90c256bf6d294fcebb1dd8c0a7093
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: risoluzione del problema di trimming SKU in preventivi negoziabili per Adobe Commerce

La patch ACSD-55339 risolve il problema relativo al taglio degli SKU dei prodotti con zeri iniziali, causando errori durante il processo di negoziazione. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.56. L’ID della patch è ACSD-55339. Il problema è pianificato per essere risolto in Adobe Commerce B2B 1.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli SKU di prodotti numerici con zeri iniziali vengono tagliati quando vengono utilizzati nei preventivi negoziabili, causando errori che impediscono l&#39;aggiornamento delle quantità o l&#39;impostazione dei prezzi.

<u>Passaggi da riprodurre</u>:

1. Passa alla sezione di creazione del prodotto nel pannello di amministrazione.
1. Imposta [!UICONTROL SKU] per il prodotto come 01910.
1. Accedi alla vetrina ed esegui le operazioni seguenti:
   1. Aggiungi il prodotto al carrello.
   1. Visualizza e modifica il carrello.
   1. Richiedi un preventivo.
1. Vai a [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] e [!UICONTROL Add Products by SKU] - 01910.

**Nota:** lo SKU viene visualizzato come *1910* invece di *01910*. Questa discrepanza impedisce all&#39;utente di aggiornare la quantità o impostare i prezzi, in quanto nel catalogo non esiste alcun prodotto con lo SKU 1910.

<u>Risultati previsti</u>:

Il preventivo negoziabile deve essere aggiornato senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato un messaggio di avviso che indica che il prodotto non esiste.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

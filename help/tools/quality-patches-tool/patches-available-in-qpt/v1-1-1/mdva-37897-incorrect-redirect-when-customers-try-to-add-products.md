---
title: 'MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente'
description: La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. L'ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: reindirizzamento non corretto quando si aggiungono prodotti visualizzati di recente

La patch MDVA-37897 risolve il problema del reindirizzamento errato quando gli utenti tentano di aggiungere prodotti con opzioni del widget Visualizzato di recente. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. L&#39;ID della patch è MDVA-37897. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sulla nostra infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando un utente tenta di aggiungere un prodotto dalla sezione Visualizzato di recente in cui è necessario selezionare alcune opzioni, viene reindirizzato alla pagina dell’elenco dei prodotti anziché alla pagina dei dettagli del prodotto.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con opzioni personalizzabili (Tipo: Pulsante di scelta).
1. Configura il widget Visualizzato di recente per mostrare i prodotti.
1. Visita i prodotti con opzioni personalizzabili in modo che vengano visualizzati nel widget Visualizzato di recente.
1. Fai clic su **Aggiungi al carrello** su uno dei prodotti nel widget Visualizzato di recente.

<u>Risultati previsti</u>:

Ti reindirizzano alla pagina dei dettagli del prodotto per scegliere le opzioni.

<u>Risultati effettivi</u>:

Ti reindirizzano alla pagina dell’elenco dei prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sulla nostra infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).

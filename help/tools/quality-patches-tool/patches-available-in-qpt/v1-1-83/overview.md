---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.83.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 58221418f5aca814cda2d72a1cd83099bbb53a0c
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.83

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.83.

QPT v1.1.83 include le seguenti patch:

1. **AC-17975**: sono stati risolti diversi problemi di compatibilità PHP 8.5 che interessano i flussi di lavoro di amministrazione, l&#39;autenticazione di checkout, l&#39;elaborazione CAPTCHA, la gestione delle categorie, le pagine di configurazione e le operazioni della riga di comando in alcuni ambienti PHP.
1. **AC-18128**: è stato risolto il problema che causava la visualizzazione di date di calendario non corrette nelle impostazioni internazionali non inglesi da parte di date di ordini e timestamp di commenti di ordini restituiti da GraphQL.
1. **AC-18096**: è stato risolto il problema che causava la restituzione delle date in un formato diverso da quello delle versioni precedenti da parte dei campi di tipo Vendite GraphQL, con il ripristino del formato di data da separato da barre (`/`) a separato da trattini (`-`).
1. **ACP2E-4639**: è stato risolto il problema relativo all&#39;errata ortografia del tipo di elementi dell&#39;elenco richieste nello schema di GraphQL, mentre il campo degli elementi meno recenti e il tipo `RequistionListItems` rimangono disponibili ma sono obsoleti.
1. **ACP2E-4838**: è stato risolto il problema che impediva a un utente amministratore con autorizzazioni limitate di eliminare clienti dalla griglia Clienti.
1. **ACP2E-4877**: è stato risolto il problema che impediva la modifica degli ordini effettuati con **[!UICONTROL Payment on Account]** in Admin mentre si trovava nello stato *Pending*.
1. **ACP2E-4908**: è stato risolto il problema che causava un eccessivo utilizzo di memoria da parte di cataloghi di grandi dimensioni in Redis o Valkey, poiché venivano create voci cache di layout separate per ogni prodotto in ogni visualizzazione dello store.
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)**: è stato corretto il problema che si verificava quando riordinando un ordine nell&#39;amministratore si creava un nuovo numero di ordine con un suffisso `-1` invece di assegnare il numero di ordine sequenziale successivo.
1. **ACP2E-4977**: è stato risolto il problema per cui i totali complessivi delle fatture e delle note di accredito per i prodotti configurabili non includono **[!UICONTROL Fixed Product Tax]** (FPT), con conseguente totale inferiore al totale dell&#39;ordine.
1. **AC-16530**: è stato risolto il problema che impediva al carrello di riflettere in modo coerente gli aggiornamenti pianificati alle regole dei prezzi del catalogo.
1. **AC-11389**: risolve il problema relativo al calcolo errato di sconti, imposte e totali ordini in alcuni scenari di arrotondamento.
1. **ACP2E-4998**: è stato risolto il problema che impediva l&#39;aggiornamento degli SKU validi a causa della mancata riuscita della richiesta REST API `POST /V1/products/tier-prices` per l&#39;intera richiesta.
1. **ACP2E-5015**: è stato risolto il problema che consentiva di rimuovere accidentalmente i prodotti e i prezzi assegnati quando i dati del catalogo richiesti non erano disponibili durante il salvataggio di un catalogo condiviso nell&#39;amministratore.
1. **AC-14940**: è stato risolto il problema che impediva l&#39;invio dell&#39;e-mail di reimpostazione della password in alcuni casi correlati allo store facendo clic su **[!UICONTROL Reset Password]** per un account cliente nell&#39;amministratore.
1. **ACP2E-5101**: è stato risolto il problema che impediva l&#39;installazione del modulo B2B se gli indicizzatori erano impostati su **[!UICONTROL Update on Schedule]**.
1. **ACP2E-5205**: risolve il problema quando il caricamento della categoria richiede molto tempo o causa un timeout quando sono coinvolte numerose categorie e prodotti. Inoltre, il conteggio dei prodotti viene ora visualizzato correttamente per ogni foglia di categoria.
1. **ACP2E-3211**: è stato risolto il problema per cui l&#39;aggiunta dello stesso prodotto al carrello contemporaneamente nella vetrina crea elementi separati nel carrello per lo stesso SKU anziché combinarli in un singolo elemento.
1. **ACP2E-5223**: è stato risolto il problema per cui l&#39;indice delle autorizzazioni del catalogo include siti Web esclusi da un gruppo di clienti.

Utilizza il menu a sinistra per passare a una pagina patch specifica.

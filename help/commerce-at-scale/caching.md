---
title: Pianificazione cache effettiva
description: Fai riferimento ai benchmark consigliati per la memorizzazione in cache per garantire il successo del sito sotto carico.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Pianificazione della memorizzazione efficace nella cache per il successo dell’e-commerce in fase di caricamento

Per fornire un’esperienza di acquisto sotto carico sarà necessaria una strategia di caching ben pianificata. Anche se inizialmente le parti interessate possono chiedere di presentare sempre ai clienti i dati dei prodotti in tempo reale, non si tratta di un utilizzo ottimale delle risorse di sistema e l’impatto delle prestazioni del sito dell’utente finale supererebbe di gran lunga i vantaggi di una visualizzazione coerente delle informazioni in tempo reale.

La fase iniziale della strategia di caching dovrebbe pertanto consistere nel definire con le parti interessate una matrice di tempi di caching accettabili per le diverse aree del sito, ad esempio:

| Area di memorizzazione in cache | Quanto spesso cambia? | Impatto se il contenuto non aggiornato viene distribuito dalla cache | Time-to-live (TTL) di caching accettabile? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pagine HTML del contenuto del sito, aggiornate tramite CMS | Raramente | Basso | 1 giorno |
| Media/risorse modello di contenuto del sito - logo, progettazione CSS, immagini | Raramente | Basso | 1 settimana |
| Pagine di elenco prodotti (PLP) | Raramente | Medium | 1 giorno |
| Pagina dettagli prodotto (PDP) | A volte | Medium | 1 ora |
| Categorie di prodotti | Raramente | Medium | 1 giorno |
| Prezzi | Frequentemente | Alta | Nessuna cache |
| Magazzino/scorte | Frequentemente | Alta | Nessuna cache |
| Ricerca nel sito | Più utenti univoci | Medium | Memorizza nella cache i risultati delle prime 100 frasi di ricerca per 1 giorno |
| Pagamento | Ogni utente univoco | Molto alta | Nessuna cache |
| Carrello | Ogni utente univoco | Molto alta | Nessuna cache |
| Pagine di pagamento | Ogni utente univoco | Molto alta | Nessuna cache |

Una volta completata la pianificazione iniziale, la configurazione tecnica può iniziare a essere implementata per configurare le cache in base a questi requisiti.

Anche se il contenuto viene aggiornato e deve essere reso attivo nella cache TTL, nella maggior parte dei casi è possibile cancellare manualmente le cache per il dispatcher [AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) e la cache [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) in modo selettivo per tale contenuto, il che significa che le modifiche urgenti verranno applicate immediatamente. Il processo di cancellazione manuale della cache deve essere pianificato e testato in anticipo in modo che, se è necessario forzare manualmente un aggiornamento su alcuni contenuti, venga documentato in un runbook per le operazioni del sito e sia chiaro come e chi deve essere coinvolto in questa azione.

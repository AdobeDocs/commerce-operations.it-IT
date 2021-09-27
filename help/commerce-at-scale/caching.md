---
title: Pianificazione effettiva della cache
description: Fai riferimento ai benchmark consigliati per la memorizzazione in cache per garantire il successo del sito sotto carico.
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# Pianificazione della memorizzazione in cache effettiva per il successo di e-commerce in fase di caricamento

Per ottenere un’esperienza di acquisto al di sotto del carico sarà necessaria una strategia di caching pianificata in anticipo. Inizialmente, la richiesta da parte delle parti interessate aziendali potrebbe consistere nel presentare sempre ai clienti i dati sui prodotti in tempo reale, ma questo non è un utilizzo ottimale delle risorse di sistema, e gli impatti delle prestazioni del sito dell&#39;utente finale supererebbero notevolmente i vantaggi di mostrare in modo coerente le informazioni in tempo reale.

La fase iniziale della strategia di caching dovrebbe pertanto consistere nel definire con le parti interessate una matrice di tempi di memorizzazione in cache accettabili per le diverse aree del sito, ad esempio:

| Area di memorizzazione nella cache | Quanto spesso cambia? | Impatto se il contenuto non aggiornato viene servito dalla cache | Memorizzazione in cache accettabile time-to-live (TTL)? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Pagine HTML del contenuto del sito, aggiornate tramite CMS | Molto spesso | Basso | 1 giorno |
| Contenuto del sito modello media/risorse - logo, progettazione CSS, immagini | Molto spesso | Basso | 1 settimana |
| Pagine per l’elenco dei prodotti (PLP) | Molto spesso | Media | 1 giorno |
| Pagina dei dettagli del prodotto (PDP) | A volte | Media | 1 ora |
| Categorie di prodotti | Molto spesso | Media | 1 giorno |
| Prezzi | Frequentemente | Alta | Nessuna cache |
| Inventario/magazzino | Frequentemente | Alta | Nessuna cache |
| Ricerca nel sito | La maggior parte degli utenti univoci | Media | Risultati della cache dalle prime 100 frasi di ricerca per 1 giorno |
| Pagamento | Ogni utente univoco | Molto alto | Nessuna cache |
| Carrello | Ogni utente univoco | Molto alto | Nessuna cache |
| Pagine | Ogni utente univoco | Molto alto | Nessuna cache |

Una volta completata questa pianificazione iniziale, la configurazione tecnica può iniziare a essere implementata per configurare le cache in base a questi requisiti.

Anche se il contenuto viene aggiornato e deve essere reso live all’interno del TTL di memorizzazione nella cache, nella maggior parte dei casi è possibile cancellare manualmente le cache per il dispatcher AEM e la cache Commerce di Adobe in modo selettivo per quel contenuto, il che significa che le modifiche urgenti verranno applicate immediatamente. Anche il processo di cancellazione manuale della cache deve essere pianificato e testato in anticipo in modo che se c&#39;è la necessità di forzare manualmente un aggiornamento su alcuni contenuti, allora è documentato in un manuale operativo del sito e chiarire come e chi deve essere coinvolto per agire in questo modo. Un esempio di operazione manuale di cancellazione della cache per AEM e Adobe Commerce è mostrato qui.

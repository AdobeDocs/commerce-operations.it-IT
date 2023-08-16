---
title: Implementazione dell’aggiornamento
description: Scopri le diverse fasi di implementazione dell’aggiornamento per i progetti Adobe Commerce.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---

# Implementazione dell’aggiornamento

L’implementazione dell’aggiornamento consiste in cinque fasi:

- Analisi dell’aggiornamento
- Sviluppo e garanzia della qualità (QA)
- Test di accettazione utente (UAT) e preparazione al lancio
- Launch
- Post-lancio

## Analisi dell’aggiornamento

L’analisi è senza dubbio la parte più importante del processo di aggiornamento. Un’analisi ben eseguita ti consente di risparmiare tempo e limita le sorprese in futuro. Il risultato di questa fase deve essere un elenco di controllo dell’aggiornamento dettagliato e un documento con tutte le dipendenze.

Di seguito sono riportati gli elementi che è possibile includere in un&#39;analisi approfondita:

- **Ambito della versione di Target**—Documentazione su [Experience League](../../release/release-notes/overview.md) e le informazioni dei webinar sulla versione del partner forniscono tutti i dettagli necessari sull’aggiornamento di target.

- **[!DNL Upgrade Compatibility Tool]risultati**- Questo strumento rende qualsiasi aggiornamento più rapido e semplice confrontando il codice corrente con il codice della versione di destinazione e generando un rapporto di tutti i problemi che devono essere risolti. Consulta la [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). I dettagli principali del rapporto includono:

   - Versione installata corrente
   - Aggiorna versione di destinazione
   - Numero e dettagli degli errori critici rilevati

- Aggiornamento dei servizi per supportare la versione di destinazione. Utilizza il seguente modello di tabella per mappare i servizi da aggiornare. Utilizza il [requisiti di sistema](../../installation/system-requirements.md) per determinare cosa aggiungere al _Esegui l’aggiornamento a_ colonna.


  | Servizio | Versione corrente | Esegui l’aggiornamento a | Note |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7.4 | 8.1 |                                                          |
  | Redis | 6.0 | 6.2 |                                                          |
  | [!DNL RabbitMQ] | 3.8 | 3.9 | Attualmente non in uso, ma è consigliabile utilizzarlo |
  | MariaDB (Cloud) | 10.4 | 10.6 |                                                          |
  | MySQL | 8.0 | -/-/ |                                                          |
  | Compositore | 1.9.2 | 2.2 |                                                          |
  | Elasticsearch | 7.10 | 7.17 |                                                          |

- **Estensioni e moduli di terze parti**: utilizza questo modello di tabella per comprendere lo stato delle estensioni e delle personalizzazioni, in modo da poter prendere decisioni strategiche e definire azioni. Si tratta di un’opportunità per sostituire eventuali estensioni native per Adobe Commerce o per il Magento Open Source, al fine di ridurre al minimo la complessità del progetto. Utilizza il `bin/magento module:status` per visualizzare un elenco di moduli ed estensioni.

  | # | Estensione/<br>nome modulo | Pacchetto Compositore | Fornitore | Versione corrente | Funzionalità | Compatibile con le più recenti<br>Versione Commerce? | Problemi | Nativo di Commerce? | Azione | Note |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Nome e collegamento dell’estensione | estensione/<br>extensionx-magento-2 | Nome fornitore | Versione installata | Requisiti aziendali | Sì/No | Elencare i problemi identificati relativi a questa estensione | Sì/No | Mantieni/Sostituisci/<br>Rimuovi |       |

- **Moduli personalizzati**- Simile alla tabella dei moduli di terze parti, questo modello consente di tenere traccia e comprendere lo stato e le azioni necessarie per l&#39;aggiornamento dei moduli personalizzati.

  | # | Nome modulo | Funzionalità | Obbligatorio | Nativo di Commerce? | Azione | Note |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Nome modulo | Requisiti aziendali | Sì/No | Sì/No | Mantieni/Sostituisci/Rimuovi |       |

- **Pacchetti compositore e dipendenze in compositore.json che richiedono un aggiornamento.**

Inoltre, i partner possono partecipare a [Versioni beta di Adobe Commerce](../../release/beta.md) e utilizza le opportunità precedenti al rilascio per accedere in anteprima al codice per una versione futura. Ottenere l’accesso anticipato al codice aiuta gli sviluppatori a prepararsi con tempo sufficiente per completare l’aggiornamento entro la data di disponibilità generale (GA, General Availability). Il codice beta viene generalmente rilasciato cinque settimane prima della data di disponibilità generale e le pre-versioni vengono rilasciate con due settimane di anticipo.

## Sviluppo e controllo qualità

Il test è la fase di un aggiornamento che richiede più tempo. Di conseguenza, questo processo dovrebbe essere il più possibile automatizzato. Il _[Guida al test delle applicazioni](https://developer.adobe.com/commerce/testing/guide/)_ fornisce dettagli su come impostare e utilizzare strumenti di test di piattaforme e sistemi per un controllo qualità più rapido. Utilizza un ambiente di staging per testare e convalidare l’aggiornamento prima di passare alla produzione.

## UAT e preparazione al lancio

UAT è una delle ultime fasi dell’aggiornamento che richiede la revisione e la convalida del sito. È inoltre necessario decidere quando distribuire e se è necessaria una pagina di manutenzione. Pianifica i processi cron e i messaggi di terze parti.

Con l’avvicinarsi della data di diffusione, la comunicazione è essenziale. Se più persone conoscono il cambiamento all&#39;orizzonte, il suo impatto su di loro e come devono affrontarlo, allora è più probabile che tu abbia un lancio di successo. Non abbiate paura di comunicare eccessivamente ogni passo del percorso—aumenta la probabilità di risonanza di recensioni da tutti gli interessati una volta che andate in diretta!

## Launch

Completa l’aggiornamento distribuendo in produzione e aggiornando le estensioni. Verificare i flussi di percorso critici con ordini simulati. Consulta questi [best practice](../prepare/best-practices.md) per alcuni suggerimenti sull’avvio con problemi minimi.

Segui il tuo piano di comunicazione e assicurati che tutte le parti interessate siano a conoscenza dell’aggiornamento e siano pienamente addestrate a supportarlo.

Infine, rivolgiti al tuo team per determinare le lezioni apprese e le insidie. Questa retrospettiva ti aiuta a migliorare il processo la prossima volta.

## Post-lancio

Dopo l’avvio del sito, assicurati di controllare i dati di analisi, la console Google Search e altre risorse per verificare che non vi siano problemi imprevisti e che tutto funzioni come previsto.

È sempre una buona idea monitorare le prestazioni attraverso strumenti di monitoraggio ben progettati. Esistono molti strumenti e strumenti per monitorare le prestazioni del sito, quindi assicurati di sceglierne uno che sia adatto alla tua organizzazione. Consigliamo ai clienti di Adobe Commerce che utilizzano il nostro sistema di gestione dell’infrastruttura cloud di avvalersi di servizi quali [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) per monitorare le prestazioni del sito.

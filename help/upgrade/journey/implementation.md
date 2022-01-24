---
title: Implementazione aggiornamento
description: Scopri le diverse fasi dell’implementazione dell’aggiornamento per i progetti Adobe Commerce e Magenti Open Source.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 1%

---


# Implementazione dell&#39;aggiornamento

L&#39;implementazione dell&#39;aggiornamento prevede cinque fasi:

- Analisi dell’aggiornamento
- Controllo dello sviluppo e della qualità (QA)
- Test di accettazione degli utenti (UAT) e preparazione all&#39;avvio
- Launch
- Post-lancio

## Analisi dell’aggiornamento

L&#39;analisi è probabilmente la parte più importante del processo di aggiornamento. Un’analisi ben eseguita consente di risparmiare tempo e di limitare le sorprese in futuro. Il risultato di questa fase dovrebbe essere una lista di controllo dettagliata dell&#39;aggiornamento e un documento con tutte le dipendenze.

Di seguito sono riportati gli elementi da includere in un’analisi approfondita:

- **Ambito di rilascio di target**—Documentazione su [Commerce DevDocs](https://devdocs.magento.com) e le informazioni dei webinar sulle versioni dei partner forniscono tutti i dettagli che devi sapere sull’aggiornamento di target.

- **[!DNL Upgrade Compatibility Tool]risultati**: questo strumento rende qualsiasi aggiornamento più rapido e semplice confrontando il codice corrente con il codice della versione di destinazione e producendo un rapporto su tutti i problemi da risolvere. Consulta la sezione [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). I principali dettagli del rapporto includono:

   - Versione installata corrente
   - Aggiorna la versione di destinazione
   - Numero e dettagli degli errori critici rilevati

- Aggiornamento dei servizi per supportare la versione di destinazione. Utilizza il seguente modello di tabella per mappare i servizi da aggiornare. Utilizza la [requisiti di sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) per determinare cosa aggiungere al _Aggiorna a_ colonna.


   | Servizio | Versione corrente | Aggiorna a | Note |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.2.33 | 8.1 |  |
   | Redis | 5,05 | 6,0 |  |
   | RabbitMQ | 3,7 | 3,8 | Non è attualmente in uso, ma è consigliabile utilizzarlo |
   | MariaDB (Cloud) | 10.2.33 | 10,4 |  |
   | MySQL | 8,0 |  |  |
   | Compositore | 1.9.2 | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Estensioni e moduli di terze parti**- Utilizza questo modello di tabella per comprendere lo stato delle estensioni e delle personalizzazioni, in modo da poter prendere decisioni strategiche e definire azioni. Questa è un’opportunità per sostituire eventuali estensioni native per Adobe Commerce o Magento Open Source per ridurre al minimo la complessità del progetto. Utilizza la `bin/magento module:status` per visualizzare un elenco di moduli ed estensioni.

   | # | Estensione/<br>nome del modulo | Pacchetto compositore | Fornitore | Versione corrente | Funzionalità | Compatibile con gli ultimi<br>Versione commerciale? | Problemi | Native to Commerce? | Azione | Note |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nome e collegamento dell’estensione | estensione/<br>extensionx-magento-2 | Nome fornitore | Versione installata | Requisiti aziendali | Sì/No | Elenco dei problemi identificati che devono affrontare questa estensione | Sì/No | Mantieni/sostituisci/<br>Rimuovi |  |

- **Moduli personalizzati**- Simile alla tabella dei moduli di terze parti, questo modello consente di tenere traccia e comprendere lo stato e le azioni necessarie per l’aggiornamento dei moduli personalizzati.

   | # | Nome modulo | Funzionalità | Obbligatorio | Native to Commerce? | Azione | Note |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nome modulo | Requisiti aziendali | Sì/No | Sì/No | Mantieni/sostituisci/Rimuovi |  |

- **Pacchetti di compositori e dipendenze in composer.json che richiedono un aggiornamento.**

Inoltre, i partner possono partecipare alla [Programma Adobe Commerce Beta](https://devdocs.magento.com/release/beta-program.html) e utilizza le opportunità pre-release per accedere in anteprima al codice per una versione futura. L’accesso anticipato al codice consente agli sviluppatori di prepararsi con tempo sufficiente per completare l’aggiornamento entro la data di disponibilità generale (GA, General Availability). Il codice beta viene generalmente rilasciato cinque settimane prima della data GA e i pre-release vengono rilasciati con due settimane di anticipo. Per la versione 2.4.4, Adobe ha iniziato a rilasciare il codice beta cinque mesi prima della data GA (8 marzo 2022), quindi i partner possono iniziare a prepararsi per tale aggiornamento ora entro [iscrizione al programma](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Sviluppo e controllo qualità

Il test è la fase di un aggiornamento che richiede il maggior tempo. Di conseguenza, tale processo dovrebbe essere il più automatizzato possibile. La _[Guida al test delle applicazioni](https://devdocs.magento.com/guides/v2.4/test/testing.html)_ fornisce dettagli su come configurare e utilizzare gli strumenti di test della piattaforma e del sistema per un controllo qualità più rapido. Utilizza un ambiente di staging per testare e convalidare l’aggiornamento prima di passare alla produzione.

## UAT e preparazione al lancio

UAT è una delle ultime fasi dell&#39;aggiornamento che richiede la revisione e la convalida del sito. È inoltre necessario decidere quando distribuire e se è necessaria una pagina di manutenzione. Pianifica i processi cron e i messaggi di terze parti.

Con l&#39;avvicinarsi della data di distribuzione, la comunicazione è essenziale. Se più persone conoscono il cambiamento all&#39;orizzonte, il suo impatto e il modo in cui deve affrontarlo, è più probabile che il lancio abbia successo. Non abbiate paura di comunicare in modo eccessivo ogni fase del percorso, aumenta la probabilità di commenti accesi da tutte le persone coinvolte una volta che andate in diretta!

## Launch

Completa l’aggiornamento distribuendo in produzione e aggiornando le estensioni. Assicurati di testare i flussi critici del percorso con ordini simulati. Dai un&#39;occhiata a questi [best practice](../prepare/best-practices.md) per alcuni suggerimenti sull&#39;avvio con problemi minimi.

Segui il tuo piano di comunicazione e assicurati che tutte le parti interessate siano a conoscenza dell’aggiornamento e siano completamente addestrate a supportarlo.

Infine, debrief con il tuo team per determinare le lezioni apprese e le insidie. Questa retrospettiva ti aiuta a migliorare il processo la prossima volta.

## Post-lancio

Dopo l’avvio del sito, controlla i dati di analisi, la console Google Search e altre risorse per garantire che non vi siano problemi imprevisti e che tutto funzioni come previsto.

È sempre consigliabile controllare le prestazioni attraverso strumenti di monitoraggio ben progettati. Ci sono molti strumenti e mezzi per monitorare le prestazioni del sito, quindi assicurati di sceglierne uno che si abbina bene con la tua organizzazione. Consigliamo ai clienti Adobe Commerce che utilizzano il nostro sistema di gestione dell’infrastruttura cloud di usufruire dei vantaggi offerti da servizi quali [Nuova relè](https://devdocs.magento.com/cloud/project/new-relic.html) per monitorare le prestazioni del sito.

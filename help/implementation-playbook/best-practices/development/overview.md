---
title: Fase di sviluppo dell’implementazione
description: Scopri le best practice di implementazione per la fase di sviluppo dei progetti Adobe Commerce.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: cca301a72b972d843b878fae28901a47c8fc0489
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---


# Fase di sviluppo

La fase di sviluppo comprende le seguenti attività:

- Configurazione dell’ambiente locale e di staging
- Pianificazione Sprint
- Esecuzione ticket
- Risoluzione dei problemi
- Revisione, unione e test del codice
- Revisione Sprint
- Approvazione del cliente

>[!TIP]
>
>Consulta [le best practice generali](general.md) per consigli di alto livello sulla gestione complessiva del processo di sviluppo.

Le sezioni seguenti includono informazioni sulle best practice per la fase di sviluppo.

## Gestione del codice

| Best practice | Descrizione |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Revisione del codice](code-review.md) | Processo di convalida consigliato per garantire che la funzionalità implementata soddisfi i requisiti |
| [Compositore rispetto a Git](code-management.md) | Determina come distribuire il codice personalizzato tenendo in considerazione la gestione delle versioni, la complessità del codice e la gestione delle dipendenze |
| [Strategia di diramazione](git-branching.md) | Gestire il codice sorgente negli archivi Git |

## Piattaforma e servizi

| Best practice | Descrizione |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Build e distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=it){target="_blank"} | Descrive le best practice per le fasi di build e implementazione di Adobe Commerce nei progetti di infrastruttura cloud |
| Debug | Eseguire il debug sistematico ed efficace del framework di Adobe Commerce |
| [Distribuzione di contenuto statico](static-content-deployment.md) | Evita problemi con il contenuto statico che non viene visualizzato nella vetrina |
| [Risoluzione dei problemi](troubleshooting.md) | Risoluzione dei problemi comuni di implementazione di Adobe Commerce |

## Database

| Best practice | Descrizione |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Modifica tabella](modifying-core-and-third-party-tables.md) | Determinare come e quando modificare le tabelle di database di Adobe Commerce e di terze parti |

## Ottimizzazione dei file

| Best practice | Descrizione |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Ridimensionamento immagine catalogo](catalog-image-resizing.md) | Fornisce indicazioni sul ridimensionamento delle immagini prima che un negozio entri in produzione per garantire prestazioni ottimali |
| [CSS e JS](optimize-css-js-files.md) | Unire e minimizzare i file CSS e JavaScript dalla riga di comando Admin o |
| [Immagini](image-optimization.md) | Ottimizzare le immagini e utilizzare Fastly per ottimizzare i tempi di risposta |

## Sviluppo front-end

| Best practice | Descrizione |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Sviluppo tema](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Descrive i modelli di sviluppo per garantire la compatibilità tra il tema, le versioni future di Adobe Commerce ed estensioni personalizzate |

## Sviluppo PHP

| Best practice | Descrizione |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Gestione delle eccezioni](exception-handling.md) | Descrive i metodi consigliati per la registrazione delle eccezioni |
| [Estensioni](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Descrive i modelli di sviluppo per garantire la compatibilità tra l’estensione, le versioni future di Adobe Commerce e altre estensioni personalizzate |
| [Blocchi di contenuto privato](private-content-block-configuration.md) | Configurare blocchi di contenuto privati per ottimizzare le prestazioni della vetrina |
| [Modifica codice PHP principale e di terze parti](modifying-core-and-third-party-code.md) | Modifica la funzionalità, il risultato o l’input di codice che non è stato creato o che non è stato controllato direttamente |

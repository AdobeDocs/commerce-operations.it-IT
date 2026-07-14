---
title: '[!DNL Commerce Version Tool]'
description: Scopri  [!DNL Commerce Version Tool]  per Adobe Commerce e utilizza vendor/bin/patch-status per controllare lo stato mensile delle patch di sicurezza.
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Le patch di sicurezza mensili per Adobe Commerce non sono cumulative e devono essere applicate in sequenza. [!DNL Commerce Version Tool] ([!DNL CVT]) consente ai commercianti di verificare la copertura delle patch segnalando quali patch di sicurezza mensili sono installate, quali patch mancano e quali CVE sono protetti dall&#39;installazione.

>[!IMPORTANT]
>
>Lo strumento [!DNL CVT] è solo informativo. Non applica patch, ripristina patch o modifica i file sorgente di Adobe Commerce. È in grado di scrivere file di cache, file temporanei a esecuzione inattiva e voci del registro di controllo per supportare il reporting sullo stato delle patch.

## Panoramica dello strumento

Lo strumento [!DNL CVT] è un eseguibile autonomo incluso in ogni patch di sicurezza Adobe Commerce mensile. Quando la patch viene applicata a un&#39;installazione di Adobe Commerce, lo strumento viene installato in `vendor/bin/patch-status`. Richiede PHP 8.1 o versione successiva e il binario `patch` del sistema. Non richiede pacchetti Composer, estensioni PHP non standard, avvio di Adobe Commerce o un passaggio di installazione separato.

Lo strumento [!DNL CVT] consente di:

- Rilevare le patch di sicurezza applicate per un&#39;installazione di Adobe Commerce supportata.
- Identificare le patch mancanti in una sequenza di patch di sicurezza isolata mensile.
- Segnalare lo stato di sicurezza protetto, vulnerabile o sconosciuto per i record CVE (Common Vulnerabilities and Exposures) correlati alle patch.
- Genera output leggibile da un computer, ad esempio JSON o CSV, per scanner, dashboard e rapporti di conformità.
- Rileva lo stato della patch per le piattaforme e i componenti supportati.

## Disponibilità

Lo strumento [!DNL CVT] supporta il reporting dello stato delle patch per le piattaforme e i componenti seguenti quando Adobe fornisce metadati di patch per la versione installata nel file del Registro di sistema delle patch.

| Piattaforma o componente | Disponibilità |
| --- | --- |
| Adobe Commerce on-premise | Supportato |
| [!DNL Magento Open Source] | Supportato |
| Business-to-business Adobe Commerce (B2B) | Supportato durante l&#39;installazione |
| Page Builder di Adobe Commerce | Supportato durante l&#39;installazione |
| Inventario Adobe Commerce | Supportato durante l&#39;installazione |
| Sono stati rilevati componenti aggiuntivi da `composer.lock` | Supportato quando rappresentato nel file del Registro di sistema della patch |

{style="table-layout:auto"}

## Casi d’uso comuni

Utilizzare lo strumento [!DNL CVT] quando è necessario:

- Verificare se un&#39;installazione di Adobe Commerce include le patch di sicurezza isolate necessarie.
- Confermare se i set di patch ignorati o incompleti lasciano la copertura CVE incompleta.
- Genera output JSON o CSV per reporting interno o scansione automatica.
- Fornire informazioni sullo stato delle patch prima di aprire una richiesta di supporto o di pianificare la correzione.

## Linee guida per l’utilizzo dei risultati

Considera l&#39;output dello strumento [!DNL CVT] come dati di rilevamento che supportano la pianificazione delle patch e la revisione della sicurezza.

Segui queste linee guida:

- Eseguire lo strumento [!DNL CVT] su un&#39;installazione Adobe Commerce stabile e supportata.
- Esaminare le patch mancanti e sconosciute prima di effettuare richieste di informazioni sullo stato di protezione.
- Mantenere l’output JSON o CSV per il controllo e l’automazione.
- Considera l&#39;output della scansione come dati operativi relativi alla sicurezza.
- Condividi solo i dettagli necessari per il supporto o la risoluzione dei problemi.

## Rilevamento patch

Lo strumento [!DNL CVT] esegue il rilevamento in due passaggi fissi. Entrambi i passaggi vengono sempre eseguiti quando si genera un rapporto sullo stato delle patch.

- **Rilevamento compositore:** Lo strumento legge il file `composer.lock` per determinare la versione di base [!DNL Adobe Commerce] e le aree dei componenti installati. Se lo strumento non è in grado di rilevare una versione di base, viene chiuso con il codice `1`.

- **Rilevamento esecuzione in prova:** Per ogni patch applicabile, lo strumento utilizza un controllo in prova delle modifiche apportate alla patch per determinare se la patch è già applicata, non è applicata o se lo stato della patch è sconosciuto. Lo strumento gestisce le dipendenze delle patch durante questo controllo in modo che i risultati riflettano la versione del componente installato.

Il report include solo le patch applicabili ai componenti installati e di installazione rilevati. Se lo strumento non è in grado di confermare la presenza di una patch applicabile, la patch viene classificata come sconosciuta.

## Inizia a utilizzare [!DNL CVT]

Utilizzare questi argomenti per generare, risolvere i problemi e tenere traccia dei rapporti sullo stato delle patch:

- [Generare un report sullo stato delle patch](generate-report.md) per eseguire lo strumento [!DNL CVT], esaminare le opzioni dei comandi e interpretare i risultati del report.
- [[!DNL Commerce Version Tool] risoluzione dei problemi](troubleshooting.md) per risolvere risultati imprevisti o errori di comando.
- [[!DNL Commerce Version Tool] note sulla versione](release-notes.md) per rivedere gli aggiornamenti.

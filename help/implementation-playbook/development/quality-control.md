---
title: Controllo qualità
description: Scopri i processi di controllo della qualità di Adobe Commerce relativi ai progetti di implementazione.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Processi e strumenti di controllo della qualità

![Diagramma del processo di controllo della qualità](../../assets/playbooks/quality-control-diagram.svg)

Il processo di controllo della qualità del diagramma precedente può essere descritto brevemente come segue.

<table>
<thead>
  <tr>
    <th>Processo di sviluppo software</th>
    <th>Flusso di lavoro QC</th>
    <th>QC</th>
    <th>Leader QC</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Sviluppo</td>
    <td>Pianificazione</td>
    <td></td>
    <td>Rivedere e contribuire ai piani di prova</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Creare specifiche di test (casi di test/scenari di test)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Preparare e acquisire i dati dei test</td>
  </tr>
  <tr>
    <td></td>
    <td>Analisi e progettazione del test</td>
    <td>Rivedere e contribuire ai piani di prova</td>
    <td>Avviare la preparazione, le specifiche</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Creare specifiche di test (casi di test/scenari di test)</td>
    <td>Scrivere o rivedere una strategia di test per il progetto</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preparare e acquisire i dati dei test</td>
    <td> Guida, guida e monitoraggio dell'analisi, della progettazione</td>
  </tr>
  <tr>
    <td>Test interni</td>
    <td>Esecuzione del test</td>
    <td>Implementa i test, esegue e registra i test</td>
    <td>Monitoraggio dell’attuazione e dell’esecuzione dei test</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Controllare le prestazioni e analizzare la sicurezza - Valutare i risultati e le deviazioni dai risultati attesi</td>
    <td>Garantire la tracciabilità dei test sulla base del test e tenere traccia dei bug nel sistema di monitoraggio dei bug</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Segnala i bug al sistema di tracciamento dei bug (Jira/Redmine/Trello)</td>
    <td>Assegnare priorità/programmare test in modo da allinearli alla pianificazione del progetto definita dal PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Nuova verifica (test di conferma) dopo la correzione dei bug</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Valutazione e reporting</td>
    <td>Segnala lo stato di avanzamento del test al lead QC e al PM</td>
    <td>Valutazione dei risultati e dell’avanzamento dei test</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Scrivi rapporti di riepilogo delle prove in base alle informazioni raccolte durante il test</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verifica dei feedback dei clienti o delle richieste di modifica (CR)</td>
    <td>Seguito</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Esegui nuovi test e test di regressione dopo aver modificato il codice sorgente</td>
    <td>Controllo</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Aggiornare le specifiche di prova</td>
    <td></td>
  </tr>
  <tr>
    <td>Manutenzione</td>
    <td>Manutenzione</td>
    <td>Revisione e contributo alle attività</td>
    <td>Revisione e stima del tempo per le attività</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Creare/aggiornare specifiche di test</td>
    <td>Avanzamento del test di follow-up</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Esegui test per queste attività</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Eseguire test di regressione</td>
    <td></td>
  </tr>
</tbody>
</table>

Simile al [strumenti](project-management-tools.md) abbiamo identificato per il processo di sviluppo, abbiamo selezionato una manciata di soluzioni e piattaforme di scelta che spesso utilizziamo per i test di controllo della qualità.

| Finalità | Strumento |
|---------------------------|---------------------------------------------------|
| Indice delle prestazioni del sito web | Google PageSpeed, Webpagetest, JMeter |
| Sicurezza | Strumento di scansione della sicurezza Adobe Commerce, SonarQube, ZAP |
| Sistema di gestione dei problemi | JIRA |
| Test dell&#39;interfaccia utente | Pixel perfetti, BrowserStack |
| Test API | Postman, SoapUI |
| Test di automazione | Selenio |


## Indice delle prestazioni del sito web

GooglePageSpeed fornisce rapporti sulle prestazioni di una pagina sia su dispositivi mobili che desktop e suggerimenti su come migliorare tale pagina.

WebPageTest è uno strumento di prestazioni web che utilizza browser reali per accedere alle pagine web e raccogliere le metriche di temporizzazione.

JMeter è un progetto Apache che può essere utilizzato come strumento di prova del carico per l&#39;analisi e la misurazione delle prestazioni di una varietà di servizi, con particolare attenzione alle applicazioni web.

## Sicurezza

SonarQube e ZAP sono stati introdotti nel processo di sviluppo, ma lo includiamo anche qui con ulteriori informazioni su come è coinvolto nel processo QC.

SonarQube è utilizzato anche per l&#39;ispezione continua della qualità del codice per eseguire revisioni automatiche con analisi statica del codice per rilevare bug, odori di codice e vulnerabilità di sicurezza.

OWASPZAP (Zed Attack Proxy) è destinato ad essere utilizzato sia da coloro che sono nuovi per la sicurezza delle applicazioni, così come tester di penetrazione professionale. Alcune delle funzionalità integrate includono l&#39;intercettazione di server proxy, crawler web tradizionali e AJAX, scanner automatizzato, scanner passivo, navigazione forzata, Fuzzier, supporto WebSocket, linguaggi di script e supporto Plug-n-Hack.

## Test dell&#39;interfaccia utente

Perfect Pixel consente agli sviluppatori e ai progettisti di markup di inserire una sovrapposizione immagine semitrasparente sopra il HTML sviluppato ed eseguire un confronto perfetto in pixel tra loro.

BrowserStack è una piattaforma di test web e mobile cloud che consente agli sviluppatori di testare i propri siti web e applicazioni mobili su browser on-demand, sistemi operativi e dispositivi mobili reali.

## Test API

Postman è la piattaforma di collaborazione per lo sviluppo delle API. Postman semplifica ogni fase della creazione di un’API e semplifica la collaborazione in modo da creare API migliori.

SoapUI è un’applicazione di test del servizio Web open source per SOAP (Simple Object Access Protocol) e i trasferimenti dello stato di rappresentanza (REST). La sua funzionalità riguarda l&#39;ispezione dei servizi web; invocare, sviluppare, simulare e deridere; prove funzionali; test di carico e conformità.

## Test di automazione

Il selenio è composto da diversi componenti (API client Selenium, Selenium WebDriver), ciascuno dei quali assume un ruolo specifico nel contribuire allo sviluppo dell&#39;automazione dei test delle applicazioni web.

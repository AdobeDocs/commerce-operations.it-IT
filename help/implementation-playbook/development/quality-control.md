---
title: Controllo qualità
description: Learn about Adobe Commerce quality control processes related to implementation projects.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Quality control process and tools

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
    <td>Create test specifications (test cases/test scenarios)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Prepare and acquire test data</td>
  </tr>
  <tr>
    <td></td>
    <td>Test Analysis and Design</td>
    <td>Rivedere e contribuire ai piani di prova</td>
    <td>Avviare la preparazione, le specifiche</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Create test specifications (test cases/test scenarios)</td>
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
    <td>Test Implementation and Execution</td>
    <td>Implements tests, execute and log the tests</td>
    <td>Monitoring implementation and execution of the tests</td>
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
    <td>Re-testing (confirmation testing) after bug fixing</td>
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
    <td>Write test summary reports based on the information gathered during the test</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verify Customer Feedbacks or Change Requests (CRs)</td>
    <td>Follow-up</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Perform re-testing and regression testing after changing the source code</td>
    <td>Controllo</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Aggiornare le specifiche di prova</td>
    <td></td>
  </tr>
  <tr>
    <td>Maintenance</td>
    <td>Manutenzione</td>
    <td>Revisione e contributo alle attività</td>
    <td>Revisione e stima del tempo per le attività</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Creare/aggiornare specifiche di test</td>
    <td>Follow-up test progress</td>
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
    <td>Perform regression testing</td>
    <td></td>
  </tr>
</tbody>
</table>

Analogamente agli [strumenti](project-management-tools.md) identificati per il processo di sviluppo, abbiamo selezionato una manciata di soluzioni e piattaforme di scelta che utilizziamo spesso per i test di controllo della qualità.

| Finalità | Strumento |
|---------------------------|---------------------------------------------------|
| Website performance index | Google PageSpeed, Webpagetest, JMeter |
| Sicurezza | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| Issue management system | JIRA |
| Test dell&#39;interfaccia utente | Pixel perfetti, BrowserStack |
| Test API | Postman, SoapUI |
| Automation testing | Selenium |


## Indice delle prestazioni del sito web

GooglePageSpeed fornisce rapporti sulle prestazioni di una pagina sia su dispositivi mobili che desktop e suggerimenti su come migliorare tale pagina.

WebPageTest è uno strumento di prestazioni web che utilizza browser reali per accedere alle pagine web e raccogliere le metriche di temporizzazione.

JMeter è un progetto Apache che può essere utilizzato come strumento di prova del carico per l&#39;analisi e la misurazione delle prestazioni di una varietà di servizi, con particolare attenzione alle applicazioni web.

## Sicurezza

SonarQube e ZAP sono stati introdotti nel processo di sviluppo, ma lo includiamo anche qui con ulteriori informazioni su come è coinvolto nel processo QC.

SonarQube è utilizzato anche per l&#39;ispezione continua della qualità del codice per eseguire revisioni automatiche con analisi statica del codice per rilevare bug, odori di codice e vulnerabilità di sicurezza.

OWASPZAP (Zed Attack Proxy) è destinato ad essere utilizzato sia da coloro che sono nuovi per la sicurezza delle applicazioni, così come tester di penetrazione professionale. Alcune delle funzionalità integrate includono l&#39;intercettazione di server proxy, crawler web tradizionali e AJAX, scanner automatizzato, scanner passivo, navigazione forzata, Fuzzier, supporto WebSocket, linguaggi di script e supporto Plug-n-Hack.

## UI testing

Perfect Pixel consente agli sviluppatori e ai progettisti di markup di inserire una sovrapposizione immagine semitrasparente sopra l&#39;HTML sviluppato ed eseguire un confronto perfetto in pixel tra loro.

BrowserStack è una piattaforma di test web e mobile cloud che consente agli sviluppatori di testare i propri siti web e applicazioni mobili su browser on-demand, sistemi operativi e dispositivi mobili reali.

## Test API

Postman è la piattaforma di collaborazione per lo sviluppo delle API. Postman semplifica ogni fase della creazione di un’API e semplifica la collaborazione in modo da creare API migliori.

SoapUI è un’applicazione di test del servizio Web open source per SOAP (Simple Object Access Protocol) e i trasferimenti dello stato di rappresentanza (REST). Its functionality covers web-service inspection; invoking, development, simulation, and mocking; functional testing; load and compliance testing.

## Test di automazione

Selenium is composed of several components (Selenium client API, Selenium WebDriver) with each taking on a specific role in aiding the development of web application test automation.

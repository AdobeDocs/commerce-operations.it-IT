---
title: Controllo qualità
description: Scopri i processi di controllo della qualità di Adobe Commerce relativi ai progetti di implementazione.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Processo di controllo qualità e strumenti

![Diagramma del processo di controllo qualità](../../assets/playbooks/quality-control-diagram.svg)

Il processo di controllo della qualità descritto nel diagramma precedente può essere descritto brevemente come segue.

<table>
<thead>
  <tr>
    <th>Processo di sviluppo software</th>
    <th>Flusso di lavoro QC</th>
    <th>QC</th>
    <th>QC Leader</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Sviluppo</td>
    <td>Pianificazione</td>
    <td></td>
    <td>Rivedere e contribuire ai piani di test</td>
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
    <td>Preparare e acquisire i dati di test</td>
  </tr>
  <tr>
    <td></td>
    <td>Analisi e progettazione dei test</td>
    <td>Rivedere e contribuire ai piani di test</td>
    <td>Avviare la preparazione e le specifiche</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Creare specifiche di test (casi di test/scenari di test)</td>
    <td>Scrivi o rivedi una strategia di test per il progetto</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preparare e acquisire i dati di test</td>
    <td> Guidare, guidare e monitorare l'analisi, la progettazione</td>
  </tr>
  <tr>
    <td>Test interni</td>
    <td>Implementazione ed esecuzione dei test</td>
    <td>Implementa i test, esegui e registra i test</td>
    <td>Monitoraggio dell’attuazione e dell’esecuzione dei test</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Controllo delle prestazioni e sicurezza dell'analisi: valutazione dei risultati e delle deviazioni dai risultati previsti</td>
    <td>Garantire la tracciabilità dei test alla base di test e tenere traccia dei bug nel sistema di tracciamento dei bug</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Pubblicare bug nel sistema di tracciamento dei bug (Jira/Redmine/Trello)</td>
    <td>Assegna priorità/pianifica i test da allineare alla pianificazione del progetto definita dal PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Nuovo test (test di conferma) dopo la correzione di bug</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Valutazione e reporting</td>
    <td>Segnala l’avanzamento del test al lead QC e al PM</td>
    <td>Valutazione dei risultati e dell’avanzamento dei test</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Scrivi i rapporti di riepilogo del test in base alle informazioni raccolte durante il test</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verifica feedback dei clienti o richieste di modifica (CR)</td>
    <td>Follow-up</td>
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
    <td>Rivedi e contribuisci alle attività</td>
    <td>Rivedere e stimare il tempo per le attività</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Crea/aggiorna specifiche di test</td>
    <td>Stato dei test di follow-up</td>
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

Simile a [strumenti](project-management-tools.md) abbiamo identificato per il processo di sviluppo una serie di soluzioni e piattaforme che spesso utilizziamo per il test del controllo di qualità.

| Finalità | Strumento |
|---------------------------|---------------------------------------------------|
| Indice delle prestazioni del sito web | Google PageSpeed, Webpagetest, JMeter |
| Sicurezza | Strumento Adobe Commerce Security Scan, SonarQube, ZAP |
| Sistema di gestione dei problemi | JIRA |
| Test interfaccia utente | Pixel perfetti, BrowserStack |
| Test API | Postman, SoapUI |
| Test di automazione | Selenio |


## Indice delle prestazioni del sito web

GooglePageSpeed genera rapporti sulle prestazioni di una pagina sia su dispositivi mobili che desktop e fornisce suggerimenti su come tale pagina può essere migliorata.

WebPageTest è uno strumento di prestazioni Web che utilizza browser reali per accedere alle pagine Web e raccogliere metriche di temporizzazione.

JMeter è un progetto Apache che può essere utilizzato come strumento di test del carico per analizzare e misurare le prestazioni di una varietà di servizi, con particolare attenzione alle applicazioni web.

## Sicurezza

SonarQube e ZAP sono stati introdotti nel processo di sviluppo, ma lo stiamo anche includendo qui con ulteriori informazioni su come è coinvolto nel processo di controllo qualità.

SonarQube è anche utilizzato per l&#39;ispezione continua della qualità del codice per eseguire revisioni automatiche con analisi statica del codice per rilevare bug, code smell e vulnerabilità di sicurezza.

OWASPZAP (Zed Attack Proxy) è destinato ad essere utilizzato sia da chi non ha familiarità con la sicurezza delle applicazioni, sia da chi effettua test di penetrazione professionali. Alcune delle funzionalità integrate includono l&#39;intercettazione del server proxy, i Web crawler tradizionali e AJAX, lo scanner automatico, lo scanner passivo, la navigazione forzata, Fuzzier, il supporto WebSocket, i linguaggi di script e il supporto Plug-n-Hack.

## Test interfaccia utente

Perfect Pixel consente agli sviluppatori e ai designer di markup di posizionare una sovrapposizione di immagine semitrasparente sopra le HTML sviluppate e di eseguire un confronto pixel-perfetto tra di loro.

BrowserStack è una piattaforma di test cloud per web e dispositivi mobili che consente agli sviluppatori di testare i propri siti web e applicazioni mobili su browser on-demand, sistemi operativi e dispositivi mobili reali.

## Test API

Postman è la piattaforma di collaborazione per lo sviluppo API. Postman semplifica ogni passaggio della creazione di un’API e semplifica la collaborazione per consentirti di creare API migliori.

SoapUI è un&#39;applicazione di test per servizi Web open-source per SOAP (Simple Object Access Protocol) e REST (Rappresentational State Transfer). La sua funzionalità copre l&#39;ispezione dei servizi web; richiamo, sviluppo, simulazione e beffa; test funzionali; test di carico e conformità.

## Test di automazione

Selenium è composto da diversi componenti (Selenium client API, Selenium WebDriver) ciascuno dei quali assume un ruolo specifico nel favorire lo sviluppo dell&#39;automazione dei test delle applicazioni web.

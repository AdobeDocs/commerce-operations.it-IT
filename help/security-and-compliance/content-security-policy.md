---
title: Panoramica della politica di sicurezza dei contenuti
description: Scopri come migliorare la posizione di sicurezza dell’archivio Adobe Commerce o Magenti Open Source utilizzando un criterio di sicurezza per i contenuti.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Panoramica della politica di sicurezza dei contenuti

Un&#39;informativa sulla sicurezza dei contenuti (Content Security Policy, CSP) può fornire ulteriori livelli di difesa per le installazioni Adobe Commerce e Magenti Open Source, aiutando a rilevare e attenuare gli attacchi di inserimento di dati (XSS) e script tra siti diversi. Questo comune vettore di attacco funziona iniettando contenuti dannosi che false afferma di provenire dal sito web. Una volta caricato ed eseguito il contenuto dannoso, può avviare il trasferimento non autorizzato dei dati.

CSP fornisce un set standardizzato di direttive che indica al browser quali risorse di contenuto possono essere considerate affidabili e che devono essere bloccate. Utilizzando criteri accuratamente definiti, i CSP possono limitare il contenuto del browser per consentire la visualizzazione solo delle risorse nella whitelist.

## Configurazione

Per evitare interferenze con le operazioni del sito, i CSP possono essere implementati in più fasi. Il CSP dispone di due modalità di funzionamento di base: `report-only mode` e `restrict mode`. Il rilascio di Adobe Commerce 2.3.5 segna la prima fase della nostra implementazione e rende disponibili i CSP in `report-only mode` per impostazione predefinita. In una versione futura, `restrict mode` è attivato per impostazione predefinita per una protezione predefinita aggiuntiva.

**Modalità solo rapporto**: Il browser viene istruito a segnalare le violazioni dei criteri, ma non a farle rispettare. Ogni volta che una risorsa richiesta viola i CSP, il browser registra gli errori risultanti nella console. Il registro della console può quindi essere utilizzato per indagare la causa di ogni violazione.

È importante esaminare tutti gli errori CSP man mano che si verificano e perfezionare i criteri fino a quando tutte le risorse necessarie non vengono inserite nella whitelist. È sicuro passare a `restrict mode` quando non si verificano più errori. In caso contrario, un CSP configurato in modo non corretto potrebbe causare la visualizzazione di una pagina vuota con numerosi errori di console nel browser. Una CSP configurata correttamente consente di distribuire i contenuti inseriti nella whitelist senza alcun impatto percepito sulle prestazioni.

**Modalità Limita**: Al browser viene indicato di applicare tutti i criteri sui contenuti e di limitare la pubblicazione alle risorse inserite nella whitelist. Poiché i CSP sono configurati dal server anziché dall’amministratore, la maggior parte dei merchants ha bisogno dell’assistenza di un integratore di sistema o di uno sviluppatore per configurarli correttamente. Vedi [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in _Estensioni PHP Commerce_ guida per sviluppatori.

## Reporting

Per impostazione predefinita, CSP invia gli errori alla console del browser, ma può essere configurato per raccogliere i registri di errore tramite richiesta HTTP. Inoltre, esistono diversi servizi di terze parti che puoi utilizzare per monitorare, raccogliere e segnalare le violazioni dei CSP.

[URI rapporto](https://report-uri.io/) è un servizio che monitora le violazioni dei CSP e visualizza i risultati in un dashboard. Sia gli esercenti che gli sviluppatori possono utilizzare il servizio per ricevere rapporti ogni volta che si verificano violazioni dei CSP.

---
title: Panoramica sulla sicurezza dei contenuti
description: Scopri come migliorare la posizione di sicurezza del tuo Adobe Commerce o store di Magento Open Source utilizzando un criterio per la sicurezza dei contenuti.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Panoramica sulla sicurezza dei contenuti

I criteri sulla sicurezza dei contenuti (Content Security Policy, CSP) possono fornire ulteriori livelli di difesa per le installazioni di Adobe Commerce e di Magento Open Source, contribuendo a rilevare e attenuare gli attacchi cross-site scripting (XSS) e i relativi attacchi di iniezione di dati. Questo comune vettore di attacco funziona inserendo contenuti dannosi che afferma erroneamente di provenire dal sito web. Una volta caricati ed eseguiti, i contenuti dannosi possono avviare il trasferimento non autorizzato dei dati.

I CSP forniscono un set di direttive standard che indica al browser quali risorse di contenuto possono essere considerate attendibili e quali devono essere bloccate. Utilizzando criteri accuratamente definiti, i CSP possono limitare il contenuto del browser in modo da consentire la visualizzazione solo delle risorse nella whitelist.

## Configurazione

Per evitare interferenze con le operazioni del sito, i CSP possono essere implementati in fasi. I CSP hanno due modalità operative di base: `report-only mode` e `restrict mode`. Il rilascio di Adobe Commerce 2.3.5 segna la prima fase della nostra implementazione e rende i CSP disponibili in `report-only mode` per impostazione predefinita. In una versione futura, `restrict mode` è attivato per impostazione predefinita per una protezione aggiuntiva preconfigurata.

**Modalità solo rapporto**: al browser viene richiesto di segnalare le violazioni dei criteri, ma non di implementarle. Ogni volta che una risorsa richiesta viola la CSP, il browser registra gli errori risultanti nella console. Il registro della console può quindi essere utilizzato per analizzare la causa di ciascuna violazione.

È importante rivedere tutti gli errori CSP man mano che si verificano e perfezionare i criteri fino a quando tutte le risorse necessarie non vengono inserite nella whitelist. È sicuro passare a `restrict mode` quando non si verificano altri errori. In caso contrario, una CSP non configurata correttamente potrebbe causare la visualizzazione di una pagina vuota nel browser, con numerosi errori della console. Una CSP correttamente configurata consente di distribuire i contenuti inseriti nella whitelist senza alcun impatto percepito sulle prestazioni.

**Modalità Limita**: al browser viene chiesto di applicare tutti i criteri per i contenuti e limitare la pubblicazione alle risorse inserite nella whitelist. Poiché i CSP sono configurati dal server, anziché dall’amministratore, la maggior parte dei commercianti ha bisogno dell’assistenza di un integratore di sistemi o di uno sviluppatore per configurarli correttamente. Consulta [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) nel _Estensioni Commerce PHP_ guida per gli sviluppatori.

## Generazione rapporti

Per impostazione predefinita, i CSP inviano gli errori alla console del browser, ma possono essere configurati per raccogliere i registri degli errori tramite richiesta HTTP. Inoltre, esistono diversi servizi di terze parti che puoi utilizzare per monitorare, raccogliere e segnalare violazioni CSP.

[URI report](https://report-uri.io/) è un servizio che monitora le violazioni CSP e visualizza i risultati in un dashboard. Sia i commercianti che gli sviluppatori possono utilizzare il servizio per ricevere rapporti ogni volta che si verificano violazioni CSP.

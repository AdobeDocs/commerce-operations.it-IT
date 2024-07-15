---
title: Panoramica sulla sicurezza dei contenuti
description: Scopri come migliorare la posizione di sicurezza del tuo store Adobe Commerce utilizzando un criterio per la sicurezza dei contenuti.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Panoramica sulla sicurezza dei contenuti

I criteri sulla sicurezza dei contenuti (Content Security Policy, CSP) possono fornire ulteriori livelli di difesa per le installazioni di Adobe Commerce, contribuendo a rilevare e attenuare gli attacchi cross-site scripting (XSS) e i relativi attacchi di iniezione di dati. Questo comune vettore di attacco funziona inserendo contenuti dannosi che afferma erroneamente di provenire dal sito web. Una volta caricati ed eseguiti, i contenuti dannosi possono avviare il trasferimento non autorizzato dei dati.

I CSP forniscono un set di direttive standard che indica al browser quali risorse di contenuto possono essere considerate attendibili e quali devono essere bloccate. Utilizzando criteri accuratamente definiti, i CSP possono limitare il contenuto del browser in modo da consentire la visualizzazione solo delle risorse nella whitelist.

## Configurazione

Per evitare interferenze con le operazioni del sito, i CSP possono essere implementati in fasi. CSP dispone di due modalità operative di base: `report-only mode` e `restrict mode`.

**Modalità solo report**: il browser è istruito a segnalare le violazioni dei criteri, ma non ad applicarle. Ogni volta che una risorsa richiesta viola la CSP, il browser registra gli errori risultanti nella console. Il registro della console può quindi essere utilizzato per analizzare la causa di ciascuna violazione.

È importante rivedere tutti gli errori CSP man mano che si verificano e perfezionare i criteri fino a quando tutte le risorse necessarie non vengono inserite nella whitelist. È possibile passare a `restrict mode` quando non si verificano altri errori. In caso contrario, una CSP non configurata correttamente potrebbe causare la visualizzazione di una pagina vuota nel browser, con numerosi errori della console. Una CSP correttamente configurata consente di distribuire i contenuti inseriti nella whitelist senza alcun impatto percepito sulle prestazioni.

**Modalità di restrizione**: al browser viene chiesto di applicare tutti i criteri per i contenuti e di limitare la pubblicazione alle risorse inserite nella whitelist.

La prima fase dell&#39;implementazione di Adobe Commerce CSP è stata introdotta in Adobe Commerce 2.3.5 e ha reso i CSP disponibili in `report-only mode` per impostazione predefinita.  In Adobe Commerce 2.4.7 e versioni successive, la CSP è configurata in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree di vetrina e nelle aree di amministrazione e in modalità `report-only` per tutte le altre pagine. L&#39;intestazione CSP corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo gli script in linea inseriti nella whitelist.

Poiché i CSP sono configurati dal server, anziché dall’amministratore, la maggior parte dei commercianti ha bisogno dell’assistenza di un integratore di sistemi o di uno sviluppatore per configurarli correttamente. Consulta [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) nella _Guida per gli sviluppatori di Commerce PHP_.


## Generazione rapporti

Per impostazione predefinita, i CSP inviano gli errori alla console del browser, ma possono essere configurati per raccogliere i registri degli errori tramite richiesta HTTP. Inoltre, esistono diversi servizi di terze parti che puoi utilizzare per monitorare, raccogliere e segnalare violazioni CSP. Le violazioni CSP possono essere segnalate a un endpoint per la raccolta aggiungendo l&#39;URI dall&#39;amministratore o dal file `config.xml` per un modulo personalizzato.  Consulta [Configurazione dell&#39;URI del report](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) nella _Guida per gli sviluppatori delle estensioni Commerce PHP_.

[Report URI](https://report-uri.io/) è un servizio che monitora le violazioni CSP e visualizza i risultati in un dashboard. Sia i commercianti che gli sviluppatori possono utilizzare il servizio per ricevere rapporti ogni volta che si verificano violazioni CSP.

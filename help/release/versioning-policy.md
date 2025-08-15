---
title: Criterio di rilascio
description: Scopri i diversi tipi di versioni di Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: f7b22089bcf88f6c881b0cbd4d7f77d795d9071b
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Criteri di rilascio di Adobe Commerce

Adobe Commerce utilizza [il controllo delle versioni semantiche](https://semver.org/) a livello del singolo modulo (ad esempio `magento/framework 101.1.1`), ma non per il numero di versione di marketing. Ad esempio:

- **Versione principale**—2
- **Versione secondaria**—2.4
- **Versione di PATCH**—2.4.8
   - **Versione patch di sicurezza**—2.4.8-p1
      - Correzione di bug di sicurezza
      - Miglioramento della sicurezza
- **Versione patch di ALPHA**—2.4.8-alpha1
- **Versione patch BETA**—2.4.8-beta1
- **Estensibilità, infrastruttura e servizi**
- **Hotfix**
- **Singola patch**
- **Patch personalizzata**

## Versione secondaria

Le seguenti linee guida si applicano alle versioni minori:

- Sono possibili modifiche che causano interruzioni; il codice scritto per Adobe Commerce 2.2.x potrebbe non funzionare più con Adobe Commerce 2.3.x. Ad esempio, le versioni minori possono introdurre il supporto per i principali requisiti di sistema e dipendenze, come il PHP.
- Le versioni del modulo possono variare. Ad esempio, alcune modifiche al modulo vengono introdotte in una nuova patch, mentre altre vengono introdotte in una versione minore.
- Versioni minori possono includere nuove funzioni che potrebbero richiedere un ulteriore intervento da parte tua o del tuo partner durante l’aggiornamento per garantire la compatibilità.
- Le versioni secondarie possono includere correzioni per problemi di sicurezza e qualità.

## Versione PATCH

I rilasci di patch sono principalmente incentrati sulla fornitura di correzioni di sicurezza, prestazioni, conformità e qualità ad alta priorità per aiutare i siti a mantenere le prestazioni al massimo.

Le seguenti linee guida si applicano alle versioni patch:

- La versione secondaria più recente supportata riceve correzioni e miglioramenti di qualità funzionale completa.
- Vengono evitate modifiche che potrebbero interrompere le estensioni o la compatibilità del codice. Ad esempio, il codice scritto per la versione 2.2.0 deve ancora funzionare sulla versione 2.2.7.
- In casi eccezionali, è possibile rilasciare modifiche che causano interruzioni o patch o hotfix aggiuntivi per risolvere problemi di sicurezza o conformità e problemi di qualità ad alto impatto. A livello di modulo, queste modifiche sono per lo più a livello di PATCH; a volte a livello di MINOR.

### Versione patch di SICUREZZA

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Versione patch di ALPHA

Le versioni precedenti al rilascio da parte di Beta delle funzioni di Adobe Commerce vengono rese pubbliche a tutti i clienti Adobe Commerce e ai partner Adobe. Le versioni di Alpha sono progettate per fornire un feedback e una valutazione tempestivi delle funzioni ancora in fase di sviluppo. Queste versioni offrono l’opportunità di eseguire test e pianificare l’integrazione in anticipo rispetto alle versioni di Beta e General Availability.

Le versioni di Alpha possono essere incomplete e possono contenere difetti. Vengono fornite &quot;COSÌ COM’È&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni di Alpha. I clienti non devono fare affidamento sul corretto funzionamento o sulle prestazioni delle versioni di Alpha o di qualsiasi documentazione o materiale ad esse allegato. L’utilizzo delle versioni di Alpha è interamente a rischio del cliente.

## Versione patch di Beta

Le versioni di disponibilità pre-generale delle funzioni di Adobe Commerce sono rese disponibili a tutti i clienti Adobe Commerce e ai partner Adobe. Consente un tempo aggiuntivo prima della disponibilità generale per rivedere il codice e i componenti interessati.

I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni di Beta. I clienti non devono fare affidamento sul corretto funzionamento o sulle prestazioni delle versioni di Beta o di qualsiasi documentazione o materiale ad esse allegato. Di conseguenza, qualsiasi utilizzo delle versioni di Beta è interamente a rischio del cliente.

## Funzionalità, infrastruttura cloud e versione di estensibilità

L’infrastruttura cloud e i rilasci di funzioni contengono nuove funzioni e aggiornamenti di funzioni che vengono forniti come servizi indipendenti, separati dai rilasci di patch. Gli esempi includono, ma non sono limitati a:

- Aggiornamenti ai servizi di hosting cloud e all’infrastruttura
- B2B
- Prodotti SaaS (Catalog Service, Connessione dati, Consigli di prodotto e Live Search)
- Tecnologia di estensibilità (SDK dell’interfaccia utente di amministrazione, Mesh API, App Builder Starter Kit, Eventi e Webhook)

## Hotfix

Gli hotfix sono patch che contengono problemi di sicurezza ad alto impatto o correzioni di qualità, come le correzioni a vulnerabilità pari a zero giorni, che interessano molti commercianti. Adobe rilascia gli hotfix (in base alle esigenze) per le versioni di Adobe Commerce supportate quando sono interessate da problemi critici di sicurezza o qualità. Gli hotfix vengono pubblicati nella [sezione Problemi noti](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) della Knowledge Base. Queste correzioni sono incluse nella prossima versione pianificata della patch.

>[!NOTE]
>
>Gli hotfix possono contenere modifiche non compatibili con le versioni precedenti.

## Singola patch

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni vengono applicate alle versioni secondarie supportate di Adobe Commerce. Adobe rilascia singole patch in base alle esigenze per Adobe Commerce in conformità con [Criteri del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Le singole patch non contengono modifiche non compatibili con le versioni precedenti.

## Patch isolata

Le patch isolate sono correzioni di sicurezza rilasciate indipendentemente da una patch di sicurezza completa per consentire un’implementazione più rapida. Ciascuna patch isolata risolve un problema di sicurezza specifico ed è inclusa nell&#39;ultima patch di sicurezza o in una patch di sicurezza completa imminente. I dettagli sul problema sono forniti nel relativo bollettino sulla sicurezza, che rimanda a un articolo della Knowledge Base (KB) contenente i dettagli della correzione, le modalità di applicazione della patch e informazioni aggiuntive.

Per trovare gli ultimi aggiornamenti per la sicurezza disponibili per Adobe Commerce, visita il [Centro sicurezza PC](https://helpx.adobe.com/security/products/magento.html).

## Patch personalizzata

Creato da personale non Adobe per risolvere un problema o modificare il codice Adobe Commerce per vari motivi. Le patch personalizzate vengono distribuite tramite lo strumento [Patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).

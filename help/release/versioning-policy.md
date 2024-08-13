---
title: Criterio di rilascio
description: Scopri i diversi tipi di versioni di Adobe Commerce, tra cui versioni secondarie, patch di sicurezza, funzionalità, hotfix, patch singole e patch personalizzate.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b5d120893668f4315e289a204649270db4f7a6bc
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Criteri di rilascio di Adobe Commerce

Adobe Commerce utilizza [il controllo delle versioni semantiche](https://semver.org/) a livello del singolo modulo (ad esempio `magento/framework 101.1.1`), ma non per il numero di versione di marketing. Ad esempio:

- **Versione principale**—2
- **Versione secondaria**—2.4
- **versione di PATCH**—2.4.5
   - **Versione patch di sicurezza**—2.4.5-p1
      - Correzione di bug di sicurezza
      - Miglioramento della sicurezza
- **Versione patch BETA**—2.4.7-beta2
- **Estensibilità, infrastruttura e servizi**
- **Hotfix**
- **Singola patch**
- **Patch personalizzata**

## Versione secondaria

Le seguenti linee guida si applicano alle versioni minori:

- Sono possibili modifiche che causano interruzioni; il codice scritto per Adobe Commerce 2.2.x potrebbe non funzionare più con Adobe Commerce 2.3.x. Ad esempio, le versioni minori possono introdurre il supporto per i principali requisiti di sistema e dipendenze, come il PHP.
- Le versioni del modulo possono variare. Ad esempio, alcune modifiche al modulo vengono introdotte in una nuova patch, mentre altre vengono introdotte in una versione minore.
- Versioni minori possono includere nuove funzioni che potrebbero richiedere un ulteriore lavoro da parte tua o del tuo partner durante l’aggiornamento per garantire la compatibilità.
- Le versioni secondarie possono includere correzioni per problemi di sicurezza e qualità.

## Versione di PATCH

I rilasci di patch sono principalmente incentrati sulla fornitura di correzioni di sicurezza, prestazioni, conformità e qualità ad alta priorità per aiutare i siti a mantenere le prestazioni al massimo.

Le seguenti linee guida si applicano alle versioni patch:

- La versione secondaria più recente supportata riceve correzioni e miglioramenti di qualità funzionale completa.
- Vengono evitate modifiche che potrebbero interrompere le estensioni o la compatibilità del codice. Ad esempio, il codice scritto per la versione 2.2.0 deve ancora funzionare sulla versione 2.2.7.
- In casi eccezionali, è possibile rilasciare modifiche che causano interruzioni o patch o hotfix aggiuntivi per risolvere problemi di sicurezza o conformità e problemi di qualità ad alto impatto. A livello di modulo, si tratta per lo più di modifiche a livello di PATCH; a volte di modifiche MINORI.

### Versione patch di SICUREZZA

{{$include /help/_includes/security-patch-release-overview.md}}

## Versione patch di Beta

Le versioni di disponibilità pre-generale delle funzioni di Adobe Commerce sono rese pubbliche a tutti i clienti Adobe Commerce e ai partner Adobe. Consente un tempo aggiuntivo prima della disponibilità generale per rivedere il codice e i componenti interessati.

I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non avrà alcun obbligo di mantenere, correggere, aggiornare, modificare, modificare o supportare in altro modo (tramite i servizi di supporto Adobe o in altro modo) le versioni di Beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni di Beta e/o di qualsiasi documentazione o materiale di accompagnamento. Di conseguenza, qualsiasi utilizzo delle versioni di Beta è interamente a rischio del Cliente.

## Funzionalità, infrastruttura cloud e versione di estensibilità

L’infrastruttura cloud e i rilasci di funzioni contengono nuove funzioni e aggiornamenti di funzioni che vengono forniti come servizi indipendenti, separati dai rilasci di patch. Alcuni esempi includono aggiornamenti ai servizi e all’infrastruttura di hosting cloud, B2B, prodotti SaaS (Catalog Service, Data Connection, Product Recommendations e Live Search) e tecnologia di estensibilità (API Mesh, Integration Starter Kit ed Eventing).

## Hotfix

Gli hotfix sono patch che contengono problemi di sicurezza ad alto impatto o correzioni di qualità, come le correzioni a vulnerabilità pari a zero giorni, che interessano molti commercianti. Adobe rilascia gli hotfix per le versioni di Adobe Commerce ancora supportate e interessate da problemi critici di sicurezza o qualità, in base alle esigenze. Gli hotfix vengono pubblicati nella [sezione Problemi noti](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) della Knowledge Base. Queste correzioni sono incluse nella prossima versione pianificata della patch.

>[!NOTE]
>
>Gli hotfix possono contenere modifiche non compatibili con le versioni precedenti.

## Singola patch

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni vengono applicate alle versioni secondarie supportate di Adobe Commerce. Adobe rilascia singole patch in base alle esigenze di Adobe Commerce in conformità con i nostri [criteri del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Le singole patch non contengono modifiche non compatibili con le versioni precedenti.

## Patch isolata

Contiene una correzione indipendente inclusa nell’ultima patch di sicurezza o in una patch di sicurezza imminente, che viene rilasciata separatamente per un’implementazione più rapida.

## Patch personalizzata

Creato da personale non Adobe per risolvere un problema o modificare il codice Adobe Commerce per vari motivi. Le patch personalizzate vengono distribuite tramite lo strumento [Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

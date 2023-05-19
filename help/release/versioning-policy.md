---
title: Criterio di rilascio
description: Scopri i diversi tipi di versioni di Adobe Commerce, tra cui versioni secondarie, patch di sicurezza, funzionalità, hotfix, patch singole e patch personalizzate.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Criteri di rilascio di Adobe Commerce

Adobe Commerce e utilizzo del Magento Open Source [controllo delle versioni semantiche](https://semver.org/) a livello di singolo modulo (ad esempio `magento/framework 101.1.1`), ma non per il numero di versione marketing. Ad esempio:

- **Versione PRINCIPALE**—2
- **Versione secondaria**—2,4
- **Versione di PATCH**—2.4.5
   - **Versione patch di SICUREZZA**—2,4,5-p1
      - Correzione di bug di sicurezza
      - Miglioramento della sicurezza
- **Versione patch BETA**—2.4.7-beta1
- **Versione funzione**
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

**Correzione bug di sicurezza**: modifica del codice software per risolvere un problema di sicurezza identificato e ottenere i risultati previsti in un’area di prodotto interessata. Queste correzioni sono generalmente compatibili con le versioni precedenti.

**Miglioramento della sicurezza**: miglioramento del software o modifica della configurazione per migliorare in modo proattivo la sicurezza all’interno dell’applicazione. Questi miglioramenti di sicurezza aiutano a risolvere i rischi di sicurezza che influiscono sulla postura di sicurezza dell’applicazione Adobe Commerce, ma che possono essere incompatibili con le versioni precedenti.

Con le versioni delle patch di sicurezza, è possibile proteggere il sito in modo più efficiente senza applicare ulteriori correzioni di qualità e miglioramenti contenuti in una versione completa delle patch. Alle versioni delle patch di sicurezza viene aggiunto &#39;-pN&#39;, dove N è la versione della patch incrementale che inizia con 1 (ad esempio, 2.3.5-p1). Le versioni delle patch di sicurezza possono includere anche gli hotfix necessari per risolvere i problemi critici che interessano l’applicazione Adobe Commerce.

Ogni versione di patch di sicurezza si basa sulla versione completa precedente della patch. Contiene le correzioni di qualità e sicurezza della versione patch precedente e le correzioni di sicurezza create tra la versione patch completa precedente e la versione patch di sicurezza.

Per istruzioni sul download e sull&#39;applicazione delle patch di sicurezza, vedere [Installazione rapida](../installation/composer.md#example---security-patch).

## Versione patch BETA

Le versioni di disponibilità pre-generale delle funzioni di Adobe Commerce sono rese pubbliche a tutti i clienti Adobe Commerce e ai partner Adobe. Consente un tempo aggiuntivo prima della disponibilità generale per rivedere il codice e i componenti interessati.

I rilasci beta possono contenere difetti e sono forniti &quot;COSÌ COM’È&quot; senza alcuna garanzia. Adobe non avrà alcun obbligo di mantenere, correggere, aggiornare, modificare, modificare o supportare in altro modo (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Si consiglia ai clienti di prestare cautela e di non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del Cliente.

## Versione funzione

Le versioni delle funzioni contengono nuove funzioni e aggiornamenti delle funzioni forniti come servizi indipendenti, separati dalle versioni patch. Alcuni esempi includono servizi come Product Recommendations e Live Search, moduli indipendenti come PWA Studi e Inventory management (MSI) e aggiornamenti ai servizi e all’infrastruttura cloud.

## Hotfix

Gli hotfix sono patch che contengono problemi di sicurezza ad alto impatto o correzioni di qualità, come le correzioni a vulnerabilità pari a zero giorni, che interessano molti commercianti. Adobe rilascia gli hotfix per le versioni di Adobe Commerce ancora supportate e interessate da problemi critici di sicurezza o qualità, in base alle esigenze. Gli hotfix vengono pubblicati in [Sezione Problemi noti](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) della nostra Knowledge Base. Queste correzioni sono incluse nella prossima versione pianificata della patch.

>[!NOTE]
>
>Gli hotfix possono contenere modifiche non compatibili con le versioni precedenti.

## Singola patch

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni vengono applicate alle versioni secondarie supportate di Adobe Commerce. Adobe rilascia singole patch in base alle esigenze di Adobe Commerce in conformità con [Criteri del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Le singole patch non contengono modifiche non compatibili con le versioni precedenti.

## Patch personalizzata

Creato da personale non Adobe per risolvere un problema o modificare il codice Adobe Commerce per vari motivi. Le patch personalizzate vengono distribuite tramite [Strumento Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Argomenti correlati

- [Controllo delle versioni](https://developer.adobe.com/commerce/php/development/versioning/)
- [Versioni future](schedule.md)
- [Criteri del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

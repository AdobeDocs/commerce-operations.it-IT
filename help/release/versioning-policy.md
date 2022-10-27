---
title: Criterio di rilascio
description: Scopri i diversi tipi di versioni di Adobe Commerce, tra cui secondarie, patch, patch di sicurezza, funzionalità, hotfix, singole patch e patch personalizzate.
source-git-commit: f9bbfb86d2197ee7252602edba455ebcae5a2b18
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Criterio di rilascio di Adobe Commerce

Utilizzo di Adobe Commerce e Magenti Open Source [versione semantica](https://semver.org/) a livello del singolo modulo (ad esempio `magento/framework 101.1.1`), ma non per il numero di versione di marketing. Ad esempio:

- **Versione principale**—2
- **Rilascio minore**—2.4
- **Versione di PATCH**—2.4.1
   - **Patch di sicurezza**—2.4.1-p1
      - Correzione bug di sicurezza
      - Miglioramento della sicurezza
- **Versione in funzione**
- **Hotfix**
- **Patch individuale**
- **Patch personalizzata**

## Rilascio minore

Le seguenti linee guida si applicano alle versioni minori:

- È possibile interrompere le modifiche; il codice scritto per Adobe Commerce 2.2.x potrebbe non funzionare più con Adobe Commerce 2.3.x. Ad esempio, le versioni minori possono introdurre il supporto per i principali requisiti di sistema e le dipendenze, come PHP.
- Le versioni del modulo possono variare. Ad esempio, alcune modifiche al modulo vengono introdotte in una nuova patch, mentre altre vengono introdotte in una versione secondaria.
- Le versioni secondarie possono includere nuove funzionalità che potrebbero richiedere ulteriore lavoro da parte dell’utente o del partner della soluzione durante l’aggiornamento per garantire la compatibilità.
- Le versioni minori possono includere correzioni per problemi di sicurezza e qualità.

## Versione di PATCH

Le release delle patch sono incentrate principalmente sulla fornitura di correzioni di qualità, prestazioni, conformità e ad alta priorità per aiutarti a mantenere le prestazioni dei tuoi siti al loro picco.

Le seguenti linee guida si applicano alle release delle patch:

- Le ultime versioni secondarie supportate ricevono correzioni e miglioramenti completi della qualità funzionale.
- Vengono evitate modifiche che potrebbero interrompere le estensioni o la compatibilità del codice. Ad esempio, il codice scritto per la versione 2.2.0 deve ancora funzionare sulla versione 2.2.7.
- In via eccezionale, possono essere rilasciati cambiamenti di interruzione o patch o hotfix aggiuntivi per risolvere problemi di sicurezza o di conformità e problemi di qualità ad alto impatto. A livello di modulo, si tratta principalmente di modifiche a livello di PATCH; a volte le modifiche a livello MINOR.

## Patch di sicurezza

**Correzione bug di sicurezza**: Modifica del codice software che risolve un problema di sicurezza identificato e fornisce i risultati previsti in un&#39;area di prodotto interessata. Queste correzioni sono generalmente compatibili con le versioni precedenti.

**Miglioramento della sicurezza**: Un miglioramento software o una modifica della configurazione per migliorare in modo proattivo la sicurezza all&#39;interno dell&#39;applicazione. Questi miglioramenti della sicurezza aiutano a risolvere i rischi di sicurezza che influiscono sulla posizione di sicurezza dell’applicazione Adobe Commerce ma che possono essere incompatibili con le versioni precedenti.

Con le versioni delle patch di sicurezza, puoi mantenere il tuo sito più sicuro senza applicare correzioni e miglioramenti di qualità aggiuntivi contenuti in una versione completa delle patch trimestrale. Le release delle patch di sicurezza vengono aggiunte con &#39;-pN&#39;, dove N è la versione della patch incrementale che inizia con 1 (ad esempio, 2.3.5-p1). Le versioni delle patch di sicurezza possono anche includere gli hotfix necessari per risolvere i problemi critici che interessano l&#39;applicazione Adobe Commerce.

Ogni rilascio di patch di sicurezza è basato sulla versione completa della patch precedente. Contiene correzioni di qualità e sicurezza derivanti dalla release precedente della patch e correzioni di sicurezza create tra la versione completa della patch precedente e la release della patch di sicurezza.

Con l&#39;annuncio del nostro [nuova strategia di rilascio e informativa sul ciclo di vita aggiornata](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (16/09/2021), le nostre versioni delle patch di sicurezza sono differenziate in base al fatto che siano applicabili alla versione secondaria più recente supportata o a una parte di una linea di rilascio secondaria precedente ancora supportata:

- **Versioni delle patch di sicurezza per la versione secondaria più recente supportata**:

   - La versione della patch di sicurezza per la versione secondaria più recente supportata (attualmente Adobe Commerce 2.4) include:

      - Correzioni di bug di sicurezza create dopo la precedente versione completa della patch.

      - Queste release delle patch di sicurezza possono anche includere gli hotfix necessari per risolvere i problemi critici che possono influenzare l&#39;applicazione Adobe Commerce.
   - La versione delle patch di sicurezza per la versione secondaria più recente supportata (attualmente Adobe Commerce 2.4) non include in genere miglioramenti della sicurezza. Sono invece incluse nella versione completa della patch per la versione secondaria più recente supportata.


- **Versioni delle patch di sicurezza per le versioni precedenti supportate**:

   - Il rilascio della patch di sicurezza per una versione precedente secondaria ancora supportata (attualmente Adobe Commerce 2.3) include:

      - Correzioni di bug di sicurezza create dopo la precedente versione della patch o della patch di sicurezza e nuovi miglioramenti della sicurezza.

      - Queste versioni delle patch di sicurezza possono anche includere gli hotfix necessari per risolvere i problemi critici che interessano l&#39;applicazione Adobe Commerce.

      |  | Bug di sicurezza | Miglioramento della sicurezza |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Versioni delle patch di sicurezza per la versione secondaria più recente supportata (attualmente 2.4) | X |  |
      | Versioni delle patch di sicurezza per le versioni secondarie precedenti e supportate (attualmente 2.3) | X | X |


Per informazioni generali sulle versioni di sicurezza, vedi [Introduzione alla nuova versione delle patch di sola sicurezza](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Per istruzioni su come scaricare e applicare le patch di sicurezza, vedi [Installazione rapida](../installation/composer.md).

## Versione in funzione

Le versioni con funzioni contengono nuove funzioni e aggiornamenti di funzionalità forniti come servizi indipendenti, separati dalle release delle patch. Alcuni esempi includono servizi come Product Recommendations e Live Search, moduli indipendenti come PWA Studi e Inventory management (MSI) e aggiornamenti ai nostri servizi cloud e all’infrastruttura.

## Hotfix

Gli hotfix sono patch che contengono correzioni di qualità o di sicurezza ad alto impatto, come correzioni a vulnerabilità di zero giorni, che interessano molti merchants. Adobe rilascia gli hotfix per le versioni Adobe Commerce ancora supportate e interessate da problemi critici di sicurezza o qualità, in base alle esigenze. Gli hotfix vengono pubblicati in [Sezione Problemi noti](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) della nostra Knowledge Base. Queste correzioni sono incluse nella prossima versione pianificata della patch.

>[!NOTE]
>
>Gli hotfix possono contenere modifiche incompatibili con le versioni precedenti.

## Patch individuale

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni vengono applicate alle versioni secondarie supportate di Adobe Commerce. Adobe rilascia le singole patch necessarie per Adobe Commerce in conformità alla [Criterio del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Le singole patch non contengono modifiche incompatibili con le versioni precedenti.

## Patch personalizzata

Creato da personale non Adobe per risolvere un problema o modificare il codice Adobe Commerce per vari motivi. Le patch personalizzate vengono distribuite tramite [Strumento Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Argomenti correlati

- [Pianificazione e impostazione del budget per i cicli di aggiornamento di Commerce](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Controllo delle versioni](https://developer.adobe.com/commerce/php/development/versioning/)
- [Versioni future](schedule.md)
- [Criterio del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

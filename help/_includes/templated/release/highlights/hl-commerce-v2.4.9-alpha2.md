---
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Note sulla versione di Adobe Commerce (v2.4.9-alpha2)

## Elementi di rilievo in v2.4.9-alpha2

Le seguenti caratteristiche si applicano alla versione Adobe Commerce 2.4.9-alpha2.

### Framework

#### Aggiunta del supporto per OpenSearch 3

Adobe Commerce 2.4.9 è ora completamente compatibile con OpenSearch 3.x. Questo aggiornamento consente ai commercianti di beneficiare di prestazioni, sicurezza e supporto a lungo termine migliorati, mantenendo al contempo la compatibilità con le versioni precedenti di OpenSearch 2.x.

_AC-11846_

#### Aggiornamento della versione Nginx da 1.26 a 1.28

La versione Nginx utilizzata negli ambienti di sviluppo e test in tutte le versioni attualmente supportate di Adobe Commerce è aggiornata dalla versione 1.26 alla versione 1.28, in linea con l’ultima versione stabile di Nginx disponibile.
Il test a livello di PR ora viene eseguito su Nginx 1.28 confermando la piena compatibilità e il supporto per tutte le versioni di Adobe Commerce.

_AC-14104_

#### Esaminare la versione più recente di jquery-validate

Aggiornamento della libreria jQuery Validate alla versione 1.21.0 per migliorare le funzionalità di convalida dei moduli, migliorare l’esperienza utente e garantire una compatibilità moderna dei browser in tutti i moduli di Adobe Commerce, sia nelle interfacce amministratore che front-end.

_AC-14403 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Esaminare la versione più recente jquery-ui

Aggiornamento della libreria dell’interfaccia utente jQuery alla versione 1.14.1 per migliorare i widget dell’interfaccia utente, migliorare l’accessibilità e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia di amministrazione e front-end di Adobe Commerce.

_AC-14417 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Esaminare la versione più recente di less.js

Il preprocessore CSS Less.js è stato aggiornato alla versione 4.2.2 per migliorare le prestazioni di compilazione CSS, migliorare il supporto della sintassi e modernizzare il processo di creazione del tema in tutti i temi front-end e amministratore di Adobe Commerce.

_AC-14418 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Esaminare la versione più recente di moment-timezone-with-data.js

Aggiornamento della libreria Moment Timezone alla versione 0.5.43 per migliorare le funzionalità di gestione del fuso orario, aggiornare i dati del fuso orario con le ultime modifiche al database del fuso orario IANA e migliorare la precisione dell’elaborazione di data e ora in tutte le operazioni internazionali e multitfuso Adobe Commerce.

_AC-14419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Esaminare la versione più recente di underscore.js

Aggiornamento della libreria dell’utility Underscore.js alla versione 1.13.7 per migliorare le funzionalità di programmazione di JavaScript, le prestazioni di manipolazione dei dati e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia Adobe Commerce frontend e amministratore.

_AC-14420 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Migrare da TinyMCE a Hugerte.org

A causa della fine del supporto di TinyMCE 5 e 6 e delle incompatibilità di licenza con TinyMCE 7, l’implementazione corrente dell’editor WYSIWYG di Adobe Commerce viene migrata da TinyMCE all’editor HugeRTE open-source (https://hugerte.org/).
Questa migrazione garantisce che Adobe Commerce rimanga conforme alle licenze open source, evita le vulnerabilità TinyMCE 6 note e offre un’esperienza di modifica moderna e supportata per commercianti e sviluppatori.

_AC-14568_

#### Aggiunta del supporto completo Valkey 8.x per 2.4.9-alpha2

Adobe Commerce 2.4.9 dispone del supporto completo dei comandi CLI per Valkey, che rispecchia la funzionalità Redis esistente. La configurazione dell’amministratore e del cloud è stata aggiornata per consentire una configurazione perfetta di Valkey.
Questo aggiornamento garantisce che Adobe Commerce rimanga a prova di futuro e performante supportando Valkey 8.x, fornendo a commercianti e sviluppatori un’alternativa affidabile a Redis con l’avvicinarsi della fine del ciclo di vita.

_AC-14604_

### Altro

#### Aggiornamento del servizio AWS Valkey 8.x per la generazione e il test CNS

Aggiornamento del servizio AWS Valkey 8.x per la build CNS

_AC-14470_

#### 2.4.9-alpha2 - Miglioramenti della qualità core di agosto

_AC-14700_

### Sicurezza

#### Miglioramenti di sicurezza per 2.4.9-alpha2

_AC-14610_

### Spedizione

#### Migrare l’integrazione USPS dalle API obsolete degli strumenti web alle nuove API RESTful USPS

Per rispettare l’annuncio di USPS del ritiro delle API legacy degli strumenti web entro il 25 gennaio 2026, l’integrazione Adobe Commerce USPS viene migrata alle nuove API RESTful USPS.

Miglioramenti principali:

* Supporto di API doppie: gli utenti amministratori ora possono scegliere tra l’API legacy degli strumenti web e la nuova API RESTful USPS tramite le impostazioni di configurazione.
* Aggiornamento autenticazione: OAuth 2.0 è stato implementato per l’accesso API sicuro.
* Formato dati migliorato: transizione da XML a JSON per una comunicazione più pulita ed efficiente.
* Nuovi campi amministratore:
   * URL REST gateway (in base alla modalità: Sviluppo o Live)
   * ID client &amp;amp; Segreto
   * Tipo di conto, numero di conto
   * CRID, MID, codice di identificazione dell’Mailer
   * AES/ITN per spedizioni internazionali
   * Metodi di spedizione consentiti specifici per REST

Questa migrazione garantisce che Adobe Commerce rimanga conforme agli standard USPS, migliori l’affidabilità del sistema e integrazioni di spedizione a prova di futuro per gli esercenti.

_AC-13257_

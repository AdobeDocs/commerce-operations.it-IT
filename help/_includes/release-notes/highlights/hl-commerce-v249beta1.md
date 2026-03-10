---
source-git-commit: c699c3db054dbfb6d43ad18ced4d4d860e2c9db5
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 0%

---
# Elementi di rilievo di Adobe Commerce (v2.4.9-beta1)

## Elementi di rilievo nella versione v2.4.9-beta1

Le seguenti caratteristiche principali si applicano alla versione Adobe Commerce 2.4.9-beta1.

### API

#### Controllo dell’ereditarietà della galleria di prodotti API REST a livello di visualizzazione archivio

Se si aggiorna un prodotto tramite API REST in un ambito di archivio, le immagini e i video del prodotto non ereditano più le modifiche dall&#39;ambito globale quando `media_gallery_entries` viene omesso dal payload o impostato su `NULL`. È ora possibile ripristinare l’ereditarietà dell’ambito per immagini e video di prodotto tramite API REST impostando il campo corrispondente su `NULL`.

_ACP2E-4358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Interfaccia utente amministratore

#### Menu Azioni per la griglia delle regole dei prezzi di catalogo

La griglia Regole prezzo catalogo nell’amministratore di Commerce ora include un menu Azioni che consente agli esercenti di attivare, disattivare o eliminare più regole prezzo catalogo contemporaneamente. In questo modo la gestione delle regole di prezzo del catalogo è in linea con le azioni in blocco esistenti disponibili per le regole di prezzo del carrello, riducendo notevolmente il tempo necessario per gestire set di regole di grandi dimensioni.

_AC-13916_

#### Anteprima visualizzazione mobile per staging contenuto

La funzione di anteprima dell’area di gestione temporanea in Admin ora consente di eseguire il rendering accurato delle anteprime dei dispositivi mobili simulate dal browser, fornendo una rappresentazione visiva di come verrà visualizzato un aggiornamento dell’area di gestione temporanea su un dispositivo mobile.

_ACP2E-3397 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Pagamento rapido

- **Offerte promozionali nel foglio paga Google Pay Express**

  Il foglio di pagamento Google Pay Express ora supporta i codici promozionali e di offerta. Gli acquirenti possono applicare, visualizzare e rimuovere le promozioni Commerce Cart direttamente all&#39;interno del Google Pay sheet, garantendo ai clienti di pagamento rapido gli stessi sconti e incentivi dei flussi di pagamento standard.

  _BUNDLE-3476_

- **Offerte promozionali nel foglio paga Apple Pay Express**

  Il PaySheet di Apple Pay Express ora supporta i codici promozionali e di offerta. Gli acquirenti possono applicare un coupon direttamente all’interno del foglio di pagamento di Apple, in modo che gli utenti di checkout rapidi possano beneficiare degli stessi sconti e campagne dei flussi di pagamento standard.

  _BUNDLE-3477_

- **Apple Pay su Chrome e Firefox**

  Apple Pay ora può essere utilizzato su Chrome e Firefox, non solo su Safari. Quando Apple Pay Express è abilitato, i pulsanti Apple Pay sono disponibili nelle posizioni di vetrina supportate e i clienti completano il pagamento digitalizzando un codice con il proprio iPhone.

  _BUNDLE-3478_

- **Callback di spedizione lato server per PayPal Express**

  Il callback di spedizione PayPal Express è stato spostato dal lato client a quello server. Questo fornisce metodi di spedizione dinamici, calcoli dei costi in tempo reale e dettagli precisi a livello di carrello direttamente nel modale PayPal, migliorando l&#39;affidabilità e ponendo le basi per funzioni future come il supporto del modulo Contatto, i flussi di switch delle app e Venmo Express.

  _BUNDLE-3479_

- **Modulo di contatto PayPal per il pagamento rapido del commerciante statunitense**

  È stato introdotto un nuovo modulo PayPal Contact per i commercianti statunitensi. Quando abilitato, gli acquirenti che utilizzano PayPal Express possono visualizzare e aggiornare l&#39;indirizzo e-mail e il numero di telefono condivisi con il commerciante direttamente all&#39;interno del modale PayPal durante i flussi espressi (PDP, mini-carrello, carrello, pagamento espresso). I recapiti selezionati vengono quindi memorizzati nell&#39;ordine Commerce.

  _BUNDLE-3480_

#### Metodi di pagamento

- **Supporto di tipo carta ELO per i pagamenti Braintree**

  È stato aggiunto il supporto per il tipo di carta ELO in Braintree Payments. Gli amministratori possono ora abilitare ELO nella configurazione della carta di credito e i clienti possono effettuare con successo gli ordini utilizzando le carte ELO al momento del pagamento, garantendo transazioni senza soluzione di continuità tramite Braintree.

  _BUNDLE-3464_

- **BLIK metodo di pagamento locale per acquirenti polacchi**

  BLIK è stato aggiunto come nuovo metodo di pagamento locale per gli acquirenti polacchi. Ciò consente di effettuare pagamenti BLIK sicuri e basati su banche all&#39;interno del flusso LPM (Local Payment Methods) di Braintree esistente, migliorando la comodità di pagamento e la conversione per i clienti in Polonia.

  _BUNDLE-3481_

- **Pagamento su fattura — nuovo metodo di pagamento BNPL per la Germania**

  È stato aggiunto un nuovo metodo di pagamento locale, Paga su fattura per gli acquirenti tedeschi. Pay Upon Invoice è un&#39;opzione Buy Now, Pay Later (BNPL) fornita da PayPal e Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) che consente ai clienti di ricevere prima le merci e pagare la fattura entro 30 giorni, senza bisogno di un conto PayPal. Poiché non si tratta di un pagamento istantaneo, la finalizzazione degli ordini è guidata da un webhook lato server di PayPal.

  _BUNDLE-3475_

#### Vaulting delle carte

- **Vaulting di Google Pay tramite l&#39;area del conto**

  I clienti possono ora effettuare il vaulting delle proprie carte Google Pay tramite l&#39;area del conto quando Google Pay Vault è abilitato in Braintree. Le carte vendute appaiono in metodi di pagamento memorizzati, possono essere utilizzate per acquisti futuri al momento del pagamento e possono essere eliminate dal cliente. Questo estende il supporto del vaulting oltre le schede e da PayPal a Google Pay.

  _BUNDLE-3459_

- **Aggiornamento account in tempo reale (RTAU) per le schede con vaulting Braintree**

  La funzione Real-Time Account Updater (RTAU) aggiunta a Braintree garantisce che i dettagli archiviati di Visa, Mastercard e Discover vengano aggiornati automaticamente quando le schede scadono o vengono sostituite. In questo modo si riducono al minimo i pagamenti non riusciti, si mantiene aggiornato Commerce Vault e si ignorano i tipi non supportati (prepagati, Apple Pay, Google Pay) senza errori.

  _BUNDLE-3462_

#### Strumenti di amministrazione

- **Collega ordine Commerce a portale Braintree**

  Un collegamento al Braintree Portal viene ora aggiunto ai dettagli dell’ordine in Commerce Admin. Facendo clic sul collegamento, la transazione correlata viene aperta nel portale Braintree (in una nuova scheda), utilizzando l&#39;ID commerciante e l&#39;ID transazione dell&#39;ordine Commerce. Questo consente di effettuare riferimenti incrociati diretti senza effettuare l’accesso a entrambi i sistemi separatamente.

  _BUNDLE-3461_

#### Sicurezza e compatibilità

- **Aggiornamento dei criteri di sicurezza dei contenuti dell&#39;integrazione cardinale per 3D Secure**

  Content Security Policy (CSP) è stato aggiornato per supportare i più recenti requisiti di integrazione Cardinal (3D Secure). In questo modo, tutti gli script, gli iframe e le risorse correlate ospitati da Cardinal utilizzati durante i flussi 3D Secure saranno consentiti dai CSP del browser, evitando richieste bloccate ed esperienze di verifica o di verifica interrotte.

  _BUNDLE-3485_

- **Compatibilità PHP 8.5 dell&#39;estensione di pagamento Braintree**

  L&#39;estensione di pagamento Braintree è stata aggiornata per supportare il runtime PHP 8.5, mantenendo la compatibilità con PHP 8.4.

  _BUNDLE-3493_

### Piattaforma e infrastruttura

#### Supporto di OpenSearch 3.x

Adobe Commerce 2.4.9-beta1 è completamente compatibile con OpenSearch 3.x. Questo aggiornamento consente ai commercianti di beneficiare di prestazioni, sicurezza e supporto a lungo termine migliorati, mantenendo al contempo la compatibilità con le versioni precedenti di OpenSearch 2.x.

_AC-11846_

#### Supporto completo di Valkey 8.x

Adobe Commerce 2.4.9-beta1 aggiunge il supporto completo per Valkey 8.x come back-end della cache compatibile con Redis, inclusa la parità completa dei comandi CLI con Redis. Le opzioni di configurazione Admin (Amministratore) e Cloud (Cloud) sono state aggiornate per garantire una configurazione perfetta di Valkey. Questo supporto è guidato dalle modifiche alla fine del supporto e delle licenze di Redis 7.2, che offrono ai commercianti un’alternativa affidabile e completamente supportata a Redis nelle linee di rilascio da 2.4.5 a 2.4.9-beta1 di Commerce.

_AC-14103, AC-14604_

#### Aggiornamento della versione Nginx da 1.26 a 1.28

La versione Nginx utilizzata negli ambienti di sviluppo e test in tutte le versioni attualmente supportate di Adobe Commerce è stata aggiornata alla versione 1.28, in linea con la versione stabile più recente di Nginx. Il test a livello di PR ora viene eseguito su Nginx 1.28, confermando la piena compatibilità e il supporto per tutte le versioni di Adobe Commerce.

_AC-14104_

#### Il supporto di Apache ActiveMQ Artemis sostituisce RabbitMQ

È stato aggiunto il supporto per Apache ActiveMQ Artemis come alternativa strategica a RabbitMQ, guidata dai rischi associati alla fine del supporto associati a RabbitMQ 4. ActiveMQ Artemis è ora completamente supportato nelle righe di rilascio da 2.4.6 a 2.4.9-beta1 di Commerce, incluso Adobe Commerce Cloud con AWS ActiveMQ per implementazioni native per il cloud, e supporta la configurazione STOMP per utenti e publisher in coda. Le installazioni esistenti di RabbitMQ 4 rimangono compatibili per i commercianti che preferiscono continuare a utilizzare il servizio corrente di coda messaggi.

_AC-14558_

### PHP e Composer

#### Compatibilità PHP 8.5

A partire da Adobe Commerce 2.4.9-beta1, la piattaforma è completamente compatibile con PHP 8.5, pur mantenendo il supporto per PHP 8.4 e consentendo PHP 8.3 per scenari di solo aggiornamento. Questo lavoro modernizza il codice di base, le dipendenze e gli strumenti in modo che i commercianti possano passare alle versioni PHP più recenti prima della fine del supporto di PHP 8.4, mantenendo la conformità PCI e lo stato della piattaforma a lungo termine.

_AC-15615_

#### Supporto PHP 8.2 rimosso

A partire da Adobe Commerce 2.4.9-beta1, PHP 8.2 non è più supportato. La piattaforma ora esegue il targeting di PHP 8.3 e versioni successive, con il codice di base, le dipendenze e gli strumenti aggiornati per funzionare in modo pulito e affidabile su PHP 8.4 e 8.5.

_AC-15758_

#### Supporto della versione espansa di Composer 2.x

In precedenza, il supporto per la versione del Compositore era limitato alla versione 2.2.x. Adobe Commerce 2.4.9-beta1 estende questo supporto per includere Composer 2.4.x e versioni successive, ampliando la compatibilità per gli ambienti di sviluppo e distribuzione.

_AC-13792 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Compatibilità con Composer 2.9 verificata

Adobe Commerce 2.4.9-beta1 è completamente compatibile con Composer 2.x, incluso Composer 2.9. Questo allineamento mantiene la compatibilità con le versioni precedenti e garantisce un’esperienza di build e implementazione stabile per gli esercenti e gli sviluppatori che utilizzano le versioni più recenti del Compositore.

_AC-14481_

### Framework

#### Aggiornamento della sicurezza e della compatibilità del framework JWT

Come parte della revisione continua della sicurezza della piattaforma, la dipendenza del framework JWT per token web è stata valutata e aggiornata all’ultima versione principale, garantendo compatibilità futura e standard di sicurezza elevati per l’autenticazione basata su token tra le integrazioni Commerce. La funzionalità esistente è stata completamente mantenuta.

_AC-13209 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### Framework di test funzionali Adobe Commerce aggiornato alle dipendenze Symfony LTS

Il framework di test funzionali di Adobe Commerce (MFTF) è stato aggiornato per utilizzare le dipendenze più recenti di Symfony LTS, incluso symfony/config, come richiesto dall’aggiornamento del token web/jwt-framework. Questo risolve i conflitti di dipendenza precedenti e garantisce uno stack stabile e supportato per i test funzionali.

_AC-13244_

#### Le funzioni OAuth PHP native sostituiscono la libreria di terze parti

La libreria `carlos-mg89/oauth` di terze parti è stata sostituita con funzioni OAuth PHP native, migliorando la sicurezza, riducendo le dipendenze esterne e migliorando la stabilità della piattaforma.

_AC-14075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Il componente Symfony Cache sostituisce Zend_Cache

A partire da Adobe Commerce 2.4.9-beta1, il componente Zend_Cache obsoleto è stato sostituito dal componente Symfony Cache. Questo aggiornamento migliora le prestazioni della cache e la manutenibilità e garantisce la compatibilità a lungo termine con PHP 8.x e gli aggiornamenti futuri della piattaforma. I back-end della cache e i comandi di gestione della cache esistenti rimangono completamente supportati, senza la necessità di apportare modifiche per le integrazioni correnti.

_AC-15823_

#### L’editor WYSIWYG è migrato da TinyMCE a HugeRTE

A causa della fine del supporto di TinyMCE 5 e 6 e delle incompatibilità di licenza con TinyMCE 7, l&#39;editor WYSIWYG di Adobe Commerce è stato migrato all&#39;editor [HugeRTE](https://hugerte.org/) open-source. Questa migrazione garantisce che Adobe Commerce rimanga conforme alle licenze open source, evita le vulnerabilità TinyMCE 6 note e offre un’esperienza di modifica moderna e supportata per commercianti e sviluppatori.

_AC-14568_

#### L&#39;implementazione MVC nativa sostituisce Laminas MVC

Adobe Commerce ha introdotto un&#39;implementazione MVC nativa, sostituendo la precedente versione di Laminas MVC, per garantire compatibilità e stabilità a lungo termine oltre PHP 8.5. Questa modifica migliora le prestazioni, riduce le dipendenze esterne e fornisce una base più pronta per il futuro per Commerce.

_AC-15160_

#### Supporto ufficiale Symfony 7.4 LTS

Con l’aggiornamento della piattaforma Adobe Commerce 2.4.9-beta1, tutte le dipendenze di Symfony sono state aggiornate alle versioni più recenti di Symfony LTS 7.4. Tutte le classi personalizzate che estendono le classi principali di Symfony hanno aggiornato le dichiarazioni dei tipi e le firme dei metodi in linea con i requisiti di Symfony più recenti, evitando problemi di compatibilità e garantendo una transizione fluida ai componenti framework aggiornati.

_AC-15170 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c127d10b)_

#### Dipendenza PHPUnit allure aggiornata alla versione 3

La dipendenza `allure-framework/allure-phpunit` è stata aggiornata alla versione principale 3, che aggiunge il supporto per PHP 8.4 e PHP 8.5 e modernizza lo stack di reporting dei test basato su Allure. La dipendenza nativa richiesta in precedenza dalle versioni precedenti di Allure PHPUnit è stata rimossa, semplificando la configurazione e la manutenzione.

_AC-14548 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Rapporti di New Relic aggiornati all’API di NerdGraph

Il modulo di reporting di New Relic è stato aggiornato per supportare l’API di tracciamento delle modifiche NerdGraph (GraphQL) di New Relic, preservando al contempo completamente l’integrazione dei marcatori di distribuzione REST v2 esistenti. La modifica offre metadati di distribuzione più completi, supporto di endpoint regionali (Stati Uniti e Unione Europea) e configurabilità tramite impostazioni di amministrazione senza interrompere le configurazioni esistenti.

_AC-15461_

#### Aggiornamenti della libreria JavaScript

- **Chart.js aggiornato alla versione 4.5.0**

  Aggiornamento della libreria di grafici JavaScript Chart.js alla versione 4.5.0 per migliorare le prestazioni di rendering dei grafici, migliorare le funzionalità visive e risolvere le vulnerabilità di sicurezza nel dashboard di amministrazione e nei moduli di reporting.

  _AC-14304, AC-15133 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/768b4442), [Contributo codice GitHub](https://github.com/magento/magento2/commit/657f983e)_

- **Aggiornamento libreria di caricamento file alla versione 4.13.4**

  Aggiornamento della libreria di caricamento file alla versione 4.13.4 per migliorare le funzionalità di caricamento dei file, l’esperienza utente e le vulnerabilità di sicurezza nella gestione dei file nell’interfaccia di amministrazione di Adobe Commerce e nei componenti front-end.

  _AC-14307 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/eb491c05)_

- **jLibreria di convalida query aggiornata alla versione 1.21.0**

  Aggiornamento della libreria jQuery Validate alla versione 1.21.0 per migliorare le funzionalità di convalida dei moduli, migliorare l’esperienza utente e garantire una compatibilità moderna dei browser in tutti i moduli di Adobe Commerce, sia nelle interfacce amministratore che front-end.

  _AC-14403 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **jLibreria interfaccia utente Query aggiornata alla versione 1.14.1**

  Aggiornamento della libreria dell’interfaccia utente jQuery alla versione 1.14.1 per migliorare i widget dell’interfaccia utente, migliorare l’accessibilità e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia di amministrazione e front-end di Adobe Commerce.

  _AC-14417 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/77c589a6)_

- **Preprocessore CSS Less.js aggiornato alla versione 4.2.2**

  Il preprocessore CSS Less.js è stato aggiornato alla versione 4.2.2 per migliorare le prestazioni di compilazione CSS, migliorare il supporto della sintassi e modernizzare il processo di creazione del tema in tutti i temi front-end e amministratore di Adobe Commerce.

  _AC-14418 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Libreria fuso orario del momento aggiornata alla versione 0.5.43**

  Aggiornamento della libreria del fuso orario del momento (`moment-timezone-with-data.js`) alla versione 0.5.43 per migliorare le funzionalità di gestione del fuso orario, aggiornare i dati del fuso orario con le ultime modifiche al database del fuso orario IANA e migliorare la precisione dell&#39;elaborazione di data e ora in tutte le operazioni internazionali e multitasking di Adobe Commerce.

  _AC-14419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Libreria dell&#39;utilità Underscore.js aggiornata alla versione 1.13.7**

  Aggiornamento della libreria dell’utility Underscore.js alla versione 1.13.7 per migliorare le funzionalità di programmazione di JavaScript, le prestazioni di manipolazione dei dati e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia Adobe Commerce frontend e amministratore.

  _AC-14420 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

### Sicurezza

#### Protezione avanzata del controllo degli accessi multisito

Questo aggiornamento offre una protezione avanzata completa degli elenchi di controllo di accesso (ACL) multisito nell’amministratore Adobe Commerce, risolvendo problemi di autorizzazione noti e precedentemente sconosciuti nella configurazione di controllo di accesso multisito. Gli utenti amministratori con accesso a siti web o store specifici non possono più visualizzare o modificare i dati che appartengono ad altri siti web o store in una distribuzione multisito.

_AC-11899_

#### Convalida CAPTCHA ora applicata per le API REST e GraphQL

Quando CAPTCHA (o reCAPTCHA) è abilitato per il modulo Crea account, ora viene applicata la stessa convalida CAPTCHA per la creazione di account cliente tramite API REST e GraphQL.

_AC-16245_

#### Sono state migliorate le prestazioni di richieste asincrone/in blocco

Questa correzione rapida per la riduzione delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la patch di sicurezza APSB25-08, ripristinando i tempi di esecuzione previsti.

_AC-14078 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Configurazione semplificata dell’autenticazione a due fattori

Gli utenti amministratori ora devono configurare solo uno dei provider 2FA abilitati per l’esercente (ad esempio, Google Authenticator o U2F) per accedere al pannello di amministrazione. Ulteriori provider abilitati possono essere configurati in un secondo momento in base alle esigenze. In precedenza, quando erano abilitati più provider 2FA, a ogni utente amministratore veniva richiesto di configurare tutti i provider abilitati prima che potesse accedere, creando attrito per gli utenti che non avevano accesso a tutti i fattori.

_AC-8253 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/71e7936b)_

### Spedizione

#### Migrazione dell’integrazione USPS alle API RESTful USPS

Per rispettare l’annunciato ritiro delle API legacy degli strumenti web da parte di USPS, Adobe Commerce ha migrato la sua integrazione USPS alle nuove API RESTful USPS.

Miglioramenti principali:

- Supporto di API doppie: gli utenti amministratori ora possono scegliere tra l’API legacy degli strumenti web e la nuova API RESTful USPS tramite le impostazioni di configurazione.
- Aggiornamento autenticazione: utilizza OAuth 2.0 per l’accesso API sicuro.
- Formato dati migliorato: utilizza JSON invece di XML per una comunicazione più pulita ed efficiente.
- Nuovi campi amministratore:
   - URL REST gateway (in base alla modalità: Sviluppo o Live)
   - ID client e segreto
   - Tipo di conto, numero di conto
   - CRID, MID, codice di identificazione dell’Mailer
   - AES/ITN per spedizioni internazionali
   - Metodi di spedizione consentiti specifici per REST

Questa migrazione garantisce che Adobe Commerce rimanga conforme agli standard USPS, migliori l’affidabilità del sistema e integrazioni di spedizione a prova di futuro per gli esercenti.

_AC-13257_

#### Migrazione dell’integrazione DHL alle API RESTful di MyDHL

L&#39;integrazione DHL shipping integrata ora supporta le API RESTful di MyDHL, pur preservando la compatibilità con l&#39;API XML DHL Express legacy. I commercianti possono scegliere quale API DHL utilizzare nell’amministratore, beneficiando delle moderne funzionalità REST senza interrompere le impostazioni esistenti basate su XML.

_AC-13258_

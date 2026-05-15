---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Elementi di rilievo di Adobe Commerce (v2.4.9)

## Elementi di rilievo nella versione v2.4.9

Le seguenti caratteristiche si applicano alla versione Adobe Commerce 2.4.9.

### Modifiche REST API

#### Controllo dell’ereditarietà della galleria di prodotti API REST a livello di visualizzazione archivio

Se si aggiorna un prodotto tramite API REST in un ambito di archivio, le immagini e i video del prodotto non ereditano più le modifiche dall&#39;ambito globale quando `media_gallery_entries` viene omesso dal payload o impostato su `NULL`. È ora possibile ripristinare l’ereditarietà dell’ambito per immagini e video di prodotto tramite API REST impostando il campo corrispondente su `NULL`.

Quando aggiorni i prodotti tramite API REST a livello di visualizzazione store:

- Se si omette `media_gallery_entries` o lo si imposta su NULL, verrà mantenuta l&#39;ereditarietà dalla raccolta predefinita/globale.
- Per ripristinare l&#39;ereditarietà per attributi specifici della raccolta (ad esempio `label`, `position`, `disabled`, `video_title`, `video_description`), impostare questi campi su NULL all&#39;interno dell&#39;array `media_gallery_entries`.

Questa modifica consente alle viste archivio di mantenere o ripristinare facilmente i valori predefiniti della raccolta, riducendo la confusione e rendendo più coerente la gestione della raccolta.

_ACP2E-4358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Modifiche all’API GraphQL

#### La mutazione GraphQL `clearCart` è ora disponibile in Magento Open Source

La mutazione GraphQL [clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) è ora disponibile per tutti gli utenti di Magento Open Source. In precedenza, questa mutazione era accessibile solo in Adobe Commerce.

_AC-16683 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### Errori più descrittivi dalla mutazione GraphQL `applyGiftCardToCart`

Gestione ottimizzata degli errori per la mutazione `applyGiftCardToCart`. La mutazione ora restituisce messaggi di errore specifici per casi quali gift card scadute o a saldo zero, migliorando l’esperienza dell’acquirente. Inoltre, il backend impedisce l&#39;applicazione di gift card aggiuntive agli ordini già gratuiti.

_LYNX-787_

#### La nuova mutazione GraphQL `clearWishlist` rimuove tutti gli elementi della lista dei desideri contemporaneamente

Aggiunta di una mutazione `clearWishlist` che rimuove tutti gli elementi da una lista dei desideri in una singola chiamata.

_LYNX-790_

#### Nuova mutazione GraphQL `exchangeExternalCustomerToken` per l&#39;autenticazione basata sull&#39;integrazione

È stata introdotta una nuova mutazione GraphQL `exchangeExternalCustomerToken` che autentica gli utenti tramite un token di integrazione e restituisce sia il token cliente che i dati cliente associati.

_LYNX-815_


#### Le nuove query GraphQL restituiscono gli ID dei gruppi di clienti, dei segmenti e delle regole del carrello applicati

Le nuove query GraphQL restituiscono il codice `uid` del gruppo di clienti, dei segmenti cliente e delle regole del carrello applicati.

_LYNX-867_

#### Le opzioni relative ai regali vengono cancellate automaticamente quando il carrello viene svuotato

È stato risolto un problema a causa del quale le opzioni regalo persistevano su un carrello vuoto dopo la rimozione di tutti gli elementi. Le opzioni relative ai regali ora vengono cancellate automaticamente quando il carrello viene svuotato, in modo da corrispondere al comportamento esistente per i coupon.

_LYNX-786_

#### Le opzioni regalo si uniscono in modo coerente quando i carrelli ospiti e clienti vengono combinati

Gestione migliorata delle opzioni regalo durante le unioni del carrello per garantire un’esperienza utente più coerente. Le opzioni relative ai regali ora seguono una logica di unione con priorità, che impedisce sostituzioni non intenzionali quando un utente ospite effettua l’accesso e il suo carrello viene unito a un carrello clienti esistente.

_LYNX-788_

#### Nuovo campo `grand_total_excl_tax` nella risposta di GraphQL `OrderTotal`

Un nuovo campo, `OrderTotal.grand_total_excl_tax`, è stato aggiunto alla risposta dell&#39;ordine di GraphQL. Questo campo fornisce il totale complessivo dell’ordine al netto delle imposte, semplificando l’accesso ai totali al netto delle imposte direttamente dall’API.

Vantaggi:

- Recupera facilmente il totale complessivo escluse le imposte per qualsiasi ordine tramite GraphQL.
- Semplifica l&#39;integrazione con i sistemi esterni che richiedono totali fiscali esclusivi.
- Riduce la necessità di calcoli personalizzati sul lato client.

_LYNX-892_

#### Gli ordini storici mostrano i dettagli per i prodotti che non sono più disponibili

Gli ordini storici ora visualizzano i dettagli completi del prodotto per le voci anche dopo che il prodotto è esaurito, in modo che i clienti e i commercianti conservino una registrazione completa di ciò che è stato acquistato.

_LYNX-913_

#### Convalida reCAPTCHA aggiunta a `updateCustomer`, `updateCustomerV2` e `contactUs` mutazioni GraphQL

Quando reCAPTCHA è abilitato per i moduli della vetrina corrispondenti, le mutazioni GraphQL `updateCustomer`, `updateCustomerV2` e `contactUs` ora applicano la stessa convalida, contribuendo a prevenire gli abusi automatizzati tramite l&#39;API.

_LYNX-941_

#### Convalida reCAPTCHA aggiunta alla mutazione GraphQL `applyCouponsToCart`

Quando reCAPTCHA è abilitato per il modulo coupon, la mutazione GraphQL `applyCouponsToCart` ora applica la stessa convalida, impedendo l&#39;enumerazione del codice coupon tramite l&#39;API.

_LYNX-942_

#### Il campo `customer_id` dell’API GraphQL B2B è stato ripristinato e completamente supportato

Il campo `customer_id` nell&#39;API GraphQL B2B è stato ripristinato e ora restituisce il valore corretto nelle query e mutazioni di gestione della società. In precedenza, il campo era obsoleto e restituiva `null`, il che ne limitava l&#39;utilità per le integrazioni B2B.

_LYNX-955_

### Interfaccia utente amministratore

#### Menu Azioni per la griglia delle regole dei prezzi di catalogo

La griglia **Regole prezzo catalogo** in Commerce Admin ora include un menu **Azioni**, che consente agli esercenti di attivare, disattivare o eliminare più regole contemporaneamente. In questo modo la gestione delle regole di prezzo del catalogo è in linea con le azioni collettive esistenti disponibili per **Regole di prezzo del carrello**, riducendo notevolmente il tempo necessario per gestire set di regole di grandi dimensioni.

_AC-13916_

#### Anteprima visualizzazione mobile per staging contenuto

La funzione di anteprima dell’area di gestione temporanea in Admin ora esegue il rendering accurato delle anteprime dei dispositivi mobili simulate dal browser, in modo che i commercianti possano vedere come apparirà un aggiornamento in staging su un dispositivo mobile prima che venga pubblicato.

_ACP2E-3397 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La nuova configurazione amministratore controlla il comportamento di unione guest e carrello clienti all’accesso

I commercianti possono ora scegliere come unire gli articoli del carrello quando un ospite effettua l’accesso e dispone già di un carrello clienti:

- **Priorità ospite**: utilizza la quantità del carrello ospiti.
- **Priorità cliente**: utilizzare la quantità del carrello cliente.
- **Unisci quantità** (impostazione predefinita) - Somma entrambe le quantità.

Configura questo comportamento in **Archivi** > **Configurazione** > **Vendite** > **Pagamento**, in **Preferenza unione carrello**. L’impostazione si applica a tutti i tipi di prodotto, fornendo ai commercianti il pieno controllo su come i carrelli ospiti e clienti vengono combinati all’accesso.

_LYNX-889_

### Braintree

#### Pagamento rapido

- **Offerte promozionali nel foglio paga Google Pay Express**

  Il foglio paga Google Pay Express ora supporta i codici promozionali e di offerta. Gli acquirenti possono applicare, visualizzare e rimuovere le promozioni del carrello Commerce direttamente all&#39;interno del Google Pay sheet, in modo che i clienti di pagamento rapido ricevano gli stessi sconti e incentivi dei flussi di pagamento standard.

  _BUNDLE-3476_

- **Offerte promozionali nel foglio paga Apple Pay Express**

  Il foglio paga Apple Pay Express ora supporta i codici promozionali e di offerta. Gli acquirenti possono applicare un coupon direttamente all’interno del foglio di pagamento di Apple, in modo che gli utenti di checkout rapidi possano beneficiare degli stessi sconti e campagne dei flussi di pagamento standard.

  _BUNDLE-3477_

- **Apple Pay su Chrome e Firefox**

  Apple Pay ora può essere utilizzato su Chrome e Firefox, non solo su Safari. Quando Apple Pay Express è abilitato, i pulsanti Apple Pay sono disponibili nelle pagine PDP, mini-carrello, carrello e pagamento e i clienti completano il pagamento digitalizzando un codice con il proprio iPhone.

  _BUNDLE-3478_

- **Callback di spedizione lato server per PayPal Express**

  Il callback di spedizione PayPal Express è stato spostato dal lato client a quello server. Questo fornisce metodi di spedizione dinamici, calcoli dei costi in tempo reale e dettagli precisi a livello di carrello direttamente nel modale PayPal, migliorando l&#39;affidabilità e ponendo le basi per funzioni future come il supporto del modulo Contatto, i flussi di switch delle app e Venmo Express.

  _BUNDLE-3479_

- **Modulo di contatto PayPal per il pagamento rapido del commerciante statunitense**

  È stato introdotto un nuovo modulo PayPal Contact per i commercianti statunitensi. Quando abilitato, gli acquirenti che utilizzano PayPal Express possono visualizzare e aggiornare l&#39;indirizzo e-mail e il numero di telefono condivisi con il commerciante direttamente all&#39;interno del modale PayPal durante i flussi espressi (PDP, mini-carrello, carrello, pagamento espresso). I recapiti selezionati vengono quindi memorizzati nell&#39;ordine Commerce.

  _BUNDLE-3480_

#### Metodi di pagamento

- **Supporto di tipo carta ELO per i pagamenti Braintree**

  È stato aggiunto il supporto per il tipo di carta ELO in Braintree Payments. Gli amministratori possono abilitare ELO nella configurazione della carta di credito e i clienti possono pagare con le carte ELO al momento del pagamento.

  _BUNDLE-3464_

- **BLIK metodo di pagamento locale per acquirenti polacchi**

  BLIK è stato aggiunto come nuovo metodo di pagamento locale per gli acquirenti polacchi. Ciò consente di effettuare pagamenti BLIK sicuri e basati su banche all&#39;interno del flusso LPM (Local Payment Methods) di Braintree esistente, migliorando la comodità di pagamento e la conversione per i clienti in Polonia.

  _BUNDLE-3481_

- **Pagamento su fattura — nuovo metodo di pagamento BNPL per la Germania**

  Aggiunta di [!DNL Pay Upon Invoice] come nuovo metodo di pagamento locale per gli acquirenti tedeschi. [!DNL Pay Upon Invoice] è un&#39;opzione Buy Now, Pay Later (BNPL) fornita da PayPal e Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) che consente ai clienti di ricevere prima le merci e di pagare la fattura entro 30 giorni senza bisogno di un conto PayPal. Poiché non si tratta di un pagamento istantaneo, la finalizzazione degli ordini è guidata da un webhook lato server di PayPal.

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

#### Dopo il refactoring dell’archiviazione hash SRI, la pagina viene caricata più rapidamente in store con più temi e impostazioni internazionali

L&#39;archiviazione hash SRI ora genera file separati per area, tema e impostazioni locali, invece di un singolo file `sri-hashes.json` di grandi dimensioni. Questa modifica assicura che per ogni pagina venga caricato solo il file hash pertinente, migliorando i tempi di caricamento delle pagine e riducendo l’utilizzo di memoria negli archivi con più temi o impostazioni internazionali.

_AC-16113 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Maggiore compatibilità con PHPUnit 12

La dipendenza del Compositore Adobe Commerce è stata aggiornata a `phpunit/phpunit` 12.x. Tutti i test vengono aggiornati per la compatibilità, migliorando la sicurezza e l&#39;allineamento con le funzioni PHPUnit più recenti. Questo aggiornamento mantiene Adobe Commerce pronto per le future versioni PHP e PHPUnit.

_AC-14808_

#### Maggiore compatibilità con RabbitMQ 4.2

RabbitMQ 4.2 è ora un broker di messaggi supportato. Questo aggiornamento è un percorso di compatibilità a breve termine che consente ai commercianti che si basano sul protocollo AMQP di continuare a utilizzare RabbitMQ prima della fine del supporto di RabbitMQ 4.1 nel febbraio 2026, senza una migrazione immediata a STOMP. Per implementazioni a lungo termine, utilizza Apache ActiveMQ Artemis come sostituto a lungo termine di RabbitMQ.

_AC-16117_

#### Apache ActiveMQ Artemis è la soluzione sostitutiva a lungo termine per RabbitMQ

Apache ActiveMQ Artemis è il broker di messaggi consigliato a lungo termine per Adobe Commerce, guidato dai rischi di fine del supporto associati a RabbitMQ 4.1. ActiveMQ Artemis è completamente supportato nelle versioni da 2.4.6 a 2.4.9 di Commerce. In Adobe Commerce Cloud, viene fornito come AWS ActiveMQ per implementazioni native per il cloud. È possibile configurare utenti consumer e autori della coda per l&#39;utilizzo di STOMP.


Le installazioni esistenti di RabbitMQ 4 rimangono compatibili per i commercianti che preferiscono continuare a utilizzare il servizio corrente di coda messaggi a breve termine. Vedere [Aggiungere compatibilità con RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42) sopra. Pianifica una migrazione ad ActiveMQ Artemis per il supporto a lungo termine.

_AC-14558_

#### Aggiungi supporto per Valkey 9.x

Adobe Commerce 2.4.9 estende il supporto per Valkey come back-end della cache compatibile con Redis:

- **Valkey 9.x**: supporto completo introdotto in Adobe Commerce 2.4.9, inclusa la parità completa dei comandi CLI con Redis e opzioni di configurazione Admin e Cloud aggiornate per una configurazione senza problemi. Questo lavoro è guidato dalle modifiche alla fine del supporto e delle licenze di Redis 7.2, che offrono ai commercianti un&#39;alternativa affidabile e completamente supportata a Redis.

_AC-14103, AC-14604, AC-16122_

#### Aggiunta del supporto per OpenSearch 3.x

Adobe Commerce 2.4.9 è completamente compatibile con OpenSearch 3.x e l’ultima versione secondaria è ora il motore di ricerca consigliato. I commercianti possono beneficiare di prestazioni, sicurezza e supporto a lungo termine migliorati, mantenendo al contempo la compatibilità con le versioni precedenti di OpenSearch 2.x.

_AC-11846, AC-16403_

#### Aggiunta del supporto per MariaDB 11.8 e 12.x

Le versioni 11.8 e 12.x di MariaDB sono ora supportate e consentono ai commercianti di adottare le ultime versioni per migliorare le prestazioni SQL e la stabilità della piattaforma a lungo termine.

_AC-16533_

### PHP e Composer

#### Compatibilità PHP 8.5

Adobe Commerce 2.4.9 ora supporta PHP 8.5 e PHP 8.4, consentendoti di eseguire il tuo store sulle ultime versioni PHP sicure e conformi. Tutte le funzioni di base, le estensioni in bundle (tra cui Page Builder, B2B, Braintree e altro) e i servizi SaaS di Adobe sono compatibili con PHP 8.5.

- PHP 8.5 e 8.4 sono completamente supportati.
- PHP 8.3 è consentito solo a scopo di aggiornamento (non consigliato per la produzione).
- Garantisce la conformità PCI e l&#39;installazione Adobe Commerce a prova di futuro.

_AC-15615_

#### Supporto PHP 8.2 rimosso

A partire da Adobe Commerce 2.4.9, PHP 8.2 non è più supportato. La piattaforma ora esegue il targeting di PHP 8.3 e versioni successive, con il codice di base, le dipendenze e gli strumenti aggiornati per funzionare in modo pulito e affidabile su PHP 8.4 e 8.5.

_AC-15758_

#### Compatibilità con Composer 2.9 verificata

Adobe Commerce 2.4.9 è completamente compatibile con Composer 2.x, incluso Composer 2.9. Viene mantenuta la compatibilità con le versioni precedenti di Composer 2.x, garantendo una build e un’esperienza di implementazione stabile per i commercianti e gli sviluppatori che utilizzano le versioni più recenti di Composer.

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

A partire dalla versione Adobe Commerce 2.4.9, il componente Zend_Cache obsoleto è stato sostituito dal componente Symfony Cache. Questo aggiornamento migliora le prestazioni della cache e la manutenibilità e garantisce la compatibilità a lungo termine con PHP 8.x e gli aggiornamenti futuri della piattaforma. I back-end della cache e i comandi di gestione della cache esistenti rimangono completamente supportati, senza la necessità di apportare modifiche per le integrazioni correnti.

_AC-15823_

#### L’editor WYSIWYG è migrato da TinyMCE a HugeRTE

A causa della fine del supporto di TinyMCE 5 e 6 e delle incompatibilità di licenza con TinyMCE 7, l&#39;editor WYSIWYG di Adobe Commerce è stato migrato all&#39;editor [HugeRTE](https://hugerte.org/) open-source. Questa migrazione garantisce che Adobe Commerce rimanga conforme alle licenze open source, evita le vulnerabilità TinyMCE 6 note e offre un’esperienza di modifica moderna e supportata per commercianti e sviluppatori.

_AC-14568_

#### L&#39;implementazione MVC nativa sostituisce Laminas MVC

Adobe Commerce ha introdotto un&#39;implementazione MVC nativa, sostituendo la precedente versione di Laminas MVC, per garantire compatibilità e stabilità a lungo termine oltre PHP 8.5. Questa modifica migliora le prestazioni, riduce le dipendenze esterne e fornisce una base più pronta per il futuro per Commerce.

_AC-15160_

#### Supporto ufficiale Symfony 7.4 LTS

Con l’aggiornamento alla piattaforma Adobe Commerce 2.4.9, tutte le dipendenze di Symfony sono state aggiornate alle versioni più recenti di Symfony LTS 7.4. Tutte le classi personalizzate che estendono le classi principali di Symfony hanno aggiornato le dichiarazioni dei tipi e le firme dei metodi in linea con i requisiti di Symfony più recenti, evitando problemi di compatibilità e garantendo una transizione fluida ai componenti framework aggiornati.

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

#### Convalida CAPTCHA ora applicata per le API REST e GraphQL

Quando CAPTCHA (o reCAPTCHA) è abilitato per il modulo Crea account, ora viene applicata la stessa convalida CAPTCHA per la creazione di account cliente tramite API REST e GraphQL.

_AC-16245_

#### Sono state migliorate le prestazioni di richieste asincrone/in blocco

Questa correzione rapida per la riduzione delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la patch di sicurezza APSB25-08, ripristinando i tempi di esecuzione previsti.

_AC-14078 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Configurazione semplificata dell’autenticazione a due fattori

Gli utenti amministratori ora devono configurare solo uno dei provider 2FA abilitati per l’esercente (ad esempio, Google Authenticator o U2F) per accedere al pannello di amministrazione. Ulteriori provider abilitati possono essere configurati in un secondo momento in base alle esigenze. In precedenza, quando erano abilitati più provider 2FA, a ogni utente amministratore veniva richiesto di configurarli tutti prima di poter accedere, creando attrito per gli utenti che non avevano accesso a ogni provider.

_AC-8253 - [Contributo codice GitHub](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

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

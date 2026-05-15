---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Elementi di rilievo di Magento Open Source (v2.4.9)

## Elementi di rilievo nella versione v2.4.9

Le seguenti caratteristiche sono valide per la versione 2.4.9 di Magento Open Source.

### API

#### Aggiunta della possibilità di mantenere l’ereditarietà della galleria di prodotti nell’API REST durante l’aggiornamento di un prodotto nel livello di visualizzazione store

L’aggiornamento del prodotto tramite API REST in un ambito di archivio non fa più sì che le immagini e i video del prodotto ereditino le modifiche dall’ambito globale se media_gallery_entries viene omesso dal payload o impostato su NULL per impedire eventuali modifiche nella galleria di prodotti in tale ambito. Inoltre, ora è possibile ripristinare l’ereditarietà dell’ambito per immagini e video di prodotto tramite API REST impostando il campo corrispondente su NULL.

_ACP2E-4358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Vaulting di Google Pay tramite l&#39;area del conto

In Adobe Commerce 2.4.9, i clienti possono ora eseguire il vaulting delle proprie carte Google Pay tramite l’area del conto quando Google Pay Vault è abilitato in Braintree. Le carte vendute appaiono in metodi di pagamento memorizzati, possono essere utilizzate per acquisti futuri al momento del pagamento e possono essere eliminate dal cliente. Questo estende il supporto del vaulting oltre le schede e da PayPal a Google Pay.

_BUNDLE-3459_

#### RTAU (Real Time Account Updater)

La funzione Real Time Account Updater (RTAU) in Adobe Commerce 2.4.9 per Braintree assicura che i dettagli archiviati di Visa, Mastercard e Discover vengano aggiornati automaticamente alla scadenza o sostituzione delle schede. In questo modo si riducono al minimo i pagamenti non riusciti, si mantiene aggiornato Magento Vault e si ignorano i tipi non supportati (prepagati, Apple Pay, Google Pay) senza errori.

_BUNDLE-3462_

#### Supporto di tipo carta ELO per i pagamenti con carta Braintree

In Adobe Commerce 2.4.9, il supporto per il tipo di carta ELO è stato aggiunto a Braintree Payments. Gli amministratori possono ora abilitare ELO nella configurazione della carta di credito e i clienti possono effettuare con successo gli ordini utilizzando le carte ELO al momento del pagamento, garantendo transazioni senza soluzione di continuità tramite Braintree.

_BUNDLE-3464_

#### Paga su fattura

Per Adobe Commerce 2.4.9 (estensione Braintree), è stato aggiunto un nuovo metodo di pagamento locale &quot;Paga su fattura&quot; per gli acquirenti tedeschi. Pay Upon Invoice è un&#39;opzione Buy Now, Pay Later (BNPL) fornita da PayPal + Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) che consente ai clienti di ricevere prima le merci e pagare la fattura entro 30 giorni, senza bisogno di un conto PayPal. Poiché non si tratta di un pagamento immediato, la finalizzazione degli ordini è guidata da un webhook lato server di PayPal.

_BUNDLE-3475_

#### Aggiungi offerte al foglio paga di Google Pay Express

Per l’estensione Braintree in Adobe Commerce 2.4.9, il foglio di pagamento Google Pay Express ora supporta i codici promozionali/offerta. Gli acquirenti possono applicare, visualizzare e rimuovere le promozioni Magento Cart direttamente all&#39;interno del Google Pay sheet, garantendo ai clienti di pagamento rapido gli stessi sconti e incentivi dei flussi di pagamento standard.

_BUNDLE-3476_

#### Aggiungi offerte al foglio paga di Apple Pay Express

Per l’estensione Braintree in Adobe Commerce 2.4.9, il foglio di pagamento Apple Pay Express ora supporta i codici promozionali/offerta. Gli acquirenti possono applicare un coupon direttamente all’interno del foglio di pagamento di Apple, in modo che gli utenti di checkout rapidi possano beneficiare degli stessi sconti e campagne dei flussi di pagamento standard.

_BUNDLE-3477_

#### Pagare con Apple Pagare su Chrome e Firefox

Per l’estensione Braintree in Adobe Commerce 2.4.9, ora Apple Pay può essere utilizzato su Chrome e Firefox, non solo su Safari. Quando Apple Pay Express è abilitato, i pulsanti Apple Pay sono disponibili nelle posizioni di vetrina supportate e i clienti completano il pagamento digitalizzando un codice con il proprio iPhone.

_BUNDLE-3478_

#### Callback spedizione lato server

Per l&#39;estensione Braintree in Adobe Commerce 2.4.9, il callback di spedizione PayPal Express è stato spostato dal lato client a quello server. Questo fornisce metodi di spedizione dinamici, calcoli dei costi in tempo reale e dettagli precisi a livello di carrello direttamente nel modale PayPal, migliorando l&#39;affidabilità e ponendo le basi per funzioni future come il supporto del modulo Contatto, i flussi di switch delle app e Venmo Express.

_BUNDLE-3479_

#### Modulo contatto PayPal

Per l’estensione Braintree in Adobe Commerce 2.4.9, viene introdotto un nuovo Modulo PayPal Contact per i commercianti degli Stati Uniti. Quando abilitato, gli acquirenti che utilizzano PayPal Express possono visualizzare e aggiornare l&#39;indirizzo e-mail e il numero di telefono condivisi con il commerciante direttamente all&#39;interno del modale PayPal durante i flussi espressi (PDP, mini-carrello, carrello, pagamento espresso). I dettagli di contatto selezionati vengono quindi memorizzati nell’ordine di Adobe Commerce.

_BUNDLE-3480_

#### BLIK (metodo di pagamento locale)

Per l’estensione Braintree in Adobe Commerce 2.4.9, è stato aggiunto BLIK come nuovo metodo di pagamento locale per gli acquirenti polacchi. Ciò consente di effettuare pagamenti BLIK sicuri e basati su banche all&#39;interno del flusso LPM (Local Payment Methods) di Braintree esistente, migliorando la comodità di pagamento e la conversione per i clienti in Polonia.

_BUNDLE-3481_

#### Criterio CSP aggiornamento integrazione cardinale

Per l’estensione Braintree in Adobe Commerce 2.4.9, Content Security Policy (CSP) è stato aggiornato per supportare i requisiti di integrazione Cardinal (3D Secure) più recenti. In questo modo, tutti gli script, gli iframe e le risorse correlate ospitati da Cardinal utilizzati durante i flussi 3D Secure saranno consentiti dai CSP del browser, evitando richieste bloccate ed esperienze di verifica/sfida interrotte.

_BUNDLE-3485_

### Framework

#### Libreria web-token/jwt-framework aggiornata all’ultima versione principale

Come parte del processo continuo di revisione della sicurezza, abbiamo valutato l’ultima versione principale del framework JWT per garantire la compatibilità futura e mantenere standard di sicurezza elevati. Non vi è alcun impatto sulle funzionalità esistenti in questa versione.

_AC-13209 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Parte 2] - Aggiorna tutta la libreria js e la dipendenza npm con l&#39;ultima versione disponibile

il supporto per la versione del compositore era disponibile solo nella versione 2.2.x del compositore. Ora il supporto è stato esteso anche alla versione 2.4.x.

_AC-13792 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Sostituire carlos-mg89/oauth con le funzioni native PHP

La libreria carlos-mg89/oauth di terze parti è stata sostituita con funzioni PHP OAuth native per migliorare la sicurezza, ridurre le dipendenze esterne e migliorare la stabilità della piattaforma.

_AC-14075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Aggiorna le librerie jquery/uppy e uppy all’ultima versione

Aggiornamento della libreria di caricamento file alla versione 4.13.4 per migliorare le funzionalità di caricamento dei file, l’esperienza utente e le vulnerabilità di sicurezza nella gestione dei file nell’interfaccia di amministrazione di Adobe Commerce e nei componenti front-end.

_AC-14307 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/eb491c05)_

#### Aggiorna la libreria jquery-validate alla versione più recente

Aggiornamento della libreria jQuery Validate alla versione 1.21.0 per migliorare le funzionalità di convalida dei moduli, migliorare l’esperienza utente e garantire una compatibilità moderna dei browser in tutti i moduli di Adobe Commerce, sia nelle interfacce amministratore che front-end.

_AC-14403 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Aggiorna la libreria jquery-ui alla versione più recente

Aggiornamento della libreria dell’interfaccia utente jQuery alla versione 1.14.1 per migliorare i widget dell’interfaccia utente, migliorare l’accessibilità e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia di amministrazione e front-end di Adobe Commerce.

_AC-14417 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Aggiorna la libreria less.js alla versione più recente

Il preprocessore CSS Less.js è stato aggiornato alla versione 4.2.2 per migliorare le prestazioni di compilazione CSS, migliorare il supporto della sintassi e modernizzare il processo di creazione del tema in tutti i temi front-end e amministratore di Adobe Commerce.

_AC-14418 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Aggiornamento della libreria moment-timezone-with-data.js alla versione più recente

Aggiornamento della libreria Moment Timezone alla versione 0.5.43 per migliorare le funzionalità di gestione del fuso orario, aggiornare i dati del fuso orario con le ultime modifiche al database del fuso orario IANA e migliorare la precisione dell’elaborazione di data e ora in tutte le operazioni internazionali e multitfuso Adobe Commerce.

_AC-14419 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Aggiornamento della libreria underscore.js alla versione più recente

Aggiornamento della libreria dell’utility Underscore.js alla versione 1.13.7 per migliorare le funzionalità di programmazione di JavaScript, le prestazioni di manipolazione dei dati e garantire una compatibilità moderna del browser per tutti i componenti dell’interfaccia Adobe Commerce frontend e amministratore.

_AC-14420 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Aggiorna la versione allure-framework/allure-phpunit a 3 e rimuovi la dipendenza nativa in 2.4.9-alpha1

In Adobe Commerce 2.4.9, la dipendenza allure-framework/allure-phpunit è stata aggiornata alla versione principale 3, che aggiunge il supporto per PHP 8.4, PHP 8.5 e modernizza il nostro stack di reporting di test basato su allure. La dipendenza nativa richiesta in precedenza dalle versioni precedenti di Allure PHPUnit è stata rimossa laddove applicabile, semplificando la configurazione e la manutenzione.

_AC-14548 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Aggiorna la dipendenza chart.js alla versione più recente

La dipendenza chart.js viene aggiornata all’ultima versione 4.5.0.

_AC-15133 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Aggiunta del supporto ufficiale per Symfony 7.4 LTS e PHP 8.5 in Adobe Commerce 2.4.9

Con gli aggiornamenti alla piattaforma Adobe Commerce 2.4.9, tutte le dipendenze di Symfony utilizzate dal pacchetto magento/compositore sono state aggiornate alle versioni più recenti di Symfony LTS 7.4. In questo modo gli strumenti Compositore di Commerce vengono allineati alla linea corrente di Symfony LTS e vengono rimossi i vincoli di dipendenza precedenti relativi alle versioni precedenti di Symfony. Inoltre, tutte le classi personalizzate che estendono le classi principali di Symfony hanno aggiornato le dichiarazioni dei tipi e le firme dei metodi in linea con i requisiti di Symfony più recenti prima dell’aggiornamento ad Adobe Commerce 2.4.9. In questo modo si evitano problemi di compatibilità e si garantisce una transizione senza problemi ai componenti del framework aggiornati.

_AC-15170 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Assicurati che la mutazione clearCart GraphQL sia disponibile in Open Source

Con Adobe Commerce 2.4.9, la mutazione clearCart GraphQL è ora disponibile per tutti gli utenti di Open Source. In precedenza, questa mutazione era accessibile solo in Adobe Commerce, ma ora fa parte della funzionalità standard del carrello GraphQL anche per Open Source.
La documentazione relativa alla mutazione è stata aggiornata per riflettere la sua disponibilità in Open Source per la versione 2.4.9.
Consulta la [documentazione sulla mutazione di GraphQL clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9] Unione della logica guest e del carrello clienti tramite Configurazione amministratore

È stata introdotta una nuova opzione di configurazione amministratore per controllare il modo in cui i carrelli ospiti e clienti vengono uniti quando un acquirente effettua l’accesso. Questo miglioramento offre flessibilità per definire il comportamento di unione del carrello più adatto alle esigenze aziendali.

_LYNX-889_

#### [AC-2.4.9] Recupero ordini cronologici con prodotti esauriti

Gli ordini storici mostrano ora i dettagli del prodotto anche se sono esauriti.

_LYNX-913_

#### [AC-2.4.9] [CE] Implementa ReCaptcha per le mutazioni GraphQL mancanti

La convalida ReCaptcha viene aggiunta per le mutazioni updateCustomer, updateCustomerV2 e contactUs.

_LYNX-941_

### Altro

#### Captcha/reCAPTCHA non funziona per API/GraphQL

In Adobe Commerce 2.4.9, quando CAPTCHA (o reCAPTCHA) è abilitato per il modulo Crea account, ora viene applicata la stessa convalida CAPTCHA per la creazione di account cliente tramite API REST e GraphQL.

_AC-16245 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

#### il ramo braintree deve essere aggiornato con il supporto PHP 8.5

L&#39;estensione di pagamento Braintree è stata aggiornata per supportare la versione più recente di PHP 8.5 runtime, mantenendo la compatibilità con PHP 8.4.

_BUNDLE-3493_

#### Operazione di cancellazione della lista dei desideri

È stata aggiunta una nuova mutazione clearWishlist per supportare operazioni di massa, che consente di rimuovere tutti gli elementi da una lista dei desideri in una singola azione.

_LYNX-790_

#### Introduzione della mutazione exchangeExternalCustomerToken

È stata introdotta la nuova mutazione GraphQL exchangeExternalCustomerToken che autentica gli utenti tramite un token di integrazione e restituisce sia il token del cliente che i dati del cliente associati.

_LYNX-815_

#### [AC] Introduzione alle query GraphQL che restituiscono ID gruppo, segmenti e regole carrello applicati

query GraphQL esposte per recuperare l’uid codificato del gruppo di clienti, dei segmenti di clienti e delle regole del carrello applicati.

_LYNX-867_

#### [AC-2.4.9] Introduzione del campo OrderTotal.grand_total_excl_tax

Alla risposta dell&#39;ordine di GraphQL è stato aggiunto il nuovo campo OrderTotal.grand_total_excl_tax. Questo campo fornisce il totale complessivo dell’ordine al netto delle imposte, semplificando l’accesso ai totali al netto delle imposte direttamente dall’API.

Vantaggi:

- Recupera facilmente il totale complessivo escluse le imposte per qualsiasi ordine tramite GraphQL.
- Semplifica l&#39;integrazione con i sistemi esterni che richiedono totali fiscali esclusivi.
- Riduce la necessità di calcoli personalizzati sul lato client.

_LYNX-892_

### PCI, sicurezza

#### Refactoring dello storage SRI per una maggiore efficienza delle prestazioni

L’archiviazione hash SRI ora genera file separati per area, tema e lingua, invece di un singolo sri-hash.json di grandi dimensioni. Questa modifica assicura che per ogni pagina venga caricato solo il file hash pertinente, migliorando le prestazioni e riducendo l’utilizzo di memoria negli archivi con più temi o impostazioni internazionali.

_AC-16113 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

### Sicurezza

#### Migliorare le prestazioni delle richieste asincrone/in blocco

Correggi il degrado delle prestazioni negli endpoint web asincroni in blocco introdotti dopo la patch di sicurezza APSB25-08, con conseguente aumento dei tempi di esecuzione.

_AC-14078 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### È necessario configurare un solo provider 2FA abilitato per ogni utente

Gli utenti amministratori ora devono configurare solo uno dei provider 2FA abilitati per l’esercente (ad esempio, Google Authenticator o U2F) per accedere al pannello di amministrazione. Ulteriori provider abilitati possono essere configurati in un secondo momento in base alle esigenze. In precedenza, quando erano abilitati più provider 2FA (ad esempio, Google Authenticator e U2F), a ogni utente amministratore veniva richiesto di configurare tutti i provider abilitati prima che potesse accedere. Questo creava attriti per gli utenti che non avevano accesso a tutti i fattori (come una chiave hardware per U2F).

_AC-8253 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/71e7936b)_

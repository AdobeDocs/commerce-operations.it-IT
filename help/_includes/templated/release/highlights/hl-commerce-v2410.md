---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Elementi di rilievo di Adobe Commerce (v2.4.10)

## Elementi di rilievo in v2.4.10-alpha1

Le seguenti caratteristiche si applicano alla versione Adobe Commerce 2.4.10-alpha1.

### Braintree

#### Corsia

È stato aggiunto il supporto di Fastlane by PayPal per un&#39;esperienza di pagamento più veloce e sicura.
I clienti possono accettare di salvare i dati di pagamento e di spedizione per acquisti futuri più veloci.
I clienti di ritorno di Fastlane possono eseguire l’autenticazione utilizzando un codice occasionale e recuperare le informazioni salvate.
I clienti possono anche aggiungere o modificare le schede e gli indirizzi di spedizione salvati durante il pagamento.
Sono inoltre supportate le opzioni di configurazione e di stile delle corsie preferenziali.

_BUNDLE-3521_

#### Approfondimenti Braintree

Braintree Insights è stato introdotto per fornire ai commercianti funzionalità di reporting centralizzato sulle prestazioni dei pagamenti in Magento Admin.
Fornisce visibilità sui dati relativi a transazioni, liquidazione, rifiuto, rifiuto del gateway e metodi di pagamento.
Supporta il filtraggio per sito web, intervallo di date e intervalli giornalieri, settimanali o mensili.
Consente ai commercianti di importare fino a 13 mesi di dati storici sulle transazioni a fini di segnalazione.
Include la conservazione dei dati e la pulizia automatizzata per la conservazione fino a 3 anni dei dati delle transazioni.

_BUNDLE-3522_

#### Swish - Metodo di pagamento locale

Swish è stato introdotto come nuovo metodo di pagamento locale svedese nell’estensione Braintree Magento.
Swish è disponibile quando sono soddisfatte le configurazioni di pagamento, paese, valuta e commerciante svedesi richieste.
I clienti con un indirizzo di spedizione o fatturazione svedese possono completare i pagamenti utilizzando Swish durante il pagamento.
È stato aggiunto il supporto per flussi di pagamento Swish con esito positivo, annullato e non riuscito con risposte di pagamento appropriate.
Swish viene visualizzato solo quando tutte le condizioni di configurazione richieste sono soddisfatte.

_BUNDLE-3523_

#### Versione aggiornata alla versione v4.9.0

Aggiornamento del modulo Braintree dalla versione 4.8.0 alla versione 4.9.0.
L’aggiornamento include le modifiche e i miglioramenti più recenti del modulo Braintree.
È stato verificato che l&#39;elaborazione del pagamento e dell&#39;estrazione da Braintree continui a funzionare come previsto dopo l&#39;aggiornamento.
I flussi esistenti per il pagamento dei clienti e la creazione degli ordini rimangono funzionali con il modulo aggiornato.
È stato eseguito un test di regressione di base per garantire che l’aggiornamento non introducesse problemi

_BUNDLE-3530_

### Framework

#### [2.4.10-alpha1] Aggiornamento componenti piattaforma

Adobe Commerce 2.4.10-alpha1 include una serie di aggiornamenti delle dipendenze della piattaforma, miglioramenti della compatibilità, aggiornamenti della libreria front-end e correzioni di stabilità. In questa versione sono incluse le seguenti modifiche completate:

- Predis: aggiornamento di `predis/predis` da 2.x a 3.x, miglioramento della compatibilità con gli ambienti Redis e Valkey e mantenimento dell&#39;allineamento del client Redis con le ultime versioni di dipendenza supportate.
- Installazione di Magento Composer: è stato risolto un problema che consentiva a `magento-composer-installer` di uscire senza interruzioni senza completare il processo di installazione, migliorando l&#39;affidabilità delle installazioni basate su Composer.
- Knockout.js: aggiornato Knockout.js da 3.5.1 a 3.5.3, insieme agli aggiornamenti di convalida e compatibilità richiesti.
- Chart.js: aggiornamento di Chart.js da 4.5.0 a 4.5.1, inclusi i necessari aggiornamenti di convalida e compatibilità.
- Less.js: aggiornato Less.js da 4.2.2 a 4.6.4, con i relativi aggiornamenti di convalida e compatibilità.
- Aggiornamento: aggiornamento aggiornato da 5.0.0 a 5.2.0, incluse le modifiche di convalida e compatibilità necessarie.
- jQuery UI: Interfaccia utente jQuery aggiornata da 1.14.1 a 1.14.2, con i relativi aggiornamenti di convalida e compatibilità.
- Compatibilità PHP 8.5: è stato risolto un problema di obsolescenza di PHP 8.5 relativo a `chr()`, assicurando che la funzione sia fornita con valori di byte validi e migliorando la compatibilità con PHP 8.5.
- Ricerca nel catalogo: è stato risolto un problema che poteva causare l&#39;arresto della reindicizzazione `catalogsearch_fulltext` durante l&#39;elaborazione, migliorando l&#39;affidabilità dell&#39;indicizzazione della ricerca nel catalogo.
- js-cookie: aggiornato js-cookie da 3.0.5 a 3.0.7 o versione supportata applicabile, per soddisfare i requisiti di dipendenza e compatibilità.

_AC-17061_

#### Garantire la compatibilità di B2B 1.5.3-p1/1.5.4-alpha1 con 2.4.10-alpha1, 2.4.9-p1, 2.4.8-p6, 2.4.7-p11 e 2.4.6-p16

B2B 1.5.4-alpha1 è compatibile con le seguenti linee di rilascio Adobe Commerce: 2.4.9, 2.4.8, 2.4.7 e 2.4.6.

_AC-17100_

#### Aggiornamento e modernizzazione delle dipendenze NPM

Sono state aggiornate le seguenti dipendenze npm alle versioni protette più recenti per risolvere le vulnerabilità di sicurezza note:

- trattino basso
- imagemin-svgo
- globo
- server-static
- grugnito
- meno
- uglify-js
- contrassegnato
- clean-css
- minimista
- trim-newlines
- terser
- css-select
- n° controllo
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

Questi aggiornamenti delle dipendenze attenuano le vulnerabilità di sicurezza identificate, mantenendo al contempo le funzionalità esistenti dell’applicazione.

_AC-17372_

#### Aggiorna dipendenza NPM: underscore.js (1.13.7 → 1.13.8)

È stato aggiornato underscore.js da 1.13.7 a 1.13.8 per includere le più recenti correzioni a monte e i miglioramenti della stabilità.

_AC-17486 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Dipendenza NPM aggiornamento: imagemin-svgo (9.0.0 → 12.0.0)

imagemin-svgo è stato aggiornato dalla versione 9.0.0 alla versione 12.0.0 per includere le ultime correzioni a monte, gli aggiornamenti di sicurezza e i miglioramenti apportati alla ottimizzazione di SVG.

_AC-17657 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aggiorna dipendenza NPM: eslint-formatter-junit (8.40.0 → 9.0.1)

Aggiornamento di eslint-formatter-junit da 8.40.0 a 9.0.1 per includere le ultime correzioni a monte e i miglioramenti di compatibilità per il reporting ESLint.

_AC-17659 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aggiorna dipendenza NPM: glob (11.0.0 → 13.0.0)

Aggiornamento di glob dalla versione 11.0.0 alla versione 13.0.0 per includere le più recenti correzioni a monte, miglioramenti delle prestazioni e della compatibilità.

_AC-17660 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aggiorna dipendenza NPM: grunt-eslint (25.0.0 → 26.0.0)

È stato aggiornato grunt-eslint dalla versione 25.0.0 alla versione 26.0.0 per includere le ultime correzioni a monte e i miglioramenti della compatibilità.

_AC-17661 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Dipendenza NPM di aggiornamento: server-static (1.16.2 → 2.2.1)

Server-static aggiornato da 1.16.2 a 2.2.1 per includere le ultime correzioni a monte, gli aggiornamenti di sicurezza e i miglioramenti di compatibilità.

_AC-17662 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aggiornamento delle dipendenze NPM più recenti per Grunt e Meno

Aggiornamento di Grunt e Less alle versioni più recenti supportate, per migliorare la stabilità e la compatibilità della build front-end.

_AC-17663 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Aggiornamento delle dipendenze di sostituzione NPM alle versioni più recenti supportate

Sono state aggiornate più dipendenze di sostituzione NPM alle versioni più recenti supportate, migliorando la sicurezza, la stabilità della build e la compatibilità.

_AC-17664 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### [B2B] Gli ordini fornitore non vengono convertiti automaticamente in ordini cliente con ActiveMQ

È stato risolto un problema a causa del quale gli ordini fornitore inseriti tramite la vetrina con approvazione automatica abilitata non venivano convertiti automaticamente in ordini cliente quando si utilizzava ActiveMQ e si eseguivano i consumatori tramite cron (bin/magento cron:run). In precedenza, i messaggi venivano aggiunti alla coda di ActiveMQ ma non elaborati a meno che il consumer non venisse avviato manualmente tramite CLI. Con questa correzione, il consumatore ora elabora i messaggi come previsto dopo l’esecuzione del cron, garantendo una conversione diretta degli ordini per i commercianti B2B che utilizzano ActiveMQ.

_AC-17679_

#### Ottimizzazione della cache L2 di Symfony e compatibilità con le versioni precedenti della cache

Adobe Commerce 2.4.10 fornisce ora il supporto ottimizzato per la cache L2 di Symfony, mantenendo l’implementazione esistente della cache basata su Zend come impostazione predefinita.

I commercianti che desiderano utilizzare la cache di Symfony devono attivarla esplicitamente e aggiornare la configurazione della cache richiesta specifica per l’implementazione di Symfony L1/L2. I commercianti esistenti che continuano a utilizzare la cache basata su Zend non devono apportare modifiche alla configurazione.

Questo approccio a doppia cache offre ai commercianti la flessibilità di adottare la cache di Symfony in base ai loro requisiti, garantendo al contempo la compatibilità con le configurazioni e le implementazioni della cache esistenti.

_AC-17865_

### Altro

#### Gestione amministrativa delle sottoregioni nazionali (Stati e province)

Gli esercenti possono ora gestire le sottoregioni dei paesi (come stati e province) direttamente dall’interfaccia di amministrazione. Questa nuova funzione consente ai commercianti di:

- Visualizzare, aggiungere, modificare, disattivare o rimuovere aree per qualsiasi paese.
- Rendi immediatamente disponibili nuove aree geografiche come opzioni a discesa al momento del pagamento, nei moduli per gli indirizzi dei clienti e durante la creazione degli ordini di amministrazione, senza richiedere modifiche al codice.
- Modifica i nomi visualizzati dell&#39;area (inclusi i nomi localizzati) e i codici ISO.
- Disattiva le aree a cui fanno riferimento gli ordini, gli indirizzi o le regole fiscali esistenti (assicurando che i dati storici rimangano accurati), evitando al contempo di eliminarle definitivamente.
- Tutte le aree predefinite rimangono invariate e sono ora visibili e gestibili nella nuova interfaccia.

Questa funzione è completamente compatibile con le versioni precedenti e garantisce che il comportamento dell’indirizzo API e rivolto al cliente rimanga coerente.

_AC-16192_

#### Aggiornamento predis/predis da 2.x a 3.x

La libreria client Redis predis/predis è stata aggiornata dalla versione 2.x alla versione 3.x. Questo aggiornamento della versione principale è in linea con i più recenti standard di dipendenza, migliora la compatibilità e garantisce la manutenzione a lungo termine.

_AC-17101 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Aggiornare knockout.js dalla versione 3.5.1 alla versione 3.5.3

Aggiornamento della libreria knockout.js dalla versione 3.5.1 alla versione 3.5.3. Questo aggiornamento introduce correzioni di bug a monte e miglioramenti di stabilità per tutti i componenti dell’interfaccia utente che utilizzano associazioni di esclusione sia nella vetrina che nell’amministratore.

_AC-17366 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Aggiornamento vernice alla versione 9 per 2.4.10-alpha1

Adobe Commerce 2.4.10 è compatibile con Vernice versione 9.0.

_AC-17972_

---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%
---
# Elementi di rilievo di Magento Open Source (v2.4.10)

## Elementi di rilievo in v2.4.10-alpha1

Le seguenti caratteristiche si applicano alla versione Magento Open Source 2.4.10-alpha1.

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

### Altro

#### Aggiornamento predis/predis da 2.x a 3.x

La libreria client Redis predis/predis è stata aggiornata dalla versione 2.x alla versione 3.x. Questo aggiornamento della versione principale è in linea con i più recenti standard di dipendenza, migliora la compatibilità e garantisce la manutenzione a lungo termine.

_AC-17101 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Aggiornare knockout.js dalla versione 3.5.1 alla versione 3.5.3

Aggiornamento della libreria knockout.js dalla versione 3.5.1 alla versione 3.5.3. Questo aggiornamento introduce correzioni di bug a monte e miglioramenti di stabilità per tutti i componenti dell’interfaccia utente che utilizzano associazioni di esclusione sia nella vetrina che nell’amministratore.

_AC-17366 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/de7188da)_

---
source-git-commit: 56974b4ada65c21ce1303e4b93bd8acb9fe41b28
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---
# Elementi di rilievo di Magento Open Source (v2.4.9-beta1)

## Elementi di rilievo nella versione v2.4.9-beta1

Le seguenti caratteristiche sono valide per la versione Magento Open Source 2.4.9-beta1.

### API

#### Aggiunta della possibilità di mantenere l’ereditarietà della galleria di prodotti nell’API REST durante l’aggiornamento di un prodotto nel livello di visualizzazione store

L’aggiornamento del prodotto tramite API REST in un ambito di archivio non fa più sì che le immagini e i video del prodotto ereditino le modifiche dall’ambito globale se media_gallery_entries viene omesso dal payload o impostato su NULL per impedire eventuali modifiche nella galleria di prodotti in tale ambito. Inoltre, ora è possibile ripristinare l’ereditarietà dell’ambito per immagini e video di prodotto tramite API REST impostando il campo corrispondente su NULL

_ACP2E-4358 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Framework

#### Esamina la versione principale più recente di web-token/jwt-framework

Come parte del processo continuo di revisione della sicurezza, abbiamo valutato l’ultima versione principale del framework JWT per garantire la compatibilità futura e mantenere standard di sicurezza elevati. Non vi è alcun impatto sulle funzionalità esistenti in questa versione.

_AC-13209 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contributo codice GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Parte 2] - Aggiorna tutta la libreria js e la dipendenza npm con l&#39;ultima versione disponibile

il supporto per la versione del compositore era disponibile solo nella versione 2.2.x del compositore. Ora il supporto è stato esteso anche alla versione 2.4.x.

_AC-13792 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Sostituire carlos-mg89/oauth con le funzioni native PHP

La libreria carlos-mg89/oauth di terze parti è stata sostituita con funzioni PHP OAuth native per migliorare la sicurezza, ridurre le dipendenze esterne e migliorare la stabilità della piattaforma.

_AC-14075 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Esaminare la versione più recente di chart.js

Aggiornamento della libreria di grafici JavaScript Chart.js alla versione 4.4.8 più recente per migliorare le prestazioni di rendering dei grafici, migliorare le funzionalità visive e risolvere le vulnerabilità di sicurezza nel dashboard di amministrazione e nei moduli di reporting.

_AC-14304 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/768b4442)_

#### Esaminare la versione più recente di jquery/uppy e uppy

Aggiornamento della libreria di caricamento file alla versione 4.13.4 per migliorare le funzionalità di caricamento dei file, l’esperienza utente e le vulnerabilità di sicurezza nella gestione dei file nell’interfaccia di amministrazione di Adobe Commerce e nei componenti front-end.

_AC-14307 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/eb491c05)_

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

#### Aggiorna la versione allure-framework/allure-phpunit a 3 e rimuovi la dipendenza nativa in 2.4.9-alpha1

In Adobe Commerce 2.4.9, la dipendenza allure-framework/allure-phpunit è stata aggiornata alla versione principale 3, che aggiunge il supporto per PHP 8.4, PHP 8.5 e modernizza il nostro stack di reporting di test basato su allure. La dipendenza nativa richiesta in precedenza dalle versioni precedenti di Allure PHPUnit è stata rimossa laddove applicabile, semplificando la configurazione e la manutenzione.

_AC-14548 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Aggiorna la dipendenza chart.js alla versione più recente

La dipendenza chart.js viene aggiornata alla versione più recente 4.5.0

_AC-15133 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Aggiunta del supporto ufficiale per Symfony 7.4 LTS e PHP 8.5 in Adobe Commerce 2.4.9

Con gli aggiornamenti alla piattaforma Adobe Commerce 2.4.9, tutte le dipendenze di Symfony utilizzate dal pacchetto magento/compositore sono state aggiornate alle versioni più recenti di Symfony LTS 7.4. In questo modo gli strumenti Compositore di Commerce vengono allineati alla linea corrente di Symfony LTS e vengono rimossi i vincoli di dipendenza precedenti relativi alle versioni precedenti di Symfony. Inoltre, tutte le classi personalizzate che estendono le classi principali di Symfony hanno aggiornato le dichiarazioni dei tipi e le firme dei metodi in linea con i requisiti di Symfony più recenti prima dell’aggiornamento ad Adobe Commerce 2.4.9. In questo modo si evitano problemi di compatibilità e si garantisce una transizione senza problemi ai componenti del framework aggiornati.

_AC-15170 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### Altro

#### Captcha/reCaptha non funziona per API/GraphQl

In Adobe Commerce 2.4.9, quando CAPTCHA (o reCAPTCHA) è abilitato per il modulo Crea account, ora viene applicata la stessa convalida CAPTCHA per la creazione di account cliente tramite API REST e GraphQL.

_AC-16245 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

### Sicurezza

#### Migliorare le prestazioni delle richieste asincrone/in blocco

Correggi il degrado delle prestazioni negli endpoint web asincroni in blocco introdotti dopo la patch di sicurezza APSB25-08, con conseguente aumento dei tempi di esecuzione.

_AC-14078 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### È necessario configurare un solo provider 2FA abilitato per ogni utente

Gli utenti amministratori ora devono configurare solo uno dei provider 2FA abilitati per l’esercente (ad esempio, Google Authenticator o U2F) per accedere al pannello di amministrazione. Ulteriori provider abilitati possono essere configurati in un secondo momento in base alle esigenze. In precedenza, quando erano abilitati più provider 2FA (ad esempio, Google Authenticator e U2F), a ogni utente amministratore veniva richiesto di configurare tutti i provider abilitati prima che potesse accedere. Questo creava attriti per gli utenti che non avevano accesso a tutti i fattori (come una chiave hardware per U2F).

_AC-8253 - [Contributo codice GitHub](https://github.com/magento/security-package/commit/71e7936b)_

### Staging e anteprima

#### [Richiesta di funzionalità] Anteprima gestione temporanea contenuti nella visualizzazione per dispositivi mobili

La funzione di anteprima dell’area di gestione temporanea nel pannello di amministrazione ora consente di eseguire il rendering accurato delle anteprime dei dispositivi mobili simulate dal browser, fornendo una rappresentazione visiva di come l’aggiornamento dell’area di gestione temporanea verrà visualizzato su un dispositivo mobile.

_ACP2E-3397 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/520f9e30)_

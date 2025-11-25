---
title: Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.3
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.3

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

La versione di sicurezza Adobe Commerce 2.4.3-p3 fornisce correzioni di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.3. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Elementi di rilievo sulla sicurezza

* Le risorse ACL sono state aggiunte al magazzino.
* La sicurezza del modello di inventario è stata migliorata.



## Adobe Commerce 2.4.3-p2

La versione di sicurezza Adobe Commerce 2.4.3-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  La versione patch risolve anche la vulnerabilità gestita da `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` e `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Elementi di rilievo sulla sicurezza

* L’utilizzo della variabile e-mail è stato dichiarato obsoleto nella versione 2.3.4 come parte di una mitigazione del rischio sulla sicurezza in favore di una sintassi della variabile più rigida. Questo comportamento legacy è stato completamente rimosso in questa versione come continuazione della riduzione dei rischi per la sicurezza.

  Di conseguenza, i modelli e-mail o newsletter che funzionavano nelle versioni precedenti potrebbero non funzionare correttamente dopo l’aggiornamento ad Adobe Commerce 2.4.3-p2. I modelli interessati includono sostituzioni amministratore, temi, temi secondari e modelli da moduli personalizzati o estensioni di terze parti. La distribuzione potrebbe essere ancora interessata anche dopo l&#39;utilizzo dello [strumento di compatibilità per l&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) per correggere gli utilizzi obsoleti. Per informazioni sui potenziali effetti e le linee guida per la migrazione dei modelli interessati, vedere [Migrazione dei modelli di posta elettronica personalizzati](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/).

* I token di accesso OAuth e i token di reimpostazione della password ora sono crittografati quando sono memorizzati nel database. <!-- AC-520 1323-->

* La convalida è stata rafforzata per impedire il caricamento di estensioni di file non alfanumeriche. <!-- AC-479-->

* Swagger è ora disabilitato per impostazione predefinita quando Adobe Commerce è in modalità di produzione. <!-- AC-1450-->

* Gli sviluppatori possono ora configurare il limite di dimensione per gli array accettati dagli endpoint RESTful di Adobe Commerce in base agli endpoint. Vedi [Sicurezza API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Sono stati aggiunti meccanismi per limitare le dimensioni e il numero di risorse che un utente può richiedere tramite un’API web a livello di sistema e per ignorare i valori predefiniti nei singoli moduli. Questo miglioramento risolve il problema risolto da `MC-43048__set_rate_limits__2.4.3.patch`. Vedi [Sicurezza API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

La versione di sicurezza Adobe Commerce 2.4.3-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nella versione precedente (Adobe Commerce 2.4.3 e Magento Open Source 2.4.3). Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.


Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). La versione della patch fornisce anche correzioni di bug per le estensioni sviluppate dal fornitore [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) e [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html).

### Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Hotfix

Questa versione include il seguente hotfix e tutti gli hotfix rilasciati per la versione della patch precedente.

* Patch `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Per informazioni sia sulla patch che sul problema, consultare l&#39;articolo della Knowledge Base [Aggiornamento Adobe Commerce 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix).

### Elementi di rilievo sulla sicurezza

**ID sessione rimossi dal database**. Questa modifica al codice può causare modifiche non significative se i commercianti dispongono di personalizzazioni o estensioni installate che utilizzano gli ID di sessione non elaborati memorizzati nel database. <!-- MC-40976-->

**Accesso amministratore limitato alle cartelle di Media Gallery**. Le autorizzazioni predefinite di Media Gallery consentono ora solo le operazioni di directory (visualizzazione, caricamento, eliminazione e creazione) che sono esplicitamente consentite dalla configurazione. Gli utenti amministratori non possono più accedere alle risorse multimediali tramite Media Gallery caricate all&#39;esterno delle directory `catalog/category` o `wysiwyg`. Gli amministratori che desiderano accedere alle risorse multimediali devono spostarle in una cartella consentita in modo esplicito o modificare le impostazioni di configurazione. Vedere [Modifica autorizzazioni cartella Catalogo multimediale](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Limiti ridotti alla complessità delle query GraphQL**. La complessità massima delle query consentita per GraphQL è stata ridotta per evitare attacchi Denial of Service (DOS). Vedere [Configurazione della sicurezza di GraphQL](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**In questa versione sono state corrette le vulnerabilità recenti del test di penetrazione**. <!-- MC-42431-->

L&#39;espressione di origine non supportata `unsafe-inline` è stata rimossa dalla direttiva Content Security Policy `frame-ancestors`. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->

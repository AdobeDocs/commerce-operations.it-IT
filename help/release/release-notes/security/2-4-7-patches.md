---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.7
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p8

La versione di sicurezza di Adobe Commerce 2.4.7-p8 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{b2b-patches}}

Questa versione include i seguenti elementi di rilievo:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

## 2,4,7-p7

La versione di sicurezza di Adobe Commerce 2.4.7-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2,4,7-p6

La versione di sicurezza Adobe Commerce 2.4.7-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Supporto MariaDB** - Aggiunto supporto per MariaDB 10.11.

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Operazioni asincrone**—Operazioni asincrone limitate per l&#39;override degli ordini dei clienti precedenti.<!-- AC-13917 -->

## 2,4,7-p5

La versione di sicurezza Adobe Commerce 2.4.7-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Questa versione introduce anche il supporto per l&#39;estensione compatibile con HIPAA [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview).

>[!ENDSHADEBOX]

### Problemi noti

**Problema**: durante l&#39;installazione di 2.4.7-p5 con PHP 8.2 o versione successiva, il sistema installa `paypal/module-braintree` versione 4.7.0, destinata alla versione 2.4.8 o successiva. Per PHP 8.1, viene utilizzata la versione corretta di Braintree 4.6.1-p5. Questa mancata corrispondenza è dovuta alla dipendenza libera da `adobe-commerce/extensions-metapackage: ~2.0` nel metapacchetto. Ciò influisce sulla compatibilità e sul set di funzioni supportate per le distribuzioni PHP 8.2+.<!-- ACPLTSRV-6276) -->

Inoltre, per le versioni 2.4.7-p3, 2.4.7-p4 e 2.4.7-p5, può essere installata la versione dell’estensione Braintree 4.6.1-p5, mentre alcuni utenti si aspettano 4.6.1-p3 o p4, a causa di dipendenze più rigide precedenti rilasciate per consentire gli aggiornamenti dell’estensione all’interno di una linea di rilascio. <!-- AC-14430 -->

**Soluzione**: per assicurarsi di disporre della versione di Braintree corretta per la versione PHP, eseguire `composer update` per installare la versione appropriata in base alla dipendenza `adobe-commerce/extensions-metapackage:2.0.0`.

## 2,4,7-p4

La versione di sicurezza Adobe Commerce 2.4.7-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

La versione di sicurezza Adobe Commerce 2.4.7-p3 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.7-p2

La versione di sicurezza Adobe Commerce 2.4.7-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

La versione di sicurezza Adobe Commerce 2.4.7-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Applica hotfix per CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Aggiorna [impostazioni di password monouso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) per Google Authenticator**-Questo aggiornamento è necessario per risolvere un errore introdotto da una [modifica non compatibile con le versioni precedenti](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) nella versione 2.4.7. La descrizione del campo **[!UICONTROL OTP Window]** fornisce ora una spiegazione accurata dell&#39;impostazione e il valore predefinito è stato modificato da `1` a `29`.

* **Compatibilità della versione B2B** - Per la compatibilità con Commerce versione 2.4.7-p1, i commercianti con estensione Adobe Commerce B2B devono eseguire l&#39;aggiornamento alla versione [B2B versione 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.7-p1 risolve un problema introdotto nell’ambito della migrazione dell’integrazione UPS da SOAP all’API REST. Questo problema ha interessato i clienti che effettuano spedizioni al di fuori degli Stati Uniti e ha impedito loro di utilizzare le misurazioni del sistema metrico/SI di chilogrammi e centimetri per i pacchetti per creare spedizioni con UPS. Per informazioni dettagliate, consulta l&#39;articolo della knowledge base [Migrazione dell&#39;integrazione del metodo di spedizione UPS da SOAP a RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api).

<!-- Last updated from includes: 2025-10-22 11:16:25 -->

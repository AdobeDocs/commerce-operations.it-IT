---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.7
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.7.
source-git-commit: e7557f6eb32bec377f426b6de3bd00ab6cc4113c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La versione di sicurezza Adobe Commerce 2.4.7-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Evidenziazione sicurezza

Questa versione include un aggiornamento del [impostazioni password monouso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) per Google Authenticator per risolvere un errore introdotto da un [modifica non compatibile con le versioni precedenti](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) al punto 2.4.7. La descrizione del **[!UICONTROL OTP Window]** fornisce ora una spiegazione accurata dell’impostazione e il valore predefinito è stato modificato da `1` a `29`.

## Hotfix inclusi in questa versione

Adobe Commerce 2.4.7-p1 risolve un problema introdotto nell’ambito della migrazione dell’integrazione UPS da SOAP all’API REST. Questo problema ha interessato i clienti che effettuano spedizioni al di fuori degli Stati Uniti e ha impedito loro di utilizzare le misurazioni del sistema metrico/SI di chilogrammi e centimetri per i pacchetti per creare spedizioni con UPS. Consulta la [Migrazione dell’integrazione del metodo di spedizione UPS da SOAP all’API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) articolo della knowledge base per i dettagli.

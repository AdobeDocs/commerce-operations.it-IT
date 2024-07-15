---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.7
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La versione di sicurezza Adobe Commerce 2.4.7-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.7.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Elementi di rilievo sulla sicurezza

* **Aggiorna [impostazioni di password monouso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) per Google Authenticator**-Questo aggiornamento è necessario per risolvere un errore introdotto da una [modifica non compatibile con le versioni precedenti](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) nella versione 2.4.7. La descrizione del campo **[!UICONTROL OTP Window]** fornisce ora una spiegazione accurata dell&#39;impostazione e il valore predefinito è stato modificato da `1` a `29`.

* **Compatibilità della versione B2B** - Per la compatibilità con Commerce versione 2.4.7-p1, i commercianti con estensione Adobe Commerce B2B devono eseguire l&#39;aggiornamento alla versione [B2B versione 1.4.2-p1](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.7-p1 risolve un problema introdotto nell’ambito della migrazione dell’integrazione UPS dall’SOAP all’API REST. Questo problema ha interessato i clienti che effettuano spedizioni al di fuori degli Stati Uniti e ha impedito loro di utilizzare le misurazioni del sistema metrico/SI di chilogrammi e centimetri per i pacchetti per creare spedizioni con UPS. Per informazioni dettagliate, consulta l&#39;articolo della knowledge base [Migrazione dell&#39;integrazione del metodo di spedizione UPS da SOAP a RESTful API](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api).

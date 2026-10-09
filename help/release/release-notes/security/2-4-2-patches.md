---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.2
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
last-update: 2026-08-19T00:00:00.000Z
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%
---

# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.2

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

La versione di sicurezza di Adobe Commerce 2.4.2-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.2.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

<!-- Last updated from includes: 2026-08-19 13:31:55 -->

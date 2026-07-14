---
title: Note sulla versione [!DNL Commerce Version Tool]
description: Scopri le  [!DNL Commerce Version Tool]  versioni, tra cui il reporting sullo stato delle nuove patch, lo stato di protezione CVE, l'output CSV e il comportamento della cache.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# Note sulla versione di [!DNL Commerce Version Tool]

Queste note sulla versione descrivono gli aggiornamenti per [!DNL Commerce Version Tool] ([!DNL CVT]).

## Versione 1.0.0 — giugno 2026 {#version-1-0-0}

### Nuove funzioni

- **Segnalazione dello stato delle patch** - Segnala quali patch di sicurezza Adobe Commerce mensili vengono applicate, mancanti o non possono essere classificate per un&#39;installazione di Adobe Commerce.
- **Stato protezione CVE** - Esegue il mapping dei risultati della patch ai valori dello stato di protezione per CVE: `PROTECTED`, `VULNERABLE`, `UNKNOWN` e `NOT_APPLICABLE`.
- **Supporto di più componenti** - Rileva i componenti Adobe Commerce installati da `composer.lock`, inclusi Adobe Commerce business-to-business (B2B), Adobe Commerce Page Builder, Adobe Commerce Inventory e altri componenti rappresentati nel file di registro delle patch.
- **Output JSON e CSV** - Fornisce l&#39;output JSON per impostazione predefinita per il consumo programmatico e l&#39;output CSV per fogli di calcolo, scanner, dashboard e strumenti di conformità.
- **Comportamento della cache non in linea** - Il file del Registro di sistema della patch viene memorizzato nella cache locale dopo ogni recupero riuscito. Se il Registro di sistema remoto non è disponibile, lo strumento [!DNL CVT] può utilizzare il Registro di sistema memorizzato nella cache con un avviso.
- **Consegna in bundle** - Viene fornito all&#39;interno di file patch di sicurezza Adobe Commerce mensili. L&#39;applicazione della patch installa [!DNL CVT] in `vendor/bin/patch-status` senza alcun passaggio di installazione separato.

## Argomenti correlati

- [Introduzione](intro.md)
- [Generare un rapporto sullo stato delle patch](generate-report.md)
- [Risoluzione dei problemi](troubleshooting.md)

---
title: Prevenire l’avvelenamento della cache
description: Scopri come evitare l’avvelenamento della cache delle pagine per la vetrina Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '265'
ht-degree: 0%
---
# Prevenire l’avvelenamento della cache

In questo argomento viene illustrato come evitare l&#39;avvelenamento della cache se si utilizza il server Web Microsoft Internet Information Server (IIS). _L&#39;intossicazione della cache_ è un metodo per modificare il contenuto della cache in modo da includere pagine diverse dello stesso sito. Ad esempio, è possibile inserire una pagina di errore HTTP 404 (non trovata) invece di una pagina non pericolosa (ad esempio, la home page della vetrina), che può causare una potenziale negazione del servizio (DoS, Denial-of-Service). Gli URL di pagina dannosi sono memorizzati nella cache da Varnish o Redis, da cui il nome _page cache poisoning_.

Questi tipi di attacchi possono essere difficili da rilevare perché non generano errori nei registri del server web.

Questa soluzione si applica alle seguenti versioni di Commerce:

- 2.0.10 e versioni successive
- 2.1.2 e versioni successive

>[!INFO]
>
>Questo argomento è destinato agli amministratori IIS esperti.

## Descrizione

Il problema si verifica se le riscritture URL sono abilitate sul server IIS e una qualsiasi delle seguenti intestazioni HTTP viene modificata prima che la richiesta raggiunga il servizio di caching di Vernice o Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Se queste intestazioni vengono modificate, l’URL e il contenuto risultanti vengono memorizzati in cache, generando potenziali vulnerabilità.

## Soluzione

È possibile rimuovere i valori di tutte le intestazioni precedenti in base all&#39;impostazione del server IIS per `Enable_IIS_Rewrites`.

- Se `Enable_IIS_Rewrites` è impostato su `0`, i valori delle intestazioni vengono rimossi.
- Se `Enable_IIS_Rewrites` è impostato su `1`, i valori delle intestazioni vengono lasciati intatti.

>[!WARNING]
>
>Se si imposta `Enable_IIS_Rewrites` su `1`, non è necessario consentire la modifica dei valori delle intestazioni precedenti prima che la richiesta raggiunga il server Web IIS.

---
title: Impedire l’avvelenamento della cache
description: Scopri come evitare l’avvelenamento della cache delle pagine per la tua vetrina Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---


# Impedire l’avvelenamento della cache

Questo argomento illustra come evitare [cache](https://glossary.magento.com/cache) avvelenamento se si utilizza il server web Microsoft Internet Information Server (IIS). _Avvelenamento da cache_ è un metodo per modificare il contenuto della cache in modo da includere pagine diverse dallo stesso sito. Ad esempio, è possibile inserire una pagina di errore HTTP 404 (Non trovato) al posto di alcune pagine secondarie (ad esempio, il [vetrina](https://glossary.magento.com/storefront) home page), che può portare a un potenziale rifiuto del servizio (DoS). Gli URL delle pagine dannose sono memorizzati nella cache da Varnish o Redis, da cui il nome _avvelenamento della cache delle pagine_.

Questi tipi di attacchi possono essere difficili da rilevare perché non generano errori nei log del server web.

Questa soluzione si applica alle seguenti versioni Commerce:

- 2.0.10 e versioni successive
- 2.1.2 e versioni successive

>[!INFO]
>
>Questo argomento è destinato agli amministratori IIS esperti.

## Descrizione

Il problema si verifica se le riscritture URL sono abilitate sul server IIS e una delle seguenti intestazioni HTTP viene modificata prima che la richiesta raggiunga il servizio di memorizzazione in cache Varnish o Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Se queste intestazioni vengono modificate, l’URL e il contenuto risultanti vengono memorizzati nella cache, con conseguente rischio di vulnerabilità.

## Soluzione

Forniamo l&#39;opzione per rimuovere i valori di tutte le intestazioni precedenti in base all&#39;impostazione del server IIS per `Enable_IIS_Rewrites`.

- Se `Enable_IIS_Rewrites` è impostato su `0`, i valori delle intestazioni vengono rimossi.
- Se `Enable_IIS_Rewrites` è impostato su `1`, i valori delle intestazioni rimangono intatti.

>[!WARNING]
>
>Se si imposta `Enable_IIS_Rewrites` a `1`, non è possibile modificare i valori delle intestazioni precedenti prima che la richiesta raggiunga il server web IIS.

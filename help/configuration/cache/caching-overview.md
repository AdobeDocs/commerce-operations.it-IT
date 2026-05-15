---
title: Panoramica della memorizzazione in cache e opzioni di configurazione
description: Scopri come memorizzare in cache Adobe Commerce, incluso l’archiviazione back-end, la configurazione front-end e il caching a pagina intera con cache di tipo vernice, Redis, Valkey e L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Panoramica sulla memorizzazione in cache e opzioni di configurazione

Adobe Commerce si basa su un’architettura di caching a più livelli per ridurre il carico del database, ridurre al minimo l’elaborazione ridondante e accelerare la distribuzione delle pagine. A livello di applicazione, Commerce gestisce oltre una dozzina di [tipi di cache](../cli/manage-cache.md#clean-and-flush-cache-types), ad esempio configurazione, layout, blocchi di HTML e raccolte, ognuno dei quali può essere indirizzato a un backend di archiviazione dedicato come [Redis](config-redis.md) o [Valkey](config-valkey.md). Per il caching a pagina intera, Adobe consiglia vivamente [Varnish](config-varnish.md), un acceleratore HTTP che serve le pagine memorizzate nella cache direttamente dalla memoria. Livelli aggiuntivi come [l2 caching](level-two-cache.md) e [firma del contenuto statico](static-content-signing.md) migliorano ulteriormente le prestazioni per le distribuzioni multi-nodo a traffico elevato.

Questa guida spiega come funziona ogni livello di caching e mostra come configurare front-end, back-end e opzioni avanzate in base ai requisiti di distribuzione.

## Memorizzazione in cache dei front-end

Un front-end della cache è un’interfaccia tra Commerce e il back-end di archiviazione della cache. È possibile definire più front-end, ciascuno con impostazioni di back-end diverse, quindi assegnare tipi di [cache](../cli/manage-cache.md#clean-and-flush-cache-types) specifici a ogni front-end.  Per informazioni dettagliate sulla configurazione, vedere [Configurare i front-end della cache](cache-types.md).

## Memorizzazione in cache dei backend

Il back-end della cache è il meccanismo di archiviazione sottostante per i dati memorizzati nella cache. Commerce fornisce un back-end predefinito per il file system, ma puoi configurare altri back-end come Redis o Valkey per migliorare le prestazioni e la scalabilità. Per informazioni dettagliate sulle opzioni disponibili, vedere [Opzioni di back-end della cache](cache-options.md).

## Memorizzazione in cache di tutta la pagina con vernice

[La cache di vernice](config-varnish.md) è un acceleratore HTTP che memorizza nella cache pagine intere. Adobe consiglia vivamente Varnish per gli ambienti di produzione in quanto è molto più veloce della cache integrata a pagina intera.

>[!NOTE]
>
>Varish funziona come proxy inverso davanti al server web e non richiede modifiche alla configurazione del back-end della cache di Commerce.

## Memorizzazione in cache L2 (due livelli)

[La cache L2](level-two-cache.md) memorizza i dati della cache localmente su ogni nodo Web mentre si utilizza una cache remota (Redis o Valkey) come origine di verità. Questo riduce il traffico di rete tra i nodi web e la cache remota, migliorando le prestazioni per i siti a traffico elevato.

## Memorizzazione in cache di contenuti statici

[La firma di contenuto statico](static-content-signing.md) invalida la cache del browser per le risorse statiche (CSS, JavaScript, immagini) incorporando una versione di distribuzione negli URL dei file.

## Terminologia di caching

[!DNL Commerce] utilizza la seguente terminologia di caching:

- **Frontend**: interfaccia o gateway per l&#39;archiviazione della cache, implementato da [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipi di cache** — Uno dei tipi incorporati forniti con [!DNL Commerce] (ad esempio `config`, `layout`, `block_html`, `full_page`) o un tipo [personalizzato](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend** — Specifica i dettagli dell&#39;archiviazione della cache [cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementata da [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend).
- **Backend a due livelli**: memorizza i record della cache in due backend: una cache locale (veloce) e una cache remota (condivisa). Vedere [Configurazione cache L2](level-two-cache.md).

## Opzioni di configurazione

La configurazione della cache è memorizzata in due file:

- `<magento_root>/app/etc/di.xml` — Configurazione dell&#39;iniezione di dipendenza globale. Modificare il file per cambiare la cache `default` front-end fornita.
- `<magento_root>/app/etc/env.php` — Configurazione specifica per l&#39;ambiente. Modifica questo file per configurare i front-end della cache personalizzata. Questo file sostituisce la configurazione equivalente in `di.xml`.

Per informazioni dettagliate sulla mappatura front-end-to-type e sulla sintassi di configurazione della cache, vedi:

- [Configurare i front-end della cache](cache-types.md) — Associare un front-end della cache a tipi di cache specifici
- [Opzioni back-end cache](cache-options.md) — Riferimento opzione back-end

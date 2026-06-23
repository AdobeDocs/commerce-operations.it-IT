---
title: Panoramica della memorizzazione in cache e opzioni di configurazione
description: Scopri come memorizzare in cache Adobe Commerce, incluso l’archiviazione back-end, la configurazione front-end e il caching a pagina intera con cache di tipo vernice, Redis, Valkey e L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# Panoramica sulla memorizzazione in cache e opzioni di configurazione

Adobe Commerce si basa su un’architettura di caching a più livelli per ridurre il carico del database, ridurre al minimo l’elaborazione ridondante e accelerare la distribuzione delle pagine. A livello di applicazione, Commerce gestisce oltre una dozzina di [tipi di cache](../cli/manage-cache.md#clean-and-flush-cache-types), ad esempio configurazione, layout, blocchi di HTML e raccolte, ognuno dei quali può essere indirizzato a un backend di archiviazione dedicato come [Redis](config-redis.md) o [Valkey](config-valkey.md). Per il caching a pagina intera nelle distribuzioni locali, Adobe consiglia vivamente [Vernice](config-varnish.md). Le distribuzioni di Commerce su Cloud utilizzano Fastly. Livelli aggiuntivi come [l2 caching](level-two-cache.md) e [firma del contenuto statico](static-content-signing.md) migliorano ulteriormente le prestazioni per le distribuzioni multi-nodo a traffico elevato.

Questa guida spiega come funziona ogni livello di caching e mostra come configurare front-end, back-end e opzioni avanzate in base ai requisiti di distribuzione.

## Memorizzazione in cache dei front-end

Un front-end della cache è un’interfaccia tra Commerce e il back-end di archiviazione della cache. È possibile definire più front-end, ciascuno con impostazioni di back-end diverse, quindi assegnare tipi di [cache](../cli/manage-cache.md#clean-and-flush-cache-types) specifici a ogni front-end.  Per informazioni dettagliate sulla configurazione, vedere [Configurare i front-end della cache](cache-types.md).

## Memorizzazione in cache dei backend

Il back-end della cache è il meccanismo di archiviazione sottostante per i dati memorizzati nella cache. Commerce fornisce un back-end predefinito per il file system, ma puoi configurare altri back-end come Redis o Valkey per migliorare le prestazioni e la scalabilità. Per informazioni dettagliate sulle opzioni disponibili, vedere [Opzioni di back-end della cache](cache-options.md).

## Memorizzazione in cache di tutta la pagina con vernice

[La cache di vernice](config-varnish.md) è un acceleratore HTTP che memorizza nella cache pagine intere. Per gli ambienti di produzione on-premise, Adobe consiglia vivamente Varnish perché è molto più veloce della cache integrata a pagina intera. In ambienti Commerce on Cloud viene utilizzato [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) per il caching a pagina intera anziché Vernice.

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

Per il mapping front-end-to-type e la sintassi di configurazione della cache:

**On-premise**—La configurazione della cache è memorizzata in due file:

- `<magento_root>/app/etc/di.xml` — Configurazione dell&#39;iniezione di dipendenza globale. Modificare il file per cambiare la cache `default` front-end fornita.
- `<magento_root>/app/etc/env.php` — Configurazione specifica per l&#39;ambiente. Modifica questo file per configurare i front-end della cache personalizzata. Questo file sostituisce la configurazione equivalente in `di.xml`.

Per maggiori dettagli, consulta:

- [Configurare i front-end della cache](cache-types.md) - Associare un front-end della cache a tipi di cache specifici
- [Opzioni back-end cache](cache-options.md)—Riferimento opzione back-end

**Adobe Commerce su Cloud**—Configura il caching con `CACHE_CONFIGURATION` in `.magento.env.yaml`. Consulta [Best practice per la configurazione del servizio Redis e Valkey](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md).

---
title: Configura tipi e front-end della cache
description: Scopri come definire i front-end della cache e associarli ai tipi di cache in Adobe Commerce. Scopri la sintassi di configurazione per env.php e di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2: id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 507
ht-degree: 1%

---

# Configurare tipi e front-end della cache

Un front-end della cache è un&#39;interfaccia tra i tipi di cache di Commerce e il back-end di archiviazione della cache. È possibile definire più front-end, ciascuno con impostazioni di back-end diverse, quindi assegnare tipi di [cache](../cli/manage-cache.md#clean-and-flush-cache-types) specifici a ogni front-end.

Utilizzare questa relazione per decidere dove memorizzare i dati per ogni tipo di cache:

`cache type` -> `cache frontend` -> `cache backend`

Questa funzione è utile quando si desidera utilizzare back-end o configurazioni di cache diversi per tipi diversi di dati memorizzati nella cache. Ad esempio, è possibile assegnare il tipo di cache `full_page` a un front-end `page_cache` che utilizza un database Valkey dedicato, mentre altri tipi di cache utilizzano il front-end `default`.

{{cloud-cache-config}}

## Usa front-end predefinito

Commerce fornisce una cache front-end `default` che funziona per tutti i tipi di cache. Estende [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando la cache front-end [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

Nella maggior parte dei casi, non è necessario personalizzare il front-end. Devi solo configurare il backend. Consulta [Opzioni di back-end della cache](cache-options.md).

## Definire un front-end di cache personalizzato

I passaggi seguenti descrivono come associare una cache front-end a un tipo di cache.

### Passaggio 1: definire un front-end della cache e assegnare tipi di cache

Per definire una cache front-end personalizzata, aggiungere la configurazione a `app/etc/env.php` (che sostituisce `di.xml`):

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Dove:

- `<unique frontend id>` — Nome univoco per identificare il front-end (ad esempio `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>` — Tipo di back-end e opzioni per questo front-end (vedere [Opzioni cache](cache-options.md))
- `<cache type>`: tipo di cache di Commerce da assegnare a questo front-end (ad esempio, `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>Adobe Commerce 2.4.9 e versioni successive utilizzano nomi di tipi di back-end semplificati, ad esempio `valkey` o `file`, con l’implementazione di Symfony Cache. Consulta [Opzioni di back-end della cache](cache-options.md) per esempi di back-end e indicazioni specifiche per la versione.


### Passaggio 2: configurare le opzioni front-end e back-end

È possibile specificare le opzioni di configurazione della cache front-end e back-end in `env.php` o `di.xml`. Questa attività è facoltativa. Se non si specificano opzioni, Commerce utilizza le impostazioni predefinite front-end e back-end.

`env.php` esempio:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

Dove:

- `<frontend_type>`: tipo di cache front-end di basso livello. Specificare un nome di classe compatibile con `Zend\Cache\Core`.Se omesso, verrà utilizzato [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

- `<frontend_option>`, `<frontend_option_value>` - Nome e valore delle opzioni passate dal framework Commerce come array associativo alla cache front-end durante la creazione.

- `<backend_type>`: tipo di cache di back-end di basso livello. Puoi specificare:
   - **Cache Symfony moderna (2.4.9+, consigliata)**: nomi semplificati come `redis`, `valkey` o `file`
   - **Legacy (basato su Zend)**: nome completo della classe compatibile con `Zend_Cache_Backend` che implementa `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>`: nome e valore delle opzioni passate dal framework Commerce come array associativo alla cache back-end durante la creazione.

>[!NOTE]
>
>**Implementazione legacy e moderna:**
>
>- **Legacy (basato su Zend)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Moderno (cache Symfony)**: `'backend' => 'valkey'` per Commerce versioni 2.4.9+ e versioni patch correnti per le righe di rilascio 2.4.5 - 2.4.8 in cui Valkey è il backend della cache supportato.
>
>La moderna implementazione della cache di Symfony offre prestazioni migliori grazie alla conformità PSR-6, alla serializzazione Igbinary, alla compressione Gzip, agli script Lua e alle connessioni persistenti.

Consulta la [documentazione Laminas](https://docs.laminas.dev/) per le opzioni basate su Zend. Per la configurazione della cache di Symfony, vedi gli articoli [Redis](redis-pg-cache.md) e [Valkey](valkey-pg-cache.md) in questa documentazione.

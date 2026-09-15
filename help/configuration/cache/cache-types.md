---
title: Configura tipi e front-end della cache
description: Scopri come definire i front-end della cache e associarli ai tipi di cache in Adobe Commerce. Scopri la sintassi di configurazione per env.php.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%
---
# Configurare tipi e front-end della cache

Una cache front-end connette i tipi di cache di Commerce all&#39;archiviazione della cache. È possibile definire più front-end e assegnare tipi di cache specifici a ciascun front-end.

>[!BEGINSHADEBOX]

Utilizza la seguente relazione per determinare dove un tipo di cache memorizza i propri dati:

tipo di cache → cache front-end → cache back-end

>[!ENDSHADEBOX]

Per una panoramica dell&#39;architettura di memorizzazione nella cache di Commerce, vedere [Panoramica sulla memorizzazione nella cache e opzioni di configurazione](caching-overview.md).

>[!NOTE]
>
>Per l&#39;infrastruttura cloud di Adobe Commerce, utilizza la [configurazione di distribuzione cloud](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) descritta nella guida per il cloud. Non modificare `app/etc/env.php` direttamente. Gli strumenti di distribuzione generano questo file e possono sovrascrivere le modifiche manuali.

## Usa front-end predefinito

Commerce fornisce un front-end predefinito che può essere utilizzato da tutti i tipi di cache.

Nella maggior parte dei casi, non è necessario definire un front-end personalizzato. Se tutti i tipi di cache possono utilizzare le stesse opzioni di back-end e back-end, utilizza il front-end predefinito e configurane il back-end. Consulta [Opzioni di backend cache](cache-options.md) per la configurazione specifica del backend.

Per le versioni di Adobe Commerce precedenti alla 2.4.9, il front-end predefinito utilizza l’implementazione della cache legacy basata su Zend. Il front-end `Magento\Framework\Cache\Core` estende `Zend_Cache_Core`. Adobe Commerce 2.4.9 e versioni successive utilizzano la moderna implementazione di Symfony. Per informazioni specifiche sulla versione, consulta [Opzioni di back-end della cache](cache-options.md).

## Definire un front-end personalizzato

Utilizza un front-end di cache personalizzato quando uno o più tipi di cache richiedono impostazioni di back-end diverse da quelle del front-end predefinito.

Per le distribuzioni locali, definire il front-end in `app/etc/env.php`. Quindi assegna ad essa uno o più tipi di cache:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

Dove:

- `<frontend-id>` è l&#39;identificatore univoco per il front-end, ad esempio `default` o `page_cache`.
- `<backend-type>` identifica il backend utilizzato dal front-end. Il valore supportato dipende dalla versione di Adobe Commerce e dal back-end selezionato.
- `backend_options` contiene le opzioni per il backend selezionato.
- `<cache-type-id>` è un tipo di cache di Commerce, ad esempio `config`, `layout`, `block_html` o `full_page`.


Per i tipi di back-end, le opzioni supportate e gli esempi di configurazione specifici della versione, vedere [Opzioni di back-end della cache](cache-options.md).

## Assegnare un tipo di cache a un front-end

La configurazione `type` mappa un tipo di cache a un front-end:

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

Dove:

- `<frontend_type>`: tipo di cache front-end di basso livello. Specificare un nome di classe compatibile con `Zend_Cache_Core`.
Se omesso, verrà utilizzato [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

- `<frontend_option>`, `<frontend_option_value>` - Nome e valore delle opzioni passate dal framework Commerce come array associativo alla cache front-end durante la creazione.

- `<backend_type>`: tipo di cache di back-end di basso livello. Puoi specificare:
  - **Cache Symfony (2.4.9+, consigliata)**: nomi semplificati come `valkey` o `file`
  - **Basato su Zend**: nome completo della classe compatibile con `Zend_Cache_Backend` che implementa `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>`: nome e valore delle opzioni passate dal framework Commerce come array associativo alla cache back-end durante la creazione.

>[!NOTE]
>
>Per i formati dei valori back-end, ad esempio i nomi di classe basati su Zend e i nomi semplificati della cache di Symfony come `valkey` o `file`, vedere [Opzioni back-end della cache](cache-options.md).

>[!MORELIKETHIS]
>
>- [Configurazione cache L2 per l&#39;ottimizzazione delle prestazioni](level-two-cache.md)
>- [Gestione della cache](../cli/manage-cache.md)

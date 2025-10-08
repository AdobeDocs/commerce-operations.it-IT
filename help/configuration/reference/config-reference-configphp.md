---
title: riferimento config.php
description: Scopri i valori del file config.php e le sezioni per la configurazione di Adobe Commerce. Scopri moduli, ambiti, impostazioni di sistema e best practice per la distribuzione.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 1%

---

# riferimento config.php

Il file `config.php` contiene le sezioni seguenti:

| Nome | Descrizione |
| --------- | -------------------|
| `i18n` | Tutti i dati di traduzione in linea. La lettura da questa sezione non è supportata. |
| `modules` | L’elenco dei moduli abilitati e disabilitati. |
| `scopes` | Elenco di negozi, gruppi di negozi e siti Web con informazioni correlate. |
| `system` | Le configurazioni di sistema necessarie per la distribuzione di contenuti statici. |
| `themes` | Configurazione dei temi installati. |

## moduli

Contiene un array di moduli e i relativi stati. Se il modulo è abilitato, il valore è 1. In caso contrario, il valore è 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Ulteriori informazioni sui [moduli].

## ambiti

Contiene un array di valori di configurazione dell&#39;ambito. Ha i seguenti sottonodi:

| Nome | Descrizione |
| ---------- | -----------------------------------|
| `websites` | Configurazione del sito web |
| `groups` | Configurazione archivi |
| `stores` | Configurazione delle viste store |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Ulteriori informazioni su [ambiti Commerce][scopes].

## sistema

Contiene un array di valori di configurazione dei campi di sistema.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Ulteriori informazioni sulle [configurazioni specifiche del sistema](config-reference-sens.md).

## temi

Contiene un array di valori per la configurazione del tema.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Ulteriori informazioni su [Temi].

<!-- link definitions -->

[Moduli]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=it
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=it#scope-settings
[Temi]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/

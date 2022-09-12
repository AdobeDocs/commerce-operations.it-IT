---
title: riferimento config.php
description: Vedi un elenco di valori nel file config.php .
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# riferimento config.php

La `config.php` il file contiene le sezioni seguenti:

| Nome | Descrizione |
| --------- | -------------------|
| `i18n` | Tutti i dati di traduzione in linea. La lettura da questa sezione non è supportata. |
| `modules` | Elenco dei moduli abilitati e disabilitati. |
| `scopes` | Elenco di negozi, gruppi di negozi e siti web con informazioni correlate. |
| `system` | Configurazioni di sistema necessarie per la distribuzione di contenuto statico. |
| `themes` | La configurazione dei temi installati. |

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

Ulteriori informazioni [Moduli].

## ambiti

Contiene una matrice di valori di configurazione dell&#39;ambito. Ha i seguenti sottonodi:

| Nome | Descrizione |
| ---------- | -----------------------------------|
| `websites` | Configurazione del sito web |
| `groups` | Memorizza la configurazione |
| `stores` | Configurazione delle viste del negozio |

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

Ulteriori informazioni [Ambiti Commerce][scopes].

## sistema

Contiene una matrice di valori di configurazione dei campi di sistema.

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

Ulteriori informazioni [Configurazioni specifiche del sistema](config-reference-sens.md).

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

Ulteriori informazioni [Temi].

<!-- link definitions -->

[Moduli]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings
[Temi]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/

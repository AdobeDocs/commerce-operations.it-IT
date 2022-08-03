---
title: Strategie di distribuzione per i file di visualizzazione statici
description: Informazioni sulle strategie di distribuzione per l’applicazione Commerce.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Strategie di distribuzione per i file di visualizzazione statici

Quando si distribuiscono file di visualizzazione statica, è possibile scegliere una delle tre strategie disponibili. Ognuno di essi fornisce risultati di distribuzione ottimali per diversi casi d’uso:

- [Standard](#standard-strategy): il processo di distribuzione regolare.
- [Rapido](#quick-strategy) (_default_): riduce al minimo il tempo necessario per la distribuzione quando vengono distribuiti file per più di un’impostazione internazionale.
- [Compatto](#compact-strategy): riduce al minimo lo spazio occupato dai file di visualizzazione pubblicati.

Le sezioni seguenti descrivono i dettagli e le caratteristiche di implementazione di ciascuna strategia.

## Strategia standard

Quando si utilizza la strategia Standard, tutti i file di visualizzazione statici per tutti i pacchetti vengono distribuiti, ovvero elaborati da [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Per ulteriori informazioni, consulta [Distribuzione di file di visualizzazione statici](../cli/static-view-file-deployment.md).

## Strategia rapida

La strategia rapida esegue le seguenti azioni:

1. Per ogni tema, viene scelta una lingua arbitraria e vengono distribuiti tutti i file per questa impostazione internazionale, come nella strategia standard.
1. Per tutte le altre impostazioni internazionali del tema:

   1. I file che sostituiscono le impostazioni internazionali distribuite vengono definiti e distribuiti.
   1. Tutti gli altri file sono considerati simili per tutte le impostazioni internazionali e vengono copiati dalle impostazioni internazionali distribuite.

>[!INFO]
>
>Da _simile_: file indipendenti dalle impostazioni internazionali, dal tema o dall’area. Questi file possono includere CSS, immagini e font.

Questo approccio riduce il tempo di distribuzione necessario per più impostazioni internazionali, anche se molti file vengono duplicati.

## Strategia compatta

La strategia compatta evita la duplicazione dei file memorizzando file simili in `base` sottodirectory.

Per il risultato più ottimizzato, vengono assegnati tre ambiti per possibili somiglianze: area, tema e impostazioni internazionali. La `base` le sottodirectory vengono create per tutte le combinazioni di questi ambiti.

I file vengono distribuiti in queste sottodirectory in base ai pattern seguenti.

| Pattern | Descrizione |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | File specifici per un&#39;area, un tema e le impostazioni internazionali particolari |
| `<area>/<theme>/default` | File simili per tutte le impostazioni internazionali di un particolare tema di una particolare area. |
| `<area>/Magento/base/<locale>` | File specifici per una particolare area e impostazioni internazionali, ma simili per tutti i temi. |
| `<area>/Magento/base/default` | File specifici per una particolare area, ma simili per tutti i temi e le impostazioni internazionali. |
| `base/Magento/base/<locale>` | File simili per tutte le aree e i temi, ma specifici per una particolare impostazione internazionale. |
| `base/Magento/base/default` | Simile per tutte le aree, i temi e le impostazioni internazionali. |

### Mappatura dei file distribuiti

L&#39;approccio alla distribuzione utilizzato nella strategia compatta significa che i file vengono ereditati da temi e impostazioni internazionali di base. Queste relazioni di ereditarietà vengono memorizzate nei file di mappa per ogni combinazione di area, tema e impostazioni internazionali. Ci sono file mappa separati per PHP e JS:

- `map.php`
- `requirejs-map.js`

La `map.php` file utilizzato da [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) per creare gli URL corretti.

La `requirejs-map.js` viene utilizzato dal `baseUrlResolver` plugin per RequireJS.

Esempio di `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Esempio di `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Suggerimenti per gli sviluppatori di estensioni

Per creare URL per file di visualizzazione statici, utilizza [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Non utilizzare le concatenazioni URL per evitare problemi con file statici non trovati e non visualizzati durante il rendering della pagina.

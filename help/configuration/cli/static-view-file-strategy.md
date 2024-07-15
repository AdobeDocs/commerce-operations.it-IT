---
title: Strategie di distribuzione per i file di visualizzazione statica
description: Scopri le strategie di distribuzione per l’applicazione Commerce.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Strategie di distribuzione per i file di visualizzazione statica

Quando si distribuiscono i file di visualizzazione statica, è possibile scegliere una delle tre strategie disponibili. Ciascuno di essi fornisce risultati di distribuzione ottimali per diversi casi d’uso:

- [Standard](#standard-strategy): il processo di distribuzione regolare.
- [Rapido](#quick-strategy) (_predefinito_): riduce al minimo il tempo necessario per la distribuzione quando vengono distribuiti file per più impostazioni locali.
- [Compatto](#compact-strategy): riduce lo spazio occupato dai file di visualizzazione pubblicati.

Le sezioni seguenti descrivono i dettagli e le caratteristiche di implementazione di ciascuna strategia.

## Strategia standard

Quando si utilizza la strategia Standard, vengono distribuiti tutti i file di visualizzazione statica per tutti i pacchetti, ovvero elaborati da [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Per ulteriori informazioni, vedere [Distribuire i file di visualizzazione statici](../cli/static-view-file-deployment.md).

## Strategia rapida

La strategia rapida esegue le azioni riportate di seguito.

1. Per ogni tema viene scelta una lingua arbitraria e vengono distribuiti tutti i file per questa lingua, come nella strategia standard.
1. Per tutte le altre lingue del tema:

   1. I file che sostituiscono le impostazioni locali distribuite vengono definiti e distribuiti.
   1. Tutti gli altri file sono considerati simili per tutte le impostazioni locali e vengono copiati dalle impostazioni locali distribuite.

>[!INFO]
>
>Per _simili_, si intendono file indipendenti dalle impostazioni locali, dal tema o dall&#39;area. Questi file possono includere CSS, immagini e font.

Questo approccio riduce al minimo il tempo di distribuzione necessario per più impostazioni locali, anche se molti file sono duplicati.

## Strategia compatta

La strategia compatta evita la duplicazione dei file archiviando file simili in sottodirectory `base`.

Per ottenere il risultato più ottimizzato, vengono assegnati tre ambiti per una possibile somiglianza: area, tema e impostazioni internazionali. Le sottodirectory `base` vengono create per tutte le combinazioni di questi ambiti.

I file vengono distribuiti in queste sottodirectory in base ai seguenti modelli.

| Pattern | Descrizione |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | File specifici per un&#39;area, un tema e una lingua particolari |
| `<area>/<theme>/default` | File simili per tutte le lingue di un particolare tema di un&#39;area particolare. |
| `<area>/Magento/base/<locale>` | File specifici per un&#39;area e una lingua particolari, ma simili per tutti i temi. |
| `<area>/Magento/base/default` | File specifici per una particolare area, ma simili per tutti i temi e le impostazioni internazionali. |
| `base/Magento/base/<locale>` | File simili per tutte le aree e i temi, ma specifici per una particolare lingua. |
| `base/Magento/base/default` | Simile per tutte le aree, i temi e le impostazioni internazionali. |

### Mappatura dei file distribuiti

L&#39;approccio alla distribuzione utilizzato nella strategia compatta implica che i file vengono ereditati dai temi di base e dalle impostazioni internazionali. Queste relazioni di ereditarietà vengono memorizzate nei file di mappa per ogni combinazione di area, tema e impostazioni internazionali. Esistono file di mappa separati per PHP e JS:

- `map.php`
- `requirejs-map.js`

Il file `map.php` è utilizzato da [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) per generare gli URL corretti.

`requirejs-map.js` è utilizzato dal plug-in `baseUrlResolver` per RequireJS.

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

Per generare gli URL per i file di visualizzazione statica, utilizzare [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Non utilizzare le concatenazioni URL per evitare problemi con i file statici che non vengono trovati e visualizzati durante il rendering della pagina.

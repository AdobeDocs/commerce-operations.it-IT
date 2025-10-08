---
title: Blocco ESI vernice
description: Scopri le funzioni ESI (Varnish Edge Side Includes) e come incorporare le pagine web per Adobe Commerce. Scopri l’implementazione e l’ottimizzazione dei blocchi ESI.
badge: label="Contributo di Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Blocco ESI vernice

Le Inclusioni lato Edge (ESI) sono direttive speciali che è possibile utilizzare per includere pagine web in altre pagine web.

Ecco un esempio:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

La vernice recupera il contenuto da `http://domain.com/index.php/page_cache/block/esi/blocks` e sostituisce con esso il tag `<esi>`.

## Commerce e vernice ESI

Il framework Commerce crea un tag ESI quando vengono soddisfatte le seguenti condizioni:

- Applicazione di caching impostata su `Varnish Cache`
- Elemento `block` del layout XML aggiunto con un attributo `ttl`

### Esempio

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Nell&#39;esempio precedente, l&#39;elemento `block` aggiunge contenuto dal modello `esi.phtml` a una home page e Varnish lo aggiorna automaticamente ogni 30 secondi.

## Limitazioni

Attualmente, Varnish non supporta ESI su HTTPS, quindi passa automaticamente a HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```

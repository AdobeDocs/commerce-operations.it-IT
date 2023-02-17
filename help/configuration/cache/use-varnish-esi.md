---
title: Blocco ESI verniciato
description: Informazioni su Edge Side Includes e su come utilizzarli per incorporare pagine web.
badge: label="Contributo di Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
source-git-commit: 90544452f5f0834e096ead6ea3df64dcb5eaea11
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Blocco ESI verniciato

Edge Side Includes (ESI) sono direttive speciali che è possibile utilizzare per includere pagine web in altre pagine web.

Esempio:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnish recupera il contenuto da `http://domain.com/index.php/page_cache/block/esi/blocks` e sostituiscono `<esi>` aggiungilo.

## ESI Commerce e Varnish

Commerce framework crea un tag ESI quando vengono soddisfatte le seguenti condizioni:

- L&#39;applicazione di caching è impostata su `Varnish Cache`
- Layout XML `block` viene aggiunto con un `ttl` attributo

### Esempio

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Nell’esempio precedente, il `block` aggiunge contenuto dal `esi.phtml` template a una homepage e Varnish automaticamente lo aggiorna ogni 30 secondi.

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

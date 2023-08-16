---
title: Blocco ESI vernice
description: Scopri le inclusioni lato Edge e come utilizzarle per incorporare le pagine web.
badge: label="Contributo di Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Blocco ESI vernice

Edge Side Includes (ESI) sono direttive speciali che è possibile utilizzare per includere pagine web in altre pagine web.

Ecco un esempio:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

La vernice recupera il contenuto da `http://domain.com/index.php/page_cache/block/esi/blocks` e sostituisci il `<esi>` aggiungeteci un tag.

## Commercio e vernice ESI

Il framework Commerce crea un tag ESI quando vengono soddisfatte le seguenti condizioni:

- L’applicazione di caching è impostata su `Varnish Cache`
- Un layout XML `block` viene aggiunto con un `ttl` attributo

### Esempio

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

Nell’esempio precedente, il `block` aggiunge contenuto dal `esi.phtml` modello a una home page e Vernice lo aggiorna automaticamente ogni 30 secondi.

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

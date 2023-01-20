---
source-git-commit: 4391091cce32618dc02b0bddb62ff9d16dd12f10
workflow-type: tm+mt
source-wordcount: '2192'
ht-degree: 0%

---
# Pacchetti Magenti Open Source

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Il Magento Open Source utilizza il Compositore per gestire i pacchetti PHP.

La `composer.json` il file dichiara l&#39;elenco dei pacchetti, mentre il `composer.lock` memorizza un elenco completo dei pacchetti (una versione completa di ciascun pacchetto e delle relative dipendenze) utilizzati per creare un&#39;installazione di Adobe Commerce o Magento Open Source.

La seguente documentazione di riferimento viene generata dal `composer.lock` e copre i pacchetti richiesti inclusi nel Magento Open Source 2.4.5.

## Dipendenze

`magento/product-community-edition 2.4.5` ha le dipendenze seguenti:

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/adobe-stock-integration: 2.1.4
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework: 103.0.5
magento/framework-amqp: 100.4.3
magento/framework-bulk: 101.0.1
magento/framework-message-queue: 100.4.5
magento/google-shopping-ads: 4.0.1
magento/inventory-metapackage: 1.2.5
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.3.0
magento/magento2-base: 2.4.5
magento/module-admin-adobe-ims: 100.4.0
magento/module-admin-analytics: 100.4.4
magento/module-admin-notification: 100.4.4
magento/module-adobe-ims: 2.1.4
magento/module-adobe-ims-api: 2.1.2
magento/module-advanced-pricing-import-export: 100.4.5
magento/module-advanced-search: 100.4.3
magento/module-amqp: 100.4.2
magento/module-analytics: 100.4.5
magento/module-asynchronous-operations: 100.4.5
magento/module-authorization: 100.4.5
magento/module-aws-s3: 100.4.3
magento/module-backend: 102.0.5
magento/module-backup: 100.4.5
magento/module-bundle: 101.0.5
magento/module-bundle-graph-ql: 100.4.5
magento/module-bundle-import-export: 100.4.4
magento/module-cache-invalidate: 100.4.3
magento/module-captcha: 100.4.5
magento/module-cardinal-commerce: 100.4.3
magento/module-catalog: 104.0.5
magento/module-catalog-analytics: 100.4.2
magento/module-catalog-cms-graph-ql: 100.4.1
magento/module-catalog-customer-graph-ql: 100.4.4
magento/module-catalog-graph-ql: 100.4.5
magento/module-catalog-import-export: 101.1.5
magento/module-catalog-inventory: 100.4.5
magento/module-catalog-inventory-graph-ql: 100.4.2
magento/module-catalog-rule: 101.2.5
magento/module-catalog-rule-configurable: 100.4.4
magento/module-catalog-rule-graph-ql: 100.4.2
magento/module-catalog-search: 102.0.5
magento/module-catalog-url-rewrite: 100.4.5
magento/module-catalog-url-rewrite-graph-ql: 100.4.3
magento/module-catalog-widget: 100.4.5
magento/module-checkout: 100.4.5
magento/module-checkout-agreements: 100.4.4
magento/module-checkout-agreements-graph-ql: 100.4.1
magento/module-cms: 104.0.5
magento/module-cms-graph-ql: 100.4.2
magento/module-cms-url-rewrite: 100.4.4
magento/module-cms-url-rewrite-graph-ql: 100.4.3
magento/module-compare-list-graph-ql: 100.4.1
magento/module-config: 101.2.5
magento/module-configurable-import-export: 100.4.3
magento/module-configurable-product: 100.4.5
magento/module-configurable-product-graph-ql: 100.4.5
magento/module-configurable-product-sales: 100.4.2
magento/module-contact: 100.4.4
magento/module-cookie: 100.4.5
magento/module-cron: 100.4.5
magento/module-csp: 100.4.4
magento/module-currency-symbol: 100.4.3
magento/module-customer: 103.0.5
magento/module-customer-analytics: 100.4.2
magento/module-customer-downloadable-graph-ql: 100.4.1
magento/module-customer-graph-ql: 100.4.5
magento/module-customer-import-export: 100.4.5
magento/module-deploy: 100.4.5
magento/module-developer: 100.4.5
magento/module-dhl: 100.4.4
magento/module-directory: 100.4.5
magento/module-directory-graph-ql: 100.4.3
magento/module-downloadable: 100.4.5
magento/module-downloadable-graph-ql: 100.4.5
magento/module-downloadable-import-export: 100.4.4
magento/module-eav: 102.1.5
magento/module-eav-graph-ql: 100.4.2
magento/module-elasticsearch: 101.0.5
magento/module-elasticsearch-6: 100.4.5
magento/module-elasticsearch-7: 100.4.5
magento/module-email: 101.1.5
magento/module-encryption-key: 100.4.3
magento/module-fedex: 100.4.3
magento/module-gift-message: 100.4.4
magento/module-gift-message-graph-ql: 100.4.3
magento/module-google-adwords: 100.4.2
magento/module-google-analytics: 100.4.1
magento/module-google-gtag: 100.4.0
magento/module-google-optimizer: 100.4.4
magento/module-graph-ql: 100.4.5
magento/module-graph-ql-cache: 100.4.2
magento/module-grouped-catalog-inventory: 100.4.2
magento/module-grouped-import-export: 100.4.3
magento/module-grouped-product: 100.4.5
magento/module-grouped-product-graph-ql: 100.4.5
magento/module-import-export: 101.0.5
magento/module-indexer: 100.4.5
magento/module-instant-purchase: 100.4.4
magento/module-integration: 100.4.5
magento/module-jwt-framework-adapter: 100.4.1
magento/module-jwt-user-token: 100.4.0
magento/module-layered-navigation: 100.4.5
magento/module-login-as-customer: 100.4.5
magento/module-login-as-customer-admin-ui: 100.4.5
magento/module-login-as-customer-api: 100.4.4
magento/module-login-as-customer-assistance: 100.4.4
magento/module-login-as-customer-frontend-ui: 100.4.4
magento/module-login-as-customer-graph-ql: 100.4.2
magento/module-login-as-customer-log: 100.4.3
magento/module-login-as-customer-page-cache: 100.4.4
magento/module-login-as-customer-quote: 100.4.3
magento/module-login-as-customer-sales: 100.4.4
magento/module-marketplace: 100.4.3
magento/module-media-content: 100.4.3
magento/module-media-content-api: 100.4.4
magento/module-media-content-catalog: 100.4.3
magento/module-media-content-cms: 100.4.3
magento/module-media-content-synchronization: 100.4.4
magento/module-media-content-synchronization-api: 100.4.3
magento/module-media-content-synchronization-catalog: 100.4.2
magento/module-media-content-synchronization-cms: 100.4.2
magento/module-media-gallery: 100.4.4
magento/module-media-gallery-api: 101.0.4
magento/module-media-gallery-catalog: 100.4.2
magento/module-media-gallery-catalog-integration: 100.4.2
magento/module-media-gallery-catalog-ui: 100.4.2
magento/module-media-gallery-cms-ui: 100.4.2
magento/module-media-gallery-integration: 100.4.4
magento/module-media-gallery-metadata: 100.4.3
magento/module-media-gallery-metadata-api: 100.4.2
magento/module-media-gallery-renditions: 100.4.3
magento/module-media-gallery-renditions-api: 100.4.2
magento/module-media-gallery-synchronization: 100.4.4
magento/module-media-gallery-synchronization-api: 100.4.3
magento/module-media-gallery-synchronization-metadata: 100.4.1
magento/module-media-gallery-ui: 100.4.4
magento/module-media-gallery-ui-api: 100.4.3
magento/module-media-storage: 100.4.4
magento/module-message-queue: 100.4.5
magento/module-msrp: 100.4.4
magento/module-msrp-configurable-product: 100.4.2
magento/module-msrp-grouped-product: 100.4.2
magento/module-multishipping: 100.4.5
magento/module-mysql-mq: 100.4.3
magento/module-new-relic-reporting: 100.4.3
magento/module-newsletter: 100.4.5
magento/module-newsletter-graph-ql: 100.4.2
magento/module-offline-payments: 100.4.3
magento/module-offline-shipping: 100.4.4
magento/module-page-cache: 100.4.5
magento/module-payment: 100.4.5
magento/module-payment-graph-ql: 100.4.0
magento/module-paypal: 101.0.5
magento/module-paypal-captcha: 100.4.2
magento/module-paypal-graph-ql: 100.4.3
magento/module-persistent: 100.4.5
magento/module-product-alert: 100.4.4
magento/module-product-video: 100.4.5
magento/module-quote: 101.2.5
magento/module-quote-analytics: 100.4.4
magento/module-quote-bundle-options: 100.4.1
magento/module-quote-configurable-options: 100.4.1
magento/module-quote-downloadable-links: 100.4.1
magento/module-quote-graph-ql: 100.4.5
magento/module-related-product-graph-ql: 100.4.2
magento/module-release-notification: 100.4.3
magento/module-remote-storage: 100.4.3
magento/module-reports: 100.4.5
magento/module-require-js: 100.4.1
magento/module-review: 100.4.5
magento/module-review-analytics: 100.4.2
magento/module-review-graph-ql: 100.4.1
magento/module-robots: 101.1.1
magento/module-rss: 100.4.3
magento/module-rule: 100.4.4
magento/module-sales: 103.0.5
magento/module-sales-analytics: 100.4.2
magento/module-sales-graph-ql: 100.4.5
magento/module-sales-inventory: 100.4.2
magento/module-sales-rule: 101.2.5
magento/module-sales-sequence: 100.4.2
magento/module-sample-data: 100.4.3
magento/module-search: 101.1.5
magento/module-security: 100.4.5
magento/module-send-friend: 100.4.3
magento/module-send-friend-graph-ql: 100.4.1
magento/module-shipping: 100.4.5
magento/module-sitemap: 100.4.4
magento/module-store: 101.1.5
magento/module-store-graph-ql: 100.4.3
magento/module-swagger: 100.4.4
magento/module-swagger-webapi: 100.4.1
magento/module-swagger-webapi-async: 100.4.1
magento/module-swatches: 100.4.5
magento/module-swatches-graph-ql: 100.4.3
magento/module-swatches-layered-navigation: 100.4.1
magento/module-tax: 100.4.5
magento/module-tax-graph-ql: 100.4.1
magento/module-tax-import-export: 100.4.4
magento/module-theme: 101.1.5
magento/module-theme-graph-ql: 100.4.2
magento/module-translation: 100.4.5
magento/module-ui: 101.2.5
magento/module-ups: 100.4.5
magento/module-url-rewrite: 102.0.4
magento/module-url-rewrite-graph-ql: 100.4.4
magento/module-user: 101.2.5
magento/module-usps: 100.4.4
magento/module-variable: 100.4.3
magento/module-vault: 101.2.5
magento/module-vault-graph-ql: 100.4.1
magento/module-version: 100.4.2
magento/module-webapi: 100.4.4
magento/module-webapi-async: 100.4.3
magento/module-webapi-security: 100.4.2
magento/module-weee: 100.4.5
magento/module-weee-graph-ql: 100.4.2
magento/module-widget: 101.2.5
magento/module-wishlist: 101.2.5
magento/module-wishlist-analytics: 100.4.3
magento/module-wishlist-graph-ql: 100.4.5
magento/page-builder: 1.7.2
magento/security-package: 1.1.4
magento/theme-adminhtml-backend: 100.4.5
magento/theme-frontend-blank: 100.4.5
magento/theme-frontend-luma: 100.4.5
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
paypal/module-braintree: 4.4.0
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
temando/module-shipping: 2.0.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
```

## Licenze di terzi

### Apache-2.0, LGPL-2.1 solo

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>libreria</td>
    <td>Client PHP per Elasticsearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>libreria</td>
    <td>Libreria API di Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>libreria</td>
    <td>AWS Common Runtime per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>libreria</td>
    <td>AWS SDK per PHP - Utilizza Amazon Web Services nel tuo progetto PHP</td>
  </tr>
  <tr>
    <td>
      paypal/modulo-braintree
    </td>
    <td>metapackage</td>
    <td>Magento Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>libreria</td>
    <td>Porta PHP della versione Javascript di LESS http://lesscss.org (Originariamente mantenuta da Josh Schmidt)</td>
  </tr>
  </tbody>
</table>

### Clausola BSD-2

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>libreria</td>
    <td>BaconQrCode è un generatore di codice QR per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>libreria</td>
    <td>Libreria di asserzioni sottili per la convalida degli input nei modelli aziendali.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>libreria</td>
    <td>Implementazione enum PHP 7.1</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>libreria</td>
    <td>Strumento per scrivere i file in modo sicuro, per evitare le condizioni di gara</td>
  </tr>
  </tbody>
</table>

### Clausola BSD-3

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>modulo magento</td>
    <td>Il backend Zend_Cache_Backend_File stock ha prestazioni estremamente scarse per la pulizia tramite tag che lo rendono inutilizzabile con l'aumento del numero di elementi memorizzati nella cache. Questo backend apporta molte modifiche che si traducono in un enorme aumento delle prestazioni, soprattutto per la pulizia dei tag.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>modulo magento</td>
    <td>Backend_Cache tramite Redis con supporto completo per i tag.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>libreria</td>
    <td>Un handler di sessioni basato su Redis con blocco ottimistico</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/ricontcha</a>
    </td>
    <td>libreria</td>
    <td>Libreria client per reCAPTCHA, un servizio gratuito che protegge i siti web dallo spam e dagli abusi.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>libreria</td>
    <td>Generare e convalidare i CAPTCHA utilizzando Figlet, immagini, ReCaptcha e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>libreria</td>
    <td>Estensioni dell’API di riflessione PHP, scansione del codice statico e generazione del codice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>libreria</td>
    <td>fornisce un'interfaccia utente basata su proprietà dell'oggetto nidificato per accedere a questi dati di configurazione all'interno del codice dell'applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>libreria</td>
    <td>Livello di astrazione del database, astrazione SQL, astrazione del set di risultati e implementazioni di RowDataGateway e TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dipendenza-plugin</a>
    </td>
    <td>compositore-plugin</td>
    <td>Sostituire i pacchetti zendframework e zfcampus con i loro equivalenti del progetto Laminas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>libreria</td>
    <td>Iniezione di dipendenza automatica per contenitori PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escape</a>
    </td>
    <td>libreria</td>
    <td>Esc in modo sicuro e sicuro di HTML, attributi di HTML, JavaScript, CSS e URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>libreria</td>
    <td>Attivazione e ascolto di eventi all’interno di un’applicazione PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">Alimentazione laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td>fornisce funzionalità per la creazione e il consumo di feed RSS e Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>libreria</td>
    <td>Fornisce un'interfaccia semplice per l'esecuzione delle richieste HTTP (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>libreria</td>
    <td>fornisce metodi di convenienza per serializzare PHP nativo su JSON e decodificare JSON su PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminati/caricatori</a>
    </td>
    <td>libreria</td>
    <td>Strategie di caricamento automatico e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>libreria</td>
    <td>Offre funzionalità generalizzate per la composizione e l’invio di messaggi di posta elettronica multiparte conformi a MIME e testo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>libreria</td>
    <td>Creare e analizzare messaggi e parti MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>libreria</td>
    <td>Sistema di applicazione modulare per applicazioni laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>libreria</td>
    <td>Livello MVC basato su eventi di Laminas, tra cui applicazioni MVC, controller e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-ricontcha</a>
    </td>
    <td>libreria</td>
    <td>wrapper OOP per il servizio Web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">router laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td>Sistema di routing flessibile per le applicazioni HTTP e console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">server laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td>Creare server RPC basati su riflessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>libreria</td>
    <td>Contenitore di iniezione a dipendenza guidata dalla fabbrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">sessione laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia orientata agli oggetti per le sessioni PHP e lo storage</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">Sapone laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>libreria</td>
    <td>Estensioni SPL, utilità array, gestori di errori e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>libreria</td>
    <td>Creazione di FIGlets e tabelle basate su testo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>libreria</td>
    <td>Componente che facilita la manipolazione e la convalida degli URI (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>libreria</td>
    <td>Classi di convalida per un'ampia gamma di domini e possibilità di catena di convalida per creare criteri di convalida complessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">vista laminas/laminas</a>
    </td>
    <td>libreria</td>
    <td>Livello di visualizzazione flessibile che supporta e fornisce più livelli di visualizzazione, aiutanti e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>libreria</td>
    <td>Alias i nomi delle classi ZF legacy agli equivalenti del progetto Laminas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>libreria</td>
    <td>Un parser PHP scritto in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>libreria</td>
    <td>Minificatore Javascript costruito in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>libreria</td>
    <td>Una porta PHP del compressore CSS YUI</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-o successivo

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>libreria</td>
    <td>Filtro HTML conforme agli standard scritto in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>libreria</td>
    <td>Precedentemente videlalvaro/php-amqplib.  Questa libreria è un'implementazione PHP pura del protocollo AMQP. È stato testato contro RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>libreria</td>
    <td>Braintree libreria client PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">mattoni/matematica</a>
    </td>
    <td>libreria</td>
    <td>Libreria arbitmetica di precisione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">mattoni/varesportatore</a>
    </td>
    <td>libreria</td>
    <td>Una potente alternativa a var_export(), che può esportare chiusure e oggetti senza __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">cristiano-riesen/base32</a>
    </td>
    <td>libreria</td>
    <td>Codificatore/decodificatore Base32 in base alla RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>libreria</td>
    <td>Credis è un'interfaccia leggera allo store a valore chiave Redis che avvolge la libreria phpredis quando disponibile per prestazioni migliori.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">compositore/ca-bundle</a>
    </td>
    <td>libreria</td>
    <td>Consente di trovare un percorso al bundle CA del sistema e include un fallback al bundle Mozilla CA.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">compositore/compositore</a>
    </td>
    <td>libreria</td>
    <td>Il Compositore ti aiuta a dichiarare, gestire e installare le dipendenze dei progetti PHP. Ti assicura di avere la giusta pila ovunque.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">compositore/minatore di metadati</a>
    </td>
    <td>libreria</td>
    <td>Libreria di utilità piccola che gestisce la minimizzazione e l'espansione dei metadati.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositore/pcre</a>
    </td>
    <td>libreria</td>
    <td>Libreria di wrapping PCRE che offre sostituzioni tipo-safe preg_*.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositore/semver</a>
    </td>
    <td>libreria</td>
    <td>Libreria di segmenti che offre utilità, analisi dei vincoli di versione e convalida.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">compositore/licenze spdx</a>
    </td>
    <td>libreria</td>
    <td>Elenco licenze SPDX e libreria di convalida.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">compositore/xdebug-handler</a>
    </td>
    <td>libreria</td>
    <td>Riavvia un processo senza Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>libreria</td>
    <td>Codice QR Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>libreria</td>
    <td>Forchetta di guzzle/ruscelli (abbandonati) da utilizzare con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>libreria</td>
    <td>Forchetta di guzzle/RingPHP (abbandonata) da utilizzare con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpans1</a>
    </td>
    <td>libreria</td>
    <td>Framework PHP che consente di codificare e decodificare strutture ASN.1 arbitrarie utilizzando le regole di codifica ITU-T X.690.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>libreria</td>
    <td>Guzzle è una libreria client HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promesse</a>
    </td>
    <td>libreria</td>
    <td>Libreria promesse Guzzle</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>libreria</td>
    <td>Implementazione del messaggio PSR-7 che fornisce anche metodi di utilità comuni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>libreria</td>
    <td>Una libreria per convalidare uno schema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">league/flysystem</a>
    </td>
    <td>libreria</td>
    <td>astrazione archiviazione file per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">lega/flysystem-aws-s3-v3</a>
    </td>
    <td>libreria</td>
    <td>Adattatore di file system AWS S3 per Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">rilevamento a campionato/mime</a>
    </td>
    <td>libreria</td>
    <td>Rilevamento di tipo mime per il sistema a molla</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monologo/monologo</a>
    </td>
    <td>libreria</td>
    <td>Invia i log a file, socket, caselle in entrata, database e vari servizi Web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>libreria</td>
    <td>Specificare in modo dichiarativo come estrarre gli elementi da un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">Codifica paragon/tempo_costante</a>
    </td>
    <td>libreria</td>
    <td>Implementazioni in tempo reale della codifica RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragon e/random_compat</a>
    </td>
    <td>libreria</td>
    <td>polyfill PHP 5.x per random_byte() e random_int() da PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogfier</a>
    </td>
    <td>libreria</td>
    <td>Converte gli stili CSS in attributi di stile in linea nel codice HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>libreria</td>
    <td>Converti selettori CSS in query XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>libreria</td>
    <td>L’API DOM moderna per i progetti PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>libreria</td>
    <td>polyfill PHP 5.x-8.x per estensione mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>libreria</td>
    <td>Libreria di comunicazioni sicure PHP - Implementazioni Pure-PHP di RSA, AES, SSH2, SFTP, X.509, ecc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia contenitore comune (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>libreria</td>
    <td>Interfacce standard per la gestione degli eventi.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune per i client HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>libreria</td>
    <td>Interfacce comuni per le fabbriche di messaggi HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune per i messaggi HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune per le librerie di log</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>libreria</td>
    <td>Un polyfill per getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collezione</a>
    </td>
    <td>libreria</td>
    <td>Una libreria PHP per rappresentare e manipolare le raccolte.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP per la generazione e l’utilizzo di identificatori univoci universali (UUID).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">react/promise</a>
    </td>
    <td>libreria</td>
    <td>Implementazione leggera di CommonJS Promises/A per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">baco di sabbro/php-css-parser</a>
    </td>
    <td>libreria</td>
    <td>Parser per file CSS scritti in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>libreria</td>
    <td>Linter JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>libreria</td>
    <td>Utilità di formato file PHAR, per quando PHP ti fa phars up</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>libreria</td>
    <td>AES Key Wrap per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP di base per codifica e decodifica sicura URL 64</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>libreria</td>
    <td>Una libreria PHP per la generazione di password una tantum in base alla RFC 4226 (algoritmo HOTP) e alla RFC 6238 (algoritmo TOTP) e compatibile con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>libreria</td>
    <td>Consente di trovare, caricare, combinare, compilare automaticamente e convalidare i valori di configurazione di qualsiasi tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>libreria</td>
    <td>Facilita la creazione di interfacce a riga di comando belle e testabili</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>libreria</td>
    <td>Converte i selettori CSS in espressioni XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/debug.git">symfony/debug</a>
    </td>
    <td>libreria</td>
    <td>Fornisce gli strumenti per facilitare il debug del codice PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">sinfonia/dipendenza-iniezione</a>
    </td>
    <td>libreria</td>
    <td>Consente di standardizzare e centralizzare il modo in cui gli oggetti vengono costruiti nell’applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecazione-contratti</a>
    </td>
    <td>libreria</td>
    <td>Funzione e convenzione generiche per attivare avvisi di obsolescenza</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>libreria</td>
    <td>Fornisce gli strumenti per gestire gli errori e facilitare il debug del codice PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>libreria</td>
    <td>Fornisce strumenti che consentono ai componenti dell'applicazione di comunicare tra loro inviando eventi e ascoltando gli stessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-contratti</a>
    </td>
    <td>libreria</td>
    <td>astrazioni generiche relative all’evento di invio</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>libreria</td>
    <td>Fornisce utilità di base per il filesystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>libreria</td>
    <td>Trova file e directory tramite un’interfaccia intuitiva e fluente</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-Contract</a>
    </td>
    <td>libreria</td>
    <td>astrazioni generiche relative ai client HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>libreria</td>
    <td>Definisce un livello orientato agli oggetti per la specifica HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>libreria</td>
    <td>Fornisce un processo strutturato per la conversione di una richiesta in una risposta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>libreria</td>
    <td>polyfill Symfony per funzioni di tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>libreria</td>
    <td>polyfill Symfony per le funzioni idn_to_ascii e idn_to_utf8 di intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizzatore</a>
    </td>
    <td>libreria</td>
    <td>polyfill Symfony per la classe Normalizer di intl e le relative funzioni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>libreria</td>
    <td>polyfill Symfony per l'estensione Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>libreria</td>
    <td>Symfony polifill backporting alcune funzionalità PHP 7.2+ per abbassare le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>libreria</td>
    <td>Symfony polifill backporting alcune funzionalità PHP 7.3+ per abbassare le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>libreria</td>
    <td>Symfony polifill backporting alcune funzionalità PHP 8.0+ per abbassare le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>libreria</td>
    <td>Symfony polifill backporting alcune funzionalità PHP 8.1+ per abbassare le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">sinfonia/processo</a>
    </td>
    <td>libreria</td>
    <td>Esegue i comandi nei sottoprocessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/contratti di servizio</a>
    </td>
    <td>libreria</td>
    <td>astrazioni generiche relative ai servizi di scrittura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>libreria</td>
    <td>Fornisce meccanismi per attraversare qualsiasi variabile PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">macchinario/cassaforte</a>
    </td>
    <td>libreria</td>
    <td>Funzioni di base PHP che generano eccezioni invece di restituire FALSE in caso di errore</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>Libreria JSON Object Signing and Encryption per PHP e Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>libreria</td>
    <td>Asserzioni per convalidare l'input/output del metodo con bei messaggi di errore.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>libreria</td>
    <td>Una porta PHP per l'implementazione di riferimento di GraphQL</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/modulo-braintree-graph-ql
    </td>
    <td>modulo magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      temando/modulo-shipping-remover
    </td>
    <td>modulo magento2</td>
    <td>Rimuove l’estensione di spedizione per più vettori Temando dal Magento 2</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      spedizione temporanea/modulo
    </td>
    <td>metapackage</td>
    <td>Estensione della spedizione multi-carrier Temando per il Magento 2</td>
  </tr>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>libreria</td>
    <td>Codificatore CBOR per PHP</td>
  </tr>
  </tbody>
</table>

### proprietario

<table>
  <thead>
    <tr>
      <th>Nome</th>
      <th>Tipo</th>
      <th>Descrizione</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/modulo-braintree-core
    </td>
    <td>modulo magento2</td>
    <td>Fork dal modulo Magento Braintree 2.2.0 di Gene Commerce per PayPal.</td>
  </tr>
  </tbody>
</table>

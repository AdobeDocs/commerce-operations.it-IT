---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---
# Pacchetti Magento Open Source

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Il Magento Open Source utilizza Composer per gestire i pacchetti PHP.

Il file `composer.json` dichiara l&#39;elenco dei pacchetti, mentre il file `composer.lock` memorizza un elenco completo dei pacchetti (una versione completa di ciascun pacchetto e delle relative dipendenze) utilizzati per creare un&#39;installazione di Magento Open Source.

La seguente documentazione di riferimento è generata dal file `composer.lock` e riguarda i pacchetti richiesti inclusi nel Magento Open Source 2.4.7-p1.

## Dipendenze

`magento/product-community-edition 2.4.7-p1` ha le seguenti dipendenze:

```config
adobe-commerce/os-extensions-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ~1.5.3
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
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
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.17
laminas/laminas-code: ^4.13
laminas/laminas-db: ^2.19
laminas/laminas-di: ^3.13
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-file: ^2.13
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-oauth: ^2.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.16
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.10.0-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.7-p1
magento/framework-amqp: 100.4.5
magento/framework-bulk: 101.0.3
magento/framework-message-queue: 100.4.7
magento/inventory-metapackage: 1.2.7-p1
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento2-base: 2.4.7-p1
magento/module-admin-analytics: 100.4.6
magento/module-admin-notification: 100.4.6
magento/module-advanced-pricing-import-export: 100.4.7
magento/module-advanced-search: 100.4.5
magento/module-amqp: 100.4.4
magento/module-analytics: 100.4.7
magento/module-application-performance-monitor: 100.4.0
magento/module-application-performance-monitor-new-relic: 100.4.0
magento/module-async-config: 100.4.0
magento/module-asynchronous-operations: 100.4.7
magento/module-authorization: 100.4.7
magento/module-aws-s3: 100.4.5
magento/module-backend: 102.0.7
magento/module-backup: 100.4.7
magento/module-bundle: 101.0.7
magento/module-bundle-graph-ql: 100.4.7
magento/module-bundle-import-export: 100.4.6
magento/module-cache-invalidate: 100.4.5
magento/module-captcha: 100.4.7
magento/module-cardinal-commerce: 100.4.5
magento/module-catalog: 104.0.7-p1
magento/module-catalog-analytics: 100.4.4
magento/module-catalog-cms-graph-ql: 100.4.3
magento/module-catalog-customer-graph-ql: 100.4.6
magento/module-catalog-graph-ql: 100.4.7
magento/module-catalog-import-export: 101.1.7
magento/module-catalog-inventory: 100.4.7
magento/module-catalog-inventory-graph-ql: 100.4.4
magento/module-catalog-rule: 101.2.7
magento/module-catalog-rule-configurable: 100.4.6
magento/module-catalog-rule-graph-ql: 100.4.4
magento/module-catalog-search: 102.0.7
magento/module-catalog-url-rewrite: 100.4.7
magento/module-catalog-url-rewrite-graph-ql: 100.4.5
magento/module-catalog-widget: 100.4.7
magento/module-checkout: 100.4.7
magento/module-checkout-agreements: 100.4.6
magento/module-checkout-agreements-graph-ql: 100.4.3
magento/module-cms: 104.0.7
magento/module-cms-graph-ql: 100.4.4
magento/module-cms-url-rewrite: 100.4.6
magento/module-cms-url-rewrite-graph-ql: 100.4.5
magento/module-compare-list-graph-ql: 100.4.3
magento/module-config: 101.2.7
magento/module-configurable-import-export: 100.4.5
magento/module-configurable-product: 100.4.7
magento/module-configurable-product-graph-ql: 100.4.7
magento/module-configurable-product-sales: 100.4.4
magento/module-contact: 100.4.6
magento/module-contact-graph-ql: 100.4.0
magento/module-cookie: 100.4.7
magento/module-cron: 100.4.7
magento/module-csp: 100.4.6
magento/module-currency-symbol: 100.4.5
magento/module-customer: 103.0.7-p1
magento/module-customer-analytics: 100.4.4
magento/module-customer-downloadable-graph-ql: 100.4.3
magento/module-customer-graph-ql: 100.4.7
magento/module-customer-import-export: 100.4.7
magento/module-deploy: 100.4.7
magento/module-developer: 100.4.7
magento/module-dhl: 100.4.6
magento/module-directory: 100.4.7
magento/module-directory-graph-ql: 100.4.5
magento/module-downloadable: 100.4.7
magento/module-downloadable-graph-ql: 100.4.7
magento/module-downloadable-import-export: 100.4.6
magento/module-eav: 102.1.7
magento/module-eav-graph-ql: 100.4.4
magento/module-elasticsearch: 101.0.7
magento/module-elasticsearch-7: 100.4.7
magento/module-email: 101.1.7
magento/module-encryption-key: 100.4.5
magento/module-fedex: 100.4.5
magento/module-gift-message: 100.4.6
magento/module-gift-message-graph-ql: 100.4.5
magento/module-google-adwords: 100.4.4
magento/module-google-analytics: 100.4.3
magento/module-google-gtag: 100.4.2
magento/module-google-optimizer: 100.4.6
magento/module-graph-ql: 100.4.7
magento/module-graph-ql-cache: 100.4.4
magento/module-graph-ql-new-relic: 100.4.0
magento/module-graph-ql-resolver-cache: 100.4.0
magento/module-grouped-catalog-inventory: 100.4.4
magento/module-grouped-import-export: 100.4.5
magento/module-grouped-product: 100.4.7
magento/module-grouped-product-graph-ql: 100.4.7
magento/module-import-export: 101.0.7
magento/module-indexer: 100.4.7
magento/module-instant-purchase: 100.4.6
magento/module-integration: 100.4.7
magento/module-integration-graph-ql: 100.4.0
magento/module-jwt-framework-adapter: 100.4.3
magento/module-jwt-user-token: 100.4.2
magento/module-layered-navigation: 100.4.7
magento/module-login-as-customer: 100.4.7
magento/module-login-as-customer-admin-ui: 100.4.7
magento/module-login-as-customer-api: 100.4.6
magento/module-login-as-customer-assistance: 100.4.6
magento/module-login-as-customer-frontend-ui: 100.4.6
magento/module-login-as-customer-graph-ql: 100.4.4
magento/module-login-as-customer-log: 100.4.5
magento/module-login-as-customer-page-cache: 100.4.6
magento/module-login-as-customer-quote: 100.4.5
magento/module-login-as-customer-sales: 100.4.6
magento/module-marketplace: 100.4.5
magento/module-media-content: 100.4.5
magento/module-media-content-api: 100.4.6
magento/module-media-content-catalog: 100.4.5
magento/module-media-content-cms: 100.4.5
magento/module-media-content-synchronization: 100.4.6
magento/module-media-content-synchronization-api: 100.4.5
magento/module-media-content-synchronization-catalog: 100.4.4
magento/module-media-content-synchronization-cms: 100.4.4
magento/module-media-gallery: 100.4.6
magento/module-media-gallery-api: 101.0.6
magento/module-media-gallery-catalog: 100.4.4
magento/module-media-gallery-catalog-integration: 100.4.4
magento/module-media-gallery-catalog-ui: 100.4.4
magento/module-media-gallery-cms-ui: 100.4.4
magento/module-media-gallery-integration: 100.4.6
magento/module-media-gallery-metadata: 100.4.5
magento/module-media-gallery-metadata-api: 100.4.4
magento/module-media-gallery-renditions: 100.4.5
magento/module-media-gallery-renditions-api: 100.4.4
magento/module-media-gallery-synchronization: 100.4.6
magento/module-media-gallery-synchronization-api: 100.4.5
magento/module-media-gallery-synchronization-metadata: 100.4.3
magento/module-media-gallery-ui: 100.4.6
magento/module-media-gallery-ui-api: 100.4.5
magento/module-media-storage: 100.4.6
magento/module-message-queue: 100.4.7
magento/module-msrp: 100.4.6
magento/module-msrp-configurable-product: 100.4.4
magento/module-msrp-grouped-product: 100.4.4
magento/module-multishipping: 100.4.7
magento/module-mysql-mq: 100.4.5
magento/module-new-relic-reporting: 100.4.5
magento/module-newsletter: 100.4.7
magento/module-newsletter-graph-ql: 100.4.4
magento/module-offline-payments: 100.4.5
magento/module-offline-shipping: 100.4.6
magento/module-open-search: 100.4.1
magento/module-order-cancellation: 100.4.0
magento/module-order-cancellation-graph-ql: 100.4.0
magento/module-order-cancellation-ui: 100.4.0
magento/module-page-cache: 100.4.7
magento/module-payment: 100.4.7
magento/module-payment-graph-ql: 100.4.2
magento/module-paypal: 101.0.7
magento/module-paypal-captcha: 100.4.4
magento/module-paypal-graph-ql: 100.4.5
magento/module-persistent: 100.4.7
magento/module-product-alert: 100.4.6
magento/module-product-video: 100.4.7
magento/module-quote: 101.2.7-p1
magento/module-quote-analytics: 100.4.6
magento/module-quote-bundle-options: 100.4.3
magento/module-quote-configurable-options: 100.4.3
magento/module-quote-downloadable-links: 100.4.3
magento/module-quote-graph-ql: 100.4.7
magento/module-related-product-graph-ql: 100.4.4
magento/module-release-notification: 100.4.5
magento/module-remote-storage: 100.4.5
magento/module-reports: 100.4.7
magento/module-require-js: 100.4.3
magento/module-review: 100.4.7
magento/module-review-analytics: 100.4.4
magento/module-review-graph-ql: 100.4.3
magento/module-robots: 101.1.3
magento/module-rss: 100.4.5
magento/module-rule: 100.4.6
magento/module-sales: 103.0.7-p1
magento/module-sales-analytics: 100.4.4
magento/module-sales-graph-ql: 100.4.7
magento/module-sales-inventory: 100.4.4
magento/module-sales-rule: 101.2.7
magento/module-sales-rule-graph-ql: 100.4.0
magento/module-sales-sequence: 100.4.4
magento/module-sample-data: 100.4.5
magento/module-search: 101.1.7
magento/module-security: 100.4.7
magento/module-send-friend: 100.4.5
magento/module-send-friend-graph-ql: 100.4.3
magento/module-shipping: 100.4.7
magento/module-sitemap: 100.4.6
magento/module-store: 101.1.7
magento/module-store-graph-ql: 100.4.5
magento/module-swagger: 100.4.6
magento/module-swagger-webapi: 100.4.3
magento/module-swagger-webapi-async: 100.4.3
magento/module-swatches: 100.4.7
magento/module-swatches-graph-ql: 100.4.5
magento/module-swatches-layered-navigation: 100.4.3
magento/module-tax: 100.4.7
magento/module-tax-graph-ql: 100.4.3
magento/module-tax-import-export: 100.4.6
magento/module-theme: 101.1.7
magento/module-theme-graph-ql: 100.4.4
magento/module-translation: 100.4.7
magento/module-ui: 101.2.7
magento/module-ups: 100.4.7-p1
magento/module-url-rewrite: 102.0.6
magento/module-url-rewrite-graph-ql: 100.4.6
magento/module-user: 101.2.7
magento/module-usps: 100.4.6
magento/module-variable: 100.4.5
magento/module-vault: 101.2.7
magento/module-vault-graph-ql: 100.4.3
magento/module-version: 100.4.4
magento/module-webapi: 100.4.6-p1
magento/module-webapi-async: 100.4.5
magento/module-webapi-security: 100.4.4
magento/module-weee: 100.4.7
magento/module-weee-graph-ql: 100.4.4
magento/module-widget: 101.2.7
magento/module-wishlist: 101.2.7
magento/module-wishlist-analytics: 100.4.5
magento/module-wishlist-graph-ql: 100.4.7
magento/page-builder: 1.7.4-p1
magento/security-package: 1.1.6-p1
magento/theme-adminhtml-backend: 100.4.7-p1
magento/theme-frontend-blank: 100.4.7-p1
magento/theme-frontend-luma: 100.4.7-p1
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0||~8.3.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

## Licenze di terze parti

### Apache-2.0, solo LGPL-2.1

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
    <td>Client PHP, ad Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>libreria</td>
    <td>Client PHP per OpenSearch</td>
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
    <td>Common Runtime di AWS per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>libreria</td>
    <td>SDK di AWS per PHP - Utilizzare Amazon Web Services nel progetto PHP</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>metapacchetto</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>libreria</td>
    <td>Porta PHP del processore LESS</td>
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
    <td>BaconQrCode è un generatore di codici QR per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>libreria</td>
    <td>Implementazione PHP 7.1 enum</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>libreria</td>
    <td>Strumento per scrivere i file in modo sicuro, per evitare race condition</td>
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
    <td>Il backend Zend_Cache_Backend_File di magazzino ha prestazioni estremamente scadenti per la pulizia da parte dei tag, rendendolo inutilizzabile con l’aumento del numero di elementi memorizzati in cache. Questo back-end apporta molte modifiche che determinano un notevole miglioramento delle prestazioni, in particolare per la pulizia dei tag.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>libreria</td>
    <td>Un gestore di sessione basato su Redis con blocco ottimistico</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>libreria</td>
    <td>Una semplice libreria per codificare e decodificare i token web JSON (JWT) in PHP. Deve essere conforme alla specifica corrente.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>libreria</td>
    <td>Libreria client per reCAPTCHA, un servizio gratuito che protegge i siti web da spam e utilizzo non corretto.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>libreria</td>
    <td>Generare e convalidare i CAPTCHA utilizzando figure, immagini, ReCaptcha e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>libreria</td>
    <td>Estensioni dell'API PHP Reflection, scansione del codice statico e generazione del codice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>libreria</td>
    <td>fornisce un'interfaccia utente basata su proprietà di oggetto nidificato per accedere ai dati di configurazione nel codice dell'applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>libreria</td>
    <td>Potenti strumenti di crittografia e hashing delle password</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>libreria</td>
    <td>Livello di astrazione del database, astrazione SQL, astrazione del set di risultati e implementazioni RowDataGateway e TableDataGateway</td>
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
    <td>Escape sicuro di HTML, attributi HTML, JavaScript, CSS e URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>libreria</td>
    <td>Attivare e ascoltare gli eventi all'interno di un'applicazione PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>libreria</td>
    <td>fornisce funzionalità per creare e utilizzare feed RSS e Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>libreria</td>
    <td>Individuazione dei file di classe PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">laminas/laminas-filter</a>
    </td>
    <td>libreria</td>
    <td>Filtrare e normalizzare a livello di programmazione dati e file</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia semplice per l'esecuzione di richieste HTTP (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>libreria</td>
    <td>Fornisci le traduzioni per la tua applicazione, e filtra e convalida i valori internazionalizzati</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>libreria</td>
    <td>fornisce metodi di convenienza per serializzare da PHP nativo a JSON e decodificare da JSON a PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>libreria</td>
    <td>Strategie di caricamento automatico e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>libreria</td>
    <td>Fornisce funzionalità generalizzate per la composizione e l'invio di messaggi di posta elettronica in più parti sia di testo che compatibili con MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>libreria</td>
    <td>Creazione di numeri pseudo-casuali protetti da crittografia e gestione di numeri interi di grandi dimensioni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>libreria</td>
    <td>Creare e analizzare parti e messaggi MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>libreria</td>
    <td>Sistema modulare per applicazioni laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>libreria</td>
    <td>Livello MVC basato su eventi di Laminas, incluse applicazioni MVC, controller e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>libreria</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>libreria</td>
    <td>Implementazione di un elenco di controllo di accesso (ACL) leggero e flessibile per la gestione dei privilegi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>libreria</td>
    <td>Wrapper OOP per il servizio Web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>libreria</td>
    <td>Sistema di routing flessibile per applicazioni HTTP e console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>libreria</td>
    <td>Creazione di server RPC basati su riflessioni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>libreria</td>
    <td>Contenitore Di Iniezione Di Dipendenza Basato Su Fabbrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia orientata agli oggetti per sessioni PHP e storage</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminati/sapone laminato</a>
    </td>
    <td>libreria</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>libreria</td>
    <td>Estensioni SPL, utility di array, gestori di errori e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>libreria</td>
    <td>Creare i file FIGlet e le tabelle basate su testo</td>
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
    <td>Classi di convalida per un'ampia gamma di domini e possibilità di concatenare le convalide per creare criteri di convalida complessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>libreria</td>
    <td>Livello di vista flessibile che supporta e fornisce più livelli di vista, helper e altro ancora</td>
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
    <td>PHP integrato nel minifier JavaScript</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>libreria</td>
    <td>Porta PHP del compressore CSS YUI</td>
  </tr>
  </tbody>
</table>

### Modifica clausola BSD-3

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>modulo magento</td>
    <td>Zend_Cache back-end che utilizza Redis con supporto completo per i tag.</td>
  </tr>
  </tbody>
</table>

### ISC

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
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/sodio_compat</a>
    </td>
    <td>libreria</td>
    <td>Pura implementazione PHP di libsodium; utilizza l’estensione PHP, se presente</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-or-later

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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurificer</a>
    </td>
    <td>libreria</td>
    <td>Filtro HTML conforme agli standard scritto in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>libreria</td>
    <td>Ex videlalvaro/php-amqplib.  Questa libreria è un’implementazione PHP pura del protocollo AMQP. È stato testato contro RabbitMQ.</td>
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
      <a href="https://github.com/braintree/braintree_php.git">albero del cervello/albero del cervello_php</a>
    </td>
    <td>libreria</td>
    <td>Braintree libreria client PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">brick/matematica</a>
    </td>
    <td>libreria</td>
    <td>Libreria aritmetica di precisione arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>libreria</td>
    <td>Una potente alternativa a var_export(), che può esportare chiusure e oggetti senza __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">cristiano-riesen/base32</a>
    </td>
    <td>libreria</td>
    <td>Codificatore/decodificatore Base32 secondo RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>libreria</td>
    <td>Credis è un’interfaccia leggera dell’archivio Redis di valori chiave che racchiude la libreria phpredis quando disponibile per prestazioni migliori.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">compositore/ca-bundle</a>
    </td>
    <td>libreria</td>
    <td>Consente di trovare un percorso per il bundle CA di sistema e include un fallback al bundle CA di Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">compositore/class-map-generator</a>
    </td>
    <td>libreria</td>
    <td>Utilità per scansionare il codice PHP e generare mappe di classe.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">compositore/compositore</a>
    </td>
    <td>libreria</td>
    <td>Composer consente di dichiarare, gestire e installare le dipendenze dei progetti PHP. Ti garantisce di avere la giusta pila ovunque.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">compositore/minificatore metadati</a>
    </td>
    <td>libreria</td>
    <td>Piccola libreria di utilità che gestisce la minimizzazione e l'espansione dei metadati.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositore/pcre</a>
    </td>
    <td>libreria</td>
    <td>Libreria di wrapping PCRE che offre sostituzioni preg_* di tipo sicuro.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositore/semver</a>
    </td>
    <td>libreria</td>
    <td>Libreria semver che offre utility, analisi e convalida dei vincoli di versione.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">licenze compositore/spdx</a>
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
    <td>Forcella di guzzle/ruscelli (abbandonati) da utilizzare con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>libreria</td>
    <td>Forchetta di guzzle/RingPHP (abbandonato) da utilizzare con elasticsearch-php</td>
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
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promise</a>
    </td>
    <td>libreria</td>
    <td>Libreria Guzzle promesse</td>
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
      <a href="https://github.com/jsonrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>libreria</td>
    <td>Libreria per convalidare uno schema JSON.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">lega/flysystem</a>
    </td>
    <td>libreria</td>
    <td>Estrazione archiviazione file per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>libreria</td>
    <td>Scheda di file system AWS S3 per Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-detection</a>
    </td>
    <td>libreria</td>
    <td>Rilevamento del tipo MIME per Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monologo/monologo</a>
    </td>
    <td>libreria</td>
    <td>Invia i registri a file, socket, caselle in entrata, database e vari servizi web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>libreria</td>
    <td>Specificare in modo dichiarativo come estrarre elementi da un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>libreria</td>
    <td>Implementazioni a tempo costante della codifica RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>libreria</td>
    <td>polyfill PHP 5.x per random_bytes() e random_int() da PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emoglificatore</a>
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
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>libreria</td>
    <td>Funzioni della funzione di accesso alle proprietà e del mutatore.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>libreria</td>
    <td>Poliriempimento PHP 5.x-8.x per estensione mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP Secure Communications: implementazioni Pure-PHP di RSA, AES, SSH2, SFTP, X.509 ecc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune per il caching delle librerie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune per la lettura dell'orologio.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>libreria</td>
    <td>Interfaccia comune dei contenitori (PHP FIG PSR-11)</td>
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
    <td>PSR-17: interfacce comuni per i message factory HTTP PSR-7</td>
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
    <td>Interfaccia comune per le librerie di registrazione</td>
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
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP per la rappresentazione e la manipolazione delle raccolte.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP per la generazione e l’utilizzo di identificatori universalmente univoci (UUID).</td>
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
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
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
    <td>PHAR formato file utilità, per quando PHP phars si up</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>libreria</td>
    <td>Semplice gestore di segnali unix che genera un errore silenzioso quando i segnali non sono supportati per un facile sviluppo su più piattaforme</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>libreria</td>
    <td>Key Wrap AES per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>libreria</td>
    <td>Libreria PHP per la generazione di password monouso secondo l'RFC 4226 (HOTP Algorithm) e l'RFC 6238 (TOTP Algorithm) e compatibile con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>libreria</td>
    <td>Un framework PHP per la gestione dell'infrastruttura a chiave pubblica. Comprende certificati a chiave pubblica X.509, certificati di attributi, richieste di certificazione e convalida del percorso di certificazione.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>libreria</td>
    <td>Consente di trovare, caricare, combinare, riempire automaticamente e convalidare i valori di configurazione di qualsiasi tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>libreria</td>
    <td>Semplifica la creazione di interfacce per riga di comando belle e testabili</td>
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
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependency-injection</a>
    </td>
    <td>libreria</td>
    <td>Consente di standardizzare e centralizzare il modo in cui gli oggetti vengono costruiti nell'applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-CONTRACTS</a>
    </td>
    <td>libreria</td>
    <td>Funzione e convenzione generiche per attivare gli avvisi di deprecazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>libreria</td>
    <td>Fornisce strumenti per gestire gli errori e facilitare il debug del codice PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>libreria</td>
    <td>Fornisce strumenti che consentono ai componenti dell'applicazione di comunicare tra loro inviando eventi e ascoltandoli</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-CONTRACTS</a>
    </td>
    <td>libreria</td>
    <td>Astrazioni generiche correlate all’evento dispatching</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>libreria</td>
    <td>Fornisce utilità di base per il file system</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>libreria</td>
    <td>Trova file e directory tramite un'interfaccia intuitiva</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>libreria</td>
    <td>Fornisce potenti metodi per recuperare le risorse HTTP in modo sincrono o asincrono</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-CONTRACTS</a>
    </td>
    <td>libreria</td>
    <td>Astrazioni generiche correlate ai client HTTP</td>
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
    <td>Fornisce un processo strutturato per convertire una richiesta in una risposta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>libreria</td>
    <td>Consente di accedere ai dati di localizzazione della libreria ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill per funzioni di tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill per le funzioni grapheme_* di intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill per le funzioni intl idn_to_ascii e idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill per la classe Normalizer di intl e funzioni correlate</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill per l’estensione Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 7.2+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 7.3+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.0+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.1+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.3+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>libreria</td>
    <td>Esegue comandi nei sottoprocessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-CONTRACTS</a>
    </td>
    <td>libreria</td>
    <td>Astrazioni generiche relative ai servizi di scrittura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>libreria</td>
    <td>Fornisce un’API orientata agli oggetti per stringhe e tratta byte, punti di codice UTF-8 e cluster di grafemi in modo unificato</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>libreria</td>
    <td>Fornisce meccanismi per passare attraverso qualsiasi variabile PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>libreria</td>
    <td>Consente l'esportazione di qualsiasi struttura di dati PHP serializzabile nel codice PHP normale</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>Libreria di firma di oggetti e crittografia JSON per PHP e Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>libreria</td>
    <td>Asserzioni per convalidare l’input/output del metodo con messaggi di errore validi.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>libreria</td>
    <td>Una porta PHP dell'implementazione di riferimento GraphQL</td>
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
      paypal/module-braintree-customer-balance
    </td>
    <td>modulo magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>modulo magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>modulo magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>modulo magento2</td>
    <td>N/D</td>
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
      paypal/module-braintree-core
    </td>
    <td>modulo magento2</td>
    <td>Fork dal modulo Magento Braintree 2.2.0 di Gene Commerce per PayPal.</td>
  </tr>
  </tbody>
</table>

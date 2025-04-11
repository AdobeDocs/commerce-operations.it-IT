---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '2906'
ht-degree: 0%

---
# Pacchetti Adobe Commerce

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce utilizza Composer per gestire i pacchetti PHP.

Il file `composer.json` dichiara l&#39;elenco dei pacchetti, mentre il file `composer.lock` memorizza un elenco completo dei pacchetti (una versione completa di ciascun pacchetto e delle relative dipendenze) utilizzati per creare un&#39;installazione di Adobe Commerce.

La seguente documentazione di riferimento è generata dal file `composer.lock` e riguarda i pacchetti richiesti inclusi in Adobe Commerce 2.4.8.

## Dipendenze

`magento/product-enterprise-edition 2.4.8` ha le seguenti dipendenze:

- adobe-commerce/extensions-metapackage: 2.0.1
- colinmollenhour/cache-backend-file: ^1.4
- colinmollenhour/cache-backend-redis: ^1.16
- colinmollenhour/credis: ^1.15
- colinmollenhour/php-redis-session-abstract: ^2.0
- compositore/compositore: ^2.0, !=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1.0
- ricerca elastica/ricerca elastica: ^8.15
- int-bcmath: *
- ext-ctype: *
- int-curl: *
- dom esterno: *
- ext-ftp: *
- int-gd: *
- ext-hash: *
- ext-iconv: *
- int-int: *
- int-int: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- ext-soap: *
- int-sodio: *
- int-spl: *
- ext-xsl: *
- int. int.: *
- ezyang/htmlpurifier: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2,18
- Codice laminato: ^4.13
- laminas/laminas-di: ^3,15
- Fuga laminare: ^2.13
- laminas/laminas-eventmanager: ^3.11
- Alimentazione laminare: ^2.22
- Filtro laminare: ^2,33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2,17
- Laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3,6
- laminas/laminas-permissions-acl: ^2.10
- Laminas/laminas-servicemanager: ^3.16
- laminati/sapone laminato: ^2.10
- laminas/laminas-stdlib: ^3,11
- laminas/laminas-uri: ^2,9
- Convalida laminas: ^2.23
- lega/flysystem: ^3.0
- league/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/compositore: ^1.10.1-beta1
- magento/compositore-dependency-version-audit-plugin: ^0.1
- magento/framework-FOREIGN-KEY: 100.4.7
- magento/magento-compositore-installer: >=0,4,0
- magento/magento-zf-db: ^3.21
- magento/magento2-ee-base: 2.4.8
- [magento/module-admin-gws](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws/): 100.4.8
- [magento/module-admin-gws-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-configurable-product/): 100.4.5
- [magento/module-admin-gws-staging](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-staging/): 100.4.5
- [magento/module-advanced-catalog](https://developer.adobe.com/commerce/php/module-reference/module-advanced-catalog/): 100.4.5
- [magento/module-advanced-checkout](https://developer.adobe.com/commerce/php/module-reference/module-advanced-checkout/): 100.4.8
- [magento/module-advanced-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-rule/): 100.4.5
- [magento/module-advanced-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-sales-rule/): 100.4.5
- [magento/module-application-server](https://developer.adobe.com/commerce/php/module-reference/module-application-server/): 100.4.1
- [magento/module-application-server-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-server-new-relic/): 100.4.1
- [magento/module-application-server-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-performance-monitor/): 100.4.1
- [magento/module-application-server-state-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor/): 100.4.1
- [magento/module-application-server-state-monitor-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor-graph-ql/): 100.4.1
- [magento/module-async-order](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): 100.4.4
- [magento/module-async-order-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-async-order-graph-ql/): 100.4.3
- [magento/module-aws-s3-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-customer-custom-attributes/): 100.4.5
- [magento/module-aws-s3-gift-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-gift-card-import-export/): 100.4.5
- [magento/module-aws-s3-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-scheduled-import-export/): 100.4.5
- [magento/module-banner](https://developer.adobe.com/commerce/php/module-reference/module-banner/): 101.2.8
- [magento/module-banner-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-banner-customer-segment/): 100.4.6
- [magento/module-banner-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-banner-graph-ql/): 100.4.4
- [magento/module-banner-staging](https://developer.adobe.com/commerce/php/module-reference/module-banner-staging/): 100.4.2
- [magento/module-bundle-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export-staging/): 100.4.5
- [magento/module-bundle-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-staging/): 100.4.8
- [magento/module-catalog-event](https://developer.adobe.com/commerce/php/module-reference/module-catalog-event/): 101.1.7
- [magento/module-catalog-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export-staging/): 100.4.5
- [magento/module-catalog-inventory-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-staging/): 100.4.6
- [magento/module-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions/): 100.4.8
- [magento/module-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions-graph-ql/): 100.4.6
- [magento/module-catalog-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-staging/): 100.4.8
- [magento/module-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging/): 100.4.8
- [magento/module-catalog-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging-graph-ql/): 100.4.7
- [magento/module-catalog-url-rewrite-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-staging/): 100.4.7
- [magento/module-checkout-address-search](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search/): 100.4.7
- [magento/module-checkout-address-search-gift-registry](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search-gift-registry/): 100.4.4
- [magento/module-checkout-staging](https://developer.adobe.com/commerce/php/module-reference/module-checkout-staging/): 100.4.7
- [magento/module-cms-staging](https://developer.adobe.com/commerce/php/module-reference/module-cms-staging/): 100.4.8
- [magento/module-configurable-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-staging/): 100.4.7
- [magento/module-custom-attribute-management](https://developer.adobe.com/commerce/php/module-reference/module-custom-attribute-management/): 100.4.7
- [magento/module-customer-balance](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance/): 100.4.8
- [magento/module-customer-balance-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance-graph-ql/): 100.4.5
- [magento/module-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes/): 100.4.8
- [magento/module-customer-custom-attributes-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes-graph-ql/): 100.4.1
- [magento/module-customer-finance](https://developer.adobe.com/commerce/php/module-reference/module-customer-finance/): 100.4.5
- [magento/module-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment/): 102.1.8
- [magento/module-customer-segment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment-graph-ql/): 100.4.1
- [magento/module-deferred-total-calculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/): 100.4.3
- [magento/module-downloadable-staging](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-staging/): 100.4.7
- [magento/module-elasticsearch-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions/): 100.4.4
- [magento/module-elasticsearch-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions-graph-ql/): 100.4.3
- [magento/module-enterprise](https://developer.adobe.com/commerce/php/module-reference/module-enterprise/): 100.4.6
- [magento/module-gift-card](https://developer.adobe.com/commerce/php/module-reference/module-gift-card/): 101.3.8
- [magento/module-gift-card-account](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account/): 101.2.8
- [magento/module-gift-card-account-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account-graph-ql/): 100.4.6
- [magento/module-gift-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-graph-ql/): 100.4.8
- [magento/module-gift-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-import-export/): 100.4.5
- [magento/module-gift-card-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-staging/): 100.4.5
- [magento/module-gift-message-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-staging/): 100.4.5
- [magento/module-gift-registry](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry/): 101.2.8
- [magento/module-gift-registry-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry-graph-ql/): 100.4.4
- [magento/module-gift-wrapping](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping/): 101.2.7
- [magento/module-gift-wrapping-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-graph-ql/): 100.4.5
- [magento/module-gift-wrapping-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-staging/): 100.4.5
- [magento/module-google-optimizer-staging](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer-staging/): 100.4.5
- [magento/module-google-tag-manager](https://developer.adobe.com/commerce/php/module-reference/module-google-tag-manager/): 100.4.8
- [magento/module-grouped-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-staging/): 100.4.6
- [magento/module-import-csv](https://developer.adobe.com/commerce/php/module-reference/module-import-csv/): 100.4.2
- [magento/module-import-csv-api](https://developer.adobe.com/commerce/php/module-reference/module-import-csv-api/): 100.4.2
- [magento/module-import-json](https://developer.adobe.com/commerce/php/module-reference/module-import-json/): 100.4.1
- [magento/module-import-json-api](https://developer.adobe.com/commerce/php/module-reference/module-import-json-api/): 100.4.1
- [magento/modulo-invito](https://developer.adobe.com/commerce/php/module-reference/module-invitation/): 100.4.7
- [magento/module-layer-navigation-staging](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation-staging/): 100.4.5
- [magento/module-logging](https://developer.adobe.com/commerce/php/module-reference/module-logging/): 101.2.8
- [magento/module-login-as-customer-logging](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-logging/): 100.4.8
- [magento/module-login-as-customer-website-restrictions](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-website-restriction/): 100.4.6
- [magento/module-media-content-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog-staging/): 100.4.5
- [magento/module-msrp-staging](https://developer.adobe.com/commerce/php/module-reference/module-msrp-staging/): 100.4.6
- [magento/module-multicoupon](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon/): 100.4.1
- [magento/module-multicoupon-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-graph-ql/): 100.4.1
- [magento/module-multicoupon-ui](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-ui/): 100.4.1
- [magento/module-multiple-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist/): 100.4.8
- [magento/module-multiple-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist-graph-ql/): 100.4.4
- [magento/module-payment-staging](https://developer.adobe.com/commerce/php/module-reference/module-payment-staging/): 100.4.5
- [magento/module-persistent-history](https://developer.adobe.com/commerce/php/module-reference/module-persistent-history/): 100.4.5
- [magento/module-price-permissions](https://developer.adobe.com/commerce/php/module-reference/module-price-permissions/): 100.4.4
- [magento/module-product-video-staging](https://developer.adobe.com/commerce/php/module-reference/module-product-video-staging/): 100.4.5
- [magento/module-promotion-permissions](https://developer.adobe.com/commerce/php/module-reference/module-promotion-permissions/): 100.4.5
- [magento/module-quote-commerce-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-commerce-graph-ql/): 100.4.1
- [magento/module-quote-gift-card-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-gift-card-options/): 100.4.5
- [magento/module-quote-staging](https://developer.adobe.com/commerce/php/module-reference/module-quote-staging/): 100.4.5
- [magento/module-reminder](https://developer.adobe.com/commerce/php/module-reference/module-reminder/): 101.2.7
- [magento/module-remote-storage-commerce](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage-commerce/): 100.4.4
- [magento/module-resource-connections](https://developer.adobe.com/commerce/php/module-reference/module-resource-connections/): 100.4.5
- [magento/module-review-staging](https://developer.adobe.com/commerce/php/module-reference/module-review-staging/): 100.4.5
- [magento/module-reward](https://developer.adobe.com/commerce/php/module-reference/module-reward/): 101.2.8
- [magento/module-reward-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-reward-graph-ql/): 100.4.7
- [magento/module-reward-staging](https://developer.adobe.com/commerce/php/module-reference/module-reward-staging/): 100.4.5
- [magento/module-rma](https://developer.adobe.com/commerce/php/module-reference/module-rma/): 101.2.8
- [magento/module-rma-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-rma-graph-ql/): 100.4.7
- [magento/module-rma-staging](https://developer.adobe.com/commerce/php/module-reference/module-rma-staging/): 100.4.5
- [magento/module-sales-archive](https://developer.adobe.com/commerce/php/module-reference/module-sales-archive/): 101.0.6
- [magento/module-sales-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-staging/): 100.4.7
- [magento/module-scalable-checkout](https://developer.adobe.com/commerce/php/module-reference/module-scalable-checkout/): 100.4.7
- [magento/module-scalable-inventory](https://developer.adobe.com/commerce/php/module-reference/module-scalable-inventory/): 100.4.6
- [magento/module-scalable-oms](https://developer.adobe.com/commerce/php/module-reference/module-scalable-oms/): 100.4.6
- [magento/module-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-scheduled-import-export/): 101.2.8
- [magento/module-search-staging](https://developer.adobe.com/commerce/php/module-reference/module-search-staging/): 100.4.6
- [magento/module-staging](https://developer.adobe.com/commerce/php/module-reference/module-staging/): 101.2.8
- [magento/module-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-staging-graph-ql/): 100.4.5
- [magento/supporto modulo](https://developer.adobe.com/commerce/php/module-reference/module-support/): 101.2.7
- [magento/module-swat](https://developer.adobe.com/commerce/php/module-reference/module-swat/): 100.4.6
- [magento/module-target-rule](https://developer.adobe.com/commerce/php/module-reference/module-target-rule/): 101.2.8
- [magento/module-target-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-target-rule-graph-ql/): 100.4.5
- [magento/module-versions-cms](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms/): 101.2.8
- [magento/module-versions-cms-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-page-cache/): 100.4.4
- [magento/module-versions-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite/): 100.4.6
- [magento/module-versions-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite-graph-ql/): 100.4.4
- [magento/module-visual-merchandiser](https://developer.adobe.com/commerce/php/module-reference/module-visual-merchandiser/): 100.4.8
- [magento/module-webapi-rest-gws](https://developer.adobe.com/commerce/php/module-reference/module-webapi-rest-gws/): 100.4.0
- [magento/module-website-restrictions](https://developer.adobe.com/commerce/php/module-reference/module-website-restriction/): 100.4.7
- [magento/module-weee-staging](https://developer.adobe.com/commerce/php/module-reference/module-weee-staging/): 100.4.5
- [magento/module-wishlist-gift-card](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card/): 100.4.4
- [magento/module-wishlist-gift-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card-graph-ql/): 100.4.4
- magento/page-builder-commerce: 1.7.5
- magento/product-community-edition: 2.4.8
- magento/security-package-ee: 1.0.3
- magento/theme-adminhtml-spectrum: 100.4.3
- magento/zend-cache: ^1.16
- magento/zend-db: ^1,16
- magento/zend-pdf: ^1.16
- monologo/monologo: ^3.6
- opensearch-project/opensearch-php: ^2.3
- pelago/emoglificatore: ^7.0
- php: ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- symfony/mailer: ^6.4
- symfony/mime: ^6.4
- symfony/process: ^6.4
- symfony/string: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3.4
- webonyx/graphql-php: ^15.0
- wikimedia/less.php: ^5.0

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
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Libreria</td>
    <td>Libreria API di Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Libreria</td>
    <td>Common Runtime di AWS per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Libreria</td>
    <td>AWS SDK per PHP - Utilizzare Amazon Web Services nel progetto PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">open-telemetry/api</a>
    </td>
    <td>Libreria</td>
    <td>API per OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">telemetria aperta/contesto</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione contestuale per OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>Metapackage</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Libreria</td>
    <td>BaconQrCode è un generatore di codici QR per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione PHP 7.1 enum</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Modulo Magento</td>
    <td>Il backend Zend_Cache_Backend_File di magazzino ha prestazioni estremamente scadenti per la pulizia da parte dei tag, rendendolo inutilizzabile con l’aumento del numero di elementi memorizzati in cache. Questo back-end apporta molte modifiche che determinano un notevole miglioramento delle prestazioni, in particolare per la pulizia dei tag.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Libreria</td>
    <td>Un gestore di sessione basato su Redis con blocco ottimistico</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Libreria</td>
    <td>Un'implementazione PHP del Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>Libreria</td>
    <td>Una semplice libreria per codificare e decodificare i token web JSON (JWT) in PHP. Deve essere conforme alla specifica corrente.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Libreria</td>
    <td>Generare e convalidare i CAPTCHA utilizzando figure, immagini, ReCaptcha e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>Libreria</td>
    <td>Estensioni dell'API PHP Reflection, scansione del codice statico e generazione del codice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Libreria</td>
    <td>fornisce un'interfaccia utente basata su proprietà di oggetto nidificato per accedere ai dati di configurazione nel codice dell'applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Libreria</td>
    <td>Iniezione di dipendenza automatica per contenitori PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escape</a>
    </td>
    <td>Libreria</td>
    <td>Escape sicuro e protetto di HTML, attributi HTML, JavaScript, CSS e URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>Libreria</td>
    <td>Attivare e ascoltare gli eventi all'interno di un'applicazione PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Libreria</td>
    <td>fornisce funzionalità per creare e utilizzare feed RSS e Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">laminas/laminas-filter</a>
    </td>
    <td>Libreria</td>
    <td>Filtrare e normalizzare a livello di programmazione dati e file</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia semplice per l'esecuzione di richieste HTTP (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>Libreria</td>
    <td>Fornisci le traduzioni per la tua applicazione, e filtra e convalida i valori internazionalizzati</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Libreria</td>
    <td>fornisce metodi di convenienza per serializzare da PHP nativo a JSON e decodificare da JSON a PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>Libreria</td>
    <td>Strategie di caricamento automatico e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Libreria</td>
    <td>Sistema modulare per applicazioni laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>Libreria</td>
    <td>Livello MVC basato su eventi di Laminas, incluse applicazioni MVC, controller e plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione di un elenco di controllo di accesso (ACL) leggero e flessibile per la gestione dei privilegi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>Libreria</td>
    <td>Wrapper OOP per il servizio Web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Libreria</td>
    <td>Sistema di routing flessibile per applicazioni HTTP e console</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>Libreria</td>
    <td>Creazione di server RPC basati su riflessioni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>Libreria</td>
    <td>Contenitore Di Iniezione Di Dipendenza Basato Su Fabbrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia orientata agli oggetti per sessioni PHP e storage</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminati/sapone laminato</a>
    </td>
    <td>Libreria</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Libreria</td>
    <td>Estensioni SPL, utility di array, gestori di errori e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Libreria</td>
    <td>Creare i file FIGlet e le tabelle basate su testo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Libreria</td>
    <td>Interfacce per il componente Translator del laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Libreria</td>
    <td>Componente che facilita la manipolazione e la convalida degli URI (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Libreria</td>
    <td>Classi di convalida per un'ampia gamma di domini e possibilità di concatenare le convalide per creare criteri di convalida complessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Libreria</td>
    <td>Livello di vista flessibile che supporta e fornisce più livelli di vista, helper e altro ancora</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione semplice e rapida delle enumerazioni con PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Libreria</td>
    <td>Un parser PHP scritto in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>Libreria</td>
    <td>Libreria client per reCAPTCHA di Google per PHP 8.4 e versioni successive</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>Libreria</td>
    <td>PHP integrato nel minifier JavaScript</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Modulo Magento</td>
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
      <a href="https://github.com/paragonie/sodium_compat">paragonie/sodio_compat</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurificer</a>
    </td>
    <td>Libreria</td>
    <td>Filtro HTML conforme agli standard scritto in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>Libreria</td>
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
      <a href="https://github.com/braintree/braintree_php">albero del cervello/albero del cervello_php</a>
    </td>
    <td>Libreria</td>
    <td>Libreria client Braintree PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">brick/matematica</a>
    </td>
    <td>Libreria</td>
    <td>Libreria aritmetica di precisione arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>Libreria</td>
    <td>Una potente alternativa a var_export(), che può esportare chiusure e oggetti senza __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">cristiano-riesen/base32</a>
    </td>
    <td>Libreria</td>
    <td>Codificatore/decodificatore Base32 secondo RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>Libreria</td>
    <td>Credis è un’interfaccia leggera dell’archivio Redis di valori chiave che racchiude la libreria phpredis quando disponibile per prestazioni migliori.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">compositore/ca-bundle</a>
    </td>
    <td>Libreria</td>
    <td>Consente di trovare un percorso per il bundle CA di sistema e include un fallback al bundle CA di Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">compositore/class-map-generator</a>
    </td>
    <td>Libreria</td>
    <td>Utilità per scansionare il codice PHP e generare mappe di classe.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">compositore/compositore</a>
    </td>
    <td>Libreria</td>
    <td>Composer consente di dichiarare, gestire e installare le dipendenze dei progetti PHP. Ti garantisce di avere la giusta pila ovunque.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">compositore/minificatore metadati</a>
    </td>
    <td>Libreria</td>
    <td>Piccola libreria di utilità che gestisce la minimizzazione e l'espansione dei metadati.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">compositore/pcre</a>
    </td>
    <td>Libreria</td>
    <td>Libreria di wrapping PCRE che offre sostituzioni preg_* di tipo sicuro.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">compositore/semver</a>
    </td>
    <td>Libreria</td>
    <td>Libreria semver che offre utility, analisi e convalida dei vincoli di versione.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">licenze compositore/spdx</a>
    </td>
    <td>Libreria</td>
    <td>Elenco licenze SPDX e libreria di convalida.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">compositore/xdebug-handler</a>
    </td>
    <td>Libreria</td>
    <td>Riavvia un processo senza Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">dottrina/lexer</a>
    </td>
    <td>Libreria</td>
    <td>Libreria parser PHP Doctrine Lexer che può essere utilizzata nei parser discendenti ricorsivi top-down.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>Libreria</td>
    <td>Libreria per la convalida delle e-mail rispetto a diverse RFC</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">elastico/trasporto</a>
    </td>
    <td>Libreria</td>
    <td>Libreria PHP per trasporto HTTP per prodotti elastici</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Libreria</td>
    <td>Client PHP per Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Libreria</td>
    <td>Codice QR Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Libreria</td>
    <td>Forcella di guzzle/ruscelli (abbandonati) da utilizzare con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Libreria</td>
    <td>Forchetta di guzzle/RingPHP (abbandonato) da utilizzare con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Libreria</td>
    <td>Guzzle è una libreria client HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promise</a>
    </td>
    <td>Libreria</td>
    <td>Libreria Guzzle promesse</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione del messaggio PSR-7 che fornisce anche metodi di utilità comuni</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>Libreria</td>
    <td>Libreria per convalidare uno schema JSON.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">lega/flysystem</a>
    </td>
    <td>Libreria</td>
    <td>Estrazione archiviazione file per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">league/flysystem-aws-s3-v3</a>
    </td>
    <td>Libreria</td>
    <td>Scheda di file system AWS S3 per Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">lega/flysystem-locale</a>
    </td>
    <td>Libreria</td>
    <td>Adattatore di file system locale per Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-detection</a>
    </td>
    <td>Libreria</td>
    <td>Rilevamento del tipo MIME per Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monologo/monologo</a>
    </td>
    <td>Libreria</td>
    <td>Invia i registri a file, socket, caselle in entrata, database e vari servizi web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Libreria</td>
    <td>Specificare in modo dichiarativo come estrarre elementi da un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Libreria</td>
    <td>Implementazioni a tempo costante della codifica RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Libreria</td>
    <td>polyfill PHP 5.x per random_bytes() e random_int() da PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emoglificatore</a>
    </td>
    <td>Libreria</td>
    <td>Converte gli stili CSS in attributi di stile in linea nel codice HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>Trova e installa le implementazioni PSR-7, PSR-17, PSR-18 e HTTPlug</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Libreria</td>
    <td>HTTPlug, astrazione del client HTTP per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>Libreria</td>
    <td>Promessa utilizzata per le richieste HTTP asincrone</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Libreria</td>
    <td>Converti selettori CSS in query XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Libreria</td>
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Libreria</td>
    <td>Funzioni della funzione di accesso alle proprietà e del mutatore.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Libreria</td>
    <td>Poliriempimento PHP 5.x-8.x per estensione mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Libreria</td>
    <td>Libreria PHP Secure Communications: implementazioni Pure-PHP di RSA, AES, SSH2, SFTP, X.509 ecc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune per il caching delle librerie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune per la lettura dell'orologio.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune dei contenitori (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>Libreria</td>
    <td>Interfacce standard per la gestione degli eventi.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune per i client HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>Libreria</td>
    <td>PSR-17: interfacce comuni per i message factory HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune per i messaggi HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>Libreria</td>
    <td>Interfaccia comune per le librerie di registrazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>Libreria</td>
    <td>Un polyfill per getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">ramsey/collection</a>
    </td>
    <td>Libreria</td>
    <td>Libreria PHP per la rappresentazione e la manipolazione delle raccolte.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>Libreria</td>
    <td>Libreria PHP per la generazione e l’utilizzo di identificatori universalmente univoci (UUID).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">react/promise</a>
    </td>
    <td>Libreria</td>
    <td>Implementazione leggera di CommonJS Promises/A per PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Libreria</td>
    <td>Parser per file CSS scritti in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Libreria</td>
    <td>Linter JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Libreria</td>
    <td>PHAR formato file utilità, per quando PHP phars si up</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>Libreria</td>
    <td>Semplice gestore di segnali unix che genera un errore silenzioso quando i segnali non sono supportati per un facile sviluppo su più piattaforme</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Libreria</td>
    <td>Key Wrap AES per PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Libreria</td>
    <td>Libreria PHP per la generazione di password monouso secondo l'RFC 4226 (HOTP Algorithm) e l'RFC 6238 (TOTP Algorithm) e compatibile con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Libreria</td>
    <td>Un framework PHP per la gestione dell'infrastruttura a chiave pubblica. Comprende certificati a chiave pubblica X.509, certificati di attributi, richieste di certificazione e convalida del percorso di certificazione.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Libreria</td>
    <td>Consente di trovare, caricare, combinare, riempire automaticamente e convalidare i valori di configurazione di qualsiasi tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symfony/console</a>
    </td>
    <td>Libreria</td>
    <td>Semplifica la creazione di interfacce per riga di comando belle e testabili</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>Libreria</td>
    <td>Converte i selettori CSS in espressioni XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/dependency-injection</a>
    </td>
    <td>Libreria</td>
    <td>Consente di standardizzare e centralizzare il modo in cui gli oggetti vengono costruiti nell'applicazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">symfony/deprecation-CONTRACTS</a>
    </td>
    <td>Libreria</td>
    <td>Funzione e convenzione generiche per attivare gli avvisi di deprecazione</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce strumenti per gestire gli errori e facilitare il debug del codice PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce strumenti che consentono ai componenti dell'applicazione di comunicare tra loro inviando eventi e ascoltandoli</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-CONTRACTS</a>
    </td>
    <td>Libreria</td>
    <td>Astrazioni generiche correlate all’evento dispatching</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce utilità di base per il file system</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Libreria</td>
    <td>Trova file e directory tramite un'interfaccia intuitiva</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce potenti metodi per recuperare le risorse HTTP in modo sincrono o asincrono</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-CONTRACTS</a>
    </td>
    <td>Libreria</td>
    <td>Astrazioni generiche correlate ai client HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Libreria</td>
    <td>Definisce un livello orientato agli oggetti per la specifica HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce un processo strutturato per convertire una richiesta in una risposta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Libreria</td>
    <td>Consente di accedere ai dati di localizzazione della libreria ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Libreria</td>
    <td>Aiuta a inviare e-mail</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Libreria</td>
    <td>Consente la manipolazione dei messaggi MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill per funzioni di tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill per le funzioni grapheme_* di intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill per le funzioni intl idn_to_ascii e idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill per la classe Normalizer di intl e funzioni correlate</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill per l’estensione Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 7.3+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.0+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.1+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.2+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Libreria</td>
    <td>Symfony polyfill supporta alcune funzioni PHP 8.3+ per ridurre le versioni PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Libreria</td>
    <td>Esegue comandi nei sottoprocessi</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">symfony/service-CONTRACTS</a>
    </td>
    <td>Libreria</td>
    <td>Astrazioni generiche relative ai servizi di scrittura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce un’API orientata agli oggetti per stringhe e tratta byte, punti di codice UTF-8 e cluster di grafemi in modo unificato</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Libreria</td>
    <td>Fornisce meccanismi per passare attraverso qualsiasi variabile PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>Libreria</td>
    <td>Consente l'esportazione di qualsiasi struttura di dati PHP serializzabile nel codice PHP normale</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Libreria</td>
    <td>Carica ed esegue il dump dei file YAML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Symfony-bundle</td>
    <td>Libreria di firma di oggetti e crittografia JSON per PHP e Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>Libreria</td>
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
    <td>Modulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Modulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Modulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Modulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Modulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-reward
    </td>
    <td>Modulo Magento2</td>
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
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>Libreria</td>
    <td>Codificatore CBOR per PHP</td>
  </tr>
  </tbody>
</table>

### Proprietario

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
    <td>Modulo Magento2</td>
    <td>Effettua il forking dal modulo Magento Braintree 2.2.0 di Gene Commerce per PayPal.</td>
  </tr>
  </tbody>
</table>

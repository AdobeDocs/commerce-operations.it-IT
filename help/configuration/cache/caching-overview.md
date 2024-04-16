---
title: Configurare la memorizzazione in cache
description: Scopri come memorizzare in cache e come configurare i meccanismi di cache per l’applicazione Adobe Commerce.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Configurare la memorizzazione in cache

[!DNL Commerce] consente di configurare alternative al caching predefinito del file system. La presente guida illustra alcune di queste alternative:

- Configura i seguenti meccanismi di cache in [!DNL Commerce] configurazione:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - File system (predefinito): non è necessaria alcuna configurazione per utilizzare il caching del file system predefinito.

- Configurare [Vernice](config-varnish.md) senza modificare il [!DNL Commerce] configurazione.

## Terminologia di caching

[!DNL Commerce] utilizza la seguente terminologia di caching:

- **Frontend**: simile a un&#39;interfaccia o a un gateway per l&#39;archiviazione nella cache, implementato da [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipi di cache**- Può essere uno dei tipi forniti con [!DNL Commerce] o puoi [crea il tuo](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Back-end**- Specifica i dettagli su [archiviazione cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementato da [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Back-end a due livelli**- Memorizza i record della cache in due backend: uno più veloce e uno più lento.

  >[!INFO]
  >
  >La configurazione della cache back-end a due livelli va oltre l’ambito di questa guida.

## Opzioni di configurazione

- Modifica del fornito `default` cache front-end:

  Puoi modificare solo il `<magento_root>/app/etc/di.xml` file, la configurazione dell’iniezione di dipendenza globale dell’applicazione Commerce.

- Configurazione di una cache personalizzata front-end:

  Puoi modificare solo il `<magento_root>/app/etc/env.php` perché esegue l&#39;override della configurazione equivalente in `di.xml` file.

>[!TIP]
>
>La vernice non richiede modifiche al [!DNL Commerce] configurazione. Consulta [Configurare e utilizzare vernice](config-varnish.md).

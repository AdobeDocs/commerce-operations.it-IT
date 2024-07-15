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

[!DNL Commerce] consente di configurare alternative al caching del file system predefinito. La presente guida illustra alcune di queste alternative:

- Configurare i seguenti meccanismi di cache nella configurazione [!DNL Commerce]:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - File system (predefinito): non è necessaria alcuna configurazione per utilizzare il caching del file system predefinito.

- Configura [Vernice](config-varnish.md) senza modificare la configurazione di [!DNL Commerce].

## Terminologia di caching

[!DNL Commerce] utilizza la seguente terminologia di caching:

- **Frontend**—Simile a un&#39;interfaccia o a un gateway per l&#39;archiviazione della cache, implementato da [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipi di cache** - Può essere uno dei tipi forniti con [!DNL Commerce] oppure puoi [crearne uno tuo](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend**—Specifica i dettagli sull&#39;[archiviazione cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementata da [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Back-end a due livelli** - Memorizza i record della cache in due backend: uno più veloce e uno più lento.

  >[!INFO]
  >
  >La configurazione della cache back-end a due livelli va oltre l’ambito di questa guida.

## Opzioni di configurazione

- Modifica del front-end della cache `default` fornito:

  Si modifica solo il file `<magento_root>/app/etc/di.xml`, la configurazione dell&#39;iniezione di dipendenza globale dell&#39;applicazione Commerce.

- Configurazione di una cache personalizzata front-end:

  Si modifica solo il file `<magento_root>/app/etc/env.php` perché sostituisce la configurazione equivalente nel file `di.xml`.

>[!TIP]
>
>Varnish non richiede modifiche alla configurazione [!DNL Commerce]. Consulta [Configurare e utilizzare Vernice](config-varnish.md).

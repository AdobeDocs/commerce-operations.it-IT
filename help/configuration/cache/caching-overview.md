---
title: Configurare la memorizzazione in cache
description: Scopri la memorizzazione in cache e come configurare i meccanismi di cache per l’applicazione Adobe Commerce e Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Configurare la memorizzazione in cache

[!DNL Commerce] consente di configurare alternative al caching predefinito del file system. Questa guida illustra alcune di queste alternative; vale a dire:

- Imposta i seguenti meccanismi di cache nel [!DNL Commerce] configurazione:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - File system (predefinito): Non è necessaria alcuna configurazione per utilizzare il caching predefinito del file system.

- Imposta la [Vernice](config-varnish.md) senza modificare [!DNL Commerce] configurazione.

## Terminologia di memorizzazione nella cache

[!DNL Commerce] utilizza la seguente terminologia di memorizzazione in cache:

- **Fronte**- Simile a un&#39;interfaccia o a un gateway per lo storage cache, implementato da [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Tipi di cache**—Può essere uno dei tipi forniti con [!DNL Commerce] oppure [creare un proprio](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Backend**- Specifica i dettagli [archiviazione cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implementato da [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Backend a due livelli**- Memorizza i record della cache in due backend: uno più veloce e uno più lento.

   >[!INFO]
   >
   >La configurazione della cache back-end a due livelli va oltre l’ambito di questa guida.

## Opzioni di configurazione

- Modifica dei dati forniti `default` frontend cache

   Modifichi solo il `<magento_root>/app/etc/di.xml` file, la configurazione dell’iniezione di dipendenza globale dell’applicazione Commerce.

- Configurazione del proprio frontend di cache personalizzato:

   Modifichi solo il `<magento_root>/app/etc/env.php` perché sostituisce la configurazione equivalente nel `di.xml` file.

>[!TIP]
>
>La vernice non richiede modifiche al [!DNL Commerce] configurazione. Vedi [Configurare e utilizzare Varnish](config-varnish.md).

---
title: Opzioni di back-end cache e riferimento archiviazione
description: Scopri le opzioni di back-end della cache in Adobe Commerce, tra cui file system, Redis, Valkey e archiviazione del database. Scopri le opzioni basate su Zend (RemoteSynchronizedCache) e Symfony Cache.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# Opzioni di back-end della cache e riferimento archiviazione

>[!NOTE]
>
>Questa pagina documenta la configurazione di `app/etc/env.php` locale.
>
>Per i progetti [!DNL Adobe Commerce on Cloud], il pacchetto `ece-tools` genera la configurazione `app/etc/env.php` risultante durante la distribuzione in base alla configurazione della variabile di distribuzione in `.magento.env.yaml`. Non si modifica il file `env.php`.  Consulta [Best practice per la configurazione di Valkey e Redis Service](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) e [distribuire le variabili](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy).

L’applicazione Commerce utilizza una cache di basso livello front-end e back-end per fornire accesso allo storage della cache. Commerce supporta diversi back-end e strategie di caching, ciascuno adatto a casi d’uso diversi. Questa pagina descrive i backend disponibili e le loro differenze.

>[!NOTE]
>
>[Varnish](config-varnish-install.md) gestisce il caching a pagina intera a livello HTTP per le distribuzioni locali. Il [Fastly Service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) lo gestisce per le distribuzioni Cloud. Nessuna delle due soluzioni utilizza il back-end della cache di basso livello.

## Opzioni cache back-end

Nella tabella seguente sono riepilogate le cache back-end disponibili:

| Back-end | Descrizione | Guida alla configurazione |
| ------- | ----------- | ------------------- |
| File system | Impostazione predefinita. Memorizza i dati della cache nei file in `var/cache/`. Nessuna configurazione richiesta. | N/D |
| Redis | Archivio dati in memoria per il caching ad alte prestazioni. | [Usa Redis per la cache predefinita](redis-pg-cache.md) |
| Valkey | Alternativa open-source compatibile con Redis. | [Usa Valkey per la cache predefinita](valkey-pg-cache.md) |
| Database | Motore di cache personalizzato supportato da un database | [Creare motori di cache personalizzati](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} (documentazione di Adobe Developer) |

>[!IMPORTANT]
>
>La cache Redis non è supportata per Adobe Commerce 2.4.9 o versioni di patch successive a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 e 2.4.8-p4. Se stai eseguendo l’aggiornamento a una di queste versioni, configura Valkey e aggiorna la configurazione della cache per utilizzarla. Per [!DNL Adobe Commerce on-premises], vedere [configurare Valkey](config-valkey.md).

## Cache back-end e implementazioni L2 {#implementation-approaches}

Commerce supporta il backend diretto della cache e il caching L2. Un back-end diretto seleziona l’archiviazione della cache. Il caching L2 aggiunge un livello di cache locale davanti allo storage remoto.

### Back-end della cache diretta

Nella tabella seguente vengono riepilogati i valori di configurazione del back-end della cache per `<Commerce-install-dir>/app/etc/env.php`. Non abilita il caching L2.

| Versione Commerce | Back-end | Valore di configurazione |
| ---------------- | ------- | -------------------- |
| 2.4.8 e versioni precedenti, se supportato | file | Impostazione predefinita. Nessuna configurazione richiesta |
| 2.4.8 e versioni precedenti, se supportato | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 e versioni precedenti, se supportato | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 e versioni successive, oltre ai backport supportati | file | `file` |
| 2.4.9 e versioni successive, oltre ai backport supportati | Valkey | `valkey` |

Per informazioni esatte sul supporto a livello di patch, vedere [Requisiti di sistema](../../installation/system-requirements.md).

>[!TAB Cache basata su Zend (versione 2.4.8 e precedenti)]

#### Esempi di back-end

Per le distribuzioni locali, negli esempi seguenti vengono configurati i back-end della cache diretta in `<Commerce-install-dir>/app/etc/env.php`. Non abilitano il caching L2. Non utilizzare questi esempi per le distribuzioni [!DNL Adobe Commerce on Cloud], che utilizzano il pacchetto `ece-tools` per generare la configurazione `app/etc/env.php` risultante durante la distribuzione.

>[!BEGINTABS]

>[!TAB Redis]

Utilizza il nome completo della classe Redis solo nelle versioni in cui è supportato Redis:

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Chiave Valvola]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## Memorizzazione nella cache L2

Il caching L2 (a due livelli) aggiunge un livello di cache locale su ciascun nodo web davanti allo storage della cache remota condivisa, riducendo il traffico di rete tra Commerce e la cache remota. Per le opzioni di implementazione, il supporto delle versioni e i passaggi di configurazione, vedere [Configurazione cache L2](level-two-cache.md).

Per i progetti Cloud, configura il caching L2 tramite le variabili di distribuzione descritte in [Distribuisci variabili](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}.

- [Usa Redis per la cache predefinita](redis-pg-cache.md)
- [Usa Valkey per la cache predefinita](valkey-pg-cache.md)
- [Configurazione cache L2](level-two-cache.md)

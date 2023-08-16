---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# Impostazioni di configurazione MariaDB

La reindicizzazione su MariaDB 10.4 e 10.6 richiede più tempo rispetto alle versioni precedenti di MariaDB o MySQL. Per accelerare la reindicizzazione, si consiglia di impostare i seguenti parametri di configurazione MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Se si verifica un peggioramento delle prestazioni non correlato all&#39;indicizzazione dopo l&#39;aggiornamento a MariaDB 10.6, è consigliabile attivare [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) impostazione. Ad esempio, `--query-cache-type=ON`.

Oltre a questi consigli, è necessario consultare l&#39;amministratore del database per configurare i seguenti parametri:

>[!NOTE]
>
>Queste impostazioni sono disponibili solo per le distribuzioni locali. I clienti di Adobe Commerce su infrastruttura cloud non hanno accesso a queste impostazioni.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)

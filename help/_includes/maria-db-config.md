---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# Impostazioni di configurazione MariaDB

La reindicizzazione su MariaDB 10.4 e 10.6 richiede più tempo rispetto alle versioni precedenti di MariaDB o MySQL. Per accelerare la reindicizzazione, si consiglia di impostare i seguenti parametri di configurazione MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

Se si verifica un peggioramento delle prestazioni non correlato all&#39;indicizzazione dopo l&#39;aggiornamento a MariaDB 10.6, provare ad abilitare l&#39;impostazione [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type). Ad esempio, `--query-cache-type=ON`.

Prima di aggiornare Adobe Commerce ai progetti di infrastruttura cloud, potrebbe essere necessario aggiornare anche MariaDB ([consulta le best practice per l&#39;aggiornamento di MariaDB](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Ad esempio:

* Adobe Commerce 2.4.6 con MariaDB versione 10.5.1 o successiva
* Adobe Commerce 2.3.5 con MariaDB versione 10.3 o precedente

Oltre a questi consigli, è necessario consultare l&#39;amministratore del database per configurare i seguenti parametri:

>[!NOTE]
>
>Queste impostazioni sono disponibili solo per le distribuzioni locali. I clienti di Adobe Commerce su infrastruttura cloud non hanno accesso a queste impostazioni.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)

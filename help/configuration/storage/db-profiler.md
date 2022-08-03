---
title: Configurare il profiler del database
description: Vedi un esempio di come configurare l'output per il profiler del database.
contributor_name: Atish Goswami
contributor_link: http://atishgoswami.com
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Configurare il profiler del database

Il profiler del database Commerce visualizza tutte le query implementate su una pagina, compreso il tempo per ogni query e i parametri applicati.

## Passaggio 1: Modificare la configurazione della distribuzione

Modifica `<magento_root>/app/etc/env.php` per aggiungere il seguente riferimento al [classe del profiler del database](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Di seguito è riportato un esempio:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Passaggio 2: Configurare l’output

Configura l’output nel file di avvio dell’applicazione Commerce; potrebbe essere `<magento_root>/pub/index.php` o potrebbe trovarsi in una configurazione host virtuale di un server web.

L’esempio seguente visualizza i risultati in una tabella a tre colonne:

- Tempo totale (visualizza la quantità totale di tempo necessario per eseguire tutte le query sulla pagina)
- SQL (visualizza tutte le query SQL; l’intestazione della riga visualizza il numero di query)
- Parametri query (visualizza i parametri per ogni query SQL)

Per configurare l’output, aggiungi quanto segue dopo la `$bootstrap->run($app);` nel file bootstrap:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Passaggio 3: Visualizza i risultati

Vai a qualsiasi pagina nella tua vetrina o Amministratore per visualizzare i risultati. Segue un esempio:

![Risultati del profiler del database di esempio](../../assets/configuration/db-profiler-results.png)

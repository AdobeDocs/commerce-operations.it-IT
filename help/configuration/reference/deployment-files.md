---
title: File di configurazione per la distribuzione
description: Scopri come funzionano i file di configurazione per l’installazione dell’applicazione Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# File di configurazione per la distribuzione

Adobe Commerce fornisce file di configurazione che consentono di personalizzare facilmente un componente e creare tipi di configurazione per estendere le funzionalità predefinite. Il processo di configurazione della distribuzione consiste nella configurazione condivisa e specifica del sistema per l&#39;installazione. La configurazione di distribuzione di Commerce è suddivisa tra [`app/etc/config.php`](../reference/config-reference-configphp.md) e [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` è _condiviso_ file di configurazione.
Questo file contiene l&#39;elenco dei moduli installati, dei temi e dei pacchetti linguistici; e le impostazioni di configurazione condivise.

   Archivia questo file nel controllo del codice sorgente e utilizzalo nei sistemi di sviluppo, staging e produzione.

   A partire dalla versione 2.2, il `app/etc/config.php` il file non è più una voce nel `.gitignore` file.
Ciò è stato fatto per facilitare [distribuzione della pipeline](../deployment/technical-details.md).

- `app/etc/env.php` contiene impostazioni specifiche dell&#39;ambiente di installazione.

Insieme, `config.php` e `env.php` sono denominati Commercio _configurazione della distribuzione_ perché i file vengono creati durante l&#39;installazione e sono necessari per avviare l&#39;applicazione Commerce.

>[!INFO]
>
>La [!DNL Commerce 2] la configurazione della distribuzione sostituisce `local.xml` in [!DNL Magento 1.x].

A differenza di altri [file di configurazione del modulo](../reference/module-files.md), la configurazione della distribuzione Commerce viene caricata in memoria durante l’inizializzazione, non viene unita ad altri file e non può essere estesa. (`config.php` e `env.php` sono tuttavia fusi tra loro).

## Dettagli sulla configurazione della distribuzione

`config.php` e `env.php` sono file PHP che restituiscono un [array associativo multidimensionale](https://www.w3schools.com:443/php/php_arrays.asp), che è fondamentalmente una disposizione gerarchica di parametri e valori di configurazione.

Al livello superiore di questo array sono _segmenti di configurazione_. Un segmento ha contenuto arbitrario (un valore scalare o una matrice nidificata) distinto da una chiave arbitraria, in cui sia la coppia chiave che la coppia valore sono definite dal framework Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) fornisce semplicemente l’accesso a queste sezioni ma non consente di estenderle.

A livello gerarchico successivo, gli elementi di ciascun segmento vengono ordinati in base alla definizione della sequenza del modulo, ottenuta unendo tutti i file di configurazione dei moduli, ad eccezione dei moduli disabilitati.

Nelle sezioni seguenti vengono descritti la struttura e il contenuto della configurazione di distribuzione:

- Gestire i moduli installati
- Configurazione specifica del sistema

## Gestire i moduli installati

La `config.php` il file contiene un elenco dei moduli installati. Adobe Commerce fornisce utility sia basate su riga di comando che su Web per gestire i moduli (installazione, disinstallazione, abilitazione, disattivazione o aggiornamento).

Esempi:

- Disinstallare i componenti: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Controlla lo stato dei componenti: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Attivare o disattivare i componenti: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

Il valore `1` o `0` indica se un modulo è abilitato o disabilitato.

I moduli disattivati non sono riconosciuti dall’applicazione Commerce; in altre parole, non partecipano all’unione della configurazione, all’iniezione di dipendenza, agli eventi, ai plug-in e così via. I moduli disattivati non modificano la vetrina o l&#39;amministratore e non influiscono sul routing.

L&#39;unica differenza pratica di un modulo disabilitato e di un modulo assente nella base di codice è che un modulo disabilitato viene trovato dall&#39;autoloader, e le sue classi e costanti sono disponibili per il riutilizzo in un altro codice.

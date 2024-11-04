---
title: File di configurazione per la distribuzione
description: Comprendere il funzionamento dei file di configurazione per l'installazione dell'applicazione Commerce.
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# File di configurazione per la distribuzione

Adobe Commerce fornisce file di configurazione che consentono di personalizzare facilmente un componente e creare tipi di configurazione per estendere le funzionalità predefinite. Il processo di configurazione della distribuzione consiste nella configurazione condivisa e specifica del sistema per l’installazione. La configurazione della distribuzione di Commerce è suddivisa tra [`app/etc/config.php`](../reference/config-reference-configphp.md) e [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` è il file di configurazione _shared_.
Questo file contiene l&#39;elenco dei moduli, dei temi e dei pacchetti di lingue installati, nonché le impostazioni di configurazione condivise.

  Archivia il file nel controllo del codice sorgente e utilizzalo nei sistemi di sviluppo, staging e produzione.

- `app/etc/env.php` contiene impostazioni specifiche dell&#39;ambiente di installazione.

Insieme, `config.php` e `env.php` sono denominati _configurazione di distribuzione_ di Commerce perché i file vengono creati durante l&#39;installazione e sono necessari per avviare l&#39;applicazione Commerce.

>[!INFO]
>
>La configurazione della distribuzione [!DNL Commerce 2] sostituisce `local.xml` in [!DNL Magento 1.x].

A differenza di altri [file di configurazione del modulo](../reference/module-files.md), la configurazione della distribuzione Commerce viene caricata in memoria quando durante l&#39;inizializzazione, non viene unita ad altri file e non può essere estesa. (`config.php` e `env.php` sono tuttavia uniti tra loro.)

## Dettagli sulla configurazione della distribuzione

`config.php` e `env.php` sono file PHP che restituiscono un [array associativo multidimensionale](https://www.w3schools.com:443/php/php_arrays.asp), fondamentalmente una disposizione gerarchica di parametri e valori di configurazione.

Al livello superiore dell&#39;array sono presenti _segmenti di configurazione_. Un segmento ha contenuto arbitrario (un valore scalare o un array nidificato) distinto da una chiave arbitraria, in cui sia la coppia chiave-valore sono definite dal framework Commerce.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) fornisce semplicemente l&#39;accesso a queste sezioni, ma non consente di estenderle.

Al livello gerarchico successivo, gli elementi in ciascun segmento vengono ordinati in base alla definizione della sequenza di moduli, che si ottiene unendo tutti i file di configurazione dei moduli, ad eccezione dei moduli disabilitati.

Nelle sezioni seguenti vengono descritti la struttura e il contenuto della configurazione di distribuzione:

- Gestire i moduli installati
- Configurazione specifica del sistema

## Gestire i moduli installati

Il file `config.php` contiene un elenco dei moduli installati. Adobe Commerce fornisce utility basate su riga di comando e web per gestire i moduli (installazione, disinstallazione, abilitazione, disabilitazione o aggiornamento).

Esempi:

- Disinstalla componenti: [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- Verifica stato dei componenti: [`bin/magento module:status`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- Abilitare o disabilitare i componenti: [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

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

I moduli disattivati non vengono riconosciuti dall&#39;applicazione Commerce; in altre parole, non partecipano alla configurazione di unione, all&#39;inserimento di dipendenze, agli eventi, ai plug-in e così via. I moduli disattivati non modificano la vetrina o l’amministratore e non influiscono sul routing.

L&#39;unica differenza pratica tra un modulo disabilitato e un modulo assente nella base di codice è che un modulo disabilitato viene trovato dall&#39;autoloader e le relative classi e costanti sono disponibili per il riutilizzo in altro codice.

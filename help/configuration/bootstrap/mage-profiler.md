---
title: Abilita profilazione
description: Scopri di più sull’abilitazione del profiler di MAGE da utilizzare con i tuoi strumenti analitici.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Abilita profilazione

Con il profiling Commerce, puoi:

- Abilita un profiler integrato.

   Puoi utilizzare un profiler integrato con Commerce per eseguire attività quali l’analisi delle prestazioni. La natura del profiling dipende dagli strumenti analitici utilizzati. Supportiamo più formati, incluso HTML. Quando abiliti il profiler, un `var/profiler.flag` viene generato un file che indica che il profiler è abilitato e le configurazioni. Se disabilitata, il file viene eliminato.

- Visualizzare i grafici delle dipendenze in una pagina Commerce.

   A _grafico a dipendenza_ è un elenco delle dipendenze degli oggetti e di tutte le loro dipendenze, nonché di tutte le dipendenze per tali dipendenze e così via.

   Dovrebbe essere particolarmente interessato all&#39;elenco di _dipendenze inutilizzate_, che sono oggetti creati perché sono stati richiesti in alcuni costruttori, ma non sono mai stati utilizzati (ovvero, nessuno dei loro metodi è stato chiamato). Di conseguenza, il tempo e la memoria del processore utilizzati per creare queste dipendenze vengono sprecati.

Commerce fornisce la funzionalità di base in [`Magento\Framework\Profiler`][profiler].

Puoi abilitare e configurare il profiler utilizzando una variabile MAGE_PROFILER o la riga di comando.

## Imposta MAGE_PROFILER

Puoi impostare il valore di `MAGE_PROFILER` in uno dei modi discussi in [Imposta il valore dei parametri di bootstrap](../bootstrap/set-parameters.md).

`MAGE_PROFILER` supporta i seguenti valori:

- `1` per abilitare l&#39;output di un profiler specifico.

   Per abilitare un profiler specifico, puoi utilizzare uno dei seguenti valori:

   - `csvfile` che utilizza [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Qualsiasi altro valore (tranne `2`), incluso un valore vuoto, che utilizza [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` per abilitare i grafici delle dipendenze.

   I grafici di dipendenza vengono generalmente visualizzati nella parte inferiore di una pagina. La figura seguente mostra una parte dell&#39;output:

   ![Grafici di dipendenza](../../assets/configuration/depend-graphs.png)

## Comandi CLI

Puoi abilitare o disabilitare il profiler utilizzando i comandi CLI:

- `dev:profiler:enable <type>` abilita il profiler con `type` di `html` (predefinito) o `csvfile`. Quando abilitato, un file flagfile `var/profiler.flag` viene creato.
- `dev:profiler:disable` disabilita il profiler. Se disabilitata, il file flagfile `var/profiler.flag` viene rimosso.

Per abilitare i grafici delle dipendenze, utilizzare l’opzione variabile .

**Per attivare o disattivare il profiler**:

1. Accedi al tuo server Commerce.
1. Passa alla directory di installazione Commerce.
1. In qualità di proprietario del file system, abilita il profiler:

   Per abilitare il profiler utilizzando il tipo `html` e crea un file flagfile:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Per abilitare il profiler utilizzando il tipo `csvfile` e crea un file flagfile:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   L&#39;output viene salvato in `<project-root>/var/log/profiler.csv`. La `profiler.csv` viene ignorato in ogni aggiornamento della pagina.

   Per disabilitare il profiler e rimuovere il flagfile:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php

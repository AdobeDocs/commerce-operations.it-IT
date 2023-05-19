---
title: Abilita profilatura
description: Scopri come abilitare MAGE Profiler per l’utilizzo con i tuoi strumenti di analisi.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Abilita profilatura

Con la profilazione Commerce, puoi:

- Abilita un profiler incorporato.

   Puoi utilizzare un profiler integrato con Commerce per eseguire attività quali l’analisi delle prestazioni. La natura del profiling dipende dagli strumenti analitici utilizzati. Supportiamo più formati, tra cui HTML. Quando si abilita il profiler, viene `var/profiler.flag` viene generato un file che indica che il profiler è abilitato e le configurazioni. Se disabilitato, il file viene eliminato.

- Visualizzare grafici delle dipendenze in una pagina Commerce.

   A _grafico delle dipendenze_ è un elenco di dipendenze oggetto e di tutte le relative dipendenze, nonché di tutte le dipendenze per tali dipendenze e così via.

   Dovresti essere particolarmente interessato all’elenco di _dipendenze non utilizzate_: oggetti creati perché richiesti in alcuni costruttori, ma mai utilizzati (ovvero, nessuno dei relativi metodi è stato chiamato). Di conseguenza, il tempo del processore e la memoria impiegata per creare queste dipendenze vengono sprecati.

Commerce fornisce la funzionalità di base in [`Magento\Framework\Profiler`][profiler].

È possibile abilitare e configurare il profiler utilizzando una variabile MAGE_PROFILER o la riga di comando.

## Imposta MAGE_PROFILER

Puoi impostare il valore di `MAGE_PROFILER` in uno dei modi descritti in [Imposta il valore dei parametri di bootstrap](../bootstrap/set-parameters.md).

`MAGE_PROFILER` supporta i seguenti valori:

- `1` per abilitare l&#39;output di un profiler specifico.

   Per abilitare un profiler specifico, puoi utilizzare uno dei seguenti valori:

   - `csvfile` che utilizza [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Qualsiasi altro valore (eccetto `2`), incluso un valore vuoto, che utilizza [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` per abilitare i grafici delle dipendenze.

   I grafici delle dipendenze vengono in genere visualizzati nella parte inferiore di una pagina. Nella figura seguente viene illustrata una parte dell&#39;output:

   ![Grafici delle dipendenze](../../assets/configuration/depend-graphs.png)

## Comandi CLI

È possibile abilitare o disabilitare il profiler utilizzando i comandi CLI:

- `dev:profiler:enable <type>` abilita il profiler con `type` di `html` (impostazione predefinita) oppure `csvfile`. Quando è attivata, un file di flag `var/profiler.flag` viene creato.
- `dev:profiler:disable` disabilita il profiler. Se disattivato, il file di flag `var/profiler.flag` è stato rimosso.

Per abilitare i grafici delle dipendenze, utilizza l’opzione della variabile.

**Per attivare o disattivare il profiler**:

1. Accedi al server Commerce.
1. Passa alla directory di installazione di Commerce.
1. In qualità di proprietario del file system, abilita il profiler:

   Per abilitare il profiler utilizzando il tipo `html` e creare un file di flag:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Per abilitare il profiler utilizzando il tipo `csvfile` e creare un file di flag:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   L&#39;output viene salvato in `<project-root>/var/log/profiler.csv`. Il `profiler.csv` viene sovrascritto a ogni aggiornamento di pagina.

   Per disattivare il profiler e rimuovere il file di flag:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php

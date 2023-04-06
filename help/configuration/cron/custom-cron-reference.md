---
title: Riferimento personalizzato per cron job e cron group
description: Scopri come personalizzare gli cronisti utilizzando i gruppi cron.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Personalizzazione del riferimento cronologico

Questo argomento consente di impostare le schede cronologiche e facoltativamente i gruppi cron per i moduli personalizzati. Se il modulo personalizzato deve pianificare periodicamente le attività, è necessario impostare una scheda cronologica per tale modulo. A _crontab_ è una configurazione cron job.

Facoltativamente, puoi impostare un gruppo personalizzato, che tra le altre cose ti consente di eseguire i lavori cron definiti in quel gruppo indipendentemente da altri lavori cron.

Per un&#39;esercitazione dettagliata, vedi [Configurare i lavori cron personalizzati e i gruppi cron (esercitazione)](custom-cron-tutorial.md).

Per una panoramica dei lavori cron, vedi [Configurare i lavori cron](../cli/configure-cron-jobs.md).

## Configurare i gruppi cron

Questa sezione illustra come creare facoltativamente un gruppo cron per un modulo personalizzato. Se non devi eseguire questa operazione, continua con la sezione successiva.

A _gruppo cron_ è un gruppo logico che consente di eseguire facilmente cron per più di un processo alla volta. La maggior parte dei moduli Commerce utilizza `default` gruppo di cron; alcuni moduli utilizzano `index` gruppo.

Se si implementa cron per un modulo personalizzato, è possibile scegliere di utilizzare il `default` gruppo o gruppo diverso.

**Per configurare un gruppo cron per il modulo**:

Crea un `crontab.xml` nella directory del modulo:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Per un gruppo, il file deve avere i seguenti contenuti:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Dove:

| Valore | Descrizione |
|---|---|
| `group_name` | Nome del gruppo cron. Il nome del gruppo non deve essere univoco. È possibile eseguire cron per un gruppo alla volta. |
| `job_name` | ID univoco per questo lavoro cron. |
| `classpath` | Classe di cui creare un&#39;istanza (classpath). |
| `method` | Metodo in `classpath` a chiamare. |
| `time` | Pianificazione in formato cron. Ometti questo parametro se la pianificazione è definita nel database Commerce o in un altro archivio. |

Il risultato `crontab.xml` con due gruppi potrebbe essere simile al seguente:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Ad esempio, vedi [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Specifica delle opzioni del gruppo Cron

È possibile dichiarare un nuovo gruppo e specificarne le opzioni di configurazione (tutte eseguite nell&#39;ambito della vista Store) tramite `cron_groups.xml` file, situato in:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Di seguito è riportato un esempio di `cron_groups.xml` file:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Dove:

| Opzione | Descrizione |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Frequenza (in minuti) in cui le pianificazioni vengono scritte nel `cron_schedule` tabella. |
| `schedule_ahead_for` | Tempo (in minuti) in anticipo che i programmi sono scritti `cron_schedule` tabella. |
| `schedule_lifetime` | Intervallo di tempo (in minuti) in cui deve essere avviato un processo cron o il processo cron viene considerato mancato (&quot;troppo tardi&quot; per essere eseguito). |
| `history_cleanup_every` | Tempo (in minuti) in cui la cronologia dei cron viene conservata nel database. |
| `history_success_lifetime` | Tempo (in minuti) in cui il record dei processi cron completati correttamente viene conservato nel database. |
| `history_failure_lifetime` | Tempo (in minuti) in cui il record dei lavori di cron non riusciti viene conservato nel database. |
| `use_separate_process` | Esegui i lavori di questo gruppo cron in un processo php separato |

## Disattiva un lavoro cron

I lavori Cron non hanno un `disable` funzionalità come quella [osservatori](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Tuttavia, un lavoro cron può essere disabilitato utilizzando la seguente tecnica: `schedule` un&#39;ora che contiene una data che non si verificherà mai.

Ad esempio, disattiva il `visitor_clean` cron job definito in `Magento_Customer` modulo:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Per disabilitare la funzione `visitor_clean` cron job, crea un modulo personalizzato e riscrive il `visitor_clean` cron `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Ora, la `visitor_clean` il lavoro cron è stato impostato per essere eseguito alle 00:00 del 30 febbraio - alla data che non si verificherà mai.

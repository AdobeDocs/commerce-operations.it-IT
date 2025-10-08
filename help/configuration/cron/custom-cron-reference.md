---
title: Riferimento a processo cron personalizzato e gruppo cron
description: Scopri come personalizzare gli utenti con Gruppi cron e schede cronologiche in Adobe Commerce. Scopri la configurazione del modulo personalizzato e l’attività pianificata.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Personalizzazione del riferimento crons

Questo argomento consente di impostare le schede cronologiche e facoltativamente i gruppi cron per i moduli personalizzati. Se il modulo personalizzato deve pianificare le attività periodicamente, è necessario impostare una scheda cronologica per tale modulo. Una _crontab_ è una configurazione di processo cron.

Facoltativamente, è possibile impostare un gruppo personalizzato che, tra le altre cose, consente di eseguire i job cron definiti in tale gruppo indipendentemente dagli altri job cron.

Per un&#39;esercitazione dettagliata, vedere [Configurare processi cron personalizzati e gruppi cron (esercitazione)](custom-cron-tutorial.md).

Per una panoramica sui processi cron, vedere [Configurare i processi cron](../cli/configure-cron-jobs.md).

## Configurare i gruppi cron

Questa sezione illustra come creare facoltativamente un gruppo cron per un modulo personalizzato. Se non è necessario eseguire questa operazione, continuare con la sezione successiva.

Un _gruppo cron_ è un gruppo logico che consente di eseguire facilmente cron per più processi alla volta. La maggior parte dei moduli di Commerce utilizza il gruppo cron `default`; alcuni moduli utilizzano il gruppo `index`.

Se si implementa cron per un modulo personalizzato, è possibile scegliere di utilizzare il gruppo `default` o un gruppo diverso.

**Per configurare un gruppo cron per il modulo**:

Crea un file `crontab.xml` nella directory del modulo:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Per un gruppo, il file deve avere il seguente contenuto:

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
| `group_name` | Nome del gruppo cron. Il nome del gruppo non deve necessariamente essere univoco. È possibile eseguire cron per un gruppo alla volta. |
| `job_name` | ID univoco per questo processo cron. |
| `classpath` | Classe da creare come istanza (classpath). |
| `method` | Metodo in `classpath` da chiamare. |
| `time` | Pianificazione in formato cron. Ometti questo parametro se la pianificazione è definita nel database di Commerce o in un altro archivio. |

Il `crontab.xml` risultante con due gruppi potrebbe essere simile al seguente:

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

Ad esempio, consulta [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Specifica delle opzioni del gruppo di celle

È possibile dichiarare un nuovo gruppo e specificarne le opzioni di configurazione (tutte eseguite nell&#39;ambito della visualizzazione archivio) tramite il file `cron_groups.xml`, che si trova in:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Di seguito è riportato un esempio del file `cron_groups.xml`:

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
| `schedule_generate_every` | Frequenza (in minuti) di scrittura delle pianificazioni nella tabella `cron_schedule`. |
| `schedule_ahead_for` | Tempo (in minuti) in anticipo per la scrittura delle pianificazioni nella tabella `cron_schedule`. |
| `schedule_lifetime` | Intervallo di tempo (in minuti) per l&#39;avvio di un processo cron o il processo cron viene considerato non eseguito (&quot;troppo tardi&quot; per l&#39;esecuzione). |
| `history_cleanup_every` | Tempo (in minuti) in cui la cronologia dei cron viene mantenuta nel database. |
| `history_success_lifetime` | Tempo (in minuti) per il quale viene conservato nel database il record dei processi cron completati correttamente. |
| `history_failure_lifetime` | Tempo (in minuti) per il quale viene conservato nel database il record dei processi cron non riusciti. |
| `use_separate_process` | Esegui i processi di questo gruppo cron in un processo php separato |

## Disattivare un processo cron

I processi Cron non dispongono di una funzionalità `disable` simile a quella di [observers](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Tuttavia, è possibile disabilitare un processo cron utilizzando la tecnica seguente: `schedule` un&#39;ora che contiene una data che non si verificherà mai.

Disattivare ad esempio il processo cron `visitor_clean` definito nel modulo `Magento_Customer`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Per disabilitare il processo cron `visitor_clean`, creare un modulo personalizzato e riscrivere il processo cron `visitor_clean` `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Ora il processo cron `visitor_clean` è stato impostato per essere eseguito alle 00:00 del 30 febbraio, in una data che non si verificherà mai.

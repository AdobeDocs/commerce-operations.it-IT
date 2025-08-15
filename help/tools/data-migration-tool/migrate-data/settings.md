---
title: Impostazioni di migrazione dati
description: Scopri come avviare la migrazione delle impostazioni da Magento 1 a Magento 2 con  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Impostazioni di migrazione dati

La modalità `Settings` migra archivi, siti Web e configurazione di sistema come impostazioni di spedizione, pagamento e imposte. In base al nostro [ordine](overview.md#migration-order) di migrazione dati, devi prima migrare le impostazioni.

Prima di iniziare, effettua le seguenti operazioni di preparazione:

1. Accedere al server applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

1. Passare alla directory `/bin` o assicurarsi che sia aggiunta al sistema `PATH`.

>[!NOTE]
>
>Verificare che Magento 2 sia distribuito in modalità `default`. La modalità Sviluppatore può causare errori di convalida nello strumento di migrazione.


Per ulteriori dettagli, consulta la sezione [primi passaggi](overview.md#first-steps).

## Esegui il comando di migrazione delle impostazioni

Per avviare la migrazione delle impostazioni, eseguire:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall&#39;inizio. È possibile utilizzare questo argomento per testare la migrazione

* `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system del file [`config.xml`](../configure.md#configure-migration-in-vendor-folder) dello strumento di migrazione. Questo argomento è obbligatorio.

>[!NOTE]
>
>Con questo comando non vengono migrate tutte le impostazioni di configurazione. Verificare tutte le impostazioni in Magento 2 Admin prima di procedere.


Il messaggio `Migration completed` viene visualizzato dopo il corretto trasferimento delle impostazioni.

## Configurare regole di migrazione personalizzate

È possibile ignorare, rinominare o modificare le configurazioni di sistema durante la migrazione delle impostazioni. Specificare le regole personalizzate nel file `settings.xml`.

1. Accedi al server applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.

1. Passa alla seguente directory:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Ad esempio, se l&#39;applicazione è installata in `/var/www/html`, il file `settings.xml.dist` si trova in una delle seguenti directory:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Per creare un file `settings.xml` dall&#39;esempio fornito, eseguire:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Apporta le modifiche in `settings.xml`.

1. Per specificare il nuovo nome del file delle impostazioni per la mappatura, modificare il tag `<settings_map_file>` nel file `path/to/config.xml`.

Per ulteriori dettagli, consulta la sezione [Modalità di migrazione impostazioni](../technical-specification.md#settings-migration-mode) della [specifica](../technical-specification.md) dello strumento.

## Passaggio successivo della migrazione

* [Migrare i dati](data.md)

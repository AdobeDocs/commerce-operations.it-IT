---
title: Impostazioni di migrazione dati
description: Scopri come avviare la migrazione delle impostazioni dal Magento 1 al Magento 2 con [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Impostazioni di migrazione dati

Il `Settings` la modalità migra archivi, siti Web e configurazione di sistema, ad esempio impostazioni di spedizione, pagamento e imposte. In base alla migrazione dei dati [ordine](overview.md#migration-order), è necessario eseguire prima la migrazione delle impostazioni.

Prima di iniziare, effettua le seguenti operazioni di preparazione:

1. Accedere al server applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

1. Cambia in `/bin` o accertarsi che sia aggiunta al sistema `PATH`.

>[!NOTE]
>
>Assicurati che il Magento 2 sia implementato in `default` modalità. La modalità Sviluppatore può causare errori di convalida nello strumento di migrazione.


Consulta la [primi passi](overview.md#first-steps) per ulteriori dettagli.

## Esegui il comando di migrazione delle impostazioni

Per avviare la migrazione delle impostazioni, eseguire:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. È possibile utilizzare questo argomento per testare la migrazione

* `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system dello strumento di migrazione [`config.xml`](../configure.md#configure-migration-in-vendor-folder) file; questo argomento è obbligatorio.

>[!NOTE]
>
>Con questo comando non vengono migrate tutte le impostazioni di configurazione. Verificare tutte le impostazioni nell&#39;amministratore di Magento 2 prima di procedere.


Il `Migration completed` viene visualizzato un messaggio dopo il corretto trasferimento delle impostazioni.

## Configurare regole di migrazione personalizzate

È possibile ignorare, rinominare o modificare le configurazioni di sistema durante la migrazione delle impostazioni. A questo scopo, specifica le regole personalizzate nel `settings.xml` file.

1. Accedere al server applicazioni come, o passare a, [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

1. Passa alla seguente directory:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Ad esempio, se l’applicazione è installata in `/var/www/html`, il `settings.xml.dist` il file si trova in una delle seguenti directory:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Per creare un `settings.xml` dall’esempio fornito, esegui:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Apporta le modifiche in `settings.xml`.

1. Per specificare il nuovo nome del file di impostazioni per la mappatura, modificare la `<settings_map_file>` tag in `path/to/config.xml` file.

Per ulteriori dettagli, vedi [Modalità di migrazione delle impostazioni](../technical-specification.md#settings-migration-mode) sezione dello strumento [specifica](../technical-specification.md).

## Passaggio successivo della migrazione

* [Migrare i dati](data.md)

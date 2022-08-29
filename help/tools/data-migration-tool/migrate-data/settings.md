---
title: Impostazioni di migrazione dei dati
description: Scopri come avviare la migrazione delle impostazioni dal Magento 1 al Magento 2 con [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Impostazioni di migrazione dei dati

La `Settings` la modalità esegue la migrazione di negozi, siti web e configurazioni di sistema come la spedizione, il pagamento e le impostazioni fiscali. Secondo la migrazione dei nostri dati [ordine](overview.md#migration-order), devi prima eseguire la migrazione delle impostazioni .

Prima di iniziare, procedi come segue per preparare:

1. Accedi al server con la tua istanza di Magento 2 come [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Modifica al Magento 2 `/bin` o accertati che venga aggiunto al percorso del sistema.

>[!NOTE]
>
>Assicurati che il Magento 2 sia distribuito in `default` modalità. La modalità Sviluppatore può causare errori di convalida nello strumento di migrazione.


Consulta la sezione [primi passi](overview.md#first-steps) per ulteriori dettagli.

## Esegui il comando di migrazione delle impostazioni

Per avviare la migrazione delle impostazioni, esegui:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. È possibile utilizzare questo argomento per testare la migrazione

* `[-a|--auto]` è un argomento facoltativo che impedisce l’arresto della migrazione in caso di errori di controllo dell’integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system per lo strumento di migrazione [`config.xml`](../configure.md#configure-migration-in-vendor-folder) file; questo argomento è obbligatorio.

>[!NOTE]
>
>Questo comando non esegue la migrazione di tutte le impostazioni di configurazione. Verifica tutte le impostazioni nel Magento 2 [Amministratore](https://glossary.magento.com/admin) prima di procedere.


La `Migration completed` viene visualizzato un messaggio dopo il corretto trasferimento delle impostazioni.

## Configurare le regole di migrazione personalizzate

È possibile ignorare, rinominare o modificare le configurazioni di sistema durante la migrazione delle impostazioni. A questo scopo, specifica le regole personalizzate nella `settings.xml` file.

1. Accedi al server con la tua istanza di Magento 2 come, o passa a, il [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Passa alla seguente directory:

   ```bash
   cd <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Ad esempio, se il Magento 2 è installato in `/var/www/html`, `settings.xml.dist` il file si trova in una delle seguenti directory:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Per creare una `settings.xml` dal file di esempio fornito, esegui:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Apporta le modifiche in `settings.xml`.

1. Per specificare il nuovo nome del file di impostazioni per la mappatura, modificare il `<settings_map_file>` in `path/to/config.xml` file.

Per ulteriori dettagli, consulta la sezione [Modalità di migrazione impostazioni](../technical-specification.md#settings-migration-mode) della sezione dello strumento [specifica](../technical-specification.md).

## Passaggio di migrazione successivo

* [Eseguire la migrazione dei dati](data.md)

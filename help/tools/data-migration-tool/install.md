---
title: Installa il [!DNL Data Migration Tool]
description: Scopri come installare il [!DNL Data Migration Tool] trasferire i dati tra il Magento 1 e il Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# Installa il [!DNL Data Migration Tool]

>[!INFO]
>
>Versioni del Magento e [!DNL Data Migration Tool] deve corrispondere.


Assicurati di utilizzare *la stessa versione rilasciata* del Magento 2 e del [!DNL Data Migration Tool]. Ad Magento, per la versione 2.2.0, è necessario utilizzare anche il [!DNL Data Migration Tool] versione 2.2.0.

## Controlla la versione

Utilizza uno dei seguenti metodi per verificare la tua versione del Magento:

- [Compositore](#composer-metapackage)
- [Archivio GitHub](#github-repository)

### Metapackage compositore

Se hai scaricato il software di Magento utilizzando un metapackage Composer, immetti il seguente comando:

```bash
php <magento_root>/bin/magento --version
```

### Archivio GitHub

Se hai clonato l’archivio GitHub Magento 2, immetti i seguenti comandi:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Se attualmente ti trovi nella `develop` ramo, è necessario passare a [ramo rilasciato](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) prima di continuare.

Se non hai ancora installato il software Adobe Commerce o Magenti Open Source, [installalo subito](../../installation/prerequisites/commerce.md).
Se cloni l’archivio GitHub, assicurati di estrarre un tag di rilascio come descritto in [(Collaboratore) Clona l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Trova versioni rilasciate di [!DNL Data Migration Tool]

Vai a [Versioni](https://github.com/magento/data-migration-tool/releases) della pagina [!DNL Data Migration Tool] Archivio GitHub per trovare le versioni rilasciate disponibili.

## Installa il [!DNL Data Migration Tool]

È possibile installare [!DNL Data Migration Tool] da:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Prima di eseguire l’installazione, assicurati di disporre di:

- Tutte le attività menzionate in [Condizioni preliminari](prerequisites.md) sezione
- [Verifica della versione](install.md#check-your-version) del software del Magento 2

### Installa da `repo.magento.com`

Per installare [!DNL Data Migration Tool], devi aggiornare `composer.json` nella directory di installazione della radice del Magento per fornire la posizione del [!DNL Data Migration Tool] pacchetto.

1. Accedi al server delle applicazioni come o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passa alla directory principale dell&#39;applicazione.
1. Immetti i seguenti comandi:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Dove `<version>` deve corrispondere alla versione del codebase Magento 2.

   Ad esempio, per la versione 2.2.0, immetti:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Quando richiesto, immetti il [chiavi di autenticazione](../../installation/prerequisites/authentication-keys.md). La tua chiave pubblica è il tuo nome utente; la tua chiave privata è la tua password.

### Installare da GitHub

Se hai clonato l’archivio GitHub, segui i passaggi seguenti per installare il [!DNL Data Migration Tool].

1. Accedi al server delle applicazioni come o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passa alla directory principale dell&#39;applicazione.
1. Immetti i seguenti comandi:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   dove `<version>` deve corrispondere alla versione del codebase Magento 2.

   Ad esempio, per la versione 2.2.0, immetti:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Verifica la versione installata [!DNL Data Migration Tool]

1. Cambia in [!DNL Data Migration Tool] directory: `<vendor>/magento/data-migration-tool`.

1. Apri [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in un editor di testo.

1. La `version` la voce in quel file è la versione del [!DNL Data Migration Tool].

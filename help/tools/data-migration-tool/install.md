---
title: Installare [!DNL Data Migration Tool]
description: Scopri come installare [!DNL Data Migration Tool] trasferire dati tra il Magento 1 e il Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Installare [!DNL Data Migration Tool]

>[!INFO]
>
>Versioni del Magento e [!DNL Data Migration Tool] deve corrispondere.


Assicurati di utilizzare *la stessa versione rilasciata* del Magento 2 e del [!DNL Data Migration Tool]. Ad esempio, per la versione di Magento 2.2.0, è necessario utilizzare anche [!DNL Data Migration Tool] versione 2.2.0.

## Verifica la versione

Utilizza uno dei seguenti metodi per verificare la versione di Magento in uso:

- [Compositore](#composer-metapackage)
- [Archivio GitHub](#github-repository)

### Metapacchetto del compositore

Se il software di Magento è stato scaricato utilizzando un metapacchetto Compositore, immettere il comando seguente:

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

Se al momento sei nel `develop` ramo, devi passare a un [ramo rilasciato](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) prima di continuare.

Se non è ancora stato installato il software Adobe Commerce o di Magento Open Source, [installalo ora](../../installation/prerequisites/commerce.md).
Se stai clonando l’archivio GitHub, assicurati di estrarre un tag di versione come descritto in [(Collaboratore) Clona l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Trova versioni rilasciate di [!DNL Data Migration Tool]

Vai a [Versioni](https://github.com/magento/data-migration-tool/releases) pagina di [!DNL Data Migration Tool] Archivio GitHub per trovare le versioni rilasciate disponibili.

## Installare [!DNL Data Migration Tool]

È possibile installare [!DNL Data Migration Tool] da:

- [&quot;repo.magento.com&quot;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Prima dell’installazione, assicurati di disporre di:

- Ha completato tutte le attività menzionate in [Precondizioni](prerequisites.md) sezione
- [Verificata la versione](install.md#check-your-version) del software Magento 2

### Installa da `repo.magento.com`

Per installare [!DNL Data Migration Tool], è necessario aggiornare `composer.json` nella directory principale di installazione del Magento per fornire la posizione del [!DNL Data Migration Tool] pacchetto.

1. Accedere al server applicazioni come, o passare a, [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory radice dell&#39;applicazione.
1. Immettete i seguenti comandi:

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

1. Quando richiesto, immetti [chiavi di autenticazione](../../installation/prerequisites/authentication-keys.md). La chiave pubblica è il nome utente; la chiave privata è la password.

### Installa da GitHub

Se hai clonato l’archivio GitHub, segui i passaggi seguenti per installare [!DNL Data Migration Tool].

1. Accedere al server applicazioni come, o passare a, [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory radice dell&#39;applicazione.
1. Immettete i seguenti comandi:

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

### Verifica versione di installata [!DNL Data Migration Tool]

1. Cambia in [!DNL Data Migration Tool] directory: `<vendor>/magento/data-migration-tool`.

1. Apri [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in un editor di testo.

1. Il `version` la voce in tale file è la versione di [!DNL Data Migration Tool].

---
title: Installa  [!DNL Data Migration Tool]
description: Scopri come installare  [!DNL Data Migration Tool] per trasferire dati tra Magento 1 e Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Installa [!DNL Data Migration Tool]

>[!INFO]
>
>Le versioni di Magento e [!DNL Data Migration Tool] devono corrispondere.


Assicurati di utilizzare *la stessa versione rilasciata* di Magento 2 e [!DNL Data Migration Tool]. Ad esempio, per Magento versione 2.2.0, è necessario utilizzare anche [!DNL Data Migration Tool] versione 2.2.0.

## Verifica la versione

Utilizza uno dei seguenti metodi per verificare la versione di Magento in uso:

- [Compositore](#composer-metapackage)
- [Archivio GitHub](#github-repository)

### Metapacchetto del compositore

Se il software Magento è stato scaricato utilizzando un metapacchetto Compositore, immettere il comando seguente:

```bash
php <magento_root>/bin/magento --version
```

### Archivio GitHub

Se hai clonato l’archivio GitHub di Magento 2, immetti i seguenti comandi:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Se sei attualmente nel ramo `develop`, devi passare a un ramo [rilasciato](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) prima di continuare.

Se non hai ancora installato il software Adobe Commerce, [installalo ora](../../installation/prerequisites/commerce.md).
Se stai clonando l&#39;archivio GitHub, assicurati di estrarre un tag di versione come descritto in [(Collaboratore) Clonare l&#39;archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Trova versioni rilasciate di [!DNL Data Migration Tool]

Vai alla pagina [Versioni](https://github.com/magento/data-migration-tool/releases) dell&#39;archivio GitHub [!DNL Data Migration Tool] per trovare le versioni rilasciate disponibili.

## Installa [!DNL Data Migration Tool]

È possibile installare [!DNL Data Migration Tool] da:

- [&quot;repo.magento.com&quot;](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Prima dell’installazione, assicurati di disporre di:

- Ha completato tutte le attività menzionate nella sezione [Precondizioni](prerequisites.md)
- [Verifica della versione](install.md#check-your-version) del software Magento 2

### Installa da `repo.magento.com`

Per installare [!DNL Data Migration Tool], è necessario aggiornare `composer.json` nella directory di installazione radice di Magento per specificare il percorso del pacchetto [!DNL Data Migration Tool].

1. Accedi al server applicazioni come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Passare alla directory radice dell&#39;applicazione.
1. Immettete i seguenti comandi:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Dove `<version>` deve corrispondere alla versione della base di codice di Magento 2.

   Ad esempio, per la versione 2.2.0, immetti:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Quando richiesto, immetti le [chiavi di autenticazione](../../installation/prerequisites/authentication-keys.md). La chiave pubblica è il nome utente; la chiave privata è la password.

### Installa da GitHub

Se hai clonato l&#39;archivio GitHub, segui i passaggi seguenti per installare [!DNL Data Migration Tool].

1. Accedi al server applicazioni come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Passare alla directory radice dell&#39;applicazione.
1. Immettete i seguenti comandi:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   dove `<version>` deve corrispondere alla versione della base di codice di Magento 2.

   Ad esempio, per la versione 2.2.0, immetti:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Verifica la versione di [!DNL Data Migration Tool] installata

1. Passare alla directory [!DNL Data Migration Tool]: `<vendor>/magento/data-migration-tool`.

1. Apri [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in un editor di testo.

1. La voce `version` in tale file è la versione di [!DNL Data Migration Tool].

---
title: Panoramica sulla migrazione
description: Scopri come avviare la migrazione dei dati da Magento 1 a Magento 2 con  [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Panoramica sulla migrazione

Prima di avviare la migrazione, arresta tutti i processi cron di Magento 1.

Durante il processo di migrazione, attieniti alle seguenti regole generali per una migrazione corretta:

1. **Non** apportare modifiche nell&#39;amministratore di Magento 1, ad eccezione di Order Management (spedizione, creazione di fatture e note di credito)
1. **Non modificare** il codice
1. **Non** apportare modifiche in Magento 2 Admin and storefront

>[!TIP]
>
>Sono consentite tutte le operazioni nella vetrina di Magento 1.

## Esegui [!DNL Data Migration Tool]

In questa sezione viene illustrato come eseguire [!DNL Data Migration Tool] per migrare impostazioni, dati o modifiche incrementali.

### Primi passaggi

1. Accedere al server applicazioni come utente con autorizzazioni di scrittura nel file system o passare a tale utente. Vedere [passare al proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

   Se si utilizza la shell bash, è possibile utilizzare la sintassi seguente per passare al proprietario del file system e immettere contemporaneamente il comando:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se il proprietario del file system non consente l&#39;accesso, è possibile effettuare le seguenti operazioni:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Per eseguire comandi Magento da qualsiasi directory, aggiungere `<magento_root>/bin` al sistema `PATH`.

   Poiché la sintassi delle shell è diversa, consultare un riferimento come [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Shell di base di esempio per CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Facoltativamente, è possibile eseguire i comandi nei modi seguenti:

   - `cd <magento_root>/bin` ed eseguirli come `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` è una sottodirectory della directory principale dei documenti del server Web.

### Sintassi dei comandi

Di seguito è riportato un esempio di comando tipico:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

- `<mode>` può essere: [`settings`](settings.md), [`data`](data.md) o [`delta`](delta.md)
- `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall&#39;inizio. È possibile utilizzare questo argomento per testare la migrazione.
- `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.
- `{<path to config.xml>}` è il percorso assoluto del file system di `config.xml`. Questo argomento è obbligatorio.

>[!NOTE]
>
>I registri vengono scritti nella directory `<magento_root>/var/`.


## Ordine di migrazione

Quando abbiamo creato [!DNL Data Migration Tool], abbiamo assunto la seguente sequenza di trasferimento dati:

1. [Impostazioni](settings.md)
1. [Dati](data.md)
1. [Modifiche](delta.md)

È consigliabile eseguire la migrazione dei dati nello stesso ordine.

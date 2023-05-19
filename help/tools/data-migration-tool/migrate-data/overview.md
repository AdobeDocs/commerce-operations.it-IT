---
title: Panoramica sulla migrazione
description: Scopri come avviare la migrazione dei dati dal Magento 1 al Magento 2 con [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Panoramica sulla migrazione

Prima di avviare la migrazione, arresta tutti i processi cron del Magento 1.

Durante il processo di migrazione, attieniti alle seguenti regole generali per una migrazione corretta:

1. **Do not** apportare modifiche nell&#39;amministratore Magento 1, ad eccezione di Order Management (spedizione, creazione di fatture e note di accredito)
1. **Do not** modificare qualsiasi codice
1. **Do not** apportare modifiche nell’interfaccia di amministrazione e vetrina del Magento 2

>[!TIP]
>
>Sono consentite tutte le operazioni nella vetrina del Magento 1.

## Esegui il [!DNL Data Migration Tool]

Questa sezione mostra come eseguire [!DNL Data Migration Tool] per migrare impostazioni, dati o modifiche incrementali.

### Primi passaggi

1. Accedere al server applicazioni come utente con autorizzazioni di scrittura nel file system o passare a tale utente. Consulta [passa al proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

   Se si utilizza la shell bash, è possibile utilizzare la sintassi seguente per passare al proprietario del file system e immettere contemporaneamente il comando:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se il proprietario del file system non consente l&#39;accesso, è possibile effettuare le seguenti operazioni:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Per eseguire comandi di Magento da qualsiasi directory, aggiungere `<magento_root>/bin` al sistema `PATH`.

   Poiché le shell hanno una sintassi diversa, consulta un riferimento come [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Shell di base di esempio per CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Facoltativamente, è possibile eseguire i comandi nei modi seguenti:

   - `cd <magento_root>/bin` ed eseguirli come `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` è una sottodirectory della directory principale dei documenti del server web.

### Sintassi dei comandi

Di seguito è riportato un esempio di comando tipico:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

- `<mode>` può essere: [`settings`](settings.md), [`data`](data.md), o [`delta`](delta.md)
- `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. È possibile utilizzare questo argomento per testare la migrazione.
- `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.
- `{<path to config.xml>}` è il percorso assoluto del file system a `config.xml`; questo argomento è obbligatorio.

>[!NOTE]
>
>I registri vengono scritti in `<magento_root>/var/` directory.


## Ordine di migrazione

Quando abbiamo creato [!DNL Data Migration Tool], abbiamo assunto la seguente sequenza di trasferimento dei dati:

1. [Impostazioni](settings.md)
1. [Dati](data.md)
1. [Modifiche](delta.md)

È consigliabile eseguire la migrazione dei dati nello stesso ordine.

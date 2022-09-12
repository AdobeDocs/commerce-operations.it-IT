---
title: Panoramica sulla migrazione
description: Scopri come avviare la migrazione dei dati dal Magento 1 al Magento 2 con [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Panoramica sulla migrazione

Prima di avviare la migrazione, interrompi tutti i lavori di cron Magento 1.

Durante il processo di migrazione, segui queste regole generali per una migrazione di successo:

1. **Non** apportare modifiche all&#39;amministratore del Magento 1, ad eccezione della gestione degli ordini (spedizione, creazione di fatture e note di accredito)
1. **Non** modificare qualsiasi codice
1. **Non** apportare modifiche al Magento 2 Admin e [vetrina](https://glossary.magento.com/storefront)

>[!TIP]
>
>Tutte le operazioni nella vetrina del Magento 1 sono consentite.

## Esegui il [!DNL Data Migration Tool]

Questa sezione mostra come eseguire il [!DNL Data Migration Tool] per eseguire la migrazione di impostazioni, dati o modifiche incrementali.

### Primi passi

1. Accedi al server applicazioni come utente autorizzato a scrivere nel file system o passa a un utente con autorizzazioni di scrittura. Vedi [passa al proprietario del file system](../../../installation/prerequisites/file-system/overview.md).

   Se si utilizza la shell bash, è possibile utilizzare la sintassi seguente per passare al proprietario del file system e immettere il comando contemporaneamente:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se il proprietario del file system non consente l&#39;accesso, è possibile effettuare le seguenti operazioni:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Per eseguire i comandi di Magento da qualsiasi directory, aggiungi `<magento_root>/bin` al sistema `PATH`.

   Poiché le conchiglie hanno sintassi diversa, consulta un riferimento come [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   shell di base di esempio per CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Facoltativamente, è possibile eseguire i comandi nei seguenti modi:

   - `cd <magento_root>/bin` e eseguili come `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` è una sottodirectory del docroot del server web.

### Sintassi dei comandi

Di seguito è riportato un esempio di comando tipico:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

- `<mode>` può essere: [`settings`](settings.md), [`data`](data.md)oppure [`delta`](delta.md)
- `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. Puoi utilizzare questo argomento per testare la migrazione.
- `[-a|--auto]` è un argomento facoltativo che impedisce l’arresto della migrazione in caso di errori di controllo dell’integrità.
- `{<path to config.xml>}` è il percorso assoluto del file system a `config.xml`; questo argomento è obbligatorio.

>[!NOTE]
>
>I registri vengono scritti in `<magento_root>/var/` directory.


## Ordine di migrazione

Quando abbiamo creato il [!DNL Data Migration Tool], abbiamo assunto la seguente sequenza di trasferimento dati:

1. [Impostazioni](settings.md)
1. [Dati](data.md)
1. [Modifiche](delta.md)

È consigliabile eseguire la migrazione dei dati nello stesso ordine.

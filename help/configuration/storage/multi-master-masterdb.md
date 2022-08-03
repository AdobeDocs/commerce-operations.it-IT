---
title: Configurazione automatica dei database master
description: Consulta le indicazioni sulla configurazione automatica della soluzione di database suddiviso.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# Configurazione automatica dei database master

{#ee-only}

{{deprecate-split-db}}

Questo argomento illustra come iniziare a utilizzare la soluzione di database suddivisi:

1. Installazione di Adobe Commerce con un singolo database master (denominato `magento`)
1. Creazione di due database master aggiuntivi per [pagamento](https://glossary.magento.com/checkout) e OMS (denominati `magento_quote` e `magento_sales`)
1. Configurazione di Adobe Commerce per l’utilizzo dei database di pagamento e di vendita

>[!INFO]
>
>Questa guida presuppone che tutti e tre i database si trovino sullo stesso host dell&#39;applicazione Commerce e che siano denominati `magento`, `magento_quote`e `magento_sales`. Tuttavia, spetta a te scegliere dove individuare i database e il loro nome. Speriamo che i nostri esempi rendano le istruzioni più facili da seguire.

## Installare il software Adobe Commerce

È possibile abilitare i database suddivisi in qualsiasi momento dopo l&#39;installazione del software Adobe Commerce; in altre parole, puoi aggiungere database suddivisi a un sistema Adobe Commerce che dispone già di dati di pagamento e di ordine. Utilizza le istruzioni in Adobe Commerce README o [guida all&#39;installazione](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html) per installare il software Adobe Commerce utilizzando un singolo database master.

## Configurare database master aggiuntivi

Creare database master di checkout e OMS come segue:

1. Accedi al server di database come qualsiasi utente.
1. Immettere il comando seguente per accedere a un prompt dei comandi MySQL:

   ```bash
   mysql -u root -p
   ```

1. Immettere MySQL `root` password dell&#39;utente quando richiesto.
1. Immettere i seguenti comandi nell&#39;ordine mostrato per creare istanze di database denominate `magento_quote` e `magento_sales` con gli stessi nomi utente e password:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Invio `exit` per uscire dal prompt dei comandi.

1. Verificare i database, uno alla volta:

   Database di estrazione:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Database del sistema di gestione ordini:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Se viene visualizzato il monitoraggio MySQL, il database è stato creato correttamente. Se viene visualizzato un errore, ripetere i comandi precedenti.

## Configurare Commerce per l’utilizzo dei database master

Dopo aver impostato un totale di tre database master, utilizzare la riga di comando per configurare Commerce per utilizzarli. Il comando imposta le connessioni al database e distribuisce le tabelle tra i database master.

### Primi passi

Vedi [Esecuzione dei comandi](../cli/config-cli.md#running-commands) per accedere ed eseguire i comandi CLI.

### Configurare il database di estrazione

Sintassi di comando:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Ad esempio:

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Viene visualizzato il seguente messaggio per confermare l&#39;esecuzione della configurazione:

```terminal
Migration has been finished successfully!
```

### Configurare il database OMS

Sintassi di comando:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Ad esempio:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

Viene visualizzato il seguente messaggio per confermare l&#39;esecuzione della configurazione:

```terminal
Migration has been finished successfully!
```

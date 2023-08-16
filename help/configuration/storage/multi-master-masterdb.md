---
title: Configura automaticamente i database master
description: Consulta le linee guida per la configurazione automatica della soluzione di database diviso.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Configura automaticamente i database master

{{ee-only}}

{{deprecate-split-db}}

In questo argomento viene illustrato come iniziare a utilizzare la soluzione di database suddiviso:

1. Installazione di Adobe Commerce con un singolo database principale (denominato `magento`)
1. Creazione di due database master aggiuntivi per l&#39;estrazione e OMS (denominati `magento_quote` e `magento_sales`)
1. Configurazione di Adobe Commerce per l&#39;utilizzo dei database di pagamento e di vendita

>[!INFO]
>
>Questa guida presuppone che tutti e tre i database si trovino sullo stesso host dell’applicazione Commerce e che siano denominati `magento`, `magento_quote`, e `magento_sales`. Tuttavia, spetta a te scegliere dove individuare i database e il nome. Ci auguriamo che i nostri esempi rendano le istruzioni più facili da seguire.

## Installare il software Adobe Commerce

È possibile abilitare i database suddivisi in qualsiasi momento dopo l&#39;installazione del software Adobe Commerce; in altre parole, è possibile aggiungere database suddivisi a un sistema Adobe Commerce che dispone già di dati di estrazione e ordine. Utilizzare le istruzioni contenute nel file README di Adobe Commerce o [guida all’installazione](../../installation/overview.md) per installare il software Adobe Commerce utilizzando un singolo database principale.

## Imposta database master aggiuntivi

Creare i database master di estrazione e OMS nel modo seguente:

1. Accedere al server del database come qualsiasi utente.
1. Immettere il comando seguente per accedere al prompt dei comandi MySQL:

   ```bash
   mysql -u root -p
   ```

1. Immettere MySQL `root` password dell&#39;utente quando richiesto.
1. Immettere i seguenti comandi nell&#39;ordine indicato per creare istanze di database denominate `magento_quote` e `magento_sales` con gli stessi nomi utente e password:

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

   Database del sistema di gestione degli ordini:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Se viene visualizzato il monitoraggio MySQL, il database è stato creato correttamente. Se viene visualizzato un errore, ripetere i comandi precedenti.

## Configurare Commerce per l’utilizzo dei database master

Dopo aver impostato un totale di tre database master, utilizzare la riga di comando per configurare Commerce per l&#39;utilizzo. Il comando consente di impostare le connessioni al database e di distribuire le tabelle tra i database master.

### Primi passaggi

Consulta [Esecuzione dei comandi](../cli/config-cli.md#running-commands) per accedere ed eseguire i comandi CLI.

### Configurare il database di estrazione

Sintassi del comando:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Ad esempio:

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Viene visualizzato il seguente messaggio per confermare la corretta configurazione:

```terminal
Migration has been finished successfully!
```

### Configurare il database OMS

Sintassi del comando:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Ad esempio:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

Viene visualizzato il seguente messaggio per confermare la corretta configurazione:

```terminal
Migration has been finished successfully!
```

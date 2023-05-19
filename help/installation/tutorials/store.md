---
title: Configurare l’archivio
description: Per configurare l’archivio Adobe Commerce o di Magento Open Source, segui la procedura riportata di seguito.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Configurare l’archivio

Prima di eseguire questo comando, è necessario effettuare le seguenti operazioni *o* devi [installare l’applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Configurare l’archivio

Utilizzo comando:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Dove la tabella seguente definisce parametri e valori:

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--base-url` | URL di base da utilizzare per accedere all’amministratore e alla vetrina in uno dei seguenti formati:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** Il regime (`http://` o `https://`) e una barra finale. `<your install dir>` è il percorso relativo alla directory principale dei documenti in cui installare l&#39;applicazione. A seconda della configurazione del server web e degli host virtuali, il percorso potrebbe essere magento2 o vuoto.<br><br>Per accedere all’applicazione su localhost, puoi utilizzare `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` che rappresenta un URL di base definito da un&#39;impostazione host virtuale o da un ambiente di virtualizzazione come Docker. Ad esempio, se imposti un host virtuale con il nome host commerce.example.com, puoi installare l’applicazione con `--base-url={{base_url}}` e accedere all’amministratore con un URL come `http://commerce.example.com/admin`. | No |
| `--language` | Codice lingua da utilizzare nell’amministrazione e nella vetrina.<br><br>Se non lo hai già fatto, puoi visualizzare l’elenco dei codici lingua immettendo `magento info:language:list` dal `bin` directory.) | No |
| `--currency` | Valuta predefinita da utilizzare nella vetrina. <br><br>(Se non lo hai già fatto, puoi visualizzare l’elenco delle valute inserendo `magento info:currency:list` dal `bin` directory.) | No |
| `--timezone` | Fuso orario predefinito da utilizzare in Admin e storefront. (Se non lo hai già fatto, puoi visualizzare l’elenco dei fusi orari inserendo `magento info:timezone:list` dal `bin` directory.) | No |
| `--use-rewrites` | `1` significa che utilizzi le riscritture del server web per i collegamenti generati nella vetrina e in Admin.<br><br>`0` disabilita l&#39;utilizzo delle riscritture del server web. Questa è l&#39;impostazione predefinita. | No |
| `--use-secure` | `1` consente l’utilizzo di Secure Sockets Layer (SSL) negli URL della vetrina. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` disabilita l&#39;utilizzo di SSL. In questo caso, anche tutte le altre opzioni URL protetto sono impostate su 0. Questa è l&#39;impostazione predefinita. | No |
| `--base-url-secure` | URL di base sicuro da utilizzare per accedere all’amministratore e alla vetrina nel seguente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa che utilizzi SSL per accedere all’Admin. Prima di selezionare questa opzione, assicurati che il server web supporti SSL.<br><br>`0` significa che non utilizzi SSL con l’amministratore. Questa è l&#39;impostazione predefinita. | No |
| `--admin-use-security-key` | `1` fa in modo che l’applicazione utilizzi un valore chiave generato in modo casuale per accedere alle pagine in Admin e nei moduli. Questi valori chiave aiutano a prevenire attacchi di tipo cross-site script forgery. Questa è l&#39;impostazione predefinita.<br/><br/>`0` disabilita l&#39;utilizzo della chiave. | No |
| `--magento-init-params` | Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione dell&#39;applicazione<br/><br/>Ad esempio: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

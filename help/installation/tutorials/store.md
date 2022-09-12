---
title: Configurare lo store
description: Segui questi passaggi per configurare il tuo archivio Adobe Commerce o Magenti Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Configurare lo store

Prima di eseguire questo comando, è necessario effettuare le seguenti operazioni *o* devi [installare l&#39;applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Configurare lo store

Utilizzo comando:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Se la tabella seguente definisce parametri e valori:

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--base-url` | URL di base da utilizzare per accedere all’amministratore e alla vetrina in uno dei seguenti formati:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** Il regime (`http://` o `https://`) e una barra finale sono entrambi necessari. `<your install dir>` è il percorso relativo al docroot in cui installare l&#39;applicazione. A seconda della configurazione del server web e degli host virtuali, il percorso potrebbe essere magento2 o vuoto.<br><br>Per accedere all&#39;applicazione su localhost, puoi utilizzare `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` che rappresenta un URL di base definito da un&#39;impostazione host virtuale o da un ambiente di virtualizzazione come Docker. Ad esempio, se imposti un host virtuale con il nome host commerce.example.com, puoi installare l’applicazione con `--base-url={{base_url}}` e accedi all’amministratore con un URL come `http://commerce.example.com/admin`. | No |
| `--language` | Codice lingua da utilizzare nell’amministrazione e nella vetrina.<br><br>Se non lo hai già fatto, puoi visualizzare l’elenco dei codici della lingua immettendo `magento info:language:list` dal `bin` ). | No |
| `--currency` | Valuta predefinita da utilizzare nella vetrina. <br><br>(Se non lo hai già fatto, puoi visualizzare l&#39;elenco delle valute immettendo `magento info:currency:list` dal `bin` ). | No |
| `--timezone` | Fuso orario predefinito da utilizzare in Admin e nella vetrina. Se non lo hai già fatto, puoi visualizzare l’elenco dei fusi orari immettendo `magento info:timezone:list` dal `bin` ). | No |
| `--use-rewrites` | `1` significa che utilizzi le riscritture del server web per i collegamenti generati nella vetrina e nell’amministrazione.<br><br>`0` disabilita l&#39;utilizzo delle riscritture del server web. Questa è l’impostazione predefinita. | No |
| `--use-secure` | `1` abilita l&#39;utilizzo di Secure Sockets Layer (SSL) negli URL di vetrina. Assicurati che il server web supporti SSL prima di selezionare questa opzione.<br><br>`0` disabilita l’utilizzo di SSL. In questo caso, anche tutte le altre opzioni URL sicure vengono considerate pari a 0. Questa è l’impostazione predefinita. | No |
| `--base-url-secure` | URL di base sicuro da utilizzare per accedere all&#39;amministratore e alla vetrina nel seguente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa che utilizzi SSL per accedere all’amministratore. Assicurati che il server web supporti SSL prima di selezionare questa opzione.<br><br>`0` significa che non utilizzi SSL con l’amministratore. Questa è l’impostazione predefinita. | No |
| `--admin-use-security-key` | `1` fa sì che l’applicazione utilizzi un valore chiave generato in modo casuale per accedere alle pagine nell’amministratore e nei moduli. Questi valori chiave consentono di evitare attacchi di falsificazione di script tra siti diversi. Questa è l’impostazione predefinita.<br/><br/>`0` disabilita l’utilizzo della chiave. | No |
| `--magento-init-params` | Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione dell&#39;applicazione<br/><br/>Ad esempio: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

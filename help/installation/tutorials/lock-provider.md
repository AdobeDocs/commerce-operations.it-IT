---
title: Configurare il provider di blocco
description: Segui questi passaggi per evitare che i processi cron duplicati e i gruppi cron vengano eseguiti sulla distribuzione Adobe Commerce o Magenti Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Configurare il provider di blocco

Prima di eseguire questo comando, è necessario effettuare le seguenti operazioni *o* devi [installare l&#39;applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Configurare il blocco

Configura un provider di blocco per impedire il lancio di lavori cron duplicati e gruppi cron duplicati. (Richiede Adobe Commerce o Magenti Open Source 2.2.x, 2.2.5 e versioni successive e 2.3.3 e versioni successive.)

Adobe Commerce e Magenti Open Source utilizzano il database per salvare i blocchi per impostazione predefinita. Se sui server sono presenti più nodi, è consigliabile utilizzare Zookeeper come provider di blocco.

Se si esegue Adobe Commerce sull&#39;infrastruttura cloud, non è necessario configurare le impostazioni del provider di blocchi. L&#39;applicazione configura il provider del blocco file per i progetti Pro durante il processo di provisioning. Vedi [Variabili cloud](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Utilizzo dei comandi

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrizioni dei parametri

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--lock-provider` | Nome provider di blocco: `db`, `zookeeper`oppure `file`.<br><br>Provider di blocco predefinito: `db` | No |
| `--lock-db-prefix` | Prefisso del database specifico per evitare conflitti di blocco quando si utilizza `db` provider di blocco.<br><br>Il valore predefinito: `NULL` | No |
| `--lock-zookeeper-host` | Host e porta per connettersi al cluster Zookeeper quando si utilizza il `zookeeper` provider di blocco.<br><br>Ad esempio: `127.0.0.1:2181` | Sì, se si imposta `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Il percorso in cui Zookeeper salva le serrature.<br><br>Il percorso predefinito è: `/magento/locks` | No |
| `--lock-file-path` | Percorso in cui vengono salvati i blocchi di file. | Sì, se si imposta `--lock-provider=file` |

---
title: Configurare il provider di blocchi
description: Segui questi passaggi per evitare che i processi e i gruppi cron duplicati vengano eseguiti nell’implementazione di Adobe Commerce.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Configurare il provider di blocchi

Prima di eseguire questo comando, è necessario eseguire *o* [installare l&#39;applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Installazione sicura

{{$include /help/_includes/secure-install.md}}

## Configurare il blocco

Configurare un provider di blocchi per impedire l&#39;avvio di processi cron e gruppi cron duplicati. (Richiede Adobe Commerce 2.2.x, 2.2.5 e versioni successive e 2.3.3 e versioni successive).

Per impostazione predefinita, Adobe Commerce utilizza il database per salvare i blocchi. Se sui tuoi server sono presenti più nodi, ti consigliamo di utilizzare Zookeeper come provider di blocchi.

Se esegui Adobe Commerce su un’infrastruttura cloud, non è necessario configurare le impostazioni del provider di blocchi. L&#39;applicazione configura il provider di blocco file per i progetti Pro durante il processo di provisioning. Vedi [Variabili cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Utilizzo dei comandi

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrizioni dei parametri

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--lock-provider` | Nome provider di blocchi: `db`, `zookeeper` o `file`.<br><br>Provider di blocchi predefinito: `db` | No |
| `--lock-db-prefix` | Prefisso db specifico per evitare conflitti di blocco quando si utilizza il provider di blocchi `db`.<br><br>Valore predefinito: `NULL` | No |
| `--lock-zookeeper-host` | Host e porta per la connessione al cluster Zookeeper quando si utilizza il provider di blocchi `zookeeper`.<br><br>Esempio: `127.0.0.1:2181` | Sì, se si imposta `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Percorso in cui Zookeeper salva i blocchi.<br><br>Percorso predefinito: `/magento/locks` | No |
| `--lock-file-path` | Percorso in cui vengono salvati i blocchi di file. | Sì, se si imposta `--lock-provider=file` |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->

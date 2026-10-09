---
title: Configurare il provider di blocchi
description: Segui questi passaggi per evitare che i processi e i gruppi cron duplicati vengano eseguiti nell’implementazione di Adobe Commerce.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
last-update: 2026-08-19T00:00:00.000Z
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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

Se esegui Adobe Commerce su un’infrastruttura cloud, non è necessario configurare le impostazioni del provider di blocchi. L&#39;applicazione configura il provider di blocco file per i progetti Pro durante il processo di provisioning. Vedi [Variabili cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-cloud).

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

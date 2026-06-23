---
title: Cancellazione della cache con più istanze di vernice
description: Scopri come funziona la cancellazione della cache con più istanze di Vernice in Adobe Commerce. Scopri le best practice per la configurazione e la gestione.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 0%

---

# Cancellazione della cache con più istanze di vernice

Adobe Commerce supporta più istanze di vernice pronte all’uso.

Questo argomento illustra le nozioni di base sulla configurazione di più istanze di Vernice con Commerce.

{{varnish-config-cloud}}

## Configurazione per eliminare più istanze di vernice

Commerce elimina gli host Varnish dopo aver configurato gli host Varnish utilizzando il comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

È necessario utilizzare il parametro `--http-cache-hosts` per specificare un elenco separato da virgole di host e porte di ascolto di Microsoft. (Non separare gli host con uno spazio).

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

È quindi possibile eliminare tutti gli host Vernice quando si aggiorna la cache di Commerce (nota anche come _pulizia_ della cache) nell&#39;Admin o utilizzando la riga di comando.

Per aggiornare la cache utilizzando l&#39;amministratore, fare clic su **SISTEMA** > Strumenti > **Gestione cache**, quindi fare clic su **Svuota cache di Magento** nella parte superiore della pagina. (Puoi anche aggiornare singoli tipi di cache).

Per aggiornare la cache di più istanze di Microsoft da cli, utilizzare il comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) come [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

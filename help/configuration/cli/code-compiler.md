---
title: Compilatore di codice
description: Scopri come eseguire il compilatore di codice dalla riga di comando.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Compilatore di codice

{{file-system-owner}}

La compilazione del codice include quanto segue (in nessun ordine particolare):

- Generazione del codice dell&#39;applicazione (factory, proxy)
- Aggregazione della configurazione di area (configurazioni ottimizzate di iniezione di dipendenza per area)
- Generazione di intercettori (generazione di codici ottimizzata di intercettori)
- Generazione della cache di intercettazione
- Generazione del codice degli archivi (codice generato per le API)
- Generazione attributi dati del servizio (classi di estensione generate per gli oggetti dati)

Le classi di compilazione del codice sono disponibili nello spazio dei nomi [\Magento\Setup\Module\Di\App\Task\Operation][operation].

Per eseguire il compilatore a tenant singolo:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

Per compilare il codice prima di installare l&#39;applicazione Commerce:

In alcuni casi, potrebbe essere utile compilare il codice prima di installare l&#39;applicazione Commerce.

1. Abilita i moduli.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilizzare l&#39;opzione `[-c|--clear-static-content]` per cancellare il contenuto statico. Ciò è necessario se in precedenza hai attivato o disattivato i moduli e devi cancellare il contenuto statico generato in precedenza per essi.

   Vedi [Abilita moduli](../../installation/tutorials/manage-modules.md).

1. Compila il codice.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Per compilare il codice senza un database, vedere [Distribuire i file di visualizzazione statica senza installare il Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation

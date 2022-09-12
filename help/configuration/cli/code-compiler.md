---
title: Compilatore di codice
description: Scopri come eseguire il compilatore di codice dalla riga di comando.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Compilatore di codice

{{file-system-owner}}

La compilazione del codice comprende i seguenti elementi (in nessun ordine particolare):

- Generazione del codice dell&#39;applicazione (stabilimenti, proxy)
- Aggregazione di configurazione dell&#39;area (ottimizzata) [iniezione di dipendenza](https://glossary.magento.com/dependency-injection) configurazioni per area)
- Generazione di intercettori (generazione di codici ottimizzata di intercettatori)
- Generazione della cache di intercettazione
- Generazione del codice degli archivi (codice generato per API)
- Generazione attributi di dati del servizio (generato [estensione](https://glossary.magento.com/extension) classi per oggetti dati)

È possibile trovare le classi di compilazione del codice nel [\Magento\Setup\Module\Di\App\Task\Operation][operation] spazio dei nomi.

Per eseguire il compilatore a tenant singolo:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Per compilare il codice prima di installare l’applicazione Commerce:

In alcuni casi, potrebbe essere utile compilare il codice prima di installare l’applicazione Commerce.

1. Abilitare i moduli.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilizza la `[-c|--clear-static-content]` opzione di cancellazione [contenuto statico](https://glossary.magento.com/static-content). Questo è necessario se in precedenza hai abilitato o disabilitato i moduli e devi cancellare per essi il contenuto statico generato in precedenza.

   Vedi [Abilitare i moduli](../../installation/tutorials/manage-modules.md).

1. Compila il codice.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Per compilare il codice senza un database, vedere [Distribuire file di visualizzazione statici senza installare il Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation

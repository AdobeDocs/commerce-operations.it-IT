---
title: Rapporti di dipendenza
description: Crea rapporti che mostrano i totali per le dipendenze di moduli, circolari e framework.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# Rapporti di dipendenza

{{file-system-owner}}

Puoi eseguire i seguenti tipi di report:

- **Dipendenze dal modulo**: Mostra il numero totale di dipendenze tra i moduli e se le dipendenze sono dure o morbide.
- **Dipendenze circolari**: Mostra il numero totale di catene di dipendenza e il numero e l&#39;elenco di dipendenze circolari per ciascun modulo.
- **Dipendenze del framework**: Mostra il numero totale di dipendenze dal framework Commerce per modulo (incluso il numero totale di voci del framework per ogni libreria).

Una dipendenza in un commento è anche una dipendenza.

## Eseguire rapporti di dipendenza

Opzioni di comando:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

Nella tabella seguente sono illustrate le opzioni, i parametri e i valori di questo comando.

| Parametro | Valore | Obbligatorio |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Rapporto sulle dipendenze del modulo. | Sì |
| `show-modules-circular` | Rapporto dipendenze circolari. | Sì |
| `show-framework` | Rapporto sulle dipendenze del framework. | Sì |
| `-d --directory` | Percorso della directory di base per iniziare la ricerca dei dati del report. | No |
| `-o --output` | Specifica il percorso assoluto del file system e il nome del file di output del valore separato da virgole (csv) per il report. | No |

Se non viene passato alcun nome di file o directory come argomento, viene utilizzata la seguente radice dell&#39;applicazione come directory predefinita e vengono utilizzati i seguenti nomi di file predefiniti:

| Comando | Nome file |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Rapporto sulle dipendenze del modulo di esempio

Di seguito è riportata una parte dell’output del report delle dipendenze di un modulo di esempio:

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Esempio di rapporto sulle dipendenze circolari

Di seguito è riportata una parte dell&#39;output per un report di dipendenze circolari di esempio:

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Rapporto sulle dipendenze del framework di esempio

Di seguito è riportata una parte dell&#39;output per un report delle dipendenze del framework di esempio:

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```

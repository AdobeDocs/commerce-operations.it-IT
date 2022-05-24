---
title: '"[!DNL Upgrade Compatibility Tool] Prerequisiti"'
description: 'Verifica che il sistema soddisfi i requisiti necessari per eseguire il [!DNL Upgrade Compatibility Tool] per il progetto Adobe Commerce. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] prerequisiti

{{commerce-only}}

Requisiti minimi per l&#39;esecuzione del [!DNL Upgrade Compatibility Tool] sono:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7,3 |
| Compositore | nessuno |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`oppure `>=16.0.0`) |
| Limiti di memoria | Almeno 2 GB di RAM |
| Chiavi di accesso di Adobe Commerce | nessuno |
| Adobe Commerce | nessuno |

Puoi eseguire il [!DNL Upgrade Compatibility Tool] in diversi sistemi operativi (Windows non supportato). Non è necessario eseguire il [!DNL Upgrade Compatibility Tool] dove si trova l’istanza Adobe Commerce.

È necessario per [!DNL Upgrade Compatibility Tool] per avere accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server. Fai riferimento a [installare](../upgrade-compatibility-tool/install.md) per ulteriori informazioni.

Se esegui la [!DNL Upgrade Compatibility Tool] rispetto a un&#39;istanza Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere un&#39;elevata quantità di RAM (almeno 2 GB). È possibile utilizzare `[=MODULE-PATH]` nel comando per specificare la directory del percorso del modulo per evitare problemi dovuti a una limitazione della memoria insufficiente:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `[=MODULE-PATH]`: Directory del percorso del modulo specifico.

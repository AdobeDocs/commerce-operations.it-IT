---
title: Prerequisiti per lo strumento di compatibilità per l’aggiornamento
description: 'Verifica che il sistema soddisfi i requisiti necessari per eseguire lo strumento di compatibilità per l’aggiornamento del progetto Adobe Commerce. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prerequisiti per lo strumento di compatibilità per l’aggiornamento

L’esecuzione dello strumento di compatibilità per l’aggiornamento consente di identificare le operazioni da eseguire **prima** aggiornamento della versione Adobe Commerce.

I requisiti minimi per l’esecuzione dello strumento di compatibilità per l’aggiornamento sono i seguenti:

| **Requisiti** | **Vincoli** |
|----------------|-----------------|
| Versione PHP | >= 7,3 |
| Compositore | nessuno |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`oppure `>=16.0.0`) |
| Limiti di memoria | Almeno 2 GB di RAM |
| Chiavi di accesso di Adobe Commerce | nessuno |
| Adobe Commerce (Open Source o Enterprise) | nessuno |

È possibile eseguire lo strumento di compatibilità per l&#39;aggiornamento in qualsiasi sistema operativo. Non è necessario eseguire lo strumento di compatibilità per l’aggiornamento in cui si trova l’istanza di Adobe Commerce.

È necessario che lo strumento di compatibilità per l’aggiornamento abbia accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, puoi installarlo su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server. Fai riferimento a [installare](../upgrade-compatibility-tool/install.md) per ulteriori informazioni.

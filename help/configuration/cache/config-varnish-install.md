---
title: Installa vernice
description: Scopri i requisiti di installazione di Vernice per il caching di Adobe Commerce. Scopri le risorse di installazione e le linee guida per la configurazione.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Installa vernice

L&#39;installazione del software Vernice esula dallo scopo di questa guida. Per ulteriori informazioni sull&#39;installazione di Vernice, vedere:

- [guida all&#39;installazione](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guide all&#39;installazione di vernice](https://www.varnish-cache.org/docs)
- [Come installare Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Questo argomento è stato scritto per Varnish su CentOS e Apache 2.4. Se si imposta la vernice in un ambiente diverso, è probabile che alcuni comandi siano diversi. Per ulteriori informazioni, consulta la documentazione precedente.
>
>Se si desidera installare i moduli di vernice (vmod), ad esempio la modalità saint, è consigliabile installare Vernice compilando il codice anziché installandolo da un pacchetto. Per ulteriori dettagli, vedere [Modalità SAINT](config-varnish-advanced.md#saint-mode).

## Conferma la versione di vernice

Apri un terminale e immetti il seguente comando per visualizzare la versione di Vernice:

```bash
varnishd -V
```

Prima di continuare, assicurati che [Adobe Commerce supporti](../../installation/system-requirements.md) la versione installata di Vernice. Se esegui una versione non supportata, devi passare a una versione supportata. Per ulteriori informazioni, consultare la documentazione di installazione di Vernice.

---
title: Installa vernice
description: Consulta i consigli sull’installazione di Varnish.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Installa vernice

L&#39;installazione del software Vernice esula dallo scopo di questa guida. Per ulteriori informazioni sull&#39;installazione di Vernice, vedere:

- [guida all’installazione](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guide all&#39;installazione di vernice](https://www.varnish-cache.org/docs)
- [Come installare Vernice (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Questo argomento è stato scritto per Varnish su CentOS e Apache 2.4. Se si imposta la vernice in un ambiente diverso, è probabile che alcuni comandi siano diversi. Per ulteriori informazioni, consulta la documentazione precedente.
>
>Se si desidera installare i moduli di vernice (vmod), ad esempio la modalità saint, è consigliabile installare Vernice compilando il codice anziché installandolo da un pacchetto. Consulta [Modalità Saint](config-varnish-advanced.md#saint-mode) per ulteriori dettagli.

## Conferma la versione di vernice

Apri un terminale e immetti il seguente comando per visualizzare la versione di Vernice:

```bash
varnishd -V
```

Assicurati che [Adobe Commerce e il Magento Open Source supportano](../../installation/system-requirements.md) la versione installata di Vernice prima di continuare. Se esegui una versione non supportata, devi passare a una versione supportata. Per ulteriori informazioni, consultare la documentazione di installazione di Vernice.

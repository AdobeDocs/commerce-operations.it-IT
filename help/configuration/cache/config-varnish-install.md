---
title: Installa vernice
description: Consulta i consigli sull’installazione di Varnish.
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '165'
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

Di seguito è riportato un esempio:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Assicurati che la versione sia 6.x prima di continuare. Se utilizzi una versione precedente alla 6.x, devi passare a una versione supportata. Per ulteriori informazioni, consultare la documentazione di installazione di Vernice.

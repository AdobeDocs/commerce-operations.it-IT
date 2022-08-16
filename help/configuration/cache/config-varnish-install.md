---
title: Installa Varnish
description: Consulta i consigli sull'installazione di Varnish.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Installa Varnish

L&#39;installazione del software Vernish va oltre lo scopo di questa guida. Per ulteriori informazioni sull&#39;installazione di Varnish, vedi:

- [guida all&#39;installazione](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guide all&#39;installazione in vernice](https://www.varnish-cache.org/docs)
- [Come installare Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Questo argomento è scritto per Vernish su CentOS e Apache 2.4. Se si sta impostando Varnish in un ambiente diverso, alcuni comandi sono probabilmente diversi. Per ulteriori informazioni, consulta la documentazione precedente.
>
>Se si intende installare i moduli Varnish (vmods), ad esempio la modalità saint, è necessario installare Varnish compilando il codice anziché installandolo da un pacchetto. Vedi [Modalità Saint](config-varnish-advanced.md#saint-mode) per ulteriori dettagli.

## Conferma la versione verniciata

Apri un terminale e immetti il seguente comando per visualizzare la versione di Varnish:

```bash
varnishd -V
```

Segue un esempio:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Assicurati che la versione sia 6.x prima di continuare. Se esegui una versione inferiore a 6.x, devi effettuare l’aggiornamento a una versione supportata. Per ulteriori informazioni, consulta la documentazione di installazione di Varnish .
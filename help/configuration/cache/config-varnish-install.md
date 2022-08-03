---
title: Installa Varnish
description: Consulta i consigli sull'installazione di Varnish.
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Installa Varnish

L&#39;installazione del software Vernish va oltre lo scopo di questa guida. Per ulteriori informazioni sull&#39;installazione di Varnish, vedi:

- [wiki di installazione](http://wiki.mikejung.biz/Varnish)
- [Guide all&#39;installazione in vernice](https://www.varnish-cache.org/docs)
- [Come installare Varnish (Tecmint)](http://www.tecmint.com/install-varnish-cache-web-accelerator)

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

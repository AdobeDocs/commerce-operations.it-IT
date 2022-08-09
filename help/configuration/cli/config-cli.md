---
title: Strumento da riga di comando
description: Utilizzare lo strumento della riga di comando Commerce per eseguire attività di installazione e configurazione.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Strumento da riga di comando

Commerce dispone di un’interfaccia a riga di comando (CLI) —`<magento_root>/bin/magento`- che esegue attività di installazione e configurazione, tra cui:

- Installazione di Commerce (e delle attività correlate, ad esempio l’aggiornamento dello schema del database, creazione di una configurazione di distribuzione)
- Cancellazione della cache
- Gestione degli indici, inclusa la reindicizzazione
- Creazione di dizionari di traduzione e pacchetti di traduzione
- Generazione di classi inesistenti, ad esempio fabbriche e intercettori per i plug-in, generando la configurazione dell&#39;iniezione di dipendenza per il gestore oggetti
- Distribuzione di file di visualizzazione statici
- Creazione di CSS da meno

Ulteriori vantaggi includono:

- Un singolo comando (`<magento_root>/bin/magento list`) elenca tutti i comandi di installazione e configurazione disponibili.
- Interfaccia utente coerente basata su Symfony.
- La CLI è estensibile in modo che gli sviluppatori di terze parti possano &quot;plug-in&quot; ad essa. Questo ha il vantaggio aggiuntivo di eliminare la curva di apprendimento degli utenti.
- I comandi per i moduli disabilitati non vengono visualizzati.

Questo argomento illustra la configurazione del software Adobe Commerce e Magenti Open Source tramite CLI. Per informazioni sull’installazione di Commerce, consulta [Flusso di installazione](https://devdocs.magento.com/guides/v2.4/install-gde/install-flow-diagram.html) in _Guida all’installazione_.

## Prerequisiti

Prima di iniziare a utilizzare CLI, assicurati che:

1. Il sistema soddisfa i requisiti descritti in [Requisiti di sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) in _Guida all’installazione_.
1. Hai completato tutte le attività preliminari descritte in [Prerequisiti](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) in _Guida all’installazione_.
1. Dopo aver effettuato l’accesso al server Commerce, passa a un utente con autorizzazioni di scrittura nel file system Commerce. Vedi [passa al proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) in _Guida all’installazione_.

## Esecuzione dei comandi

Per la shell bash, utilizza la sintassi seguente per passare al proprietario del file system e immettere il comando contemporaneamente:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Se il proprietario del file system non consente l&#39;accesso, è possibile utilizzare quanto segue:

```bash
sudo -u <file system owner> <command>
```

**Per eseguire i comandi CLI da qualsiasi directory**:

Aggiungi `<magento_root>/bin` al sistema `PATH`.

shell di base di esempio per CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Facoltativamente, puoi eseguire quanto segue:

- `cd <magento_root>/bin` e eseguili come `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` è una sottodirectory del docroot del server web

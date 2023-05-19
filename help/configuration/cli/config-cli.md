---
title: Strumento da riga di comando
description: Utilizza lo strumento da riga di comando di Commerce per eseguire le attività di installazione e configurazione.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Strumento da riga di comando

Commerce dispone di un&#39;unica interfaccia della riga di comando (CLI):`<magento_root>/bin/magento`: esegue attività di installazione e configurazione, tra cui:

- Installazione di Commerce (e delle attività correlate, come l’aggiornamento dello schema del database, creare una configurazione di distribuzione)
- Cancellazione della cache
- Gestione degli indici, inclusa la reindicizzazione
- Creazione di dizionari di traduzione e pacchetti di traduzione
- Generazione di classi inesistenti, ad esempio factory e intercettori per i plug-in, che generano la configurazione dell&#39;iniezione di dipendenza per il gestore di oggetti
- Distribuzione di file di visualizzazione statica
- Creazione di CSS da meno

Ulteriori vantaggi includono:

- Un singolo comando (`<magento_root>/bin/magento list`) elenca tutti i comandi di installazione e configurazione disponibili.
- Interfaccia utente coerente basata su Symfony.
- La CLI è estensibile in modo che sviluppatori di terze parti possano collegarla. Questo ha il vantaggio aggiuntivo di eliminare la curva di apprendimento degli utenti.
- I comandi per i moduli disattivati non vengono visualizzati.

In questo argomento viene illustrata la configurazione di Adobe Commerce e del software di Magento Open Source utilizzando CLI. Per informazioni sull’installazione di Commerce, consulta [Flusso di installazione](../../installation/overview.md) nel _Guida all’installazione_.

## Prerequisiti

Prima di iniziare a utilizzare CLI, verificare che:

1. Il sistema soddisfa i requisiti descritti in [Requisiti di sistema](../../installation/system-requirements.md) nel _Guida all’installazione_.
1. Hai completato tutte le attività preliminari descritte in [Prerequisiti](../../installation/prerequisites/overview.md) nel _Guida all’installazione_.
1. Dopo aver effettuato l’accesso al server Commerce, passa a un utente che dispone delle autorizzazioni di scrittura per il file system Commerce. Consulta [passa al proprietario del file system](../../installation/prerequisites/file-system/overview.md) nel _Guida all’installazione_.

## Esecuzione dei comandi

Per la shell Bash, utilizzare la sintassi seguente per passare al proprietario del file system e immettere contemporaneamente il comando:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Se il proprietario del file system non consente l&#39;accesso, è possibile utilizzare quanto segue:

```bash
sudo -u <file system owner> <command>
```

**Per eseguire comandi CLI da qualsiasi directory**:

Aggiungi `<magento_root>/bin` al sistema `PATH`.

Shell di base di esempio per CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Facoltativamente, è possibile eseguire le operazioni seguenti:

- `cd <magento_root>/bin` ed eseguirli come `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` è una sottodirectory della directory principale dei documenti del server web

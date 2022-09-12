---
title: Imposta una maschera (facoltativo)
description: Migliora la postura di sicurezza dell’installazione on-premise di Adobe Commerce o Magento Open Source limitando le autorizzazioni del file system.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Imposta una maschera (facoltativo)

Il gruppo di server web deve disporre di autorizzazioni di scrittura per determinate directory nel file system; tuttavia, si potrebbe desiderare una maggiore sicurezza, soprattutto nella produzione. Offriamo la flessibilità di limitare ulteriormente tali autorizzazioni utilizzando un [umulo](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

La nostra soluzione è quella di consentirti facoltativamente di creare un file denominato `magento_umask` nella directory radice dell&#39;applicazione che limita le autorizzazioni per il gruppo di server web e per tutti gli altri.

>[!NOTE]
>
>Consigliamo di modificare il umask solo su un utente singolo o su un sistema di hosting condiviso. Se si dispone di un server applicazioni privato, il gruppo deve avere accesso in scrittura al file system; la umask rimuove l&#39;accesso in scrittura dal gruppo.

Maschera predefinita (senza `magento_umask` specificato) `002`, che significa:

* 775 per le directory, che significa il pieno controllo da parte dell&#39;utente, il pieno controllo da parte del gruppo, e permette a tutti di attraversare la directory. Queste autorizzazioni sono in genere richieste dai provider di hosting condivisi.

* 664 per i file, che significa scrivibile dall&#39;utente, scrivibile dal gruppo, e di sola lettura per tutti gli altri

Un suggerimento comune è quello di utilizzare un valore di `022` in `magento_umask` file, il che significa:

* 755 per le directory: controllo completo per l&#39;utente e tutti gli altri possono scorrere le directory.
* 644 per i file: autorizzazioni di lettura e scrittura per l&#39;utente e di sola lettura per tutti gli altri.

Per impostare `magento_umask`:

1. In un terminale della riga di comando, accedi al server delle applicazioni come [proprietario del file system](../prerequisites/file-system/overview.md).
1. Passa alla directory di installazione dell&#39;applicazione:

   ```bash
   cd <Application install directory>
   ```

1. Utilizzare il comando seguente per creare un file denominato `magento_umask` e scrivi `umask` valore per esso.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Ora dovresti avere un file denominato `magento_umask` in `<Magento install dir>` il cui unico contenuto è il `umask` numero.

1. Disconnettiti e accedi nuovamente come [proprietario del file system](../prerequisites/file-system/overview.md) per applicare le modifiche.

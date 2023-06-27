---
title: Impostare una maschera (facoltativo)
description: Migliora la postura di sicurezza dell’installazione on-premise di Adobe Commerce o di Magento Open Source limitando le autorizzazioni del file system.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Impostare una maschera (facoltativo)

Il gruppo di server web deve disporre di autorizzazioni di scrittura per determinate directory nel file system; tuttavia, potrebbe essere necessario un livello di protezione più elevato, soprattutto in produzione. Dell offre la flessibilità necessaria per limitare ulteriormente tali autorizzazioni utilizzando un [maschera](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

La nostra soluzione consiste nel creare un file denominato `magento_umask` nella directory principale dell&#39;applicazione che limita le autorizzazioni per il gruppo di server web e tutti gli altri.

>[!NOTE]
>
>È consigliabile modificare l’umask solo su un sistema di hosting condiviso o con un solo utente. Se si dispone di un server applicazioni privato, è necessario che il gruppo disponga dell&#39;accesso in scrittura al file system; l&#39;umask rimuove l&#39;accesso in scrittura dal gruppo.

La maschera predefinita (senza `magento_umask` specificato) è `002`, ossia:

* 775 per le directory, il che significa il controllo completo da parte dell’utente, il controllo completo da parte del gruppo e consente a tutti di attraversare la directory. Queste autorizzazioni sono in genere richieste dai provider di hosting condivisi.

* 664 per i file, ovvero scrivibile dall&#39;utente, scrivibile dal gruppo e di sola lettura per tutti gli altri

Un suggerimento comune è quello di utilizzare un valore di `022` nel `magento_umask` file, ovvero:

* 755 per le directory: pieno controllo per l’utente e tutti gli altri utenti possono attraversare le directory.
* 644 per i file: autorizzazioni di lettura-scrittura per l’utente e di sola lettura per tutti gli altri utenti.

Per impostare `magento_umask`:

1. In un terminale della riga di comando, accedere al server applicazioni come [proprietario del file system](../prerequisites/file-system/overview.md).
1. Passare alla directory di installazione dell&#39;applicazione:

   ```bash
   cd <Application install directory>
   ```

1. Utilizza il seguente comando per creare un file denominato `magento_umask` e scrivi il `umask` valore.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Ora dovresti avere un file denominato `magento_umask` nel `<Magento install dir>` con l&#39;unico contenuto che è il `umask` numero.

1. Esci e accedi di nuovo come [proprietario del file system](../prerequisites/file-system/overview.md) per applicare le modifiche.

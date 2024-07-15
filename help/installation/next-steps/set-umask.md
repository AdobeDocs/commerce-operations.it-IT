---
title: Impostare una maschera (facoltativo)
description: Migliora la postura di sicurezza dell’installazione on-premise di Adobe Commerce limitando le autorizzazioni del file system.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Impostare una maschera (facoltativo)

Il gruppo di server web deve disporre di autorizzazioni di scrittura per determinate directory nel file system; tuttavia, potrebbe essere necessario un livello di protezione più elevato, soprattutto in produzione. Ti offriamo la flessibilità di limitare ulteriormente tali autorizzazioni utilizzando una [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

La nostra soluzione consiste nel consentire la creazione facoltativa di un file denominato `magento_umask` nella directory principale dell&#39;applicazione che limita le autorizzazioni per il gruppo di server Web e tutti gli altri utenti.

>[!NOTE]
>
>È consigliabile modificare l’umask solo su un sistema di hosting condiviso o con un solo utente. Se si dispone di un server applicazioni privato, è necessario che il gruppo disponga dell&#39;accesso in scrittura al file system; l&#39;umask rimuove l&#39;accesso in scrittura dal gruppo.

L&#39;umask predefinita (senza `magento_umask` specificato) è `002`, ovvero:

* 775 per le directory, il che significa il controllo completo da parte dell’utente, il controllo completo da parte del gruppo e consente a tutti di attraversare la directory. Queste autorizzazioni sono in genere richieste dai provider di hosting condivisi.

* 664 per i file, ovvero scrivibile dall&#39;utente, scrivibile dal gruppo e di sola lettura per tutti gli altri

Si consiglia di utilizzare un valore di `022` nel file `magento_umask`, ovvero:

* 755 per le directory: pieno controllo per l’utente e tutti gli altri utenti possono attraversare le directory.
* 644 per i file: autorizzazioni di lettura-scrittura per l’utente e di sola lettura per tutti gli altri utenti.

Per impostare `magento_umask`:

1. In un terminale della riga di comando, accedi al server applicazioni come [proprietario del file system](../prerequisites/file-system/overview.md).
1. Passare alla directory di installazione dell&#39;applicazione:

   ```bash
   cd <Application install directory>
   ```

1. Utilizzare il comando seguente per creare un file denominato `magento_umask` e scrivervi il valore `umask`.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   In `<Magento install dir>` dovrebbe essere presente un file denominato `magento_umask` con l&#39;unico contenuto il numero `umask`.

1. Esci e accedi di nuovo come [proprietario del file system](../prerequisites/file-system/overview.md) per applicare le modifiche.

---
title: Proprietà e autorizzazioni dei file
description: Scopri l’importanza delle autorizzazioni del file system quando si lavora con le installazioni locali di Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Proprietà e autorizzazioni dei file

È importante proteggere l’installazione di Adobe Commerce o Magento Open Source in un ambiente di sviluppo per evitare problemi relativi all’accesso a persone o processi non autorizzati e potenzialmente dannosi per il sistema. Per proteggere l&#39;installazione, utilizzare le seguenti linee guida relative alla proprietà e alle autorizzazioni del file system.

## Proprietario del file system

Il proprietario del file system è un utente che possiede e detiene le autorizzazioni di scrittura per i file nel file system.

Esistono due tipi di proprietari del file system:

- **Hosting condiviso con un singolo utente**

   I provider di hosting condivisi consentono di accedere al server applicazioni come un unico utente. In qualità di singolo utente, puoi accedere, trasferire file tramite FTP ed eseguire il server web. È possibile impostare un [`umask`](#restrict-access-with-a-umask) limitare ulteriormente l&#39;accesso, in particolare in un ambiente produttivo.

- **Hosting privato con due utenti**

   L&#39;hosting privato è utile se gestisci un server applicativo. Ogni utente ha una responsabilità specifica:

   - La _utente web server_ esegue Admin e storefront.

   - La _utente della riga di comando_ esegue i lavori cron e le utilità della riga di comando.
   Entrambi gli utenti richiedono le stesse autorizzazioni al file system, quindi è consigliabile utilizzare un [gruppo condiviso](configure-permissions.md#set-ownership-and-permissions-for-two-users) e imposta un [`umask`](#restrict-access-with-a-umask).

### Limitare l&#39;accesso con una maschera

Per rafforzare la sicurezza, in particolare in un ambiente di produzione su un sistema di hosting condiviso, puoi utilizzare `umask` limitare l&#39;accesso. A `umask`—anche definiti come _maschera di creazione file system_- è un set di bit che controlla come vengono impostate le autorizzazioni del file per i file appena creati.

>[!WARNING]
>
>La sicurezza del file system è complessa e importante. È consigliabile consultare un amministratore di sistema o un amministratore di rete esperto prima di decidere il livello di autorizzazioni da impostare. Forniamo un meccanismo da utilizzare, ma la creazione di una strategia di autorizzazione è responsabilità tua.

Adobe Commerce e Magenti Open Source utilizzano una maschera predefinita a tre bit: `002`. Sottrae la maschera predefinita dalle impostazioni predefinite UNIX di 666 per i file e 777 per le directory.

Ad esempio:

- **775 per le directory**- Controllo completo da parte dell&#39;utente, controllo completo da parte del gruppo e consente a tutti di attraversare la directory. Queste autorizzazioni sono in genere richieste dai provider di hosting condivisi.

- **664 per i file**- Scritto dall&#39;utente, scrivibile dal gruppo e di sola lettura per tutti gli altri.

Per ulteriori informazioni sulla creazione di un `magento_umask` file, vedi [Imposta una maschera](../../next-steps/set-umask.md).

## Autorizzazioni, proprietà e modalità di applicazione

Consigliamo autorizzazioni e proprietà diverse quando utilizzi diverse modalità di applicazione Adobe Commerce e Magenti Open Source:

- Predefinito
- Sviluppatore
- Produzione

Vedi [Informazioni sulle modalità](../../../configuration/bootstrap/application-modes.md) in _Guida alla configurazione_.

Discutiamo ulteriormente le raccomandazioni sulle autorizzazioni in [Autorizzazioni di accesso ai file system](../../../configuration/deployment/file-system-permissions.md) in _Guida alla configurazione_.

>[!TIP]
>
>Prima di installare Adobe Commerce o Magenti Open Source, rivedi [Configurare la proprietà e le autorizzazioni dei file](configure-permissions.md).

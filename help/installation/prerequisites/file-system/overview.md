---
title: Proprietà e autorizzazioni dei file
description: Scopri l’importanza delle autorizzazioni per il file system quando utilizzi le installazioni locali di Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Proprietà e autorizzazioni dei file

È importante proteggere l’installazione di Adobe Commerce in un ambiente di sviluppo per evitare problemi relativi a persone o processi non autorizzati che accedono al sistema e potrebbero danneggiarlo. Per proteggere l&#39;installazione, utilizzare le seguenti linee guida relative alla proprietà e alle autorizzazioni del file system.

## Proprietario file system

Il proprietario del file system è un utente che possiede e detiene le autorizzazioni di scrittura per i file nel file system.

Esistono due tipi di proprietari del file system:

- **Hosting condiviso con un singolo utente**

  I provider di hosting condivisi consentono di accedere al server applicazioni come un unico utente. In qualità di utente singolo, puoi accedere, trasferire file tramite FTP ed eseguire il server web. È possibile impostare un valore [`umask`](#restrict-access-with-a-umask) limitare ulteriormente l’accesso, in particolare in un ambiente di produzione.

- **Hosting privato con due utenti**

  L&#39;hosting privato è utile se gestisci un server applicazioni. Ogni utente ha una responsabilità specifica:

   - Il _utente server web_ esegue l’amministratore e la vetrina.

   - Il _utente della riga di comando_ esegue processi cron e utilità della riga di comando.

  Entrambi gli utenti richiedono le stesse autorizzazioni per il file system, pertanto è consigliabile utilizzare un [gruppo condiviso](configure-permissions.md#set-ownership-and-permissions-for-two-users) e imposta un [`umask`](#restrict-access-with-a-umask).

### Limitare l’accesso con una maschera

Per rafforzare la sicurezza, in particolare in un ambiente di produzione su un sistema di hosting condiviso, puoi utilizzare `umask` per limitare l&#39;accesso. A `umask`—denominati anche _maschera di creazione file system_- è un insieme di bit che controlla il modo in cui vengono impostate le autorizzazioni per i file appena creati.

>[!WARNING]
>
>La sicurezza del file system è complessa e importante. È consigliabile consultare un amministratore di sistema o un amministratore di rete esperto prima di decidere il livello di autorizzazioni da impostare. Ti forniamo un meccanismo da utilizzare, ma la creazione di una strategia di autorizzazioni è responsabilità tua.

Adobe Commerce utilizza una maschera predefinita a tre bit: `002`. Sottrarre la maschera di default dai valori di default UNIX 666 per i file e 777 per le directory.

Ad esempio:

- **775 per directory**- Controllo completo da parte dell&#39;utente, controllo completo da parte del gruppo e possibilità per tutti di attraversare la directory. Queste autorizzazioni sono in genere richieste dai provider di hosting condivisi.

- **664 per file**: scrivibile dall&#39;utente, scrivibile dal gruppo e di sola lettura per tutti gli altri.

Per ulteriori informazioni sulla creazione di un’ `magento_umask` file, vedi [Imposta una maschera](../../next-steps/set-umask.md).

## Autorizzazioni, proprietà e modalità di applicazione

Quando utilizzi le diverse modalità dell’applicazione Adobe Commerce, consigliamo di utilizzare autorizzazioni e proprietà diverse:

- Predefinito
- Sviluppatore
- Produzione

Consulta [Informazioni sulle modalità](../../../configuration/bootstrap/application-modes.md) nel _Guida alla configurazione_.

Vengono ulteriormente discusse le raccomandazioni sulle autorizzazioni in [Autorizzazioni di accesso ai file system](../../../configuration/deployment/file-system-permissions.md) nel _Guida alla configurazione_.

>[!TIP]
>
>Prima di installare Adobe Commerce, controlla [Configurare la proprietà e le autorizzazioni dei file](configure-permissions.md).

---
title: Software opzionale
description: Ulteriori informazioni sui software opzionali che è possibile installare per supportare le installazioni locali di Adobe Commerce.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Software opzionale

Si consiglia vivamente di installare NTP per garantire che le attività correlate a cron funzionino correttamente. Ad esempio, le date del server potrebbero essere nel passato o nel futuro.

Le altre utilità facoltative illustrate in questo argomento possono essere utili per l&#39;installazione, ma non sono necessarie per installare o utilizzare Adobe Commerce.

## Installazione e configurazione di Network Time Protocol (NTP)

[NTP](https://www.ntp.org/) consente ai server di sincronizzare gli orologi di sistema utilizzando [server pool disponibili a livello globale](https://www.ntppool.org/en/). Si consiglia di utilizzare i server NTP considerati attendibili, siano essi soluzioni hardware dedicate della rete interna o server pubblici esterni.

Se distribuisci Adobe Commerce su più host, NTP è un modo semplice per garantire che i loro orologi siano tutti sincronizzati, indipendentemente dal fuso orario in cui si trovano i server. Inoltre, le attività relative alle cron (come l’indicizzazione e le e-mail transazionali) dipendono dall’accuratezza dell’orologio del server.

### Installare e configurare NTP su Ubuntu

Immettere il comando seguente per installare NTP:

```bash
apt-get install ntp
```

Continua con [Utilizzare i server pool NTP](#use-ntp-pool-servers).

### Installare e configurare NTP su CentOS

Per installare e configurare NTP:

1. Immettere il seguente comando per trovare il software NTP appropriato:

   ```bash
   yum search ntp
   ```

1. Seleziona un pacchetto da installare. Ad esempio: `ntp.x86_64`.

1. Installa il pacchetto.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Immettere il comando seguente in modo che NTP venga avviato all&#39;avvio del server.

   ```bash
   chkconfig ntpd on
   ```

1. Procedi alla sezione successiva.

### Utilizzare i server pool NTP

La selezione dei server del pool dipende dall&#39;utente. Se si utilizzano server pool NTP, ntp.org consiglia di utilizzare [server di pool](https://www.ntppool.org/en/) che sono vicini al fuso orario dei server, come descritto nel [Pagina progetto pool NTP](https://www.ntppool.org/en/use.html). Se si dispone di un server NTP privato disponibile per tutti gli host della distribuzione, è possibile utilizzare tale server.

1. Apri `/etc/ntp.conf` in un editor di testo.

1. Cerca righe simili alle seguenti:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Sostituire tali righe o aggiungere altre righe che specifichino il server del pool NTP o altri server NTP. È consigliabile specificarne più di uno.

1. Di seguito è riportato un esempio di utilizzo di tre server NTP basati negli Stati Uniti:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Salva le modifiche apportate a `/etc/ntp.conf` ed esci dall’editor di testo.

1. Riavviare il servizio.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Invio `date` per controllare la data del server.

   Se la data non è corretta, accertati che la porta client NTP (in genere, UDP 123) sia aperta nel firewall.

   Prova la `ntpdate _[pool server hostname]_` comando. In caso di esito negativo, cercare l&#39;errore restituito.

   In caso contrario, provare a riavviare il server.

## Creare phpinfo.php

Il [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) file visualizza una grande quantità di informazioni su PHP e le sue estensioni.

>[!NOTE]
>
>Utilizzare `phpinfo.php` in un sistema di sviluppo _solo_. Può essere un problema di sicurezza in produzione.

Aggiungi il seguente codice in qualsiasi punto della directory principale dei documenti del server web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Per ulteriori informazioni, vedere [pagina manuale phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Per visualizzare i risultati, immetti il seguente URL nel campo posizione o indirizzo del browser:

```http
http://<web server host or IP>/phpinfo.php
```

Se viene visualizzato un errore 404 (Non trovato), verificare quanto segue:

* Avvia il server web, se necessario.
* Verificare che il firewall consenta il traffico sulla porta 80.

  [Aiuto per Ubuntu](https://help.ubuntu.com/community/UFW)

  [Guida di CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

L&#39;applicazione phpMyAdmin è un&#39;utilità di amministrazione del database facile da usare e gratuita. È possibile utilizzarlo per controllare e modificare il contenuto del database. È necessario accedere a phpMyAdmin come utente amministrativo del database MySQL.

Per ulteriori informazioni su phpMyAdmin, vedere [home page phpMyAdmin](https://www.phpmyadmin.net/).

Per informazioni più dettagliate sull&#39;installazione, vedere [documentazione sull&#39;installazione di phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Utilizzare phpMyAdmin in un sistema di sviluppo _solo_. Può essere un problema di sicurezza in produzione.

1. Per usare phpMyAdmin, immetti il seguente comando nel campo indirizzo o percorso del browser:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Quando richiesto, accedere utilizzando il database MySQL `root` o il nome utente e la password dell&#39;utente amministratore.

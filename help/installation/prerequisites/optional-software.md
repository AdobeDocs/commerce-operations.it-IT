---
title: Software opzionale
description: Ulteriori informazioni sul software opzionale che è possibile installare per supportare le installazioni on-premise di Adobe Commerce e Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# Software opzionale

Si consiglia vivamente di installare NTP per garantire che le attività relative al cron funzionino correttamente. (Ad esempio, le date del server potrebbero essere passate o future).

Le altre utilità facoltative discusse in questo argomento potrebbero aiutarti con l&#39;installazione; tuttavia, non è necessario installare o utilizzare Adobe Commerce o Magenti Open Source.

## Installazione e configurazione del protocollo NTP (Network Time Protocol)

[NTP](https://www.ntp.org/) consente ai server di sincronizzare i blocchi di sistema utilizzando [server pool disponibili a livello globale](https://www.ntppool.org/en/). Si consiglia di utilizzare i server NTP considerati attendibili, siano essi soluzioni hardware dedicate alla rete interna o server pubblici esterni.

Se distribuisci Adobe Commerce o Magento Open Source su più host, NTP è un modo semplice per garantire che i loro orologi siano tutti sincronizzati, indipendentemente dal fuso orario in cui si trovano i server. Inoltre, le attività relative ai cron (come l’indicizzazione e le e-mail transazionali) dipendono dall’accuratezza dell’orologio server.

### Installa e configura NTP su Ubuntu

Immettere il seguente comando per installare NTP:

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

1. Seleziona un pacchetto da installare. Ad esempio, `ntp.x86_64`.

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

La selezione dei server pool dipende da te. Se utilizzi server pool NTP, ntp.org consiglia di utilizzare [server pool](https://www.ntppool.org/en/) vicini al fuso orario dei server, come descritto in [Pagina del progetto del pool NTP](https://www.ntppool.org/en/use.html). Se disponi di un server NTP privato disponibile per tutti gli host nella distribuzione, puoi utilizzare tale server.

1. Apri `/etc/ntp.conf` in un editor di testo.

1. Cerca righe simili alle seguenti:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Sostituisci queste righe o aggiungi altre righe che specificano il server del pool NTP o altri server NTP. È una buona idea specificare più di uno.

1. Un esempio di utilizzo di tre server NTP basati negli Stati Uniti:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Salva le modifiche in `/etc/ntp.conf` e esci dall’editor di testo.

1. Riavvia il servizio.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Invio `date` per controllare la data del server.

   Se la data non è corretta, assicurarsi che la porta client NTP (in genere UDP 123) sia aperta nel firewall.

   Prova la `ntpdate _[pool server hostname]_` comando. Se non riesce, cerca l&#39;errore che restituisce.

   Se tutto il resto non riesce, prova a riavviare il server.

## Crea phpinfo.php

La [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) visualizza una grande quantità di informazioni [PHP](https://glossary.magento.com/php) e le sue estensioni.

>[!NOTE]
>
>Utilizzo `phpinfo.php` in un sistema di sviluppo _only_. Può essere un problema di sicurezza nella produzione.

Aggiungi il seguente codice in qualsiasi punto del docroot del server web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Per ulteriori informazioni, consulta la sezione [pagina manuale phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Per visualizzare i risultati, immettere quanto segue [URL](https://glossary.magento.com/url) nel campo posizione o indirizzo del browser:

```http
http://<web server host or IP>/phpinfo.php
```

Se viene visualizzato un errore 404 (Non trovato), controlla quanto segue:

* Se necessario, avvia il server web.
* Assicurati che il firewall consenta il traffico sulla porta 80.

   [Aiuto per Ubuntu](https://help.ubuntu.com/community/UFW)

   [Aiuto per CentOS](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

L&#39;applicazione phpMyAdmin è un&#39;utilità di amministrazione gratuita del database facile da usare. Puoi utilizzarlo per controllare e manipolare il contenuto del database. È necessario accedere a phpMyAdmin come utente amministrativo del database MySQL.

Per ulteriori informazioni su phpMyAdmin, consulta la sezione [home page di phpMyAdmin](https://www.phpmyadmin.net/).

Per informazioni più dettagliate sull&#39;installazione, consulta la sezione [Documentazione di installazione di phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Utilizzare phpMyAdmin in un sistema di sviluppo _only_. Può essere un problema di sicurezza nella produzione.

1. Per utilizzare phpMyAdmin, immetti il seguente comando nel campo indirizzo o posizione del browser:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Quando richiesto, effettuare l&#39;accesso utilizzando il database MySQL `root` nome utente e password dell&#39;utente amministrativo.

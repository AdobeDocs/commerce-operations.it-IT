---
title: Configurare l’applicazione
description: Scopri la configurazione post-installazione richiesta per le distribuzioni locali Adobe Commerce e Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Configurare l’applicazione

Dopo aver completato l’installazione di Adobe Commerce o del Magento Open Source, devi configurarlo. Questo argomento fornisce alcune impostazioni di configurazione consigliate.

## Imposta cron

Lo scheduler attività UNIX, cron, è fondamentale per le operazioni quotidiane dell&#39;applicazione. Pianifica cose come reindicizzazione, newsletter, e-mail e sitemap. A *crontab* è una configurazione cron.

È necessario installare Adobe Commerce e i servizi Magenti Open Source nel *crontab*, oppure alcune funzionalità di base (e alcune estensioni di terze parti) non funzionano correttamente.

Per ulteriori informazioni su cron, tra cui come rimuovere un crontab ed eseguire cron dalla riga di comando, vedi [Configurare ed eseguire cron](../../configuration/cli/configure-cron-jobs.md).

## Impostazioni di sicurezza e raccomandazioni

Dopo l’installazione, si consiglia quanto segue:

* Assicurati che la proprietà e le autorizzazioni del file siano impostate correttamente
* Consigliamo vivamente [modifica dell’URI amministratore predefinito](../tutorials/admin-uri.md) da `admin` a qualcos&#39;altro
* Assicurati che [`X-Frame-Option` Intestazione HTTP](../../configuration/security/xframe-options.md) è impostato correttamente.
* Precauzioni relative agli script tra siti diversi (XSS) [protezione dei modelli](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Se è stato installato da [clonazione dell’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), accertati di includere solo i file e le cartelle necessari per l&#39;ambiente di produzione quando distribuisci l&#39;applicazione. I file e le cartelle non necessari possono potenzialmente esporre rischi per la sicurezza.

## Abilita riscrittura del server Apache

Se si utilizza il server web Apache, è necessario abilitare le riscritture del server affinché le pagine vengano visualizzate correttamente. In caso contrario, verranno visualizzate pagine senza stili e altri problemi.

[Sezione sulle riscritture del server Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Memorizzazione in cache in un ambiente a più nodi web

Se hai più nodi web, *impossibile* utilizza la memorizzazione in cache dei file predefinita dell&#39;applicazione perché non esiste alcuna sincronizzazione tra i nodi web. In altre parole, l&#39;attività su un nodo web viene scritta solo nel file system di quel nodo web. L’attività successiva, se eseguita su un altro nodo web, può causare la scrittura di file non necessari o causare errori.

Invece, utilizza [Redis](../../configuration/cache/config-redis.md) sia per la cache predefinita che per la cache della pagina.

## Impostazioni server

Questa sezione descrive brevemente le impostazioni che si consiglia di considerare per il server su cui viene eseguita l&#39;applicazione. Alcune di queste impostazioni non sono direttamente correlate all&#39;applicazione; sono forniti solo come suggerimenti.

### Rotazione del registro

UNIX `logrotate` Utility consente di amministrare i sistemi che generano un gran numero di file di log. Consente la rotazione automatica, la compressione, la rimozione e l&#39;invio di file di log. Ogni file di registro può essere gestito quotidianamente, settimanalmente, mensilmente o quando il file di registro supera una dimensione specificata.

Per ulteriori informazioni, consulta uno dei seguenti argomenti:

* [Procedura: Esercitazione del comando di rotazione del registro finale con dieci esempi](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` pagina man](https://linuxconfig.org/logrotate-8-manual-page)

### Imposta le regole di iptables per consentire a vari servizi di comunicare

Se si dispone di uno o più server, è necessario aprire le porte nel firewall per consentire ai servizi di comunicare. Ad esempio, se utilizzi il motore di ricerca Solr con Adobe Commerce, devi abilitarlo per comunicare con il server web. Se si dispone di più nodi web, è necessario attivarli per comunicare tra loro.

Ulteriori informazioni:

* Ubuntu: [Pagina della documentazione di Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Procedura dettagliata per CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

### Regole di sicurezza Enhanced Linux (SELinux)

Non abbiamo una raccomandazione per sapere se utilizzi SELinux; tuttavia, se lo utilizzi, devi configurare i servizi per comunicare tra loro in modo analogo alla configurazione di iptables.

Ulteriori informazioni:

* Ubuntu: [Manuale Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [Wiki CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurare un server di posta elettronica

Adobe Commerce e Magenti Open Source richiedono un server di posta elettronica. Non consigliamo un server particolare, ma puoi provare uno dei seguenti:

* Postfix per CentOS ([Esercitazione sull&#39;Oceano Digitale](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentazione di CentOS](https://www.centos.org))
* Postfix per Ubuntu ([Esercitazione sull&#39;Oceano Digitale](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentazione Ubuntu](https://help.ubuntu.com/community/MailServer))

### Ottimizzare il motore di ricerca per migliorare le prestazioni:

Elasticsearch o OpenSearch è richiesto per tutte le installazioni a partire dalla versione 2.4.0.

* [Installare e configurare il motore di ricerca](../../configuration/search/overview-search.md)

### Impostare una coda messaggi

A partire dalla versione 2.3.0, Adobe Commerce e Magenti Open Source includono funzionalità di coda dei messaggi. Nelle versioni precedenti, è disponibile solo per Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Impostazioni solo per Adobe Commerce

Puoi configurare quanto segue solo se utilizzi Adobe Commerce:

* [Dividi database per il pagamento, la gestione degli ordini e altre tabelle di database](../../configuration/storage/multi-master.md)

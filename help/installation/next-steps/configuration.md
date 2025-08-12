---
title: Configurare l’applicazione
description: Scopri la configurazione post-installazione richiesta per le distribuzioni Adobe Commerce on-premise.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a7c98879e027948fc887e28d4baa5fb04214ca95
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Configurare l’applicazione

Ora che hai completato l’installazione di Adobe Commerce, devi configurarlo. In questo argomento vengono fornite alcune impostazioni di configurazione consigliate.

## Configura cron

L&#39;utilità di pianificazione UNIX cron è fondamentale per le operazioni quotidiane dell&#39;applicazione. Pianifica elementi come reindicizzazione, newsletter, e-mail e sitemap. Una *crontab* è una configurazione cron.

È necessario installare i servizi Adobe Commerce in *crontab*, altrimenti alcune funzionalità di base (e alcune estensioni di terze parti) non funzioneranno correttamente.

Per ulteriori informazioni su cron, tra cui come rimuovere un crontab ed eseguire cron dalla riga di comando, vedere [Configurare ed eseguire cron](../../configuration/cli/configure-cron-jobs.md).

## Impostazioni di sicurezza e raccomandazioni

Dopo l&#39;installazione, si consiglia quanto segue:

* Assicurati che la proprietà e le autorizzazioni del file siano impostate [correttamente](../prerequisites/file-system/configure-permissions.md)
* È consigliabile [modificare l&#39;URI di amministrazione predefinito ](../tutorials/admin-uri.md) da `admin` a qualcos&#39;altro
* Verificare che l&#39;intestazione HTTP [`X-Frame-Option`](../../configuration/security/xframe-options.md) sia impostata correttamente.
* Prendi precauzioni contro il cross-site scripting (XSS) [proteggendo i modelli](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Se hai installato [clonando l&#39;archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), assicurati che quando distribuisci l&#39;applicazione includi solo i file e le cartelle necessari per l&#39;ambiente di produzione. I file e le cartelle che non sono necessari possono potenzialmente esporre rischi per la sicurezza.

## Abilita riscritture server Apache

Se utilizzi il server web Apache, devi abilitare le riscritture del server per la corretta visualizzazione delle pagine. In caso contrario, verranno visualizzate le pagine senza stili e altri problemi.

[La sezione sulle riscritture del server Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Memorizzazione in cache in un ambiente con più nodi Web

Se si dispone di più nodi Web, *non è possibile* utilizzare il file caching predefinito dell&#39;applicazione perché non esiste alcuna sincronizzazione tra i nodi Web. In altre parole, l’attività su un nodo web viene scritta solo nel file system di quel nodo web. L’attività successiva, se eseguita su un altro nodo web, può causare la scrittura di file non necessari o errori.

Utilizzare invece [Redis](../../configuration/cache/config-redis.md) sia per la cache predefinita che per la cache delle pagine.

## Impostazioni server

In questa sezione vengono illustrate brevemente le impostazioni che si consiglia di prendere in considerazione per il server in cui viene eseguita l&#39;applicazione. Alcune di queste impostazioni non sono direttamente correlate all’applicazione; vengono fornite solo come suggerimenti.

### Rotazione del registro

L&#39;utilità UNIX `logrotate` consente di amministrare sistemi che generano un numero elevato di file di log. Consente la rotazione, la compressione, la rimozione e l&#39;invio automatico di file di registro. Ogni file di registro può essere gestito quotidianamente, settimanalmente, mensilmente o quando supera una determinata dimensione.

Per ulteriori informazioni, consulta una delle seguenti sezioni:

* [Procedura: esercitazione del comando di rotazione del registro con dieci esempi](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* Pagina man [`logrotate`](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>Le seguenti informazioni sulla disponibilità si applicano ai progetti Adobe Commerce on Cloud Infrastructure:
>
>* Gli ambienti Starter non dispongono della rotazione del registro.
>
>* Non è possibile configurare la rotazione dei registri negli ambienti di integrazione Pro. Devi implementare una soluzione/script personalizzato e [configurare il cron](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) per eseguire lo script in base alle esigenze.

### Imposta le regole iptables per consentire a vari servizi di comunicare

Che si disponga di uno o più server, è necessario aprire le porte nel firewall per consentire ai servizi di comunicare. Ad esempio, se utilizzi il motore di ricerca Solr con Adobe Commerce, devi abilitarlo per comunicare con il server web. Se disponi di più nodi web, devi abilitarli per comunicare tra loro.

Ulteriori informazioni:

* Ubuntu: [Pagina documentazione Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [procedure CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Regole di sicurezza Enhanced Linux (SELinux)

Non si consiglia di utilizzare SELinux; tuttavia, se lo si utilizza, è necessario configurare i servizi per comunicare tra loro in modo simile alla configurazione di iptable.

Ulteriori informazioni:

* Ubuntu: [Manuale Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [wiki CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurare un server di posta elettronica

Adobe Commerce richiede un server di posta elettronica. Non è consigliabile utilizzare un server specifico, ma è possibile provare a eseguire una delle operazioni seguenti:

* suffisso per CentOS ([esercitazione Oceano digitale](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [documentazione CentOS](https://www.centos.org))
* Postfix per Ubuntu ([Esercitazione Oceano digitale](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentazione di Ubuntu](https://help.ubuntu.com/community/MailServer))

### Ottimizza le prestazioni del motore di ricerca:

Elasticsearch o OpenSearch sono necessari per tutte le installazioni a partire dalla versione 2.4.0.

* [Installare e configurare il motore di ricerca](../../configuration/search/overview-search.md)

### Configurare una coda di messaggi

A partire dalla versione 2.3.0, Adobe Commerce include le funzionalità della coda di messaggi. Nelle versioni precedenti, è disponibile solo per Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Impostazioni solo per Adobe Commerce

Puoi configurare quanto segue solo se utilizzi Adobe Commerce:

* [Dividere i database per l&#39;estrazione, la gestione degli ordini e altre tabelle di database](../../configuration/storage/multi-master.md)

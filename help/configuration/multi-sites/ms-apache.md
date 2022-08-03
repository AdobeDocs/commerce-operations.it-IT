---
title: Configurazione di più siti web con Apache
description: Segui questa esercitazione per configurare più siti web con Apache.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Configurazione di più siti web con Apache

Presupponiamo che:

Se necessario, copia il `index.php` script punto di ingresso per il sito web o [vista store](https://glossary.magento.com/store-view) e aggiungilo quanto segue:

- Si sta lavorando su una macchina di sviluppo (laptop, macchina virtuale e così via)

   Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente in hosting; per ulteriori informazioni, consulta il provider di hosting .

   Sono necessarie ulteriori attività per configurare Adobe Commerce sull’infrastruttura cloud. Dopo aver completato le attività discusse in questo argomento, vedi [Configurazione di più siti web o negozi](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in _Guida alla Commerce Cloud_.

- Si utilizza un host virtuale per sito Web; il file di configurazione dell&#39;host virtuale è `/etc/httpd/httpd.conf`

   Diverse versioni di Apache su diversi sistemi operativi configurano host virtuali in modo diverso. Consulta la [Documentazione di Apache](https://httpd.apache.org/docs/2.4/vhosts) o un amministratore di rete se non si è sicuri di come impostare un host virtuale.

- Il software Commerce è installato in `/var/www/html/magento2`
- Sono disponibili due siti web diversi da quelli predefiniti:

   - `french.mysite.mg` con codice del sito web `french` e memorizzare il codice della vista `fr`
   - `german.mysite.mg` con codice del sito web `german` e memorizzare il codice della vista `de`

## Roadmap per la configurazione di più siti web con Apache

L&#39;impostazione di più archivi consiste nelle seguenti attività:

1. [Configurare siti web, negozi e viste store](ms-admin.md) nell&#39;amministratore.
1. Crearne uno [Host virtuale Apache](#step-2-create-apache-virtual-hosts) per sito web Commerce.

## Passaggio 1: Crea siti web, store e visualizzazioni store nell’Admin

Vedi [Configurazione di più siti web, negozi e viste store nell’Admin](ms-admin.md).

## Passaggio 2: Creare host virtuali Apache

Questa sezione illustra come impostare i valori per `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` utilizzo della variabile server Apache `SetEnvIf` in un host virtuale.

Per ulteriori informazioni `SetEnvIf`, vedi:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Per creare host virtuali Apache**:

1. Come utente con `root` , apri il file di configurazione dell&#39;host virtuale in un editor di testo.

   Ad esempio, apri `/etc/httpd/conf/httpd.conf`

1. Individua la sezione che inizia con `<VirtualHost *:80>`.
1. Crea i seguenti host virtuali dopo eventuali host virtuali esistenti:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Salva le modifiche in `httpd.conf` e esci dall’editor di testo.
1. Riavvia Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Verificare il sito

A meno che il DNS non sia configurato per gli URL degli archivi, devi aggiungere un percorso statico all&#39;host nel tuo `hosts` file:

1. Individuare il sistema operativo `hosts` file.
1. Aggiungi il percorso statico nel formato:

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Vai a uno dei seguenti URL nel browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente in hosting; per ulteriori informazioni, consulta il provider di hosting .
>- Sono necessarie attività aggiuntive per configurare Adobe Commerce sull’infrastruttura cloud; vedere [Configurazione di più siti Web o negozi Cloud](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in _Guida alla Commerce Cloud_.


### Risoluzione dei problemi

- Se i siti francesi e tedeschi restituiscono 404 ma l&#39;amministratore carica, assicurati di aver completato il processo [Passaggio 6: Aggiungi il codice store all&#39;URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono 404 s, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, assicurati di configurare correttamente gli host virtuali.

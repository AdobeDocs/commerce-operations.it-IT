---
title: Configurare più siti web con Apache
description: Segui questa esercitazione per configurare più siti web con Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Configurare più siti web con Apache

Si presuppone che:

Se necessario, copia il file `index.php` script del punto di ingresso per la vista del sito web o store e aggiungi quanto segue:

- Stai lavorando su una macchina di sviluppo (laptop, macchina virtuale e così via)

   Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.

   Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce. Dopo aver completato le attività descritte in questo argomento, vedere [Configurazione di più siti Web o store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nel _Guida di Commerce su infrastruttura cloud_.

- Si utilizza un host virtuale per sito Web; il file di configurazione host virtuale è `/etc/httpd/httpd.conf`

   Diverse versioni di Apache su diversi sistemi operativi configurano gli host virtuali in modo diverso. Consulta la [Documentazione di Apache](https://httpd.apache.org/docs/2.4/vhosts) o un amministratore di rete se non si è sicuri della modalità di configurazione di un host virtuale.

- Il software Commerce è installato in `/var/www/html/magento2`
- Sono disponibili due siti Web diversi da quello predefinito:

   - `french.mysite.mg` con il codice del sito web `french` e memorizza il codice di visualizzazione `fr`
   - `german.mysite.mg` con il codice del sito web `german` e memorizza il codice di visualizzazione `de`

## Roadmap per la configurazione di più siti web con Apache

L&#39;impostazione di più archivi consiste nelle seguenti attività:

1. [Configurare siti Web, store e visualizzazioni dello store](ms-admin.md) in Admin.
1. Crea un elemento [Host virtuale Apache](#step-2-create-apache-virtual-hosts) per sito web Commerce.

## Passaggio 1: creare siti web, store e visualizzazioni dello store in Admin

Consulta [Configurare più siti web, store e visualizzazioni dello store in Admin](ms-admin.md).

## Passaggio 2: creare host virtuali Apache

Questa sezione illustra come impostare i valori per `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` utilizzo della variabile server Apache `SetEnvIf` in un host virtuale.

Per ulteriori informazioni su `SetEnvIf`, vedi:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Per creare host virtuali Apache**:

1. Come utente con `root` , aprire il file di configurazione host virtuale in un editor di testo.

   Ad esempio, apri `/etc/httpd/conf/httpd.conf`

1. Individua la sezione che inizia con `<VirtualHost *:80>`.
1. Crea i seguenti host virtuali dopo gli host virtuali esistenti:

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

1. Salva le modifiche apportate a `httpd.conf` ed esci dall’editor di testo.
1. Riavvia Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Verifica il sito

A meno che il DNS non sia configurato per gli URL dei tuoi archivi, devi aggiungere una route statica all&#39;host nel tuo `hosts` file:

1. Individuazione del sistema operativo `hosts` file.
1. Aggiungi la route statica nel formato:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Vai a uno dei seguenti URL nel browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.
>- Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce; consulta [Configurare più siti web o store Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nel _Guida di Commerce su infrastruttura cloud_.


### Risoluzione dei problemi

- Se i siti francese e tedesco restituiscono 404 secondi ma l’amministratore carica, assicurati di aver completato [Passaggio 6: aggiungi il codice dello store all’URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono il codice 404, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, verificare di aver configurato correttamente gli host virtuali.

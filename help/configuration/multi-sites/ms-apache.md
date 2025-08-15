---
title: Configurare più siti web con Apache
description: Segui questa esercitazione per configurare più siti web con Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Configurare più siti web con Apache

Si presuppone che:

Se necessario, copiare lo script del punto di ingresso `index.php` esistente per la visualizzazione del sito Web o dello store e aggiungervi quanto segue:

- Stai lavorando su una macchina di sviluppo (laptop, macchina virtuale e così via)

  Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.

  Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce. Dopo aver completato le attività descritte in questo argomento, vedere [Configurare più siti Web o store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nella _guida di Commerce sull&#39;infrastruttura cloud_.

- Si utilizza un host virtuale per sito Web; il file di configurazione dell&#39;host virtuale è `/etc/httpd/httpd.conf`

  Diverse versioni di Apache su diversi sistemi operativi configurano gli host virtuali in modo diverso. Se non sei sicuro di come configurare un host virtuale, consulta la [documentazione di Apache](https://httpd.apache.org/docs/2.4/vhosts) o un amministratore di rete.

- Software Commerce installato in `/var/www/html/magento2`
- Sono disponibili due siti Web diversi da quello predefinito:

   - `french.mysite.mg` con codice sito Web `french` e codice visualizzazione archivio `fr`
   - `german.mysite.mg` con codice sito Web `german` e codice visualizzazione archivio `de`

## Roadmap per la configurazione di più siti web con Apache

L&#39;impostazione di più archivi consiste nelle seguenti attività:

1. [Configura siti Web, archivi e visualizzazioni dello store](ms-admin.md) nell&#39;amministratore.
1. Crea un [host virtuale Apache](#step-2-create-apache-virtual-hosts) per sito Web Commerce.

## Passaggio 1: creare siti web, store e visualizzazioni dello store in Admin

Vedere [Configurare più siti Web, store e visualizzazioni dello store in Admin](ms-admin.md).

## Passaggio 2: creare host virtuali Apache

In questa sezione viene illustrato come impostare i valori per `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` utilizzando la variabile del server Apache `SetEnvIf` in un host virtuale.

Per ulteriori informazioni su `SetEnvIf`, vedere:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Per creare gli host virtuali Apache**:

1. In qualità di utente con privilegi `root`, apri il file di configurazione host virtuale in un editor di testo.

   Ad esempio, apri `/etc/httpd/conf/httpd.conf`

1. Individuare la sezione che inizia con `<VirtualHost *:80>`.
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

1. Salvare le modifiche apportate a `httpd.conf` e uscire dall&#39;editor di testo.
1. Riavvia Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Verifica il sito

A meno che il DNS non sia configurato per gli URL dei tuoi archivi, devi aggiungere una route statica all&#39;host nel file `hosts`:

1. Individuare il file `hosts` del sistema operativo.
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
>- Sono necessarie attività aggiuntive per configurare Adobe Commerce sull&#39;infrastruttura cloud; consulta [Configurare più siti Web o store Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

### Risoluzione dei problemi

- Se i siti francese e tedesco restituiscono 404 secondi ma l&#39;amministratore si carica, assicurati di aver completato [Passaggio 6: aggiungi il codice dello store all&#39;URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono il codice 404, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, verificare di aver configurato correttamente gli host virtuali.

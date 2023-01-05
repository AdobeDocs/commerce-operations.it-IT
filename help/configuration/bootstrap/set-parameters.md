---
title: Imposta il valore dei parametri di bootstrap
description: Scopri come impostare i parametri di avvio per l’applicazione Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Bootstrap parametri

Questo argomento illustra come impostare i valori dei parametri di avvio dell’applicazione Commerce. Vedi [Panoramica dell&#39;inizializzazione dell&#39;applicazione e dell&#39;avvio](initialization.md).

La tabella seguente illustra i parametri di avvio che è possibile impostare:

| Parametro Bootstrap | Descrizione |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Specifica percorsi di directory e URL personalizzati |
| MAGE_PROFILER | Abilita grafici di dipendenza e profilazione HTML |

>[!INFO]
>
>- Non tutti i parametri di bootstrap sono documentati.
>- Ora puoi impostare la modalità applicazione (sviluppatore, predefinito, produzione) utilizzando [`magento deploy:mode:set {mode}`](../cli/set-mode.md) comando.


## Impostare parametri utilizzando una variabile di ambiente

Questa sezione illustra come impostare i valori dei parametri di bootstrap utilizzando le variabili di ambiente.

### Impostare la modalità applicazione

È possibile specificare le variabili di bootstrap come variabili di ambiente a livello di sistema, che consentono a tutti i processi di utilizzarle.

Ad esempio, puoi utilizzare il `MAGE_PROFILER` variabile di ambiente di sistema per specificare una modalità come segue:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Imposta la variabile utilizzando un comando specifico della shell. Poiché le conchiglie hanno sintassi diversa, consulta un riferimento come [unix.stackexchange.com][unix-stackx].

Esempio di shell di base per CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Se `PHP Fatal error` viene visualizzato nel browser dopo aver impostato un valore del profiler e aver riavviato il server web. Il motivo potrebbe essere legato alla memorizzazione in cache del codice bytecode PHP, che memorizza in cache bytecodes e percorsi classici PHP.

## Imposta parametri per Apache o Nginx

Questa sezione illustra come specificare la modalità per Apache o Nginx.

### Impostazione Nginx

Consulta la sezione [Nginx configurazione di esempio] su _GitHub_.

### Impostazione Apache.htaccess

Un modo per impostare la modalità dell&#39;applicazione è quello di modificare `.htaccess`. In questo modo, non è necessario modificare le impostazioni di Apache.

Puoi modificare `.htaccess` in una delle posizioni seguenti, a seconda del punto di ingresso dell’applicazione Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Per impostare una variabile**:

1. Apri uno dei file precedenti in un editor di testo e aggiungi o rimuovi il commento dall’impostazione desiderata.

   Ad esempio, per specificare un [modalità](application-modes.md), rimuovi il commento seguente:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Imposta il valore di `MAGE_PROFILER` a uno dei seguenti elementi:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Salva le modifiche in `.htaccess`; non è necessario riavviare Apache per rendere effettiva la modifica.

### Impostazione Apache

Il server web Apache supporta l’impostazione della modalità applicazione utilizzando `mod_env` direttive.

Apache `mod_env` La direttiva è leggermente diversa [Apache versione 2.2] e [Apache versione 2.4].

Le procedure seguenti mostrano come impostare la modalità applicazione in un host virtuale Apache. Non è l’unico modo per utilizzare `mod_env` direttive; consulta la documentazione di Apache per ulteriori informazioni.

>[!TIP]
>
>Nella sezione seguente si presuppone che tu abbia già configurato l&#39;host virtuale. In caso contrario, consulta una risorsa come [esercitazione su DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Per specificare una variabile di bootstrap per Apache su Ubuntu**:

1. Come utente con `root` , apri il file di configurazione host virtuale in un editor di testo.

   Ad esempio, se l&#39;host virtuale è denominato `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. In qualsiasi punto della configurazione dell&#39;host virtuale, aggiungi la seguente riga:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Ad esempio:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salva le modifiche e esci dall’editor di testo.
1. Abilita l&#39;host virtuale se non lo hai già fatto:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Ad esempio:

   ```bash
   a2ensite my.magento.conf
   ```

1. Dopo aver impostato la modalità , riavvia il server web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>Questa sezione presuppone che tu abbia già configurato l&#39;host virtuale. In caso contrario, consulta una risorsa come [esercitazione su DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Per specificare una variabile bootstrap per Apache su CentOS**:

1. Come utente con `root` privilegi, apri `/etc/httpd/conf/httpd.conf` in un editor di testo.

1. In qualsiasi punto della configurazione dell&#39;host virtuale, aggiungi la seguente riga:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Ad esempio:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salva le modifiche e esci dall’editor di testo.

1. Dopo aver impostato la modalità , riavvia il server web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versione 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versione 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx configurazione di esempio]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables

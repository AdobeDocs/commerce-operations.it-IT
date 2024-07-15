---
title: Imposta il valore dei parametri di bootstrap
description: Scopri come impostare i parametri di bootstrap per l’applicazione Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrap parametri

In questo argomento viene illustrato come impostare i valori dei parametri di avvio dell&#39;applicazione Commerce. Vedere [Panoramica sull&#39;inizializzazione e l&#39;avvio dell&#39;applicazione](initialization.md).

Nella tabella seguente vengono illustrati i parametri di bootstrap che è possibile impostare:

| Bootstrap parametro | Descrizione |
| ------------------- | -------------------------------------------- |
| DIR_IMMAGINE | Specifica percorsi URL e directory personalizzati |
| IMMAGINE_PROFILER | Abilita i grafici delle dipendenze e la profilatura dei HTML |

>[!INFO]
>
>- Non tutti i parametri di bootstrap sono documentati.
>- È ora possibile impostare la modalità applicazione (sviluppatore, predefinito, produzione) utilizzando il comando [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Impostare i parametri utilizzando una variabile di ambiente

Questa sezione illustra come impostare i valori dei parametri di bootstrap utilizzando variabili di ambiente.

### Impostare la modalità applicazione

È possibile specificare le variabili di avvio automatico come variabili di ambiente a livello di sistema, in modo che tutti i processi possano utilizzarle.

Ad esempio, è possibile utilizzare la variabile di ambiente di sistema `MAGE_PROFILER` per specificare una modalità nel modo seguente:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Imposta la variabile utilizzando un comando specifico della shell. Poiché la sintassi delle shell è diversa, consultare un riferimento come [unix.stackexchange.com][unix-stackx].

Esempio di shell Bash per CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Se un `PHP Fatal error` viene visualizzato nel browser dopo aver impostato un valore di profiler, riavviare il server Web. Il motivo potrebbe essere legato alla memorizzazione in cache del bytecode PHP, che memorizza nella cache i bytecode e i classpath PHP.

## Imposta parametri per Apache o Nginx

Questa sezione illustra come specificare la modalità per Apache o Nginx.

### Impostazione Nginx

Vedi la [configurazione di esempio Nginx] in _GitHub_.

### Impostazione Apache .htaccess

Un modo per impostare la modalità applicazione consiste nel modificare `.htaccess`. In questo modo, non è necessario modificare le impostazioni di Apache.

Puoi modificare `.htaccess` in uno dei seguenti percorsi, a seconda del punto di ingresso nell&#39;applicazione Commerce:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Per impostare una variabile**:

1. Apri uno dei file precedenti in un editor di testo e aggiungi o rimuovi il commento dall’impostazione desiderata.

   Ad esempio, per specificare una [modalità](application-modes.md), rimuovi il commento seguente:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Impostare il valore di `MAGE_PROFILER` su uno dei valori seguenti:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Salvare le modifiche apportate a `.htaccess`; non è necessario riavviare Apache per rendere effettiva la modifica.

### Impostazione Apache

Il server web Apache supporta l&#39;impostazione della modalità applicazione utilizzando `mod_env` direttive.

La direttiva Apache `mod_env` è leggermente diversa nelle versioni [Apache 2.2] e [Apache 2.4].

Le procedure seguenti mostrano come impostare la modalità applicazione in un host virtuale Apache. Questo non è l&#39;unico modo per utilizzare `mod_env` direttive. Per informazioni dettagliate, consulta la documentazione di Apache.

>[!TIP]
>
>La sezione seguente presuppone che tu abbia già configurato l&#39;host virtuale. In caso contrario, consulta una risorsa come [questa esercitazione su DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Per specificare una variabile di bootstrap per Apache su Ubuntu**:

1. In qualità di utente con privilegi `root`, apri il file di configurazione host virtuale in un editor di testo.

   Ad esempio, se l&#39;host virtuale è denominato `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. In qualsiasi punto della configurazione host virtuale, aggiungi la seguente riga:

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

1. Dopo aver impostato la modalità, riavviare il server Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>In questa sezione si presuppone che l&#39;host virtuale sia già stato configurato. In caso contrario, consulta una risorsa come [questa esercitazione su DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Per specificare una variabile di bootstrap per Apache su CentOS**:

1. In qualità di utente con privilegi di `root`, apri `/etc/httpd/conf/httpd.conf` in un editor di testo.

1. In qualsiasi punto della configurazione host virtuale, aggiungi la seguente riga:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Ad esempio:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Salva le modifiche e esci dall’editor di testo.

1. Dopo aver impostato la modalità, riavviare il server Web:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache versione 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache versione 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Configurazione campione Nginx]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables

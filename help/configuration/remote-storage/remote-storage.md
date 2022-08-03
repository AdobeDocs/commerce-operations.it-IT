---
title: Configura archiviazione remota
description: Scopri come configurare il modulo Archiviazione remota per l’applicazione Commerce locale.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Configura archiviazione remota

Il modulo Archiviazione remota offre la possibilità di archiviare i file multimediali e pianificare le importazioni/esportazioni in un contenitore di storage remoto persistente utilizzando un servizio di archiviazione, ad esempio AWS S3. Per impostazione predefinita, la [!DNL Commerce] l&#39;applicazione memorizza i file multimediali nello stesso file system che contiene l&#39;applicazione. Ciò è inefficiente per configurazioni complesse e con più server e può causare prestazioni peggiorate durante la condivisione delle risorse. Il modulo Archiviazione remota consente di memorizzare i file multimediali nella `pub/media` e di importare/esportare i file nel `var` directory dell&#39;archivio oggetti remoti per sfruttare il ridimensionamento dell&#39;immagine lato server.

>[!INFO]
>
>L’archiviazione remota è disponibile solo nelle versioni 2.4.2 e successive. Consulta la sezione [Note sulla versione 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>Il modulo di archiviazione remota ha _limitato_ supporto su Adobe Commerce sull’infrastruttura cloud. Impossibile risolvere completamente i problemi relativi al servizio dell&#39;adattatore di archiviazione di terze parti.

![immagine schema](../../assets/configuration/remote-storage-schema.png)

## Opzioni di archiviazione remota

È possibile configurare lo storage remoto utilizzando `remote-storage` con l&#39;opzione [`setup` Comando CLI][setup]. La `remote-storage` utilizza la sintassi seguente:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

La `parameter-name` fa riferimento al nome specifico del parametro di archiviazione remota. Nella tabella seguente sono elencati i parametri disponibili per la configurazione dell&#39;archiviazione remota:

| Parametro della riga di comando | Nome parametro | Descrizione | Valore predefinito |
|--- |--- |--- |--- |
| `remote-storage-driver` | autista | Nome scheda<br>Valori possibili:<br>**file**: Disattiva l&#39;archiviazione remota e utilizza il filesystem locale <br>**aws-s3**: Utilizza la [Servizio di archiviazione semplice Amazon (Amazon S3)](remote-storage-aws-s3.md) | nessuno |
| `remote-storage-bucket` | secchio | Nome dell&#39;archivio oggetti o del contenitore | nessuno |
| `remote-storage-prefix` | prefisso | Prefisso opzionale (posizione all’interno dell’archivio oggetti) | vuoto |
| `remote-storage-region` | regione | Nome della regione | nessuno |
| `remote-storage-key` | chiave di accesso | Chiave di accesso opzionale | vuoto |
| `remote-storage-secret` | chiave segreta | Chiave segreta opzionale | vuoto |

### Adattatori di storage

Il percorso di archiviazione predefinito si trova nel file system locale. A _scheda di memoria_ consente di connettersi a un servizio di archiviazione e archiviare i file ovunque. [!DNL Commerce] supporta la configurazione dei seguenti servizi di archiviazione:

- [Servizio di archiviazione semplice Amazon (Amazon S3)](remote-storage-aws-s3.md)

## Abilita archiviazione remota

È possibile installare l&#39;archiviazione remota durante un nuovo [!DNL Commerce] installazione o aggiunta a un&#39;istanza Commerce esistente utilizzando `remote-storage` coppie nome-e-valore del parametro con `setup` Comandi CLI. Minimalmente, è necessario fornire lo storage `driver`, `bucket`e `region`.

Gli esempi seguenti abilitano lo storage remoto con una scheda di storage AWS S3 negli Stati Uniti:

- Installa nuovo [!DNL Commerce] con archiviazione remota

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Abilita archiviazione remota su esistente [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## Limitazioni

Non è possibile abilitare contemporaneamente lo storage remoto e lo storage del database. Disabilitare la memorizzazione del database se si utilizza l&#39;archiviazione remota.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

L&#39;abilitazione dello storage remoto potrebbe influire sull&#39;esperienza di sviluppo stabilita. Ad esempio, alcune funzioni del file PHP potrebbero non funzionare come previsto. È necessario applicare l’utilizzo di Commerce Framework per le operazioni di file.

L&#39;elenco delle funzioni native PHP vietate è disponibile in [Standard di codifica Magento] archivio.

## Migra contenuto

Dopo aver abilitato lo storage remoto per un adattatore specifico, puoi utilizzare CLI per eseguire la migrazione esistente _media_ file nell&#39;archivio remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Il comando di sincronizzazione esegue la migrazione solo dei file nel `pub/media` directory, _not_ i file di importazione/esportazione nel `var` directory. Vedi [Importazione/esportazione pianificata][import-export] in _Guida utente di Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[nginx-module]: http://nginx.org/en/docs/http/ngx_http_image_filter_module.html
[Standard di codifica Magento]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp

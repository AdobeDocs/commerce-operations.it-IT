---
title: Configura archiviazione remota
description: Scopri come configurare il modulo di archiviazione remota per l’applicazione Commerce on-premise.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Configura archiviazione remota

Il modulo Archiviazione remota consente di memorizzare i file multimediali e pianificare le importazioni e le esportazioni in un contenitore di archiviazione remota persistente utilizzando un servizio di archiviazione, ad esempio AWS S3.

Per impostazione predefinita, l&#39;applicazione Adobe Commerce memorizza i file multimediali nello stesso file system che contiene l&#39;applicazione. Ciò è inefficiente per configurazioni complesse e con più server e può comportare un peggioramento delle prestazioni durante la condivisione delle risorse. Con il modulo Archiviazione remota è possibile archiviare i file multimediali nella directory `pub/media` e importare/esportare i file nella directory `var` dell&#39;archivio oggetti remoto per sfruttare il ridimensionamento delle immagini lato server.

>[!BEGINSHADEBOX]

Non è possibile abilitare contemporaneamente l&#39;archiviazione del database _e_ nell&#39;archiviazione remota. È necessario disabilitare l&#39;archiviazione del database prima di abilitare l&#39;archiviazione remota.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

L&#39;abilitazione dell&#39;archiviazione remota potrebbe influire sulla tua esperienza di sviluppo consolidata. Ad esempio, alcune funzioni dei file PHP potrebbero non funzionare come previsto. L&#39;utilizzo di Commerce Framework per le operazioni sui file deve essere applicato. L&#39;elenco delle funzioni di nativo PHP proibite è disponibile nella [archivio standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) di codifica magento.

>[!ENDSHADEBOX]

>[!INFO]
>
>- L’archiviazione remota è disponibile solo per Commerce versione 2.4.2 e successive. Consulta le [2.4.2 note sulla versione](https://experienceleague.adobe.com/it/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- Il modulo di archiviazione remota dispone del supporto _limitato_ su Adobe Commerce nell&#39;infrastruttura cloud. Adobe non è in grado di risolvere completamente i problemi relativi al servizio adattatore di archiviazione di terze parti. Vedere [Configurare l&#39;archiviazione remota per l&#39;infrastruttura](cloud-support.md) Commerce su cloud per indicazioni sull&#39;implementazione dell&#39;archiviazione remota per progetti cloud.

![immagine schema](../../assets/configuration/remote-storage-schema.png)

## Opzioni di archiviazione remota

È possibile configurare l&#39;archiviazione remota utilizzando l&#39;opzione `remote-storage` con il [`setup` comando](../../installation/tutorials/deployment.md) CLI. L&#39;opzione `remote-storage` utilizza la sintassi seguente:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

Si `parameter-name` riferisce al nome specifico del parametro di archiviazione remota. Nella tabella seguente sono elencati i parametri disponibili per la configurazione dell&#39;archiviazione remota:

| Parametro della riga di comando | Nome parametro | Descrizione | Valore predefinito |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nome scheda<br>Valori possibili:<br>**file**: disabilita l&#39;archiviazione remota e utilizza il file system locale <br>**aws-s3**: utilizza il [servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md) | nessuno |
| `remote-storage-bucket` | bucket | Archiviazione oggetto o nome contenitore | nessuno |
| `remote-storage-prefix` | prefisso | Prefisso opzionale (posizione all&#39;interno dello spazio di archiviazione oggetti) | vuoto |
| `remote-storage-region` | area geografica | Nome regione | nessuno |
| `remote-storage-key` | accesso chiave | Chiave accesso opzionale | vuoto |
| `remote-storage-secret` | chiave segreta | Chiave segreta facoltativa | vuoto |

### Adattatori di storage

Il percorso di archiviazione predefinito si trova nel file system locale. Un _adattatore di archiviazione_ consente di connettersi a un servizio di archiviazione e di archiviare i file ovunque. [!DNL Commerce] supporta la configurazione dei seguenti servizi di archiviazione:

- [Servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md)

## Abilita archiviazione remota

È possibile installare lo storage remoto durante un&#39;installazione di Adobe Commerce o aggiungere lo storage remoto a un&#39;istanza di Commerce esistente. Negli esempi seguenti viene illustrato ogni metodo utilizzando un set di parametri con comandi dell&#39;interfaccia della riga di comando di `remote-storage` Commerce `setup` . È necessario fornire almeno lo spazio di archiviazione `driver`, `bucket`e `region`.

- Esempio: installare Commerce con l’archiviazione remota

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Esempio: abilitare l&#39;archiviazione remota su Commerce esistente

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Per Adobe Commerce sull&#39;infrastruttura cloud, vedere [Configurare l&#39;archiviazione remota per Commerce sull&#39;infrastruttura cloud](cloud-support.md).

## Migrare i contenuti

Dopo aver abilitato l&#39;archiviazione remota per una scheda specifica, è possibile utilizzare l&#39;interfaccia della riga di comando per eseguire la migrazione dei file media _esistenti_ nell&#39;archivio remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Il comando Sincronizzazione consente di migrare solo i `pub/media` file nella directory, _non_ i file di importazione/esportazione nella `var` directory. Vedere [Scheduled Importa/Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=it) in _Commerce 2.4 Guida utente_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html

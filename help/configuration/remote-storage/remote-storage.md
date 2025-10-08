---
title: Configura archiviazione remota
description: Scopri come configurare il modulo di archiviazione remota per l’applicazione Commerce on-premise.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '521'
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

L&#39;abilitazione dell&#39;archiviazione remota potrebbe influire sull&#39;esperienza di sviluppo consolidata. Ad esempio, alcune funzioni dei file PHP potrebbero non funzionare come previsto. È necessario applicare l&#39;utilizzo di Commerce Framework per le operazioni sui file. L&#39;elenco delle funzioni native PHP non consentite è disponibile nell&#39;archivio [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php).

>[!ENDSHADEBOX]

>[!INFO]
>
>- L’archiviazione remota è disponibile solo per Commerce versione 2.4.2 e successive. Consulta le [2.4.2 note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- Il modulo di archiviazione remota dispone del supporto _limitato_ su Adobe Commerce nell&#39;infrastruttura cloud. Adobe non è in grado di risolvere completamente i problemi relativi al servizio adattatore di archiviazione di terze parti. Consulta [Configurare l&#39;archiviazione remota per Commerce sull&#39;infrastruttura cloud](cloud-support.md) per informazioni sull&#39;implementazione dell&#39;archiviazione remota per i progetti cloud.

![Diagramma dello schema di configurazione dell&#39;archiviazione remota che illustra la relazione tra l&#39;archiviazione locale e quella cloud](../../assets/configuration/remote-storage-schema.png)

## Opzioni di archiviazione remota

È possibile configurare l&#39;archiviazione remota utilizzando l&#39;opzione `remote-storage` con il comando CLI [`setup`](../../installation/tutorials/deployment.md). L&#39;opzione `remote-storage` utilizza la sintassi seguente:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` fa riferimento al nome del parametro specifico dell&#39;archiviazione remota. Nella tabella seguente sono elencati i parametri disponibili per la configurazione dell&#39;archiviazione remota:

| Parametro della riga di comando | Nome parametro | Descrizione | Valore predefinito |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nome scheda<br>Valori possibili:<br>**file**: disabilita l&#39;archiviazione remota e utilizza il file system locale <br>**aws-s3**: utilizza il [servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md) | nessuno |
| `remote-storage-bucket` | bucket | Archiviazione oggetto o nome contenitore | nessuno |
| `remote-storage-prefix` | prefisso | Prefisso facoltativo (posizione all&#39;interno dell&#39;archivio oggetti) | vuoto |
| `remote-storage-region` | area geografica | Nome regione | nessuno |
| `remote-storage-key` | chiave di accesso | Chiave di accesso opzionale | vuoto |
| `remote-storage-secret` | chiave segreta | Chiave segreta opzionale | vuoto |

### Adattatori di storage

Il percorso di archiviazione predefinito si trova nel file system locale. Un _adattatore di archiviazione_ consente di connettersi a un servizio di archiviazione e di archiviare i file ovunque. [!DNL Commerce] supporta la configurazione dei seguenti servizi di archiviazione:

- [Servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md)

## Abilita archiviazione remota

È possibile installare lo storage remoto durante un&#39;installazione di Adobe Commerce o aggiungere lo storage remoto a un&#39;istanza di Commerce esistente. Gli esempi seguenti illustrano ogni metodo utilizzando un set di parametri `remote-storage` con comandi CLI di Commerce `setup`. È necessario fornire almeno lo spazio di archiviazione `driver`, `bucket` e `region`.

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

Dopo aver abilitato l&#39;archiviazione remota per una scheda specifica, è possibile utilizzare CLI per migrare i file _media_ esistenti nell&#39;archiviazione remota.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Il comando sync esegue la migrazione solo dei file nella directory `pub/media`, _not_ i file di importazione/esportazione nella directory `var`. Vedi [Importazione/esportazione pianificata](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) nella _Guida utente di Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html

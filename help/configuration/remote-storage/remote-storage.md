---
title: Configura archiviazione remota
description: Scopri come configurare il modulo di archiviazione remota per l’applicazione Commerce on-premise.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Configura archiviazione remota

Il modulo Archiviazione remota consente di memorizzare i file multimediali e pianificare le importazioni e le esportazioni in un contenitore di archiviazione remota persistente utilizzando un servizio di archiviazione, ad esempio AWS S3. Per impostazione predefinita, l&#39;applicazione Adobe Commerce memorizza i file multimediali nello stesso file system che contiene l&#39;applicazione. Ciò è inefficiente per configurazioni complesse e con più server e può comportare un peggioramento delle prestazioni durante la condivisione delle risorse. Con il modulo Archiviazione remota, è possibile archiviare i file multimediali in `pub/media` e importare/esportare file in `var` directory dell&#39;archivio oggetti remoto per sfruttare il ridimensionamento dell&#39;immagine lato server.

>[!INFO]
>
>L’archiviazione remota è disponibile solo per Commerce versione 2.4.2 e successive. Consulta la [Note sulla versione 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>Il modulo di archiviazione remota dispone di _limitato_ supporto per Adobe Commerce su infrastruttura cloud. L&#39;Adobe non è in grado di risolvere completamente i problemi relativi al servizio adattatore di archiviazione di terze parti. Consulta [Configurare l’archiviazione remota per l’infrastruttura Commerce on Cloud](cloud-support.md) come guida all’implementazione dell’archiviazione remota per i progetti cloud.

![immagine schema](../../assets/configuration/remote-storage-schema.png)

## Opzioni di archiviazione remota

È possibile configurare l&#39;archiviazione remota utilizzando `remote-storage` opzione con [`setup` Comando CLI](../../installation/tutorials/deployment.md). Il `remote-storage` L&#39;opzione utilizza la sintassi seguente:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

Il `parameter-name` fa riferimento al nome del parametro specifico di archiviazione remota. Nella tabella seguente sono elencati i parametri disponibili per la configurazione dell&#39;archiviazione remota:

| Parametro della riga di comando | Nome parametro | Descrizione | Valore predefinito |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nome adattatore<br>Valori possibili:<br>**file**: disabilita l&#39;archiviazione remota e utilizza il file system locale <br>**aws-s3**: utilizza [Servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md) | nessuno |
| `remote-storage-bucket` | bucket | Archiviazione oggetto o nome contenitore | nessuno |
| `remote-storage-prefix` | prefisso | Prefisso facoltativo (posizione all&#39;interno dell&#39;archivio oggetti) | vuoto |
| `remote-storage-region` | area geografica | Nome regione | nessuno |
| `remote-storage-key` | chiave di accesso | Chiave di accesso opzionale | vuoto |
| `remote-storage-secret` | chiave segreta | Chiave segreta opzionale | vuoto |

### Adattatori di storage

Il percorso di archiviazione predefinito si trova nel file system locale. A _scheda di storage_ consente di connettersi a un servizio di archiviazione e archiviare i file ovunque. [!DNL Commerce] supporta la configurazione dei seguenti servizi di archiviazione:

- [Servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md)

## Abilita archiviazione remota

È possibile installare l’archiviazione remota durante un’installazione di Adobe Commerce o aggiungere l’archiviazione remota a un’istanza di Commerce esistente. Gli esempi seguenti illustrano ogni metodo utilizzando un insieme di `remote-storage` parametri con Commerce `setup` Comandi CLI. Minimamente, è necessario fornire lo storage `driver`, `bucket`, e `region`.

- Esempio: installare Commerce con l’archiviazione remota

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Esempio: abilitare l’archiviazione remota su Commerce esistente

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Per l’infrastruttura cloud di Adobe Commerce, consulta [Configurare l’archiviazione remota per l’infrastruttura Commerce on Cloud](cloud-support.md).

## Limitazioni

Non è possibile attivare contemporaneamente sia l&#39;archiviazione remota che l&#39;archiviazione del database. Disattivare l&#39;archiviazione del database se si utilizza l&#39;archiviazione remota.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

L&#39;abilitazione dell&#39;archiviazione remota potrebbe influire sull&#39;esperienza di sviluppo consolidata. Ad esempio, alcune funzioni dei file PHP potrebbero non funzionare come previsto. È necessario applicare l’utilizzo di Commerce Framework per le operazioni sui file.

L&#39;elenco delle funzioni native PHP non consentite è disponibile in [archivio standard di codifica magento][code-standard].

## Migrare i contenuti

Dopo aver attivato l&#39;archiviazione remota per una scheda specifica, è possibile utilizzare CLI per eseguire la migrazione di _media_ file nell&#39;archivio remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Il comando di sincronizzazione esegue la migrazione solo dei file nel `pub/media` directory, _non_ i file di importazione/esportazione in `var` directory. Consulta [Importazione/Esportazione programmata](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) nel _Guida utente di Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php

---
title: Configurare il bucket AWS S3 per l’archiviazione remota
description: Configura il progetto Commerce per utilizzare il servizio di archiviazione AWS S3 per l’archiviazione remota.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Configurare il bucket AWS S3 per l’archiviazione remota

[Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3) è un servizio di archiviazione degli oggetti che offre scalabilità, disponibilità dei dati, sicurezza e prestazioni leader del settore. Il servizio AWS S3 utilizza contenitori o bucket per l’archiviazione dei dati. Questa configurazione richiede la creazione di un bucket _private_. Per Adobe Commerce sull&#39;infrastruttura cloud, vedere [Configurare l&#39;archiviazione remota per Commerce sull&#39;infrastruttura cloud](cloud-support.md).

>[!WARNING]
>
>Adobe scoraggia fortemente l’uso di contenitori pubblici perché comporta gravi rischi per la sicurezza.
>
>Quando si utilizza un bucket S3 fornito dal cliente per l’archiviazione di risorse o supporti, Adobe non è responsabile e non fornisce supporto per eventuali problemi, perdite di dati o interruzioni relativi alla configurazione, alla gestione o al funzionamento del bucket S3. La risoluzione dei problemi e la manutenzione del bucket S3 sono di esclusiva responsabilità del cliente.

**Per abilitare l&#39;archiviazione remota con la scheda AWS S3**:

1. Accedi al tuo dashboard di Amazon S3 e crea un bucket _private_.

1. Configura [i ruoli AWS IAM](https://aws.amazon.com/iam/). In alternativa, genera l’accesso e le chiavi segrete.

1. Disattiva l&#39;archiviazione del database predefinita.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configura Commerce per l’utilizzo del bucket privato. Consulta [Opzioni di archiviazione remota](remote-storage.md#remote-storage-options) per un elenco completo dei parametri.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Sincronizzare i file multimediali con l&#39;archiviazione remota.

   ```bash
   bin/magento remote-storage:sync
   ```

## Configurare Nginx

>[!NOTE]
>
>Questo approccio non è applicabile ai progetti Adobe Commerce su infrastrutture cloud. Nginx non può essere configurato su Adobe Commerce nell’infrastruttura cloud. Per ulteriori informazioni, consulta la [documentazione specifica per il cloud](cloud-support.md).

Nginx richiede una configurazione aggiuntiva per eseguire l&#39;autenticazione con la direttiva `proxy_pass`. Aggiungere le seguenti informazioni proxy al file `nginx.conf`:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Autenticazione

Se utilizzi le chiavi di accesso e segrete invece di [ruoli AWS IAM](https://aws.amazon.com/iam/), devi includere il modulo Nginx [`ngx_aws_auth`](https://github.com/anomalizer/ngx_aws_auth).

### Autorizzazioni

L’integrazione di S3 si basa sulla capacità di generare e archiviare immagini memorizzate nella cache sul file system locale. Pertanto, le autorizzazioni per le cartelle di `pub/media` e directory simili sono le stesse per S3 quando si utilizza l&#39;archiviazione locale.

### Operazioni per file

Si consiglia di utilizzare i metodi dell&#39;adattatore di file [!DNL Commerce] nello sviluppo della codifica o dell&#39;estensione, indipendentemente dal tipo di archiviazione dei file. Quando si utilizza S3 per l&#39;archiviazione, non utilizzare operazioni I/O native del file PHP, ad esempio `copy`, `rename` o `file_put_contents`, perché i file S3 non si trovano nel file system. Per esempi di codice, vedere [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18).


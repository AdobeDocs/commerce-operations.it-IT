---
title: Configurare il bucket AWS S3 per l’archiviazione remota
description: Configura il progetto Commerce per utilizzare il servizio di archiviazione AWS S3 per l’archiviazione remota.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Configurare il bucket AWS S3 per l’archiviazione remota

[Amazon Simple Storage Service (Amazon S3)][AWS S3] è un servizio di archiviazione degli oggetti che offre scalabilità, disponibilità dei dati, sicurezza e prestazioni leader del settore. Il servizio AWS S3 utilizza contenitori o bucket per l’archiviazione dei dati. Questa configurazione richiede la creazione di un bucket _private_. Per Adobe Commerce sull&#39;infrastruttura cloud, vedere [Configurare l&#39;archiviazione remota per Commerce sull&#39;infrastruttura cloud](cloud-support.md).

>[!WARNING]
>
>L&#39;Adobe scoraggia fortemente l&#39;uso di secchi pubblici perché comporta gravi rischi per la sicurezza.

**Per abilitare l&#39;archiviazione remota con la scheda AWS S3**:

1. Accedi al tuo dashboard di Amazon S3 e crea un bucket _private_.

1. Configura [i ruoli AWS IAM]. In alternativa, genera l’accesso e le chiavi segrete.

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

Se utilizzi le chiavi di accesso e segrete invece di [ruoli AWS IAM], devi includere il modulo Nginx [`ngx_aws_auth`][ngx repo].

### Autorizzazioni

L’integrazione di S3 si basa sulla capacità di generare e archiviare immagini memorizzate nella cache sul file system locale. Pertanto, le autorizzazioni per le cartelle di `pub/media` e directory simili sono le stesse per S3 quando si utilizza l&#39;archiviazione locale.

### Operazioni per file

Si consiglia di utilizzare i metodi dell&#39;adattatore di file [!DNL Commerce] nello sviluppo della codifica o dell&#39;estensione, indipendentemente dal tipo di archiviazione dei file. Quando si utilizza S3 per l&#39;archiviazione, non utilizzare operazioni I/O native del file PHP, ad esempio `copy`, `rename` o `file_put_contents`, perché i file S3 non si trovano nel file system. Per esempi di codice, vedere [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18).

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth

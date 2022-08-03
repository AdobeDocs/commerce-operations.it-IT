---
title: Configurare il bucket AWS S3 per l’archiviazione remota
description: Configura il progetto Commerce per utilizzare il servizio di archiviazione AWS S3 per l’archiviazione remota.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Configurare il bucket AWS S3 per l’archiviazione remota

La [Servizio di archiviazione semplice Amazon (Amazon S3)][AWS S3] è un servizio di storage per oggetti che offre scalabilità, disponibilità, sicurezza e prestazioni leader del settore. Il servizio AWS S3 utilizza bucket o contenitori per l’archiviazione dei dati. Questa configurazione richiede la creazione di un _privato_ secchio.

>[!WARNING]
>
>L&#39;Adobe scoraggia fortemente l&#39;uso di secchi pubblici perché comporta gravi rischi per la sicurezza.

**Per abilitare lo storage remoto con la scheda AWS S3**:

1. Accedi al tuo dashboard Amazon S3 e crea un _privato_ secchio.

1. Configurazione [AWS IAM] ruoli. In alternativa, genera le chiavi di accesso e segrete.

1. Disattivare la memorizzazione predefinita del database.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configura Commerce per utilizzare il bucket privato. Vedi [Opzioni di archiviazione remota](remote-storage.md#remote-storage-options) per un elenco completo dei parametri.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Configura input penna

Nginx richiede una configurazione aggiuntiva per eseguire Authentication con il `proxy_pass` direttiva. Aggiungi le seguenti informazioni proxy al `nginx.conf` file:

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

Se utilizzi le chiavi di accesso e segrete anziché [AWS IAM] ruoli, devi includere [`ngx_aws_auth` Modulo Nginx][ngx repo].

### Autorizzazioni

L&#39;integrazione S3 si basa sulla capacità di generare e memorizzare immagini memorizzate nella cache sul file system locale; pertanto, le autorizzazioni per le cartelle per `pub/media` e directory simili sono le stesse per S3 quando si utilizza l&#39;archiviazione locale.

### Operazioni sui file

Si consiglia vivamente di utilizzare [!DNL Commerce] metodi dell&#39;adattatore file nello sviluppo della codifica o dell&#39;estensione, indipendentemente dal tipo di archiviazione dei file. Quando si utilizza S3 per lo storage, non utilizzare operazioni I/O native per i file PHP, ad esempio `copy`, `rename` o `file_put_contents`, poiché i file S3 non si trovano nel file system. Vedi [DriverInterface.php] per esempi di codice.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
[DriverInterface.php]: https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18

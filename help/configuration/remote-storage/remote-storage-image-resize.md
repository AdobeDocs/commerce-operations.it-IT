---
title: Configurare il ridimensionamento delle immagini per l'archiviazione remota
description: Ottimizzare le risorse disco configurando il ridimensionamento delle immagini lato server.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Configurare il ridimensionamento delle immagini per l&#39;archiviazione remota

Per impostazione predefinita, Adobe Commerce supporta il ridimensionamento delle immagini lato applicazione. Tuttavia, attivando il modulo di archiviazione remota, è possibile utilizzare Nginx per scaricare il ridimensionamento delle immagini sul lato server, dove è possibile risparmiare risorse disco e ottimizzare l&#39;utilizzo del disco.

Il diagramma seguente mostra come Nginx recupera, ridimensiona e memorizza le immagini nella cache. Il ridimensionamento è determinato dai parametri inclusi nell’URL, ad esempio altezza e larghezza.

![ridimensionamento immagine](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Per i progetti Adobe Commerce su infrastrutture cloud, consulta [Configurare l&#39;archiviazione remota per Commerce su infrastrutture cloud](cloud-support.md)

## Configurare il formato URL in Adobe Commerce

Per ridimensionare le immagini sul lato server, devi configurare Adobe Commerce in modo da fornire argomenti per l’altezza, la larghezza e la posizione (URL) dell’immagine.

**Per configurare Commerce per il ridimensionamento delle immagini lato server**:

1. Nel pannello _Amministratore_, fare clic su **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Nel riquadro di destra espandere **[!UICONTROL Url options]**.

1. Nella sezione _Formato URL contenuto multimediale catalogo_, cancella **[!UICONTROL Use system value]**.

1. Selezionare l&#39;URL `Image optimization based on query parameters` nel campo **_Formato URL contenuto multimediale catalogo_**.

1. Fare clic su **[!UICONTROL Save Config]**.

1. Passa alla [configurazione Nginx](#configure-nginx).

## Configurare Nginx

Per continuare a configurare il ridimensionamento delle immagini lato server, è necessario preparare il file `nginx.conf` e fornire un valore `proxy_pass` per l&#39;adattatore scelto.

**Per consentire a Nginx di ridimensionare le immagini**:

1. Installa il modulo filtro immagini [Nginx][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Creare un file `nginx.conf` in base al file `nginx.conf.sample` del modello incluso. Ad esempio:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Facoltativo_] Configura un valore `proxy_pass` per la scheda specifica.

   - [Servizio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html

---
title: Configurare il ridimensionamento delle immagini per l'archiviazione remota
description: Ottimizza le risorse del disco configurando il ridimensionamento delle immagini lato server.
source-git-commit: 7fc5d561baa3c2a4aab160a35a1c8a302a62a3b1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# Configurare il ridimensionamento delle immagini per l&#39;archiviazione remota

Per impostazione predefinita, Adobe Commerce supporta il ridimensionamento dell’immagine sul lato dell’applicazione. Tuttavia, abilitando il modulo Archiviazione remota, è possibile utilizzare Nginx per scaricare il ridimensionamento dell&#39;immagine sul lato server, dove è possibile salvare le risorse del disco e ottimizzare l&#39;utilizzo del disco.

Il diagramma seguente mostra come Nginx recupera, ridimensiona e archivia le immagini nella cache. Il ridimensionamento è determinato dai parametri inclusi nell’URL, ad esempio altezza e larghezza.

![ridimensionamento immagine](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Per Adobe Commerce sui progetti di infrastruttura cloud, consulta [Configurare lo storage remoto per l’infrastruttura Commerce su Cloud](cloud-support.md)

## Configurare il formato URL in Adobe Commerce

Per ridimensionare le immagini sul lato server, è necessario configurare Adobe Commerce in modo da fornire argomenti relativi all’altezza, alla larghezza e alla posizione (URL) dell’immagine.

**Per configurare Commerce per il ridimensionamento delle immagini lato server**:

1. In _Amministratore_ pannello, fai clic su **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Nel riquadro a destra, espandi **[!UICONTROL Url options]**.

1. In _Formato URL contenuti nel catalogo_ sezione, cancella **[!UICONTROL Use system value]**.

1. Seleziona la `Image optimization based on query parameters` URL nel **_Formato URL contenuti nel catalogo_** campo .

1. Clic **[!UICONTROL Save Config]**.

1. Procedi alla [Configurazione di Nginx](#configure-nginx).

## Configura input penna

Per continuare a configurare il ridimensionamento dell’immagine lato server, devi preparare la `nginx.conf` e fornire un `proxy_pass` valore per l&#39;adattatore scelto.

**Per abilitare Nginx al ridimensionamento delle immagini**:

1. Installa il [Modulo filtro immagini nginx][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Crea un `nginx.conf` in base al modello incluso `nginx.conf.sample` file. Ad esempio:

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

1. [_Facoltativo_] Configura un `proxy_pass` valore per l&#39;adattatore specifico.

   - [Servizio di archiviazione semplice Amazon (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html

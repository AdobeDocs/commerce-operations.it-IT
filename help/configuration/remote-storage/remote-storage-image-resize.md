---
title: Configurare il ridimensionamento delle immagini per l'archiviazione remota
description: Ottimizzare le risorse disco configurando il ridimensionamento delle immagini lato server.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# Configurare il ridimensionamento delle immagini per l&#39;archiviazione remota

Per impostazione predefinita, Adobe Commerce supporta il ridimensionamento delle immagini lato applicazione. Tuttavia, attivando il modulo di archiviazione remota, è possibile utilizzare Nginx per scaricare il ridimensionamento delle immagini sul lato server, dove è possibile risparmiare risorse disco e ottimizzare l&#39;utilizzo del disco.

Il diagramma seguente mostra come Nginx recupera, ridimensiona e memorizza le immagini nella cache. Il ridimensionamento è determinato dai parametri inclusi nell’URL, ad esempio altezza e larghezza.

![Configurazione Nginx per il ridimensionamento dell&#39;immagine di archiviazione remota con le impostazioni del blocco del server](../../assets/configuration/remote-storage-nginx-image-resize.png)

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

1. Installa il modulo filtro immagini [Nginx](https://nginx.org/en/docs/http/ngx_http_image_filter_module.html).

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


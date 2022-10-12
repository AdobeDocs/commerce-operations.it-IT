---
title: Archiviazione remota per Commerce su infrastruttura cloud
description: Consulta le indicazioni su come configurare l’archiviazione remota per Adobe Commerce sull’infrastruttura cloud.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Configurare lo storage remoto per l’infrastruttura Commerce su Cloud

Se scegli di utilizzare la soluzione di archiviazione remota con un progetto di infrastruttura cloud Adobe Commerce, utilizza la [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) guida _Favoloso_ per garantire il funzionamento di Flast Image Optimization con AWS S3.

Preparati con il tuo [Credenziali definitive](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#cloud-fastly-creds). Nei progetti Pro, utilizza SSH per connetterti al server e ottenere le credenziali Flast dal `/mnt/shared/fastly_tokens.txt` file. Gli ambienti di staging e produzione dispongono di credenziali univoche. Devi ottenere le credenziali per ogni ambiente.

Continua a configurare l’archiviazione remota per i progetti cloud con le seguenti attività:

1. Configura un [Integrazione di back-end](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crea logica VCL per [Autenticazione AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crea logica VCL per [richieste di back-end al bucket AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).

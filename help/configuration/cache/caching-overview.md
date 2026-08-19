---
title: Panoramica della memorizzazione in cache e opzioni di configurazione
description: Scopri come memorizzare in cache Adobe Commerce, incluso l’archiviazione back-end, la configurazione front-end e il caching a pagina intera con cache di tipo vernice, Redis, Valkey e L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# Panoramica sulla memorizzazione in cache e opzioni di configurazione

Adobe Commerce utilizza più livelli di caching per ridurre l’elaborazione ripetuta, ridurre il carico del database e migliorare i tempi di risposta. Questi livelli operano in punti diversi della richiesta e della consegna delle risorse:

- **Il caching delle applicazioni** memorizza i dati generati o elaborati utilizzando i tipi di cache di Commerce.
- **Il caching HTTP a pagina intera** memorizza le risposte HTTP complete prima che raggiungano l&#39;applicazione Commerce.
- **L2 caching** può aggiungere una cache locale in ogni nodo Web davanti all&#39;archiviazione della cache remota condivisa.
- **La memorizzazione nella cache statica dei contenuti** consente ai browser di riutilizzare CSS, JavaScript, immagini e altre risorse statiche.

Questa pagina fornisce una panoramica concettuale di questi livelli e collegamenti alle relative linee guida di configurazione. Per le scelte di back-end, i dettagli di implementazione e le impostazioni specifiche della versione, vedere [Opzioni di back-end cache e riferimento archiviazione](cache-options.md).

## Caching dei livelli

### Memorizzazione nella cache delle applicazioni

Il caching delle applicazioni Commerce è organizzato come segue:

>[!BEGINSHADEBOX]

tipo di cache → cache front-end → cache back-end

>[!ENDSHADEBOX]

Un tipo di **cache** identifica il tipo di dati da memorizzare nella cache, ad esempio configurazione, layout, blocco di HTML o contenuto a pagina intera. Una **cache front-end** collega uno o più tipi di cache all&#39;archiviazione. Un backend **cache** fornisce l&#39;implementazione dell&#39;archiviazione.

È possibile assegnare tipi di cache diversi a front-end diversi quando sono necessarie impostazioni di cache o storage separati. Per informazioni sulla configurazione, vedere [Configurare i tipi e i front-end della cache](cache-types.md).

### Memorizzazione in cache HTTP a pagina intera

Il caching HTTP a pagina intera memorizza le risposte complete a livello HTTP o CDN. Per le distribuzioni di produzione:

- **Adobe Commerce on-premise**—Adobe consiglia [Vernice](config-varnish.md) per il caching a pagina intera. La vernice funziona come proxy inverso davanti al server web.
- **Adobe Commerce sull&#39;infrastruttura cloud** utilizza [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"} per il livello di caching Edge e a pagina intera. L&#39;infrastruttura cloud non utilizza un servizio di vernice gestito separatamente.

>[!NOTE]
>
>La modifica del back-end della cache dell’applicazione Commerce non configura Varnish o Fastly. Il caching HTTP a pagina intera è configurato e gestito separatamente dalla cache delle applicazioni di basso livello.

### Memorizzazione nella cache L2

L2, o a due livelli, il caching aggiunge una cache locale su ciascun nodo web Commerce mantenendo la memoria cache remota condivisa. I dati a cui si accede di frequente possono essere serviti localmente, riducendo la comunicazione con la cache remota in implementazioni a più nodi.

La configurazione L2 e le implementazioni supportate variano in base alla versione e al tipo di distribuzione di Commerce. Per ulteriori dettagli, vedere [Configurazione cache L2](level-two-cache.md).

### Memorizzazione in cache di contenuti statici

Commerce può migliorare la memorizzazione nella cache del browser di risorse statiche come CSS, JavaScript e immagini aggiungendo una versione di distribuzione ai relativi URL. Quando il contenuto cambia, l’URL cambia e il browser richiede la nuova risorsa invece di utilizzare una copia precedentemente memorizzata nella cache.

## Configurazione specifica per la distribuzione

Le seguenti attività di configurazione variano a seconda del tipo di distribuzione.

| Attività | On-premise | Infrastruttura cloud |
| --- | --- | --- |
| Back-end della cache dell&#39;applicazione | [Opzioni di back-end cache e riferimento archiviazione](cache-options.md) | [Best practice per la configurazione del servizio Valkey e Redis](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| caching HTTP a pagina intera | [Configura vernice](config-varnish.md) | [Panoramica dei servizi rapidi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) |

Le seguenti attività si applicano a tutti i tipi di distribuzione:

- **Configurare tipi di cache e front-end** [Configurare i front-end e i tipi di cache](cache-types.md) per associare i tipi di cache ai front-end della cache.
- **Configura memorizzazione nella cache L2**—[Configurazione cache L2](level-two-cache.md).
- **Configura l&#39;annullamento della validità della cache del browser per il contenuto statico**—[Firma del contenuto statico e annullamento della validità della cache del browser](static-content-signing.md).

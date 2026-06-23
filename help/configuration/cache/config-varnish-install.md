---
title: Installa vernice
description: Scopri i requisiti di installazione di Vernice per il caching di Adobe Commerce. Scopri le risorse di installazione e le linee guida per la configurazione.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T21:26:58.525Z'
TQID: 'https://experienceleague.adobe.com/Cvy4Qsi-5Fom1t5wqNlq1SiSs4Bb8-DPsWrGfapWfSc'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 0%

---

# Installa vernice

{{varnish-config-cloud}}

L&#39;installazione di Vernice esula dall&#39;ambito di questa guida. In questo argomento si presuppone una versione supportata di Vernice e un server di origine Adobe Commerce in esecuzione dietro a Vernice. Gli esempi in questa guida utilizzano Inginx come server web di origine.

- [guida all’installazione](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Guide all&#39;installazione di vernice](https://www.varnish-cache.org/docs)
- [Come installare Vernice (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Se si desidera installare i moduli di vernice (vmod), ad esempio la modalità saint, è consigliabile installare Vernice compilando il codice anziché installandolo da un pacchetto. Per ulteriori dettagli, vedere [Modalità SAINT](config-varnish-advanced.md#saint-mode).

## Conferma la versione di vernice

Apri un terminale e immetti il seguente comando per visualizzare la versione di Vernice:

```shell
varnishd -V
```

Prima di continuare, assicurati che [Adobe Commerce supporti](../../installation/system-requirements.md) la versione installata di Vernice. Se esegui una versione non supportata, devi passare a una versione supportata. Per ulteriori informazioni, consultare la documentazione di installazione di Vernice.

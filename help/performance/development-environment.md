---
title: Ambiente di sviluppo Recommendations
description: Scopri i consigli sulle prestazioni per la configurazione dell’ambiente di sviluppo Adobe Commerce o di Magento Open Source locale.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Raccomandazioni per l’ambiente di sviluppo

Questa pagina fornisce consigli per gli ambienti di sviluppo di Commerce.

## Pulire le cache invece di disattivare

Molti sviluppatori tendono a disabilitare tutte le cache sulle loro istanze di sviluppatori. È consigliabile pulire solo le cache, senza disabilitare tutte le cache. [!DNL Commerce] viene eseguito in modo più efficiente quando [pulire le cache](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) invece di disattivarli completamente. La maggior parte dei tipi di cache vengono raramente invalidati durante lo sviluppo.

Se [disattivare le cache](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), è consigliabile disabilitare solo le cache di pagina e di blocco nelle istanze di sviluppo. Ricorda di abilitare tutte le cache durante il test.

## Comandi da evitare in modalità di sviluppo

In modalità di sviluppo, non eseguire comandi per la compilazione, la generazione di codice e la distribuzione di contenuto statico. Questi comandi sono stati creati per essere utilizzati solo in modalità di produzione.

**Non eseguire** comandi di produzione in modalità di sviluppo:

* `setup:di:compile` genera classi generate automaticamente e cache di configurazione ottimizzate.

  ```bash
  bin/magento setup:di:compile
  ```

  In modalità di sviluppo, il Magento esegue la generazione on-demand, senza bisogno di eseguirla. Se è stata modificata una firma di una classe e occorre rigenerarne la generazione automatica `factories/proxies/interceptors`, rimuovere tali classi o _generato_ cartella.

* `setup:static-content:deploy` distribuisce contenuto statico per un archivio.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  In modalità di sviluppo, il Magento lo esegue su richiesta; non è necessario eseguirlo.

## Tempo di caricamento normale della pagina in una macchina virtuale

Se si sviluppa su una VM e il caricamento di una pagina di Magento richiede più di 2 secondi, rivedere le impostazioni dell&#39;ambiente.

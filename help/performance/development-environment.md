---
title: Ambiente di sviluppo Recommendations
description: Scopri i consigli sulle prestazioni per la configurazione dell’ambiente di sviluppo Adobe Commerce locale o Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Raccomandazioni in materia di ambiente di sviluppo

Questa pagina fornisce consigli per gli ambienti di sviluppo Commerce.

## Pulisci le cache invece di disattivarle

Molti sviluppatori tendono a disabilitare tutte le cache sulle loro istanze di sviluppatori. Si consiglia di pulire solo le cache, senza disabilitare tutte le cache. [!DNL Commerce] esegue in modo più efficiente quando [pulire le cache] invece di disattivarli completamente. La maggior parte dei tipi di cache viene raramente invalidata durante lo sviluppo.

Se [disattivare le cache], consigliamo solo di disabilitare le cache di pagine e blocchi nelle istanze di sviluppo. Ricorda di abilitare tutte le cache durante il test.

## Comandi da evitare in modalità di sviluppo

In modalità di sviluppo, non eseguire comandi per la compilazione, la generazione del codice e la distribuzione di contenuti statici. Questi comandi sono stati creati solo per la modalità di produzione.

**Non eseguire** comandi di produzione in modalità di sviluppo:

* `setup:di:compile` genera classi generate automaticamente e cache di configurazione ottimizzate.

   ```bash
   bin/magento setup:di:compile
   ```

   In modalità di sviluppo, il Magento esegue la generazione su richiesta; non è necessario eseguirlo. Se è stata modificata una firma di una classe e è necessario rigenerarla automaticamente `factories/proxies/interceptors`, rimuovi tali classi o _generato_ cartella.

* `setup:static-content:deploy` distribuisce contenuto statico per uno store.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   In modalità di sviluppo, il Magento lo esegue su richiesta; non è necessario eseguirlo.

## Tempo di caricamento normale della pagina in una macchina virtuale

Se si sviluppa su una VM e il caricamento di una pagina di Magento richiede più di 2 secondi, rivedere le impostazioni dell&#39;ambiente.

<!-- Link definitions -->

[pulire le cache]: ../configuration/cli/manage-cache.md#clean-and-flush-cache-types
[disattivare le cache]: ../configuration/cli/manage-cache.md#enable-or-disable-cache-types

---
title: Raccomandazioni per l’ambiente di sviluppo
description: Scopri i consigli sulle prestazioni per la configurazione dell’ambiente di sviluppo Adobe Commerce locale.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Raccomandazioni per l’ambiente di sviluppo

Questa pagina fornisce consigli per gli ambienti di sviluppo Commerce.

## Pulire le cache invece di disattivare

Molti sviluppatori tendono a disabilitare tutte le cache sulle loro istanze di sviluppatori. È consigliabile pulire solo le cache, senza disabilitare tutte le cache. [!DNL Commerce] viene eseguito in modo più efficiente quando [pulisci le cache](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) anziché disabilitarle completamente. La maggior parte dei tipi di cache vengono raramente invalidati durante lo sviluppo.

Se [disattivi le cache](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), ti consigliamo di disabilitare solo le cache di pagina e di blocco nelle istanze di sviluppo. Ricorda di abilitare tutte le cache durante il test.

## Comandi da evitare in modalità di sviluppo

In modalità di sviluppo, non eseguire comandi per la compilazione, la generazione di codice e la distribuzione di contenuto statico. Questi comandi sono stati creati per essere utilizzati solo in modalità di produzione.

**Non eseguire** comandi di produzione in modalità di sviluppo:

* `setup:di:compile` genera classi generate automaticamente e cache di configurazione ottimizzate.

  ```bash
  bin/magento setup:di:compile
  ```

  In modalità di sviluppo, Magento esegue la generazione su richiesta; non è necessario eseguirla. Se hai modificato una firma di una classe e devi rigenerare `factories/proxies/interceptors` generato automaticamente, rimuovi tali classi o la cartella _generated_.

* `setup:static-content:deploy` distribuisce il contenuto statico per un archivio.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  In modalità di sviluppo, Magento lo esegue su richiesta; non è necessario eseguirlo.

## Tempo di caricamento normale della pagina in una macchina virtuale

Se si sviluppa su una VM e il caricamento di una pagina Magento richiede più di 2 secondi, rivedere le impostazioni dell&#39;ambiente.
